# Liquid Locations — State of Play
_21 August 2026. Read this first for anything Liquid Locations._

---

## The one-line version

A production-services business for Spain that was a **marketing website** and is now becoming a **software-automated production company** — one executive producer running international shoots off a structured supplier/permit/rate database instead of a coordination department.

---

## What it is

International agencies and production companies in London, Hamburg, Berlin, Düsseldorf, Stockholm and New York shoot in Spain. They hire a Spanish *productora de servicios* to physically execute: crew, kit, locations, permits, hotels, transport, catering, insurance, payroll.

Incumbents — Palma Pictures, Twenty Four Seven, Fresco Film, Nostromo, Lee Films — do this with people. Sourcing and coordination is 20–33% of the client invoice [unverified], and it is a repeatable, information-heavy workflow.

**The thesis:** capture that workflow in a database plus automation, and one experienced EP does the work of a line producer, a production manager, a coordinator and a location scout — undercutting on the production fee while paying local crew properly.

James is the EP. He is bilingual, Barcelona-based, and already works these sets as a digitech.

---

## Where it stands, honestly

| Layer | State |
|---|---|
| **Website** | Live at `callingjhphoto-cmd.github.io/liquid-locations` — single 185 KB `index.html`, GSAP, 20-location database, quote builder |
| **Business docs** | `business_plan.md`, `pricing.md`, `pitch_email.md` — written 23 Mar 2026, **predate the research** |
| **Research** | ✅ **NEW.** 81 KB Gemini Deep Research report, 21 Aug 2026, read in full |
| **Build plan** | ✅ **NEW.** `BUILD_PLAN.md` — data model, wedge, phases, stop conditions |
| **Software** | ❌ Nothing built |
| **Clients** | ❌ None. 48 London outreach drafts written, **all unsent** |
| **Entity** | ❌ No S.L. registered |
| **Locations catalogued** | 1 — Inner Flow, Barcelona |

**Last commit:** 16 Apr 2026. `index.html` has been uncommitted since 5 Aug. Today's tax fix is also uncommitted.

> **The site is live and the business is dormant.** That gap is the actual state of play.

---

## What today changed

### 1. A real research base exists

Commissioned via `GEMINI_DEEP_RESEARCH_PROMPT.md`, returned 21 Aug. Twelve workflow phases mapped stills-vs-TVC, real margin structures, statutory rate tables, permit regimes for four regions, supplier maps, a full data model, a phased build plan with falsifiable stop conditions, and ten load-bearing assumptions each marked supported or contradicted.

Everything below traces to `research/RESEARCH_gemini_2026-08-21.md`.

### 2. A live credibility bug was found and fixed

The site's Tax Incentives section pitched the Article 36.2 rebate — 30% mainland, 54% Canaries — to a client base that is **legally excluded from it**.

> Article 36.2 of Ley 27/2014 covers feature films and audiovisual fiction, animation and documentary series. **Advertising commercials (*spots publicitarios*) and stills photography are strictly excluded** — [verified — Ley 27/2014 Art. 36.2; AEAT binding rulings V1746-15, V2300-21].

Minimum qualifying spend is €1M in Spain anyway — above almost any commercial job.

**Fixed today** in `index.html`: eligibility carve-out added to the subtitle, a bordered callout in the body, and a qualifier on the table note. Verified in file. **Not yet deployed** — the live URL still shows the old copy.

### 3. The wedge was confirmed independently

Kit list → parse → RFQ fan-out → comparison matrix ranked **Rank 1 of 6** on value ÷ effort, ahead of call sheets, VAT, contracts, permits, and — last — autonomous scouting. Same conclusion reached in conversation before the research arrived.

---

## The wedge

```
Client drops unstructured PDF / email rider
        ↓
Semantic parser  →  canonical product records
        ↓
Compatibility module  →  flags missing dependencies
        ↓                 (SkyPanel X21 with no stands or distro)
Relational query  →  supplier tables + trade-discount profiles by region
        ↓
Branded RFQs email out  →  responses compile into a cost + margin matrix
```

No client IT integration. No legal liability handoff. Attacks the single biggest coordinator time sink in bidding.

**The parsing problem, named:**
- >60% of inbound riders are flattened PDFs or email body text
- riders name the head ("ARRI M90") and omit ballast cables, 63A/32A breakout distro, ballast mounts, safety bonds
- shorthand — "Titan Tubes", "Panchros", "M90", "Phase One 150" — must map to ERP product codes

**Hard constraint:** no major Spanish rental house exposes a public API. EPC, Aluzine, Cinelux, Ovide, Servicevision all quote manually from internal ERPs and export static PDFs, 12–24h turnaround. **The engine's output is an email and an inbox parser, not an API call.** Design for that from day one.

**Stop condition:** <85% zero-shot parse precision on raw PDFs → stop. Below that, verification costs more than a coordinator.

---

## The numbers that matter

### Where the model wins

| | Traditional | Automated | Saving |
|---|---|---|---|
| **Stills, Barcelona** — 2 days, 8-person team, 3 locations | €21.100 | €13.910 | **−34,1%** |
| **TVC, Andalucía** — 4 days, 40 crew, 5 locations | €226.500 | €193.800 | **−14,4%** |

The TVC saving is smaller because crew (€56.000), trucks (€28.000), catering and base camp (€22.000) are irreducible physical cost.

