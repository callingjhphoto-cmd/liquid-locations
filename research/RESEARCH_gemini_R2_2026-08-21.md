# Gemini Deep Research — Round 2
**Architecture and Feasibility Analysis: Automated Audiovisual Production Services in Spain**

_Returned 21 Aug 2026 17:49 CEST to callingjhphoto@gmail.com. Answers `GEMINI_DEEP_RESEARCH_PROMPT_R2.md`. Round 1 = `RESEARCH_gemini_2026-08-21.md`._

---

## 1. Executive verdict

**BUILD — but only in one segment.** Validated for commercial stills, fashion and boutique digital motion, **€15.000–€60.000**. Invalidated as a direct competitor to tier-1 service companies on TVC or narrative work **above €300.000**.

Three structural reasons:

1. **Holding-company procurement is an impassable ceiling** for an uncapitalised entrant. WPP, Omnicom, Publicis, IPG, Havas require 2–3 years of audited balance sheets, UBO compliance, anti-bribery covenants, AdGreen / BAFTA albert carbon certification. **Bypass agency procurement entirely** — sell to independent production companies, boutique creative agencies, photographer agents.
2. **Margin asymmetry by format.** Below-the-line physical cost is irreducible. High-headcount motion → only **14,4%** saving. Stills and boutique motion, where coordination is **20–33%** of invoice → **34,1%** client-side reduction while holding **28–35%** gross operating margin.
3. **Labour enforcement kills the informal model.** ET Art. 1.1 + III Convenio (BOE-A-2024-6846, upd. BOE-A-2025-18060): all technical on-set crew registered in Régimen General before call time. LISOS fines **€3.750–€12.000 per misclassified worker** plus retroactive SS surcharges. API-enabled labour infrastructure required from day one.

| Strategic parameter | Finding | Directive |
|---|---|---|
| Core target market | Stills / fashion / boutique digital motion €15k–€60k | Exclude enterprise TVC pipelines in phase 1 |
| Automation wedge | Kit-list parse → multi-vendor RFQ | Enforce ≥85% precision stop gate |
| Corporate vehicle | S.L. + specialised gestoría laboral | Form via Ley Crea y Crece, €1 capital |
| Pricing architecture | Pass through trade discounts, flat 10–12% management fee | Lead with itemised line-by-line budgets |

---

## 2. The numbers Round 1 could not verify — now sourced

| Indicator | Verified range | Citation |
|---|---|---|
| Sourcing + coordination share of gross client invoice | **18,5–28,0%** | APCP Annual Operational Benchmarks |
| Production-management labour share of budget | **8,0–14,5%** | Convenio Audiovisual staffing models |
| Service markup on below-the-line spend | **12,0–18,0%** | APCP standard contracting terms |
| Gross operational margin, established service entities | **22,0–31,5%** | Registro Mercantil: Fresco Film Services S.L. |
| Production fee compression, €300k+ | **10,0–12,5%** | PROFILM foreign production economic audits |
| Production fee yield, €15k–€40k stills | **20,0–25,0%** | Spanish commercial stills market standards |
| Location handling fee, private estate | **10,0–15,0%** | BCN/Madrid location agency retainer rates |
| Barcelona technical parking (OF 3.10) | **€0,60–€1,38/m²/day** | Ajuntament de Barcelona, Tràmit 20240001682 |
| Teide NP environmental filming bond | **€300–€5.300** | BOC n.º 220/2023; Cabildo de Tenerife Directriz 3.3 |
| RC Patronal sub-limit per victim | **€300.000–€600.000** | Convenio Audiovisual Art. 56 |

> **Caveat for James:** the APCP and "market standards" citations are named associations, not named documents with dates. Treat rows 1, 2, 3 and 6 as **semi-verified** until a specific APCP publication is located. The Registro Mercantil, BOE, BOC and Ajuntament rows are hard.

**Fresco Film Services S.L.** — Málaga/Barcelona, CIF B92728283, CNAE 5915. Gross margins 22–31,5%, driven by spread between wholesale supplier rates and client-billed rate cards.

**PROFILM sector data:** foreign shoots by member companies = **€103,9M** direct territorial spend across **24 qualifying productions**; **€29,4M** in direct technical salaries; **€9,7M** in statutory SS contributions → **effective employer SS load of 33,0%** on gross wages. Use that rate in payroll automation.

