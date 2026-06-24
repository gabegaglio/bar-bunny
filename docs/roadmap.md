# Bar Bunny — Roadmap

MVP delivered in five phases. Each phase should ship something demoable and stay
within the design precedent in [`../CLAUDE.md`](../CLAUDE.md).

---

## Phase 1 — Core foundation
Stand up the skeleton and prove the map works.

- Scaffold `mobile/` (Expo + TypeScript + Expo Router) and `backend/` (FastAPI).
- Clerk authentication (sign up, sign in, session, sign out).
- Location services: opt-in permission flow, clear explanation, revocable.
- Google Maps integration: render the map at 70–80% of the home screen.
- Nearby venue discovery via Places API; render bars as default markers.
- Floating top bar (search icon + location indicator) — no chrome.

**Done when:** a signed-in user opens the app and sees nearby bars as nodes on a
dark, map-dominant home screen.

---

## Phase 2 — Route builder
The primary feature.

- Tap a node → preview card → Add to route.
- Route state (Zustand): ordered stops, add/remove/reorder.
- Generate route via Directions API: ordered stops, walking time, total distance,
  estimated duration; draw the route on the map.
- Save routes (backend persistence). Edit, duplicate, delete.
- Glassmorphic bottom carousel + route cards.

**Done when:** a user builds, visualizes, and saves a multi-stop route.

---

## Phase 3 — Discovery
Make finding venues effortless.

- Search by zip code / neighborhood / city (Geocoding API); map recenters instantly.
- Filters: distance, rating, open now, happy hour, live music, sports bar,
  cocktail bar, dive bar, rooftop bar.
- Venue detail view (hours, rating, popularity, photos via Places).
- Save venues / favorites; node "saved" and "visited" states.

**Done when:** a user searches an area, filters results, and saves venues.

---

## Phase 4 — Heat map
Visualize nightlife activity — privacy-first.

- Backend aggregation pipeline (Redis + Postgres): activity, route frequency, venue
  engagement, saved venues; aggregated, anonymized, and **delayed**.
- Heat overlay on the map with Off / Low / Medium / High toggle.
- Verify non-identifiability (no individual user can be derived). See
  [`privacy.md`](privacy.md).

**Done when:** a user toggles an anonymized activity heat map over the map.

---

## Phase 5 — Polish
Make it feel premium.

- Reanimated transitions, marker state animations, carousel motion.
- UI refinement against the design system and inspiration references.
- Performance: map marker virtualization, query caching (React Query), cold-start.
- Accessibility review (contrast, dynamic type, screen reader labels, hit targets).
- Safety features hardened: share-with-trusted-contact, emergency contact, hide
  activity, opt out of analytics.

**Done when:** the app meets all seven success criteria smoothly.

---

## Success criteria (MVP exit)

A user can: open the app → see nearby bars immediately → discover venues from the
map → build a multi-stop route → save and share it → explore activity via heat maps —
all through a clean, modern, map-first interface with minimal friction.
