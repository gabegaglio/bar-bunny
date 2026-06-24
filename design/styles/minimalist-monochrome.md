# Design Style: Minimalist Monochrome

> Standalone style reference. One of the two parents of the app's chosen direction —
> see [`swiss-mono-hybrid.md`](swiss-mono-hybrid.md).

## Design Philosophy

**Reduction to Essence.** Minimalist Monochrome strips design to its most fundamental
elements: black, white, and typography. No accent colors to hide behind, no gradients to
soften edges, no shadows for false depth. Every decision stands on its own merit. Design
as discipline — restraint as the ultimate form of expression.

**Emotional keywords:** Austere, authoritative, timeless, editorial, intellectual,
dramatic, refined, stark, confident, uncompromising.

The visual language of high-end fashion editorials, architectural monographs, museum
catalogs, luxury identities (Chanel, Celine, Bottega Veneta), and award-winning book
design. It commands respect through confidence — using scale, contrast, rhythm, and
negative space rather than color.

**This design is NOT:** colorful/playful; soft/rounded/friendly; gradient/accent-based;
shadow-heavy; generic; busy; "Minimalist Modern with colors removed."

### The DNA
1. **Pure black & white** — true `#000000`/`#FFFFFF`; gray only for secondary text/borders
2. **Serif typography as hero** — classical serif for sophistication and editorial weight
3. **Oversized type scale** — 8xl/9xl+; words become graphic elements
4. **Line-based visual system** — hairlines, rules, borders, underlines instead of fills
5. **Sharp geometric precision** — 0 radius, perfect 90° corners, architectural alignment
6. **Dramatic negative space** — generous margins make black elements impactful
7. **Inversion for emphasis** — black bg/white text instead of accent colors

### Differentiation from Minimalist Modern
Pure B&W (not blue + gradients); serif (not Inter sans); sharp 0px (not rounded); flat
(not shadowed); lines/borders/type (not gradient fills); editorial-luxury vibe (not
contemporary tech); austere & commanding (not approachable).

## Design Tokens

### Colors (strictly monochrome)
```
background       #FFFFFF   foreground       #000000
muted            #F5F5F5   mutedForeground  #525252
accent           #000000   accentForeground #FFFFFF
border           #000000   borderLight      #E5E5E5
card             #FFFFFF   cardForeground   #000000   ring  #000000
```
**Rule:** no other colors, ever. The palette is absolute.

### Typography
- **Display/headlines:** "Playfair Display", Georgia, serif (high-contrast, italics)
- **Body:** "Source Serif 4", Georgia, serif (readable long-form)
- **Mono/labels:** "JetBrains Mono" (dates, metadata, technical details)
- **Scale (dramatic):** `xs 12` · `sm 14` · `base 16` · `lg 18` · `xl 20` · `2xl 24` ·
  `3xl 32` · `4xl 40` · `5xl 56` · `6xl 72` · `7xl 96` · `8xl 128` · `9xl 160`
- **Tracking/leading:** headlines `tracking-tight`/`tighter`; body `normal`; labels
  `tracking-widest`; `leading-none` (display), `leading-relaxed` 1.625 (body)

### Border radius
**All values: 0px.** No exceptions — defines the architectural character.

### Borders & lines
```
hairline 1px #E5E5E5 · thin 1px #000 · medium 2px #000 · thick 4px #000 · ultra 8px #000
```
Section rules (thick/ultra), column dividers (thin), card borders (thin/medium),
link underlines (thin, on hover).

### Shadows
**None.** Depth from color inversion, border weight, scale contrast, negative space.

### Textures & patterns (REQUIRED — prevent flat design)
- **Horizontal lines (global):** `repeating-linear-gradient(0deg…)`, `100% 4px`, 1.5%
- **Grid (editorial sections):** crossed 1px lines, `40px 40px`, 1.5%
- **Diagonal (process/timeline):** 45° lines, ~42px, 1%
- **Noise (global, paper):** SVG fractal noise, 2%
- **Inverted (dark sections):** white vertical lines (Stats) ~3%; radial white gradient
  (Final CTA) ~5%

## Components
- **Buttons** — Primary: black bg/white text, `px-8 py-4`, uppercase `tracking-widest`
  `font-medium text-sm`, hover inverts to white/black + border, instant (0–100ms).
  Secondary: transparent + 2px black border, fills black on hover. Ghost: text-link,
  underline on hover. Always rectangular; consider `→` for CTAs.
- **Cards** — Standard: white, 1px black border, `p-6`/`p-8`, no shadow/radius. Inverted:
  black bg/white text, no border, use sparingly. Borderless: whitespace-separated, rules
  above/below if needed.
- **Inputs** — white bg, 2px black border (bottom or full), no radius, `#525252` italic
  placeholder, focus thickens border to 3–4px (no colored ring). Textarea: visible resize.

## Layout
Container `max-w-6xl`, `px-6 md:px-8 lg:px-12`. Section padding `py-24 md:py-32 lg:py-40`,
separated by thick (4–8px) black rules. CSS Grid, 12-column base, strong vertical rhythm.

## Effects & Animation — **minimal and instant**
0–100ms transitions, binary on/off, purposeful (hover/focus only). Cards/features: full
color inversion (100ms). Buttons: inversion, `transition-none`. Blog images: border 2→4px,
scale 105% + grayscale→color (300ms). Links: instant underline. Testimonials: quote-mark
opacity up, bottom border thickens. **No** bouncy/floating/parallax/slow-easing/gradient
animation.

## Iconography
Outlined thin strokes (`strokeWidth: 1`–`1.5`), 20–24px, always black; standalone or in
black-stroke/white-fill circles. `<Icon size={20} strokeWidth={1.5} className="text-black" />`

## Responsive
Maintain sharp corners + B/W palette. Hero `9xl`→`5xl` on mobile; stack columns; borders
become full-width rules; keep generous vertical spacing. The monochrome drama must survive
mobile — no generic patterns.

## Accessibility
Pure black/white = 21:1 (AAA). Focus REQUIRED: buttons 3px outline + 3px offset
(`focus-visible`); inputs thicken bottom border 2→4px; links border appears/thickens;
secondary elements 3px outline + 2px offset. Visible black skip link. 44×44px touch
targets.

## Bold Choices (non-negotiable)
Oversized hero word (8xl+/9xl desktop); hero rule + small bordered square; inverted stats
(black bg/white text + vertical-line texture); no accent colors (black IS the accent);
4px black rules between all sections; editorial pull-quote testimonials with oversized
quotation marks; sharp everything (0 radius); instant interactions (≤100ms); typography
as graphics; layered textures (not flat); boxed drop cap; elevated pricing tier; hover
inversions; image borders thicken on hover with scale.

## Success Looks Like
Opening a high-end fashion magazine / walking a modern art gallery / an award-winning
architectural monograph. NOT a generic template, a tech landing page, something that
"needs a pop of color," or Minimalist Modern with colors removed.
