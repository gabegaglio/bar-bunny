# Bar Bunny — Product Specification

## Overview

Bar Bunny is a mobile-first nightlife discovery and bar-hopping application designed
to help users discover nearby bars, build custom bar-hop routes, explore nightlife
hotspots, and see real-time activity trends in their area.

The experience should feel modern, premium, minimal, and location-centric.

**The map is the product. Everything else supports the map.**

---

## Design principles

(Authoritative version lives in [`../CLAUDE.md`](../CLAUDE.md) and
[`../design/design-system.md`](../design/design-system.md).)

Direction: **Swiss Mono** (Swiss International + Minimalist Monochrome) — see
[`../design/styles/swiss-mono-hybrid.md`](../design/styles/swiss-mono-hybrid.md).

- Clean, objective, minimal UI with heavy whitespace and a visible grid
- Mobile-first, fast, simple navigation
- Pure black & white — **no accent color**; emphasis via inversion, weight, and scale
- **No gradients. No glassmorphism. No drop shadows. No rounded corners (0px).**
- **No colored emoji** — monochrome line icons only
- Light vs. dark is semantic: editorial surfaces light, map/night surfaces inverted
- Snappy 100–200ms animations (no slow/springy motion)
- Three type voices: Inter (UI), Playfair Display (statements), JetBrains Mono (data)
- Large map-focused layouts, bordered floating cards, icons integrated into layouts

---

## Tech stack

### Frontend
- React Native + Expo
- TypeScript
- Expo Router
- React Query
- Zustand
- React Native Maps
- Reanimated

### Backend
- FastAPI
- PostgreSQL
- Redis

### Authentication
- **Clerk**

### Maps — Google Maps Platform
- Maps SDK
- Places API
- Directions API
- Geocoding API

---

## User experience

### Home screen
The primary experience.

**Top:** search icon, location indicator.
**Center:** interactive map occupying 70–80% of the screen.
**Bottom:** floating bordered carousel (white card over the inverted map — not glass).

Carousel cards display: bar name, rating, distance, open/closed status, popularity
indicator.

Users can: swipe through bars, tap a card, expand details, add to route.

### Map experience
Bars appear as **nodes** on the map.

Node states:
- **Default** — small clean marker
- **Selected** — enlarged marker, visual highlight
- **Visited** — unique state
- **Saved** — unique state

Users can: tap a marker, open a preview, add to route, save for later.

---

## Route builder (primary feature)

Flow: **Select bar → Add to route → Continue adding → Generate route.**

Display: ordered stops, estimated walking time, total distance, estimated duration.
Route visualization appears directly on the map.

Route features: save, duplicate, edit, delete, share; public or private option.

---

## Discovery

### Nearby bars — filters
Distance, rating, open now, happy hour, live music, sports bar, cocktail bar,
dive bar, rooftop bar.

### Zip code & area discovery
Search by zip code, neighborhood, or city. Results update the map instantly
(e.g. Hoboken, Jersey City, Lower Manhattan).

---

## Heat map system

Visualizes nightlife activity.

**Sources:** anonymous user activity, route-creation frequency, venue engagement,
optional check-ins, saved venues.

**Display:** heat overlay on the map. Toggle: Off / Low / Medium / High Activity.

**Privacy:** fully anonymous, aggregated, delayed, non-identifiable. No individual
tracking. See [`privacy.md`](privacy.md).

---

## User accounts

### Profile
Displays saved routes, favorite bars, route history, privacy settings.

Minimal social features initially — **avoid becoming a social media platform.**

---

## Privacy & safety

Privacy is a core feature. Full detail in [`privacy.md`](privacy.md).

- Location: opt-in, clearly explained, revocable at any time.
- Never expose exact user locations or movement history publicly.
- Heat map data aggregated, anonymous, delayed, non-identifiable.
- Safety: share route with trusted contact, emergency contact, hide activity
  completely, disable participation in analytics.

---

## Information architecture

Avoid traditional bottom tab bars where possible. Prefer map-centric navigation with
lightweight floating controls.

**Main sections:** Map · Routes · Saved · Profile — all reachable through floating UI.

---

## Future features (post-MVP)

- **Friend groups** — group bar hops, invite friends, shared route planning.
- **Venue partnerships** — venue profiles, specials, events, promotions.
- **AI recommendations** — suggest routes by distance, preferences, time available,
  and popularity (e.g. "Best 4-stop cocktail route in Hoboken").

---

## Success criteria

A user should be able to:
1. Open the app.
2. See nearby bars immediately.
3. Discover venues from the map.
4. Build a multi-stop bar-hopping route.
5. Save and share that route.
6. Explore nightlife activity through heat maps.
7. Do all of this through a clean, modern, map-first interface with minimal friction.
