---
title: "ðŸ§  TW Network â€” Super-Vault Mestre (MOC)"
aliases:
  - "MOC Geral"
  - "Home"
  - "Super-Vault"
  - "Index"
tags:
  - tw/moc
  - tw/hub
  - type/dashboard
updated: 2026-11-05
---

# ðŸ§  TW Network â€” Super-Vault Mestre (MOC)

> [!ABSTRACT] **Segundo CÃ©rebro Unificado do Ecossistema TW Network**
> Este cofre centraliza toda a inteligÃªncia tÃ©cnica, engenharia reversa, game design, esquemas de banco de dados, infraestrutura em nuvem e regras de plugins da rede **TW Network** (Servidor de Minecraft RankUP & Plataforma Web E-Commerce).

---

## ðŸ—ºï¸ VisÃ£o Integrada do Grafo (Graph Hub)

```mermaid
graph TD
    MOC["ðŸ§  Super-Vault Mestre"]

    %% 3 Pilares Principais
    MOC --> WEB["ðŸŒ 01 - Web & Loja"]
    MOC --> JAVA["ðŸ§© 02 - Plugins Java"]
    MOC --> GAME["ðŸŽ® 03 - Servidor & Game Loop"]
    MOC --> DIARIO["ðŸ“… 04 - DiÃ¡rio de Bordo"]

    %% ConexÃµes do Web
    WEB --> DB["ðŸ—„ï¸ [[Neon PostgreSQL]]"]
    WEB --> MP["ðŸ’³ [[Mercado Pago SDK]] & [[Fluxo Pix]]"]
    WEB --> SEC["ðŸ›¡ï¸ [[Seguranca e Hardening]]"]
    WEB --> INFRA["â˜ï¸ [[Render Web Service]]"]

    %% ConexÃµes do Java
    JAVA --> CORE["âš™ï¸ [[02-CORE-MODULE|tw-core]]"]
    JAVA --> RANKS["ðŸ† [[04-RANKS-MODULE|tw-ranks]]"]
    JAVA --> MINAS["â›ï¸ [[05-MINAS-MODULE|tw-minas]]"]
    JAVA --> ECO["ðŸ’° [[03-ECONOMIA-MODULE|tw-economia]]"]

    %% ConexÃµes do Game Loop
    GAME --> PRECOS["ðŸ’Ž [[tabela_precos|Tabela de PreÃ§os]]"]
    GAME --> JORNADA["ðŸ—ºï¸ [[jornada_jogador|Jornada do Jogador]]"]
    GAME --> MUNDOS["ðŸŒ [[mundo_lobby|Mundos & Arenas]]"]
    GAME --> CMDS["âŒ¨ï¸ [[MOC_Comandos|Comandos da Rede]]"]

    %% Pontes de IntegraÃ§Ã£o Cruzada
    DB -. Sincronia de VIPs e Cash .-> CORE
    RANKS -. LiberaÃ§Ã£o de Vantagens .-> MP
    ECO -. Tabela de PreÃ§os .-> PRECOS
```

---

## ðŸ§­ Clusters de Conhecimento

### ðŸŒ 1. [[00 - MOC (Map of Content)|Plataforma Web & E-Commerce]]
*DocumentaÃ§Ã£o do frontend React 19, backend Express 5 e banco de dados na nuvem.*
* **Arquitetura & SeguranÃ§a:** [[Tech Stack]] â€¢ [[Seguranca e Hardening]] â€¢ [[Autenticacao e Contas]]
* **Banco de Dados Relacional (Neon):** [[Neon PostgreSQL]] â€¢ [[Tabela Usuarios]] â€¢ [[Tabela Pedidos]] â€¢ [[Tabela Cupons]]
* **Pagamentos Automatizados:** [[Mercado Pago SDK]] â€¢ [[Fluxo Pix]]
* **Nuvem & Infraestrutura:** [[Render Web Service]] â€¢ [[Render Blueprint render.yaml]] â€¢ [[Variaveis de Ambiente]] â€¢ [[Configs de Servidor Nginx e Docker]]
* **Identidade Visual Minecraft:** [[Texturas e Icones Minecraft]] â€¢ [[Design System e Componentes]]

---

