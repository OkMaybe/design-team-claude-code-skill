# Discovering and applying through an app's token system

The goal of this file: figure out *how this specific app themes itself*, so a design change goes
through its native tokens (and inherits dark mode / spacing scale / responsive behavior) instead of
fighting it with raw values. Read the section that matches what you find. Detect first, then apply.

## How to detect which system is in use

Look, in roughly this order:

1. `tailwind.config.{js,ts,cjs}` or `@theme` / `@config` in a CSS file → **Tailwind**.
2. A CSS file full of `--token-name: value;` under `:root` / `[data-theme]` → **CSS custom properties**.
3. `styled-components` / `@emotion` imports, a `theme.ts`/`theme.js`, or a `<ThemeProvider>` →
   **CSS-in-JS + theme object**.
4. `@mui/material`, `@chakra-ui`, `antd`, shadcn/ui (`components/ui/*` + CSS vars) →
   **component library** (each has its own theming entry point).
5. `.scss`/`.sass` with `$variables` or `@use` maps → **Sass**.
6. None of the above, just hand-written CSS/`.module.css` → **plain CSS** (consider proposing a token layer).

An app can mix these (e.g. Tailwind *driven by* CSS variables — very common in shadcn). When mixed,
the CSS-variable layer is usually the real source of truth; Tailwind classes just reference it.

## Tailwind

- Values live in `theme.extend` (colors, spacing, fontSize, borderRadius, boxShadow…). A reference
  value should map to an existing key when one matches (`text-slate-700`, `p-3`, `rounded-lg`).
- If the exact value isn't in the scale, don't inline `style={{padding:'12px'}}` or `p-[12px]` as a
  reflex — check whether the design implies a *new scale token* that belongs in the config. One-offs
  are fine sparingly (`p-[13px]`), but repeated one-offs mean the scale is missing a step.
- Tailwind v3+ often maps colors to CSS variables (`--background`, `--primary`) — if so, change the
  variable, and every utility that references it updates. Confirm in `globals.css`/`:root`.
- Dark mode: values usually differ under `.dark` or `[data-theme=dark]`. Match both.

## CSS custom properties (design tokens)

- Change the token at its definition (`:root { --space-3: 12px; }`), not at every call site, so the
  change propagates and stays consistent.
- Check for **theme scopes**: tokens frequently get redefined under `[data-theme="dark"]`, `.dark`,
  or a media query. A change that looks wrong in dark mode usually means you edited only the light scope.
- Watch for **aliasing**: `--button-bg: var(--color-primary)`. Decide whether the design change
  belongs at the primitive (`--color-primary`, affects everything) or the semantic alias
  (`--button-bg`, affects only buttons). Getting this level right is what prevents over-broad changes.

## CSS-in-JS + theme object (styled-components / emotion)

- Find the `theme` object (often `theme.ts`). Components read `props.theme.colors.primary`,
  `theme.space[3]`, etc. Apply the change in the theme object when the value is a shared token.
- For a component-specific tweak, edit that component's styled block — but prefer referencing theme
  tokens (`${({theme}) => theme.space[3]}`) over literals so it stays consistent and themeable.
- Specificity is generated at runtime; conflicts usually come from prop-based variants or a parent
  styled component. When a value won't take, check the variant logic and any `&&`/nested selectors.

## Component libraries

- **MUI:** theme via `createTheme(...)` (`palette`, `spacing`, `typography`, `components.MuiX`
  overrides). Global changes go in the theme; per-instance goes via `sx`. Beware MUI's own
  specificity — `sx` usually wins, but component `styleOverrides` may not.
- **Chakra:** extend the theme (`extendTheme`), use tokens/`theme` scale keys; per-instance via style props.
- **shadcn/ui:** it's your code + CSS variables. Edit the component in `components/ui/*` and the CSS
  vars in `globals.css`. This is the "mixed Tailwind + CSS vars" case — the vars are the source of truth.
- **Ant Design:** `ConfigProvider` theme tokens; component-level via `theme.components`.

## Sass

- Change the `$variable` or map entry at its definition and recompile. Confirm the dev server picks
  up the recompiled CSS (some setups need a restart / watch to re-emit).
- Sass variables are compile-time only — they won't respond to runtime theme switching, so if the app
  also has a runtime dark mode, the real switching layer is probably CSS variables, not Sass.

## Plain CSS / CSS Modules

- There may be no token layer. Apply the value, but if you're repeating the same hex/px across files,
  that's the moment to *propose* introducing CSS variables — it's the cheapest lasting fix for drift
  and makes every subsequent design change a one-line edit.
- CSS Modules scope class names but not values; a global stylesheet or reset can still win the
  cascade. When a value won't take, check global CSS and element/tag selectors, not just the module.

## After you apply — always

Whatever the system, the value only counts once it survives the cascade in the running app. Render
the route, read the element's **computed** style, and diff it against the reference's computed style.
If they don't match, the token was overridden downstream — go find the winning rule.
