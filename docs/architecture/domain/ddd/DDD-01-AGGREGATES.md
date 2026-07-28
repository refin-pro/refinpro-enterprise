# DDD-01: Aggregates and Consistency Boundaries

- **Status:** Draft
- **Version:** 0.1
- **Date:** 2026-07-28
- **Scope:** Domain-Driven Design
- **Related Documents:**
  - ADR-001 - Multi-Tenancy
  - REFINPRO-DOMAIN-MODEL

---

# 1. Purpose

Este documento define os Aggregates iniciais do domínio do REFINPRO Enterprise.

Um Aggregate representa um limite de consistência transacional do domínio.

Cada Aggregate deverá possuir uma única Aggregate Root.

Objetivos:

- Definir limites de consistência;
- Reduzir acoplamento entre entidades;
- Evitar agregados excessivamente grandes;
- Garantir invariantes de negócio;
- Definir referências entre agregados;
- Preparar os contratos de repositório.

---

# 2. Aggregate Design Principles

O REFINPRO adotará os seguintes princípios:

1. Cada Aggregate possui uma única Aggregate Root;
2. Entidades externas referenciam outras Aggregates por identidade;
3. Não haverá dependência direta de objetos internos de outro Aggregate;
4. Transações deverão alterar apenas os Aggregates necessários;
5. Invariantes internas deverão ser protegidas pela Aggregate Root;
6. Consistência eventual poderá ser utilizada entre Aggregates quando apropriado;
7. Aggregates não deverão ser definidos apenas pela estrutura das tabelas.

---

# 3. Initial Aggregate Map

Os Aggregates iniciais serão:

```text
Company Aggregate
User Aggregate
Authorization Aggregate
Customer Aggregate
LoanContract Aggregate
AmortizationSchedule Aggregate
Installment Aggregate
Payment Aggregate
AuditLog Aggregate
Attachment Aggregate