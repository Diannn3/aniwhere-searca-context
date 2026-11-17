AniWhere 
is a harvest-based market discovery and decision-support platform for farmers. Instead of functioning like a traditional agricultural marketplace where farmers create listings and wait for buyers, AniWhere starts with the farmer’s actual harvest. A farmer enters their crop, quantity, location, and optionally when the harvest will be available. The platform then searches nearby selling outlets—such as trading centers, cooperatives, processors, restaurants, MSMEs, public markets, and other verified buyers—and shows which ones are realistically suitable for that harvest.
Its core feature is “Can I sell here?” AniWhere checks available information about each outlet—such as crop accepted, quantity requirements, buying schedule, quality requirements, and current buyer offers—and returns one of four understandable results: matches your harvest, accepts part of your harvest, contact to confirm, or does not match. Importantly, the platform does not treat missing information as a confirmed match, and it separates relatively stable, verified place information from time-sensitive buyer offers that have update and expiry dates.
Farmers can then compare up to three selling options using factors such as accepted quantity, unsold quantity, posted price, distance, estimated transport cost, and potential proceeds after transport. They do not need an account to browse and can contact buyers directly. In this way, AniWhere is designed less as an online marketplace and more as a market-access decision layer that helps farmers answer a practical question: “Where can I realistically sell this harvest?”
For the hackathon MVP, AniWhere is being built as a Laguna-focused web application, initially supporting tomato, eggplant, and calamansi matching while allowing directory browsing for other crops. The planned stack is Astro, Svelte, TypeScript, MapLibre GL JS, Turf, openrouteservice, and Supabase PostgreSQL/Auth. The MVP includes location-based market discovery, explainable harvest-to-buyer matching, comparison of selling options, transport estimates, buyer-offer management, Filipino and English interfaces, and direct buyer contact.
Its business model is currently free for farmers, with an initial institutional-service model for cooperatives, local government agriculture offices, and agricultural programs that need to maintain verified selling outlets, coordinate demand, and help farmers access markets. AniWhere also explicitly avoids paid placement in farmer recommendations, so results are intended to be based on suitability rather than sponsorship.
Quick Links
• GitHub: [add link]
• Live App: [add link]
• Figma: [add link]
• Supabase: [add link]
• Pitch Deck: [add link]
• Final Concept Note: [add link]
• Hackathon Guidelines: [add link]
• Master Data Sheet: [add link]


Current Status
• NextGen Agri Hackathon: Top 10 Finalist
• Concept Note: Final
• MVP: In development
• Design: In development
• Data: In development
• Pitch Deck: To be finalized


MVP Scope
• Laguna pilot
• Tomato, eggplant, and calamansi matching
• Farmer input: crop, quantity, location, optional availability date
• “Can I sell here?” states: Match / Partial / Contact to confirm / No match
• Compare up to three selling options using accepted quantity, price, distance, transport estimate, and proceeds after transport
• Direct buyer contact
• Verified place data kept separate from time-sensitive buyer offers


Tech Stack
Core Stack
• Astro — web application shell
• Svelte — interactive UI and components
• TypeScript — type-safe application logic
• Supabase PostgreSQL — places, crops, offers, and source records
• Supabase Auth — buyer and admin authentication
• MapLibre GL JS — interactive map
• Turf — straight-line distance and geospatial fallback
• openrouteservice — road distance and travel time


Architecture
Farmer / Buyer / Admin → Astro + Svelte → Matching / Map / Compare → Supabase + Routing services


External Services
• OpenStreetMap / map tiles
• Supabase
• openrouteservice


Repository
• GitHub repository: [add link]
• Deployment: [add link]
• Environment / setup notes: [add link or path]


Useful References
• Supabase Agent Skills: https://github.com/supabase/agent-skills
• MapLibre GL JS docs: https://maplibre.org/maplibre-gl-js/docs/
• Turf docs: https://turfjs.org/
• openrouteservice docs: https://openrouteservice.org/dev/#/api-docs


