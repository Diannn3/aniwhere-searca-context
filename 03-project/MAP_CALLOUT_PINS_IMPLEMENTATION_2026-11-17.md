---
title: AniWhere callout pins: implementation plan
date: 2026-11-17
status: plan, not built
builds: docs/MAP_CALLOUT_PINS_PLAN_2026-11-17.md
---

# How the callout-pins plan gets built

The design and the evidence are in [MAP_CALLOUT_PINS_PLAN_2026-11-17.md](MAP_CALLOUT_PINS_PLAN_2026-11-17.md). This file says how: branch, files, functions, commits, tests and gates.

## Goal contract

**Branch:** new `update/aniwhere-callout-pins`, from `update/aniwhere-native-pins` at 969e80d. Local only, never pushed unless asked.

**Done means:**
1. Every tier-1 place on the live map is a pill sitting **above** its point, with a tail ending on a ground dot. Any other place is a numbered mini-pin. No tag sits beside a dot any more.
2. Tier size is set by rank and zoom: 4 places on phones, 6 on desktop, about 3 more per zoom step past the fit. Zooming in never shows fewer pills.
3. The selected place is the same pill, inverted to ink. Desktop adds the short name. There is no separate name label.
4. The origin "A" and its label are drawn by MapLibre, so pins avoid them.
5. Route arrows are gone. The distance chip never covers the origin, the destination pin or the control column, and it is hidden when no clear spot exists.
6. At 390×844 with nothing selected, the phone map shows at least 430 px of map between the top bar and the sheet.
7. Saved, Compare, the desktop hero and the confirm rows are fixed as listed in step F.
8. The offline SVG map and the landing sample map use the same callout anatomy.
9. All gates pass, and a fresh critic scores **8 or more**, or 3 critic rounds have run.

**Allowed paths:**
- `src/lib/map/*`
- `src/components/map/*`
- `src/components/discovery/*`
- `src/components/landing/AlmanacMap.astro`
- `src/components/saved/*`
- `src/components/compare/*`
- `src/pages/index.astro`
- `src/styles/{map,discover,global}.css`
- `tests/*`
- `docs/*`

**Forbidden:**
- the fit logic (`src/lib/fit*`) and route data semantics;
- `.env*`, `.vercel`, `.mcp.json` and any settings;
- new npm dependencies.

**Trust boundary (tests stay as they are):**
- the route never changes fit;
- straight-line distance is always labelled as such;
- the origin is the municipality center;
- demo data is labelled.

**Halting gate:** if two consecutive attempts at a step make no measurable progress, or fail with the same error, stop and re-plan that step before trying again.

## Phase A: callout pin images (spike first)

**A0. Spike, not committed.** Before building on the shape, add one callout image and layer in a running preview. Check that the tail stays centred over its point at three label widths ("1 ✓ 300 kg", "3 ◐ 200 of 300", "11 ⊘ No match"), at both 390 and 1440. Measure the text offset that puts the tail tip on the point. If the two-zone stretch drifts, fall back to a fixed-width tail image placed as its own icon under a plain pill.

**A1. `src/lib/map/native-pins.ts`, images (about 110 lines):**
- `callout(status, variant)` replaces `pill()`:
  - canvas 48×38;
  - body `roundRect(1,1,46,28,9)`;
  - tail: a triangle 9 px wide and 6 px tall, centred at x=24, under the body;
  - same fill, stroke and dash per fit as now, with a soft shadow.
- Image options:
  - `stretchX: [[10*PR,19*PR],[29*PR,38*PR]]`: two zones either side of the fixed centre that holds the tail;
  - `stretchY: [[10*PR,19*PR]]`;
  - `content: [5*PR,3*PR,43*PR,27*PR]`: the body only, so the tail stays outside the text box.
- Variants:
  - `aniwhere-callout-<status>` (normal);
  - `aniwhere-callout-<status>-ring` (hover: ink ring 2 px);
  - `aniwhere-callout-selected` (ink fill `#20251e`, white stroke).
- `glyph(status, inverse)`: add white glyph variants `aniwhere-glyph-<status>-inv` for the inverted pin, so each fit glyph stays distinct on ink.
- `originDisc()`: an ink disc 30 px across with a white "A" and a 2 px paper ring, replacing the HTML origin marker.
- Delete `chevron()` and `namePill()`.

## Phase B: layers and tiers

**B1. `native-pins.ts`, layers (about 140 lines).** Layers, bottom to top:

