# Gemini Deep Research prompt — Liquid Locations, Round 2
_Commissioned 21 August 2026. Round 1 (`RESEARCH_gemini_2026-08-21.md`, 81 KB) is already read and acted on. This round exists to close what Round 1 left unverified, and to answer the go-to-market questions Round 1 did not touch._

---

## Role

You are a research analyst with combined expertise in Spanish audiovisual production services, Spanish corporate and labour law, procurement and vendor onboarding at international advertising agencies, and applied NLP for document extraction.

Your output will be used to decide whether to register a Spanish S.L. and commit 3–9 months of build time. Assume the reader already knows the industry. **Do not restate basics. Do not repeat Round 1 findings except to correct them.**

---

## Context — what is already established

A Barcelona-based executive producer (bilingual EN/ES, works as a stills digital technician on international shoots) is building **Liquid Locations**: a Spanish *productora de servicios* that executes shoots in Spain for production companies in London, Hamburg, Berlin, Düsseldorf, Stockholm and New York — with the sourcing and coordination layer automated by software rather than staffed by a coordination department.

Round 1 established, and this round should treat as settled unless you find contradicting primary sources:

1. **Art. 36.2 rebate (Ley 27/2014) excludes commercials and stills.** Confirmed by AEAT binding rulings V1746-15 and V2300-21. €1M minimum Spanish spend regardless.
2. **The wedge is kit list → parse → RFQ fan-out → cost matrix.** Ranked first of six candidate automations on value ÷ effort.
3. **No major Spanish rental house exposes a public API.** EPC, Aluzine, Cinelux, Ovide, Servicevision all quote manually from internal ERPs, 12–24h turnaround. The engine's I/O is email out, inbox parser back.
4. **Modelled savings: stills −34,1%, TVC −14,4%.** Lead with stills.
5. **Falsos autónomos is an existential risk.** On-set technicians must be on *contrato temporal* in Régimen General before call time. Fines €3.750–12.000 per misclassified worker (BOE-A-2024-6846; ET Art. 1.1).
6. **Holding-company procurement (WPP, Omnicom, Publicis, IPG, Havas) requires 2–3 years of filed balance sheets.** A new S.L. cannot clear it — so entry must be below the procurement threshold.
7. **The moat is supplier data + a permit knowledge graph + client trust**, not the software.

---

## Part 1 — Verify the numbers Round 1 could not

Round 1 returned these as **unverified**. For each, find primary or citable sources — filed accounts, sector association publications (APCP, PROFILM, Spain Film Commission, AEPA), academic or consultancy studies, published rate cards, tenders, or court/inspection rulings. **Where no source exists, say so explicitly and state what would be needed to establish it.** Do not smooth over a gap with a plausible figure.

