# Project Roadmap: Hot Eats & Windy Holler

This roadmap outlines the completed architecture, current verified baseline, and prioritized future enhancements for the Hot Eats restaurant platform and Windy Holler, its fictional parody pizzeria.

## Project Vision & Operating Principles

Hot Eats is a production-quality, local-first restaurant website library built for speed, reliability, and owner autonomy.
- **Local-first & static**: Hugo renders the public site; Python handles validation, updates, and packaging. No runtime application server, database, or analytics tracker.
- **Zero-friction owner ergonomics**: Minimal typing, voice- and text-expansion-friendly CLI (`./he`), clear diffs before save, and automatic snapshot recovery.
- **Clean provider handoffs**: Order, reservation, and loyalty destinations link out to dedicated providers with explicit availability guards and fallback contacts, keeping payments and sensitive guest data off the site.
- **Strict verification**: Changes must pass deterministic data contracts, multi-preset builds, and integrity checks before publication.

---

## Completed Milestones (Verified Baseline)

### Architecture & Core Engine
- [x] **24 Modular Restaurant Features**: Complete modular registry in `data/modules.json` covering Dining, Visit, Gatherings, and About with explicit dependency graphs (`requires`, `requires_any`).
- [x] **9 Cohesive Presets**: Full styling, typography, palette, and layout configurations for `kitchen-sink`, `diner`, `cafe`, `fine-dining`, `fast-casual`, `bar`, `bakery`, `food-truck`, and `multi-location`.
- [x] **Multi-Location Pizzeria Implementation**: Profile (`profiles/windy-holler.toml`), custom brand stylesheet (`assets/css/windy-holler.css`), bespoke imagery (`assets/images/windy-holler/`, `static/images/parody/`), and brand-scoped partials (`layouts/partials/home-windy-holler.html`, `windy-holler-*.html`) for Windy Holler, a fictional Chicago-style pizzeria in Razorback territory.
- [x] **Local Owner CLI (`./he`)**: Single entry point for `preview`, `build`, `doctor`, `test`, `check`, `today`, `menu`, `history`, `restore`, and operational utilities.
- [x] **Independent Client Sculptor (`scripts/sculpt.py`)**: Staged, isolated client generation with frozen helper and provenance receipt, preventing accidental overwrites.

### Component System & Living Style Guide
- [x] **18 Presentation Components across 54 Layouts**: Production-ready partials in `layouts/partials/components/` with fallback states, semantic headings, and accessibility tokens.
- [x] **Six Guest-Page Integrated Additions**: Menu sections, tasting menus, beverage flights, team profiles, private dining spaces, and visit planning steps integrated into live templates and data models.
- [x] **Living Style Guide (`/site-kit/`)**: Interactive component catalog, design token references, and side-by-side preset comparison switcher at desktop (1280px) and phone (390px) viewports.
- [x] **Component Showcase**: Scoped showcase routes (`/component-showcase/` and `/site-kit/presets/<preset>/component-showcase/`) rendering all six components in every preset design.

### Data Integrity & Verification
- [x] **Version 2 Restaurant Data Schema**: Rigorous validation in `scripts/model.py` for schedules, date exceptions, provider actions, pricing strings, media confinement, and presentation objects.
- [x] **Owner Change Safety**: Diff-before-save, per-operation snapshots in `.local/history/`, and one-command rollback (`./he restore`).
- [x] **Comprehensive Verification Suite (`./he test`)**: 65 automated unit tests, contracts, JS syntax checks, 9 preset builds, link/anchor auditing, SVG asset verification, and synthetic publication isolation.

---

## Phase 1: Near-Term Priorities

Focus: Operational ergonomics, browser testing automation, and high-fidelity client data.

