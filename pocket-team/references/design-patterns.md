# Design Patterns Reference

## 1. Layout Patterns

**Card Grid**: Equal-width cards in responsive grid. Use for: product listings, feature showcases, team pages.
**Split Screen**: Two equal columns, often image + content. Use for: hero sections, comparisons, signup pages.
**Bento Grid**: Mixed-size cards in asymmetric grid. Use for: dashboards, portfolios, feature highlights.
**Asymmetric Layout**: Intentional imbalance creates visual interest. Use for: editorial, creative portfolios.

**Hero Patterns**:
- Full-bleed: Background image/video fills viewport. High impact, use for brand storytelling.
- Split: Content left, image right (or reverse). Best for SaaS, product pages.
- Centered: Text centered, minimal visual. Best for launch pages, announcements.
- Animated: Motion-driven hero. Use sparingly for high-impact moments.

**Navigation Patterns**:
- Top bar: Standard for desktop. Logo left, nav center or right, CTA far right.
- Side nav: Persistent left sidebar. Best for dashboards, admin panels.
- Bottom nav (mobile): 3-5 tabs max. Primary actions in thumb zone.
- Mega menu: For large sites with many categories. Show structure visually.
- Hamburger: Last resort -- hides navigation behind a click. Use only when space is critical.

## 2. Typography System

**Type Scale Ratios**:
- Minor Third (1.2): Subtle differences. Good for dense UIs, dashboards.
- Major Third (1.25): Balanced. Good general purpose.
- Perfect Fourth (1.333): Clear hierarchy. Good for marketing, editorial.
- Golden Ratio (1.618): Dramatic. Good for expressive, brand-heavy designs.

**Hierarchy Levels**: Display (hero text) > H1 > H2 > H3 > H4 > Body > Small > Caption > Overline

**Line Height Rules**:
- Display text: 1.1 - 1.2 (tight)
- Headings: 1.2 - 1.3
- Body text: 1.5 - 1.6
- Long-form reading: 1.6 - 1.8

**Measure (Line Length)**: 45-75 characters for body text. 20-40 for headlines. Max 90 for wide layouts.

**Font Pairing Strategies**:
- Contrast: Serif heading + sans body (or reverse). Creates clear hierarchy.
- Superfamily: Same typeface family for heading + body (e.g. Inter + Inter Display).
- Weight contrast: Same font, different weights. Minimal but effective.
- Monospace accent: Mono for code, data, labels alongside a proportional body font.

**Web Font Loading**: Use font-display: swap. Preload critical fonts. Prefer WOFF2 format. Limit to 2 families, 4 weights max.

## 3. Color System

**60-30-10 Rule**: 60% dominant (background), 30% secondary (cards, sections), 10% accent (CTAs, links).
**Semantic Colors**: Success (green), Warning (amber), Error (red), Info (blue). Consistent across app.
**Neutral Palette**: Minimum 9 steps from near-white to near-black. Use for text, borders, backgrounds.
**Dark Mode**: Not just inverted -- reduce overall contrast, increase surface elevation, desaturate vivid colors, use darker shadows not lighter.
**Color Accessibility**: 4.5:1 contrast for normal text, 3:1 for large text (18px+ or 14px+ bold). Never convey information by color alone.

## 4. Spacing and Grid

**Base Unit**: 4px or 8px. All spacing should be multiples of this unit.
**Spacing Scale**: 4, 8, 12, 16, 24, 32, 48, 64, 96. Use consistently.
**Grid Systems**: 12-column desktop, 8-column tablet, 4-column mobile. Gutter: 16-32px.
**Breakpoints**: 375px (mobile), 768px (tablet), 1024px (laptop), 1280px (desktop), 1536px (wide).
**Container Max-Width**: 1200-1440px for content. Full-bleed for heroes.

## 5. Component Patterns

**Button Hierarchy**: Primary (filled, brand color), Secondary (outlined), Tertiary (text only), Ghost (transparent), Destructive (red). One primary per view.

**Form Design**: Labels above inputs (not placeholder-only). Group related fields. Validate on blur for most fields, on submit for complex ones. Show error messages inline below the field.

**Modal/Dialog**: Confirmation (destructive actions), Informational (read content), Form (collect input). Max width 480-640px. Always have a close mechanism. Trap focus inside.

**Empty States**: Illustration + clear explanation + primary action. Turn absence into opportunity.

**Loading Patterns**: Skeleton screens (preferred) > progress bars (for known duration) > spinners (last resort). Never show blank screens.

**Error Handling**: Inline validation > toast notifications > error pages. Always provide recovery path. Never just say Error.

**Navigation Components**: Breadcrumbs (for deep hierarchies), Tabs (for same-page content switching), Pagination (for lists), Steppers (for multi-step flows).

## 6. Motion and Animation

**Duration Guidelines**:
- Micro-interactions (hover, focus, toggle): 100-150ms
- Transitions (expand, slide, fade): 200-300ms
- Page transitions: 300-500ms
- Complex animations: 500-1000ms

**Easing Functions**:
- ease-out: Elements entering the screen (decelerating)
- ease-in: Elements leaving the screen (accelerating)
- ease-in-out: Elements moving position

**Performance**: Use transform and opacity only for 60fps. Avoid animating layout properties (width, height, margin). Use will-change sparingly.

**Reduced Motion**: Always support @prefers-reduced-motion: reduce. Replace motion with opacity fades. Never rely on animation for meaning.

**Principles**: Every animation needs a purpose. If you cannot explain why it moves, it should not move.
