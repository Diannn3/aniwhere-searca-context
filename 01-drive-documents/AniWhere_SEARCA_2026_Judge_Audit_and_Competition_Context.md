# AniWhere — SEARCA Agri-FoodEx 2026: Competition Context, Adversarial Judge Audit, and Feature Strategy

**Date:** 2026-11-18 (Asia/Manila)  
**Purpose:** Reusable research and decision brief for Team Ani and a local coding/research agent.  
**Status:** Concept evaluation and proposed features; no new features implemented by this report.  
**Evaluation frame:** Application screening and potential hackathon/final pitching; not an official SEARCA judging report.  
**Source notation:** `[USER BRIEF]` means supplied by the team; `[VERIFIED PUBLIC]` means corroborated through public sources; `[REPO/CONCEPT]` means the team's documented prototype/concept; `[ANALYST]` denotes an independent assessment or recommendation.

## Executive verdict

**Provisional judge assessment: 6.2/10 — promising platform foundation, insufficiently differentiated AI and field evidence.** This is a subjective, unweighted diagnostic, **not** the competition's official scoring scale or weight allocation. With a focused, working SIGNAL → SPLIT → RECOVER demonstration, a careful defense against existing competitors, and honest demonstration metrics, the concept could become materially more compelling. An 8/10-caliber presentation is an aspiration, not a predicted result.

**Core argument:** The important failure is not merely that farmers lack a map. Farmers and buyers operate with fragmented information about harvest quantities, receiving requirements, availability dates, grades, minimums, and changes. Existing market-linkage projects already exist. AniWhere needs to contribute a narrow, distinctive **pre-trip decision layer** that (1) turns informal messages into reviewable data, (2) calculates feasible options given actual constraints, and (3) revises those options when circumstances change. AI performs constrained interpretation and explanation; rules/optimization own agricultural compatibility and allocation.

### Five uncomfortable questions

1. **Who supplies the buyer-side facts?** No AI can infer reliable current capacity or purchase intent from an absent data source.
2. **Why not use AgriEX or DOST-PCAARRD's existing initiatives?** The concept must position itself as an interoperability-ready decision/verification tool, not claim that digital linkage is a worldwide novelty.
3. **What is actually AI?** The original voice-entry feature is accessible form filling. Splitting kilograms across buyers is operations research, not inherently AI. The AI's value must be demonstrated against a non-AI baseline.
4. **What happens when a buyer cancels, a grade fails, or a route is unaffordable?** Good marketplace discovery alone is not a feasible selling plan.
5. **What real impact can the team claim?** At present: a functional demo, a deterministic engine, and limited farmer discovery. Not verified sales, income gains, farmer adoption, avoided spoilage, or validated climate benefits.

---

# Part I. Competition context

## Organizer, purpose, and stage — [USER BRIEF]

- **Competition:** SEARCA Agri-FoodEx: AI for Agri-Food Systems — Youth Innovation Challenge.
- **Organizer:** Southeast Asian Regional Center for Graduate Study and Research in Agriculture (SEARCA), Emerging Innovation for Growth Department (EIGD).
- **Purpose:** practical, responsible, scalable AI and emerging-technology solutions for Southeast Asian agriculture and food systems.
- **Format:** application screening; pre-hackathon learning and mentoring; concept refinement; onsite hackathon and final pitching.
- **WUR:** published call describes collaboration with Wageningen University & Research experts/resources. Potential separate Food Systems Innovation Challenge referrals are not automatic.
- **Eligibility:** teams of **4–8 enrolled** undergraduate or graduate students from qualifying University Consortium institutions; interdisciplinarity encouraged; student-led; faculty advisers/technical mentors encouraged; **minimum TRL 2**, concept formulated; a finished production application not required.
- **Institutional endorsement:** shortlisted teams must obtain it for finals.

## Dates — [USER BRIEF, partially public-corroborated]

| Milestone | Date supplied | Verification status |
|---|---|---|
| Application deadline | **18 Nov 2026** | Corroborated by SEARCA public call and Kasetsart University announcement |
| Screening | 18–25 Nov 2026 | User-provided call summary; original PDF was inaccessible in this research session |
| Shortlisted ten teams / onboarding | 25 Nov 2026 | User-provided call summary |
| Bootcamp, mentoring, refinement | 25 Nov–5 Dec 2026 | User-provided call summary |
| In-person hackathon / final pitch | 9–10 Dec 2026, SEARCA HQ, Los Baños | User-provided call summary; **unresolved** because application-form copy reportedly mentions different dates |
| Potential support/mentoring | December 2026 onward | Subject to organizer rules |

**Important unresolved contradiction:** Team's copied application form says learning activities on **2–13 November** and onsite participation on **17–18 November**, inconsistent with the above December schedule. Neither reading should be treated as organizer-confirmed without written confirmation. As of **18 November 2026**, this is urgent. Contact **eigd@searca.org** for the operative itinerary and endorsement deadlines. Do not present these dates as reconciled.

## Support — [USER BRIEF]

- PHP **75,000 travel support per team** for top five teams, subject to applicable rules.
- PHP **300,000 total seed funding for five teams**, subject to allocation; no official equal split established by the provided call summary. A Kasetsart announcement states PHP 60,000 for each of five teams, but that is a secondary summary and should not override organizer rules without confirmation.
- Mentorship, learning, potential incubation/network support.

