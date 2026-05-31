# Design Team 🎯

> Your product design team — a Claude Code skill that puts five senior design specialists at your side, on demand.

**Design Team** is a design-intelligence skill for [Claude Code](https://docs.claude.com/en/docs/claude-code). Instead of one generic "make it prettier" response, it routes your request to the right specialist (or coordinates several) so you get the same rigor a real product design team would bring — research, visual craft, strategy, conversion, and systems thinking.

## The five specialists

| Role | What they own |
|------|---------------|
| 🔬 **UX Researcher** | User flows, journey mapping, usability heuristics, research synthesis |
| 🎨 **UI Designer** | Visual design, layout, typography, color, spacing, component craft |
| 🧭 **Product Strategist** | Problem framing, prioritization, information architecture, trade-offs |
| 📈 **Conversion Optimizer** | Funnels, CTAs, A/B testing, persuasion, friction removal |
| 🧱 **Design System Architect** | Tokens, components, consistency, accessibility, design-to-dev handoff |

## When it activates

The skill triggers automatically when you ask about UI/UX design, design reviews, conversion
optimization, wireframing, design systems, user research, accessibility, UX copy, visual design,
typography, color, design psychology, A/B testing, user-flow mapping, Google Stitch prompts, or
Figma work — and whenever you **share a Figma link, a Stitch screenshot, or any UI screenshot**.

Vague nudges work too:

- *"Make this better."*
- *"This feels off — why?"*
- *"How do I improve conversions on this page?"*
- *"Review this design."*

## What's inside

```
design-team/
├── SKILL.md                 # Entry point: roles, routing, workflow
└── references/
    ├── accessibility-checklist.md   # WCAG-oriented audit checklist
    ├── anti-patterns.md             # Common UX/UI mistakes to avoid
    ├── conversion-tactics.md        # Funnel & CTA optimization playbook
    ├── design-patterns.md           # Reusable interaction & layout patterns
    ├── prompt-templates.md          # Ready-to-use design prompts
    ├── stitch-figma-workflow.md     # Google Stitch → Figma build pipeline
    └── ux-psychology.md             # Cognitive principles behind good design
```

The skill uses **progressive disclosure**: `SKILL.md` stays focused on routing and method, while the
detailed playbooks live in `references/` and are pulled in only when a task needs them.

## Installation

Clone into your Claude Code skills directory so it's available across all projects:

```bash
git clone https://github.com/billzajac/design-team-claude-code-skill.git
cp -r design-team-claude-code-skill/design-team ~/.claude/skills/design-team
```

Or, for a single project, copy the `design-team/` folder into that project's `.claude/skills/`.

Verify it's loaded:

```
/skills
```

You should see **design-team** in the list.

## Usage

Just describe what you need in plain language — no special command required:

```
Review this checkout screen and tell me what's hurting conversions.
```

```
Here's a Figma link — audit it for accessibility and give me a prioritized fix list.
```

```
Help me design an onboarding flow for a habit-tracking app.
```

Claude will pull in the relevant specialist(s) and reference material automatically.

## Acknowledgments

Design Team is based on **Zarah's Pocket Team** — her original concept of carrying a full product
team in your pocket. This skill builds on that idea. Huge thanks to **Zarah** for the inspiration. 🙏

## License

[MIT](./LICENSE)