### ðŸ§© 2. [[00-ROUTER-AND-TAXONOMY|Engenharia de Plugins Java (Purpur 26.3 & Java 25)]]
*DocumentaÃ§Ã£o tÃ©cnica dos 9 mÃ³dulos proprietÃ¡rios da suÃ­te `tw-*` construÃ­dos em Maven.*
* **Diretrizes de Engenharia:** [[01-ARCHITECTURE-AND-CORE-RULES|Regras de Arquitetura, ConcorrÃªncia e PDC]]
* **MÃ³dulos do Sistema:**
  * [[02-CORE-MODULE|tw-core]] â€” FundaÃ§Ã£o, HikariCP, TWUser, menus e TextDisplay
  * [[03-ECONOMIA-MODULE|tw-economia]] â€” Saldos (Money/Tokens/Souls), boosters e cheques
  * [[04-RANKS-MODULE|tw-ranks]] â€” ProgressÃ£o A-Z, prestÃ­gios e correio
  * [[05-MINAS-MODULE|tw-minas]] â€” Central de minas, oficina, cartinhas e meteorito
  * [[06-TERRENOS-MODULE|tw-terrenos]] â€” AgÃªncia de lotes, voo protegido e compras atÃ´micas
  * [[07-MAQUINAS-MODULE|tw-maquinas]] â€” Geradores em bloco, combustÃ­vel e saque transacional
  * [[08-SPAWNERS-MODULE|tw-spawners]] â€” Geradores atÃ© 10k, modo virtual vs fÃ­sico e almas
  * [[09-FARMS-MODULE|tw-farms]] â€” PlantaÃ§Ãµes no plot, silos virtuais e enxadas em Ã¡rea
  * [[10-CAIXAS-MODULE|tw-caixas]] â€” Chaves virtuais, pity, roleta e consumÃ­veis
* **Cookbook de Desenvolvimento:** [[11-FEATURE-COOKBOOK|Feature Cookbook]]

---

### ðŸŽ® 3. [[MOC_Geral|Servidor, Economia & Game Loop]]
*ConfiguraÃ§Ãµes in-game, balanceamento econÃ´mico, menus e comandos do servidor.*
* **Centrais MOC:** [[MOC_Sistemas]] â€¢ [[MOC_Economia]] â€¢ [[MOC_Mundos]] â€¢ [[MOC_Comandos]] â€¢ [[MOC_Interacoes]]
* **Economia & Mercado:** [[tabela_precos|Tabela de PreÃ§os]] â€¢ [[fluxo_monetario|Fluxo MonetÃ¡rio]] â€¢ [[boosters_multiplicadores|Boosters]]
* **Game Loop & Gameplay:** [[jornada_jogador|Jornada do Jogador]] â€¢ [[combate_pvp|Combate PvP]]
* **Mundos:** [[mundo_lobby|Lobby Spawn]] â€¢ [[mundo_minas|Mundo Minas]] â€¢ [[mundo_terrenos|Terrenos PlotSquared]] â€¢ [[mundo_mina_pvp|Arena PvP]]
* **Comandos:** [[comandos_jogadores|Jogadores]] â€¢ [[comandos_economia|Economia]] â€¢ [[comandos_staff|Staff]] â€¢ [[comandos_admin|Admin]]

---

### ðŸ“… 4. DiÃ¡rio de Bordo & DecisÃµes HistÃ³ricas
*Registro cronolÃ³gico de evoluÃ§Ã£o do ecossistema:*
* [[2026-11-03 - Redesign Frontend e Seguranca]]
* [[2026-11-05 - Setup Neon e Deploy no Render]]
* [[2026-11-05 - Criacao do Super Vault Unificado]]
* [[2026-11-05 - Sincronizacao Frontend com Game Loop e Ranks]]
* [[2026-11-05 - Remocao de Contas Demo e Hardening de Producao]]
* [[2026-11-05 - Protocolo Estrito de Memoria e Vault-First]]
* [[2026-11-05 - Auditoria e Refatoracao de Design Area de Contas]]
* [[2026-11-06 - Redesign Mobile-First Painel de Perfil]]

---

> [!TIP] Dica de NavegaÃ§Ã£o no Obsidian
> Pressione **`Ctrl + G`** para abrir o **Graph View**. Os nÃ³s estÃ£o agrupados por cor: Ciano para Web, Verde para Plugins Java e Dourado para Game Loop/Economia!