## Priority areas — [USER BRIEF]

1. Climate-resilient and sustainable agriculture.
2. Food and nutrition security.
3. Biodiversity and ecosystem stewardship.
4. Circular agriculture and food loss/waste.
5. Inclusive agri-food value chains.
6. Digital agriculture and smart farming.
7. Rural livelihoods and agripreneurship.
8. Other credible emerging agri-food challenges.

**AniWhere's authentic strongest fit:** inclusive agri-food value chains; digital agriculture; rural livelihoods. **Secondary and conditional:** food loss/waste (by enabling earlier and more feasible decisions); climate relevance (through avoidable journeys and potentially reduced waste, not a measured emissions reduction). Do **not** claim demonstrated climate impact.

## Assessment areas — [USER BRIEF]

**Screening:** significance of problem; SEARCA priority alignment; concept and implementation clarity; team capabilities; collaboration.

**Final pitch:** food-system impact and climate relevance; feasibility/work plan; progress and feedback integration; business model/scalability/sustainability; delivery, visuals, and Q&A.

**No numerical weights were verified.** Any scores in this report are **analyst-only** heuristic ratings.

## Application fields and files — [USER BRIEF]

- Team/member details, problem statement, solution, primary technology, beneficiaries, expected impact, development stage, team capability, attainable development/validation during program, participation commitments, originality and privacy/documentation consent.
- One file each, maximum 10 MB: concept note; combined member profiles/CVs; proof of enrollment/affiliation; optional supporting material.
- No confirmed required concept-note page count, pitch length, or slide limit.

## Immediate administrative risks

1. **Roster:** Existing five-page AniWhere concept note lists **three students**, while this competition requires **4–8 enrolled members**. User reports exploring adding an agribusiness student, but current registration status is not confirmed here. Ensure final official roster actually meets eligibility.
2. **Name:** Old note uses team **Walang Ani Buseng**; competition brief specifies **Ani**. Align every application field, cover page, CV pack, and supporting file.
3. **Claims:** Rephrase features as implemented versus planned. The existing frontend and schema scaffold are not a live farmer-buyer network.
4. **Timing:** Application deadline is **today, 18 November 2026** in local context; do not postpone submission for speculative feature development.
5. **Rules:** The linked official PDF and Google Form could not be opened through the browsing environment in this pass. Treat the detailed team-supplied copy as the working brief until organizer confirmation.

## Public competition links

- Provided official-call copy: https://iad.intaff.ku.ac.th/attach/w158/f20261105035726_Ebq6t58f8f.pdf
- Provided university announcement: https://iad.intaff.ku.ac.th/portal/iad/fund_view.php?aWQlM0Q1Mzc=
- Application: https://forms.gle/oy5wa3ZiuBKRd5Rs5
- Kasetsart University's independently indexed announcement: https://src.ku.ac.th/th/index2.php?nid=12960&pg=disnews
- SEARCA official social call (deadline independently corroborated): https://ph.linkedin.com/company/searca
- Organizer: eigd@searca.org

---

# Part II. What AniWhere currently is — [REPO/CONCEPT]

**Core premise:** Laguna-first pre-transaction **harvest-based discovery**, not checkout, procurement guarantee, or an operating marketplace.

**Basic journey:** Farmer provides crop, kilograms, municipality, ready date, and optional variety/grade/packaging. Deterministic engine evaluates sample outlets and returns: **Matches / Accepts part / Contact to confirm / Does not match**. Users browse a map, outlet details, saved outlets, and comparison of up to three options. A Bagsakan workspace can edit local buying needs. Demo records are explicitly fictional.

**Documented engineering foundation:** Astro/Svelte/TypeScript/Tailwind frontend; offline-first map fallback; reviewed static route artifacts; explicit evidence freshness and known-versus-unknown semantics; comparison with transport cost only when available; local FAQ; proposed/partially scaffolded live conversational AI tools; declarative Supabase market-data schema with untested undeployed production operations. Working browser-local prototype does not equal an authenticated production buyer network. The repo README reports 11 fictional outlets across seven demo crops. See https://github.com/Diannn3/aniwhere (private to authorized users).

**Primary limitation:** The system can evaluate compatibility *given provided data*, but cannot know absent, stale, or unverified buyer demand. A model must not invent prices, purchase commitments, capacity, crop grades, drive times, or real-world acceptance.

**Evidence to date:** Prototype and one farmer interview according to team concept note; no verified aggregate field measurements demonstrating impact. Farmer quote must remain attributed to one participant rather than a representative survey.

---

# Part III. Evidence on problem significance and prior solutions

## Size and nature of the problem

