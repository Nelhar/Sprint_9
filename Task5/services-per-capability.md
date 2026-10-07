# Сервисы по capability

**Дата (время кейса):** 2026-08-31. На MVP «сервис» — это **модуль модульного монолита** со своей схемой БД ([ADR-001](../Task2/adr-001-architecture-style.md)). Колонка «Когда выделяется» показывает переход к отдельному сервису ([transition-architecture.md](transition-architecture.md)).

**Владельцы — роли команды из шести контракторов** ([team-structure.md](team-structure.md)): **TL** — Tech Lead / backend; **BE-1** — backend: каталог, уведомления; **BE-2** — backend: интеграции; **MOB** — Flutter; **FE** — бэк-офис и веб; **SRE** — платформа и QA. Бизнес-владелец указан в скобках.

| Capability | Продукт / сервис (модуль) | Владелец | Внешняя зависимость | Когда выделяется |
|---|---|---|---|---|
| 1.1 Онбординг и KYC продавцов | `sellers` + KYC-адаптер | FE / BE-2 (CEO) | Smile ID или Youverify (NIN, BVN, KRA PIN) | По триггеру ADR-001 (план — Г2+) |
| 1.2 Каталог и медиа | `catalog` + конвейер изображений (WebP, 3 размера) | BE-1 | S3, CloudFront | По триггеру ADR-001 (план — Г2+) |
| 1.3 Ценообразование и промо | `catalog.pricing` | BE-1 (CEO) | — | — |
| 1.4 Модерация и снятие контента | `backoffice` (OSS-админка) | FE | — | — |
| 2.1 Диплинки и атрибуция | `app` + App Links / Universal Links + сервис отложенных диплинков | MOB (маркетинг) | Branch или AppsFlyer OneLink; сторы (проверка доменов) | — |
| 2.2 Согласия и рассылки | `identity.consent` + `notifications` | TL (DPO) | Africa's Talking, Meta BSP | Вместе с `notifications` |
| 2.3 Лояльность и рефералы | `loyalty` | BE-1 (маркетинг) | — | 6 мес. — модуль |
| 3.1 Каталог для покупателя (офлайн) | Мобильное приложение (Flutter) | MOB | App Store, Google Play | — |
| 3.2 Поиск | `catalog.search` (PostgreSQL pg_trgm) | BE-1 | → OpenSearch / Typesense (12 мес.) | Модуль остаётся; внешний движок — 12 мес. или > 50 тыс. SKU |
| 3.3 Рекомендации | `catalog.reco` (правила) | BE-1 | — | 12+ мес. |
| 4.1 Корзина и оформление | `ordering` | TL (CEO) | — | 12+ мес. (последним — ядро) |
| 4.2 Приём платежей | `payments` + адаптеры PSP (в ядре — KE; в ячейке NG — `worker-ng`) | TL / BE-2 (CFO) | M-Pesa Daraja, Paystack, Flutterwave; Ozow (6 мес.) | **Г2, Q4 2027** (сервис со своей БД, по триггеру) |
| 4.3 Флеш-распродажи и резерв | `ordering.inventory` | TL | — | — |
| 5.1 Передача отправок | `fulfillment` + адаптеры перевозчиков | BE-2 (CEO) | Sendbox + запас GIG Logistics (NG), перевозчик KE + second-source | По триггеру ADR-001 (план — Г2+) |
| 5.2 Сеть ПВЗ и выдача | `fulfillment.pickup` | BE-2 | ПВЗ Sendbox, Pickup Mtaani | — |
| 5.3 Track & trace | `fulfillment.tracking` | BE-2 | Вебхуки перевозчиков | По триггеру ADR-001 (план — Г2+) |
| 5.4 Возвраты | `backoffice.returns` → `returns` | FE → BE-2 (CFO) | Перевозчики (обратная доставка) | 12 мес. — модуль |
| 6.1 Выплаты продавцам | `payments.payouts` | TL (CFO) | M-Pesa B2C (KE), Paystack и Flutterwave Transfers (NG) | Г2, Q4 2027 (вместе с `payments`) |
| 6.2 Сверка и учёт | `payments.reconciliation` (ежедневный джоб) | TL (CFO) | Выписки PSP | Г2, Q4 2027 (вместе с `payments`) |
| 7.1 Поддержка | Helpdesk SaaS | Операции (CEO) | Helpdesk с WhatsApp-входом | — |
| 7.2 Споры и антифрод | `risk` (правила) | TL | Риск-движки PSP | По триггеру ADR-001 (план — Г2+) |
| 7.3 Отзывы | `reviews` | BE-1 | — | 6 мес. — модуль |
| 8.1 Мобильное приложение | Flutter-приложение (Android + iOS) | MOB | Сторы, FCM/APNs, Crashlytics | — |
| 8.2 SMS / USSD | `notifications.ussd` | BE-1 | Africa's Talking | **6 мес.** (с `notifications`) |
| 8.3 WhatsApp для продавцов | `notifications.whatsapp` | BE-1 | WhatsApp Cloud API через BSP | **6 мес.** |
| 8.4 Партнёрский API (B2B) | `partner-api` | BE-2 (CEO) | — | 12 мес. — отдельный сервис |
| 9.1 Идентификация и резидентность | `identity` (OTP, маршрутизатор резидентности, PII-хранилище) + ячейка `cell-ng` | TL (DPO) | AWS Local Zone Лагос, MTN Cloud, OpenBao | Ячейка — с MVP |
| 9.2 Аналитика и дашборды | Read replica + Grafana | SRE (CEO, инвестор) | Grafana Cloud | — |
| 9.3 Комплаенс | Процессы + реестр обработок | Architect (DPO, юрист) | NDPC, ODPC, Information Regulator | — |
| — Платформа (сквозное) | EKS, Terraform, Argo CD, OTel | SRE | AWS, GCP (DR), GitHub, Grafana Cloud | — |

## Assumptions

- **AS-59.** Роли шести контракторов (TL, BE-1, BE-2, MOB, FE, SRE) — проектное допущение; реальные профили контракторов сверяются в первую неделю, роли перераспределяются без изменения архитектуры.

**Нагрузка на роли.** Больше всего внешних зависимостей у TL и BE-2 (платежи, логистика). Поэтому на них — первые учения FMEA, а сопровождение M-Pesa и Flutterwave дублируется: у каждого адаптера два владельца знаний — TL и BE-2.