1. **Loopback Visual Editor (`./he edit`)**
   - Provide a lightweight, local browser interface for common owner tasks (updating today's announcement, toggling sold-out dishes, pausing services, adding date exceptions).
   - Leverage the existing Python backend and validation pipeline; preview diffs and create snapshot backups before committing edits to `data/restaurant.json`.
   - Ensure touch- and keyboard-friendly controls optimized for mobile and desktop local browsers.

2. **Windy Holler Content Pack** (first pass done 2026-11-17)
   - Fictional menu, six locations, specials, rooms, news dispatches, FAQ, and four original illustrations are in place.
   - Next: structured pizza sizes and prices (engine change in hot-eats first) and recurring weekly events.
   - Keep it fictional: no real business names, contacts, reviews, press, or staff.

3. **Automated Browser Regression Harness**
   - Introduce an optional pinned browser test runner (Playwright / Puppeteer) to exercise interactive client journeys:
     - Menu search and real-time category/dietary filtering.
     - Location switcher persistence and URL query parameter propagation.
     - Mobile drawer navigation, keyboard trap prevention, and escape-key handling.
     - Patron brief tool: drafting, local JSON import/export, and mail-app handoff.
   - Validate responsive layouts across 1280px, 768px, 390px, and 320px breakpoints.

---

## Phase 2: Core Enhancements

Focus: Content management depth, print artifacts, and search visibility.

1. **CLI & Tooling for Menu Item Lifecycle**
   - Add `./he menu add` and `./he menu archive` subcommands to allow creating new dishes and retiring seasonal items without manually editing raw JSON.
   - Enforce schema rules (unique IDs, decimal pricing, required categories) at point of entry.
   - Maintain historical dish permalinks with clear archived notices or redirects.

2. **Shareable Print Layouts**
   - Implement dedicated print stylesheets and a clean printable menu view (`/menu/print/`) formatted for standard Letter and A4 paper.
   - Include restaurant identity, current date, location-specific pricing, dietary key, and QR code permalinks.
   - Provide a printable location visit sheet with directions, parking notes, and accessibility facts.

3. **Media Pipeline & Rights Register**
   - Establish a media rights and permissions register (`data/media_register.json`) tracking photo credits, license expiration, and model releases.
   - Support responsive image generation for client photography while preserving vector SVG assets without raster conversion.
   - Add gallery collection filtering and high-resolution modal previews.

4. **Discoverability & Rich Snippets**
   - Expand Schema.org `Restaurant` and `LocalBusiness` JSON-LD output to include geo-coordinates, postal addresses, price range, and accepted payment methods.
   - Generate OpenGraph and Twitter card metadata for dish permalinks, news items, and event records.
   - Add automatic sitemap generation for publication builds.

---

## Phase 3: Operational Utilities & Advanced Features

Focus: In-house kitchen tooling, scheduling automation, and internationalization.

1. **Professional Kitchen Utilities Expansion**
   - Extend `./he scale` with recipe card templates and batch conversion tables.
   - Enhance `./he cost` with ingredient price databases, yield percentages, and margin calculators.
   - Export operational logs (`.local/operations.jsonl`) to structured CSV summaries for prep sheets and waste reporting.

2. **Recurring Event & Truck Schedule Engine**
   - Support recurring date rules (e.g., "Every Tuesday", "First Friday of each month") with timezone-aware calendar generation.
   - Provide automated expiry and rollover for weekly food truck stops and taproom events.
   - Export standards-compliant iCalendar (`.ics`) feeds for guest calendars.

3. **Multilingual Guest Content (i18n)**
   - Utilize Hugo’s native multilingual features for localized menus and visitor guidance.
   - Maintain synchronous translation status to flag missing or outdated dish translations.
   - Preserve location and service query parameters across language toggles.

---

## Explicit Boundaries & Out of Scope

To preserve simplicity, speed, and privacy, the following are intentionally **excluded** from the platform architecture:
- **No hosted databases or authentication servers**: No user logins, passwords, session cookies, or member databases.
- **No integrated payment processing**: Credit card transactions and order fulfillment are handled exclusively by authorized external providers.
- **No third-party analytics or surveillance trackers**: No Google Analytics, Meta Pixel, or marketing beacons.
- **No automated publication**: The only automated deployment is the noindex Windy Holler preview to GitHub Pages on push to `main` (`.github/workflows/deploy.yml`). Publication builds and any other deployment remain under explicit owner control.
