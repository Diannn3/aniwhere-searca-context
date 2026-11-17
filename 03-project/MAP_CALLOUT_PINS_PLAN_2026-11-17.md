# AniWhere map: callout pins plan (deepsearch, 2026-11-17)

Status: proposal, not built. Base: `update/aniwhere-native-pins` (HEAD 969e80d). Critic history: round 25 = 8.1 (HTML tags carrying their number), native rebuild rounds 26–28 = 7.6 / 7.4 / 7.4.

## What the evidence says

### Our own record (vault)
- **Round 25 scored 8.1** with tags that *were* the marker: the rank number sat on the tag.
- **Since the native rebuild split each place into a dot plus a separate tag,** every critic has flagged "which tag belongs to which dot". Rounds 26–28 named it as the top or second issue.
- **UPPETITE's map** (`kain_elbi-draft-recovery/.../MapCanvas.svelte`) used the same engine-placed labels around dots (`text-variable-anchor` with a radial offset) and stalled at 7.3. That makes two products and one failure mode.
- **What carries over from UPPETITE:**
  - renderer collision instead of HTML markers;
  - rank tiers;
  - invisible "blockers" that reserve room;
  - a 20 px invisible hit circle.

### Label position research
- **Imhof (classic cartography)** prefers up-and-right of the point.
- **A 2024 user study (PerceptPPO)** found readers associate a label best when it sits **directly above** its point, then below, then right. The full order is T, B, R, TR, BR, L, TL, BL. Top was "especially favored". ([arXiv 2407.11996](https://arxiv.org/html/2407.11996v2))
- **Imhof's rules:** a label must be legible, easy to associate with its feature, and must not overlap other map content. ([Cartographic Perspectives CP60](https://cartographicperspectives.org/index.php/journal/article/download/cp60-kern-brewer/pdf/1397), [Christensen, Marks & Shieber](https://www.merl.com/publications/docs/TR94-12.pdf))
- **Why our tags fail:** they move between sides and leave a gap, so association breaks. A label that is physically joined to its point removes the problem.

### Industry precedent
- **Airbnb tiers its pins.**
  - The best-ranked listings get full oval *price pins*; the rest get small *mini-pins* with no price.
  - Hovering a mini-pin enlarges it and reveals its price.
  - The tiers were A/B-tested (bookings +0.27%). Their stated principle is "less is more".
  - This matches our phone top-five rule, but Airbnb tiers by rank on purpose, not by collision luck.
  - Sources: [Airbnb engineering](https://medium.com/airbnb-engineering/improving-search-ranking-for-maps-13b03f2c2cca), [Learning to Rank for Maps at Airbnb](https://arxiv.org/abs/2407.00091), [Airbnb community](https://community.withairbnb.com/t5/Ask-about-your-listing/AirBnB-Map-Symbols-Small-Unlabeled-White-and-Gray-Shapes/m-p/1880164).
- **The callout shape is native to MapLibre.** A stretchable image with **two `stretchX` zones** keeps a centre part fixed while the pill grows around the text, so a pointer tail stays centred. ([MapLibre stretchable image](https://maplibre.org/maplibre-gl-js/docs/examples/add-a-stretchable-image-to-the-map/), [Mapbox equivalent](https://docs.mapbox.com/mapbox-gl-js/example/add-image-stretchable))
- **Route arrows** help mainly when zoomed in or in step-by-step previews. In an overview they read as clutter. That matches what critics reported twice. Clear, distinct start and end markers do the direction work instead. ([Kurviger forum](https://forum.kurviger.de/t/app-route-arrows/1205), [navigation manual](https://www.manualsdir.com/manuals/115979/mio-miomap-c220.html?page=22), [Azure Maps forum](https://community.fabric.microsoft.com/t5/Desktop/Azure-Maps-path-layer-route/m-p/4727221))
- **Map bottom sheets** use a few deliberate resting heights: peek = summary, mid = details, full = everything. The map behind stays interactive, and arbitrary stops "feel like sliders". ([Material bottom sheets](https://material.io/components/sheets-bottom), [Google Maps-style sheet](https://proandroiddev.com/building-a-google-maps-style-bottom-sheet-with-jetpack-compose-eccc1f3cf578), [SwiftUI sheets](https://www.createwithswift.com/exploring-interactive-bottom-sheets-in-swiftui/))

### Repos and skills
- **Borrow ideas only, no new dependencies:**
  - the MapLibre stretchable-image example;
  - UPPETITE's `MapCanvas.svelte` (tiers, blockers, hit layer);
  - [svelte-maplibre image symbols](https://svelte-maplibre.vercel.app/examples/image_symbols), MIT, for Svelte patterns;
  - mapcn's MarkerLabel (React, MIT) as a visual reference.
- **Skills:**
  - vault MapLibre skills `maplibre-cartography` and `maplibre-source-wiring`, plus `aniwhere-map-ui`;
  - the motion contract (`docs/motion/*`);
  - `web-design-guidelines` for the review pass.
  - The account's skill catalog has no map or cartography skill, so the vault skills are the source.

## The plan

### 1. Callout pins: the label *is* the pin (fixes association, the critics' #1 issue)
- **Shape:** each tier-1 place is a rounded pill with a small tail pointing straight down at its spot. It carries the rank number, the fit glyph and the figure: `1 ✓ 300 kg`, `3 ◐ 200 of 300`, `6 ? Confirm`, `11 ⊘ No match`.
- **Placement:** the pill always sits **above** its point (PerceptPPO's top position). One rule, no side-switching and no gap. A small ground dot under the tail tip marks the exact spot.
- **Drawing:** a stretchable pill image per fit state, with **two `stretchX` zones** either side of the tail, `icon-text-fit: both` and `icon-anchor: bottom`. Tier ordering uses `symbol-sort-key = rank`.
- **Tier 2 (mini-pins):** places outside the tier, or whose pill would collide, are small numbered dots (Airbnb's mini-pin) at 22 px with an 11 px numeral and a thin white halo. Hovering a mini-pin, or its list row, grows it into its full pill (Airbnb behaviour).
- **Tier size is set by rank and zoom, not by chance:**
  - phone overview: top 4;
  - desktop overview: top 6;
  - each zoom step in adds about 3 more.

  Zooming in never shows fewer labels.
- **Selected pin:** the same pill, inverted (ink fill, white text), slightly larger, with the ground dot ringed in its fit colour. On desktop the pill also carries the short name ("Kusina Verde · 300 kg"). On phones the name lives in the trip card only (the critic's call), so no separate floating name label is needed.
- **Hover:** a mini-pin grows into its pill; a pill gets an ink ring. Nothing else moves.

### 2. Origin and route
- **Origin "A":** a native symbol (disc plus a "Los Baños center" label), so every pin, mini-pin and the chip avoid it automatically. This fixes the label covering a dot or the chip.
- **Direction arrows:** removed. The route reads from the A disc to the inverted destination pin. The line keeps its trace-in animation, which shows direction once, as it is drawn.
- **Distance chip:** placed on a clear stretch of the route after one collision pass. It avoids the origin label, the destination pin and the right-hand control column. If no stretch is clear, it moves into the trip card, which already shows the same numbers.
- **Fit padding:** sized from the actual pill height (tail included) and the control column, so the destination pin never runs off the canvas.

### 3. Phone map room
- **Top:** in map view the summary card collapses to a one-line pill, "Tomatoes · 300 kg · Edit", with the List/Map toggle in the same row. That gives about 70 px more map.
- **Bottom sheet:** three deliberate heights. Peek shows the title plus one row; with a place selected, peek shows the compact trip card (fit, kg, km, View details, pager); full shows the list. Target: at least 430 px of visible map at 390×844.

### 4. Consistency
- **Saved page:** use the shared heading tokens and the standard card surface (drop the pink tint).
- **Compare ledger:** right-align kg and ₱ cells with tabular figures.
- **Desktop landing hero:** add top padding back by tightening the form, so "Find places to sell" stays above the 900 px fold.
- **Contact-to-confirm rows:** one note under the group header; each card keeps only what differs ("Ask: capacity, price").

### 5. Motion (vault contract tokens)
| Moment | Motion |
|---|---|
| First load | Pins settle top-down by rank (opacity + 4 px drop, 20 ms stagger, cap 8). Mini-pins fade in. |
| Hover | Mini-pin grows to pill (180 ms standard); pill ring 120 ms. |
| Select | Pill inverts (180 ms) → camera eases to show A and the destination (480 ms in/out) → route traces from A (520 ms) → chip fades in (180 ms). |
| Step | Old route fades (120 ms), then the same beat. |
| Zoom | The tier grows; new pills fade in through the symbol fade (180 ms). |
| Reduced motion | Final state, no movement. |

## Order of work (small commits, checks after each)
1. Callout pill images (two stretch zones, tail) and the pill layer.
2. Tiering by rank and zoom; mini-pin fallback; hover-to-expand.
3. Selected pin; drop the separate name label; native origin.
4. Remove arrows; chip collision pass; fit padding from pin metrics.
5. Phone map: one-line summary, sheet heights.
6. Consistency fixes (Saved, Compare, hero, confirm note).
7. Live-map tests:
   - every tier-1 pin sits above its own point;
   - no pin overlaps another, the origin or the chip;
   - zooming in never reduces the tier;
   - the selected destination is inside the frame;
   - reduced motion shows the final state.
8. One fresh critic round on a dedicated port, with the title guard. Owner decisions are stated up front, including **"(h) labels sit above their point as callout pins"**, so a critic cannot reverse the evidence-based placement.

## Risks
- **The tail must stay centred over the point at every pill width.** Verify the two-zone stretch at 390 and 1440 before building on it.
- **Inverted selected pin:** contrast of white text on ink is fine, but check that the fit glyph stays distinct (white glyph variants are needed).
- **Pills above points stack vertically in dense clusters.** The collision engine plus tiering handles this. Clusters 3/4/A and 9/11 are the test cases.
- **The offline SVG map** should adopt the same callout anatomy in a follow-up (same shapes, no leaders).
