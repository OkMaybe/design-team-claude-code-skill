# Stitch + Figma Workflow Guide

## Phase 1: Stitch Exploration

### Vibe Design Prompt Structure
[Product type] + [Target audience] + [Vibe/feeling reference] + [Key features] + [Constraints]

Example: A premium fintech dashboard for millennial investors, feeling like Linear meets Stripe -- clean data visualization, dark mode, card-based layout with real-time portfolio tracking

### Multi-Screen Generation Strategy
1. Start with the core screen (homepage, dashboard, or key action screen)
2. Generate related screens from the core context
3. Connect screens into interactive prototype flows
4. Use Shift+click to multi-select and apply unified theme changes

### Variant Generation
- Always generate 3-5 options using different vibe references
- Compare variants side-by-side on the canvas
- Mix elements from multiple variants in Figma refinement

### Evaluation Before Moving to Figma
- Does it avoid generic AI patterns?
- Is the visual hierarchy clear?
- Does each screen serve a specific user goal?
- Is the layout distinctive or template-like?

## Phase 2: Stitch Review and Selection

### Scoring Dimensions
Rate each variant 1-5 on three dimensions:
- **Distinctiveness**: Would it stand out from competitors?
- **Usability**: Is the hierarchy clear, navigation intuitive?
- **Conversion Potential**: Does it guide users toward the desired action?

### Selection Process
- If no variant scores above 3 on all dimensions, re-prompt with more specifics
- Document WHY the winning direction was chosen (feeds into design rationale)
- Identify best elements from each variant to combine in Figma

## Phase 3: Figma Transition

### Export Process
One-click export preserves Auto Layout structure and editable layers.

### Figma Cleanup Checklist (run immediately after export)
- [ ] Rename all layers semantically (no Frame 427, Group 12)
- [ ] Convert repeated elements to components with variants
- [ ] Apply Auto Layout to all containers
- [ ] Extract colors to Figma styles or variables
- [ ] Extract typography to text styles
- [ ] Normalize spacing to 8px grid
- [ ] Replace generic/default fonts with brand typography
- [ ] Verify color contrast meets WCAG AA
- [ ] Remove unused layers or hidden elements
- [ ] Set up page structure (Cover, Components, Screens, Flows)

## Phase 4: Figma Refinement

### Production Polish
- Apply design-patterns.md rules
- Run conversion-tactics.md against the layout
- Review typography: heading hierarchy, line lengths, weights
- Review color: brand consistency, semantic usage, contrast
- Review spacing: consistent rhythm, whitespace, grid alignment

### Interaction States
Add for every interactive element:
- Default, Hover, Focus, Active/Pressed, Disabled, Loading, Error, Empty

### Responsive Behavior
Define at key breakpoints:
- 375px (mobile), 768px (tablet), 1280px (desktop)
- Document what changes at each breakpoint

### Component Documentation
- Create variants for all states and sizes
- Document usage guidelines (when to use, when not to use)
- Add micro-interactions: hover states, focus animations, transition specs

## Phase 5: Code Export and Handoff

### Stitch HTML/CSS Review
- Check for semantic HTML tags (not just divs)
- Verify heading hierarchy
- Check meaningful class names
- Verify accessibility attributes (ARIA, alt text)
- Check responsive media queries

### Figma Dev Mode
- Measurements, spacing, color values, typography specs
- Export assets at required resolutions

### Design Token Export
Export as JSON or CSS custom properties:
- Colors (brand, semantic, neutral)
- Typography (families, sizes, weights, line heights)
- Spacing (scale values)
- Elevation (shadow definitions)
- Border radius values

### Handoff Documentation
- Component inventory with usage guidelines
- Interaction specifications (timing, easing, triggers)
- Responsive behavior notes
- Edge cases and error states
- Accessibility requirements

## Stitch Prompt Library

### Landing Pages by Industry
- **SaaS**: Pricing page with tiers, toggle, comparison table, feeling like Stripe/Vercel
- **E-commerce**: Product detail with gallery, variants, reviews, feeling like Apple Store
- **Portfolio**: Creative showcase with project grid, about, contact CTA
- **Healthcare**: Wellness landing with benefit cards, testimonials, download CTA
- **Fintech**: Dashboard landing with feature highlights, security badges, demo CTA
- **Education**: Course landing with curriculum, instructor bio, enrollment CTA
- **Marketplace**: Two-sided homepage with search, categories, featured listings
- **Real Estate**: Property listing with gallery, details, map, contact CTA
- **Food/Restaurant**: Menu, reservations, gallery, reviews
- **Non-profit**: Donation page with impact story, tiers, progress bar

### Dashboards by Data Type
- **Analytics**: Metrics overview, charts, filters, date ranges
- **Finance**: Portfolio, transactions, performance graphs
- **Project Management**: Kanban, timeline, team workload
- **CRM**: Contact list, pipeline, activity feed
- **Healthcare**: Patient records, vitals, appointments
- **IoT/Monitoring**: Real-time sensors, alerts, status maps
- **Marketing**: Campaign performance, audience segments, ROI
- **Developer Tools**: API metrics, logs, deployment status

### Mobile Apps by Category
- **Social**: Feed, profiles, messaging, discovery
- **Productivity**: Task lists, calendar, notes, collaboration
- **Health/Fitness**: Activity tracking, goals, workout plans
- **Marketplace**: Browse, search, product detail, cart
- **Banking**: Accounts, transfers, spending insights
- **Travel**: Search, booking, itinerary, maps
- **Learning**: Course catalog, lessons, progress, quizzes
- **Messaging**: Conversations, contacts, media sharing

### Vibe Anchor Reference

| Feeling | Brand References |
|---------|----------------|
| Premium/Sophisticated | Stripe, Apple, Aesop |
| Playful/Friendly | Duolingo, Notion, Figma |
| Data-Dense/Precise | Linear, Vercel, GitHub |
| Editorial/Content-First | Medium, Substack, NYT |
| Warm/Human | Headspace, Airbnb, Mailchimp |
