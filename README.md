# Bar Bunny

Mobile-first nightlife discovery and bar-hopping app. Discover nearby bars, build
custom bar-hop routes, explore nightlife hotspots, and see real-time activity trends
in your area.

**The map is the product. Everything else supports the map.**

> Status: **Planning / pre-build.** This repository currently contains product
> specs, the design system, and the design precedent. No application code has been
> written yet — see [`docs/roadmap.md`](docs/roadmap.md) for the build phases.

## What it does

- See nearby bars on a map the moment you open the app
- Tap venue nodes to preview, save, or add them to a route
- Build, save, and share multi-stop bar-hopping routes
- Discover venues by zip code, neighborhood, or city
- View anonymized nightlife activity through a heat map

## Tech stack

| Layer    | Choice                                                                 |
| -------- | ---------------------------------------------------------------------- |
| Mobile   | React Native + Expo, TypeScript, Expo Router, React Query, Zustand, React Native Maps, Reanimated |
| Backend  | FastAPI, PostgreSQL, Redis                                             |
| Auth     | Clerk                                                                  |
| Maps     | Google Maps Platform — Maps SDK, Places, Directions, Geocoding         |

## Repository structure

```
assets/        Brand assets (logo)
design/        Design system + UI inspiration references
docs/          Product spec, roadmap, user flows, privacy, architecture
mobile/        React Native + Expo app (scaffolded in Phase 1)
backend/       FastAPI service (scaffolded in Phase 1)
```

## Start here

- [`CLAUDE.md`](CLAUDE.md) — the design & engineering precedent (read this first)
- [`docs/product-spec.md`](docs/product-spec.md) — full product specification
- [`docs/roadmap.md`](docs/roadmap.md) — MVP phases and success criteria
- [`design/design-system.md`](design/design-system.md) — colors, type, components

## Design philosophy

**Swiss Mono** — a mix of Swiss International Typographic + Minimalist Monochrome:
black & white with a single functional Swiss Red signal, 0px radius, a visible grid,
no gradients/glassmorphism/shadows, monochrome icons, and the map running inverted
(black/white). "A transit map for nightlife." See
[`design/styles/swiss-mono-hybrid.md`](design/styles/swiss-mono-hybrid.md). Privacy
and safety are core features.
