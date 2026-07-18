---
name: ditto
description: >-
  Apply visual/design changes to an existing app so the result matches a reference EXACTLY —
  computed-value accurate, not just "close." Use this whenever the user is implementing or matching
  a design and the output keeps coming out slightly off, whenever they say a design "isn't hitting
  it," "isn't matching," "looks close but wrong," "still off," "make it pixel-perfect," "build this
  out exactly," or "match the design," and whenever they hand over a reference (a Claude Design
  page or URL, exported HTML, a token file, a screenshot, or a Figma frame) and want the running app
  to look like it. Also trigger on narrower cues like "the spacing/padding/color/font is off,"
  "implement this component to spec," "why doesn't my CSS change take effect," or any design-parity
  task inside an existing codebase — even if the user never says the word "design." The core method:
  measure the reference as COMPUTED CSS values (never eyeballed from an image), map those onto the
  app's OWN token system, change one component and all its states at a time, then render the running
  app, inspect its computed styles, diff against the reference, and fix the actual cascade rule
  that's overriding the change — iterating until computed values match.
---

# Ditto

Copy a design reference **exactly** into an existing app — same as the original, down to the
computed pixel. Not "roughly," not "close enough." Ditto.

## Why this is hard (read this first — it changes everything)

When someone says "the design isn't hitting it," the instinct is to assume the model can't *see* or
*understand* the design. That's almost never the real problem — especially when the user has already
handed over HTML, tokens, or a live reference page. Comprehension is the easy part.

The reference renders perfectly **in isolation**, because nothing is competing with it. The failure
happens on the way *into* an existing, fully-built app, where the change collides with:

- **Cascade / specificity.** You set `padding: 12px`, but an existing rule (a global class, a
  component-library default, a parent selector, an `!important`) already wins. Your change is
  *correct and silently ignored*. Then the temptation is to pile on more overrides — that's the
  thrash that makes this "take forever."
- **Token indirection.** The app already themes itself through its own tokens (a Tailwind theme, CSS
  variables, a theme object, CSS-in-JS). The reference's raw values are a *different* set. Every
  change forces a choice: hardcode raw hex (bypasses the app's system, breaks dark mode and the
  spacing scale) or *guess* the mapping to the app's tokens. Guessing drifts, every time.
- **Container distortion.** The reference lives on a bare page. The real component lives inside the
  app's grid, max-widths, flex parents, resets, and `box-sizing`. Same CSS, different rendered result.
- **Partial application.** The reference shows one state. The real component has hover / focus /
  active / disabled, variants, responsive breakpoints, and dark mode. Applying the default state and
  missing the rest is why it reads as "80% right, still off."

So the whole method below is built to defeat those four forces: **measure the reference precisely,
apply through the app's own tokens, scope narrowly, then measure the *running app* and correct the
rule that's actually winning.** Do not try to nail it by reading code and reasoning about it — close
the loop with measurement, because the cascade is not fully predictable from source.

## The method

### 1. Capture the reference as computed values — not a picture

You cannot recover exact hex, `8px`-vs-`10px` spacing, or font weights from a screenshot; that
information is gone the moment it's an image. Get the *numbers*.

- **Live reference page (e.g. a Claude Design page in the browser):** use the browser/Chrome tooling
  to read the target element's **computed styles** directly from the rendered DOM
  (`getComputedStyle`), not a screenshot of it. Prefer reading the *specific* element you're editing
  over ingesting the whole page.
- **Exported HTML:** render it and read its computed styles the same way. Don't trust the *source*
  CSS alone — it may use shorthands, inherited values, or its own variables; what matters is the
  **computed** result.
- **A token file:** treat it as the source of truth for values, but still confirm how a real element
  composes them.

Pull the concrete properties that matter for the element at hand — typically:
`color`, `background-color`, `font-family`, `font-size`, `font-weight`, `line-height`,
`letter-spacing`, `padding`, `margin`, `gap`, `border`, `border-radius`, `box-shadow`, `width`,
`height`. Write the reference values down so you have an explicit target to diff against later.

**Avoid dumping the entire reference HTML + all tokens into context.** A giant paste gets skimmed,
not attended to. Look up the specific values for the specific element on demand instead.

### 2. Map onto the app's own token system (the "token bridge")

