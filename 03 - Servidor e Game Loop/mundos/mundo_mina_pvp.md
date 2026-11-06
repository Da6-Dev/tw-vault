---
title: "Mundo Mina PvP e Arena Hostil (Winter Edition)"
aliases: ["mundo mina pvp", "mina pvp", "pvp arena", "mina_pvp_winter"]
tags:
  - tw/mundo
  - tw/pvp
  - tw/combate
mundo_nome: "mina_pvp_winter"
status: ativo
versao: "2.0.0"
ultima_atualizacao: "2026-11-06"
---

📍 [[MOC_Geral|Início]] ➔ [[MOC_Mundos|Mundos]] ➔ **mundo_mina_pvp**

# ⚔️ Mundo Mina PvP e Arena Hostil (`mina_pvp_winter`)

> [!danger] Zona de Alto Risco, Tema Winter e Combate Real
> A Mina PvP é a arena de combate e extração do servidor, ambientada no mapa temático de inverno (`mina_pvp_winter`). Itens dropam no chão ao morrer e desconectar em combate resulta em morte instantânea! O mundo legado (`mina_pvp`) foi descarregado e arquivado em backup.

---

## ⚙️ Configurações Globais (Multiverse-Core & Inventários)

- **Identificador de Pasta:** `mina_pvp_winter`
- **Alias Visual:** `&c&lTW &f&lMINA PVP`
- **Dificuldade:** `hard`
- **PVP:** `true` (Habilitado)
- **Fome (Hunger):** `true` (Habilitada)
- **Voo (Allow Flight):** `false` (Proibido voar sob qualquer circunstância)
- **Clima (Weather):** `false` (Sem chuva ou tempestades prejudiciais)
- **Spawn Seguro:** X: `-64.0`, Y: `110.0`, Z: `16.0` (Piso Y: `109`)
- **Inventário:** Isolado no grupo `mina_pvp` em `plugins/Multiverse-Inventories/groups.yml` (jogadores não entram com itens da Survival/Terrenos).

---

## 🛡️ Regiões WorldGuard (`mina_pvp_winter/regions.yml`)

### 1. Zona Segura do Spawn (`spawn`) — Prioridade 10
- **Área Cuboid:** X: `-76` a `-52`, Y: `95` a `130`, Z: `4` a `28`.
- `pvp`: `deny` (Impossível sofrer dano de jogadores no spawn).
- `invincible`: `allow` (Imortalidade na plataforma de entrada).
- `allow-combat-entry`: `deny` *(Jogadores marcados em combate pelo CombatLog são bloqueados de correr para dentro do spawn).*
- `block-break` & `block-place`: `deny`.

### 2. Arena Global Externa (`__global__`) — Prioridade 0
- `pvp`: `allow`
- `invincible`: `deny` (Dano totalmente ativo).
- `fall-damage`: `allow` (Dano de queda ativo).
- `block-break` & `block-place`: `deny` (Proteção estrutural total contra quebra e construção).
- `tnt` & `fire-spread`: `deny`.
- `mob-spawning`: `deny`.

---

## ⏱️ Sistema de Combate (`CombatLog`)

> [!warning] Regras de Combate
> - **Tag de Combate:** Duração de **15 segundos** na ActionBar.
> - **Punição por Desconexão (Combat-Log):** Modo `kill` (Morte com drop total do inventário).
> - **Elytra & Teleporte:** Desativados durante a luta.
> - **Comandos Bloqueados:** `/tpa`, `/spawn`, `/warp`, `/warps`, `/minapvp`, `/pvp`, `/pvpsair`, `/mine`, `/mina`, `/mvtp`.

---

## 🎒 Kits de Batalha (`tw-minas`)
- **Comandos:** `/minapvp` (Entrar na arena), `/pvpsair` (Sair da arena), `/kits` (Kits PvP).
- **Kit Básico:** Armadura e Espada de Ferro, Escudo, Arco, 24 Flechas, 24 Bifes, 2 Maçãs Douradas.
- **Kit VIP:** Espada de Diamante Sharp 1, Armadura de Ferro Prot 1, 4 Maçãs Douradas.
- **Kit Prestígio:** Espada de Diamante Sharp 2, Armadura de Diamante Prot 1, 6 Maçãs Douradas.

---
⬅️ [[mundo_terrenos|Nota Anterior: mundo_terrenos]] | 🔼 [[MOC_Mundos|Voltar a Mundos]] | ➡️ [[MOC_Comandos|Ir para Comandos]]
