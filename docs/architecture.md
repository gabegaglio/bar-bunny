# Bar Bunny — Architecture

High-level system design and draft data model. Implementation begins in Phase 1
([`roadmap.md`](roadmap.md)).

---

## System overview

```
┌─────────────────────────────┐
│  Mobile app (Expo / RN)     │
│  Expo Router · React Query  │
│  Zustand · RN Maps · Reanim │
└───────┬─────────────┬───────┘
        │             │
        │ Clerk SDK   │ HTTPS (REST/JSON)
        ▼             ▼
   ┌─────────┐   ┌─────────────────────────┐
   │  Clerk  │   │  FastAPI backend        │
   │ (auth)  │   │  routes · venues · heat │
   └─────────┘   └───────┬─────────┬───────┘
                         │         │
                    ┌────▼───┐ ┌───▼────┐
                    │Postgres│ │ Redis  │
                    │(durable│ │(cache, │
                    │ data)  │ │ heat   │
                    └────────┘ │ aggreg)│
                               └────────┘

         Google Maps Platform (called from client and/or server):
         Maps SDK · Places · Directions · Geocoding
```

- **Auth:** Clerk issues sessions; the backend verifies Clerk tokens on protected
  endpoints. User identity is keyed by Clerk user id.
- **Backend:** FastAPI serves venue lookups, route persistence/sharing, and the
  heat-map aggregation API.
- **Postgres:** durable data (users, routes, saved venues, cached venue records).
- **Redis:** hot caches (nearby results, sessions) and the rolling heat-map
  aggregation buffers (so raw events expire and only aggregates persist).

---

## Google Maps API → feature mapping

| API           | Powers                                                        |
| ------------- | ------------------------------------------------------------- |
| Maps SDK      | The map surface, nodes/markers, route polylines, heat overlay |
| Places API    | Nearby bars, venue details, photos, ratings, open/closed      |
| Directions API| Route generation: ordered stops, walking time, distance       |
| Geocoding API | Zip / neighborhood / city search → recenter map               |

Keys are restricted (platform + API scope) and **never committed** — see
[`privacy.md`](privacy.md).

---

## Draft data model

Indicative, not final — refined in Phase 1.

- **users** — `id`, `clerk_user_id`, `created_at`, privacy/safety prefs
  (`hide_activity`, `analytics_opt_out`), `emergency_contact`, `trusted_contact`.
- **venues** — cached Places data: `id`, `google_place_id`, `name`, `lat`, `lng`,
  `categories[]` (cocktail/dive/rooftop/sports/live-music…), `rating`,
  `price_level`, `hours`, `last_synced_at`.
- **routes** — `id`, `owner_user_id`, `name`, `visibility` (public/private),
  `total_distance`, `est_duration`, `created_at`, `updated_at`.
- **route_stops** — `id`, `route_id`, `venue_id`, `position` (ordering).
- **saved_venues** — `user_id`, `venue_id`, `state` (saved/visited), `created_at`.
- **heatmap_aggregates** — `geohash_cell`, `time_bucket`, `activity_score`,
  `sample_count`. **Aggregated, anonymized, delayed**; cells below a minimum
  `sample_count` are suppressed so no individual is derivable.

No table stores raw, timestamped, per-user location trails for public exposure.

---

## Privacy by architecture

- Precise coordinates are coarsened (geohash cells) before any aggregation.
- Heat-map raw inputs live in short-TTL Redis buffers; only aggregates persist.
- A minimum aggregation threshold + time delay prevent re-identification.
- Hidden / analytics-opted-out users contribute to **nothing** visible.
