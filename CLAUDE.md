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

**Visual direction: Swiss Mono** — a mix of Swiss International Typographic + Minimalist
Monochrome. "A transit map for nightlife." Full reasoning in
[`design/styles/swiss-mono-hybrid.md`](design/styles/swiss-mono-hybrid.md); working
tokens in [`design/design-system.md`](design/design-system.md).

- **Map-first.** The interactive map occupies 70–80% of the home screen. UI sits over
  it in bordered cards; it never boxes the map in with chrome.
- **Pure monochrome — black & white only. No accent color** (no Swiss Red, no gold).
  Selection, live state, primary CTAs, and focus are expressed through **inversion,
  border weight, fill-vs-outline, and scale** — never color.
- **Light vs. dark is semantic, not a theme toggle.** Editorial surfaces (onboarding,
  route summary, profile, lists) run light (white/black). The map and night surfaces
  run **inverted** (black/white). Inversion is also how we emphasize.
- **NO gradients. NO glassmorphism / blur. NO drop shadows. NO rounded corners (0px).**
  Depth comes from contrast, border weight, pattern, and inversion only.
- **NO colored emoji.** Monochrome `lucide-react` line icons only (1–1.5px stroke).
- **The grid is law and visible.** Thick black section rules, hairline dividers,
  asymmetric ratios (8:4 / 7:5 / 5:7), strict left alignment, generous negative space.
- **Three type voices, zoned:** Inter (structure/UI/labels, UPPERCASE), Playfair
  Display (large editorial statements & pull-quotes), JetBrains Mono (data — distance,
  ETA, coordinates, stop numbers). No other fonts.
- **Motion is snappy, 100–200ms,** `ease-out`/`ease-linear`. Color inversions, 90° icon
  rotation, scale 1.05, -1px lift, grayscale→color on imagery. No spring/cinematic
  motion. Respect `prefers-reduced-motion`.

See [`design/styles/`](design/styles/) for the full style references and
[`design/inspiration/`](design/inspiration/) for visual references.

### Quick review checklist
- [ ] No gradient, glassmorphism/blur, or drop shadow anywhere in the diff
- [ ] No rounded corners (0px radius everywhere)
- [ ] No color at all beyond black & white (no accent); state never shown by color alone
- [ ] No colored emoji; icons are monochrome line icons
- [ ] Map remains visually dominant; map/night surfaces use inversion, not glass
- [ ] Fonts are Inter / Playfair Display / JetBrains Mono only
- [ ] Motion stays 100–200ms (no slow/springy easing)

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
