---
title: "Interface: GUI Menu Principal"
aliases: ["gui menu principal", "menu.yml", "deluxemenus menu", "hub de menus"]
tags:
  - tw/interacoes
  - tw/gui
  - tw/deluxemenus
  - tw/hub
plugin_fonte: "DeluxeMenus"
arquivo_config: "plugins/DeluxeMenus/gui_menus/menus/menu.yml"
status: ativo
versao: "2.0.0"
ultima_atualizacao: "2026-11-05"
---

📍 [[MOC_Geral|Início]] ➔ [[MOC_Interacoes|Interações]] ➔ **gui_menu_principal**

# 📜 Interface: GUI Menu Principal (`menu.yml`)

> [!abstract] Hub Central do Servidor
> Menu de **54 slots (6 linhas)** que ancora todo o ecossistema do servidor. Aberto com `/menu`, `/ajuda` ou ao clicar no [[npc_menu|NPC do Spawn]]. Segue estritamente o [[gui_design_system|Design System]].

---

## 🎛️ Mapa de Slots e Disposição Visual (54 Slots)

```text
Linha 1 [00 a 08]: [ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ 👤 ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ]
Linha 2 [09 a 17]: [ ⬛ ][ ⛏️ ][ 🏆 ][ 🏡 ][ 🏭 ][ 👾 ][ 🌾 ][ 🗝️ ][ ⬛ ]
Linha 3 [18 a 26]: [ ⬛ ][ ⬛ ][ ⬛ ][ 💎 ][ ⚔️ ][ ✨ ][ ⬛ ][ ⬛ ][ ⬛ ]
Linha 4 [27 a 35]: [ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ]
Linha 5 [36 a 44]: [ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ][ ⬛ ]
Linha 6 [45 a 53]: [ ⬛ ][ ⬛ ][ ⬛ ][ 🏆 ][ ❌ ][ ⬛ ][ ⬛ ][ ⬛ ][ 🌀 ]
```

### Detalhamento dos Componentes:

#### 1. Cabeçalho & Moldura
- **Slots 00-03, 05-18, 26-29, 33-47, 50-52:** Moldura com `BLACK_STAINED_GLASS_PANE` (nome vazio `' '`).
- **Slot 04 (Topo Central):** `head-%player_name%` — **Perfil do Jogador**.
  - *Exibe:* Saldo (`%vault_eco_balance_formatted%`), Tokens (`%tw_tokens%`), Almas (`%tw_souls%`), Rank Atual (`%tw_rank%`).

#### 2. Sistemas Centrais (Linha 2 & 3)
- **Slot 19:** `DIAMOND_PICKAXE` ➔ **Minas** (`[openguimenu] minas`)
- **Slot 20:** `NETHER_STAR` ➔ **Trilha de Ranks** (`/ranks`)
- **Slot 21:** `GRASS_BLOCK` ➔ **Terrenos** (`/terrenos`)
- **Slot 22:** `FURNACE` ➔ **Máquinas Industriais** (`/maquinas`)
- **Slot 23:** `SPAWNER` ➔ **Mercado de Spawners** (`/spawners`)
- **Slot 24:** `HAY_BLOCK` ➔ **Central Agrícola** (`/farms`)
- **Slot 25:** `TRIPWIRE_HOOK` ➔ **Caixas & Recompensas** (`/caixas`)
- **Slot 30:** `EMERALD` ➔ **Mercado Global** (`/shop`)
- **Slot 31:** `IRON_CHESTPLATE` ➔ **Kits da Arena PvP** (`/kits`)
- **Slot 32:** `ENDER_EYE` ➔ **Cosméticos Visuais** (`/cosmetics`)

#### 3. Rodapé de Navegação (Linha 6)
- **Slot 48:** `GOLD_BLOCK` ➔ **Ranking Magnatas** (`/baltop`).
- **Slot 49 (Centro Inferior):** `BARRIER` ➔ **Botão Universal de Fechamento** (`[close]`).
- **Slot 53:** `ENDER_PEARL` ➔ **Spawn** (`/spawn`).

---

## 🎨 Especificação de Lore
Todos os itens seguem o padrão em 3 seções do [[gui_design_system|Design System]]:
```yaml
display_name: '&#7FB4F4&lMINAS &8• &fMineração'
lore:
  - '&7Acesse a central de mineração do servidor'
  - '&7e teleporte-se para as áreas do seu rank.'
  - ''
  - '&7Seu Rank: &a%tw_rank%'
  - '&7Status: &aDisponível'
  - ''
  - '&a▶ Clique para acessar as minas'
```

---
⬅️ [[gui_arquitetura_navegacao|Nota Anterior: Arquitetura de Navegação]] | 🔼 [[MOC_Interacoes|Voltar a Interações]] | ➡️ [[gui_minas|Próxima Nota: GUI Central de Minas]]
