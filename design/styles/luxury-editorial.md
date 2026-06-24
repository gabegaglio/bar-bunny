# Design Style: Luxury / Editorial

> Standalone style reference. Kept for inspiration; **not** the app's chosen direction
> (the app uses the Swiss × Monochrome hybrid). Its serif headlines, gold accent,
> grayscale-on-hover imagery, and cinematic motion are a useful palette to borrow from.

## Design Philosophy

**Core Principles:** Elegance through restraint, precision, and depth. Emulates high-end
fashion magazines (Vogue, Harper's Bazaar, Kinfolk) and luxury brands (Chanel, Hermès,
Aesop). Success depends on exquisite typographic hierarchy, generous negative space,
slow cinematic motion, intentional asymmetry, and layered depth through subtle shadows.

**Vibe:** Sophisticated, timeless, expensive, serene, curated, deliberate, editorial,
tactile.

**The Secret:** Luxury isn't decoration — it's removing everything unnecessary and
perfecting what remains. Slow all motion to cinematic speeds (1500–2000ms for images).
Add more space than feels comfortable. Use asymmetry. Layer depth through subtle shadows
(never harsh) and inner borders. It should feel like expensive paper you want to touch.

## Design Tokens

### Colors (sophisticated monochrome)
- **Background** `#F9F8F6` (Warm Alabaster) — off-white; warm undertone is critical
- **Foreground** `#1A1A1A` (Rich Charcoal) — not pure black; primary text and borders
- **Muted bg** `#EBE5DE` (Pale Taupe) — subtle elevation/alternate backgrounds
- **Muted fg** `#6C6863` (Warm Grey) — secondary text, captions, metadata
- **Accent** `#D4AF37` (Metallic Gold) — sparingly: hover, underlines, focus, small
  decorative elements. Never for large areas.
- **Accent fg** `#FFFFFF` — only on dark/gold elements

Layering: borders/dividers use `#1A1A1A` at 10–20% opacity. Dark sections invert:
`#1A1A1A` bg, `#F9F8F6` text, muted text at 60–80% opacity. Never pure black/white text.

### Typography (the most critical element)
- **Headings:** "Playfair Display" — high-contrast editorial serif
- **Body:** "Inter" — humanist sans-serif
- **Scale:** hero `text-6xl`–`text-9xl`+ (`leading-[0.9]`); sections `text-5xl`–`7xl`;
  subsections `text-3xl`–`4xl`; body `text-base`–`lg` (`leading-relaxed`); labels
  `text-xs` uppercase; micro `text-[10px]`
- **Weights:** Playfair Regular (400), Light (300) for contrast, Italic for emphasis;
  Inter Medium (500) for buttons/links, Regular (400) body, Light (300) sparingly
- **Tracking:** uppercase labels `tracking-[0.25em]`–`[0.3em]`; buttons `[0.2em]`;
  headlines `tracking-tight`/default; body default (never adjust)
- **Leading:** headlines `leading-[0.9]`–tight; body `leading-relaxed` (1.625)

### Radius & Borders (architectural precision)
- **Radius:** `0px` everywhere — strictly rectangular
- **Borders:** always `1px`; `#1A1A1A` full opacity for strong, 10–20% for subtle;
  single borders (often `border-t` only); dividers as `h-px`/`w-px` lines

### Shadows & Effects (subtle layered depth)
- Extremely soft, low-opacity shadows — never harsh. Examples: hero
  `shadow-[0_8px_32px_rgba(0,0,0,0.12)]`; features `shadow-[0_4px_24px_rgba(0,0,0,0.08)]`;
  cards `shadow-[0_2px_8px_rgba(0,0,0,0.02)]` → `[0_8px_24px_rgba(0,0,0,0.06)]` on hover;
  primary buttons `shadow-[0_4px_16px_rgba(0,0,0,0.15)]` → `[0_8px_24px_rgba(0,0,0,0.25)]`;
  inner borders `shadow-[inset_0_0_0_1px_rgba(0,0,0,0.04-0.08)]`
- **Paper noise:** SVG fractal noise overlay at 2% opacity, fixed, pointer-events none,
  z-50 — "expensive paper" feel
- **Imagery:** default `grayscale` → `grayscale-0` on hover; transition
  `duration-[1500ms]`–`[2000ms]`; subtle `group-hover:scale-105`; shadows deepen on
  hover; coordinate via `group`