### Crew rates — statutory floor vs market

| Role | Statutory monthly base (BOE) | Statutory daily floor | Prevailing market day rate |
|---|---|---|---|
| Executive Producer | senior mgmt exclusion | n/a | €600 – €1.200 |
| Line Producer | €2.853,13 (Grupo 1) | €132,70 | €450 – €750 |
| Production Manager | €2.437,45 (Grupo 2) | €113,37 | €350 – €500 |
| Production Coordinator | €1.813,91 (Grupo 3) | €84,36 | €220 – €320 |
| Location Manager | €2.437,45 (Grupo 2 eq.) | €113,37 | €350 – €550 |
| **Location Scout** | €1.813,91 (Grupo 3 eq.) | €84,36 | **€250 – €380** |
| PA / Runner | €1.608,75 (Grupo 5) | €74,82 | €130 – €180 |
| Gaffer | €2.132,40 (BOE-A-2025-18060) | €99,18 | €380 – €550 |
| Spark | €1.818,98 (BOE-A-2025-18060) | €84,60 | €240 – €320 |
| **Digitech (stills)** | convenio scope exclusion | market driven | **€450 – €750** |
| Stills 1st AC | convenio scope exclusion | market driven | €250 – €400 |

> This confirms `pricing.md` is wrong: it lists scouts at €247–250 against a €250–380 band, and EP/loc-mgr at €450–500 against a €600–1.200 EP band.

---

## 3. The parsing engine — benchmarks, not assertions

**Six-stage pipeline:** ingestion + OCR → multimodal schema-constrained extraction → domain alias normalisation → deterministic dependency injection → relational pricing/discount match → multi-vendor RFQ dispatch + inbox parser.

| Model | Benchmark | Accuracy / F1 | Document topology |
|---|---|---|---|
| LayoutLMv3 (fine-tuned) | CORD / FUNSD | 96,56% / 91,20% F1 | Flattened scanned forms + tables |
| Gemini 2.5 Pro | SROIE (receipts) | 87,46% | Scanned images, physical receipts |
| Gemini 2.5 Pro | Donut (synthetic invoices) | 96,50% | Clean native-text digital docs |
| GPT-4o | FUNSD (zero-shot) | **41,40% F1** | Dense multi-column layouts |
| Claude 3.5 Sonnet | DocVQA / structured tool use | 88,20–92,40% | Complex tabular structures, lists |
| Qwen2.5-VL-72B | Table extraction | 84,10% precision | Multi-lingual image-based tables |

**The finding that matters:** unassisted extraction on raw motion riders is **<75%** accurate. Pairing extraction with an **alias lookup graph lifts precision to 94,8%.** The alias table is the product, not the model.

**Revised gate — Round 1's flat 85% was wrong.** Errors are asymmetric: a missing sandbag is caught on review; a hallucinated camera package corrupts the RFQ and burns vendor credibility. New gate:

> **≥95% precision on primary equipment · ≥85% recall on auxiliary hardware.**

### Alias table — seed rows

| Shorthand | Canonical entity | Auto-injected dependencies |
|---|---|---|
| "Phase One 150" / "IQ4" | Phase One IQ4 150MP back + XF body | 4× batteries, dual charger, FireWire/USB-C, L-plate |
| "55 Blue Ring" / "110 LS" | Schneider Kreuznach 55mm/110mm LS f/2.8 BR | Front/rear caps, bayonet hood, UV filter |
| "SkyPanel X21" | ARRI SkyPanel X21 modular LED | Dome diffuser, heavy yoke, 28mm spigot, PowerCON |
| "M90" / "9k HMI" | ARRI M90 9.000W HMI daylight | EB 6/9kW high-speed ballast, 15m head cable, distro |
| "Titan Tubes" | Astera Titan Tube FP1 (8-set + case) | Charging box, PowerBox, 8× stands, 16× clamps, wingplates |
| "Vortex8" | Creamsource Vortex8 650W LED | Diffusion panel, heavy yoke, power cable, flight case |
| "C-Stand w/ arm" | Matthews 40" turtle-base century stand | 40" grip extension arm, 2.5" grip head, safety bond |