| Layer | Type | Purpose |
|---|---|---|
| `aniwhere-place-hit` | circle r 20, invisible | Click and hover target (unchanged). |
| `aniwhere-place-dot` | circle | One dot per place. Radius from feature-state `pill`: **4** (ground dot under a pill) or **11** (mini-pin); 13 when selected. Halo 2 px paper. |
| `aniwhere-place-num` | symbol | Rank numeral, 11 px bold, ignore-placement. `text-opacity` from feature-state: 0 when `pill`, else 1. |
| `aniwhere-place-pill` | symbol | Tier-1 pills. Filter `tier1 && !selected && !dimmed`. `symbol-sort-key = rank`, single `text-anchor: bottom`, measured `text-offset` (A0), `icon-text-fit: both`, text = `[rank] [glyph] [figure]`. Collision on, so a pill that does not fit is dropped and its place stays a mini-pin. |
| `aniwhere-place-hover` | symbol | Ring variant for the hovered id, whether it is a pill or a mini-pin, so hovering a mini-pin expands it. Allow-overlap and ignore-placement, so nothing else moves. |
| `aniwhere-place-selected` | symbol | Inverted pill. Desktop text `name · figure`, phone `rank · figure`. Allow-overlap. |
| `aniwhere-origin` | symbol | Origin disc (allow-overlap) plus the label "Los Baños center", placed right or left of the disc by `text-variable-anchor-offset`. Top of the stack, so it is placed first and pills give way to it. |

Also in B1:
- `tierSize(base, zoom, fitZoom) = base + 3 * max(0, floor(zoom - fitZoom))`, a pure function so it can be unit-tested.
- Remove the `aniwhere-place-tag`, `aniwhere-place-tag-selected`, `aniwhere-place-name` and `aniwhere-place-block` layers, `setNamedPlace()` and the `BESIDE` offsets.

**B2. `src/components/map/LiveLagunaMap.svelte`, data (about 120 lines):**
- `syncPinData()`:
  - drop `nameAnchor`, `nameOffset`, `tagAllowed` and the origin label discs;
  - add `tier1 = onScreen && !dimmed && rank <= tierSize(phone ? 4 : 6, map.getZoom(), fitZoom)`;
  - `fitZoom` is recorded in `fitAllOutlets()`.
- `markPlacedPills()`, run on `idle`: query the rendered `aniwhere-place-pill` features and set feature-state `{ pill: true }` on those ids (false on the rest). This drives the dot radius and numeral opacity. Pills that collide therefore stay as mini-pins rather than leaving a bare 4 px dot.
- Call `syncPinData()` on `zoomend` (debounced to a frame), so the tier grows as the map zooms in.
- Hover: set the hover layer filter to the hovered id, from map hover or list-row hover (`aniwhere:outlet-hover`).
- Replace `clampPinTag()` on `idle` with `markPlacedPills()`.

**B3. Native origin (about 130 lines, mostly deletions):**
- Remove `ensureOrigin()`'s HTML marker, `flipOriginLabel()`, the `aniwhere-origin-block` source and layer, and the origin CSS in `src/styles/map.css` (lines 58–73).
- Set the origin source data in `syncPinData()`, with the aria label moved to the map's text summary.

## Phase C: route, chip, framing

**C1. Route (about 80 lines):**
- Delete the `aniwhere-route-arrows` layer, `setArrows()` and every call to it. The trace-in stays.
- `syncTripLabel()`: build the boxes to avoid from metrics, not DOM nodes:
  - the origin disc and label (canvas `measureText` with the label font);
  - the selected pill box (projected point, measured width, pill height plus tail);
  - the right-hand control column (56 px);
  - the phone sheet.
- If no candidate point is clear, hide the chip (today it falls back to the midpoint). The trip card already shows the same distance.

**C2. `src/lib/map/map-config.ts` (about 60 lines with tests):**
- `selectedRoutePadding(compact, inset, pin?)`, where `pin = { height, halfWidth }` comes from the selected pill metrics.
- `top = max(base.top, pin.height + 16)`.
- `left` and `right = max(base, pin.halfWidth + 12)`, so the destination pin is never cut off.
- Update `map-config.test.ts`.

## Phase D: live-map tests

**D1. Rewrite `tests/live-map-pins.spec.ts` (about 140 lines).** It stays skipped when the live map cannot load.
- **Above its own point:** for each rendered pill, `queryRenderedFeatures` at its projected point minus 20 px in y returns that same id from the pill layer.
- **Tier caps:** desktop has at most 6 pills and includes rank 1; phone has at most 4.
- **Zoom grows the tier:** count the pills, `zoomIn`, wait for `idle`, and expect at least as many.
- **Mini-pins:** each place without a pill has `pill` feature-state false and a visible numeral.
- **Hover expands:** hovering a mini-pin's point shows the hover layer for that id.
- **Selection:** clicking rank 1 updates the URL, shows the selected layer and no pill or name layers, removes the arrow layer, and the chip box does not intersect the selected pill box.
- **Destination in frame:** the selected point, with the pill height above it, lies inside the container.
- **Reduced motion:** the existing gradient check stays.
- Update `tests/ani-premium-visual.spec.ts` where it references the origin marker.

**D2. Unit tests:** `tierSize()`, plus the padding cases above.

## Phase E: phone map room

**E1. Summary line (about 100 lines, `DiscoveryExperience.svelte` and `src/styles/discover.css`):**
- Add a `docket-line` row: "Tomatoes · 300 kg · Edit". It shows only in phone map view (the `:has([data-view=map])` rules at lines 281–292).
- Put the List/Map switch in that same row.
- The H1 stays in the DOM but is visually hidden in that view, so headings and tests keep working.
- The fit filter row stays one swipeable row (owner decision b).