### Grid & vertical lines
- 4 fixed full-height vertical gridlines (`w-px`, `bg-[#1A1A1A]/20`, pointer-events
  none) at column boundaries — editorial grid structure
- 12-column grid, max width `1600px`, `px-8` mobile / `px-16` desktop, asymmetric offset
  starts (`col-start-2`, `col-start-6`)

## Component Principles
- **Buttons** — rectangular, `h-12`/`h-14`/`h-10`, generous `px-8`–`px-10`, uppercase
  `text-xs` `tracking-[0.2em]`. Primary: dark bg, white text, gold layer slides in from
  left (`translate-x-[-100%]`→`0`, `duration-500`, custom cubic-bezier), text above via
  z-index. Secondary: transparent + thin border, fills dark on hover. Link: underline on
  hover, optional gold.
- **Cards** — transparent bg, single `border-t`, `border-[#1A1A1A]` 1px, generous
  `p-8`/`p-12`, barely-visible hover bg shift; featured use `border-t-4` gold; image
  cards grayscale + slow reveal, `aspect-[3/4]`/`[4/5]`, `group`.
- **Inputs** — bottom border only, transparent bg, gold on focus, `h-12`, `px-0 py-2`;
  Inter `text-sm` input text; Playfair italic warm-grey placeholder; no rings.

## Interactive States (slow & deliberate)
Hover `duration-500`–`700` (images 1500–2000ms); `ease-out` or
`cubic-bezier(0.25,0.46,0.45,0.94)`; gold accent appears subtly; subtle scale/translate;
shadows deepen. Focus: `ring-1` or gold border change, minimal. Disabled: `opacity-50`,
no pointer events. Micro: FAQ icon rotates 90° + gold border + fade-in translateY;
testimonial stars scale; blog shadows deepen; nav links gold.

## Layout (breaking symmetry)
Avoid 50/50 — use 7/5, 4/4/4, offset starts. Bottom-left alignment. Section padding
`py-24`–`py-32`; component `p-8`–`p-12`; gaps `12`/`16`. Alternate light
(`#F9F8F6`)/dark (`#1A1A1A`) sections; `border-t` separators; dark sections invert with
muted text at 60–80%. Max container `1600px`; reading columns `max-w-md`–`xl`.

## The Bold Factor (signatures)
Vertical text labels (`writing-mode: vertical-rl`); drop caps (Playfair, float-left,
7xl, `leading-[0.8]`, `mr-3`); mixed italic headlines with gold italic words; grayscale
image transitions (1500–2000ms + scale + shadow); visible gridlines (4 @ 20%); gold
sliding button animation; decorative horizontal lines (`h-px w-8 md:w-12`); extreme type
scale (`text-5xl`→`text-9xl` vs `text-[10px]` labels); layered subtle shadows;
multi-layered testimonial interactions.

## Anti-Patterns
No rounded corners; no harsh shadows; no pure black/white text (use charcoal/alabaster);
no fast animations (≥500ms, images 1500–2000ms); no vibrant colors (mono + gold only);
don't center everything; don't overcrowd (mobile `py-20`, desktop `py-32`); only Playfair
+ Inter; icons sparing/thin; gold never dominant; images large portrait (3:4, 4:5); no
tight tracking on body; never skip grayscale; no generic mobile stacking.

## Animation (cinematic timing)
Buttons `duration-500`; colors `duration-700`; images `[1500ms]`–`[2000ms]`; backgrounds
`duration-700`. Easing `ease-out` or custom cubic-bezier — never `ease-in`/`ease-in-out`.
Combine properties (`scale` + `grayscale`); button fills via transform on absolute
overlay. Effects feel intentional and layered.

## Accessibility
Charcoal/alabaster 12.6:1 (AAA); warm-grey/alabaster 4.8:1 (AA); gold/charcoal 5.2:1
(AA); white/charcoal 14.5:1 (AAA). Focus: `ring-1` or gold border, never removed. Respect
`prefers-reduced-motion`. Large body (16–18px), generous line-height, left alignment.
48px (`h-12`) touch targets with spacing.

## Implementation Notes
Tailwind v4 with custom color values; Google Fonts (Playfair Display, Inter); lucide-react
sparingly; custom CSS for noise (SVG data URI) and vertical writing mode. Responsive:
mobile stacks + reduced padding/type; tablet 2–3 col grids; desktop full 12-col asymmetry
+ visible gridlines + vertical text. Performance: CSS transforms (GPU), grayscale, low-cost
shadows. Extract colors to config; build button/card/input variants; add fadeIn keyframe.
