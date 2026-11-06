---
tags:
  - seguranca
  - owasp
  - hardening
aliases:
  - Hardening
  - Seguranca
created: 2026-11-05
---

# 🛡️ Segurança e Hardening — TW Network

> Medidas de proteção e blindagem contra vulnerabilidades OWASP Top 10 aplicadas no servidor Express e pool de conexões.

Voltar para o [[00 - MOC (Map of Content)]] | Ver [[Tech Stack]].

---

## 🔒 1. Proxy Reverso Confiável (	rust proxy)

No arquivo server.ts:
`	ypescript
app.set('trust proxy', 1);
`
* **Motivo:** O site roda atrás de proxies reversos (Cloudflare e Nginx no Render). Sem o 	rust proxy, todas as requisições chegam com o IP do proxy, fazendo com que o rate limiter bloqueie **todos** os jogadores de uma vez. Com o nível 1 configurado, o Express lê o cabeçalho X-Forwarded-For e identifica o IP real do cliente.

---

## 🛑 2. Fail-Fast de Chave Secreta (JWT_SECRET)

No arquivo server.ts:
`	ypescript
const DEV_JWT_SECRET = 'twnetwork_jwt_secret_dev_2026_rankup_natal';
const isProduction = process.env.NODE_ENV === 'production';

if (isProduction) {
  const secret = process.env.JWT_SECRET?.trim();
  if (!secret || secret === DEV_JWT_SECRET || secret === 'undefined' || secret === 'null') {
    throw new Error(
      'Configuração inválida para produção: JWT_SECRET não foi definido ou está utilizando a chave padrão insegura de desenvolvimento.'
    );
  }
}
`
* **Motivo:** Impede que o servidor seja iniciado em produção se o administrador esquecer de configurar uma chave criptográfica forte, bloqueando o uso de chaves dev conhecidas.

---

## 🌐 3. Restrição de CORS Condicional

`	ypescript
const defaultAllowedOrigins = ['https://twnetwork.com.br', 'https://www.twnetwork.com.br'];
const parsedAllowedOrigins = process.env.ALLOWED_ORIGINS
  ? process.env.ALLOWED_ORIGINS.split(',').map((o) => o.trim().replace(/^['"]|['"]$/g, '').replace(/\/+$/, '')).filter(Boolean)
  : [];
const allowedOrigins = parsedAllowedOrigins.length > 0 ? parsedAllowedOrigins : defaultAllowedOrigins;

app.use(
  cors({
    origin: isProduction ? allowedOrigins : true,
    credentials: true,
  })
);
`
* **Em Desenvolvimento:** Aberto para testes locais rápidos.
* **Em Produção:** Bloqueia requisições originadas de domínios não autorizados.

---

## 🚦 4. Proteção com Rate Limiters Dedicados

1. **Global (/api/):** Máximo de 300 requisições a cada 15 minutos (com exceção para o endpoint /api/health, permitindo monitoramento de uptime contínuo).
2. **Autenticação (/api/auth/login e /api/auth/cadastrar):** Máximo de 20 tentativas por 15 minutos por IP (combate ataques de força bruta e credential stuffing).
3. **Cupons (/api/cupons/validar):** Máximo de 25 tentativas a cada 5 minutos (evita robôs tentando adivinhar códigos promocionais por dicionário).

---

## 🛡️ 5. Compatibilidade de Popups OAuth (COOP & Referrer-Policy)

No arquivo server.ts:
`	ypescript
app.use(
  helmet({
    contentSecurityPolicy: {
      directives: {
        defaultSrc: ["'self'"],
        scriptSrc: ["'self'", "'unsafe-inline'", "'unsafe-eval'", "https://accounts.google.com", "https://*.google.com"],
        styleSrc: ["'self'", "'unsafe-inline'", "https://fonts.googleapis.com"],
        imgSrc: ["'self'", "data:", "blob:", "https://mc-heads.net", "https://*.googleusercontent.com"],
        connectSrc: ["'self'", "https://accounts.google.com", "https://*.googleapis.com", "https://api.mercadopago.com", "ws:", "wss:"],
        frameSrc: ["'self'", "https://accounts.google.com"],
        fontSrc: ["'self'", "https://fonts.gstatic.com", "data:"],
      },
    },
    crossOriginEmbedderPolicy: false,
    crossOriginOpenerPolicy: { policy: 'same-origin-allow-popups' },
    referrerPolicy: { policy: 'strict-origin-when-cross-origin' },
  })
);
`
* **O Problema da Tela Branca no Popup:** Por padrão, o Helmet ativa cross-origin-opener-policy: same-origin. Isso faz com que o navegador isole o popup do Google e defina window.opener = null, impedindo que o script do Google envie o token JWT via postMessage de volta para a aplicação e travando a janela em tela branca.
* **A Solução:** Definir a política como same-origin-allow-popups e o eferrerPolicy como strict-origin-when-cross-origin, autorizando explicitamente o handshake entre a janela mãe do site e o popup de login.

---

## 🚫 6. Proibição Estrita de Contas Demo em Produção

* **Regra Inegociável:** Nenhum seed de contas com senhas padrão (como '123') deve rodar em produção.
* **Frontend Seguro:** O AuthContext não mantém mocks de fallback (CONTAS_PADRAO) em localStorage. Todas as contas passam obrigatoriamente pela validação do PostgreSQL Neon e do Google OAuth.

---

## 🔗 Relações & Conexões
* [[Autenticacao e Contas]] — Como os tokens JWT são assinados e consumidos.
* [[Variaveis de Ambiente]] — Gestão segura de chaves.
* [[Render Web Service]] — Onde o Rate Limiting e CORS estão em vigor.