# AniWhere map: pins, lines and motion plan (deepsearch, 2026-11-14)

Status: proposal, not built. Branch base: `update/aniwhere-map-almanac` (HEAD 4a70cbc). Critic round 25 = 8.1.

## What the map does today (and why it still feels fiddly)

- Every place is an HTML marker (a `<button>` tag). A custom JavaScript spiral search places them, rotated `<div>` "leaders" link moved tags back to their true spot, and CSS classes swap tags for numbered dots.
- The layout only re-runs when a pan or zoom ends (`moveend` / `zoomend`). During a gesture, tags drift with stale offsets and then jump into place. Collisions, the safe area, the top-five rule and the route-dot hiding are all hand-written.
- Leaders exist only because tags get pushed away from their points. Most of the "lines and stuff" clutter the critics flagged (crossing leaders, anchor dots on chip borders) comes from this.
- Motion is CSS keyframes on HTML pins, plus a `line-gradient` step reveal for the route and contours. Camera, trace and chip are timed separately rather than as one sequence.

## What the research says

- **Markers vs layers.** HTML markers have no collision awareness and slow down as their number grows. MapLibre symbol layers run collision detection every frame and show only what fits. ([Mapbox: markers vs layers](https://docs.mapbox.com/help/dive-deeper/markers-vs-layers/), [Lemontree refactor](https://dev.to/mapbox/how-lemontree-improved-map-performance-with-a-small-refactor-2272), [Symbol layer playground](https://versatiles.org/playground/symbol-layer/))
- **Native placement tools** ([MapLibre style spec, layers](https://maplibre.org/maplibre-style-spec/layers/)):
  - `symbol-sort-key` gives placement priority, so the best fit wins.
  - `text-variable-anchor` / `text-variable-anchor-offset` try the label on several sides of its point before giving up.
  - `icon-text-fit` draws a pill behind the text.
  - `icon-optional` / text-only fallback and `icon-padding` / `text-padding` control collision spacing.
  - MapLibre fades symbols in and out as they collide or clear, so labels never snap.
- **Pin plus optional label.** Google's marker collision docs separate the pin's collision from its label's. Hiding the label while keeping the pin "preserves context". This is the dot-and-tag pattern we already use, done natively. ([Google: control collision behavior](https://developers.google.com/maps/documentation/javascript/3d/marker-collision), [Mapbox: label placement](https://blog.mapbox.com/map-label-placement-in-mapbox-gl-c6f843a7caaa))
- **Leaders.** Labelling research keeps leaders short, uncrossed and ranked, and moves overflow labels to the frame edge. With a fixed map scale, the better fix is to avoid leaders by placing labels next to their points and dropping the low-ranked ones. ([Gedicke et al., Zoomless Maps, IEEE TVCG 2021](https://arxiv.org/abs/2008.13556))
- **Our own precedent.** UPPETITE (`kain_elbi-draft-recovery/app/src/components/map/MapCanvas.svelte`) uses symbol-layer pills ranked by `symbol-sort-key`. It reserves room for HTML controls and the route with invisible "blocker" symbols (`route-blockers`, `pick-blockers`, `top-dot-blockers`) and clusters the rest.
- **Selected and touch.** The selected marker should differ by more than colour (size or outline). Pins anchor at their point. Tap areas can be larger than the visible mark. ([Shopify MapMarker](https://shopify.dev/docs/api/checkout-ui-extensions/2025-07/ui-components/media-and-visuals/mapmarker), [HERE hit areas](https://docs.here.com/here-kb/docs/how-to-increase-marker-click-or-tap-tolerance-using-h-map-hitarea-in-here-maps-api-for-javascript), [Apple HIG: Maps](https://developer.apple.com/design/human-interface-guidelines/maps))
- **Route lines.**
  - Route widths of about 5–8 px, a wider casing underneath and round caps. ([Geoapify route styling](https://dev.to/geoapify-maps-api/how-to-visualize-and-style-routes-on-a-maplibre-gl-map-416g))
  - Direction is clearest with arrows fixed to the line in planning views. Arrows that slide along the line distract. ([Esri on direction](https://www.caliper.com/learning/?p=434657), [Kurviger forum](https://forum.kurviger.de/t/app-route-arrows/1205))
  - A progressive reveal uses `line-gradient` with a `step` on `line-progress` (needs `lineMetrics`). ([MapLibre gradient line](https://maplibre.org/maplibre-gl-js/docs/examples/create-a-gradient-line-using-an-expression/), [MapLibre animate a line](https://maplibre.org/maplibre-gl-js/docs/examples/animate-a-line/), [Mapbox cinematic routes](https://mapbox.com/blog/building-cinematic-route-animations-with-mapboxgl))
- **Map motion.**
  - Animated zoom transitions roughly halved task time, and short animations worked as well as long ones. ([Shanmugasundaram & Irani 2008](https://hci.cs.umanitoba.ca/publications/details/the-effect-of-animated-transitions-in-zooming-interfaces))
  - A transition between places should show the start and the end together at some point. ([arXiv 2406.11493](https://www.arxiv.org/pdf/2406.11493))
  - Tweening can hide changes, a form of change blindness. ([MSU thesis](https://d.lib.msu.edu/etd/17458/FULL_TEXT/view))
  - Feature-state switches snap unless you animate them yourself. ([MapLibre hover example](https://maplibre.org/maplibre-gl-js/docs/examples/create-a-hover-effect/))
- **Vault contract** (`docs/motion/MOTION.md`, `docs/motion/QA_CHECKLIST.md`):
  - one focal action per beat;
  - tokens of 120 / 180 / 320 / 480 ms, with the standard, enter, exit and in/out curves;
  - camera moves only when they lead to information;
  - no loops;
  - reduced motion keeps a stable final state.

## The plan

### 1. Pins: native "dot + optional tag" (replaces the HTML pins and the spiral)

- **Dot (always shown):**
  - a `circle` layer in the fit colour, with a white stroke and the rank number as a small symbol on top;
  - dashed ring for "does not match";
  - collision with `icon-overlap: always`, so a place never disappears.
- **Tag (optional):** a `symbol` layer with:
  - `icon-text-fit: both` on a rounded SDF pill (fit colour or outline per state);
  - formatted text: fit glyph image + "300 kg" / "200 of 300" / "Confirm" / "No match";
  - `text-variable-anchor: [right, left, top, bottom]`, so it sits beside its dot;
  - `symbol-sort-key: rank`, so the best fit wins;
  - padding of 4–6 px.

  When a tag doesn't fit, MapLibre hides it and the dot stays. Fading is built in, layout follows every frame of pan and zoom, and **no leader lines are needed**.
- **Blockers** (from UPPETITE): invisible symbols for the origin "A" and its label, the trip chip, and points along the route. Tags never cover them. The floating controls are handled with map padding.
- **Phone top-five rule:** a filter `rank <= 5` on the tag layer when the sheet is up. Hovering or selecting a place lifts its tag via feature-state.
- **Selected place:** stays one HTML marker (rich tag + name label, focusable, `aria-pressed`). The origin "A" also stays HTML. That is 2 HTML markers instead of 12.
- **Keyboard and screen reader:** unchanged. The map stays a single tab stop with arrow keys and the text summary; list rows remain the button equivalents.
- **Hit areas:** a transparent 22 px `circle` hit layer under each dot (as in UPPETITE), so dots are easy to tap.

### 2. Lines

- **Leaders:** removed, since tags sit next to their dots.
- **Route:**
  - keep Route Blue at 4.5 px over a 9 px cream casing, under the basemap labels;
  - add small **fixed direction chevrons** along the line (`symbol-placement: line`, about 120 px spacing, ink at 60%), shown only after the trace finishes;
  - the straight-line fallback stays dashed and labelled.
- **Trip chip:** moves into the symbol engine (a pill at the route midpoint with blockers at both ends), so it is collision-aware every frame instead of re-placed in JS.
- **Reach rings:** one label per ring as a point feature at a fixed north-west bearing, not along the line. Ring labels drop out on collision (`text-optional`) and are hidden on the phone overview except the outer ring. This stops them running through tags and clipping at the edge.
- **Dots on the route while selected:** become a native filter. Non-selected places are features within a small buffer of the route line.

### 3. Motion (one sequence per action, vault tokens)

| Moment | Beat | Timing / curve |
|---|---|---|
| First load | Dots settle (opacity + 4 px drop, 20 ms stagger by rank, cap 10). Tags fade in with MapLibre's symbol fade. Rings trace once. | 180 ms enter, rings 480 ms |
| Hover (pin or list row) | Dot grows by 2 px with a ring; its tag lifts above others. No camera move. | 120 ms standard |
| Select | (1) The selected tag settles (scale 1.06) and others fade to dots. (2) The camera eases to the route bounds, showing start and end together. (3) The route traces from A, then the chevrons and trip chip fade in. (4) On phones the trip card unfolds alongside step 2. | (1) 180 ms; (2) 480 ms in/out; (3) 520 ms enter, then 180 ms |
| Step to next place | Cross-fade the route (old out 120 ms, new traces) and ease the camera. No zoom-out-and-in arc. | 120 ms + 480 ms |
| Deselect | The route and chip fade out, the camera eases back to all places, and tags fade back in with the symbol fade. | 180 ms + 300 ms |
| Zoom / pan | Labels fade in or out as space allows; nothing jumps. | MapLibre `fadeDuration` set to 180 ms |
| Reduced motion | Camera jumps, the route shows in full, and there is no stagger. MapLibre symbol fade is set to 0. | instant |

- Feature-state changes snap in MapLibre, so hover and selection emphasis use the HTML selected marker plus short CSS transitions. Dots switch through a paint expression with a 120 ms style transition.
- There are no loops, pulses, sliding arrows or long `flyTo` arcs. A deselect while a route is tracing cancels the trace.

## Order of work (small commits, check after each)

1. Native dot + tag layers behind a flag, kept at parity with today's look. Add `symbol-sort-key`, variable anchors, the top-five filter on phones and the hit layer.
2. Blockers (origin, chip, route), then remove the spiral layout, leaders and CSS dot classes. Keep the selected and origin HTML markers.
3. Route chevrons, trip chip as a symbol, and ring labels at a fixed bearing.
4. The motion sequence (select, step, deselect), symbol fade at 180 ms, and the reduced-motion path.
5. New Playwright checks on the live map: tags never overlap (query rendered features), the selected tag is visible, reduced motion gives the final frame instantly, no console errors. Then 390/1440 captures and a critic round.

## Risks

- **Formatted text with an inline glyph image** needs the glyph SDF images registered with `addImage`. The fit glyphs are simple shapes, so this is fine, but it needs a check on MapLibre 6.
- **Live-map pins have almost no end-to-end coverage today:** 14 tests block the map library and use the offline map. Step 5 adds live checks so the rework isn't untested.
- **The offline SVG map** keeps its own pins. It should match the new dot + tag look in a follow-up (same shapes, no leaders).
- **Glyph and font loading:** the tag text uses the basemap's font stack (as the ring labels already do), so no new font requests.
