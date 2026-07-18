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

## Companion skill: Ditto 📐

This repo also ships **Ditto** — a second, complementary skill for a different job: getting an
existing app to match a design reference *exactly*, computed-value accurate rather than just "close."

Where Design Team helps you *decide* what good looks like, Ditto helps you *reproduce* a finished
design faithfully in a real, already-built codebase. It measures the reference's exact computed CSS
(instead of eyeballing a screenshot), applies changes through the app's **own** token system, renders
the running app, diffs computed value against computed value, and tracks down the cascade rule that's
overriding a change — iterating until it truly matches. It triggers on cues like *"it's not hitting
it,"* *"looks close but wrong,"* or *"make it pixel-perfect."*

```
ditto/
├── SKILL.md                    # The fidelity method
└── references/
    └── token-systems.md        # Finding & applying an app's token system, stack by stack
```

## Installation

Clone into your Claude Code skills directory so it's available across all projects:

```bash
git clone https://github.com/billzajac/design-team-claude-code-skill.git
cp -r design-team-claude-code-skill/design-team ~/.claude/skills/design-team
cp -r design-team-claude-code-skill/ditto ~/.claude/skills/ditto
```

Or, for a single project, copy the `design-team/` folder into that project's `.claude/skills/`.

Verify it's loaded:

```
/skills
```

You should see **design-team** and **ditto** in the list.

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
