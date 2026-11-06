---
title: "Design System & Guia de Estilo Visual (UI)"
aliases: ["gui design system", "design system menus", "estilo de menus", "ui design system"]
tags:
  - tw/interacoes
  - tw/gui
  - tw/design-system
  - tw/ui-ux
status: ativo
versao: "1.0.0"
ultima_atualizacao: "2026-11-05"
---

📍 [[MOC_Geral|Início]] ➔ [[MOC_Interacoes|Interações]] ➔ **gui_design_system**

# 🎨 Design System & Guia de Estilo Visual (UI) — TW Network

> [!abstract] Padronização Visual e Ergonômica
> Este documento estabelece as diretrizes canônicas para todas as interfaces gráficas (GUIs) da rede **TW Network**, integrando menus de terceiros (como [[gui_menu_principal|DeluxeMenus]]) e menus nativos da suíte de plugins [[00-ROUTER-AND-TAXONOMY|tw-*]].

---

## 🏛️ 1. Princípios Estruturais

1. **Consistência Estrutural:** Apenas dois tamanhos canônicos são permitidos:
   - **54 Slots (6 Linhas / 9x6):** Menus Principais, Hubs e Catálogos Extensos (Minas, Ranks, Máquinas, Spawners, Farms, Caixas, Loja).
   - **27 Slots (3 Linhas / 9x3):** Submenus rápidos, Diálogos de Confirmação e Painéis de Gerenciamento local (Agência de Terrenos, Painel de Bloco).
   - *Nota:* Tamanhos arbitrários (36 ou 45 slots) foram oficialmente descontinuados.
2. **Previsibilidade Motora (Botões Universais):**
   - **Retorno ao Menu Anterior:** Slot `45` (em 54 slots) ou Slot `18` (em 27 slots).
   - **Fechar Interface:** Slot `49` (em 54 slots) ou Slot `22` (em 27 slots).
3. **Hierarquia Rígida de Lore (3 Seções):** Topo (Função) ➔ Meio (Status Dinâmico) ➔ Rodapé (Ação de Clique).

---

## 📐 2. Geometria de Slots e Molduras

### 2.1. Matriz de 54 Slots (Menus Principais / Hubs)
```text
Linha 1 [00 a 08]: [ B ][ B ][ B ][ B ][ P ][ B ][ B ][ B ][ B ]
Linha 2 [09 a 17]: [ B ][ C ][ C ][ C ][ C ][ C ][ C ][ C ][ B ]
Linha 3 [18 a 26]: [ B ][ C ][ C ][ C ][ C ][ C ][ C ][ C ][ B ]
Linha 4 [27 a 35]: [ B ][ C ][ C ][ C ][ C ][ C ][ C ][ C ][ B ]
Linha 5 [36 a 44]: [ D ][ D ][ D ][ D ][ D ][ D ][ D ][ D ][ D ]
Linha 6 [45 a 53]: [ R ][ B ][ B ][ I ][ B ][ X ][ B ][ B ][ S ]
```

- `[ B ]` **Moldura Externa:** `BLACK_STAINED_GLASS_PANE` ou `GRAY_STAINED_GLASS_PANE` (nome vazio `' '`).
- `[ P ]` **Slot 4:** Perfil do Jogador (`head-%player_name%`).
- `[ C ]` **Conteúdo Ativo:** Categorias e sistemas (Linhas 2, 3 e 4).
- `[ D ]` **Divisória Inferior:** Slots 36 a 44 como faixa de contraste visual.
- `[ R ]` **Slot 45:** Botão Universal de Retorno (`ARROW`).
- `[ I ]` **Slot 48:** Informações Globais / Ranking dos Mais Ricos (`GOLD_BLOCK` / `baltop`).
- `[ X ]` **Slot 49:** Botão Universal de Fechamento (`BARRIER`).
- `[ S ]` **Slot 53:** Atalho Rápido ao Spawn (`ENDER_PEARL`).

---

### 2.2. Matriz de 27 Slots (Submenus e Diálogos)
```text
Linha 1 [00 a 08]: [ B ][ B ][ B ][ B ][ T ][ B ][ B ][ B ][ B ]
Linha 2 [09 a 17]: [ B ][ C ][ C ][ C ][ C ][ C ][ C ][ C ][ B ]
Linha 3 [18 a 26]: [ R ][ B ][ B ][ B ][ X ][ B ][ B ][ B ][ H ]
```

