# AniWhere — SEARCA Agri-FoodEx Concept Note: Judge-Driven Revision Plan

**Date:** 18 November 2026 (Asia/Manila)
**Status:** Editorial and feature-scope plan only; the original concept note remains unchanged.
**Inputs:** User-provided five-page `AniWhere_SEARCA_AgriFood_Concept_Note.docx`; AniWhere repo README and architecture/limitations; `AniWhere_SEARCA_2026_Judge_Audit_and_Competition_Context.md`.
**Audience:** Team Ani, its faculty mentor, and anyone rewriting the application materials.
**Evidence notation:** [ORIGINAL] sourced from the five-page document; [BRIEF] supplied competition details; [RECOMMEND] our design/editorial proposal; [TO VERIFY] currently unsupported or unresolved.

## Editorial verdict

Do not turn the application into a catalog of 100 imagined AI features. Retain the existing harvest-first core and make a single, visibly useful AI intervention the differentiator: **AI converts informal farmer/buyer descriptions into reviewable structured requirements, which the existing deterministic matching engine uses to surface compatible options and unknowns**. A *small*, constraint-aware split/replan demonstration is a stretch capability if time permits, not evidence of current deployment.

**Suggested central promise:** "Make a harvest discoverable, make buyer needs understandable, and make the pre-trip decision safer." It is a proposed decision-support workflow, **not** a guaranteed sale or measured waste-reduction intervention.

**Suggested title:** **AniWhere: AI-Assisted Harvest Visibility and Pre-Trip Market Discovery**.
**Suggested short tagline:** *Turn fragmented harvest and buyer information into actionable options before the truck leaves.*

## Judge's primary objections and what the note must fix

| Objection | Current note weakness | Revision response | Evidence standard |
|---|---|---|---|
| "Isn't this another farmer-buyer directory?" | Opens with discovery and voice entry; direct differentiation is not sustained | State that directory/price boards don't establish crop-, date-, volume-, grade- and freshness-specific fit | Cite DA-AMAS, SEARCA AgriEX, and DOST-PCAARRD honestly; no claim of being first |
| "Where is the AI?" | AI mostly recognizes speech and fills a form | Lead with AI structured extraction from both *buyer needs* and *farmer harvest descriptions*, including ambiguity flags | Show before/after example, optional AI eval protocol; don't claim parser is deployed |
| "Who supplies actual demand?" | Bagsakan browser-local; fictional demo records | Explain authorized buyer/steward input, confirmation, expiry, provenance; verified pilot dependency | Separate interactive demo from operational pilot |
| "What if a buyer withdraws?" | Fit engine shows a current snapshot, not a recovery plan | Present limited scenario replanning as development goal; do not promise allocation without reliable capacity | Synthetic cancellation demonstration; objective and constraints disclosed |
| "Why does this reduce food loss?" | Problem significance might be conflated with causal product effect | Say *potential* reduction in failed trips/distress selling; propose measures for pilot | National farms are context, not target addressable users; no fake impact % |
| "How do farmers actually use it?" | Voice-first framing overclaims device availability/UX | Retain picture/tap/manual entry and assisted steward workflows as fallbacks | Test a few actual farmer tasks; label exploratory sample |
| "Are you eligible?" | Existing document lists three students and older name | Align name 'Team Ani'; verify ≥4 actual enrolled students; mentor role student-led | Matching actual application, CVs, proofs of enrollment |

## Section-by-section edit map for the original five-page document

### Cover/title + subtitle [ORIGINAL paragraphs 0–3]
- [KEEP] AniWhere name, UPLB, Laguna-first origin.
- [CHANGE] Replace "voice-first AI" as primary identity with **AI-assisted market visibility and pre-trip decisions**.
- [CHANGE] Update team name from **Walang Ani Buseng** to **Ani** only if that is the registered entry name.
- [VERIFY] Team roster includes at least four eligible students, per supplied competition requirements.

### Summary [ORIGINAL paragraphs 5–7]
- [CHANGE] First sentence: describe fragmented buyer demand, supply visibility, and time-sensitive perishable harvest decisions; show consequences without generalizing every failed sale as spoilage.
- [CHANGE] Second paragraph: concise 3-step process: `capture informal information → human-verified structured requirements → deterministic fit and pre-trip options`.
- [KEEP] Existing four outcomes and no-guarantee boundary.
- [KEEP] Honest prototype note: fictional records, same-browser buyer workspace, one farmer interview; synthetic demo tests functionality, **not** real market impact.
- [OPTIONAL] Mention split/replan only as a proposed hackathon stretch demonstration, not centerpiece of current technical readiness.

