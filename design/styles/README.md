# Design Styles

Standalone design-language references. Each file is a complete, self-contained system.

| File | Style | Role | One-line character |
| ---- | ----- | ---- | ------------------ |
| [`swiss-mono-hybrid.md`](swiss-mono-hybrid.md) | **Swiss Mono** | **★ App direction** | Swiss structural rigor + Monochrome editorial drama — "a transit map for nightlife" |
| [`swiss-international.md`](swiss-international.md) | Swiss International Typographic | Parent of hybrid | Objective, grid-as-law, grotesque type, functional Swiss Red |
| [`minimalist-monochrome.md`](minimalist-monochrome.md) | Minimalist Monochrome | Parent of hybrid | Pure black & white, serif as hero, line-based, inversion for emphasis |
| [`luxury-editorial.md`](luxury-editorial.md) | Luxury / Editorial | Reference only | Playfair + Inter, alabaster/charcoal, gold, cinematic motion |

## What the app uses

**Swiss Mono** ([`swiss-mono-hybrid.md`](swiss-mono-hybrid.md)) is Bar Bunny's chosen
visual language — a mix of Swiss International + Minimalist Monochrome. Its working
tokens are wired into [`../design-system.md`](../design-system.md) and the precedent in
[`../../CLAUDE.md`](../../CLAUDE.md).

## Brand pivot note

This direction **replaces** the original dark-mode/glassmorphic nightlife concept. Both
hybrid parents are white-first and explicitly reject glassmorphism and gradients, so:
- Glassmorphism is **dropped** everywhere.
- The palette becomes **black / white + a single functional Swiss Red**.
- "Dark mode" is reframed as **inversion**: the map and night surfaces run black-on-white
  inverted; editorial surfaces run light. See the hybrid doc's dark-mode section.
