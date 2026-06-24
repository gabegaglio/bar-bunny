# Design Style: Swiss Mono (Bar Bunny's chosen direction)

> The app's design language. A deliberate synthesis of **Swiss International**
> ([`swiss-international.md`](swiss-international.md)) and **Minimalist Monochrome**
> ([`minimalist-monochrome.md`](minimalist-monochrome.md)). The app's working tokens
> live in [`../design-system.md`](../design-system.md); this file is the *why* and the
> reasoning behind every merge decision.

## The thesis

Swiss gives us **objective structure** — the grid as law, grotesque type, functional
signaling, mechanical motion. Monochrome gives us **editorial drama** — true black/white,
oversized serif statements, line-based depth, inversion for emphasis.

Bar Bunny's identity = **a transit map for nightlife.** Stark, confident, instantly
legible, architectural. The map screen reads like a Swiss transit diagram; the editorial
surfaces (onboarding, route summaries, profile) read like a black-and-white art-book
spread. No glassmorphism, no gradients, no soft corners — depth comes from contrast,
pattern, and border weight only.

**Pure monochrome.** Black and white are the *entire* palette — no accent color, not
even Swiss Red. Monochrome's discipline ("black IS the accent") fully governs. Everything
a color would normally do — selection, live state, primary CTAs, focus — is done with
**inversion, border weight, fill-vs-outline, and scale** instead.

## How the two parents are reconciled

Where the parents disagree, here is the ruling and the reasoning.

| Dimension | Swiss | Monochrome | **Swiss Mono ruling** |
| --------- | ----- | ---------- | --------------------- |
| Palette | White / black / **red** | True black/white only | **Monochrome wins outright — pure black & white, no accent (no Swiss Red).** Swiss's functional-red role is reassigned to *inversion, border weight, fill-vs-outline, and scale*. This keeps maximum austerity; a nightlife app gets its "energy" from stark high-contrast inversion instead of a signal color. |
| Headline type | Inter Black, uppercase | Playfair Display serif | **Dual voice.** Inter is the structural/objective voice (labels, UI, data, most headings — Swiss). Playfair Display is reserved for large *editorial statements* and pull-quotes (Monochrome drama). Two voices, clearly zoned — never mixed in one line except deliberate italic emphasis words. |
| Metadata type | — | JetBrains Mono | **Kept.** Mono is perfect for a map app: coordinates, distances, ETAs, open-until times, route stop numbers. It signals "data." |
| Borders | Thick 2–4px | Hairline → 8px scale | **Full weight scale** (`1px` hairline dividers → `2/4px` structural → `8px` section rules). Black, visible. |
| Motion | Snappy 150–200ms | Instant 0–100ms | **Snappy-to-instant: 100–200ms, `ease-out`/`linear`.** No cinematic/luxury slowness. Inversions, 90° icon rotation, scale 1.05, -1px lift. |
| Imagery | (type-led, sparse) | Grayscale → color on hover (300ms) | **Grayscale default, reveal to full color on hover at ~250ms.** Fast, not cinematic. Venue photos earn color on interaction. |
| Depth | Pattern texture | Inversion + border weight | **Both.** Patterns (grid/dots/diagonal/noise) + inversion + border weight. Zero shadows. |
| Dark mode | White-first | White-first, inverts for emphasis | **Inversion is the bridge.** See below. |

## Resolving the nightlife dark-mode tension

The previous Bar Bunny spec was dark-mode-first + glassmorphic. Both parents are
**white-first and anti-glass**, so glassmorphism is dropped entirely. But a nightlife map
app benefits from dark surfaces — so we use the move **both** parents already endorse:
**inversion.**

- **Default / editorial surfaces** (onboarding, route summary, profile, lists) →
  light: white bg, black type, emphasis via inversion/weight.
- **The map and "night" surfaces** → inverted: black bg, white type, white-line texture.
  The map uses a custom monochrome Google Maps style (black land, white roads/labels),
  markers as small black/white squares. The selected node and route line read as the
  **brightest white with the heaviest weight** (the route line is the thickest white
  stroke; the selected node inverts and gains a white ring).