| # | Claim to verify | Round 1 range |
|---|---|---|
| 1.1 | Sourcing + coordination as a share of the total client invoice | 20–33% |
| 1.2 | Production-management labour (LP, PM, coordinators, runners) as a share of gross budget | 8–15% |
| 1.3 | Service markup on top | 12–18% |
| 1.4 | Gross operational margin, established Spanish service companies | 18–32% |
| 1.5 | Production fee compression at €300k+ projects | toward 10–12% |
| 1.6 | Production fee sustained on €15k–40k stills jobs | up to 20–25% |
| 1.7 | Location handling fee on private-property hire | 10–15% |
| 1.8 | Barcelona Ordenança Fiscal 3.10 technical parking | €0,60–1,20/m²/day + €50–120 admin |
| 1.9 | Canarias national-park environmental security bonds | €1.000–6.000 refundable |
| 1.10 | RC Patronal (employer's liability) cover per victim | €300–600k |

**Preferred evidence:** filed cuentas anuales at the Registro Mercantil for Palma Pictures, Twenty Four Seven, Fresco Film, Nostromo, Lee Films, Garlic Films, Blur Films, or comparable — revenue, gross margin, staff count, and the trend across the last three filed years. Name the company, the year, and the figure.

---

## Part 2 — The parse gate, empirically

Round 1 set a stop condition: **<85% zero-shot parse precision on raw kit riders → stop the build.** That number was asserted, not measured.

Answer:

- **2.1** What zero-shot extraction accuracy is actually reported in published benchmarks for structured line-item extraction from flattened/scanned PDFs and free-text email bodies — invoices, bills of materials, purchase orders, technical riders? Cite benchmark names, models, and dates. Distinguish native-text PDF from scanned image.
- **2.2** How much does a domain alias/synonym table lift that accuracy in documented cases? Quantify the delta where studies exist.
- **2.3** What is the documented failure profile — is the residual error dominated by missed line items, wrong quantities, or wrong entity resolution? Which of those is recoverable by a human in seconds vs. which silently corrupts a quote?
- **2.4** Is 85% the right gate at all? Argue for a different threshold if the evidence supports one, and separate **precision** from **recall** — an engine that misses a €40 safety bond is a different business risk from one that hallucinates a €900 head.
- **2.5** Are there existing commercial products doing kit-list → RFQ in film/TV/events, anywhere in the world? Name them, their pricing, their traction, and whether they died. Include adjacent verticals — construction BOM, industrial procurement, AV/event rental (Current RMS, Rentman, Flex, HireHop, inspHire). **Which already ship a rider-parsing feature?**

---

## Part 3 — The entity decision

Round 1 said "decide the entity" without resolving it. Resolve it.

- **3.1** Compare, for this exact use case: **autónomo**, **S.L.**, and **S.L. + external payroll/gestoría**, and the option of **invoicing through an existing productora as an umbrella** while building. Cover: setup cost and time, minimum capital, ongoing accounting cost, personal liability exposure, ability to hire crew under Régimen General, credibility with a London client, and how each is treated on an agency vendor form.
- **3.2** What is the **minimum viable payroll capability**? Can a gestoría run Sistema RED altas/bajas at shoot cadence — sometimes 48h notice, sometimes 30 crew for 4 days? What does that cost per worker per production? Name real Spanish providers who serve production companies and their published or quoted pricing.
- **3.3** What insurance is **mandatory vs. commercially expected**: RC General, RC Patronal, all-risks equipment, cast/production insurance, cyber. Give Spanish market premium ranges for a company doing €200k–600k first-year turnover, with named brokers or insurers who write audiovisual risk in Spain.
- **3.4** **Working capital.** Round 1 says clients pay incumbents partly for cash-flowing productions before milestones clear. What are actual payment terms from London/German/US production companies to Spanish service companies — and what financing instruments (confirming, factoring, ICO lines, Enisa) are realistically available to a first-year S.L.? What do they cost?

---

## Part 4 — Who actually buys, and how they choose

Round 1 mapped the workflow and the compliance risk but never mapped **the buyer**. This is the biggest gap.

- **4.1** For stills and low-mid commercial jobs **below the holding-company procurement threshold** — who is the actual decision-maker? Photographer's agent? Producer at a small production company? In-house brand producer? Map the decision chain for a €15k–60k stills shoot in Spain commissioned from London, Hamburg or New York.
- **4.2** How is a Spanish service company **found** by that buyer today? Rank the real channels by observed use: Spain Film Commission and regional film office directories, personal referral from crew, Production Base / The Dots / Free The Birds-type directories, LinkedIn, Instagram, agent rosters, repeat business. Where possible cite surveys or trade reporting, not intuition.
- **4.3** What does a **first-time** Spanish service vendor have to show to win job #1 — a reel, a location library, references, a rate card, proof of insurance, a specific past credit? What disqualifies instantly?
- **4.4** **Price sensitivity.** Round 1's pitch is a −34% saving on stills. Is a 34% cheaper unknown vendor actually attractive to this buyer, or does the discount read as risk? Find evidence — procurement studies, agency-side commentary, documented switching behaviour in production services.
- **4.5** Who are the **direct competitors at this exact tier** — small Spanish service outfits and one-person fixers serving foreign stills clients in Barcelona, Madrid, Málaga, Mallorca, Canarias? Name them, their positioning, their published rates, their size. This is the real competitive set, not Palma Pictures.
- **4.6** Is there an underserved **inbound corridor** worth naming? Compare volume and growth of shoots into Spain from the UK, Germany, the Nordics, the US and the Gulf, for stills and commercials specifically. Which corridor has the most volume per existing Spanish supplier?

---

## Part 5 — The supplier data asset

The moat is claimed to be verified supplier data. Test whether it can be built.

- **5.1** How many rental houses, grip/lighting suppliers, location agencies, transport, catering, and crew agencies exist per region — Cataluña, Madrid, Andalucía, Baleares, Canarias, Valencia? Give counts with sources.
- **5.2** What **trade-discount structures** are actually offered to production companies vs. list price, and on what basis — volume, relationship, account age, prompt payment? Real ranges with sources.
- **5.3** Is any of this data **legally acquirable at scale** — film commission directories, association member lists, BORME, trade fair exhibitor lists (ISE, Cine Europe, Conecta Fiction)? Give the licence terms for each. Which explicitly forbid reuse?
- **5.4** What is the realistic **cold-start path** — how does a new service company get trade pricing before it has volume? Are there buying groups, association memberships (APCP, PROFILM, AEC), or referral structures that grant it?
- **5.5** How fast does this data **decay** — rate cards, contacts, availability? What is the maintenance burden in hours per month to keep 200 suppliers current?

---

## Part 6 — Kill the idea

Argue the strongest possible case that this business should **not** be built. Not a risk list — a genuine attempt to falsify it, using evidence.

Address at minimum:
- Whether the coordination cost being attacked is real margin or a cross-subsidy the client already refuses to pay for separately.
- Whether one EP plus software can hold three concurrent productions without a failure that ends the client relationship — find documented cases of thin-staffed service companies failing on set.
- Whether the automation advantage is durable, or whether an incumbent with 40 staff adopts the same LLM tooling in 2026–2027 and keeps every other advantage.
- Whether the correct move is instead to **sell the software to incumbents** rather than compete with them — and what that market looks like (how many Spanish service companies, what they spend on tooling, who already sells to them).
- Whether James should simply keep working as a highly-paid digitech and stop.

Then, separately: **the strongest case that it should be built**, on the same evidentiary standard. State which case the evidence actually favours and by how much.

---

## Part 7 — First 90 days, costed

A concrete plan, not a phase chart.

- Week-by-week for weeks 1–12: what gets built, what gets registered, who gets contacted, what gets tested.
- **Every line costed in euros** with a named source for the cost.
- A named falsifiable stop condition at week 4, week 8 and week 12.
- The single cheapest experiment that would produce the strongest evidence for or against the whole thesis — and what it costs.

---

## Output requirements

1. **Every factual claim carries a source.** Format: `[verified — <source, ref, date>]` or `[unverified — <what would establish it>]`. A claim with no source and no unverified tag is a failure of the brief.
2. **Never substitute a plausible figure for a missing one.** "No source found" is a valid and valuable answer.
3. **Spanish legal citations by BOE reference.** Company financials by company name + filing year.
4. Currency in euros, Spanish decimal convention (`€1.234,56`).
5. Distinguish **stills** from **TVC** throughout — they are different businesses with different margins, and the model wins on stills.
6. Where you contradict Round 1, say so explicitly and show the source that overrides it.
7. Lead the report with a **one-page verdict**: build / don't build / build a different thing, with the three pieces of evidence that decided it.
8. Length is not a virtue. Density is. Cut anything the reader already knows from the Context section above.

---

## Files this round is answering into

| Path | What |
|---|---|
| `STATE_OF_PLAY.md` | Read-first status — Round 1 conclusions, honest gaps |
| `BUILD_PLAN.md` | Data model, wedge spec, phases, compliance, all unverified tags |
| `research/RESEARCH_gemini_2026-08-21.md` | Round 1 report, 81 KB |
| `index.html` | Live site — `callingjhphoto-cmd.github.io/liquid-locations` |
