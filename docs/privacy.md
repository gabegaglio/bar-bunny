# Bar Bunny — Privacy & Safety

Privacy is a **core feature**, not a setting buried in a menu. These requirements are
binding (see also [`../CLAUDE.md`](../CLAUDE.md)).

---

## Location handling

Location must be:
- **Opt-in** — never collected before the user grants permission.
- **Clearly explained** — the primer screen states exactly why location is used.
- **Revocable at any time** — from Profile → Privacy, with immediate effect.

Hard rules:
- **Never expose a user's exact location.**
- **Never expose a user's movement history publicly.**
- Precise coordinates stay on-device or are coarsened server-side; only what a
  feature strictly needs is sent.

---

## Heat map privacy

Heat map data must be:
- **Aggregated** — computed across many users, never per-user.
- **Anonymous** — no identifier ties a data point to a person.
- **Delayed** — not real-time, so presence can't be inferred from the overlay.
- **Non-identifiable** — minimum aggregation thresholds; suppress sparse cells so a
  single user can't be reverse-derived.

**No individual user tracking. Ever.**

Sources feeding aggregation (all anonymized): activity, route-creation frequency,
venue engagement, saved venues, optional check-ins.

---

## Safety features

Users must be able to:
- **Share a route with a trusted contact.**
- Set an **emergency contact**.
- **Hide activity completely** (no contribution to any visible signal).
- **Disable participation in analytics** entirely.

These are first-class, easy-to-reach actions — not hidden.

---

## Data minimization & secrets

- Collect the minimum needed for a feature to function.
- API keys (Google Maps, Clerk) and secrets are **never committed** — `.env` /
  platform secret stores only (`.env` is gitignored).
- Default to privacy-preserving settings; make the safe choice the easy choice.

---

## Anti-goals

- Not a social media platform.
- No public movement feeds.
- No selling or exposing identifiable location data.
