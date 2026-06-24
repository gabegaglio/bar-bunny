# Bar Bunny — Design System

Working tokens and component rules. The direction is **Swiss Mono** — a mix of Swiss
International + Minimalist Monochrome. Reasoning and merge decisions live in
[`styles/swiss-mono-hybrid.md`](styles/swiss-mono-hybrid.md); the precedent is in
[`../CLAUDE.md`](../CLAUDE.md). References: [`inspiration/`](inspiration/).

> **Pivot:** this replaces the earlier dark/glassmorphic nightlife system.
> **No glassmorphism. No gradients. No rounded corners. No shadows.** Depth comes from
> contrast, border weight, pattern, and inversion only.

---

## Foundations

### Color
**Pure monochrome — black and white are the entire palette. No accent color.** There is
no Swiss Red and no gold. Everything a color would normally signal (selection, live
state, primary CTAs, focus) is expressed through **inversion, border weight,
fill-vs-outline, and scale**.

| Token             | Role                                            | Value      |
| ----------------- | ----------------------------------------------- | ---------- |
| `bg`              | Default (editorial) background                  | `#FFFFFF`  |
| `fg`              | Default text / borders                          | `#000000`  |
| `bg-invert`       | Map / "night" surface background                | `#000000`  |
| `fg-invert`       | Text on inverted surfaces                       | `#FFFFFF`  |
| `muted`           | Secondary background (rhythm)                   | `#F2F2F2`  |
| `muted-2`         | Alt secondary background                        | `#F5F5F5`  |
| `secondary-fg`    | Secondary / metadata text                       | `#525252`  |
| `border`          | Structural borders                              | `#000000`  |
| `border-light`    | Subtle dividers                                 | `#E5E5E5`  |

Light vs. dark is **semantic, not a theme toggle**: editorial surfaces (onboarding,
route summary, profile, lists) are light; the map and night surfaces are inverted.

### Typography — three voices, clearly zoned
- **Inter** — structural/objective voice: labels, UI, headings, data. Weights 400 / 500
  / 700 / 900. UPPERCASE for labels & most headings.
- **Playfair Display** — editorial voice: large statements & pull-quotes only.
  400 + italic (italic emphasis words may sit inside an Inter or Playfair headline).
- **JetBrains Mono** — data voice: coordinates, distances, ETAs, open-until times, route
  stop numbers, section numbers.

| Style        | Font / size / weight              | Use                                  |
| ------------ | --------------------------------- | ------------------------------------ |
| Display      | Inter or Playfair, `text-7xl`–`9xl` / 900 or 400 | Hero statements (let words be images) |
| Section head | Inter `text-4xl`–`5xl` / 700–900, UPPERCASE | Section titles                |
| Title        | Inter `text-xl`–`2xl` / 700       | Card titles, venue names             |
| Body         | Inter `text-base`–`lg` / 400–500, `leading-relaxed` | Reading text         |
| Label        | Inter `text-xs` / 500, UPPERCASE, `tracking-widest` | Overlines, controls   |
| Data         | JetBrains Mono `text-xs`–`sm`     | Distance, ETA, coords, stop numbers  |

Tracking: `tracking-tighter` on large headlines, `tracking-widest` on small labels,
default on body.

### Spacing & radius
- 4px grid: 4 / 8 / 12 / 16 / 24 / 32. Generous negative space (`py-24`→`py-32`,
  cards `p-8`→`p-12`).
- **Radius: `0px` everywhere.** No exceptions.

### Borders & lines (depth, not shadow)
Full weight scale: `1px` hairline (`border-light` dividers) → `2px`/`4px` structural
(black) → `4px`/`8px` section rules. Grid is visible. **No shadows anywhere.**

### Texture / pattern
Subtle CSS patterns add depth: grid 24px (3%), dots 16px (4%), diagonal 45° (2%), global
noise (1.5–2%). On inverted map/night surfaces use white-line / radial textures (~3–5%).

---

## Components

### Buttons
Rectangular, uppercase, `tracking-widest`, height `h-12`+ (44px min touch target).
- **Primary** — black bg / white text → inverts (white/black) on hover. *Critical* CTAs
  gain emphasis from a thick (4px) black frame, not color.
- **Secondary** — white + 2px black border → fills black on hover.
- **Ghost** — text + underline on hover.
- Motion ≤150ms, no scale. Optional `→` glyph on CTAs.

### Cards / containers
1–2px black border, white or `#F2F2F2` bg, `p-8`/`p-12`, 0 radius / 0 shadow. **Full
color inversion on hover** (white→black); the selected/active card stays inverted.
Numbered with a mono label (`01`, `02`).

### Inputs
2px black box border or `border-b-2` underline. **Focus thickens the border to 4px black**
plus a 3px black `focus-visible` outline. Italic `#525252` placeholder. No glow.

### Map markers (nodes)
| State    | Style                                                            |
| -------- | ---------------------------------------------------------------- |
| Default  | Small black square (white outline on the inverted map)           |
| Selected | Enlarged, **inverted**, with a thin ring — brightest/heaviest    |
| Saved    | Distinct monochrome glyph (filled)                               |
| Visited  | Distinct monochrome glyph (outlined / dimmed)                    |

Route line: the thickest black stroke (white on the inverted map). The map uses a custom
monochrome Google Maps style (black land, white roads/labels).

### Bottom carousel card (NOT glass)
Bordered white card over the inverted map. Venue name (Title) · rating · distance
(mono) · open/closed (bold black vs. `secondary-fg`) · **Add to route**. Swipeable;
selecting pans the map and inverts the node.

### Icons
`lucide-react`, thin stroke (1–1.5px), monochrome, sized 20–24px, often enclosed in a
black square/circle. Never colored emoji.

---

## Motion
Instant-to-snappy, **100–200ms**, `ease-out` / `ease-linear`. Color inversions, 90° plus
rotation, scale 1.0→1.05, -1px lift, grayscale→color (~250ms) on imagery. No spring,
elastic, parallax, or cinematic slowness. CSS-based; respect `prefers-reduced-motion`.

---

## Imagery
Venue/editorial **photographs** default to **grayscale**, large, prominent, rectangular
(0 radius), framed by a 1px black border instead of a shadow. Photos may reveal their
full color on hover (~250ms, optional, with a subtle `scale-105`) — this is the *only*
place real-world color ever appears, and it applies to photographic content only. The UI
chrome itself remains strictly black & white; never tint UI or use color to signal state.

---

## DON'T (enforceable in review)
- No gradients
- No glassmorphism / blur surfaces
- No rounded corners (0px radius everywhere)
- No drop shadows (depth = contrast / border / pattern / inversion)
- No color at all beyond black and white (no Swiss Red, no gold, no accent)
- No state conveyed by color alone — use weight, fill-vs-outline, icon, or label
- No colored emoji
- No slow/cinematic or springy motion (keep it 100–200ms)
- No centered-everything layouts — use the asymmetric Swiss grid
- No decorative fonts beyond Inter / Playfair Display / JetBrains Mono
