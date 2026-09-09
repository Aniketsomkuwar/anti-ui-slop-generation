---
name: anti-ai-slop-reference
description: Detect and flag AI-generated low-quality or misleading content (slop) with comprehensive pattern catalog and tracking, expanded v3.1.0
version: \"3.1.0\"
argument-hint: \"[--scan] [--list] [--clear]\"
allowed-tools:
  - Read
  - Write
  - AskUserQuestion
---

<objective>
Provide comprehensive design reference for AI-assisted UI generation, documenting 100+ AI slop patterns across 14 categories (Visual, Typography, Color/Contrast, Layout/Space, Motion, Copy, Imagery, Quality, Accessibility, Design-Token, State Coverage, Real-Content Stress Test, Responsive Consistency, Interaction Feedback, Dark Mode/Theme Parity). This skill serves as the design knowledge base that AI agents read before generating UI, while anti-ai-slop-real serves as the operational skill that detects and tracks slop in existing codebases. Extends v2.0.0 catalog with 30 new patterns covering component states, content stress testing, responsive consistency, interaction feedback, and dark mode parity.
</objective>

<routing>

| Flag | Action | Description |
|------|--------|-------------|
| (none) | Scan mode | Scan files for slop indicators (operational skill) |
| --list | List tracked slop items | Show all previously identified slop with status, grouped by category |
| --clear | Clear resolved slop entries | Remove tracked slop items from storage |
| --scan PATH | Scan specific path | Run operational scan (anti-ai-slop-real) |

</routing>

<process>

<step name=\"init_context\">
Ensure directories exist (use cwd if available, fallback to home):
```bash
# Docs stored in current working directory for project-local tracking
# Fallback to ~/.hermes/slop-tracker/ if no cwd detected
mkdir -p ./slop-tracker
mkdir -p ./references
mkdir -p ./notes
# Also create legacy path for backward compatibility
mkdir -p ~/.hermes/slop-tracker
```
</step>

<step name=\"reference\">
Provide design reference for AI-assisted UI generation. Show pattern catalog with all 100+ patterns across 14 categories. Every finding uses evidence model (Source/Render/Judgment/Confidence) plus severity (blocker/major/nit) and auto_fix boolean tag, logged to slop-log.json under D-category (Design-Token/Drift).
</step>

</process>

<pattern_catalog_summary>
Total patterns: 100+

Visual: V1-V17 (17 patterns)
Typography: T1-T15 (15 patterns)
Color and Contrast: C1-C6 (6 patterns)
Layout and Space: L1-L9 (9 patterns)
Motion: M1-M8 (8 patterns)
Copy: P1-P9 (9 patterns)
Imagery: I1-I6 (6 patterns)
General Quality: Q1-Q8 (8 patterns)
Accessibility: A1-A8 (8 patterns) NEW
Design-Token / Drift Detection: D1-D6 (6 patterns) NEW
State Coverage: S1-S8 (8 patterns) NEW
Real-Content Stress Test: R1-R6 (6 patterns) NEW
Responsive/Breakpoint Consistency: B1-B5 (5 patterns) NEW
Interaction Feedback Audit: F1-F6 (6 patterns) NEW
Dark Mode / Theme Parity: DM1-DM5 (5 patterns) NEW

</pattern_catalog_summary>

<pattern_catalog_detail>