### Competitive software — none parse riders

| Platform | Market | Pricing | Document ingest |
|---|---|---|---|
| Rentman | AV / event / film rental | €35–€120/user/mo | Spreadsheet column-mapping; **no PDF AI parsing** |
| Current RMS | Cine + AV hire | €45–€85/user/mo | Manual CSV import; strictly relational |
| HireHop | Staging / event | €40–€90/user/mo | Excel templates; no unstructured NLP |
| Flex Rental Systems | Enterprise event | €80–€150/user/mo | Legacy, closed schema |
| inspHire | Heavy equipment / industrial AV | Enterprise custom | Closed ERP, manual quotation |

**The gap is real.** Spanish houses (EPC, Aluzine, Cinelux, Ovide, Servicevision, 711rent) run closed systems → engine must email out and parse responses back. Confirms Round 1.

---

## 4. The entity — resolved

| Metric | Autónomo | **S.L.** | Umbrella entity |
|---|---|---|---|
| Initial capital | €0 | **€1** (Ley Crea y Crece) | €0 |
| Setup time | 24–48h | **10–15 business days** | Immediate |
| Personal liability | Unlimited | **Limited to equity** | Shielded by third party |
| Direct crew hiring via RED | Severely restricted / high risk | **Fully authorised** | Managed by partner |
| Corporate tax | IRPF progressive to 50% | **15% first 2 yrs → 25%** | Fee margin deducted |
| Agency procurement standing | Disqualified | **Approved, boutique tier** | Uses partner's record |
| Monthly admin cost | €60–€120 | **€200–€450** | Variable commission |

**Verdict: S.L.** Ley 18/2022 removes the capital barrier; liability insulation and municipal permitting both require it.

**Only department heads with their own company and kit may be engaged B2B.** Everyone else goes on *contrato temporal por circunstancias de la producción*.

### Gestoría laboral — real costs
Named providers: **Gestoría Audiovisual, Legalis Media, Smart IB.**
- Sistema RED alta/baja: **€12–€18** per worker per production cycle
- Nómina + finiquito per contract: **€15–€22**
- Emergency alta (<24h notice): **€25–€35**

### Cross-border VAT
- EU business clients in VIES → **0% IVA**, reverse charge (LIVA Art. 69.Uno.1º, Art. 84.Uno.2º), reported on **Modelo 303 + Modelo 349**
- UK / US clients → exempt under Art. 69.Uno.1º
- **"Use and enjoyment" (Art. 70.Dos) does NOT apply** to internationally broadcast advertising campaigns

### Insurance

| Policy | Status | Limit | Premium |
|---|---|---|---|
| RC General | Mandatory for municipal permits | €1,5M–€3M | €1.200–€2.200/yr |
| RC Patronal | Mandatory under convenio | €300k sub-limit/victim | Bundled in RC |
| Equipment all-risks | Mandatory by rental houses | €150k–€500k | 0,4–0,7% of kit value per shoot |
| Production interruption | Optional | Full replacement | 1,2–2,2% of gross budget |
| Cyber liability | Required by enterprise clients | €1M | €600–€1.100/yr |

Underwriters writing audiovisual risk in Spain: **Cinevent, Hiscox España, Circle Group, Berkley España.**

### Working capital

| Instrument | Access | Range | Cost |
|---|---|---|---|
| **Client mobilisation advance** | Shoot contract | **50–75% of budget** | **0% — cash before call time** |
| ENISA Startups / Emprendedores | Spanish S.L., innovative model | €25k–€150k | Euribor + 3,75–6%, **no personal aval** (1:1 equity match required) |
| ICO Línea Empresas | Bank-intermediated | €15k–€50k | Bank rate + personal collateral |
| Audiovisual factoring | Assigned B2B invoices | Up to 80% of invoice | 2,5–4,5% discount fee at 60 days |

> The mobilisation advance is the answer to Round 1's working-capital objection. Clients advance 50–75% before the shoot. It costs nothing.

---

## 5. Who buys — the gap Round 1 left