- PSA 2022 CAF **final** results released in July 2026: approximately **7.73 million farms** and **0.82 ha average farm size**. These are *farm counts/average area*, **not** AniWhere serviceable-market size, potential users, or adoption forecasts. Source: https://psa.gov.ph/content/2022-census-agriculture-and-fisheries-agricultural-farm-and-parcel-characteristics-final
- DA-AMAS 24 August 2026: early-warning improvements sought to connect growers with buyers earlier, prevent vegetable gluts, spoilage, and distress selling. This establishes policy relevance **not** a causal effect estimate for AniWhere. Source: https://www.da.gov.ph/da-sharpens-early-warning-system-to-curb-vegetable-gluts/
- DA documented a case of 2.5 tons of discarded Chinese cabbage under market/weather constraints; illustrates possible consequence, not a nationwide typical loss rate. Source: https://www.da.gov.ph/da-seeks-ways-to-cut-vegetable-losses-amid-weather-woes/
- A 2025 Philippine-focused peer-reviewed paper, *Training, credit, and infrastructure for improving market access among small-scale producers in the Philippines*, points to infrastructure, credit, and information asymmetry; market access is not solved by information alone. Source: https://www.sciencedirect.com/science/article/abs/pii/S0306919225000570
- World Bank AgriConnect overview emphasizes buyers, information, finance, infrastructure, and farmer organizations as complementary. Source: https://www.worldbank.org/ext/en/agriconnect/faq
- A 2026 Ethiopian mixed-methods study of 385 vegetable growers found that indigenous communication channels and digital ICT channels were used complementarily. This is relevant design evidence **from Ethiopia**, not proof of the same adoption behavior in Laguna. Source: https://consensus.app/papers/agago-endris-synergetic-usage-of-indigenous-communication/w:0d50c60b-b6e5-4766-acef-8981f80d4a8a/
- A 2025 Ugandan study of verified postharvest-information distribution identifies coordination, low digital literacy, and institutional dissemination constraints. Again, a cross-context reference rather than a Philippine effect size. Source: https://consensus.app/papers/kiwelu-ngulube-empowering-rural-smallholder-farmers-access-to/w:1bc2404e-7677-454c-b2fa-41502945d0c7/

## Hard competitive critique

| Alternative or initiative | Documented capability | Honest implication for AniWhere |
|---|---|---|
| SEARCA + AppGeese **AgriEX**, Liliw, Laguna | Farmer market access, buyer communication, orders, market-demand visibility via cooperative coordinator | Most threatening local precedent; a pitch claiming "first digital farm-to-market bridge" would be weak |
| DOST-PCAARRD **Agri-Aqua Business Hub** (AABH) | Institutional buyers, supply-chain coordination, expected harvest data and market linkage | AniWhere should complement existing programs and explore a workflow/plugin/steward model |
| DA **Agribusiness and Marketing Assistance Service (AMAS)** | Public agricultural marketing information and institutional linkage | Institutional extension and stewardship matter; government is not absent from the problem |
| **Mayani** | Commercial agricultural market/input/credit platform | Basic buyer discovery and selling access are not novel on their own |
| DOST-PCAARRD **Green Chain+** (2026) | Smart transport and BAPTC supply-chain digitization work | Broad logistics and transport optimizers are not unique to AniWhere |

Sources:
- https://www.searca.org/press/searca-digital-agri-project-reshapes-farming-liliw
- https://www.searca.org/news/liliw-farmers-reimagine-agriculture-searca-pilot-project-digital-agriculture
- https://ispweb.pcaarrd.dost.gov.ph/weather-disruptions-reshape-vegetable-flows-and-prices-from-farm-to-market/
- https://newport.pcaarrd.dost.gov.ph/index.php/quick-information-dispatch-qid-articles/dost-pcaarrd-agri-aqua-business-hub-builds-a-market-oriented-ube-supply-partnership-in-famy-laguna
- https://www.da.gov.ph/da-sharpens-early-warning-system-to-curb-vegetable-gluts/
- https://mayani.ph/
- https://pcaarrd.dost.gov.ph/index.php/quick-information-dispatch-qid-articles/green-chain-to-enable-smart-transport-and-delivery-of-vegetables-for-benguet-province

**Differentiation that could survive questioning:** A low-friction, evidence-labelled **pre-trip decision layer** on top of farmer and buyer records, specifically capable of interpreting informal requirements, preserving unknowns, reconciling partial harvests across multiple compatible outlets, and recovering from updates/cancellations without hiding infeasibility. Compare against existing systems empirically in a future pilot, not through claims of worldwide novelty.

---

# Part IV. Skeptical hackathon scoring (unofficial)

**Provisional 6.2/10.** A subjective diagnostic; not computed from organizer-published weights and not a prediction of shortlisting.

| Dimension | Analyst grade | Reason |
|---|---:|---|
| Problem relevance | 8.5/10 | Clearly serious, local evidence and institutional demand |
| SEARCA alignment | 9.0/10 | Inclusive value chains, digital ag, farmer livelihood; conditional waste relevance |
| Differentiation | 4.0/10 | AgriEX, AABH, and other linkage initiatives already overlap |
| Meaningful AI | 4.0/10 | Proposed voice parser reduces form friction but weak AI decision contribution |
| Demo feasibility | 7.5/10 | Existing frontend supports compelling synthetic scenarios |
| Implementation feasibility | 6.5/10 | New AI/data flows possible, but real integrations and reliability need work |
| Evidence and impact case | 5.5/10 | Good public problem context, very limited product-specific evidence |
| Business sustainability | 4.5/10 | Proposed LGU/cooperative subscription unvalidated; steward maintenance costs unknown |

