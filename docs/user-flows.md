# Bar Bunny — User Flows

Step-by-step flows for the core experiences. All screens follow the design precedent
in [`../CLAUDE.md`](../CLAUDE.md): Swiss Mono — pure black & white (no accent), map-
dominant, bordered floating cards (no glass), inverted map surface, no chrome.

---

## 1. Onboarding & location opt-in

1. Launch → brand splash (logo on near-black).
2. Sign in / sign up via **Clerk**.
3. Location permission primer screen — plainly explains *why* location is used
   (find nearby bars) and that it's **revocable any time**.
4. User grants or declines:
   - **Granted** → map centers on current area.
   - **Declined** → map defaults to a searchable area; prompt to search a zip/city.
5. Land on Home.

---

## 2. Home — map + carousel

1. Map fills 70–80% of the screen; nearby bars render as **default nodes**.
2. Floating top: search icon (left/right) + location indicator. No nav bar.
3. Floating bordered carousel at the bottom (white card over the inverted map, not
   glass): bar name, rating, distance,
   open/closed, popularity.
4. Interactions:
   - Swipe carousel → map pans to highlight the corresponding node.
   - Tap card → expand detail.
   - Tap **Add to route** → adds to the current route.

---

## 3. Map node interaction

1. Tap a node → it animates to the **selected** state (enlarged, inverted, with a thin
   ring — the brightest/heaviest marker) and a bordered preview card appears.
2. Preview shows key info + actions: **Add to route**, **Save**, **View details**.
3. Node states reflect status:
   - **Default** — small clean marker
   - **Selected** — enlarged + highlight
   - **Saved** — unique saved styling
   - **Visited** — unique visited styling

---

## 4. Route builder

1. Add bars from carousel, node preview, or detail view.
2. Route tray shows **ordered stops**; user can reorder / remove.
3. **Generate route** → Directions API returns walking time, total distance,
   estimated duration; the route draws directly on the map.
4. Save → name the route, choose **Public** or **Private**.
5. Manage a saved route: edit, duplicate, delete, **share**.
6. **Share with a trusted contact** is offered as a safety action (see privacy).

---

## 5. Discovery — area search & filters

1. Tap search → full-bleed search modal (white, bordered, underlined input — not glass).
2. Enter zip code / neighborhood / city → map recenters instantly (Geocoding).
3. Open filters → distance, rating, open now, happy hour, live music, sports bar,
   cocktail bar, dive bar, rooftop bar.
4. Results update nodes + carousel live.

---

## 6. Heat map

1. Open the heat map control (floating).
2. Toggle: **Off / Low / Medium / High Activity**.
3. Anonymized, aggregated, delayed heat overlay renders over the map.
4. No individual users are ever shown or derivable.

---

## 7. Profile & privacy

1. Open Profile (floating control, not a tab bar).
2. View saved routes, favorite bars, route history.
3. Privacy settings: revoke location, hide activity completely, opt out of analytics,
   set an emergency / trusted contact.