**Candidate summary opening (to refine, not to paste blindly):**
> Smallholder farmers often know what they will harvest before they know where the harvest can realistically be accepted. Buyer needs, receiving windows, grades, and available capacities are spread across personal contacts and informal messages. When these details cannot be discovered or verified before travel, farmers risk wasted trips, missed opportunities, or distress selling. AniWhere proposes a lightweight AI-assisted bridge that turns informal harvest and buying information into reviewable, searchable records and checks the fit of a specific harvest before transport.

### Background of the Problem [ORIGINAL paragraphs 9–12]
- [KEEP, QUALIFY] PSA 7.73 million farms and 0.82 ha average farm size as scale/context for fragmentation; do **not** call all 7.73m addressable users, vegetable farmers, or potential paying customers.
- [KEEP] One Laguna farmer quote with explicit `one nonrepresentative interview` label. Do not convert quote to survey finding.
- [ADD] Precisely distinguish three gaps: (1) supply not visible beyond known networks; (2) demand not standardized/updated; (3) compatibility and transport terms not easily comparable.
- [ADD] DA August 2026 early-warning / market-linkage push and targeted published studies; cite by actual title/date and working URL.
- [ADD] One paragraph that acknowledges DA-AMAS / AgriEX / other existing linkage initiatives and their overlapping work, then narrows AniWhere's contribution to **pre-trip fit, uncertainty, information capture, and potential partial allocation**.
- [CUT] Unverified broad claims about typical farmer literacy; present as design hypothesis to test.

### Proposed Solution [ORIGINAL paragraphs 14–23]
- [KEEP] Four deterministic fit states; list/map/outlet details, saved outlets, comparison, known amount-after-transport (not profit), null/unknown distinction.
- [REORGANIZE] Organize as `Existing functional prototype` and `Proposed hackathon additions`, no ambiguous implementation tense.
- [ADD] Explicit sample workflow including both buyer and farmer participation: buyer says "500 kg kamatis, Friday morning" → AI drafts fields and flags "morning cutoff unknown" → buyer confirms → farmer search checks current terms.
- [ADD] Proposed optional split/replan feature only if it can be demonstrated under bounded scenarios; do not overstuff the note.
- [FIX] "Kukunin lahat" sounds like a promise; use "Tugma sa nakatalang kondisyon" / "Posibleng tanggapin lahat—kumpirmahin muna" until actual acceptance is confirmed.

### AI Integration section [ORIGINAL paragraphs 24–28 and 2 tables]
- [REPLACE MAIN HEADLINE] "AI Integration: Market Information Interpretation and Guided Discovery".
- [REPLACE TABLE] A transparent pipeline:
  1. Typed/voice input from **farmer or buyer**; no assumed universal offline microphone service.
  2. AI extracts standardized crop, quantity/unit, date, municipality, optional grade/packaging/receiving window; returns `unknown` when ambiguous.
  3. Confirmation screen; authorized submitter checks extracted data; offers have source/update/expiry.
  4. Existing deterministic fit engine checks structured conditions and four states.
  5. Optional AI explains unresolved fields / helps prepare buyer confirmation, but cannot invent acceptance or prices.
  6. *Stretch:* mathematical allocation and scenario recompute; no LLM-invented capacity or solution.
- [KEEP] Rules-first parser as economical fallback and interactive manual forms.
- [ADD] Guardrails: no invented prices/capacity, no unconsented private-message scraping, explicit demo mode, audit trail / expiry, user confirmation, protect precision errors in dates and local-unit conversion.
- [ADD] Proposed AI evaluation with 30–50 sample utterances, field-level accuracy, critical error count, and manual form baseline; do not assert performance before testing.
- [CHECK] Repo contains a separate undeployed Gemini Live provider scaffold; don't describe it as production-ready or present mutually exclusive voice stacks as already integrated.

### Objectives [ORIGINAL paragraphs 29–34]
- [CHANGE] Replace narrowly speech-focused objectives with three measurable outcomes:
  * correctly convert informal buyer/farmer information into **reviewed** structured records;
  * improve discovery of **plausible** contacts and explain current/missing fit conditions;
  * validate feasibility of updating/rechecking changed conditions without false commitments.
