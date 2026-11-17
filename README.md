# Windy Holler: a fictional Chicago-style pizzeria

This checkout is **Windy Holler Chicago-Style Pizzeria**, a parody restaurant site: Chicago deep dish in Razorback territory. `site-profile.json` selects `profiles/windy-holler.toml` with the `multi-location` preset and `use_examples: false`; the records are in `data/restaurant.json`. Every name, address, phone number, dish, price, and story is invented and marked `demo`; see [CLIENT-START.md](CLIENT-START.md) for the fiction rules.

The engine was copied from the Hot Eats master. Its nine illustrative presets, component library and owner tools remain useful engine references below.

**Public preview:** [https://ryan258.github.io/guzanos-pizza/](https://ryan258.github.io/guzanos-pizza/). `.github/workflows/deploy.yml` deploys the preview build to GitHub Pages on every push to `main`: noindex on every page (CI fails the deploy otherwise), review bar, parody note, guide and example routes included. Anyone with the link can see it; noindex is not access control. It is not a publication build.

## Start here

Requires **Hugo 0.166 or newer (extended) and Python 3.11+**; CI builds with 0.166.0. Node is used only by the verification command for JavaScript syntax; no npm or Python package installation is needed.

```sh
./he preview
```

Open http://127.0.0.1:1417/ and `/site-kit/`. Choose another example:

```sh
./he preview --preset food-truck
./he doctor
```

Presets: `kitchen-sink`, `diner`, `cafe`, `fine-dining`, `fast-casual`, `bar`, `bakery`, `food-truck`, `multi-location`. They select modules, a complete illustrative dataset, homepage composition, and component layouts. Each has its own typography, color, border, and card treatment; see [the preset designs](docs/preset-designs.md). Examples are maintained in `data/scenarios.json`; the client's editable records live in `data/restaurant.json`.

The [component living style guide](http://127.0.0.1:1417/site-kit/#presets) includes a nine-design switcher, side-by-side previews of real example pages at desktop or phone widths, and 54 rendered layouts with individual selectors and comparison controls, alternate states, template calls and sample input data, design tokens, category/search tools, palette previews, and a narrow preview. Choose Component showcase in the comparison page selector to see menu sections, tasting menus, beverage flights, team profiles, private dining spaces, and visit steps in each design. The six additions also render on enabled guest pages using validated restaurant records and the selected preset’s layouts. Its layout selectors start with the active preset’s choices. See [component integration](docs/component-library.md). The guide and its preset preview routes are excluded from publication builds.

## Everyday owner work

```sh
./he today
./he menu
./he check
./he today --service pickup --state paused --apply
./he menu --item item-1 --state sold-out --apply
./he history
```

Without `--apply`, changes display a diff. Applied changes create recovery snapshots, materialize the selected example if necessary, and reset publication approval. Short commands work with aliases, voice input, and text expansion. See [the owner guide](docs/owner-guide.md) for hours, menu CSV editing, restore, staff briefs, recipe scaling/cost estimates, and private operational logs.

## Independent restaurant copy

```sh
python3 scripts/sculpt.py --destination ../my-restaurant --name "My Restaurant" --slug my-restaurant --preset cafe
```

The destination must be new and outside this source. The master requires its sibling `the-website-factory/scripts/scaffold_core.py`; generated clients carry a frozen helper and provenance receipt. Copying stages and validates all transformations before reserving the final destination. It clears contacts, schedules, provider destinations, reviews, jobs, and approvals. Retained narrative, menu, policy, and media examples still need editing and review. Private `.local/` state and old build output are never copied.

Use the wrapper to select profile, preset, and dataset consistently. Plain Hugo remains an engine-level development entry point and does not perform Python preflight validation.

## Implemented local capabilities

The inherited engine has historical automated and multi-preset evidence. See [verification scope](docs/verification.md) for the distinction between that history and this checkout’s current fictional dataset. Business facts, provider outcomes, browser/device/print use and publication remain separate acceptance checks.

- Menu search, category/service/location filters, stable dish links, explicit sold-out states, and full/filtered printing.
- Location detail pages, split schedules, date exceptions, access facts, click-to-call, and approved-schedule current-status display.
- Location/service-specific provider handoffs with available/paused/unavailable states and fallback contacts.
- Structured content records and detail pages for specials, catering, events, story, team, sourcing, reviews, news, calendars, careers, access information, press, and truck stops.
- Expired-event states and calendar downloads; local gathering briefs with editable export/import and optional mail-app draft handoff.
- Guest-task search with synonyms and content, mobile quick actions, native FAQs, privacy content, and no-JavaScript reading fallbacks.
- Schema validation, dependency checks, owner diffs/snapshots, content provenance, staged copying, fresh builds, and explicit publication gates.

Provider URLs begin empty. The site does not process payment, send inquiries, create reservations, or collect analytics. Optional professional utilities are local arithmetic and logs, not POS, accounting, or inventory integrations.

## Verification

```sh
./he test
```

Runs the owner-controlled contract regressions, JavaScript syntax check, nine preset builds, local links/assets/anchors, Unicode/copy recovery cases, SVG processing, edited-menu behavior, and a synthetic publication fixture. Temporary artifacts live in the system temporary directory. No network calls or publication. See [verification scope](docs/verification.md).

## Review and publication artifacts

```sh
./he build
./he build --mode publication --destination /tmp/my-restaurant-release
```

Builds use a fresh destination outside source and print a sibling source/data/output manifest. If source changes during a build, no successful manifest is issued. Publication mode requires reviewed client content and a real domain, removes operator/demo output, and enables public metadata. It does not deploy. Preview noindex is not access control. Read [publication and provider acceptance](docs/publication.md) before connecting or releasing a real restaurant.

## Editing map

| Source | Owns |
| --- | --- |
| `site-profile.json`, `profiles/`, `presets/` | Selected identity, module set, presentation, example/client choice; profile settings override the preset |
| `data/restaurant.json` | Client public restaurant records |
| `data/scenarios.json` | Nine illustrative example datasets |
| `data/modules.json` | Module contracts, dependencies, navigation and search vocabulary |
| `scripts/model.py` | Versioned validation and configuration resolution |
| `scripts/owner.py` | Local updates, snapshots, imports, and professional utilities |
| `layouts/partials/modules/` | Independent module renderers |
| `layouts/partials/windy-holler-*.html`, `home-windy-holler.html` | Brand-scoped Windy Holler templates (active when `profileID = "windy-holler"` and `use_examples: false`) |
| `layouts/partials/components/`, `data/component_library.json` | Reusable restaurant components and guide-only example data |
| `assets/` | Readable CSS/JavaScript (`windy-holler.css`, `site.js`) and processed media (`assets/images/windy-holler/`) |
| `.local/` | Private snapshots/operational logs; excluded from public output and copying |

Read [architecture](docs/architecture.md), [data model](docs/data-model.md), [module menu](docs/chisel-menu.md), [sculpting](docs/sculpting.md), and [remediation status](docs/remediation-status.md).
