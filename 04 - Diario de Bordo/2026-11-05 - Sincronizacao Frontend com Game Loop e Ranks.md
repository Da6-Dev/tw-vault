---
tags:
  - diario
  - changelog
  - frontend
  - gameloop
  - ranks
  - vips
created: 2026-11-05
---

# 📅 2026-11-05 — Sincronização do Frontend com o Game Loop e Ranks Natalinos

> Registro da atualização e alinhamento completo do site com os sistemas in-game documentados no Super-Vault: Tríade VIP Oficial (Festivo, Nevasca, Polar), 11 Ranks Natalinos, Prestígios End Game e Mundos.

Voltar para o [[00 - MOC (Map of Content)]].

---

## 🚀 Resumo das Entregas

### 1. Tríade VIP Oficial na Loja e Showcase
* Substituição dos nomes genéricos pelos oficiais do servidor:
  * **VIP Festivo** (R$ 19,90): Mina `vip_festivo` (Nether Gold Ore), chat `/vc`, kit festivo semanal, bônus de venda +25% e 3 lotes no `/terrenos`.
  * **VIP Nevasca** (R$ 39,90): Minas `vip_festivo` e `vip_nevasca` (Nether Quartz Ore), chat `/vc`, `/fly` em terrenos e lobby, `/reparar` ilimitado, bônus de venda +50% e 5 lotes de terreno.
  * **VIP Polar** (R$ 69,90): Todas as minas VIP incluindo `vip_polar` (Ancient Debris), chat `/vc`, `/fly` irrestrito, bônus máximo de venda +100% (2.0x dobro), comandos `/feed` e `/hat`, 10 lotes e 1x Chave Divina Semanal.
* Atualização do Showcase VIP na Home (`VipShowcase.jsx`) e da tabela de comparativo de recursos no `LojaPage.jsx`.
* Atualização dos pacotes de chaves na loja para as Chaves Festivas, Nevadas e Combo Caixa Divina com Pity System.

### 2. Nova Seção de Ranks & Prestígios no Guia do Jogador
* Criação do componente `RanksSection.jsx` e `RanksSection.css`.
* Integração da aba **Ranks & Prestígios** no `GuiaPage.jsx`.
* Apresentação interativa dos **11 Ranks Lineares** (`Carvão` a `Noel/MAX`) e dos **3 Prestígios End Game** (`Grinch` 1.5x, `Yeti` 2.0x, `Krampus` 3.0x), contendo custos de evolução, minas e recompensas via `/correio`.
* Destaque para os comandos `/rankupmax` e `/prestigio`.

### 3. Atualização dos Comandos Oficiais e Mundos
* Atualização do catálogo de comandos em `GuiaComandos.jsx` divididos em 5 categorias oficiais:
  * Ranks & Prestígios (`/rankup`, `/rankupmax`, `/ranks`, `/prestigio`, `/menu`, `/spawn`).
  * Minas & PvP (`/mina`, `/minaslista`, `/minapvp`, `/pvpsair`).
  * Indústria & Plots (`/terreno`, `/maquinas`, `/maquinas status`, `/spawners`, `/farms`, `/caixas`).
  * Economia & Correio (`/money`, `/pay`, `/baltop`, `/cheque`, `/correio`).
  * Comandos VIP (`/vc`, `/fly`, `/reparar [all]`, `/feed`, `/hat`, `/kit vip`).
* Atualização dos dados do servidor em `serverData.js` e do Hub de Atividades (`PlayerHub.jsx`) com os mundos reais (`RankUP Natal`, `Mina PvP & Arenas`, `Mundo Terrenos Plots`, `Lobby Principal`) e líderes com ranks reais (`Krampus`, `Yeti`, `Grinch`, `Noel`, `Estrela`).

---

## 🔗 Referências Bidirecionais
- [[tw_ranks|Sistema de Ranks e Prestígios]]
- [[mundo_minas|Mundo de Mineração Progressiva]]
- [[tabela_precos|Tabela de Preços e Cotações]]
- [[rag_consolidado|Base RAG Consolidada]]
