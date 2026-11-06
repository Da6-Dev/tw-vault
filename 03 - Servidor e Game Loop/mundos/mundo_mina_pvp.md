---
title: "Mundo Mina PvP e Arena Hostil (Winter Edition)"
aliases: ["mundo mina pvp", "mina pvp", "pvp arena", "mina_pvp_winter"]
tags:
  - tw/mundo
  - tw/pvp
  - tw/combate
mundo_nome: "mina_pvp_winter"
status: ativo
versao: "2.1.0"
ultima_atualizacao: "2026-11-06"
---

📍 [[MOC_Geral|Início]] ➔ [[MOC_Mundos|Mundos]] ➔ **mundo_mina_pvp**

# ⚔️ Mundo Mina PvP e Arena Hostil (`mina_pvp_winter`)

> [!danger] Zona de Alto Risco, Tema Winter e Combate Real
> A Mina PvP é a arena de combate e extração do servidor, ambientada no mapa temático original de inverno (`mina_pvp_winter`). O mapa é base e puro (sem blocos ou estruturas artificiais inseridas). As demarcações de regiões de proteção e spawn são definidas pelo administrador via WorldGuard in-game.

---

## ⚙️ Configurações Globais (Multiverse-Core & Inventários)

- **Identificador de Pasta:** `mina_pvp_winter`
- **Alias Visual:** `&c&lTW &f&lMINA PVP`
- **Dificuldade:** `hard`
- **PVP:** `true` (Habilitado)
- **Fome (Hunger):** `true` (Habilitada)
- **Voo (Allow Flight):** `false` (Proibido voar sob qualquer circunstância)
- **Clima (Weather):** `false` (Sem chuva ou tempestades)
- **Inventário:** Isolado no grupo `mina_pvp` em `plugins/Multiverse-Inventories/groups.yml` (jogadores não entram com itens da Survival/Terrenos).

---

## 🛡️ Regiões WorldGuard (`mina_pvp_winter/regions.yml`)
O arquivo de regiões está limpo (`regions: {}`) para que as áreas (como Spawn, Barreira e Arena) sejam demarcadas diretamente no mapa com a varinha do WorldEdit/WorldGuard (`//wand` e `/rg define`).

---

## ⏱️ Sistema de Combate (`CombatLog`)

> [!warning] Regras de Combate
> - **Tag de Combate:** Duração de **15 segundos** na ActionBar.
> - **Punição por Desconexão (Combat-Log):** Modo `kill` (Morte com drop total do inventário).
> - **Elytra & Teleporte:** Desativados durante a luta.
> - **Comandos Bloqueados:** `/tpa`, `/spawn`, `/warp`, `/warps`, `/minapvp`, `/pvp`, `/pvpsair`, `/mine`, `/mina`, `/mvtp`.

---

## 🎒 Permissões e Kits de Batalha (`tw-minas`)
- **Comandos Liberados na Whitelist:** `/minapvp`, `/pvp`, `/pvpsair`, `/kits`.
- **Permissões Nativas de Acesso:**
  - `tw-minas.pvp.enter`: `true` (liberado para todos os jogadores).
  - `tw-minas.pvp.leave`: `true` (liberado para todos os jogadores).
  - `tw-minas.kits`: `true` (acesso ao menu de kits).
  - `tw-minas.kits.vip`: para jogadores VIP.
  - `tw-minas.kits.prestige`: para jogadores Prestígio.

---
⬅️ [[mundo_terrenos|Nota Anterior: mundo_terrenos]] | 🔼 [[MOC_Mundos|Voltar a Mundos]] | ➡️ [[MOC_Comandos|Ir para Comandos]]