**Strengths:** real prototype; correct null/freshness semantics; farmer-first UX; interdisciplinary potential; location near SEARCA/UPLB ecosystem; thoughtful avoidance of fabricated prices; feasibility of controlled demos.

**Weak assumptions:** farmers will abandon existing contacts; buyer demand will appear without a provider; AI can produce fresh market information from informal sources without permission; all 'matches' can be converted into trips/sales; farmer use alone sustains a two-sided system; an institutional buyer will pay for this; no existing program covers the same ground.

**Do not call theoretical prevented spoilage or saved pesos a measured benefit.** Use sample-only counterfactuals labeled illustrative, and future metrics labeled planned evaluation.

---

# Part V. Adversarial feature review

Ratings below are **analyst judgments**, not official weights; compare relative tradeoffs, not decimal precision.

| Feature | Judge rating | AI or conventional software? | Keep / simplify / remove |
|---|---:|---|---|
| AI Buyer + Harvest Information Interpreter | 8.8 | AI extracts messy Taglish text into typed draft, with provenance and human verification | **KEEP core** |
| Constraint-aware Harvest Splitter | 8.6 | Deterministic integer/linear optimization; AI only interprets constraints/explains outputs | **KEEP core**, no fake AI claim |
| Mission Control | 8.5 as demo | Preloaded scenario perturbations invoke real decision engine | **KEEP as demo shell**, not a product |
| Buyer record freshness/contradiction flagging | 8.3 | AI compares free-text updates; deterministic time policy | Keep secondary guardrail |
| Last-Kilo Matcher | 7.8 | Cooperative aggregation + simple constraint solving | Optional future pilot; requires actual farmers/consent |
| Buyer Spec Overlay | 6.6 | Vision may explain visible characteristics, not certify grades/safety | Narrow to reference/education |
| Taglish voice input | 6.4 | Speech-to-text + extraction; accessibility | Keep as input mode, not headline |
| Surplus-to-Product Studio | 4.8 | LLM brainstorming; hard food-safety/economics | Defer |
| AniCouncil agents | 4.1 | Multiple agents may perform role-play without real authority/data | Remove from MVP |
| Barangay Digital Twin | 3.7 | Synthetic simulation lacking calibration | Remove branding and scope from MVP |

## Feature 1 — SIGNAL: AI-assisted information intake

**Problem:** Buyers communicate purchasing needs via calls, notes, text or photos. A farmer and potential buyer use different units and language; incomplete requirements do not become discoverable structured data without manual effort.

**Demo contract:** Submit an unstructured, fictional buyer note: “Kailangan namin mga 180 kilos na kamatis, biyernes ng umaga, hindi masyadong hinog, tawag muna sa presyo.” AI returns a **draft**, e.g. `crop=tomato`, `quantity≈180 kg` with approximate flag, `date=Friday` only after resolving relative date with Manila timezone, `receiving_window=morning` but no invented hour, `maturity_requirement=unstructured/clarify`, `price=null`, `needs_confirmation=true`. Show original text line, extracted field, confidence or uncertainty *reason*, and buyer approval; only approved records enter the demo's authoritative data store.

**AI-added value:** semantic extraction from varied Taglish and underspecified phrases; synonym resolution; ambiguous-unit/date detection. Plain rules can handle well-structured forms and must be available as baseline/fallback.

**Failure test:** “Tatlong kaing” must not become an exact kilogram count without a locally agreed conversion and user confirmation. “Huwebes” must not silently resolve to a past date. A price absent from the note must remain unknown. A mere keyword mention of a crop must not imply current purchase intent.

**Technology:** model structured JSON schema (with Zod or equivalent), deterministic validation, canonical crop dictionaries, provenance metadata, approval action. Gemini structured-output docs: https://ai.google.dev/gemini-api/docs/structured-output?lang=rest . For evaluation, use https://github.com/promptfoo/promptfoo and its JSON-schema eval guide: https://github.com/promptfoo/promptfoo/blob/main/site/docs/guides/evaluate-json.md .

## Feature 2 — SPLIT: constraint-aware partial harvest allocation

**Problem:** Multiple buyers may accept different amounts, grades, days, and volumes. A single MATCH result does not answer where the complete harvest could go or what remains without a buyer.

**Decision:** Given available lots and known compatible outlets, show one **feasible allocation** or explicitly say no full allocation exists. The objective might prioritize quantity assigned, then the farmer's entered hauling costs; don't secretly optimize invented profitability. The algorithm must respect crop/grade/date, min/max buyer quantity, committed kilograms, and offer availability. Preserve known-vs-unknown states.

**Illustrative allocation:** 300 kg tomatoes, 0 kg previously committed for this scenario; Buyer A verified demo need 180 kg, Buyer B demo need 120 kg, backups C 70 kg and D 50 kg, with grade/time compatibility. If A and B qualify, allocated total = 300 kg, remainder = 0. If A cancels and C/D are the only eligible backups, B+C+D = 240 kg, remainder = 60 kg **unplaced**; don't manufacture another buyer. (All values synthetic for demo only.)

