---
tags:
  - diario
  - changelog
  - arquitetura
  - vault
  - git-submodule
created: 2026-11-05
---

# 📅 2026-11-05 — Criação do Super-Vault Unificado da TW Network

> Registro da unificação dos 3 cofres de documentação (Site, Plugins Java e Servidor Minecraft) em um repositório centralizado de conhecimento e ligação via Git Submodule.

Voltar para o [[00 - MOC (Map of Content)]].

---

## 🚀 Motivação & Arquitetura

Antes desta iniciativa, o conhecimento da rede estava fragmentado em 3 locais:
1. `twnetworksite/vault` (Web, Loja e Neon DB)
2. `TW-Plugin/.vault` (Plugins Java e 9 módulos Maven)
3. `TW_Network_Lastest/docs/rag` (Gameplay, comandos e mundos)

Essa divisão dificultava a visualização em grafo (`Ctrl + G`) no Obsidian e causava dessincronização de regras (como preços de VIPs na loja versus privilégios in-game).

### 🛠️ Entregas Realizadas:

1. **Repositório Centralizado:**
   - Criação do repositório [`Da6-Dev/tw-vault`](https://github.com/Da6-Dev/tw-vault) no GitHub.
   - Consolidação de todas as notas sob uma taxonomia de 4 pilares:
     - `01 - Web e Loja`
     - `02 - Plugins Java`
     - `03 - Servidor e Game Loop`
     - `04 - Diario de Bordo`
2. **Mapa de Conteúdo Mestre:**
   - Elaboração do [[00 - MOC (Map of Content)]] com links cruzados e diagrama de fluxo em Mermaid.
3. **Distribuição via Git Submodule:**
   - Integração do `tw-vault` nos 3 repositórios da rede (`twnetworksite`, `TW-Plugin` e `TW_Network_Lastest`), garantindo que qualquer alteração de documentação seja sincronizada para todos.
