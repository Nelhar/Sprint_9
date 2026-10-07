# SLO-контракт: Уведомления (SMS, WhatsApp, push, USSD)

**Владелец сервиса:** модуль `notifications` (первым выделяется в сервис, [Task5/transition-architecture.md](../../Task5/transition-architecture.md)). **Потребители:** покупатели (статус заказа, OTP), продавцы без кабинета (WhatsApp), сельские покупатели (SMS/USSD). **Критический путь:** «заказ создан → продавец узнал и подтвердил → покупатель знает статус».

## SLI — что и как измеряем

| SLI | Тип (OpenSLO) | «Хорошее» событие | Все события | Где измеряется |
|---|---|---|---|---|
| **SLI-NOT-1 Своевременность передачи шлюзу** | ratioMetric | Сообщение принято шлюзом (Africa's Talking / WhatsApp Cloud API) ≤ 60 с после бизнес-события | Все транзакционные сообщения | `notifications_sent_total{channel,within_60s}` |
| **SLI-NOT-2 Доставка** | ratioMetric | Получен отчёт о доставке (DLR, статус `delivered` от WhatsApp) ≤ 5 мин | Все отправленные с DLR | Callback DLR → `notifications_delivered_total` |
| **SLI-NOT-3 OTP** | ratioMetric | OTP доставлен ≤ 30 с | Все запросы OTP | Метрика адаптера + DLR |
| **SLI-NOT-4 USSD** | ratioMetric | Ответ USSD-меню ≤ 2 с (у оператора тайм-аут сессии около 180 с, но каждое меню должно быть быстрым) | Все USSD-запросы | `ussd_response_duration_bucket` |

## SLO — целевые значения

| SLI | Цель | Окно | Бюджет ошибок |
|---|---|---|---|
| SLI-NOT-1 | **99%** | 28 дней | 1% сообщений позже 60 с |
| SLI-NOT-2 | **95%** | 7 дней | 5%: зависит от сети оператора и DND-фильтров |
| SLI-NOT-3 | **98%** | 7 дней | 2% |
| SLI-NOT-4 | **99%** < 2 с | 28 дней | 1% |

Уведомления асинхронны: сбой шлюза не останавливает оформление заказа (Bulkhead). Поэтому доступность «приёма в очередь» = доступности монолита, а SLO задаётся по **своевременности и доставке**, а не по аптайму.

```yaml
apiVersion: openslo/v1
kind: SLO
metadata:
  name: notifications-timeliness
  displayName: Уведомления — передача шлюзу за 60 с
spec:
  service: notifications
  indicator:
    metadata: { name: sent-within-60s }
    spec:
      ratioMetric:
        counter: true
        good:  { metricSource: { type: Prometheus, spec: { query: 'sum(rate(notifications_sent_total{kind="transactional",within_60s="true"}[5m]))' } } }
        total: { metricSource: { type: Prometheus, spec: { query: 'sum(rate(notifications_sent_total{kind="transactional"}[5m]))' } } }
  timeWindow: [ { duration: 28d, isRolling: true } ]
  budgetingMethod: Occurrences
  objectives: [ { displayName: Своевременность, target: 0.99 } ]
```

## SLA — что гарантируется и что при нарушении

| Кому | Обещание | При нарушении |
|---|---|---|
| CEO и операции (внутренний SLA, ниже SLO) | 98% уведомлений о заказе переданы оператору за 60 с; 90% доставлены за 5 мин | Пост-мортем; переключение канала SMS ↔ WhatsApp |
| Продавцы без кабинета | Заказ приходит в WhatsApp ≤ 5 мин; без подтверждения за 30 мин — дубль по SMS и звонок оператора | Ручная эскалация бэк-офисом |
| Маркетинг | Маркетинговые рассылки — **только при записи согласия** (A3 п.2), без SLO по скорости | Блокировка отправки без согласия — техническая, не обходится |

## Механизмы

Outbox → очередь (SQS; Kafka — по триггеру ADR-001, по плану в Г2). Уведомления на номера +234 отправляет воркер ячейки NG — номер не покидает Нигерию через ядро ([ADR-003](../../Task4/adr-003-data-residency.md)). Retry с экспоненциальной задержкой и jitter (5 попыток), затем fallback на второй канал: SMS ↔ WhatsApp. Дедупликация по `event_id`. Шаблоны WhatsApp утверждаются у Meta заранее (до 01.10). Rate limit под лимиты BSP. Подробно — [fmea.md](../fmea.md).

## Assumptions

- **AS-53.** Тайм-аут USSD-сессии у операторов — около 180 с, поэтому каждое меню должно отвечать ≤ 2 с, чтобы весь сценарий укладывался в сессию.
- **AS-54.** Доля доставленных SMS (DLR) зависит от DND-фильтров операторов Нигерии — отсюда SLO доставки 95%, а не 99%.