**AI-added value:** extracting natural-language restrictions and verbalizing a deterministic plan; no claim that the optimizer is an LLM. For small demos, a transparent exact deterministic assignment solver may suffice. Google OR-Tools offers linear assignment, packing, routing and capacity-constrained examples: https://developers.google.com/optimization/examples .

**Failure tests:** buyer date mismatch; unit kg vs kaing; grade requirement absent; minimum acceptance > allocated amount; one buyer duplicated across records; buyer cancellation; all outlets incompatible; unknown hauling cost; stale price. Output must remain feasible and explain unknowns.

## Feature 3 — RECOVER: scenario-based update and replanning

**Problem:** Buying needs can change, and perishable harvest plans may become obsolete before loading. Good pre-trip decisions need adaptation, not static lists.

**Demo mechanism:** Judges click a *sample scenario injection*, e.g. buyer cancels; remaining available quantity changes; one outlet's grade terms change; arrival window closes. The platform invalidates relevant offers; recomputes fit/allocation; visually displays **before versus after**, the displaced kilograms, and required confirmations.

**What makes this legitimate:** real state transitions and algorithms must execute; no prerecorded animation pretending to replan. Mark injected data and replan as synthetic. Document how a real buyer/steward update would later enter the same system.

**AI role:** summarize the consequences in clear Filipino/English; identify exactly which recorded fact changed and which action remains unconfirmed. AI **does not** decide buyer acceptance or generate replacement offers.

**Risk:** If all feasible backups are also fictional, judges will know the outcome is staged. Make scenario uncertainty explicit and invite them to select an unexpected cancellation/quantity.

## Feature 4 — evidence/uncertainty auditor (valuable supporting differentiator)

**Purpose:** When an old buyer record conflicts with a new message, AI creates an edit proposal with side-by-side quotes and null-safe changes. Human reviewer approves; deterministic freshness threshold hides/labels expired offers. Do not turn absence into a negative match; do not invent a buyer's current demand or assign a numerical reliability score without calibration.

**Why valuable:** Makes the system less fragile as data volume grows and makes AI's work operationally useful to cooperative or LGU stewards. Less stage drama, more defensible sustainability story.

---

# Part VI. Smallest coherent feature set and scope control

## Proposed MVP — SIGNAL + SPLIT + RECOVER

**What is built / proposed:** Existing AniWhere UI and rule-based fit engine remain. Add a *single* AI structured extraction route with sample notes and an approval step; a small deterministic multi-outlet allocator that reuses fit results; and two scenario buttons that change synthetic state and trigger recomputation. Local fallback should keep a stored reviewed example if live inference is unavailable, clearly labeled **precomputed fallback**.

**What NOT to build for this demo:** production buyer authentication, live on-farm sensors, real-time price predictor, autonomous multi-agent council, digital twin, credit products, food-processing recommendation engine, vision-grade certification, general-purpose buyer social network, or a real logistics marketplace.

## Technical architecture

```text
FARMER typed/voice input                BUYER free-text / sample bulletin
          |                                           |
  Rules + optional AI parse                LLM structured extraction
          |                                           |
  Farmer confirmation                      Buyer/steward confirmation
          |                                           |
  Typed HarvestQuery               Approved BuyerOffer + source metadata
          \                                           /
            ------ Existing deterministic fit ------
                              |
                 Constraint-aware allocator
                              |
               UI: assigned / partial / unknown
                              |
               Perturbation: cancelled offer
                              |
                   Recompute + AI explain
```

**Trust boundaries:** LLM is an interpreter/explainer, not source of market truth. Existing `CONTACT_TO_CONFIRM` must remain distinct from `NO_MATCH`. Price and capacity remain `null` when unknown. An outlet accepting a crop is not a purchase commitment. Farmer consent should gate location and buyer information sharing. Synthetic records must have an unmistakable demo label.

## Suggested data fields beyond current schema

- `harvest_lot_id`, `quantity_kg`, `committed_kg`, `available_kg`, optional grade/variety/packaging.
- `buyer_offer_id`, `max_accepted_kg`, `min_accepted_kg`, `requirements_json`, `valid_from`, `valid_until`, `receiving_window`, `status`.
- `raw_input_source`, `raw_text_hash`, `extracted_fields`, `field_unknowns`, `reviewer_id`, `reviewed_at`, `data_mode`.
- `allocation_run_id`, `scenario_id`, `assigned_kg_by_offer`, `unplaced_kg`, `objective`, `constraints_explanation`, `input_snapshot_hash`.
- `event_id`, `event_type`, `affected_offer_id`, `effective_at`, `before_snapshot`, `after_snapshot` for reproducible demo event logs.

No need to deploy all those tables for competition demo: typed local fixtures and deterministic state may be faster; use existing production schema scaffold later.

---

# Part VII. Demo storyboard (about 3 minutes if the actual pitch format permits; pitch length not confirmed)

**Scene 1 — Problem / before (20–30 sec):** One farmer has 300 kg tomatoes due Friday. A web directory lists outlet names but cannot answer who needs the crop, whether they accept the quantity, or whether terms are still valid. Explain that this is a synthetic illustration of an important real problem, not a real trial.

**Scene 2 — SIGNAL (40–50 sec):** Introduce a realistic Taglish buyer note and make the model parse it into a structured *draft*. Deliberately leave price and exact hours unknown; approve the note. The UI immediately has a new searchable buyer offer. Judges see why AI helps capture fragmented information.

