---
title: "Diário de Bordo: 2026-11-06 - Unificação dos Menus do Plugin TW-Minas no Design System"
aliases: ["diario 2026-11-06", "unificacao tw-minas menus"]
tags:
  - tw/diario-de-bordo
  - tw/minas
  - tw/gui
  - tw/design-system
autor: "Antigravity & DaviPsss"
data: "2026-11-06"
status: concluido
---

# 📅 Diário de Bordo: 2026-11-06 — Unificação dos Menus de TW-Minas no Design System

## 🎯 Contexto e Solicitação
O jogador/administrador solicitou que a opção de Minas no `/menu` do DeluxeMenus abrisse diretamente o menu nativo do plugin proprietário `tw-minas` e que todas as interfaces gráficas (GUIs) deste plugin fossem refatoradas para seguir estritamente o **Design System Oficial** e a **Arquitetura de Navegação**.

---

## 🛠️ Alterações Realizadas

### 1. Servidor e DeluxeMenus
- **`plugins/DeluxeMenus/gui_menus/menus/menu.yml`**:
  - Atualizado o item `minas` (Slot 19) para executar diretamente `[player] minas` (removendo `[close]` concorrente e chamada a menu secundário do DeluxeMenus).
- **`plugins/CommandWhitelist/config.yml`**:
  - Whitelist atualizada com o comando `/minas` (ao lado de `/mina`), garantindo execução sem restrições.

### 2. Classes Java do Plugin `tw-minas`
Todas as classes em `br.com.tw.minas.menus.*` foram alinhadas às dimensões padronizadas (54 ou 27 slots), moldura preta (`BLACK_STAINED_GLASS_PANE`), títulos canônicos com prefixo `&8➔ &b&l...` e lores em 3 seções:
- **`MinaMainMenu.java` (Central de Minas - 54 Slots):**
  - Slot 4: Cabeça do jogador com resumo de progresso e saldo.
  - Slots 20 a 24: Acesso a Minerar, Catálogo, Meta Comunitária, Oficina e Missões.
  - Slot 31: Ranking de Mineradores.
  - Slot 45: Botão Voltar para `/menu`.
  - Slot 49: Botão Fechar.
  - Slot 53: Atalho para `/spawn`.
- **`CatalogoMenu.java` (Catálogo de Minas - 54 Slots):**
  - Exibição organizada das 16 minas.
  - Slot 45: Voltar à Central de Minas.
  - Slot 48: Atalho para o `/menu`.
  - Slot 49: Fechar.
- **`OficinaMenu.java` (Oficina de Picaretas - 54 Slots):**
  - Redimensionado de 45 para 54 slots.
  - Slot 4: Picareta do jogador.
  - Linhas centrais com 11 habilidades.
  - Slot 45: Voltar à Central de Minas.
  - Slot 49: Fechar.
- **`CartinhasMenu.java` (Missões - 27 Slots):**
  - Redimensionado de 36 para 27 slots.
  - Slots 11, 13, 15: Missões com barra visual de progresso.
  - Slot 18: Voltar à Central de Minas.
  - Slot 22: Fechar.
- **`RankingMenu.java` (Ranking - 27 Slots):**
  - Redimensionado de 36 para 27 slots.
  - Slots 11, 13, 15: Top 3 mineradores com cabeças personalizadas.
  - Slot 18: Voltar à Central de Minas.
  - Slot 22: Fechar.

### 3. Compilação e Deploy
- Compilação realizada com sucesso via Maven (`mvn clean package -DskipTests`) no repositório `TW-Plugin` em Java 25.
- Deploy executado com substituição dos arquivos `tw-minas-1.0-SNAPSHOT.jar` e `tw-core-1.0-SNAPSHOT.jar` no diretório `plugins/` do servidor.
- Bateria de 120 testes automatizados (`tests/e2e/test_menus.py` e `tests/test_adversarial_navigation.py`) executada com **100% de aprovação**.

---

## 📌 Documentos Relacionados
- [[gui_minas|GUI Central de Minas]]
- [[gui_tw_plugins|Menus dos Plugins Proprietários TW-*]]
- [[gui_design_system|Design System dos Menus]]
- [[gui_arquitetura_navegacao|Arquitetura de Navegação]]