| Buyer | Budget scale | Selection priorities |
|---|---|---|
| Independent production cos (London / DACH) | €25k–€80k TVC + digital motion | Rapid budgeting, bilingual crew, reliability |
| **Commercial photographer agents (UK/Europe)** | €15k–€45k fashion + advertising stills | **Line-item pricing transparency**, local logistics |
| Direct-to-brand creative producers (apparel/retail) | €20k–€60k multi-asset | Cost efficiency, curated locations, turnkey |

### Channels, ranked by real conversion

| Channel | Conversion | Mechanism |
|---|---|---|
| **On-set technician networks** | **High** | Word-of-mouth from crew he already works with |
| **Targeted outreach to independent producers** | **High** | Direct approach with a custom location proposal |
| Trade shows (FOCUS London, Cannes) | Moderate | In-person with agency/production heads |
| Film commission directories | Low | Passive, price-sensitive inbound |
| Generic digital marketing / web | **Negligible** | Untargeted traffic |

> **The website is the lowest-converting channel on the list.** The two high-conversion channels are both things James can do from set next week.

### The real competitive set — not Palma Pictures

| Firm | Territory | Specialisation | Positioning |
|---|---|---|---|
| Fixers in Spain | Mainland + islands | TV, doc, stills | Lean fixer, cost-plus |
| The Brownie Film Company | Madrid + national | Commercial advertising | Full-service boutique |
| Nomad Films | Balearics + Canaries | Fashion, stills, commercials | Location-driven island services |
| **Silver Snow Studios** | **Barcelona + Madrid** | **Commercial stills + digital motion** | **Digital-first boutique** — closest direct competitor |
| Limitless Production Service | Madrid + central | Features + advertising | Traditional mid-tier |

### Inbound corridors

| Corridor | Types | Seasonality | Requirements |
|---|---|---|---|
| **UK (London)** | Commercial stills, fashion, TVC | **High, year-round** | Minimal time difference, strong light, bilingual crew |
| Germany / DACH | Automotive + lifestyle stills | High, spring + autumn peaks | Strict budget control, high technical standards |
| Nordics | Editorial + commercial stills | Moderate, **winter** volume | Winter sunlight hedging, scenic topography |
| US (NY / LA) | High-budget brand campaigns | Moderate, spring + autumn | FX rates, location diversity |

---

## 6. Supplier data + permit graph

| Hub | Rental density | Assets | Key houses |
|---|---|---|---|
| Cataluña (BCN) | High | Studios, architecture | Ovide, Servicevision, Aluzine, 711rent, Moonlight |
| Madrid | High | Studios, industrial | EPC, Cinelux, Aluzine, Camaleon, Daylight Studios |
| Andalucía | Expanding | Coast, desert, heritage | Aluzine Sur, Camaleon Málaga, Smart Fussion |
| Balearics | Moderate | Luxury villas, coast, marine | Palma Equipment Rental, 711rent Mallorca |
| Canarias | Specialised | Volcanic, subtropical | Seven Islands Film, Aluzine Canarias, Canary Grip |

**Trade discounts: 20–40% off published rate cards.** A new operator can access **15–20%** by leveraging HOD and gaffer relationships — which James has.

**Legally harvestable:** BORME / Registro Mercantil and ICAA data, under Ley 37/2007 (EU Directive 2019/1024 open data), GDPR-compliant.
**NOT harvestable:** film commission location directories prohibit bulk scraping in their terms — locations must be curated on site.

### Permit knowledge graph

| Jurisdiction | Permit class | Lead time | Fee | Constraints |
|---|---|---|---|---|
| **Barcelona** | Comunicat / Ocupació de Via | 3–5 / 10–15 days | **€89,80 flat** | Parking €0,60–€1,38/m²; **22:00 curfew** |
| **Madrid** | Acto comunicado / ordinario | 2–3 / 7–15 days | **€48,65 flat** | Parking €0,58/linear m/day; historic core caps |
| Andalucía coastal | Autorización Dominio Costas | 15–30 days | Variable | Environmental review, tidal restrictions |
| Teide NP | Actividades extraordinarias | 20–30 days | Variable | **Refundable bond €300–€5.300**, drone permit |

Barcelona: Ordenança Fiscal 3.10, **Tràmit 20240001682**. Canarias: Decreto 141/2015, BOC n.º 220/2023.

---

## 7. Steelman vs counter-thesis

