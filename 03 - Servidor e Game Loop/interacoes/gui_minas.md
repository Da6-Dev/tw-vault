---
title: "Interface: GUI Central de Minas"
aliases: ["gui minas", "minas.yml", "deluxemenus minas", "catalogo de minas"]
tags:
  - tw/interacoes
  - tw/gui
  - tw/deluxemenus
  - tw/minas
plugin_fonte: "DeluxeMenus"
arquivo_config: "plugins/DeluxeMenus/gui_menus/menus/minas.yml"
status: ativo
versao: "2.0.0"
ultima_atualizacao: "2026-11-05"
---

📍 [[MOC_Geral|Início]] ➔ [[MOC_Interacoes|Interações]] ➔ **gui_minas**

# ⛏️ Interface: GUI Central de Minas (`minas.yml`)

> [!abstract] Catálogo Unificado de Mineração
> Interface gráfica de **54 slots (6 linhas)** acessada via `/minaslista` ou `/minhasminas`, conectando os 16 setores de mineração do servidor com suporte a exibição em **Estado Duplo (Dual-State)**.

---

## 🔒 Lógica de Estado Duplo (Dual-State)

Cada mina possui duas entradas com `priority` no DeluxeMenus:
1. **Estado Desbloqueado (`priority: 1`):**
   - Ativado quando o jogador possui a permissão/rank necessário (ex: `tw.mina.carvao`).
   - *Visual:* Título com `&a✔`, ícone brilhante/normal e som `ENTITY_ENDERMAN_TELEPORT`.
   - *Ação:* Executa `[player] mina <nome>` e fecha o menu.
2. **Estado Bloqueado (`priority: 2`):**
   - Ativado quando o requisito não foi atingido.
   - *Visual:* Título com `&c🔒`, lore indicando o rank/requisito pendente.
   - *Feedback Sonoro de Negação:* `ENTITY_VILLAGER_NO`.
   - *Ação:* Exibe mensagem no chat informando o rank necessário para desbloqueio.

---

## 🗺️ Distribuição das 16 Minas nos Slots

```text
Linha 1 [00 a 08]: [ B ][ B ][ B ][ B ][ B ][ B ][ B ][ B ][ B ]
Linha 2 [09 a 17]: [ B ][ 1 ][ 2 ][ 3 ][ 4 ][ 5 ][ 6 ][ 7 ][ B ]  <- Minas Rank (Carvão a Ouro)
Linha 3 [18 a 26]: [ B ][ 8 ][ 9 ][10 ][ V1][ V2][ V3][ B ][ B ]  <- Minas Rank (Dima a Netherita) + 3 VIPs
Linha 4 [27 a 35]: [ B ][ P1][ P2][ P3][ B ][ B ][ B ][ B ][ B ]  <- 3 Minas Prestígio
Linha 5 [36 a 44]: [ D ][ D ][ D ][ D ][ D ][ D ][ D ][ D ][ D ]  <- Divisória de Contraste
Linha 6 [45 a 53]: [ ⬅️ ][ B ][ B ][ B ][ ❌ ][ B ][ B ][ B ][ B ]  <- Botões Universais
```

### Detalhamento das Minas:
- **Ranks Iniciais (Linha 2):**
  - Slot 10: Mina Carvão (`COAL_ORE`)
  - Slot 11: Mina Ferro (`IRON_ORE`)
  - Slot 12: Mina Lápis (`LAPIS_ORE`)
  - Slot 13: Mina Redstone (`REDSTONE_ORE`)
  - Slot 14: Mina Ouro (`GOLD_ORE`)
  - Slot 15: Mina Diamante (`DIAMOND_ORE`)
  - Slot 16: Mina Esmeralda (`EMERALD_ORE`)
- **Ranks Avançados & VIPs (Linha 3):**
  - Slot 19: Mina Quartzo (`NETHER_QUARTZ_ORE`)
  - Slot 20: Mina Obsidiana (`OBSIDIAN`)
  - Slot 21: Mina Netherita (`ANCIENT_DEBRIS`)
  - Slot 22: Mina VIP Ferro (`IRON_BLOCK`)
  - Slot 23: Mina VIP Ouro (`GOLD_BLOCK`)
  - Slot 24: Mina VIP Diamante (`DIAMOND_BLOCK`)
- **Prestígios (Linha 4):**
  - Slot 28: Mina Mítica (`CRYING_OBSIDIAN`)
  - Slot 29: Mina Cósmica (`RESPAWN_ANCHOR`)
  - Slot 31: Mina Abissal (`LODESTONE`)

---

## 🔄 Navegação Universal
- **Slot 45:** `ARROW` ➔ **Voltar ao Menu Principal** (`[openguimenu] principal`).
- **Slot 49:** `BARRIER` ➔ **Fechar Menu** (`[close]`).

---
⬅️ [[gui_menu_principal|Nota Anterior: GUI Menu Principal]] | 🔼 [[MOC_Interacoes|Voltar a Interações]] | ➡️ [[gui_tw_plugins|Próxima Nota: Menus TW-Plugins]]
