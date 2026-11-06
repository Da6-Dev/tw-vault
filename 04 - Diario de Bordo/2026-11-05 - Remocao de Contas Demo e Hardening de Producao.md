---
tags:
  - diario
  - changelog
  - auth
  - seguranca
  - hardening
  - producao
created: 2026-11-05
---

# 📅 2026-11-05 — Remoção de Contas Demo e Hardening de Produção

> Registro da eliminação completa de contas demo, credenciais de teste, mocks em localStorage e limpeza do banco Neon para abertura ao público.

Voltar para o [[00 - MOC (Map of Content)]].

---

## 🚀 Resumo das Entregas

### 1. Frontend: Remoção de Contas Demo & Mock
* **`LoginPage.jsx` & `LoginPage.css`:**
  * Remoção do divisor *"ou teste rápido com contas demo"*.
  * Remoção do grid de chips com contas demo (`TeDabliukkkkk` e `Minerador_Pro`).
  * Remoção da função `handleDemo()` e da importação de `loginDemo`.
* **`AuthContext.jsx`:**
  * Exclusão da constante `CONTAS_PADRAO` com senhas fracas (`'123'`) e cargos/VIPs desatualizados.
  * Inicialização limpa de usuários cadastrados locais com array vazio `[]`.
  * Remoção completa da função `loginDemo()` e sua desvinculação do contexto.

### 2. Backend & Banco de Dados Neon
* **`server.ts`:**
  * Remoção do seed inicial automático de contas em `inicializarBanco()`, eliminando o risco de criação de credenciais fracas no banco em produção.
  * Preservação da criação de tabelas e seed exclusivo de cupons promocionais ativos.
* **Banco de Dados PostgreSQL (Neon Cloud):**
  * Limpeza via SQL das contas de teste pré-existentes (`tedabliu@twnetwork.com.br` e `minerador@twnetwork.com.br`).
  * Banco 100% limpo e pronto para o cadastro autêntico do público e da equipe em `/cadastro`.

---

## 🔗 Referências Bidirecionais
- [[Seguranca e Hardening|Diretrizes de Segurança e Hardening]]
- [[Tabela Usuarios|Estrutura da Tabela Usuarios]]
- [[Neon PostgreSQL|Banco Neon Serverless]]


### 3. Resolução do Popup do Google (COOP & Referrer-Policy)
* **Diagnóstico da Tela Branca no Popup:** O middleware Helmet utilizava por padrão `cross-origin-opener-policy: same-origin`, o que cortava o `window.opener` e impedia que o popup do Google devolvesse o token via `postMessage`.
* **Correção Aplicada:**
  * Configurado `crossOriginOpenerPolicy: { policy: 'same-origin-allow-popups' }`.
  * Configurado `referrerPolicy: { policy: 'strict-origin-when-cross-origin' }`.
  * Liberado `https://*.googleapis.com` e `https://*.google.com` no CSP.
* **Deploy ao vivo:** Deploy ID `dep-dbmhsd17lnhs73953t5g` com status **LIVE**.
