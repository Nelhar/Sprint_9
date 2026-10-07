# Task4 — регуляторные ограничения и стратегия данных

| Файл | Содержание |
|---|---|
| [data-residency-map.md](data-residency-map.md) | Требования по странам (известно / допущение); Data Residency Map по шаблону курса (исправлен «Франкфурт»); регламент трансграничной передачи |
| [cloud-regions-comparison.md](cloud-regions-comparison.md) | AWS af-south-1, AWS Local Zone Лагос, GCP africa-south1, Azure SA North, MTN Cloud Лагос: сервисы, задержки, цены, SLA, оплата по счёту, вывод |
| [adr-003-data-residency.md](adr-003-data-residency.md) | ADR-003: ячейки данных по странам. Маскирование, шифрование и ключи, репликация, сроки хранения; **раздел «Обратимость и триггеры пересмотра»** |
| [c4-container.puml](c4-container.puml) / [c4-container.png](c4-container.png) | C4 Container, контейнеры сгруппированы по регионам развёртывания |
| [deployment-diagram.puml](deployment-diagram.puml) / [deployment-diagram.png](deployment-diagram.png) | Deployment (PlantUML): AZ, Local Zone, вторая площадка Нигерии, DR в GCP |
| [failover-plan.md](failover-plan.md) | HA-решение и сценарии отказа (AZ, регион, ячейка NG, CDN): кто решает, шаги, время, потери данных; учения |

**Коротко.** Консервативное допущение: все данные нигерийцев хранятся **и обрабатываются** в Нигерии (AWS Local Zone Лагос со своей точкой входа, воркером партнёров и NAT; бэкапы на MTN Cloud). DR ядра — логическая реплика RDS в Cloud SQL через Google DMS (WAL-архив из RDS недоступен). Решение обратимо: любой ответ юристов через 4–6 недель меняет конфигурацию и место развёртывания ячейки, но не код. Шифрование не используется как замена локализации.
