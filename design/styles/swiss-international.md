# Design Style: Swiss International (International Typographic Style)

> Standalone style reference. One of the two parents of the app's chosen direction —
> see [`swiss-mono-hybrid.md`](swiss-mono-hybrid.md).

## Design Philosophy

**The International Typographic Style (Swiss Style)** is not merely a visual trend; it
is a philosophy of objective communication born in 1950s Switzerland. It rejects
personal expression and subjectivity in favor of universal clarity, mathematical
precision, and logical structure.

**Core Tenets:**

1. **Objectivity over Subjectivity** — design recedes to let content speak. Every
   visual decision is justifiable by the content's needs. The designer is a conduit
   for information, not an artist expressing themselves.
2. **The Grid as Law** — the grid is the absolute authority and the visible skeleton
   of the information. Prefer **asymmetrical organization** over static centering to
   create dynamic rhythm and tension. Grid is made visible through subtle textures.
3. **Typography is the Interface** — type is the primary structural and graphical
   element. Grotesque sans-serifs (Inter, Helvetica) are neutral vessels for meaning.
   Scale, weight, and position create hierarchy.
4. **Active Negative Space** — white space is a structural element. It defines
   boundaries and gives weight to massive typography.
5. **Layered Texture & Depth** — maintain flatness (no shadows/3D) but achieve depth
   through subtle pattern overlays: grid lines (24px), dot matrices (16px), diagonal
   stripes, noise.
6. **Universal Intelligibility** — understood instantly; clean, legible, modern.

**The Vibe:** Intellectual & architectural; structured yet organic; brutally precise;
timeless (avoids glassmorphism, neumorphism, soft rounded corners).

**Visual Signatures:** flush-left ragged-right text; grotesque sans-serif; mathematical
scales; the **Swiss Red `#FF3000`** as a functional signal (not decoration);
pattern-based texture; Bauhaus-inspired geometric abstraction.

## Design Tokens

### Colors (strict palette)
- **Background** `#FFFFFF` — neutral canvas
- **Foreground** `#000000` — text is absolute
- **Muted** `#F2F2F2` — secondary backgrounds for rhythm
- **Accent** `#FF3000` (Swiss Red) — the **only** signal color, used sparingly for CTAs and critical emphasis
- **Border** `#000000` — structure is visible

### Typography
- **Family:** Inter (closest to Helvetica/Akzidenz-Grotesk)
- **Weights:** Black (900) and Bold (700) for headings; Regular (400)/Medium (500) for body
- **Style:** UPPERCASE for almost all headings and labels
- **Tracking:** `tracking-tighter` for large headlines, `tracking-widest` for small labels
- **Scale:** extreme contrast — headlines `text-7xl`–`text-9xl`+; body legible/objective

### Radius & Border
- **Radius:** `0px` (strictly rectangular)
- **Borders:** thick, visible (`border-2`/`border-4`); define the grid

### Shadows & Effects
- **Shadows:** none — maintain flatness. Only subtle ring shadows for compositional
  geometry (e.g. `shadow-[0_0_0_8px_rgba(255,48,0,0.1)]` accent circles).
- **Effects:** color inversion (Black→White, White→Red), scale (1.0→1.05), rotation
  (0°→90° for plus icons), vertical translate (-1px lift on hover).

### Textures & Patterns (critical for depth)
- **Grid** `.swiss-grid-pattern` — 24×24px lines, 3% opacity (hero, sidebars, muted bg)
- **Dot matrix** `.swiss-dots` — radial dots, 16×16px, 4% opacity (section headers)
- **Diagonal** `.swiss-diagonal` — 45° lines, 10px, 2% opacity (accent backgrounds)
- **Noise** `.swiss-noise` — SVG fractal noise, 1.5% opacity (global body)

**Application:** patterns on muted gray (`#F2F2F2`) and occasionally white. Never on
pure black or red areas. Patterns enhance, never dominate.

## Components

- **Buttons** — rectangular (`rounded-none`); solid black/white text (primary), white +
  black border (secondary); hover inverts or switches to Swiss Red; uppercase, bold,
  tracking-wide.
- **Cards** — defined by borders (`border-black`); white or muted gray bg; generous
  uniform padding (`p-8`/`p-12`); hover changes whole card bg with text inversion.
- **Inputs** — underlined (`border-b`) or thick rectangular box; focus → sharp Swiss
  Red border, no glow.

## Layout
Grid is God and often visible (borders on elements). Embrace asymmetrical balance.
Strict left alignment. Horizontal/vertical lines as separators.

## Non-Genericness
Massive responsive typography (`text-6xl` → `text-[10rem]`); visible structure (4px
borders, 24px grid pattern, asymmetric ratios 8:4/7:5/5:7); numbered section labels
(01./02./03./04.) in red; layered geometric Bauhaus compositions; four CSS patterns;
bold interaction states (full inversions, rotating icons, scale, lift); active negative
space; functional color (red only for CTAs/hover/section numbers — never decorative).

## Spacing & Iconography
High density in information clusters, spaciousness in narrative sections. `lucide-react`
icons as functional symbols; stroke width matches typography; often enclosed in
squares/circles.

## Animation
Instant, mechanical, snappy, precise. `duration-200 ease-out` or `duration-150
ease-linear`. No elastic/spring. Navigation vertical-slide with color change; stats
scale + rotating plus + bg snap; feature cards invert + arrow rotation; testimonials
-1px lift + border color change; FAQ rotating plus + bg inversion; buttons instant bg
change. Hover always indicates interactivity through color/scale/position — never fades.

## Responsive
Bold character at all sizes. Mobile: `text-6xl` hero, single column, borders stay 4px,
full-width CTAs (`h-16`), patterns keep opacity/scale, stats 2×2, nav collapses.
Tablet: two-column, `text-8xl`, asymmetric grids, 44×44px targets. Desktop: full
asymmetric grids, `text-9xl`/`text-[10rem]`, multi-column, sticky headers, all hovers.

## Accessibility
Black/white ≈ 21:1 contrast. Ensure red-on-white meets AA. Focus: 2px red ring with
offset. 44×44px touch targets. CSS animations respect `prefers-reduced-motion`. Proper
heading hierarchy, semantic HTML5, ARIA where needed.