- [ADD METRICS] Structured extraction critical-field accuracy; time required to produce a reviewable buying requirement vs manual entry; deterministic allocation validity and correctly unplaced kg; follow-up qualified inquiry rate (pilot only).
- [KEEP] Accessibility objective, but distinguish aspirational `under two minutes` from a measured result.

### Target Market / Beneficiaries [ORIGINAL paragraphs 35–37]
- [NARROW] Primary: smallholder perishable vegetable growers in one Laguna pilot locality; secondary: participating receiving points / cooperatives who publish requirements. Don't imply general Philippine adoption.
- [ADD] Crucial data steward role (cooperative/LGU agricultural office / market operator), but treat partner identification as future work unless authorized.

### Value Proposition [ORIGINAL paragraphs 38–40 and 1 table]
- [CHANGE] Articulate specific value for **each side**:
  * farmer: harvest-specific choices, known/unknown terms, fewer uninformed trips as a hypothesis;
  * buyer: easy expression of procurement needs via voice/text; fewer mismatched inquiries as hypothesis;
  * steward: reviewable extracted records and stale-info management.
- [ADD] Explain why this is not general e-commerce, price prediction, or checkout; preserve no-sale-guarantee.

### Business Model [ORIGINAL paragraph 42]
- [KEEP] Free farmer access; institutional workflow/support subscription as a *hypothesis*.
- [CHANGE] Define who would actually update/verify demand and why they'd do so; routine updating cost is probably a larger business-model risk than inference cost.
- [ADD] Explicit alternatives: partnerships/extension stewardship, paid onboarding/service fees, not paid placement modifying matches.

### Regional Relevance and Scalability [ORIGINAL paragraphs 44–45]
- [KEEP] Local data stewards, standard contracts for crop/unit/date/validity.
- [CUT] Sweeping "just translate dictionaries to Bahasa/Thai/Vietnamese" equivalence; standards, user trust, languages, institutions and enforcement are not plug-and-play.
- [ADD] Replication hypothesis: one municipality and 1–2 crops first; then replicate with locally verified records and translators/partners.

### Team [ORIGINAL paragraph 47]
- [UPDATE] 4–8 enrolled UPLB students if verified; add agribusiness member and specific responsibilities only if actually confirmed. If not yet confirmed, treat this as an immediate eligibility blocker, not an editorial problem.
- [KEEP] Existing prototype provenance (UPLB NextGen Agri finalist), technical competency, mentor role; no fabricated deployment metrics.
- [ADD] Describe interdisciplinary complementarity: applied mathematics / software / data, agri business/on-the-ground workflows, usability research, partner outreach.

### References [ORIGINAL paragraphs 48–53]
- [AUDIT] Each "Source" hyperlink must lead to a valid cited page, and statistics should match releases and dates.
- [ADD] AgriEX and DOST-PCAARRD comparison (as context, not proof that AniWhere is unique), plus local postharvest supply chain empirical research.
- [KEEP] Local interview clearly distinguished from published evidence; include methodology note if available.

## Coherent scope: what to promise versus what to build

**Already documented as implemented:** harvest form, discovery/map, outlet detail, saved, three-outlet comparison, deterministic four-state fit, local Bagsakan editor, fictional data, fallback help. The production schema is a scaffold only; do not present a live buyer database or deployed AI.

**Primary *proposed* AI addition — essential:** both-sided buyer/harvest interpretation into strict structured drafts with missing/ambiguous markers and explicit submitter review.

**Smallest demo enhancement — feasible:** display a buyer note, extracted draft, user approval, a revised matching result and a visible "contact to confirm" unknown; this alone is defensible.

**Optional engineering-plus-demo stretch:** pre-trip allocation across 2–3 compatible offers, buyer cancellation event, deterministic recompute with unplaced remainder, and source/validity explanation. Label as mathematical planning / optimization rather than claiming the LLM solved allocation.

**Defer:** AniCouncil roleplaying agents; digital twin; autonomous negotiation; photo-based quality guarantees; live price forecasts; processing studio; raw data scraping; nationwide rollout; payment/booking as if already operational.

## Suggested single demo scenario (3 minutes, time only illustrative; final pitch limit unknown)

