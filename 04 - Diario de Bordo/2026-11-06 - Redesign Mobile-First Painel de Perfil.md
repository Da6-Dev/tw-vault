# 2026-11-06 - Redesign Mobile-First do Painel de Perfil

## Entregas

### AnimatedTabs - Bottom Nav Mobile
- Adicionado prop mobileLabels ao componente AnimatedTabs.jsx
- Renderiza dois elementos: .perfil-tabs-desktop (pill, desktop) e .perfil-tabs-mobile-nav (bottom nav fixo, mobile)
- Bottom nav com icone + rotulo curto + badge de notificacao por aba
- Indicador de aba ativa: border-top 2px solid var(--mc-emerald)

### PerfilPage.jsx - Ajustes de Wrapper
- Passado mobileLabels: { passe, recompensas, pedidos, conta, configuracoes } ao AnimatedTabs
- .perfil-conteudo-wrapper recebeu classe adicional .perfil-conteudo-com-bottom-nav
- Calendario: grid dos 7 dias envolvido em div.calendario-dias-wrapper para habilitar scroll horizontal mobile

### PerfilPage.css - Media Queries Mobile-First
- Bottom Nav: .perfil-tabs-mobile-nav, .perfil-tab-mobile-btn, .ativo, .tab-mobile-icon, .tab-mobile-label, .tab-mobile-badge
- Calendario Carrossel: .calendario-dias-wrapper com overflow-x auto, grid fixo em repeat(7, 160px)
- Trilha: .trilha-rotulos-coluna width 52px, texto dos rotulos oculto, apenas icones; cards em 155px
- Missoes: 1 coluna, .missao-botao-col width 100% padding-left 52px, btn-completar-missao width 100%
- Padding bottom-nav: .perfil-conteudo-com-bottom-nav padding-bottom 80px em <= 640px

## Build
- 2406 modules transformados - 0 erros

## Arquivos Modificados
- [[AnimatedTabs]]
- [[PerfilPage]]
