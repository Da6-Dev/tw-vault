---
title: "Diário de Bordo: 2026-11-06 - Migração e Configuração da Mina PvP de Inverno"
aliases: ["diario 2026-11-06 pvp winter", "migracao mina_pvp_winter"]
tags:
  - tw/diario-de-bordo
  - tw/pvp
  - tw/mundos
  - tw/multiverse
  - tw/worldguard
autor: "Antigravity & DaviPsss"
data: "2026-11-06"
status: concluido
---

# 📅 Diário de Bordo: 2026-11-06 — Migração e Configuração da Mina PvP de Inverno (`mina_pvp_winter`)

## 🎯 Contexto e Solicitação
O administrador solicitou a remoção definitiva do mapa antigo da Mina PvP (`mina_pvp`) e a ativação configurada e segura do novo mapa temático de inverno (`mina_pvp_winter`).

---

## 🛠️ Alterações Executadas

### 1. Desativação e Backup do Mundo Antigo
- A pasta de dimensão `world/dimensions/minecraft/mina_pvp` e suas regiões do WorldGuard foram arquivadas em segurança no diretório `backups/old_mina_pvp`.
- A entrada do mundo legado foi removida de `plugins/Multiverse-Core/worlds.yml`.

### 2. Configurações Globais no Multiverse-Core (`worlds.yml`)
- Registrado `minecraft:mina_pvp_winter`:
  - `alias`: `&c&lTW &f&lMINA PVP`
  - `difficulty`: `hard`
  - `pvp`: `true`
  - `allow-flight`: `false`
  - `allow-weather`: `false`
  - `keep-spawn-in-memory`: `true`
  - `spawning`: Desativados spawns naturais de monstros/animais para combate limpo.
  - `spawn-location`: Coordenadas oficiais em `x: -64.0, y: 110.0, z: 16.0`.

### 3. Isolamento de Inventário no Multiverse-Inventories (`groups.yml`)
- Atualizado o grupo `mina_pvp` para conter exclusivamente `mina_pvp_winter`, garantindo que os jogadores não tragam inventário da Survival/Terrenos para dentro da arena e vice-versa.

### 4. Integração no Plugin Proprietário `tw-minas` (`config.yml`)
- Atualizada a chave `pvp.world` para `mina_pvp_winter` tanto no servidor quanto no código-fonte padrão do repositório Java (`TW-Plugin`).
- Ajustado o spawn de teleporte do comando `/minapvp` para as coordenadas `X: -64.0, Y: 110.0, Z: 16.0, floor-y: 109`.

### 5. Regiões e Proteções no WorldGuard (`mina_pvp_winter/regions.yml`)
- **Região `__global__`**: `pvp: allow`, `invincible: deny`, `fall-damage: allow`, `block-break: deny`, `block-place: deny`, `tnt: deny`, `fire-spread: deny`, `mob-spawning: deny`.
- **Região `spawn` (Cuboid -76 a -52, Y 95 a 130, Z 4 a 28)**: `pvp: deny`, `invincible: allow`, `allow-combat-entry: deny` (anti-combatlog flee), `fall-damage: deny`.

---

## 📌 Documentos Relacionados
- [[mundo_mina_pvp|Mundo Mina PvP e Arena Hostil]]
- [[combate_pvp|Combate e Regras de PvP]]
