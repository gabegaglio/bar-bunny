# Bar Bunny — Design System

Concrete tokens and component rules. The precedent in [`../CLAUDE.md`](../CLAUDE.md)
governs; this file makes it buildable. References live in
[`inspiration/`](inspiration/).

---

## Foundations

### Color
Dark mode first. **No gradients. No colored emoji. One accent color, used sparingly.**

| Token              | Role                                  | Value (proposed, confirm) |
| ------------------ | ------------------------------------- | ------------------------- |
| `bg/primary`       | App background (map underlay)         | near-black `#0A0A0B`      |
| `surface/glass`    | Glass cards (semi-transparent + blur) | `rgba(20,20,22,0.55)`     |
| `surface/raised`   | Solid raised surface                  | `#161618`                 |
| `text/primary`     | Primary text                          | `#F5F5F7`                 |
| `text/secondary`   | Secondary text                        | `#A1A1AA`                 |
| `accent`           | Single brand accent (CTAs, selection) | **TBD — confirm hex**     |
| `state/positive`   | Open now                              | muted green               |
| `state/muted`      | Closed / inactive                     | `#52525B`                 |

> **TBD:** pick one accent hex that matches the bunny brand (a single warm neon is a
> good direction). Used only for active/selected states and primary CTAs — never as
> a fill gradient.

### Typography
Inter (or SF Pro / Geist). No decorative fonts. Premium, highly readable.

| Style       | Size / weight        | Use                          |
| ----------- | -------------------- | ---------------------------- |
| Display     | 28–32 / 600          | Screen titles (rare)         |
| Title       | 20–22 / 600          | Card titles, venue names     |
| Body        | 15–16 / 400–500      | Default text                 |
| Caption     | 12–13 / 500          | Distance, status, metadata   |

### Spacing & radius
- 4px base grid: 4 / 8 / 12 / 16 / 24 / 32.
- Heavy whitespace; let content breathe over the map.
- Radius: cards 20–24px, controls/pills 999px (fully rounded), markers circular.

### Elevation, not borders
Separate elements with shadow + glass, **not hard borders**. Avoid 1px dividers and
nav-bar chrome. If you reach for a border, reconsider.

---

## Glassmorphism spec

Use **only** on: bottom carousel, route cards, search modal, floating controls.

- Background: `surface/glass` (semi-transparent dark).
- Blur: moderate (~20–30 blur radius); **never so heavy it hurts readability**.
- Subtle inner highlight at top edge optional; no gradients.
- Always keep text contrast AA+ over the blurred map beneath.

---

## Components

### Map markers (nodes)
| State    | Style                                              |
| -------- | -------------------------------------------------- |
| Default  | Small circular monochrome marker                   |
| Selected | Enlarged, accent ring/highlight, subtle pop anim   |
| Saved    | Distinct saved glyph (monochrome line icon)        |
| Visited  | Distinct visited treatment (e.g. filled/dimmed)    |

### Bottom carousel card (glass)
Bar name (Title) · rating · distance · open/closed (`state/*`) · popularity ·
**Add to route** action. Horizontally swipeable; selecting pans the map.

### Floating controls
Search, location, heat-map toggle, profile — circular/pill glass buttons floating
over the map. No bottom tab bar.

### Icons
Monochrome **line icons only** (e.g. Lucide on RN, or SF Symbols). Integrated
directly into layouts. **Never colored emoji.**

---

## Motion
Reanimated. Smooth, native-feeling, purposeful: marker select pop, carousel paging,
modal/sheet spring, route draw-on. Nothing flashy.

---

## DON'T (enforceable in review)
- No gradients (anywhere)
- No colored emoji
- No hard borders / nav-bar chrome / bottom tab bars
- No heavy blur that hurts readability
- No more than one accent color
- No decorative fonts
- No UI that shrinks the map below ~70% on the home screen