**E2. Sheet heights (about 60 lines, `MapOutletPicker.svelte`).** Keep the three snaps, `map | peek | full`:
- `peek` with nothing selected is the header plus one row;
- `peek` with a place selected is the compact trip card;
- measure `mobilePickerInset` at 390×844 and tune until at least 430 px of map is visible.

## Phase F: consistency

| Commit | Files | Change |
|---|---|---|
| F1 (about 30 lines) | `SavedOutletsExperience.svelte` | Headings use the shared title tokens. The empty state's `bg-[#FCECD8]/25` tint becomes the standard card surface. |
| F2 (about 40 lines) | `ComparisonExperience.svelte` | Can accept, Left over, Gross and transport cells are right-aligned with `tabular-nums`. Each metric header aligns with its column. |
| F3 (about 20 lines) | `src/pages/index.astro` | Restore desktop hero top padding by tightening the form gaps. "Find places to sell" must end at or above 880 px at 1440×900. |
| F4 (about 50 lines) | `DiscoveryExperience.svelte` | The Contact-to-confirm group gets one `result-group__note`. Each row's `ledger-confirm-note` shrinks to "Ask: capacity, price". |

## Phase G: offline and landing parity

**G1. `src/components/map/ResilientLagunaMap.svelte` (about 140 lines, split if over):**
- An SVG callout: a path for the body and tail above each tier-1 point, using the same fills, glyphs and text;
- numbered mini-pins for the rest, with the same tier caps;
- the inverted pin for the selected place;
- no leader lines.

**G2. `src/components/landing/AlmanacMap.astro` (about 80 lines):** the sample chips become callouts above their dots. The phone crop, and place 3 above its dot, are kept.

## Motion (vault tokens: 120 / 180 / 320 / 480)

| Moment | How it is built |
|---|---|
| First load | Mini-pins fade in with the dot opacity transition (320 ms). Pills appear through MapLibre's symbol fade (`fadeDuration` 180). No per-pin stagger, because native symbols cannot be staggered without timers. |
| Hover | The hover layer appears through the symbol fade (180 ms). The dot radius change uses `circle-radius-transition` 180 ms. |
| Select | The selected layer appears (180 ms), then `frameSelection` 480 ms, then the route trace 520 ms, then the chip `trip-in` 180 ms. This is the existing beat minus the arrows. |
| Step | The old route fades 120 ms, then the same beat runs (unchanged). |
| Zoom | The tier grows through the symbol fade. |
| Reduced motion | `fadeDuration` 0 and all transitions 0: the final state at once (already wired). |

## Commits and gates

Each commit is at most 150 changed lines. Never stage `.gitignore` or the CRLF-only spec files. Every commit ends with the Claude trailer.

**Order:** A1, B1, B2, B3, C1, C2 (+D2), D1, E1, E2, F1, F2, F3, F4, G1, G2, then docs.

**Gates:**
- **After every commit:** `pnpm check`, plus unit tests (`NODE_OPTIONS=--no-experimental-webstorage pnpm test`).
- **After each phase:** `pnpm build`, plus Playwright with `--retries=1`, run in the background. Known flakes, accepted only as "flaky": map-outlet-picker at 768, local-runtime-routing:143, ani-premium-visual:53 and map-routing:108.
- **Before the critic:** a self-check of screenshots at 390 and 1440 on a dedicated preview port (4331, never 4323), and a `web-design-guidelines` review pass.

## Critic loop

- A fresh critic agent each round runs `docs/aniwhere-ui-audit/critic/critic-capture.mjs <round> http://127.0.0.1:4331` (the title guard is on) and scores 0–10.
- The owner decisions a–g are stated up front, plus **(h) labels sit above their point as callout pins**.
- Rounds 29, 30 and 31: stop at 8 or more. Below 8, I fix the ranked list and run the next round, with 3 rounds at most.
- Reports go to `docs/aniwhere-ui-audit/critic/round-29..31/REPORT.md`.

## Roles

| Role | Who |
|---|---|
| Maker | Me, this session. |
| Checker | The deterministic gates above. |
| Critic | A separate general-purpose agent per round that never sees my reasoning, only the brief and the screenshots. |

No other subagents are needed. Every step touches the same map files, so the steps run one after another, not in parallel sessions.

## Risks and fallbacks

| Risk | Fallback |
|---|---|
| The tail drifts at some widths | A0 catches it. Use a separate tail icon under a plain pill. |
| `idle` feature-state pass flickers on first load | Mini-pins render first, and pills fade over them. If it is visible, hold the dot opacity until the first `idle`. |
| Dense clusters (3/4/A and 9/11) | The collision engine plus the tier caps. The ground dots are still separated by `spreadDots()`. |
| The phone map is still under 430 px | Shrink the filter row to icon-only chips first (it already hides the words). Then reduce peek to the header only. |

## Completion receipt (filled in at the end)

- **Commit hashes:**
- **Gate outputs:** check, unit, build, Playwright counts.
- **Critic scores and report paths:**
- **brain_dump entry:**
