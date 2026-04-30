# SDLC RACI Matrix

## Обозначения

- **R** – Responsible (исполняет)
- **A** – Accountable (несет ответственность, один!)
- **C** – Consulted (консультируется до)
- **I** – Informed (уведомляется после)
- **S** – Support (оказывает поддержку)

---

## Матрица

| Отдел / Этап | Проектирование | Кодинг | Тестирование | Доставка | Эксплуатация |
|---|---|---|---|---|---|
| **Менеджмент** | Business Requirements<sup>A</sup><br>Acceptance Criteria<sup>A</sup> |  |  | Release (go-live)<sup>A</sup> | Monitoring<sup>I</sup><br>Post-release Support<sup>I</sup> |
| **Архитекторы** | Business Requirements<sup>R</sup><br>Acceptance Criteria<sup>R</sup><br>HLD<sup>AR</sup><br>LLD<sup>C</sup> | API Contract<sup>AC</sup><br>Code<sup>C</sup> | Security Testing<sup>C</sup> | Release (go-live)<sup>C</sup> | Monitoring<sup>C</sup> |
| **Тимлиды** | LLD<sup>AR</sup> | Code<sup>A</sup><br>Unit Tests<sup>A</sup><br>Dev Documentation<sup>A</sup><br>Runbook<sup>A</sup><br>API Contract<sup>R</sup> | Auto Tests<sup>C</sup> | Release (merge)<sup>R</sup><br>Release (go-live)<sup>C</sup> | Post-release Support<sup>A</sup><br>Monitoring<sup>C</sup> |
| **Разработчики** | LLD<sup>R</sup> | Code<sup>R</sup><br>Unit Tests<sup>R</sup><br>Dev Documentation<sup>R</sup><br>Runbook<sup>R</sup><br>API Contract<sup>R</sup> | Auto Tests<sup>S</sup> | Release (deploy prep)<sup>R</sup> | Post-release Support<sup>R</sup> |
| **QA** | Acceptance Criteria<sup>R</sup> | Unit Tests<sup>C</sup> | Auto Tests<sup>AR</sup><br>Security Testing<sup>C</sup> | Release (go-live)<sup>C</sup> | Post-release Support<sup>R</sup><br>Monitoring<sup>C</sup> |
| **DevOps** |  | Code<sup>S</sup><br>CI/CD Pipeline<sup>AR</sup> | Auto Tests<sup>S</sup><br>Security Testing<sup>S</sup> | Release (deploy)<sup>R</sup> | Monitoring<sup>AR</sup><br>Post-release Support<sup>R</sup> |
| **AppSec** | LLD<sup>C</sup> | Code<sup>C</sup><br>API Contract<sup>C</sup> | Security Testing<sup>AR</sup> | Release (go-live)<sup>C</sup> | Monitoring<sup>C</sup> |

---

# Краткие требования к артефактам

## Business Requirements
- бизнес-цель и ценность
- KPI
- границы задачи
- основные ограничения и допущения

## Acceptance Criteria
- проверяемость
- edge cases
- отсутствие неоднозначности
- явные критерии приемки

## HLD
- архитектура решения
- интеграции и внешние зависимости
- контракты и интерфейсы
- архитектурные диаграммы
- нефункциональные требования

## LLD
- дизайн сервисов и модулей
- модели данных
- взаимодействие компонентов
- ключевые технические решения

## Code
- контейнеризация
- stateless-подход
- секреты вне кода
- масштабируемость
- отсутствие запуска от root
- healthcheck без зависимости от пула основного процесса

## Unit Tests
- покрытие в SonarQube
- запуск в CI
- соответствие quality gates

## API Contract
- OpenAPI / Swagger
- обратная совместимость
- актуальность спецификации
- описание ошибок и основных сценариев

## Dev Documentation
- README
- onboarding для нового инженера
- как расширять и дорабатывать систему

## Runbook
- запуск
- диагностика
- восстановление
- базовые операционные сценарии

## Auto Tests
- запуск из CI/CD
- изоляция
- контейнеризация
- воспроизводимость окружения

## Security Testing
- SAST
- DAST
- ручная проверка логики и типовых уязвимостей

## CI/CD Pipeline
- сборка
- тесты
- деплой
- воспроизводимость
- прозрачность статусов

## Release
- все тесты зелёные
- актуальные HLD / LLD / документация
- rollback plan
- smoke-check
- release notes
- go / no-go решение

## Monitoring
- метрики (latency, errors, saturation)
- логи
- алерты
- дашборды
- health probes

## Post-release Support
- обработка инцидентов
- багфиксы
- стабилизация
- сопровождение после релиза

---

# Правила

- у каждого артефакта должен быть **один A**
- если у артефакта нет **A**, значит нет явного владельца
- DevOps отвечает за платформу и delivery pipeline, а не за бизнес-логику
- QA отвечает за качество и проверку, но не за разработку продуктового кода
- Тимлид отвечает за техническую целостность решения внутри команды
- Архитекторы отвечают за верхнеуровневый дизайн, согласованность требований и архитектурные ограничения
