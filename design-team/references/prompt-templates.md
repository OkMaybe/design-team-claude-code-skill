# Prompt Templates & Stitch Recipes

Structured thinking frameworks for design work and ready-to-use Google Stitch prompt recipes.

---

## Part 1: Design Frameworks

### 1. Design Brief Template

```
Context: [Project type, industry, user demographic]
Task: [Specific design deliverable needed]
Format: [Expected output: wireframe, mockup, specs, copy]
Tone: [Visual/verbal tone: professional, playful, premium, etc.]
Constraints: [Technical limits, brand guidelines, timeline]
```

**Usage:** Fill in each field before starting any design task. The brief keeps scope tight and prevents drift. Share with stakeholders for alignment before pixel work begins.

**Example:**
```
Context: B2B SaaS, developer tools, technical leads aged 28-45
Task: Redesign the onboarding flow to reduce time-to-first-value
Format: High-fidelity mockups for 5 screens with interaction annotations
Tone: Data-dense, precise, developer-friendly (think Linear, Vercel)
Constraints: Must use existing design system tokens, ship within 2 sprints
```

### 2. User Persona Template

```
Name: [Realistic name]
Age: [Age range]
Role: [Job title or life role]
Technical Comfort: [Novice / Intermediate / Advanced / Expert]

Goals (3 primary):
1. [What they want to achieve]
2. [What they want to achieve]
3. [What they want to achieve]

Frustrations (3 primary):
1. [What blocks or annoys them]
2. [What blocks or annoys them]
3. [What blocks or annoys them]

A Day in Their Life:
[2-3 sentences describing a typical day, focusing on moments
where your product fits into their workflow or routine.]

Quote:
"[A sentence that captures their mindset and attitude.]"

Behavioral Traits:
- [Trait relevant to product usage]
- [Trait relevant to product usage]
- [Trait relevant to product usage]
```

### 3. Design Critique Framework

```
First Impression: [Gut reaction in one sentence - what works, what feels off]
Strengths: [2-3 things done well, each with the reason it works]
Issues (severity-ranked):
  1. [Critical - blocks the user or breaks trust]
  2. [Major - hurts usability or conversion]
  3. [Minor - polish, consistency, nitpicks]
Recommendations: [Specific, actionable fix tied to each issue]
```

**Usage:** Use for any design review. Lead with what works, rank issues by user impact (not personal taste), and make every recommendation concrete and tied to a principle.

### 4. User Flow Template

```
Goal: [What the user is trying to accomplish]
Entry Point: [Where the flow begins - ad, email, nav, deep link]
Steps:
  1. [Screen/state] -> [user action] -> [system response]
  2. ...
Decision Points: [Where the path branches, and on what condition]
Success State: [What "done" looks like to the user]
Failure / Edge Cases: [Errors, empty states, drop-off risks]
```

**Usage:** Map the flow before designing screens. Every step should reduce friction toward the goal -- flag any step that adds work without adding value.

### 5. Competitive Teardown Template

```
Competitor: [Name + the product area reviewed]
What they do well: [Patterns worth borrowing, each with why]
Where they fall short: [Gaps, friction, dated patterns]
Differentiation opportunity: [The ONE thing we can own]
Takeaways: [Concrete decisions for our design]
```

**Usage:** Study 3-5 competitors before a redesign. The goal is informed differentiation, not imitation.

---

## Part 2: Stitch Prompt Recipes

Ready-to-use prompt skeletons for Google Stitch. Always generate 3+ variants and refine the winner in Figma. See references/stitch-figma-workflow.md for the full prompt library and the Stitch-to-Figma process.

### Recipe Structure

```
[Product type] + [Target audience] + [Vibe/feeling reference] + [Key features] + [Constraints]
```

### Ready-to-Use Prompts

**Landing page:**
```
A [industry] landing page for [audience], feeling like [brand reference]. Hero with a single
value proposition and one primary CTA, [3-4 key sections], social proof near the CTA.
Constraints: [brand colors/fonts], WCAG AA contrast, mobile-first.
```

**Dashboard:**
```
A [data type] dashboard for [user role], feeling like [Linear / Vercel / etc]. Overview metrics
row, [primary visualization], filters and date range. Dark mode, card-based layout, dense but
scannable hierarchy.
```

**Mobile app screen:**
```
A [category] mobile app [screen name] for [audience], feeling like [brand reference]. Primary
actions in the thumb zone, bottom navigation (3-5 tabs), [key feature]. 44px+ touch targets,
generous spacing.
```

**Usage:** Fill the brackets, then produce Exploratory / Directed / Precise variants (see SKILL.md). Score each on Distinctiveness / Usability / Conversion before moving to Figma.
