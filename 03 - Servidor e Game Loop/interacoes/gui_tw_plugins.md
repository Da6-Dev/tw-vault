---
title: "Interfaces: Menus dos Plugins TW-*"
aliases: ["gui tw plugins", "menus tw", "tw menus", "configuracoes de menus tw"]
tags:
  - tw/interacoes
  - tw/gui
  - tw/plugins
  - tw/design-system
status: ativo
versao: "1.1.0"
ultima_atualizacao: "2026-11-06"
---

📍 [[MOC_Geral|Início]] ➔ [[MOC_Interacoes|Interações]] ➔ **gui_tw_plugins**

# 🧩 Interfaces: Menus dos Plugins Proprietários (`tw-*`)

> [!abstract] Integração Nativa da Suíte TW
> Todos os submódulos da rede `tw-*` estão alinhados estritamente ao [[gui_design_system|Design System]] e à [[gui_arquitetura_navegacao|Arquitetura de Navegação]]. O módulo de mineração (`tw-minas`) foi integralmente migrado em Java para interfaces de 54 e 27 slots com molduras em `BLACK_STAINED_GLASS_PANE`, botão de retorno e descrições em 3 seções.

---

## 📂 Visão Geral dos Menus Padronizados

| Módulo | Implementação / Arquivo | Tamanho | Título Canônico | Botão Voltar | Botão Fechar |
|---|---|:---:|---|:---:|:---:|
| [[04-RANKS-MODULE\|tw-ranks]] | `plugins/tw-ranks/menus/ranks.yml` | 54 Slots | `&8➔ &#7FB4F4&lTRILHA DE RANKS` | Slot 45 | Slot 49 |
| [[06-TERRENOS-MODULE\|tw-terrenos]] | `plugins/tw-terrenos/menus/terrenos.yml` | 27 Slots | `&8➔ &#7FB4F4&lAGÊNCIA DE TERRENOS` | Slot 18 | Slot 22 |
| [[07-MAQUINAS-MODULE\|tw-maquinas]] | `plugins/tw-maquinas/menus/maquinas.yml` | 54 Slots | `&8➔ &#7FB4F4&lFÁBRICA DE MÁQUINAS` | Slot 45 | Slot 49 |
| [[08-SPAWNERS-MODULE\|tw-spawners]] | `plugins/tw-spawners/menus/spawners.yml` | 54 Slots | `&8➔ &#7FB4F4&lMERCADO DE SPAWNERS` | Slot 45 | Slot 49 |
| [[09-FARMS-MODULE\|tw-farms]] | `plugins/tw-farms/menus/farms.yml` | 54 Slots | `&8➔ &#7FB4F4&lCENTRAL AGRÍCOLA` | Slot 45 | Slot 49 |
| [[10-CAIXAS-MODULE\|tw-caixas]] | `plugins/tw-caixas/menus/caixas.yml` | 54 Slots | `&8➔ &#7FB4F4&lCHAVES & CAIXAS VIRTUAIS` | Slot 45 | Slot 49 |
| [[05-MINAS-MODULE\|tw-minas]] | `MinaMainMenu.java` (Central) | 54 Slots | `&8➔ &#7FB4F4&lCENTRAL DE MINAS` | Slot 45 | Slot 49 |
| [[05-MINAS-MODULE\|tw-minas]] | `CatalogoMenu.java` (Catálogo) | 54 Slots | `&8➔ &#7FB4F4&lCATÁLOGO DE MINAS` | Slot 45 | Slot 49 |
| [[05-MINAS-MODULE\|tw-minas]] | `OficinaMenu.java` (Oficina) | 54 Slots | `&8➔ &#7FB4F4&lOFICINA DE MINAS` | Slot 45 | Slot 49 |
| [[05-MINAS-MODULE\|tw-minas]] | `CartinhasMenu.java` (Missões) | 27 Slots | `&8➔ &#7FB4F4&lMISSÕES DE MINERAÇÃO` | Slot 18 | Slot 22 |
| [[05-MINAS-MODULE\|tw-minas]] | `RankingMenu.java` (Ranking) | 27 Slots | `&8➔ &#7FB4F4&lRANKING DE MINERADORES` | Slot 18 | Slot 22 |

---

## 🛠️ Especificações por Subsistema

### 1. `tw-ranks` (`ranks.yml`)
- **Tamanho:** 54 Slots.
- **Estrutura:** Exibe a progressão contínua de ranks (A-Z) e prestígios com verificação de saldo (`$%vault_eco_balance_formatted%`).
- **Navegação:** Slot 45 retorna ao `/menu`.

### 2. `tw-terrenos` (`terrenos.yml`)
- **Tamanho:** 27 Slots (Submenu Rápido).
- **Estrutura:** Acesso às ações de compra progressiva de lotes PlotSquared, teleporte (`/plot home`), ativação de voo protegido (`/fly`) e permissões de membros.
- **Navegação:** Slot 18 (`ARROW`) retorna ao `/menu`, Slot 22 (`BARRIER`) fecha a interface.

### 3. `tw-maquinas` (`maquinas.yml`)
- **Tamanho:** 54 Slots.
- **Estrutura:** Loja industrial com geradores em bloco (Carvão a Netherita), compra de combustível refinado e coleta centralizada de lucros.

### 4. `tw-spawners` (`spawners.yml`)
- **Tamanho:** 54 Slots.
- **Estrutura:** Painel de aquisição de geradores com empilhamento até 10.000 entidades, alternância de modo virtual/físico e balcão de almas (`%tw_souls%`).

### 5. `tw-farms` (`farms.yml`)
- **Tamanho:** 54 Slots.
- **Estrutura:** Gerenciador do silo virtual (capacidade base de 50k itens), upgrade de colheita em área 3x3 e toggle de auto-venda de safra.

### 6. `tw-caixas` (`caixas.yml`)
- **Tamanho:** 54 Slots.
- **Estrutura:** Catálogo de caixas de recompensa com exibição do sistema de *Pity* dinâmico, saldo de chaves virtuais e forja de fragmentos.

### 7. `tw-minas` (Nativo Java em `br.com.tw.minas.menus.*`)
- Consulte a documentação dedicada detalhada em [[gui_minas|GUI Central de Minas]].
- Possui arquitetura em cascata: `Central de Minas (54s)` ➔ `Catálogo (54s)`, `Oficina (54s)`, `Missões (27s)`, `Ranking (27s)`.
- Todos os submenus possuem botão de retorno para a `Central de Minas` e atalho para o `/menu`.

---
⬅️ [[gui_minas|Nota Anterior: GUI Minas]] | 🔼 [[MOC_Interacoes|Voltar a Interações]] | ➡️ [[MOC_Interacoes|Voltar ao MOC]]