### Visual Details (V1-V17)
- V1: Border accent on rounded element (>=2px border + >=12px radius)
- V2: Glassmorphism everywhere (translucent cards + backdrop-filter: blur)
- V3: Side-tab accent border (colored border >=3px on card side)
- V4: Hairline border with wide shadow (1px border + >=20px shadow blur)
- V5: Repeating-gradient stripes on surfaces
- V6: Extreme border radius (>=24px turns cards into blobs)
- V7: Amateurish hand-drawn SVG (complex inline SVG with rough geometry)
- V8: Generic AI icons (sparkle, star, magic, lightning, diamond, robot, AI orb)
- V9: Lucide icons (every icon from same thin-stroke library)
- V10: Colored left stripe (thin vertical bar on card/section edges)
- V11: Small arrows (→/↗) on almost every button as decoration
- V12: AI capsule badges (pill shape, thin border, glow, uppercase \"AI Powered\", etc.)
- V13: Generic AI typography (large monospace headings, HOW IT WORKS uppercase with wide tracking)
- V14: Typeface chosen without reason (font picked as AI default, not brand fit)
- V15: Generic illustrations (Undraw, Storyset, 3D blob with no product connection)
- V16: Mixed icon styles in one view (outline + filled + duotone)
- V17: Leftover placeholder images (lorem-picsum, unsplash-random) in production build

### Typography (T1-T15)
- T1: Flat type hierarchy (adjacent roles differ <1.25x, lack contrast)
- T2: Icon tile stacked above heading (repeated feature cards)
- T3: Italic serif display headline (serif italic >=32px in generic startup hero)
- T4: Hero eyebrow or pill chip (tracked uppercase text above hero heading)
- T5: Repeated section kickers (3+ sections with same uppercase tracked label)
- T6: Oversized hero headline (8+ words with >=48px or text-5xl styling)
- T7: Crushed letter spacing (display tracking < -0.05em, body with negative tracking)
- T8: Overused font (Inter, Geist, Space Grotesk, Instrument Serif as default identity)
- T9: Single font for everything (one family with identical weight/width/spacing across roles)
- T10: All-caps body text (paragraphs/long blocks >=20 words in uppercase)
- T11: \"It's not just X, it's Y\" / \"more than just a Z\" construction
- T12: Buzzword stacking (seamless, leverage, unlock, elevate, robust, cutting-edge)
- T13: Em-dash overuse as a sentence-structure crutch (3+ em-dashes in body block)
- T14: Inflated fake urgency/stats with no source (\"only 3 spots left\", \"10,000+ happy customers\")
- T15: Rule-of-three headline tic (\"Fast. Reliable. Secure.\")

### Color and Contrast (C1-C6)
- C1: AI color palette (purple/violet gradients or cyan-on-dark without brand evidence)
- C2: Dark mode with glowing accents (dark surfaces with colored box shadows/neon text)
- C3: Gradient text (background-clip: text + transparent fill on headings/metrics)
- C4: Gray text on colored background (neutral gray on chromatic surface, loses contrast)
- C5: Cream/beige reflex (warm off-white as whole page's generic surface without palette)
- C6: Contrast failing WCAG AA (<4.5:1 normal text, <3:1 large text)

### Layout and Space (L1-L9)
- L1: Hero metric layout (centers large number, tiny label, supporting stats with generic treatment)
- L2: Identical card grids (4+ siblings with identical icon/heading/paragraph sizing)
- L3: Monotonous spacing (same gap/padding token for item/group/component/section boundaries)
- L4: Nested cards (3+ nested levels repeating borders/fills/radii/shadows)
- L5: Numbered section markers (01/02/03 labels for independent sections)
- L6: Line length too long (>80 chars per line running text)
- L7: Content overflowing its container (text/media spills, clips, accidental horizontal scroll)
- L8: Positioned child clipped by overflow container (tooltip/menu/popover cut by overflow:hidden/clip)
- L9: Non-semantic markup (div-soup instead of button/nav/main/header)

### Motion (M1-M8)
- M1: Bounce or elastic easing (dialogs/cards/routine controls with overshoot/spring effects)
- M2: Layout-property animation (width/height/padding/margin/top/left causing reflow)
- M3: Image hover transform (generic cards repeatedly scale/rotate on hover)
- M4: Blanket scroll-fade-in applied to every section indiscriminately
- M5: Uniform 300ms ease-in-out duration regardless of element size/distance
- M6: Reflexive hover:scale-105 / lift-shadow on non-interactive cards
- M7: No respect for prefers-reduced-motion
- M8: Staggered-list-reveal cliché applied to non-list content

### Copy (P1-P9)
- P1: Em-dash overuse (3+ em-dash characters in body block)
- P2: Marketing buzzword (supercharge, streamline, empower, world-class, enterprise-grade, seamlessly, unlock)
- P3: Aphoristic cadence (Multiple sections repeat Not X. Y. or Less X. More Y. patterns)
- P4: Theater framing copy (Marketing dismisses category as theater without explaining practical failure)
- P5: \"It's not just X, it's Y\" / \"more than just a Z\" construction
- P6: Buzzword stacking (supercharge, leverage, unlock, elevate, robust, cutting-edge)
- P7: Em-dash overuse as a sentence-structure crutch
- P8: Inflated fake urgency/stats with no source (\"only 3 spots left\", \"10,000+ happy customers\")
- P9: Rule-of-three headline tic (\"Fast. Reliable. Secure.\")

### Imagery (I1-I6)
- I1: Broken or placeholder image (missing/empty src, #, known placeholder services, placeholder API paths)
- I2: Generic stock-photo tells (diverse-team-laughing-at-laptop, handshake close-up, lightbulb-idea shot)
- I3: AI-image generation artifacts (garbled embedded text, malformed hands, uncanny facial symmetry, inconsistent lighting/shadows)
- I4: Mixed icon styles in one view (outline + filled + duotone)
- I5: Inconsistent aspect ratios/crops across a grid or gallery
- I6: Leftover placeholder images (lorem-picsum, unsplash-random) in production build

### General Quality (Q1-Q8)
- Q1: Cramped padding (text/controls within ~8px of bordered/colored edge)
- Q2: Body text touching viewport edge (especially on mobile)
- Q3: Justified text without effective hyphenation/language support
- Q4: Low contrast text (misses WCAG AA: 4.5:1 normal, 3:1 large text)
- Q5: Skipped heading level (rendered outline jumps h1 to h3 or similar)
- Q6: Tight line height (body text below 1.3, display headings role-based exceptions)
- Q7: Tiny body text (below 12px, 12-13px readability risk)
- Q8: Wide letter spacing on body (tracking above 0.05em)

### Accessibility (A1-A8) NEW
- A1: Missing/generic alt text (\"image\", \"photo1.png\")
- A2: Contrast failing WCAG AA (<4.5:1 normal text, <3:1 large text)
- A3: No visible focus state / outline removed with no replacement
- A4: Non-semantic markup (div-soup instead of button/nav/main/header)
- A5: Broken keyboard nav (unreachable interactive elements, no skip-to-content)
- A6: Form inputs with no associated label
- A7: Color-only status indication (no icon/text fallback)
- A8: Missing ARIA roles/live regions on dynamic content

### Design-Token / Drift Detection (D1-D6) NEW
- D1: Multiple border-radius values for the same component type across files
- D2: Hardcoded hex/px instead of referencing defined tokens
- D3: Spacing off the defined scale (random 13px/22px instead of 8/16/24)
- D4: Font-size/weight combos outside the type scale
- D5: Divergent shadow/elevation values for equivalent components
- D6: Near-duplicate hex values that should collapse into one token

### State Coverage (S1-S8) NEW
- S1: Empty state (zero items/no data) — must be intentional design, not bare blank container
- S2: Loading state — skeleton or spinner present; flag if missing entirely
- S3: Skeleton/loading layout mismatch — skeleton shape doesn't match real content's final layout (causes visible layout shift on load)
- S4: Error state — a failed fetch/action has a visible, human-readable error, not a silent failure or raw stack trace
- S5: Disabled state — actions requiring precondition are visibly disabled, not just non-functional
- S6: Partial-data state — some fields present, others null/undefined — doesn't break layout or show \"undefined\"/\"null\" as text
- S7: Permission-gated state — role-restricted UI shows appropriate message, not broken/empty view
- S8: Offline/network-loss state, where relevant

### Real-Content Stress Test (R1-R6) NEW
- R1: Long text overflow (long name, long email, long title) — check truncation/wrap behavior exists
- R2: List with 0 items, 1 item, and 100+ items — check for layout breaking or missing pagination/virtualization at scale
- R3: Mismatched string lengths in a set that's supposed to align (e.g. table columns, card titles)
- R4: Number edge cases — zero, negative, very large numbers, decimals where integers were assumed
- R5: Missing/broken image fallback (alt text and a placeholder graphic, not a broken-image icon)
- R6: Special characters / RTL text / emoji not breaking layout

### Responsive / Breakpoint Consistency (B1-B5) NEW
- B1: Same component's spacing/type-scale token usage checked at each breakpoint (mobile/tablet/desktop) — flag drift introduced only at certain sizes
- B2: Touch targets below 44x44px (iOS) / 48x48px (Android) on mobile breakpoints
- B3: Horizontal scroll appearing unintentionally at any breakpoint
- B4: Content/functionality that silently disappears on smaller breakpoints instead of adapting
- B5: Fixed pixel widths that don't scale, causing overflow or excess whitespace

### Interaction Feedback Audit (F1-F6) NEW
- F1: Async actions (save/submit/delete) with no loading indicator during the wait
- F2: Destructive actions (delete, remove, cancel subscription) with no confirmation step
- F3: Successful actions with no success feedback (toast, inline message, visual state change)
- F4: Double-submit not prevented (button stays clickable during a pending request)
- F5: Form validation errors that don't map to the specific field they belong to
- F6: Hover/focus/active states missing on any clickable element

### Dark Mode / Theme Parity (DM1-DM5) NEW
- DM1: Contrast ratio re-checked independently in dark mode (good light-mode ratio doesn't guarantee good dark-mode one)
- DM2: Icons/illustrations that are literally just inverted rather than purpose-built for dark backgrounds (halos, wrong shadows)
- DM3: Semantic colors (error red, success green) not re-tuned for dark backgrounds and failing contrast there
- DM4: Elevation/shadow system that relied on light-mode shadows now invisible or wrong on dark backgrounds
- DM5: Spacing/layout drift between light and dark versions of the same component

</pattern_catalog_summary>

<references>
- references/slop-patterns.md — 100+ AI slop phrase and design patterns with risk levels and corrections
- references/content-quality-guidelines.md — Quality standards for content evaluation
</references>

<related_skills>
- anti-ai-slop-real — Operational skill: detects and tracks slop in codebases via --scan, --list, --clear
- content-pipeline — AI UGC video production (may generate slop)
- capture — Note capture workflow
- gsd:progress — GSD progress checking and routing
</related_skills>

<how_to_use>
This skill is a **design reference only** — AI agents load it before generating UI. It documents 100+ anti-patterns and design principles to avoid.

### Loading the Skill
```bash
/skill anti-ai-slop-reference
```

### Reference Workflow for AI Agent:
1. Load the skill via `/skill anti-ai-slop-reference`
2. Read the pattern catalog from `references/slop-patterns.md`
3. Check each design decision against all 100+ patterns (V1-V17, T1-T15, C1-C6, L1-L9, M1-M8, P1-P9, I1-I6, Q1-Q8, A1-A8, D1-D6, S1-S8, R1-R6, B1-B5, F1-F6, DM1-DM5)
4. Apply replacement principles where patterns are detected
5. Ensure hierarchy uses a proper font system (single family with strong hierarchy through size/weight/width/spacing; second family earns place through clear role)
6. Verify colors carry defined jobs (brand, action, status, emphasis, surfaces); repeated decorative gradients/glows dilute those jobs
7. Check spacing communicates relationship (related items sit close; sections receive larger separation; repeated spacing tokens remain useful when semantic roles differ visibly)
8. If motion used, it communicates state, continuity, or causality (default surfaces stay still; one meaningful transition carries more value than many ornamental effects)
9. If decoration used, it carries meaning (domain artifacts, real product UI, data, photography, diagrams, and brand motifs provide specificity; generic icons and blobs disappear when carrying no information)
10. Asymmetry follows priority (give more space to more important content; avoid arbitrary card-size variation created solely to appear designed)
11. For each component, check state coverage (S1-S8): empty, loading, error, disabled, partial-data, permission-gated, offline states designed intentionally
12. For each component, run real-content stress test (R1-R6): long text, list scales, mismatched lengths, number edge cases, image fallbacks, RTL/special chars/emoji
13. For each component, check responsive consistency (B1-B5): spacing/type-scale across breakpoints, touch targets, unintended horizontal scroll, disappearing functionality, fixed pixel widths
14. For each interactive element, check interaction feedback audit (F1-F6): async actions with loading, destructive actions with confirmation, success feedback, double-submit prevention, form validation mapping, hover/focus/active states
15. If dark mode detected, check dark mode parity (DM1-DM5): contrast re-checked independently, icons purpose-built not just inverted, semantic colors re-tuned, elevation/shadow system working, spacing/layout drift resolved
12. Track exempted patterns if applicable (patterns that communicate real meaning or follow established brand)
13. Generate UI that consciously avoids all 100+ anti-patterns

### When NOT to Use This Skill
- Do NOT run `--scan` or `--fix` commands — this is a reference guide only
- Do NOT expect auto-fix suggestions — those belong in anti-ai-slop-real operational skill
- Do NOT use for runtime detection — use anti-ai-slop-real for that

### Integration with anti-ai-slop-real
- Load anti-ai-slop-reference first for design patterns
- Run `hermes --skill anti-ai-slop-real --scan` for operational detection and tracking
- Findings from operational skill can reference pattern IDs from this design guide
- Exemptions tracked in slop-log.json can reference patterns from both skills

## Pattern Reference Quick Lookup Table

| Category | Patterns | Key Avoidances |
|----------|----------|----------------|
| Visual | V1-V17 | Borders >=2px+radius >=12px, glassmorphism, generic icons, extreme radius, mixed icon styles, placeholder images in production |
| Typography | T1-T15 | Flat hierarchy, oversized headlines, all-caps body, single font, "it's not just X it's Y", buzzword stacking, em-dash overuse, fake urgency, rule-of-three headline |
| Color | C1-C6 | Purple/violet gradients, dark mode glowing accents, gradient text, gray on colored, cream reflex, WCAG AA contrast failures |
| Layout | L1-L9 | Identical card grids, monotonous spacing, nested cards, line length >80 chars, content overflow, positioned child clipped, non-semantic markup |
| Motion | M1-M8 | Bounce easing, layout-property animation, image hover transform, blanket scroll-fade-in, uniform 300ms ease, hover-scale on non-interactive, no prefers-reduced-motion, staggered-list-reveal on non-list |
| Copy | P1-P9 | Em-dash overuse, marketing buzzwords, aphoristic cadence, theater framing, "it's not just X it's Y", buzzword stacking, fake urgency, rule-of-three headline |
| Imagery | I1-I6 | Broken/placeholder images, stock-photo tells, AI-image artifacts, mixed icon styles, inconsistent aspect ratios, leftover placeholder images in production |
| Quality | Q1-Q8 | Cramped padding, viewport edge text, justified text, low contrast, skipped headings, tight line height, tiny body text, wide letter spacing |
| Accessibility | A1-A8 | Missing alt text, WCAG contrast failures, no focus state, div-soup markup, broken keyboard nav, unlabeled form inputs, color-only status, missing ARIA roles/live regions |
| Design-Token | D1-D6 | Multiple border-radius values, hardcoded hex/px, spacing off scale, font combos outside type scale, divergent shadow values, near-duplicate hex values |
| State Coverage | S1-S8 | Missing empty state, missing loading state, skeleton/layout mismatch, missing error state, non-disabled non-functional actions, missing permission-gated state, missing offline state |
| Real-Content Stress Test | R1-R6 | Long text overflow, list scale breakage, mismatched string lengths, number edge cases, broken image fallback, RTL/special chars/emoji breaking layout |
| Responsive Consistency | B1-B5 | Drift at certain breakpoints, touch targets <44/48px, unintended horizontal scroll, disappearing functionality, fixed pixel widths causing overflow/whitespace |
| Interaction Feedback | F1-F6 | Async actions without loading, destructive actions without confirmation, success feedback missing, double-submit not prevented, form validation not mapped to field, missing hover/focus/active states |
| Dark Mode / Theme Parity | DM1-DM5 | Contrast not re-checked in dark mode, inverted-only icons, semantic colors not re-tuned, elevation/shadow system wrong on dark, spacing/layout drift between light/dark |

## For AI Agent Integration

This skill is designed to be loaded as a **knowledge base** - the AI agent reads the pattern catalog and design principles, then applies them when generating UI. It does NOT need to run `--scan` or `--fix` commands.

The agent should:
1. Load the skill via `/skill anti-ai-slop-reference`
2. Read the pattern catalog from `references/slop-patterns.md`
3. Reference the replacement principles when making design decisions
4. Track exempted patterns if applicable
5. Generate UI that consciously avoids all 100+ anti-patterns

This is a reference guide only - no scan tracking, no slop-log.json, no remediation actions. Pure design guidance for AI-assisted UI generation.

## Integration Notes

This skill was updated from v2.0.0 to v3.1.0 to match the anti-ai-slop-real operational skill upgrade. New categories added:
- Accessibility A1-A8 (8 patterns)
- Design-Token D1-D6 (6 patterns)
- State Coverage S1-S8 (8 patterns)
- Real-Content Stress Test R1-R6 (6 patterns)
- Responsive Consistency B1-B5 (5 patterns)
- Interaction Feedback Audit F1-F6 (6 patterns)
- Dark Mode/Theme Parity DM1-DM5 (5 patterns)

The evidence model (Source/Render/Judgment/Confidence), severity tags (blocker/major/nit), and auto_fix boolean are consistent with anti-ai-slop-real v3.0.0+ and slop-log.json schema.