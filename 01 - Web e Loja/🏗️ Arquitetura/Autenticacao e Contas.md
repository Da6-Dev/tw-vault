---
tags:
  - autenticacao
  - jwt
  - oauth
  - contas
aliases:
  - Auth
  - Login
created: 2026-11-05
---

# 👤 Autenticação e Contas — TW Network

> Fluxos de cadastro, login, sessões seguras e vinculação de Nickname do Minecraft para jogadores da rede TW Network.

Voltar para o [[00 - MOC (Map of Content)]] | Ver [[Tabela Usuarios]].

---

## 📋 Métodos de Entrada do Jogador

`mermaid
sequenceDiagram
    participant J as Jogador
    participant F as Frontend (React)
    participant B as Backend (Express)
    participant DB as Neon PostgreSQL

    alt Login Tradicional (Nick ou E-mail + Senha)
        J->>F: Digita Nick/E-mail e Senha
        F->>B: POST /api/auth/login
        B->>DB: Busca usuário pelo Nick/E-mail
        B->>B: Compara hash com bcryptjs
        B->>F: Retorna JWT Token assinado
        F->>F: Salva em localStorage (tw_auth_token)
    else Login Social (Google OAuth 2.0)
        J->>F: Clica em "Entrar com Google"
        F->>B: POST /api/auth/google (Credential JWT)
        B->>B: Valida token no googleOAuthClient
        B->>DB: Cria conta ou autentica jogador
        B->>F: Retorna JWT da TW Network
    end
`

---

## 🌐 Configuração do Google Identity Services (GSI)

Para que o login com o Google funcione em produção sem o erro origin_mismatch ou ccess_denied:

1. **Origens JavaScript Autorizadas (*Authorized JavaScript Origins*):**
   - https://twnetwork.onrender.com (Produção principal)
   - https://twnetwork.com.br (Domínio personalizado oficial)
   - http://localhost:5173 e http://localhost:3000 (Ambientes de desenvolvimento)

2. **URIs de Redirecionamento Autorizados (*Authorized Redirect URIs*):**
   - https://twnetwork.onrender.com/login
   - https://twnetwork.onrender.com/cadastro

3. **Validação Criptográfica no Backend:**
   - O frontend envia a credential (JWT emitido pelo Google).
   - O backend valida a assinatura do token usando googleOAuthClient.verifyIdToken({ idToken, audience: clientId }).
   - Isso garante proteção total contra personificação e falsificação de e-mails.

---

## 🎮 Validação e Vinculação de Nickname

O sistema garante que os benefícios comprados na loja sejam entregues para a pessoa certa no servidor:

1. **Formato do Nickname:**
   - Entre 3 e 16 caracteres.
   - Apenas letras, números e underscore (^[a-zA-Z0-9_]+$).
   - Verificado no backend através da função alidarFormatoNick().

2. **Vinculação Obrigatória:**
   - Usuários que entram pelo Google entram inicialmente com 
ick_vinculado = false.
   - Um modal interativo (VincularNickModal.jsx) solicita ao jogador que informe o seu Nick exato do Minecraft antes de finalizar qualquer compra na loja.
   - Endpoint: PUT /api/auth/vincular-nick.

---

## 🔗 Relações & Conexões
* [[Tabela Usuarios]] — Onde os dados de sessão e senhas ficam persistidos.
* [[Seguranca e Hardening]] — Proteção contra força bruta e política COOP same-origin-allow-popups.
* [[Fluxo Pix]] — O pedido fica associado ao Nick vinculado para entrega dos itens.