1. Show a farmer with **300 kg tomato** ready Friday; current directory offers don't reveal capacity/terms.
2. Buyer note: "Kailangan namin 180kg kamatis sa Friday, morning lang, size medium"; AI extracts **180 kg, Friday (exact date resolves from explicit reference context), medium size, 'morning' = time unknown**.
3. Buyer checks and approves; sample offer appears with a **DEMO / FICTIONAL** label.
4. Farmer searches 300 kg; outlet A has 180 kg capacity; outlet B 120 kg; the app shows a feasible split subject to known requirements and marks missing grade/time as conditions to confirm.
5. Judges click *Buyer A unavailable*. Deterministic scenario recompute marks A invalid, allocates to known eligible backups if possible and leaves any remainder explicitly unplaced.
6. End by explaining the real pilot prerequisites: participating cooperative/buyer, dated verified offers, farmer tests, and tracking inquiry/delivery outcomes. No claim of measured food-loss reduction.

## Minimal evidence and acceptance checks

- **Accuracy:** 30–50 labeled synthetic Taglish messages + negative/ambiguous cases; compare extracted crop/quantity/date/requirements against expected; record errors and correction rate.
- **Baseline:** measure a small set of manual-form vs AI-review tasks. Avoid statistical significance claims with a small sample.
- **Rules:** test unknown capacity/price, expiry, duplicate offers, grade incompatibility, partial acceptance, cancelled offer, date mismatch.
- **Math:** ensure assigned kg cannot exceed available kg or capacity; `assigned + unplaced = available`; a "contact to confirm" offer never treated as confirmed.
- **Disclosure:** all synthetic figures carry visual demo labels; comparison outputs aren't promises or profit figures.
- **Qualitative validation:** ask farmers what detail they need before travel and buyers which fields they would actually maintain; report interview count and limitations.

## Application-day editorial priority order

1. **Eligibility / team consistency (P0):** actual 4th member, enrollment, application name, CV pack; contact organizer about conflicting schedule if necessary.
2. **Summary + problem (P0):** rewrite to scale, fragmentation, pre-trip risks, evidence and limitations.
3. **AI pipeline (P0):** meaningful two-sided information interpretation with human approval; label proposed vs existing.
4. **Demonstration plan + objectives (P0):** one viable scenario, small test metrics, no performance inventions.
5. **Existing solutions + competitive positioning (P1):** candid comparison to DA-AMAS / AgriEX, narrow differentiator.
6. **Business model + stewardship / pilot (P1):** honest institutional payer hypothesis and future-data maintenance.
7. **Final production check (P1):** links, dates, local terms, safe match labels, accessible layout, consistent roster.

## Concrete pass/fail audit before filing

- [ ] At least four actual enrolled students and all names consistent.
- [ ] Competition dates carefully qualified; deadline highlighted and organizer clarifications requested as needed.
- [ ] No implementation claim for undeployed AI, backend or live buyer data.
- [ ] At least one concrete, inspectable example of AI improving structured information rather than just chat.
- [ ] A conventional-rules baseline is acknowledged; no false claim that arithmetic is generative AI.
- [ ] Source evidence has publication dates, links, and no false extrapolation.
- [ ] Existing competitors acknowledged; exact niche explained.
- [ ] Demo scenario reproducible with synthetic data and failure handling.
- [ ] Pilot scope is one locality / one-to-two crops and a real proposed update owner.
- [ ] All pages proofed for readability; no confirmed page count or pitch time invented.

## Key sources / references

- Original uploaded concept note: `AniWhere_SEARCA_AgriFood_Concept_Note.docx`, 5 pages, 18 Nov 2026 source attachment.
- Uploaded judge audit and competition brief: https://drive.google.com/file/d/1hzpVzqpvubYKFUrqaSlvYBXqRpjYep66/view?usp=drivesdk
- PSA 2022 Census of Agriculture and Fisheries final results: https://psa.gov.ph/ (verify exact citation against original source hyperlink)
- DA, "DA sharpens early-warning system to curb vegetable gluts" (24 Aug 2026): https://www.da.gov.ph/da-sharpens-early-warning-system-to-curb-vegetable-gluts/
- DA Agribusiness and Marketing Assistance: https://www.da.gov.ph/services/agribusiness-and-marketing-assistance/
- ACIAR vegetable chain research: search indexed institutional publication and quote precisely before publication.
- User-supplied competition PDF: https://iad.intaff.ku.ac.th/attach/w158/f20261105035726_Ebq6t58f8f.pdf
- Competition form: https://forms.gle/oy5wa3ZiuBKRd5Rs5
- Organizer: eigd@searca.org