> **Stills is where the model wins — and stills is the market James already sells into. Lead with stills.**

### How a service company is paid

| Component | Rate |
|---|---|
| Production fee — TVC | 10–20% [verified — APCP / industry benchmark] |
| Production fee — stills | 15–25% [verified — APCP / industry benchmark] |
| Equipment sub-rental markup | 10–20%, or 20–40% trade discount retained as spread [verified] |
| Travel/logistics handling | 5–10% flat [verified] |
| Location handling | 10–15% [unverified] |
| Gross operational margin, incumbents | 18–32% [unverified] |

---

## The three things that could kill it

### 1. Falsos autónomos
On-set technicians work within the production company's *ámbito de organización y dirección*. The Labour Inspectorate **actively audits sets**. Sparks, grips, PAs and camera assistants must be on *contrato temporal* and registered in Régimen General **before call time**.

Exposure: retroactive employer SS quotas (~31,5–33%) + 20–35% surcharges, and **€3.750–12.000 fines per misclassified worker** [verified — BOE-A-2024-6846; ET Art. 1.1].

**This kills the naive "one person plus freelancers" model.** Payroll and Sistema RED alta capability is a precondition, not a feature.

### 2. Procurement onboarding
WPP, Omnicom, Publicis, IPG and Havas require **2–3 years of filed corporate balance sheets**, AEAT and Seguridad Social clearance certificates, UBO proof, signed anti-bribery/AML/sanctions compliance, GDPR guarantees, often €1–2M cyber liability, plus AdGreen carbon tracking.

A new S.L. cannot clear that gate. **Enter below procurement level** — direct with production companies and photographers who buy on relationship.

### 3. What clients actually buy
Agencies pay incumbents a premium for **working capital** (cash-flowing €500k+ productions before milestones clear), **total indemnity**, **24/7 crisis resolution** and **procurement compliance**.

Automation addresses none of those. It attacks the cost of coordination — which is the part they were never really paying for.

**So the honest positioning is not "cheaper Palma Pictures."** It is smaller stills and low-mid commercial jobs, below the procurement threshold, where a €7k saving on a €21k job decides whether the job happens at all.

---

## What the moat actually is

Not the software — generic workflow UIs and form builders are reproducible in a weekend. The research says so explicitly. Three assets:

1. **Verified supplier data** — real trade-discount structures, real performance history
2. **The permit knowledge graph** — Barcelona OEP/OGE 3–5 vs 10–15 business days, Ordenança Fiscal 3.10, 22:00 residential curfew, Ciutat Vella restrictions; Madrid €48,65 admin + €0,58/linear metre/day; Andalucía beaches needing Costas at 2–4 weeks; Canarias national-park bonds of €1.000–6.000
3. **Client trust and financial capacity**

James has (2) partially and (3) not yet. (1) is buildable.

---

## Build phases

| Phase | Months | Delivered | Stop condition |
|---|---|---|---|
| **1. RFQ wedge** | 1–3 | Kit-list parser, supplier mapping, RFQ dispatch across BCN/Madrid/Málaga, cost matrix | <85% parse precision |
| **2. Locations + permits** | 4–6 | Spatial catalogue with visual search, auto permit packages, occupancy-tax calculation | >15% of permit submissions rejected |
| **3. Full engine** | 7–9 | Brief intake → crew → call sheets → travel → cross-border billing | One EP can't run 3 concurrent productions cleanly |

---

## Immediate next actions

1. **Deploy the tax fix.** The live URL still advertises a rebate the client base can't claim. Fixed locally, uncommitted.
2. **Build the alias table, not the app.** A CSV of ~200 shorthand → canonical mappings from real riders. Zero infrastructure; it is the parser's ceiling.
3. **Test the 85% gate on real riders** before any app code.
4. **Reconcile `pricing.md`** — it lists scouts at €247–250/day against a €250–380 market band, and EP/loc-mgr at €450–500 against a €600–1.200 EP band.
5. **Don't build the location library yet.** Highest curation cost, lowest automation ROI, hardest to seed legally — every Spanish film commission directory is public-view but non-licensable.
6. **Decide the entity.** Falsos autónomos exposure and permit-mandatory public liability both need a real vehicle.
7. **The 48 unsent London drafts** are still unsent, and now partly wrong — they predate both the research and the rebate correction.

---

## Files

| Path | What |
|---|---|
| `STATE_OF_PLAY.md` | This file. Read first. |
| `BUILD_PLAN.md` | The engine plan — data model, wedge spec, phases, stop conditions, compliance |
| `ITERATION_PROMPT.md` | Prompt for pushing the idea further |
| `GEMINI_DEEP_RESEARCH_PROMPT.md` | The commissioning prompt |
| `research/RESEARCH_gemini_2026-08-21.md` | Full 81 KB report |
| `index.html` | The entire live site |
| `business_plan.md`, `pricing.md`, `pitch_email.md` | 23 Mar 2026 — predate the research, conflicts flagged in `BUILD_PLAN.md` §1.1 and §11.2 |
| `INDEX.md`, `liquid-locations-review.md`, `website_review.md` | Prior state and site reviews |

**Related:** `~/Documents/Claude/projects/fixer/` — the seam pattern this build copies (`lib/ai.ts`). `~/Documents/Claude/memory/SIDE_BUSINESS_MERGED_PLAN_2026-08-21.md` — BORME infrastructure shared with side-business option A. One scraper, two businesses.
