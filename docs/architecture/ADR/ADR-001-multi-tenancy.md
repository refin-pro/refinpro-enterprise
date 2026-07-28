# ADR-001: Estratégia de Multi-Tenancy

- **Status:** Accepted
- **Date:** 2026-07-28
- **Decision Owners:** REFINPRO Enterprise Architecture
- **Scope:** Plataforma SaaS
- **Related Domains:** Company, User, Customer, LoanContract, Security, Audit

---

## 1. Context

O REFINPRO Enterprise será desenvolvido como uma plataforma SaaS para gerenciamento de contratos de empréstimos.

A plataforma poderá atender múltiplas empresas clientes (tenants), mantendo os dados de cada organização logicamente isolados.

Cada tenant poderá possuir:

- Usuários;
- Perfis;
- Permissões;
- Clientes/devedores;
- Contratos;
- Parcelas;
- Pagamentos;
- Anexos;
- Registros de auditoria.

A estratégia de multi-tenancy deve oferecer:

- Isolamento seguro entre tenants;
- Escalabilidade;
- Boa eficiência operacional;
- Baixo custo inicial de infraestrutura;
- Facilidade de manutenção;
- Compatibilidade com PostgreSQL;
- Evolução futura para arquiteturas de maior isolamento;
- Suporte à auditoria e rastreabilidade.

---

## 2. Decision Drivers

A decisão será orientada pelos seguintes critérios:

1. Segurança e isolamento de dados;
2. Complexidade operacional;
3. Custo de infraestrutura;
4. Facilidade de desenvolvimento;
5. Facilidade de manutenção;
6. Escalabilidade;
7. Backup e recuperação;
8. Observabilidade;
9. Evolução futura;
10. Compatibilidade com PostgreSQL.

---

## 3. Options Considered

### Option A: Shared Database + Shared Schema + tenant_id

Todos os tenants utilizarão o mesmo banco de dados e as mesmas tabelas.

Cada entidade pertencente a um tenant possuirá um identificador:

```text
tenant_id