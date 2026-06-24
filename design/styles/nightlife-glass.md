# Design Style: Nightlife Glass (original concept — reference only)

> The app's **original** direction, kept here for reference. **Not** the current
> direction — the app now uses pure-monochrome **Swiss Mono**
> ([`swiss-mono-hybrid.md`](swiss-mono-hybrid.md)), which drops glassmorphism. Preserved
> in case the premium dark/glass aesthetic is revisited.

## Design Philosophy

Modern, premium, minimal, location-centric. **The map is the product.** Dark-mode-first
nightlife aesthetic without feeling flashy: large map-focused layouts, floating UI,
glassmorphic surfaces, minimal chrome, hidden navigation where possible, icons integrated
directly into layouts, clean typography, heavy whitespace, smooth native-feeling motion.

**Vibe:** premium, nocturnal, calm, tactile glass over a living map.

## Design Tokens

### Color (dark mode first)
| Token            | Role                                  | Value                  |
| ---------------- | ------------------------------------- | ---------------------- |
| `bg/primary`     | App background (map underlay)         | near-black `#0A0A0B`   |
| `surface/glass`  | Glass cards (semi-transparent + blur) | `rgba(20,20,22,0.55)`  |
| `surface/raised` | Solid raised surface                  | `#161618`              |
| `text/primary`   | Primary text                          | `#F5F5F7`              |
| `text/secondary` | Secondary text                        | `#A1A1AA`              |
| `accent`         | Single brand accent (CTAs, selection) | TBD (one warm neon)    |
| `state/positive` | Open now                              | muted green            |
| `state/muted`    | Closed / inactive                     | `#52525B`              |

Single accent color only. **No gradients. No colored emoji.**

### Typography
Inter / SF Pro / Geist. Premium, highly readable. No decorative fonts.

### Radius, borders, shadows
Rounded glass cards (20–24px), fully-rounded pill controls. Limited hard borders — rely
on glass + subtle elevation instead of boxes/dividers. No traditional nav bars/tab bars.

### Glassmorphism (the signature)
Used **sparingly** on: bottom carousel, route cards, search modal, floating controls.
Semi-transparent dark surface + moderate blur (~20–30). Never so heavy it hurts
readability. No gradients; optional subtle top-edge highlight.

## Components
- **Markers (nodes):** default small circular marker; selected enlarged + accent
  highlight; saved/visited distinct treatments.
- **Bottom carousel (glass):** bar name, rating, distance, open/closed, popularity,
  Add to route. Swipeable; selection pans the map.
- **Floating controls:** circular/pill glass buttons (search, location, heatmap,
  profile) over the map. No bottom tab bar.
- **Icons:** monochrome line icons (Lucide / SF Symbols), integrated into layouts.

## Motion
Smooth, native-feeling (Reanimated): marker-select pop, carousel paging, modal/sheet
spring, route draw-on. Purposeful, not flashy.

## Why it was set aside
The Swiss / Monochrome direction the user chose is white-first and explicitly rejects
glassmorphism and (in pure form) accent color. The two are not compatible as a single
system, so this concept lives on as a reference rather than the active spec.