This makes light/dark a *semantic* choice (editorial vs. map), not a theme toggle — fully
consistent with both parents' "inversion for emphasis."

## Tokens (summary — full table in `../design-system.md`)

```
--bg            #FFFFFF    --fg            #000000
--bg-invert     #000000    --fg-invert     #FFFFFF
--muted         #F2F2F2    --muted-2       #F5F5F5
--secondary-fg  #525252    --border-light  #E5E5E5
--border        #000000    (no accent / signal color — pure B&W)
radius          0px        shadows         none
```

Type: **Inter** (400/500/700/900) structural · **Playfair Display** (400 + italic)
editorial statements · **JetBrains Mono** (400/500) metadata.

## Components

- **Buttons** — rectangular `rounded-none`, uppercase, `tracking-widest`. Primary: black
  bg / white text → inverts to white/black on hover. *Critical* CTAs get extra weight via
  a thick (4px) black frame, not color. Secondary: white + 2px black border → fills black.
  Ghost: underline on hover. ≤150ms, no scale. CTAs may carry a `→`.
- **Cards** — defined by 1–2px black borders, white or `#F2F2F2` bg, generous `p-8`/`p-12`,
  zero radius/shadow. Full color inversion on hover (white→black); the selected/active
  item stays inverted. Numbered with mono labels (`01`, `02`).
- **Inputs** — box with 2px black border OR underline (`border-b-2`); focus **thickens the
  border to 4px black** (Monochrome's approach) plus a 3px black `focus-visible` outline.
  Italic `#525252` placeholder. No glow rings.
- **Map markers (nodes)** — default: small black square (white outline on the inverted
  map); selected: enlarges, **inverts**, and gains a thin ring (the brightest, heaviest
  marker); saved: filled glyph; visited: outlined/dimmed glyph. Route line: the thickest
  black stroke (white on the inverted map).
- **Section labels** — Swiss numbered prefixes in black (`#525252` for the number, black
  for the word): `01. MAP` `02. ROUTES` `03. DISCOVER` `04. PROFILE`, uppercase,
  `tracking-widest`.

## Layout

Grid is law and **visible**: 4px black section rules, hairline column dividers, asymmetric
ratios (8:4 / 7:5 / 5:7), optional fixed vertical gridlines at 12-col boundaries. Strict
left alignment, ragged right. Generous negative space (`py-24`→`py-32`, `p-8`→`p-12`).
Massive responsive type (`text-6xl` mobile → `text-9xl`/`text-[10rem]` desktop) — let
words be images.

## Patterns / texture (depth without shadow)

Grid 24px (3%), dots 16px (4%), diagonal 45° (2%), global noise (1.5–2%). On dark/map
surfaces use **inverted** white-line / radial textures (~3–5%).

## Motion

Instant-to-snappy, **100–200ms**, `ease-out` or `ease-linear`. Color inversions, 90° plus
rotation, scale 1.0→1.05, -1px lift, grayscale→color (~250ms) on imagery. No spring,
elastic, parallax, or luxury slowness. All CSS-based; respect `prefers-reduced-motion`.

## Accessibility

Black/white = 21:1 (AAA) — the palette is accessible by construction. Focus: 3px black
outline (`focus-visible`) with offset, or border thicken to 4px on inputs. State is never
conveyed by color alone (there is none) — use weight, fill-vs-outline, icon, and label.
44×44px touch targets. Semantic HTML, proper heading order, ARIA on icon-only controls.

## Do / Don't

**Do:** pure black & white · emphasis via inversion, border weight, fill-vs-outline, and
scale · Inter for structure + Playfair for statements + JetBrains Mono for data · 0px
radius · visible grid + thick rules · inversion for the map and emphasis · grayscale
imagery revealing color on hover · snappy 100–200ms motion.

**Don't:** any accent color (no Swiss Red, no gold) · gradients · glassmorphism · rounded
corners · drop shadows · state conveyed by color alone · slow/cinematic or springy motion
· centered-everything layouts · soft "friendly" UI.
