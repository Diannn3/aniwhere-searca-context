# Third-Party Notices & Dependency Audit

**Project:** AniWhere: Harvest-Based Market Discovery for Farmers  
**Hackathon:** UPLB TTBDO NextGen Agri Hackathon 2026  
**Audited:** 18 September 2026

---

## 1. Core Runtime & Build Dependencies

| Dependency | Version | License | Justification & Scope |
| :--- | :--- | :--- | :--- |
| **Astro** | `^5.x` / `v7 preview` | MIT | Static site generator providing zero-JS static HTML shell, fast SSG builds, and file-based routing. |
| **Svelte** | `^5.x` | MIT | Lightweight client islands for reactive state (HarvestForm, DiscoveryExperience, OutletDetail, Comparison, BuyerWorkspace) with fine-grained runes. |
| **@astrojs/svelte** | `^7.x` | MIT | Official integration bridge enabling Svelte 5 components inside Astro layouts. |
| **Tailwind CSS** | `^4.x` | MIT | Utility-first styling framework with Laguna design token CSS variables. |
| **@tailwindcss/vite** | `^4.x` | MIT | Vite plugin integration for Tailwind v4. |
| **TypeScript** | `^5.x` | Apache-2.0 | Type safety across pure domain models, matching rules, and state adapters. |
| **Vitest** | `^3.x` | MIT | Blazing-fast unit testing framework for deterministic matching and arithmetic suites. |

---

## 2. Typography & Open-Source Assets

| Asset | Source / Author | License | Usage |
| :--- | :--- | :--- | :--- |
| **Fraunces** (via `@fontsource-variable/fraunces`) | Undercase Type (Phaedra Charles, Flavia Zimbardi) | SIL Open Font License 1.1 | Display typography for headings and outlet titles (`--font-display`). |
| **Atkinson Hyperlegible Next** (via `@fontsource-variable/atkinson-hyperlegible-next`) | Braille Institute of America | SIL Open Font License 1.1 | Body, controls and labels (`--font-body`). |
| **Source Sans 3** (via `@fontsource-variable/source-sans-3`) | Paul D. Hunt / Adobe | SIL Open Font License 1.1 | Digits only (unmodified file, `unicode-range: U+0030-0039`) so figures have a plain zero. |
| **Source Serif 4** | Frank Grießhammer / Adobe | SIL Open Font License 1.1 | Installed dependency; not currently imported by the app. |
| **Hero Landscape** | Public Domain / CC0 | Unsplash / CC0 | Atmospheric background imagery depicting Laguna rice fields and Mt. Makiling. |

---

## 3. Architecture Invariant

No proprietary, closed-source, or telemetry-gathering libraries are included. The frontend operates with 0 external tracking scripts, 0 third-party cookie dependencies, and 0 paid API quotas.
