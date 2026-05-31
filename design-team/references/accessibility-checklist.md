# Accessibility Checklist (WCAG 2.1 AA)

## Perceivable

- [ ] Text contrast >= 4.5:1 (normal text), >= 3:1 (large text 18px+ or 14px+ bold)
- [ ] Non-text contrast >= 3:1 (icons, borders, focus rings, form controls)
- [ ] No information conveyed by color alone (add icons, patterns, or text)
- [ ] Images have meaningful alt text (or alt="" for decorative)
- [ ] Complex images have long descriptions
- [ ] Video has captions; audio has transcripts
- [ ] Content reflows at 320px width without horizontal scroll
- [ ] Text resizable to 200% without loss of content
- [ ] No text in images (use real text with CSS)
- [ ] Audio does not autoplay

## Operable

- [ ] All interactive elements reachable by keyboard (Tab, Enter, Space, Arrows)
- [ ] Focus order follows visual/logical reading order
- [ ] Focus indicators clearly visible (2px+ solid outline with offset)
- [ ] Skip-to-content link as first focusable element
- [ ] No keyboard traps
- [ ] Touch targets >= 44x44px (48x48 preferred)
- [ ] Sufficient spacing between touch targets (8px+ gap)
- [ ] Respects prefers-reduced-motion
- [ ] No content flashing more than 3 times per second
- [ ] Timeout warnings with option to extend
- [ ] Multiple ways to find content (search, sitemap, nav)
- [ ] Link purpose clear from text alone (no click here)

## Understandable

- [ ] lang attribute set on html element
- [ ] Language changes marked on inline elements
- [ ] Form labels explicitly associated with inputs (for/id)
- [ ] Required fields clearly indicated (not by color alone)
- [ ] Error messages identify field and suggest correction
- [ ] Error messages appear near the relevant field
- [ ] Consistent navigation across pages
- [ ] Consistent identification of repeated components
- [ ] No unexpected context changes on input
- [ ] Instructions independent of sensory characteristics

## Robust

- [ ] Valid HTML (proper nesting, unique IDs)
- [ ] ARIA used correctly (valid roles, required states)
- [ ] Heading hierarchy logical (no skipped levels)
- [ ] Landmark regions defined (main, nav, banner, contentinfo)
- [ ] Dynamic content updates announced (aria-live)
- [ ] Status messages programmatically determinable
- [ ] Custom components have appropriate ARIA roles + keyboard behavior
- [ ] Name, role, value programmatically determinable for all UI components

## Quick Audit Shortlist (Top 10)

Run these first for maximum impact:
1. Color contrast ratios (4.5:1 text, 3:1 large)
2. Keyboard navigation works for all interactive elements
3. Focus indicators visible
4. Images have alt text
5. Form labels associated with inputs
6. Heading hierarchy is logical
7. Touch targets >= 44px
8. No color-only information
9. Error messages are specific and near the field
10. Reduced motion support