Before touching values, find out how *this* app themes itself — because a change made through the
app's tokens inherits its dark mode, spacing scale, and responsive behavior for free, while a raw
hardcode fights all of that.

Discover the system (see `references/token-systems.md` for stack-by-stack recipes): Tailwind config,
CSS custom properties, a theme object, CSS-in-JS, or a component library. Then translate the
reference values into that system:

- If the app already has a token that matches the reference value, **use the token**, not the raw value.
- If a mapping between the reference's tokens and the app's tokens doesn't exist yet, **establish it
  once** and record it (see step 7). This is the single biggest cure for drift: after the bridge
  exists, a design change becomes "apply token X," not "guess a hex."
- Only hardcode a raw value when the app genuinely has no token layer — and if you find yourself
  doing it repeatedly, that's the signal to propose adding one.

### 3. Scope to one component and *all* its states

Whole-screen rewrites thrash; small, complete diffs converge. Pick one component and enumerate what
"done" means for it before editing:

- states: default, hover, focus, focus-visible, active, disabled, loading/empty/error where relevant
- variants: sizes, kinds (primary/secondary), selected/unselected
- responsive breakpoints and dark mode

Match each against the reference. A component that's perfect in its default state but wrong on hover
is not done.

### 4. Apply the change

Make the edit through the token bridge, at the component level, for the states you enumerated.

### 5. Render the running app and measure it

This is the step that's usually missing when a design "won't hit." Reading your own diff tells you
what you *intended*; only the running app tells you what actually rendered after the cascade had its say.

- Start/reuse the dev server and open the actual route.
- Read the **computed CSS** of the real element you changed (use the preview/inspect tooling that
  returns computed values — this is far more reliable than a screenshot for spacing, color, and type).
- Diff **computed-against-computed**: the element's computed `padding` vs. the reference's computed
  `padding`, and so on down your list. Your target is a measured equality, not a vibe.
- Use a screenshot to catch layout/structure problems and to show the user proof — but decide
  fidelity from the computed numbers, not the picture.

### 6. When a value doesn't take, find the rule that's *winning*

If a computed value still doesn't match after you set it, it's almost always cascade/specificity —
your rule is losing to another. Don't stack more overrides or reach for `!important`; that's how the
thrash spiral starts and how the stylesheet rots.

Instead, inspect the element and find the rule that's actually applied (dev-tools-style: which
selector sets the winning value). Then fix it at that level — adjust the app's own component/token,
raise your selector to match intentionally, or remove the competing rule. Fixing the source of the
conflict once beats fighting it forever.

### 7. Iterate to zero, then record the bridge

Repeat 4–6 until the computed diff for the component is zero, then move to the next component.

Once per project, capture what you learned so the *next* change is fast, not another rediscovery.
Write a short `DESIGN-BRIDGE.md` (or add to the project's existing design notes) with:

- where the reference lives (the Claude Design page URL / the exported HTML / the token file)
- the app's token system and how to apply through it
- the token mapping (reference value/token → app token), even partial
- any known cascade gotchas (global resets, high-specificity rules, `!important` hotspots)

This artifact is what turns "takes forever every time" into "follows the same short loop every time,"
and it's why this skill pays off across future projects, not just today's.

## Anti-patterns (the fast way to stay stuck)

- **Eyeballing a screenshot** to derive values → you'll be permanently ~1px and one shade off.
- **Pasting the whole reference** (HTML + every token) into context → skimmed, not used.
- **Hardcoding raw hex/px** that bypasses the app's tokens → looks off in dark mode / other states, drifts.
- **Adding `!important` or deeper overrides** to force a value → wins the battle, rots the cascade,
  hides the real conflict.
- **Rebuilding the whole screen** at once → nothing is measurable, everything thrashes.
- **Declaring done from the diff** without rendering the running app → you verified intent, not result.

## Tooling notes

Tool names vary by environment; what matters is the *capability*:

- **Read the reference's computed styles** — browser/Chrome automation that can navigate to the
  Claude Design page (or open the exported HTML) and evaluate `getComputedStyle` on a selector.
- **Render the app and read *its* computed styles** — a preview/dev-server + an inspect capability
  that returns computed CSS for a selector (and a screenshot for structure and for showing the user).

If a capability is missing in the current environment, say so and fall back to the best available
(e.g. read the reference's source CSS and reason carefully), but flag that fidelity will be lower
without the measurement loop.
