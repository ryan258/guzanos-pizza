# Gusano's Chicago-Style Pizzeria

Preset: multi-location, with Gusano's page choices in `profiles/gusanos-pizza.toml`. Run `./he preview`. Edit `data/restaurant.json` or use `./he today` and `./he menu`.

This is an unofficial redesign exercise built from public gusanos.pizza content (read 2026-10-19). It is not affiliated with Gusano's. Every record is `draft` until Gusano's reviews it. Don't publish it without their authorization.

Use `./he check` before review and `./he test` for the verification suite. Publication is a separate local build gate and never deploys. Read `docs/owner-guide.md`.

## Status (2026-10-19)

Verified locally:

- `./he doctor`: Hugo 0.166.0 extended and Python 3.14.7; content and configuration are valid.
- `./he test`: passed (64 unit tests, all nine preset builds, links/assets/anchors, publication fixture).
- Browser at desktop and 375 px: home, specials, a location page, contact, and ordering render with no console errors; the header location switch remembers and clears a location.

Not verified: assistive technology, print, real devices, the Heartland and Toast ordering links, deployed headers, and every business fact. `./he check` lists 70 records awaiting review.

## Next steps

1. Walk the guest journeys in `./he preview`: search, location switching, menu filters, the gathering brief, and phone navigation.
2. Get from Gusano's: current specials, trivia nights for Rogers and Shiloh Dr., catering lead times, private-room capacities, accessibility facts, real photos, Joplin's online ordering link, and confirmation of hours. Mark a record `approved` only after its review.
3. Make engine changes in hot-eats first (`docs/architecture.md` → Upgrade a client): structured pizza sizes and prices, and recurring weekly events.
4. Keep it local. Publication needs a real domain, owner approvals, and Gusano's authorization.

Engine base: hot-eats commit `<fill in>`. Engine files matched the hot-eats working tree on 2026-10-19, before that work was committed. Upgrade steps: `docs/architecture.md` → Upgrade a client.
