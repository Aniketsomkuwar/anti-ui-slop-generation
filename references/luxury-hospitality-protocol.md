# Luxury Hospitality Design Contract — H1-H12

Pre-generation design contract for ultra-luxury hospitality, Michelin-grade restaurants,
and architectural destination venues. Read this **before** generating UI in that domain.

The operational skill (`anti-ai-slop-real`) detects these as H1-H12 after the fact. This
document exists so the patterns never get written in the first place.

**Scope gate:** applies to luxury hospitality, fine dining, and destination venues only.
Do not apply to SaaS, dashboards, dev tools, or aggregators.

## The Domain Thesis

A destination venue's value is sensory specificity. Generic UI grammar does not merely
look plain here — it actively miscategorises the venue as a booking aggregator. Every
rule below follows from one question:

> Does this element say *"this place exists"* or *"this place is listed"*?

Anything that reads as a listing is the defect. Structure must follow the venue's own
logic: the room, the service, the seasonal menu, the arrival.

---

## 1. Forbidden Patterns

Never generate these. IDs match the detection catalog.

### H1 — Card-grid aggregation
Never rows of identical rounded cards with a cropped image header and a plain text body.
**Instead:** full-bleed canvas, asymmetric split viewport, or an editorial index/ledger.
Signature dishes deserve full-bleed presence; the full menu belongs in a typographic index.

### H2 — Generic status pills
Never a status pill with a pulsing green/red dot ("Open Today • Live", "Active Now").
**Instead:** a typographic ledger line — `Open · 18:00–23:00` — or a jewel dot that carries
meaning. Reserve live indicators for live inventory the user is about to act on.

### H3 — Fake chrome around media
Never mock window headers, tab strips with close buttons, or "LIVE MAP" status bars around
embedded media.
**Instead:** media is an architectural plane. Full-bleed, no simulated OS or browser UI.

### H4 — Raw embedded maps
Never an unstyled Google Map — pastel roads, yellow highways — inside a dark interface.
**Instead:** custom monochromatic CSS filters plus a dark overlay, or purpose-built vector
or static cartography drawn to the palette.

### H5 — Circular icon lists
Never an icon-in-a-circle stacked beside label rows for address, phone, or hours.
**Instead:** structured tabular ledgers, architectural key-value rows, or editorial copy.

### H6 — Fintech sans pairing
Never geometric startup sans (Outfit, Poppins, Inter, DM Sans, Montserrat) against a
classical luxury serif.
**Instead:** humanist, Roman, or sharp editorial — Plus Jakarta Sans, Tenor Sans, Syne,
Manrope. The sans must defer to the serif, not compete with it.

### H7 — Hover-gated core content
Never hide core sensory information — dish photos, ingredients, pricing — entirely inside
hover reveals unless explicitly instructed.
**Instead:** confident, static presence. Hover may *add*; it must never *gate*.

---

## 2. Mandatory Design Codes

Absence of these is itself the defect.

### H8 — The canvas over the card
Full-bleed backgrounds, architectural hairline borders (`1px solid rgba(gold, 0.2)`), and
asymmetrical split viewports — rather than boxed containers. Let the surface run to the edge.

### H9 — Editorial typographic scale
Numbers, coordinates, and labels are design elements, not incidental text. Roman or serif
numerals ("01", "02"), wide letter-spacing (`0.2em`), small caps.

### H10 — Discreet dietary and status indicators
Replace heavy "VEG / NON-VEG" badges with minimalist jewel dots — 4-6px glowing accents
framed in glass discs. The information survives; the shouting does not.

### H11 — Cinematic media integration
Background video always carries calibrated gradient scrims — linear **and** vignette —
that bleed seamlessly into the dark palette without harsh edges. A scrim that fights the
palette is worse than none.

### H12 — Tabular concierge hierarchy
Present arrival, contact, and venue data like a five-star concierge dossier: category key
on the left, refined Cormorant Garamond serif values on the right.

---

## 3. Pre-Emit Checklist

Run before handing back any luxury hospitality UI:

- [ ] No 3+ sibling rounded cards with image headers and plain text bodies (H1)
- [ ] No animated or pulsing status dot (H2)
- [ ] No simulated window/tab chrome around media (H3)
- [ ] Every map is filtered or redrawn to the palette (H4)
- [ ] No icon-in-circle contact rows (H5)
- [ ] No geometric startup sans paired with the display serif (H6)
- [ ] No `<img>`, price, or ingredient list gated behind hover (H7)
- [ ] Full-bleed sections and hairline borders present, not boxed containers (H8)
- [ ] Numerals, coordinates, and labels set editorially (H9)
- [ ] Dietary indicators are jewel dots, not badges (H10)
- [ ] Every background video has linear + vignette scrim with no hard edge (H11)
- [ ] Contact/arrival data is a key-value dossier (H12)

---

## 4. Exemption Rules

These are legitimate and must not be "fixed":

- **H1** — the grid *is* the product (a real listing or taxonomy the venue operates)
- **H2** — the status is live inventory the user is about to act on
- **H4** — the map is the primary interaction *and* is restyled to the palette
- **H7** — the user explicitly asked for hover-gated content on a named component
- **H9** — a house style guide mandates a different numeral treatment (cite the guide)
- **H10** — regulatory or allergy-safety labelling mandates explicit dietary text.
  **Safety labelling is never slop.**

---

## 5. Relationship to the Base Catalog

In this domain these H-IDs supersede their base-catalog equivalents. Report one, not both.

| H-ID | Supersedes | Note |
|------|-----------|------|
| H1 | L2, V6, I5 | H1 when the cards carry image headers |
| H2 | V12, M4, M6 | H2 when the badge reports venue status; the pulse is the tell |
| H4 | C1, C4 | H4 is the cause; C1/C4 fire only on residual contrast after filtering |
| H5 | A4, L9 | H5 when the icon list encodes contact or venue data |
| H6 | T8, V14 | H6 names the *pairing* failure, which T8 does not |
| H10 | V12 | H10 when the badge is dietary |
| H8 | L4, V6 | H8 for "unbox", L4 for "un-nest" |
| H9 | T5, L5 (inverse) | T5/L5 flag decorative overuse; H9 flags editorial treatment that is absent |

H3, H7, and H11 have no base-catalog equivalent — they are new.

---

## 6. Application Order

When generating, resolve in this order — later choices depend on earlier ones:

1. **Canvas** (H8) — full-bleed planes and split viewports before any component exists
2. **Media** (H3, H4, H11) — how imagery, video, and maps sit in the canvas
3. **Structure** (H1, H5, H12) — index vs grid, ledger vs icon list, dossier vs prose
4. **Type** (H6, H9) — serif/sans pairing, then numeral and label treatment
5. **Indicators** (H2, H10) — status and dietary marks last, sized to the system
6. **Content presence** (H7) — confirm nothing sensory ended up behind a hover

Generating in reverse — indicators before canvas — is what produces a luxury site that
looks like a SaaS dashboard wearing a serif font.
