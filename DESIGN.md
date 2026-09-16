---
name: Prop4You Portfolio Atelier
locale: pt-BR
colors:
  background: hsl(39 28% 96%)
  foreground: hsl(216 34% 13%)
  primary: hsl(208 76% 39%)
  brand: hsl(22 88% 50%)
  border: hsl(35 16% 80%)
typography:
  display:
    fontFamily: Inter, ui-sans-serif, system-ui, sans-serif
  body:
    fontFamily: Inter, ui-sans-serif, system-ui, sans-serif
  mono:
    fontFamily: ui-monospace, SFMono-Regular, Consolas, monospace
rounded:
  surface: 1.125rem
---

# Prop4You Portfolio Atelier Design System

## Product context and visual intent

Portfolio Atelier is a calm, premium real-estate operating surface for Brazilian, Hispanic and US-based property investors. It pairs trustworthy editorial restraint with clearly actionable product controls. Auth and onboarding prioritize comprehension, keyboard access and low-friction progression over decoration.

## Color palette and tokens

The runtime authority is `backend/src/interfaces/web/frontend/src/index.css`.

- Background: `hsl(39 28% 96%)`; surfaces: white and `hsl(38 24% 94%)`.
- Foreground: `hsl(216 34% 13%)`; muted text: `hsl(216 12% 42%)`.
- Primary action: `hsl(208 76% 39%)`; brand signal: `hsl(22 88% 50%)`.
- Status: destructive `hsl(6 70% 48%)`, success `hsl(150 55% 32%)`, warning `hsl(36 86% 44%)`, info `hsl(205 74% 42%)`.
- Borders: `hsl(35 16% 80%)`; base radius: `1.125rem`.

## Typography and layout

- UI and headings use Inter with system sans fallbacks; technical metadata uses the mono token.
- Default copy is pt-BR; English and Spanish are supported only through the shared i18n catalog.
- Auth surfaces are single-purpose, responsive forms. No critical action may require hover, pointer-only interaction or JavaScript-only submission.
- Supported view matrix: mobile `360×740`, `390×844`, `430×932`; tablet `768×1024`, `834×1194`, `1024×1366`; desktop `1280×800`, `1440×900`, `1920×1080`.

## Components and states

- ReUI is the global component authority for every product route and shared
  frontend surface. Use governed adapters from `src/components/reui/`; never
  vendor examples directly into runtime pages.
- Select visual behavior through typed `variant`, `size`, `width`, orientation
  and state props. Pages and feature components must not pass skin-oriented
  `className` to ReUI components.
- Primitive CSS is owned by `.reui-*`, `data-variant`, `data-size` and semantic
  tokens. Context selectors such as `.feature .reui-input` are prohibited.
- Repeated control + label or option structures must be compounds (for example
  `CheckboxField` and `RadioGroupOption`), not page-local raw labels or div soup.
- Native visible form controls are implementation details of ReUI adapters;
  pages may keep only hidden inputs required by server-authoritative HTML POST.
- Every variant/state used by product routes must be represented in the
  `/design-system/` preview and pass `npm run audit:reui-governance`.
- Every form field has an explicit label, programmatic error association, invalid state and server-authoritative validation.
- Use native/selectable form controls inside ReUI adapters whenever form POST compatibility matters.
- OTP, password visibility, plan choice and profile facts must expose valid keyboard and screen-reader semantics.
- Controls render idle, focus, invalid, disabled and success/status states where applicable.
- Progressive validation stays absent while a field is empty. After the user
  enters, pastes or autofills a value, unmet criteria use destructive color plus
  an explicit failure icon and met criteria use success color plus a check; color
  alone never carries status. Clearing the value restores the untouched state.
- Password-strength UI uses one segmented meter plus the compact criteria row;
  visible labels such as `Weak`, `Not started` and `Very strong` are redundant
  and prohibited. Equivalent progress remains available to assistive technology.

## Motion, brand voice and anti-patterns

- Motion is short, non-blocking and respects reduced motion; no bounce easing for product-critical UI.
- Use direct task-oriented labels and specific recovery/rate-limit feedback. Do not expose internal IDs, route metadata, state-machine codes or diagnostic chrome.
- A base das páginas usa a cor sólida `--background`; gradientes são permitidos apenas em detalhes de estado ou elementos decorativos confinados, nunca como tratamento do fundo do shell.
- `.portfolio-atelier-dark` é uma superfície explícita de preview e referência do design system. Ela não é ativada por preferência de sistema nem deve chegar a uma rota de produto sem decisão registrada e prova visual própria.
- Avoid decorative icon-only controls, generic feature grids and vendor/demo UI in product routes.
