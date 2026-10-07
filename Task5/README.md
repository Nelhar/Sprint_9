# Task5 — MVP Roadmap и решения Build / Buy / Partner

| Файл | Содержание |
|---|---|
| [capability-map.md](capability-map.md) | Иерархия: 9 capabilities L1 и 29 — L2; таблица: решение Build/Buy/Partner, обоснование, стоимость, риск; расчёт отказа от своей логистики и своей платёжной оркестрации |
| [value-stream.puml](value-stream.puml) / [value-stream.png](value-stream.png) | Value Stream «покупатель получил товар — продавец получил деньги» с нанесёнными capabilities |
| [services-per-capability.md](services-per-capability.md) | capability → модуль/сервис → владелец → внешняя зависимость → когда выделяется |
| [roadmap.md](roadmap.md) + [roadmap.puml](roadmap.puml) / [roadmap.png](roadmap.png) | Mermaid и PlantUML Gantt; 4 контрольные точки (scope, команда, стоимость инфраструктуры); ёмкость 43 из 48 чел-нед; отбор 29 функций по критерию К1–К4 |
| [adr-004-payment-provider.md](adr-004-payment-provider.md) | ADR-004: мульти-PSP (M-Pesa напрямую; в NG Paystack основной, Flutterwave резерв; Ozow в ZA), география провайдеров, комиссия ≈ 1,8% с НДС ≤ 2,5% GMV |
| [transition-architecture.md](transition-architecture.md) | Сейчас → MVP → 6 мес. → 12 мес. по слоям; Strangler Fig; временные компоненты и условия их удаления |
| [risk-register.md](risk-register.md) | 15 рисков: вероятность, влияние, митигация, владелец, измеримый триггер |
| [team-structure.md](team-structure.md) | Оргструктура (2 потока + платформа), офис в Найроби или удалённо, дежурства 24/7 при 6 контракторах |

**Коротко.** В MVP — **8 из 29** функций (урезанные), 6 закрыты партнёрами или ручным процессом, 11 — через 6–12 месяцев, 4 — не делаем. Своя логистика окупается от ~760 тыс. доставок в год только на ПО, без курьерской операции; прямой эквайринг — от GMV карт > $50 млн/год. Оба варианта пересматриваются через 12 месяцев по триггерам.