Design System


Brand
• Name: AniWhere
• Meaning: Ani + Anywhere
• Personality: practical, trustworthy, local, modern, farmer-first
• Tagline: [TBD]


Logo
• Primary logo: [add]
• Icon / mark: [add]
• Light version: [add]
• Dark version: [add]


Colors
Brand Palette
• Primary — Field Olive: #597928
• Secondary — Young Leaf: #91AC67
• Primary Dark — Soil Brown: #6E3511
• Background — Rice Cream: #FCECD8
• Surface — Warm Surface: #FFFDF8
• Text Primary — Field Ink: #20251E
• Data / Location — Route Blue: #4E7380


Semantic Match States
• Match: #1F6B3B
• Partial: #8A5A00
• Contact to Confirm: #185C85
• No Match: #9B2F27


Usage Rules
• Olive is the dominant AniWhere brand color; brown is a supporting soil / structural accent.
• Use Young Leaf primarily as a soft fill or secondary accent with dark text; avoid white text on it.
• Match-state colors are semantic and separate from the core brand palette.
• Every match state must use text + icon + color, never color alone.




Typography
• Display font: [TBD]
• Heading font: [TBD]
• Body font: [TBD]
• Type scale: Display / H1 / H2 / H3 / Body / Small / Label


Spacing
• 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64


Radius
• sm / md / lg / full


Match States
• Matches your harvest
• Accepts part of your harvest
• Contact to confirm
• Does not match
Each state should use text + icon + color, not color alone.


Map System
Define marker styles for trading centers, cooperatives, processors, restaurants, MSMEs, and public markets.


Core Components
• Button
• Input
• Crop selector
• Result / buyer card
• Match badge
• Map marker
• Comparison card
• Navigation


Useful References
• Google design.md: https://github.com/google-labs-code/design.md
• UI skills / create-design-md: https://github.com/ibelick/ui-skills


User Experience
Farmer Flow
Open AniWhere → Enter crop → Enter quantity → Set location → Optional availability date → Find selling options → View “Can I sell here?” → Compare → Contact buyer
Buyer Flow
Login → Open assigned outlet → Create or update buying requirement → Set crop, quantity, price, requirements, and expiry → Publish
Admin Flow
Review place → Verify source → Approve or edit → Assign buyer representative
Core Screens
• Landing / home
• Harvest form
• Results list
• Map
• Outlet / buyer details
• Compare
• Buyer dashboard
• Admin review
States & Errors
• Loading
• No results
• Location denied
• Routing unavailable
• Map unavailable
• Missing price
• Expired offer
• Partial match
• Stale information
Language & Copy
Maintain simple Filipino and English wording. Avoid technical language in farmer-facing states. Missing information should become “Contact to confirm,” not a guessed match.




Data
Data Types
• Verified Place — relatively stable outlet information
• Place Capability — crops and requirements a place is known to handle
• Buyer Offer — time-sensitive demand, quantity, price, schedule, and expiry
• Reference Price — contextual PSA / DA price data, not a guaranteed buyer quote
• Demo Data — fictional data used only for prototype demonstration and clearly labeled
Data Sources
• OpenStreetMap — location seed data
• DA / KADIWA / public sources — markets and market context
• PSA — production and historical price context
• LGU / municipal agriculture sources — local outlet information
• Buyers — current buying requirements
• Manual verification — contact and outlet validation
Database
• places
• crops
• place_crop_capabilities
• buyer_offers
• buyer_assignments
• source_records
• users
Freshness Rules
• Place: show last verified date
• Buyer offer: show updated date + expiry
• Price: always show source + timestamp/type
• Demo data: always visibly labeled DEMO
• Unknown data: never treated as a confirmed match


Useful Repositories
• DBML: https://github.com/holistics/dbml
• Open Food Network: https://github.com/openfoodfoundation/openfoodnetwork
• Teikei: https://github.com/teikei/teikei


Suggestion Bank
1.
