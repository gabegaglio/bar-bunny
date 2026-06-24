# Bar Bunny — Project Precedent

This file is the law for Bar Bunny. Every contributor and every AI agent must follow
it. Design rules here are **non-negotiable** and enforceable in review.

---

## Product north star

Bar Bunny is a mobile-first nightlife discovery and bar-hopping app. **The map is the
product.** Everything else supports the map. The experience must feel modern, premium,
minimal, and location-centric.

---

## Design precedent (hard rules)

These are not suggestions. A change that violates any of these should be rejected.

- **Map-first.** The interactive map occupies 70–80% of the home screen. UI floats
  over it; it never boxes the map in.
- **Dark mode first.** Near-black primary background. Glass surfaces are
  semi-transparent. A single brand accent color — no more.
- **NO gradients.** Anywhere. Flat surfaces only.
- **NO colored emoji.** Use monochrome line icons (e.g. Lucide / SF Symbols) only.
- **Limited borders / no chrome.** Avoid traditional nav bars and tab bars. Integrate
  icons directly into the screen. Separate content with whitespace and subtle
  elevation, not boxes and dividers.
- **Glassmorphism, sparingly.** Allowed on: bottom carousel, route cards, search
  modal, floating controls. Avoid heavy blur. Readability always wins.
- **Typography is premium and clean.** Inter / SF Pro / Geist. No decorative fonts.
- **Heavy whitespace. Smooth, native-feeling animations** (Reanimated).
- **Floating, map-centric navigation.** Avoid bottom tab bars where possible.

See [`design/design-system.md`](design/design-system.md) for concrete tokens and
[`design/inspiration/`](design/inspiration/) for visual references.

### Quick review checklist
- [ ] No gradient anywhere in the diff
- [ ] No colored emoji; icons are monochrome line icons
- [ ] No new hard borders / nav-bar chrome
- [ ] Glass effects limited to the approved surfaces, blur kept readable
- [ ] Map remains visually dominant on map screens
- [ ] Fonts are Inter / SF Pro / Geist only

---

## Privacy & safety are features

- Location is **opt-in, clearly explained, and revocable at any time.**
- **Never** expose a user's exact location or movement history.
- Heat map data must be **aggregated, anonymized, delayed, and non-identifiable.**
  No individual user tracking.
- Ship safety affordances: share route with a trusted contact, emergency contact,
  hide activity completely, opt out of analytics.

See [`docs/privacy.md`](docs/privacy.md).

---

## Tech stack (committed)

**Mobile:** React Native + Expo, TypeScript, Expo Router, React Query, Zustand,
React Native Maps, Reanimated.

**Backend:** FastAPI, PostgreSQL, Redis.

**Auth:** Clerk.

**Maps:** Google Maps Platform — Maps SDK, Places API, Directions API, Geocoding API.

Mobile code lives in `mobile/`, backend in `backend/`. Don't mix concerns across
those boundaries.

---

## Engineering conventions

- **Secrets never get committed.** API keys (Google Maps, Clerk) live in `.env` /
  platform secrets. `.env` is gitignored.
- **Plan before code.** Non-trivial features get a short plan / design note first
  (this repo started planning-first on purpose).
- **TypeScript everywhere** on mobile; type the API boundary.
- Keep components small; match the surrounding code's style and naming.
- End git commit messages with:

  `Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>`

---

## Current status

Planning / pre-build. No application code yet. `mobile/` and `backend/` are
placeholders until Phase 1 of [`docs/roadmap.md`](docs/roadmap.md).
