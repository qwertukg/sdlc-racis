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
| **Менеджмент** | [Business Requirements](#business-requirements)<sup>A</sup><br>[Acceptance Criteria](#acceptance-criteria)<sup>A</sup> |  |  | [Release](#release)<sup>A</sup> | [Monitoring](#monitoring)<sup>I</sup><br>[Post-release Support](#post-release-support)<sup>I</sup> |
| **Аналитика** | [Business Requirements](#business-requirements)<sup>R</sup><br>[Acceptance Criteria](#acceptance-criteria)<sup>R</sup><br>[HLD](#hld)<sup>AR</sup><br>[LLD](#lld)<sup>C</sup> | [API Contract](#api-contract)<sup>AC</sup><br>[Code](#code)<sup>C</sup> | [Security Testing](#security-testing)<sup>C</sup> | [Release](#release)<sup>C</sup> | [Monitoring](#monitoring)<sup>C</sup> |
| **Тимлиды** | [LLD](#lld)<sup>AR</sup> | [Code](#code)<sup>A</sup><br>[Unit Tests](#unit-tests)<sup>A</sup><br>[Dev Documentation](#dev-documentation)<sup>A</sup><br>[Runbook](#runbook)<sup>A</sup><br>[API Contract](#api-contract)<sup>R</sup> | [Auto Tests](#auto-tests)<sup>C</sup> | [Release](#release)<sup>R</sup> | [Post-release Support](#post-release-support)<sup>A</sup><br>[Monitoring](#monitoring)<sup>C</sup> |
| **Разработчики** | [LLD](#lld)<sup>R</sup> | [Code](#code)<sup>R</sup><br>[Unit Tests](#unit-tests)<sup>R</sup><br>[Dev Documentation](#dev-documentation)<sup>R</sup><br>[Runbook](#runbook)<sup>R</sup><br>[API Contract](#api-contract)<sup>R</sup> | [Auto Tests](#auto-tests)<sup>S</sup> | [Release](#release)<sup>R</sup> | [Post-release Support](#post-release-support)<sup>R</sup> |
| **QA** | [Acceptance Criteria](#acceptance-criteria)<sup>R</sup> | [Unit Tests](#unit-tests)<sup>C</sup> | [Auto Tests](#auto-tests)<sup>AR</sup><br>[Security Testing](#security-testing)<sup>C</sup> | [Release](#release)<sup>C</sup> | [Post-release Support](#post-release-support)<sup>R</sup><br>[Monitoring](#monitoring)<sup>C</sup> |
| **DevOps** |  | [Code](#code)<sup>S</sup><br>[CI/CD Pipeline](#cicd-pipeline)<sup>AR</sup> | [Auto Tests](#auto-tests)<sup>S</sup><br>[Security Testing](#security-testing)<sup>S</sup> | [Release](#release)<sup>R</sup> | [Monitoring](#monitoring)<sup>AR</sup><br>[Post-release Support](#post-release-support)<sup>R</sup> |
| **AppSec** | [LLD](#lld)<sup>C</sup> | [Code](#code)<sup>C</sup><br>[API Contract](#api-contract)<sup>C</sup> | [Security Testing](#security-testing)<sup>AR</sup> | [Release](#release)<sup>C</sup> | [Monitoring](#monitoring)<sup>C</sup> |

---

# Краткие требования к артефактам

## Business Requirements
<a id="business-requirements"></a>

- бизнес-цель и ценность
- KPI
- границы задачи
- основные ограничения и допущения

## Acceptance Criteria
<a id="acceptance-criteria"></a>

- проверяемость
- edge cases
- отсутствие неоднозначности
- явные критерии приемки

## HLD
<a id="hld"></a>

- архитектура решения
- интеграции и внешние зависимости
- контракты и интерфейсы
- архитектурные диаграммы
- нефункциональные требования

## LLD
<a id="lld"></a>

- дизайн сервисов и модулей
- модели данных
- взаимодействие компонентов
- ключевые технические решения

## Code
<a id="code"></a>

- контейнеризация
- stateless-подход
- секреты вне кода
- масштабируемость
- отсутствие запуска от root
- healthcheck без зависимости от пула основного процесса

## Unit Tests
<a id="unit-tests"></a>

- покрытие в SonarQube
- запуск в CI
- соответствие quality gates

## API Contract
<a id="api-contract"></a>

- OpenAPI / Swagger
- обратная совместимость
- актуальность спецификации
- описание ошибок и основных сценариев

## Dev Documentation
<a id="dev-documentation"></a>

- README
- onboarding для нового инженера
- как расширять и дорабатывать систему

## Runbook
<a id="runbook"></a>

- запуск
- диагностика
- восстановление
- базовые операционные сценарии

## Auto Tests
<a id="auto-tests"></a>

- запуск из CI/CD
- изоляция
- контейнеризация
- воспроизводимость окружения

## Security Testing
<a id="security-testing"></a>

- SAST
- DAST
- ручная проверка логики и типовых уязвимостей

## CI/CD Pipeline
<a id="cicd-pipeline"></a>

- сборка
- тесты
- деплой
- воспроизводимость
- прозрачность статусов

## Release
<a id="release"></a>

- все тесты зелёные
- актуальные HLD / LLD / документация
- rollback plan
- smoke-check
- release notes
- go / no-go решение

## Monitoring
<a id="monitoring"></a>

- метрики (latency, errors, saturation)
- логи
- алерты
- дашборды
- health probes

## Post-release Support
<a id="post-release-support"></a>

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
- Аналитика отвечает за требования, верхнеуровневое описание решения и согласованность постановки
