# Windy Holler Chicago-Style Pizzeria

Preset: multi-location, with page choices in `profiles/windy-holler.toml`. Run `./he preview`. Edit `data/restaurant.json` or use `./he today` and `./he menu`.

Windy Holler is a **fictional parody pizzeria**: "Chicago deep dish in Razorback country." Every name, address, phone number, dish, price, and story is invented. It is not affiliated with any real restaurant or with the University of Arkansas. On 2026-11-17 it replaced an earlier unofficial redesign dataset based on a real pizzeria; no real-business records remain in `data/`.

The preview is deliberately public: every push to `main` deploys it to https://ryan258.github.io/guzanos-pizza/ through `.github/workflows/deploy.yml`. Every page is noindex, and CI refuses to deploy a page without it. The repository was renamed from `gusanos-pizza` to `guzanos-pizza` on 2026-11-17; the old Pages URL no longer serves the site. If you rename it again, update `--base-url` in the workflow to match.

Use `./he check` before review and `./he test` for the verification suite. Publication is a separate local build gate and never deploys. Read `docs/owner-guide.md`.

## Fiction rules

- Phones use the fiction-reserved 555-0100 to 555-0199 range; email uses the reserved `.example` domain. Addresses are made-up streets.
- No provider, map, or external links. Ordering actions are `unavailable`; the careers record is `unavailable`.
- Every record's metadata status is `demo`, and the 16 news dispatches carry state `demo` plus a visible "Parody" fact, so a publication build rejects them.
- Don't add fake reviews, press coverage, or staff profiles, and don't reuse a real business's name, menu, or contact details.
- Original illustrations live in `static/images/parody/`. For engine upgrades, add `--exclude /static/images/parody` to the `rsync` in `docs/architecture.md` so they survive.

## Status (2026-11-17)

- `./he doctor` and `./he test` pass on Hugo 0.168.0 (65 unit tests, all nine preset builds, links/assets/anchors, publication fixture).
- Browser at desktop and 375 px: home, news, gallery, and a dispatch render with no console errors or horizontal overflow.

Not verified: assistive technology, print, real devices, and the deployed site after this change (nothing has been pushed).

## Next steps

1. Walk the guest journeys in `./he preview`: search, location switching, menu filters, the gathering brief, and phone navigation.
2. Make engine changes in hot-eats first (`docs/architecture.md` → Upgrade a client): structured pizza sizes and prices, and recurring weekly events.
3. Push to `main` (when you choose) so the site deploys at the renamed URL; until then the new URL serves the old build, whose links still point at the old path.

Engine base: hot-eats commit `<fill in>`. Engine files matched the hot-eats working tree on 2026-10-19, before that work was committed. Upgrade steps: `docs/architecture.md` → Upgrade a client.
