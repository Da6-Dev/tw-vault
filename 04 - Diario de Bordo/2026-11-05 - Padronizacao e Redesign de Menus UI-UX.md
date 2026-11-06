---
tags:
  - diario
  - changelog
  - ui-ux
  - menus
  - design-system
  - deluxemenus
  - tw-plugins
created: 2026-11-05
---

# 📅 2026-11-05 — Padronização, Redesign e Interligação de Menus (UI/UX)

> Registro completo da reestruturação e interligação de todos os menus (GUIs) do servidor, instituindo o Design System canônico, arquitetura hub-and-spoke e modelos YAML unificados.

Voltar para o [[00 - MOC (Map of Content)]] ou [[MOC_Interacoes|Central de Interações]].

---

## 🎯 1. Motivação e Objetivos

Anteriormente, os menus do servidor operavam de forma isolada e com dimensões inconsistentes (menus de 45 slots misturados com submenus heterogêneos), forçando os jogadores a memorizarem múltiplos comandos de chat e causando fricção ao navegar entre sistemas.

O objetivo desta iniciativa foi:
1. Criar um **Design System definitivo** para eliminar qualquer inconsistência visual.
2. Mapear uma **Arquitetura de Navegação contínua**, guiando a progressão do jogador do início ao fim.
3. Produzir **configurações YAML padronizadas** para o [[gui_menu_principal|DeluxeMenus]] e os módulos nativos da suíte [[00-ROUTER-AND-TAXONOMY|tw-*]].

---

## 🛠️ 2. Entregas Técnicas Realizadas

### 2.1. Design System & Guia de Estilo Visual ([[gui_design_system]])
- **Padronização de Dimensões:**
  - **54 Slots (6 linhas / 9x6):** Menus Principais, Hubs e Catálogos Extensos.
  - **27 Slots (3 linhas / 9x3):** Submenus rápidos, Diálogos de Confirmação e Painéis de Gerenciamento.
  - *Descontinuação total* de layouts arbitrários (36 ou 45 slots).
- **Molduras Consistentes:** Uso de `BLACK_STAINED_GLASS_PANE` em todas as bordas e faixas divisórias com nomes vazios (`' '`).
- **Paleta Cromática Unificada:**
  - `&#7FB4F4` (Ciano Principal) para títulos e itens nobres.
  - `&e` (Dourado) para valores, saldo (`$%vault_eco_balance_formatted%`), tokens e multiplicadores.
  - `&7` (Cinza Claro) para descrições de recursos e regras.
  - `&8` (Grafite) para prefixos de títulos (`&8➔`) e divisórias.
  - `&a` / `&c` para estados de sucesso/desbloqueado e alerta/fechamento.
- **Lore Estruturada em 3 Seções:** Topo (função) ➔ Meio (status dinâmico) ➔ Rodapé (ação de clique clara).

### 2.2. Arquitetura de Navegação Hub-and-Spoke ([[gui_arquitetura_navegacao]])
- **Hub Central (`/menu`):** Ancoragem de 54 slots com perfil do jogador no Slot 4, ranking no Slot 48, botão fechar no Slot 49 e spawn no Slot 53.
- **Conexão Direta aos 10 Sistemas:**
  - Mineração (`/minaslista`), Ranks (`/ranks`), Terrenos (`/terrenos`), Máquinas (`/maquinas`), Spawners (`/spawners`), Farms (`/farms`), Caixas (`/caixas`), Mercado (`/shop`), Kits PvP (`/kits`), Cosméticos (`/cosmetics`).
- **Botões Universais de Navegação:**
  - **Retorno ao Menu Pai:** Sempre no **Slot 45** (em 54 slots) ou **Slot 18** (em 27 slots).
  - **Fechar Menu:** Sempre no **Slot 49** (em 54 slots) ou **Slot 22** (em 27 slots).

### 2.3. Modelos YAML Implementados e Validados
- **DeluxeMenus:**
  - `plugins/DeluxeMenus/gui_menus/menus/menu.yml` (Hub Central de 54 slots).
  - `plugins/DeluxeMenus/gui_menus/menus/minas.yml` (Catálogo de 16 minas com lógica Dual-State: liberadas com teleporte vs bloqueadas com som de negação).
- **Plugins Nativos TW ([[gui_tw_plugins]]):**
  - Modelos gerados em `plugins/tw-*/menus/` para `tw-ranks`, `tw-terrenos`, `tw-maquinas`, `tw-spawners`, `tw-farms`, `tw-caixas` e `tw-minas/minas_extra.yml`.
- **Blindagem no `CommandWhitelist`:**
  - Inclusão dos comandos de navegação (`menu`, `minaslista`, `minhasminas`, `ranks`, `terrenos`, `plot`, `plots`, `p`, `maquinas`, `spawners`, `farms`, `caixas`, `shop`, `cosmetics`) para assegurar que nenhum clique resulte em bloqueio de permissão.

---

## 🧪 3. Garantia de Qualidade & Testes

A integridade do projeto foi verificada por suítes de testes automatizados e controle de qualidade adversarial:
- **Suíte E2E Canônica (`tests/e2e/test_menus.py`):** **114/114 testes aprovados**.
- **Validação Adversarial de Navegação (`tests/test_adversarial_navigation.py`):** **6/6 testes aprovados**.
- **Fuzzing & Geometria de Slots (`tests/test_adversarial_harness.py`):** **2.399 verificações aprovadas** sem colisões ou falhas.
- **Auditoria de Estresse de Grafos (`tests/adversarial_suite.py`):** **1.809 asserções aprovadas** (zero becos sem saída ou ciclos infinitos).
- **Auditoria Pós-Vitória Independente:** Veredito **APPROVE (100% verde)**.
