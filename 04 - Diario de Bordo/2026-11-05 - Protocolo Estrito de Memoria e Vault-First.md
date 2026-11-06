---
tags:
  - diario
  - changelog
  - governanca
  - agentes
  - vault
created: 2026-11-05
---

# 📅 2026-11-05 — Protocolo Estrito de Memória e Diretriz Vault-First

> Registro do endurecimento das diretrizes de engenharia de IA: adoção obrigatória do princípio Vault-First no início de cada tarefa e da sincronização automática do Vault a cada commit.

Voltar para o [[00 - MOC (Map of Content)]].

---

## 🚀 Resumo das Entregas

### 1. Diretriz Vault-First (Lei Zero)
* **Regra Estabelecida no `AGENTS.md` e `.cursorrules`:** Proibição de inspecionar ou varrer arquivos do projeto às cegas.
* **Fluxo Inicial Mandatório:** O agente deve sempre iniciar consultando o índice mestre em [[00 - MOC (Map of Content)]] e lendo as notas técnicas relacionadas antes de tomar qualquer decisão ou modificar arquivos.

### 2. Ciclo de Auto-Alimentação da Memória
* **Regra Estabelecida:** Nenhuma tarefa ou commit pode ser finalizado sem que:
  1. A respectiva nota técnica do subsistema em `vault/` seja atualizada.
  2. Seja criada ou enriquecida a entrada diária no `04 - Diario de Bordo`.
  3. Seja preservado o grafo do Obsidian no `00 - MOC`.
  4. O submódulo `vault/` seja commitado e enviado primeiro (`push origin main`), seguido pelo commit do repositório pai.

---

## 🔗 Referências Bidirecionais
- [[00 - MOC (Map of Content)|MOC Principal]]
- [[Seguranca e Hardening|Diretrizes de Segurança e Hardening]]
- [[Autenticacao e Contas|Autenticação e Contas]]
