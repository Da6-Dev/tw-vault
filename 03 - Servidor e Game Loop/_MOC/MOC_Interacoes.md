---
title: "MOC — Interações, NPCs e Interfaces"
aliases: ["MOC Interações", "Interações", "Menus", "MOC Menus"]
tags:
  - tw/moc
  - tw/interacoes
  - tw/gui
status: ativo
versao: "2.0.0"
ultima_atualizacao: "2026-11-05"
---

📍 [[MOC_Geral|Início]] ➔ **MOC Interações**

# 💬 Central de Interações Visuais e Menus

> [!info] Experiência do Usuário (UI/UX Unificada)
> O servidor adota um Design System coeso e padronizado em 54/27 slots, interligando DeluxeMenus, FancyNpcs, FancyHolograms e os menus nativos da suíte `tw-*`.

---

## 🎨 Design System & Arquitetura de Navegação

- [[gui_design_system|🎨 Design System & Guia de Estilo]]: Diretrizes de slots (54/27), paleta cromática (`&#7FB4F4`, `&e`, `&7`), molduras em vidro e estrutura de lore em 3 seções.
- [[gui_arquitetura_navegacao|🧭 Arquitetura de Navegação & Fluxo UX]]: Topologia em estrela centrada no `/menu`, matriz dos 10 sistemas, botões universais de retorno (45/18) e fechamento (49/22).

---

## 🎛️ Interfaces Gráficas (GUIs)

- [[gui_menu_principal|📜 GUI Menu Principal (`menu.yml`)]]: Hub central de 54 slots com perfil do jogador, atalhos aos 10 subsistemas, ranking e botão de fechar.
- [[gui_minas|⛏️ GUI Central de Minas (`minas.yml`)]]: Catálogo de 54 slots com 16 minas (Ranks, VIPs, Prestígio), exibição em estado duplo (desbloqueada vs bloqueada) e retorno no slot 45.
- [[gui_tw_plugins|🧩 Menus dos Plugins Proprietários (`tw-*`)]]: Configurações YAML padronizadas para Ranks, Terrenos, Máquinas, Spawners, Farms, Caixas e Oficina de Minas.

---

## 🤖 Elementos de Imersão no Mundo

- [[npc_menu|🤖 NPC Menu Principal]]: Coordenadas, skin natalina e ação de clique direito.
- [[hologramas|✨ Hologramas do Spawn]]: Holograma de boas-vindas com placeholders dinâmicos e guia de menu.

---
⬅️ [[MOC_Geral|Voltar ao Mapa Geral]] | 🔼 [[00 - MOC (Map of Content)|MOC Mestre]] | ➡️ [[gui_design_system|Ver Design System]]