**Scene 3 — SPLIT (40–50 sec):** Search the farmer's harvest. Existing four-state fit engine checks crop/date/terms. Allocator distributes among Buyer A (180 kg) and Buyer B (120 kg); shows 300 assigned, zero unplaced. Explain that mathematical optimization, not a language-model guess, produced the allocation.

**Scene 4 — RECOVER (40–50 sec):** Judge chooses a cancellation of Buyer A. System recomputes using eligible backups B (120), C (70), D (50); 240 placed, 60 unplaced. No promise of sale; surface contact-to-confirm actions. Before/after quantity movement is visibly shown.

**Scene 5 — Reality and measurement (20–30 sec):** State what needs to happen next: real participating buyer/cooperative, verification workflow, and farmer usability tests; measure extraction accuracy and completion of qualified introductions. Close with a narrow action plan, not an unsupported income claim.

**Adversarial moment to volunteer:** Show how the system handles an unsupported phrase or missing capacity by saying **Contact to confirm** rather than inventing a number. This may be more persuasive than flawless happy-path AI.

## Evaluation protocol to support a hackathon pitch

- Build a labeled benchmark of **30–50 synthetic Taglish/Filipino/English sample messages** with expected values, deliberate uncertainty, local units, crop names, and dates. Report counts actually tested, exact-field accuracy, critical-field error rate, and unresolved rates. Don't present made-up improvement percentages.
- Include a form-entry/manual baseline: how long does a participant need to convert the note to a buying record without AI? Compare speed and corrections over a small set of users, with caution about sample size.
- Run **10+ deterministic allocation test cases**: normal full fit, partial, incompatible, rejected grade, expired/withdrawn offer, duplicated outlet, unknown price, min quantity, and date mismatch. All accepted allocations must satisfy constraints.
- Validate demo replan responsiveness by running real state transitions, checking that total `allocated_kg + unplaced_kg = available_kg` and that no buyer capacity is exceeded.
- Use one or two actual farmers/receiving operators for qualitative feedback **if available**, but do not turn a hackathon sample into claimed impact.
- Present **future-pilot outcome metrics:** verified offers refreshed, qualified introductions, farmer contact success, actual accepted kg, denied-trip reasons, sample farmer time to discover a viable buyer. Distinguish pilot target from observed result.

## Small pilot proposal, not demo prerequisite

- Geography: one Laguna municipality, one to two crop types (e.g., kamatis/talong).
- Data stewardship: one participating cooperative, buyers, or agricultural office; defined update owner and offer expiry protocol.
- Test participants: exploratory, not statistically powered, e.g. 10–15 farmers and 5–8 receiving points if recruitment possible.
- Tasks: post and verify actual dated buying requirements, search for compatible harvests, perform pre-trip confirmation, record resulting contact/delivery outcomes.
- Privacy: consent for personal messages and voice; no unauthorized scraping of private chats; minimize exact farm location disclosure; keep sample records separate from production.
- Business model hypothesis: free to farmers; potential paid institutional/steward workspace with onboarding, record maintenance, and aggregate anonymized reporting. Test willingness to pay rather than assuming LGUs will subscribe.

---

# Part VIII. Judge's adversarial Q&A

**Q: Isn't this just AgriEX with ChatGPT added?**  
A: AgriEX and other market-linkage projects are important predecessors. AniWhere is proposed as a pre-trip **compatibility, information-repair, and allocation** tool: it structures informal buyer terms, preserves missing information, and plans partial quantities under explicit constraints. We are not claiming the world's first marketplace or a validated better alternative. A pilot must compare both approaches.

**Q: Why is AI necessary?**  
A: AI interprets varied natural-language buying conditions into reviewable structured drafts and explains unresolved details. The ordinary software baseline is manual form entry + fixed search. We will show a benchmark that quantifies extraction accuracy and corrective burden. Compatibility and allocation remain deterministic.

**Q: What if the buyer data are fake?**  
A: Today's entries are clearly fictional for an interactive prototype. The demonstration validates **workflow and algorithm behavior**, not market coverage or real transactions. The pilot needs approved buyer inputs, expiry, stewardship, and contact outcomes.

**Q: Why don't you guarantee a sale?**  
A: A digital platform cannot guarantee buyer intent. We distinguish **compatible**, **partial**, **unknown**, and **incompatible** records. Contact and confirmation remain essential; the objective is better-informed decisions before transport.

**Q: How does this reduce food waste?**  
A: Earlier visibility and partial-load alternatives could plausibly reduce unsuccessful trips and unplaced harvests, but we have not measured reduced waste. The immediate proof is a functioning pre-trip planning workflow; waste impact is a hypothesis to evaluate with real delivery outcomes.

**Q: What is climate relevance?**  
A: Potentially fewer avoidable trips and less perishable food loss. No verified carbon or climate-benefit estimate exists. A future pilot can track avoided/repeated trips and actual spoilage if feasible.

**Q: Why do farmers need a new app instead of calling a trader?**  
A: Many will continue calling trusted traders. AniWhere should assist farmer groups/stewards in digitizing those existing relationships and make additional verified options visible, not demand exclusive platform adoption. Assisted onboarding and optional voice are accessibility strategies.

