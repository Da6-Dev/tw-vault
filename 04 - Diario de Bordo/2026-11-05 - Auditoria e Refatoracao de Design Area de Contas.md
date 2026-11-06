# 2026-11-05 - Auditoria e Refatoração de Design — Área de Contas

## Resumo

Revisão completa de design e correção de bugs estruturais nas três telas da área de contas da plataforma web TW Network.

---

## Entregas

### Bugs Críticos Corrigidos

| ID | Arquivo | Bug | Correção |
|----|---------|-----|----------|
| B1 | `index.css` | Variáveis CSS faltantes: `--badge-bg`, `--mc-gold`, `--mc-ice`, `--shadow-sm` usadas em vários componentes mas não definidas no `:root` | Adicionadas em modo escuro e modo claro |
| B2 | `CadastroPage.jsx` / `.css` | JSX usava `.cadastro-grid` e `.cadastro-form-card` mas o CSS definia `.cadastro-card` e `.cadastro-form-col` — layout de 2 colunas quebrado | Classes alinhadas no JSX |
| B3 | `AnimatedTabs.jsx` + `PerfilPage.css` | Tabs usavam `flex-wrap` quebrando as abas em linhas e destruindo a animação `layoutId` do Framer Motion | Removido `flex-wrap`, adicionado `min-w-max`; container com `overflow-x: auto` |
| B4 | `LoginPage.css` | `btn-toggle-eye` referenciado no JSX mas sem CSS definido | Movido para `index.css` como componente compartilhado |

### Melhorias de Design e UX

- **LoginPage:** Adicionado ícone badge visual no cabeçalho (`Grass_Block` icon), `role="alert"` acessível nos erros, fundo pontilhado sutil (padrão pixelado Minecraft)
- **CadastroPage:** Mesmo fundo pontilhado; `role="alert"` no erro; styles inline do Google wrapper movidos para CSS; `min-width: 0` nos inputs de senha para funcionar corretamente em grid
- **PerfilPage:** 7 novas media queries mobile (480px, 540px, 600px) cobrindo: KPI strip, calendário 2 colunas, passe em coluna, missões em 1 coluna, configurações compactas, layout de pedidos em mobile

### Limpeza e Consistência

- **14 cores hardcoded** substituídas por variáveis CSS do design system em `PerfilPage.css` (ex: `#2ecc71` → `var(--mc-emerald)`, `#f39c12` → `var(--mc-gold)`, `#e74c3c` → `var(--mc-redstone)`)
- `.auth-divider`, `.btn-toggle-eye`, `.password-wrapper`, `.btn-google-login` e `.auth-google-wrapper` **centralizados em `index.css`** como componentes compartilhados entre Login e Cadastro
- CSS de Login e Cadastro reescritos limpos, sem duplicações

---

## Arquivos Modificados

- `src/index.css` — +4 variáveis, classes compartilhadas de auth
- `src/pages/LoginPage.css` — reescrito (componentes movidos para index.css)
- `src/pages/LoginPage.jsx` — ícone badge, `role="alert"`, styles inline removidos
- `src/pages/CadastroPage.jsx` — bug B2 corrigido, `role="alert"`, styles inline removidos
- `src/pages/CadastroPage.css` — reescrito com `min-width: 0`, media queries 480px/360px
- `src/pages/PerfilPage.css` — tabs overflow scroll, 14 cores hardcoded → variáveis, 7 media queries mobile
- `src/components/ui/AnimatedTabs.jsx` — `flex-wrap` removido, `min-w-max` adicionado

## Verificação

```
✓ npm run build — 0 erros, 0 warnings de tipo
✓ 2406 módulos transformados
✓ CSS bundle: 148.73 kB (gzip: 22.69 kB)
```

## Links Relacionados

- [[Design System e Componentes]]
- [[Autenticacao e Contas]]
- [[Seguranca e Hardening]]
- [[Tech Stack]]
