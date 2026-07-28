# REFINPRO Enterprise - Domain Model

- **Status:** Draft
- **Version:** 0.1
- **Date:** 2026-07-28
- **Scope:** Core Domain
- **Related ADR:** ADR-001 - Multi-Tenancy

---

# 1. Purpose

Este documento define o modelo conceitual inicial do domínio do REFINPRO Enterprise.

O objetivo é estabelecer:

- Entidades;
- Agregados;
- Value Objects;
- Relacionamentos;
- Responsabilidades;
- Regras de negócio;
- Limites de consistência;
- Conceitos financeiros centrais.

Este documento representa o domínio conceitual e não deve ser interpretado como uma definição final do banco de dados.

A implementação persistente será definida posteriormente através do modelo relacional e do Prisma Schema.

---

# 2. Domain Overview

O REFINPRO Enterprise é uma plataforma SaaS para gerenciamento de contratos de empréstimos e seus respectivos ciclos financeiros.

O fluxo principal do domínio é:

```text
Company
   │
   ▼
Customer
   │
   ▼
LoanContract
   │
   ▼
Installment
   │
   ▼
Payment

# 27. Financial Domain Decisions

## 27.1 Payment Allocation

Um pagamento poderá ser alocado em uma ou mais parcelas.

## 27.2 Renegotiation

Uma renegociação deverá preservar o contrato original e criar um novo contrato relacionado.

## 27.3 Financial Position Calculation

A posição financeira será calculada considerando uma data de referência.

O sistema não deverá depender de atualizações diárias persistidas exclusivamente pela passagem do tempo.

## 27.4 Amortization Schedule Versioning

Cronogramas de amortização deverão ser preservados.

Alterações relevantes deverão gerar uma nova versão do cronograma ou um novo contrato, conforme a natureza da operação.