**Q: Who pays to keep data current?**  
A: A stewardship workflow with cooperative/LGU/operator participation is a critical future requirement. AI may reduce transcription and discrepancy-checking costs but cannot replace accountable updates. The institutional payer hypothesis remains unvalidated.

**Q: How scalable across SEA?**  
A: The *data contracts* (crop, quantity, origin, date, requirements, provenance) can be adapted to other crops, languages and countries. Adoption, legal rules, data partnerships and unit conversions require local validation. Not one-click pan-ASEAN expansion.

**Q: Your team is only three people, yes?**  
A: The old concept note had three student members. Eligibility requires 4–8; the final application must include an actual fourth enrolled member and consistent documents. Never pretend eligibility is resolved when it isn't.

**Q: What did you achieve during the bootcamp?**  
A: Show an honest git-diff/task log, benchmark table, tested scenarios, and mentor-feedback revisions; do not retroactively claim an experiment that did not happen.

---

# Part IX. Research and engineering skills/resources to use

## Installed skills located and inspected in this session

| Skill | Where | Practical use for AniWhere |
|---|---|---|
| Data — `market-sizing` | `skills://plugins/data/market-sizing/skill.md` | Separate 7.73m national farm count from addressable Laguna pilot; build bounded TAM/SAM/SOM assumptions; no inflated market claim |
| Data — `validate-data` | `skills://plugins/data/validate-data/skill.md` | Adversarial claim audit: numeric validity, representative versus anecdotal evidence, source freshness, denominator, misleading visual claims |
| Data — `design-kpis` | `skills://plugins/data/design-kpis/skill.md` | Define product KPIs (valid offer conversion, time to viable match, confidence errors) and leakage/false-match guardrails |
| Data — `product-business-analysis` | `skills://plugins/data/product-business-analysis/skill.md` | Compare and select features using actual evidence and capacity constraints |
| Vercel — `ai-sdk` | `skills://plugins/vercel/ai-sdk/skill.md` | Typed extraction and model integration; structured output; can be applied to Astro backend/serverless endpoint |
| Supabase — `supabase` | `skills://plugins/supabase/supabase/skill.md` | Future verified buyer/offer database, invitation roles, RLS, expiry, audit trail; do not confuse scaffold with deployed database |

## External workflows and implementation references

- **Superpowers / brainstorming, writing-plans, verification-before-completion:** https://github.com/obra/superpowers . Use to force a small scope, testable contracts, and proof before declaring a feature done.
- **Promptfoo eval skill and JSON schema tests:** https://github.com/promptfoo/promptfoo/blob/main/plugins/promptfoo/skills/promptfoo-evals/SKILL.md and https://github.com/promptfoo/promptfoo/blob/main/site/docs/guides/evaluate-json.md . Use for Taglish edge cases, date ambiguity, empty fields, hallucinated price detection, and repeatable CI checks.
- **Google OR-Tools examples:** https://developers.google.com/optimization/examples and https://github.com/google/or-tools . Use for split allocations and capacity/route constraints, not for interpreting language.
- **Gemini API structured outputs:** https://ai.google.dev/gemini-api/docs/structured-output?lang=rest . Use constrained output to prevent malformed extraction, while remembering JSON conformance does **not** guarantee factual correctness.
- **GSMA AgriTech UX Guidebook:** https://www.gsma.com/solutions-and-impact/connectivity-for-good/mobile-for-development/gsma_resources/agritech-ux-design-guidebook/ . Use for low-digital-literacy flow design, assisted onboarding, progressive disclosure and field usability tests.
- **MDN Web Speech recognition:** https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition . Speech availability varies; never promise all phones can do offline Filipino speech recognition.
- **Google AI tool calling:** https://ai.google.dev/gemini-api/docs/tools . Model can request typed functions, but authoritative engine must validate permissions and parameters.

**Recommended workflow:** Brainstorm only SIGNAL/SPLIT/RECOVER → write a one-page interaction specification → create synthetic test fixtures and expected outputs → implement extraction behind a strict schema → enforce deterministic allocation constraints → build two crisis scenarios → execute automated evaluation and UI regression checks → record honest evidence for pitch.

---

# Part X. Prioritized actions

## Do for application deadline, 18 Nov 2026

1. Verify and finalize **4–8-member roster** and institutional eligibility; use **Team Ani** consistently; complete required uploads.
2. Submit a narrower solution: **AI-assisted information normalization + constraint-aware harvest discovery**. Explain SIGNAL/SPLIT/RECOVER as a **proposed development-and-demo plan** if not yet implemented.
3. Clarify schedule conflict with organizer but do not assume one set of dates is true.
4. Replace broad novelty/impact claims with the exact problem, official sources, prototype state, and measurable pilot hypotheses.

## During possible bootcamp, depending on confirmed organizer dates

- Convert buyer notes to typed draft fields with human approval; test difficult Taglish.
- Implement robust partial allocation and unplaced-kg accounting.
- Add cancellation and receiving-window scenarios with real replan.
- Prepare evidence logs and failures, not only polished animations.
- Request feedback from a farmer, buyer, and one technical reviewer if feasible; document revisions.