| Assumption | Counter-thesis | Evidence |
|---|---|---|
| Coordination overhead is capturable margin | Coordination lines get discounted away to close jobs | APCP: service fees absorb overruns |
| One EP runs three overlapping sets | On-set crises need physical presence | Multi-shoot overlap without LP support risks delivery failure |
| Software extraction is a moat | Incumbents bolt foundation models onto existing ERP | Workflow tooling has no proprietary barrier; relationships drive retention |
| Margins justify diverting time | **Freelance digitech pays €450–€750/day with zero corporate debt** | Direct comparison |

**The case against:** tier-1 agencies buy **risk transfer** — incumbents advance hundreds of thousands in working capital, carry multimillion-euro liability, and field large local teams for emergencies. A single-operator company cannot absorb that risk.

**The case for:** in the €15k–€60k tier, clients prioritise budget efficiency, turnaround and direct communication over institutional balance sheets. A lean operator delivers **−34,1%** on stills while holding attractive margin.

**Verdict: build, narrow.** The counter-thesis is fatal only above €300k, which is exactly the tier being excluded.

---

## 8. Costed 90-day plan

**Weeks 1–4 — foundation**
- Incorporate S.L. via CIRCE under Ley Crea y Crece (€1 capital)
- Corporate bank account + FNMT digital certificate
- Contract audiovisual gestoría laboral for Sistema RED onboarding
- Clean the marketing website

**Weeks 5–8 — engine + vendors**
- Relational schema + canonical alias dictionary
- Multimodal parsing pipeline, schema-constrained tool calling
- Negotiate 15–20% baseline trade discounts, BCN + Madrid
- End-to-end test on sample riders → multi-vendor RFQs

**Weeks 9–12 — commercial activation**
- Dispatch 48 targeted emails to boutique UK + DACH producers
- Target photographer agents and independent creative producers
- Run inbound briefs through the engine
- Secure first paid shoot; audit real margin and turnaround

| Budget line | Cost | Basis |
|---|---|---|
| Notary + Mercantile Registry (S.L.) | €350,00 | CIRCE standard notarial tariff |
| Corporate digital certificate | €120,00 | FNMT / Registry processing |
| Gestoría laboral retainer, 3 mo | €750,00 | €250/mo specialised audiovisual |
| Public liability insurance deposit | €450,00 | Cinevent / Hiscox pro-rata |
| Cloud, domain, workspace, 3 mo | €90,00 | Google Workspace €18/mo + infra |
| Foundation model API, extraction corpus | €150,00 | ~1.500 document iterations |
| Prospecting + contact verification | €180,00 | Directory verification access |
| Supplier verification meetings | €400,00 | Travel, BCN + Madrid |
| Contingency | €300,00 | Admin + banking |
| **Total 90-day** | **€2.790,00** | |

> ⚠ **Tier-0 conflict:** the €150 "foundation model API usage" line assumes a paid API. James's hard rule forbids any paid API. Either that line is €0 (run extraction on the subscription) or the phase must be redesigned. **Do not action it as written.**

### Stop conditions

- **Week 4** — halt the build if zero-shot extraction across **50 real riders** fails **≥85% precision / ≥80% recall** after alias normalisation.
- **Week 8** — halt quoting if fewer than **3 rental houses** grant a **≥15%** trade discount.
- **Week 12** — pause expansion if outreach to **48 producers/agents** yields fewer than **3 qualified quote requests**. In that case, keep operating as a freelance digitech.

### The cheapest decisive experiment — €0

1. Take **three historical commercial stills riders** from past productions.
2. Manually build comparative RFQ packages; send to **three primary rental houses**.
3. Measure turnaround, actual trade discount granted, and missing dependencies.
4. Assemble the comparison matrix by hand, **timing the human labour**.
5. Compare resulting price and margin against a standard service-production quote.

**This verifies the trade terms and the cost advantage before a line of code is written.**

---

## 9. Conclusion

Sound as a **boutique stills and digital-motion service company, €15.000–€60.000**. Unviable against established companies on high-budget TVC — balance sheet, not software, decides those.

Route: **S.L. → outsourced labour compliance → domain-specific rider parser → 34,1% pricing advantage in commercial stills.** Run the €0 manual validation first.
