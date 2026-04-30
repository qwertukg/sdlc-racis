# SDLC RACI Matrix

## Обозначения

- **R** – Responsible (исполняет)
- **A** – Accountable (несет ответственность, один!)
- **C** – Consulted (консультируется до)
- **I** – Informed (уведомляется после)
- **S** – Support (помогает)

---

## Матрица

| Роль / Этап | Проектирование | Кодинг | Тестирование | Доставка | Эксплуатация |
|---|---|---|---|---|---|
| **Business Owner (BO)** | Business Requirements<sup>A</sup><br>Acceptance Criteria<sup>A</sup> |  |  | Release (go-live)<sup>I</sup> | Monitoring<sup>I</sup> |
| **Architect / Analyst (AR/AN)** | Business Requirements<sup>R</sup><br>Acceptance Criteria<sup>R</sup><br>HLD<sup>AR</sup><br>LLD<sup>C</sup> | API Contract<sup>AC</sup><br>Code<sup>C</sup> | Security Testing<sup>C</sup> |  |  |
| **Tech Lead (TL)** | LLD<sup>AR</sup> | Code<sup>A</sup><br>Unit Tests<sup>A</sup><br>Dev Documentation<sup>A</sup><br>Runbook<sup>A</sup><br>API Contract<sup>R</sup> | Auto Tests<sup>C</sup> | Release (merge)<sup>C</sup> | Post-release Support<sup>A</sup> |
| **Developer (DEV)** | LLD<sup>R</sup> | Code<sup>R</sup><br>Unit Tests<sup>R</sup><br>Dev Documentation<sup>R</sup><br>Runbook<sup>R</sup><br>API Contract<sup>R</sup> | Auto Tests<sup>S</sup> |  | Post-release Support<sup>R</sup> |
| **QA (QA + AQA)** | Acceptance Criteria<sup>R</sup> | Unit Tests<sup>C</sup> | Auto Tests<sup>AR</sup><br>Security Testing<sup>C</sup> |  | Post-release Support<sup>R</sup><br>Monitoring<sup>C</sup> |
| **DevOps (DO)** |  | Code<sup>S</sup><br>CI/CD Pipeline<sup>AR</sup> | Auto Tests<sup>S</sup><br>Security Testing<sup>S</sup> | Release (deploy)<sup>R</sup> | Monitoring<sup>AR</sup><br>Post-release Support<sup>R</sup> |
| **AppSec (AS)** | LLD<sup>C</sup> | Code<sup>C</sup><br>API Contract<sup>C</sup> | Security Testing<sup>AR</sup> |  | Monitoring<sup>C</sup> |
| **Release Manager (RM)** |  |  |  | Release (go-live)<sup>A</sup> |  |

---

# Краткие требования к артефактам

## Business Requirements
- бизнес-цель и ценность
- KPI
- границы задачи

## Acceptance Criteria
- проверяемость
- edge cases
- отсутствие неоднозначности

## HLD
- архитектура
- интеграции
- контракты
- диаграммы

## LLD
- дизайн сервисов
- модели данных
- взаимодействие компонентов

## Code
- контейнеризация
- stateless
- секреты вне кода
- масштабируемость

## Unit Tests
- покрытие (Sonar)
- CI запуск
- quality gates

## API Contract
- OpenAPI / Swagger
- обратная совместимость
- актуальность

## Dev Documentation
- README
- onboarding
- как развивать систему

## Runbook
- запуск
- диагностика
- восстановление

## Auto Tests
- CI запуск
- изоляция
- контейнеризация

## Security Testing
- SAST
- DAST
- ручная проверка

## CI/CD Pipeline
- сборка
- тесты
- деплой
- воспроизводимость

## Release
- все тесты зелёные
- rollback
- smoke-check
- release notes
- go/no-go

## Monitoring
- метрики (latency, errors)
- логи
- алерты
- дашборды

## Post-release Support
- инциденты
- багфиксы
- стабилизация

---

# Правила

- у каждого артефакта **один A**
- нет A → нет владельца
- DevOps отвечает за платформу, не за бизнес-логику
- QA отвечает за качество, не за код
- Tech Lead отвечает за целостность решения
