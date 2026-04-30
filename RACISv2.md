# SDLC RACI Matrix

## Роли

- **BO** – Business Owner / Product Owner  
- **AN** – Analyst  
- **AR** – Architect  
- **TL** – Tech Lead  
- **DEV** – Developer  
- **QA** – QA Engineer  
- **AQA** – QA Automation  
- **DO** – DevOps / Platform  
- **AS** – AppSec  
- **RM** – Release Manager / Delivery  

---

## Обозначения

- **R** – Responsible (исполняет)
- **A** – Accountable (несет ответственность, один!)
- **C** – Consulted (консультируется до)
- **I** – Informed (уведомляется после)
- **S** – Support (помогает)

---

## Матрица

| Артефакт / Этап | BO | AN | AR | TL | DEV | QA | AQA | DO | AS | RM |
|---|---|---|---|---|---|---|---|---|---|---|
| **Business Requirements** | A | R | C | I | I | I | I | I | I | I |
| **Acceptance Criteria** | A | R | C | C | I | R | I | I | I | I |
| **HLD** | I | C | A/R | C | I | I | I | I | C | I |
| **LLD** | I | C | C | A/R | R | I | I | I | C | I |
| **Code** | I | I | C | A | R | I | I | S | C | I |
| **Unit Tests** | I | I | I | A | R | C | I | I | I | I |
| **API Contract (Swagger)** | I | C | A | R | R | C | I | I | C | I |
| **Dev Documentation** | I | I | C | A | R | I | I | I | I | I |
| **Runbook / Admin Guide** | I | I | I | A | R | C | I | R | C | I |
| **Auto Tests** | I | I | I | C | S | A | R | S | I | I |
| **Security Testing (SAST/DAST)** | I | I | C | I | I | C | S | S | A/R | I |
| **CI/CD Pipeline** | I | I | I | C | S | I | I | A/R | C | I |
| **Release (go-live)** | I | I | I | C | I | C | I | R | C | A |
| **Monitoring / Alerts** | I | I | I | C | I | C | I | A/R | C | I |
| **Post-release Support** | I | I | I | A | R | R | S | R | C | I |

---

# Описание этапов и артефактов

## 1. Business Requirements

Описание бизнес-потребности.

**Требования:**
- понятная цель
- измеримый результат (KPI)
- описание ценности

**Ответственность:**
- BO – A
- Analyst – R

---

## 2. Acceptance Criteria

Критерии приемки.

**Требования:**
- проверяемость
- отсутствие неоднозначности
- покрытие happy/edge кейсов

---

## 3. HLD (High-Level Design)

Архитектура системы.

**Должно включать:**
- интеграции
- контракты
- архитектурную диаграмму
- нефункциональные требования

---

## 4. LLD (Low-Level Design)

Дизайн кода и сервисов.

**Должно включать:**
- структура сервисов
- модели данных
- взаимодействие компонентов

---

## 5. Code

Продуктовый код.

**Требования:**
- контейнеризация
- отсутствие root
- stateless
- секреты вне кода
- масштабируемость

---

## 6. Unit Tests

Тесты логики.

**Требования:**
- покрытие в SonarQube
- соответствие quality gates
- запуск в CI

---

## 7. API Contract

Контракты API.

**Требования:**
- Swagger / OpenAPI
- актуальность
- обратная совместимость

---

## 8. Документация

### Dev Documentation
- README
- как развивать систему
- onboarding

### Runbook
- как запускать
- как дебажить
- как восстанавливать

---

## 9. Auto Tests

Автотесты (UI/API).

**Требования:**
- запуск из CI
- контейнеризация
- независимость

---

## 10. Security Testing

- SAST
- DAST
- ручная проверка логики

---

## 11. CI/CD

**Должно обеспечивать:**
- сборку
- тесты
- деплой
- воспроизводимость

---

## 12. Release

Вывод в прод.

**Обязательно:**
- все тесты зелёные
- актуальные HLD/LLD
- rollout стратегия
- rollback план
- release notes
- smoke-check
- мониторинг включен

---

## 13. Monitoring

**Должно включать:**
- логи
- метрики (latency, errors)
- алерты
- дашборды

---

## 14. Post-release Support

- обработка инцидентов
- багфиксы
- стабилизация

---
