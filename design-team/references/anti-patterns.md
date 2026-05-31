# Design Anti-Patterns

## Visual Anti-Slop Rules

NEVER default to these without explicit reason:
- Roboto or Arial as brand/display fonts -- choose distinctive typography for headlines (Inter Regular/Medium is fine as the default UI/body font)
- Purple-on-white gradients as default aesthetic
- Generic card grids with rounded corners and drop shadows everywhere
- Stock photography of people in offices looking at laptops
- Identical 8px spacing on everything -- use a varied rhythm
- Glassmorphism or neumorphism without functional purpose
- Emoji as primary iconography in professional interfaces
- "Clean and modern" is NOT a design direction -- it is a cop-out

## UX Anti-Patterns

- Mystery meat navigation: icons without text labels
- Infinite scroll without back-to-top or position memory
- Modal on modal: never stack dialogs
- Dark patterns: hidden unsubscribe, pre-checked consent, confirm-shaming
- Form fields that clear on validation error
- Are you sure? for every action (alarm fatigue)
- Autoplay video or audio without user consent
- Breaking the browser back button
- Unexpected navigation on click (new tabs without indication)

## Copy Anti-Patterns

- Welcome to our platform (says nothing specific)
- Click here or Learn more without context
- Error messages that blame the user (Invalid input vs Please enter a valid email)
- Placeholder text as the only label (disappears on focus)
- ALL CAPS for anything longer than 2 words
- Technical jargon in user-facing copy
- Passive voice in CTAs (Your order will be placed vs Place my order)
- Lorem ipsum in delivered designs

## Conversion Anti-Patterns

- Multiple competing CTAs in same viewport
- Asking for email/signup before showing any value
- Trust badges that nobody recognizes
- Social proof from Anonymous or unverifiable sources
- Progress bars that lie or jump backwards
- Exit-intent popups on first visit
- Forced account creation before purchase
- Hiding pricing until the last step

## Architecture Anti-Patterns

- Tokens named by appearance (blue-500) instead of purpose (color-primary)
- Components with more than 5 boolean props (combinatorial explosion)
- Breakpoint spaghetti (different behavior at every viewport width)
- z-index arms race (z-index: 9999)
- !important as a first resort
- Inline styles mixed with CSS classes without convention
- Inconsistent naming (camelCase + kebab-case + snake_case in same system)
- No design token documentation

## Stitch-Specific Anti-Patterns

- Accepting the first Stitch generation without exploring 3+ variants
- Using Stitch default typography in production without brand alignment
- Skipping Figma refinement -- Stitch is exploration, not production
- Exporting Stitch HTML/CSS directly without semantic review
- Not checking Stitch output against WCAG accessibility standards
- Assuming Stitch understands your brand -- always apply guidelines post-generation
- Generating single screens when multi-screen flows give better context