## Before final pitch, if shortlisted

- Tell a **one-harvest** story with three concrete screens: visibility, allocation, disruption response.
- Pre-empt AgriEX and AABH in one comparative slide.
- Distinguish **AI extraction**, **mathematical allocation**, **human confirmation** and **future pilot** explicitly.
- Bring a fallback offline demo and known sample data; label both truthfully.
- Defend one paying stakeholder hypothesis and a credible maintenance owner.

---

# Part XI. Recommended pitch copy

> **Smallholder farmers often make time-sensitive selling decisions without a clear view of who can accept their harvest, in what quantity, on which date, and under what conditions.** Existing buyer contacts and digital linkage initiatives help, but fragmented and changing market information still makes a specific harvest hard to evaluate before transport.
>
> **AniWhere is an AI-assisted pre-trip harvest decision layer.** It turns informal farmer and buyer descriptions into structured, human-reviewed market information; checks real compatibility rules; and proposes feasible allocations across compatible outlets. When a buying need changes, AniWhere recalculates the options and openly shows what remains unplaced or uncertain.
>
> Our current prototype demonstrates harvest-based discovery and transparent match states with synthetic data. During the program, we propose to demonstrate AI information extraction, constrained allocation, and disruption recovery. A future Laguna pilot with participating farmers and receiving points will test whether these capabilities improve timely market discovery and reduce avoidable selling uncertainty.

## Three critical questions that could still change the recommendation

1. Has Team Ani finalized **at least four actually enrolled members** and an agribusiness/cooperative operations contributor who can validate buyer terminology?
2. Is the intended central story **single-farmer pre-trip planning** or **cooperative aggregation**? Both are valuable; attempting both equally may dilute a short demo. Recommendation here assumes **single-farmer pre-trip planning**.
3. Can you demonstrate **field-level AI extraction accuracy** with honest benchmark examples, and explain what happens when the model is uncertain? If not, a rules-based input workflow plus mathematical allocation may be more trustworthy than a theatrical LLM feature.

---

# Verification notes and bibliography

**Research completed:** reviewed team-supplied competition packet; referenced current conversation's five-page concept note and previously inspected private repo documentation; independent web searches of official/primary Philippine sources, existing SEARCA/DOST initiatives, tools and skills; academic abstract searches and paper record fetches from Consensus. The original Kasetsart PDF URL, university `fund_view` link, and Google Form URL produced access errors when opened, so the exact official call PDF could not be independently re-read or visually confirmed in this session. Do not upgrade user-provided detailed schedule/criteria to independently verified fact on the basis of secondary announcements.

**Most important sources:**

1. PSA final 2022 CAF (July 2026): https://psa.gov.ph/content/2022-census-agriculture-and-fisheries-agricultural-farm-and-parcel-characteristics-final
2. DA-AMAS early warning (24 Aug 2026): https://www.da.gov.ph/da-sharpens-early-warning-system-to-curb-vegetable-gluts/
3. SEARCA AgriEX pilot: https://www.searca.org/press/searca-digital-agri-project-reshapes-farming-liliw
4. DOST-PCAARRD AABH digital coordination: https://ispweb.pcaarrd.dost.gov.ph/weather-disruptions-reshape-vegetable-flows-and-prices-from-farm-to-market/
5. DOST-PCAARRD Laguna ube supply partnership (Nov 2026): https://newport.pcaarrd.dost.gov.ph/index.php/quick-information-dispatch-qid-articles/dost-pcaarrd-agri-aqua-business-hub-builds-a-market-oriented-ube-supply-partnership-in-famy-laguna
6. DA actual weather/market-triggered cabbage losses: https://www.da.gov.ph/da-seeks-ways-to-cut-vegetable-losses-amid-weather-woes/
7. World Bank agricultural market access context: https://www.worldbank.org/ext/en/agriconnect/faq
8. Philippines market-access literature: https://www.sciencedirect.com/science/article/abs/pii/S0306919225000570
9. 2026 farmer use of traditional+digital market information (Ethiopia): https://consensus.app/papers/agago-endris-synergetic-usage-of-indigenous-communication/w:0d50c60b-b6e5-4766-acef-8981f80d4a8a/
10. 2025 postharvest information access (Uganda): https://consensus.app/papers/kiwelu-ngulube-empowering-rural-smallholder-farmers-access-to/w:1bc2404e-7677-454c-b2fa-41502945d0c7/
11. GSMA AgriTech UX: https://www.gsma.com/solutions-and-impact/connectivity-for-good/mobile-for-development/gsma_resources/agritech-ux-design-guidebook/
12. Structured output docs: https://ai.google.dev/gemini-api/docs/structured-output?lang=rest
13. Google OR-Tools: https://developers.google.com/optimization/examples
14. Promptfoo evals: https://github.com/promptfoo/promptfoo/blob/main/plugins/promptfoo/skills/promptfoo-evals/SKILL.md
15. University announcement: https://src.ku.ac.th/th/index2.php?nid=12960&pg=disnews

**Bottom line:** Win judges' confidence through **transparent decisions** rather than invented intelligence. The most credible change is not making AniWhere a larger app; it is making one constrained harvest-to-market decision noticeably better, testable, and defensible.