- `[ B ]` **Moldura:** `BLACK_STAINED_GLASS_PANE` ou `GRAY_STAINED_GLASS_PANE`.
- `[ T ]` **Slot 4:** Ícone Temático Centralizador do Submenu.
- `[ C ]` **Slots 10 a 16:** Ações principais do submenu.
- `[ R ]` **Slot 18:** Botão Universal de Retorno (`ARROW`).
- `[ X ]` **Slot 22:** Botão Universal de Fechamento (`BARRIER`).
- `[ H ]` **Slot 26:** Atalho Rápido ao Hub Central (`NETHER_STAR` ➔ `/menu`).

---

## 🎨 3. Paleta Cromática Oficial

| Cor / Semântica | Minecraft | Hexadecimal (Purpur RGB) | Aplicação Obrigatória |
|---|---|---|---|
| **Ciano Principal** | `&b` | `&#7FB4F4` | Títulos de menus, cabeçalhos de itens e categorias nobres. |
| **Dourado / Economia** | `&e` / `&6` | `&#F7C844` | Saldos (`$%vault_eco_balance_formatted%`), preços, multiplicadores e tokens. |
| **Texto Descritivo** | `&7` | `#AAAAAA` | Descrições funcionais, contexto de jogabilidade e explicações. |
| **Destaque Claro** | `&f` | `#FFFFFF` | Nomes de jogadores, números neutros e parâmetros. |
| **Divisória / Moldura**| `&8` | `#555555` | Prefixos (`&8➔`), separadores horizontais (`&8───────────────`). |
| **Sucesso / Ação** | `&a` | `#55FF55` | Status liberado, comandos positivos (`&a▶ Clique para...`). |
| **Alerta / Fechar** | `&c` | `#FF5555` | Status bloqueado, faltam requisitos, botão fechar (`&c▶ Clique para fechar`). |
| **Místico / Almas** | `&d` | `#FF55FF` | Saldo de Almas (`%tw_souls%`), prestígios e itens forjados. |

---

## 🏷️ 4. Formato Canônico de Títulos de Menus

Todo título deve iniciar com o marcador grafite seguido da cor do tema em negrito:
```text
&8➔ <COR_TEMA>&l<NOME_DO_MENU>
```

- **Menu Principal:** `&8➔ &6&lMENU PRINCIPAL` ou `&8➔ &#7FB4F4&lMENU PRINCIPAL`
- **Minas:** `&8➔ &b&lMINAS`
- **Trilha de Ranks:** `&8➔ &#7FB4F4&lTRILHA DE RANKS`
- **Agência de Terrenos:** `&8➔ &#7FB4F4&lAGÊNCIA DE TERRENOS`
- **Fábrica de Máquinas:** `&8➔ &#7FB4F4&lFÁBRICA DE MÁQUINAS`
- **Mercado de Spawners:** `&8➔ &#7FB4F4&lMERCADO DE SPAWNERS`
- **Central Agrícola:** `&8➔ &#7FB4F4&lCENTRAL DE AGRICULTURA`
- **Chaves & Caixas:** `&8➔ &#7FB4F4&lCHAVES & CAIXAS VIRTUAIS`

---

## 📜 5. Padrão Estruturado de Lore em 3 Seções

Todo item clicável possui 3 seções intercaladas por linhas em branco (`''`):

```yaml
lore:
  # SEÇÃO 1: TOPO (O que é e o que faz)
  - '&7Acesse a central de mineração do servidor'
  - '&7e teleporte-se para as áreas do seu rank.'
  - ''
  # SEÇÃO 2: MEIO (Status dinâmico / Variáveis)
  - '&7Seu Rank: &a%tw_rank%'
  - '&7Status: &aDisponível'
  - ''
  # SEÇÃO 3: RODAPÉ (Instruções claras de clique)
  - '&a▶ Clique para acessar as minas'
```

---
⬅️ [[MOC_Interacoes|Voltar a Interações]] | 🔼 [[00 - MOC (Map of Content)|MOC Mestre]] | ➡️ [[gui_arquitetura_navegacao|Próxima Nota: Arquitetura de Navegação]]
