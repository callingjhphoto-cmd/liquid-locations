# Liquid Locations — Automation Build Plan
_Written 21 Aug 2026. Source: `research/RESEARCH_gemini_2026-08-21.md` (Gemini Deep Research, commissioned via `GEMINI_DEEP_RESEARCH_PROMPT.md`, returned to james@huertas.co.uk 21 Aug 2026, read in full)._

## 1. What changed

Liquid Locations already had a business plan, a rate card and a live site. What it did not have was an **engine**. This document is the engine plan, and it corrects three things the existing docs get wrong.

### 1.1 CORRECTION — the live site's tax-incentive section is wrong for our client base

`index.html` §Tax Incentives pitches "Spain pays you to shoot here — 30% mainland, 54% Canaries, Article 36.2."

Article 36.2 of Ley 27/2014 covers **feature films and audiovisual fiction/animation/documentary series only**. Commercial advertising (*spots publicitarios*) and stills photography are **strictly excluded** — [verified — Ley 27/2014 Art. 36.2; AEAT binding rulings V1746-15, V2300-21]. Minimum qualifying spend is €1M in Spain (€200k for VFX/post) — above almost every commercial job we would bid anyway.

Liquid Locations sells to advertising agencies and commercial production companies. **Every client the site is aimed at is ineligible for the rebate it advertises.** This is a live credibility risk with exactly the sophisticated procurement people we want to impress.

- **Action:** cut or heavily qualify the tax-incentives section before any outreach goes out from that URL.
- Memory already carried "Spain's film rebate does NOT cover stills" ([[reference-digitech-rate-benchmarks]]). The new fact is that **commercials are excluded too**, not just stills.

### 1.2 CORRECTION — the location-scout-replacement thesis is half right

The research directly tests "can a database replace the scout" and returns **Contradicted** for full replacement. What a database cannot do:

- real-time acoustic interference (metro rumble, flight paths, school recreation, AC compressor cycling, unannounced roadworks)
- internal breaker capacity, three-phase CETAC sockets, cable run length back to the genny
- historic street corner radii, low cables, tree canopy, subterranean parking weight limits for 26-tonne trucks
- neighbour, business-association and Jefe de Policía Local relationships
- dynamic light occlusion from new scaffolding, vegetation growth, glass-tower glare that sun-path apps miss

What it **can** do is kill the expensive half: early visual discovery and client shortlisting. The unit-economic model in the research reflects this — it keeps a scout, just for fewer days.

- Scenario A (stills, Barcelona): scouting+loc-mgmt €2.800 → €1.400, by cutting scout days from 4 to 2 targeted verification days, not to zero.
- **Position it as "targeted recce, not blind scouting."** Do not claim scoutless.

### 1.3 CONFIRMED — the wedge is the equipment RFQ engine

Independently ranked **Rank 1 (highest value ÷ effort)** of six automation candidates, ahead of call sheets, VAT/invoicing, contracts, permits, and (last, Rank 6) autonomous scouting. Same conclusion reached in conversation before the research came back.

---

## 2. The wedge, specified

**Kit list in → normalised → RFQ fan-out → comparison matrix out.**

1. Client drops an unstructured PDF or raw email rider into the system.
2. Semantic parser extracts and normalises items to canonical product records.
3. Deterministic compatibility module flags missing dependencies (e.g. SkyPanel X21 requested without stands or distro).
4. Relational query against supplier tables, applying known trade-discount profiles per rental house per region.
5. Branded itemised RFQs email out; responses compile into a side-by-side cost + margin matrix for the EP.

**Why this one:** no client IT integration, no legal liability handoff, and it attacks the single biggest coordinator time sink in bidding.

### The parsing problem is real and named

- **>60% of inbound riders are flattened PDFs or email body text** — needs a semantic layer, not a CSV schema.
- **Hierarchical incompleteness:** riders name the head ("ARRI M90") and omit head-to-ballast cables, 63A/32A breakout distro, ballast mounts, safety bonds.
- **Shorthand aliases:** "Titan Tubes", "Panchros", "M90", "OConnor", "Phase One 150" must map to ERP product codes.

Real stills rider vocabulary to build the alias table against: Phase One IQ4 150MP + XF body, Schneider Kreuznach 55/110mm LS f/2.8 Blue Ring, TetherPro USB-C, Inovativ Scout 37 digi-cart, Apple Studio Display, Profoto Pro-11 2400 AirTTL + ProHead Plus, Briese Focus 140, C-stands and sandbags.

Motion: ARRI Alexa 35 LPL, Cooke Panchro/i Classic FF, ARRI Hi-5, SmallHD Cine 13, Teradek Bolt 6 XT, Anton Bauer, O'Connor 2575D; SkyPanel X21, ARRI M90 9kW HMI, Astera Titan Tube 8-sets, Creamsource Vortex8, Matthews 12x12 with Ultra Bounce/Grid, Honda EU70is.

### Falsifiable exit test — Phase 1 (Months 1–3)

> **If zero-shot parsing of raw PDF kit lists into valid supplier items does not hit ≥85% precision without manual correction, stop.** Below that the verification overhead exceeds what a coordinator costs.

This is the number to hold ourselves to. It is a stop condition, not a target to argue down.

**Status of the underlying assumption:** LLM parsing of kit lists at >85% is marked **Supported** by the research. The kill risk is our implementation, not the technique.

### Hard constraint on the supplier side

> **No major Spanish rental house exposes a public REST API.** EPC, Aluzine, Cinelux, Ovide, Servicevision — all quote manually from internal ERPs (RentalTracker, EasyJob, Dynamics) and export static PDF/Excel. Status: **Contradicted** as a viable assumption.

Quote turnaround is 12–24h in normal business hours. So the engine's output is **an email RFQ and an inbox parser**, not an API call. Design for that from day one — it is the same shape as the Fixer's `/go` seam: deterministic local logic, real outbound, human-readable payload.

---

## 3. Where the money actually is

### How a Spanish service company is paid (four components)

| Component | Rate | Verification |
|---|---|---|
| Production fee (markup on net spend) — TVC | 10–20% | [verified — APCP standard practice / industry benchmark] |
| Production fee — stills/photography | 15–25% | [verified — APCP standard practice / industry benchmark] |
| — compressing at €300k+ projects | toward 10–12% | [unverified] |
| — sustaining on €15k–40k stills | up to 20–25% | [unverified] |
| Equipment sub-rental markup | 10–20% over net | [verified — industry benchmark] |
| — alternative: trade discount retained as spread | 20–40% off rate card | [verified — industry benchmark] |
| Location handling fee on private hire | 10–15% | [unverified] |
| Travel/logistics handling fee | 5–10% flat | [verified — industry benchmark] |
| Gross operational margin, traditional company | 18–32% | [unverified] |

**Marked up:** equipment, internal production personnel lines, vehicles, studio dry-hire, generators.
**Pure pass-through:** municipal permit fees, police escorts, tolls, flights, talent residuals, dietas.
**Variable:** catering, private location hire (0–15%), hotels.

### The automation target, quantified

- Production-management labour (LP, PM, coordinators, runners) = **8–15% of gross budget** [unverified].
- Plus service markup 12–18% → **coordination is 20–33% of the total client invoice** [unverified].

That band is the business. Automate the coordination layer, keep the internal management margin, undercut on the production fee.

### Spanish market day rates (10-hr day, Barcelona/Madrid)

Statutory floors from III Convenio estatal de producción audiovisual (técnicos), BOE-A-2024-6846, updated BOE-A-2025-18060. **Market rates run well above statutory minimums** and are marked unverified.

| Role | Statutory monthly base (2026) | Market day rate |
|---|---|---|
| Executive Producer | n/a (executive tier) | €600–1.200 |
| Line Producer | €2.853,13 | €450–750 |
| Production Manager | €2.437,45 | €350–500 |
| Production Coordinator | €1.813,91 | €220–320 |
| Location Manager | €2.437,45 (Grupo 2 equiv) | €350–550 |
| Location Scout | €1.813,91 (Grupo 3 equiv) | €250–380 |
| PA / Runner | €1.608,75 | €130–180 |
| Production Driver | €1.608,75 (Grupo 5 equiv) | €150–220 |
| Gaffer | €2.132,40 (2025 base) | €380–550 |
| Spark | €1.818,98 (2025 base) | €240–320 |
| Stills 1st Assistant | not covered by convenio | €250–400 |
| **Digi Tech / Capture** | not covered by convenio | **€350–550 + kit fee** |

Statutory figures [verified — BOE-A-2025-18060]; market columns [unverified]. Flexibility plus €134,59/mo (€131,69 for the 2025-base lighting grades).

> **Cross-check against our own rate card.** `pricing.md` lists Location Scout at €247–250/day; the market band here is €250–380. `pricing.md` EP/Location Manager €450–500 sits inside the €350–550 loc-mgr band but below the €600–1.200 EP band. Worth a deliberate decision rather than drift — see §7.
> **Cross-check against James's own digitech card:** €350–550 + kit fee here vs the €450–950/11h Barcelona benchmark in [[reference-digitech-rate-benchmarks]]. Different survey, different day length — do not merge them.

---

## 4. Unit economics — the actual claim

### Scenario A — commercial stills, Barcelona, 2 shoot days, 8-person inbound team, 3 locations

| Line | Traditional | Automated | Mechanism |
|---|---|---|---|
| Location scouting & management | €2.800 | €1.400 | 4 scout days → 2 targeted verification days |
| Production management personnel | €4.500 | €1.800 | EP + 1 runner replaces LP + coord + runner + EP fee |
| Camera & stills lighting | €4.200 | €3.360 | 20% trade discount passed through |
| Permits & admin | €800 | €400 | no external gestoría expediter |
| Travel & ground transport | €3.500 | €3.150 | 10% handling fee removed |
| Catering & welfare | €1.800 | €1.800 | pure pass-through |
| Production fee | €3.500 (17,5%) | €2.000 (10% / fixed) | undercut on the fee line |
| **Total to client** | **€21.100** | **€13.910** | **−€7.190, −34,1%** |

### Scenario B — TVC, Andalucía, 4 shoot days, 40 local crew, 5 locations

| Line | Traditional | Automated |
|---|---|---|
| Location dept | €8.800 | €5.600 |
| Production management crew | €18.500 | €8.200 |
| Camera/lighting/grip | €48.000 | €38.400 |
| **Technical crew labour (+32% SS)** | **€56.000** | **€56.000** |
| Permits, police, Costas | €5.200 | €4.400 |
| Transport & vehicles | €28.000 | €28.000 |
| Base camp, facilities, catering | €22.000 | €22.000 |
| Insurance & legal | €6.000 | €5.200 |
| Production fee | €34.000 (15%) | €26.000 (12%) |
| **Total to client** | **€226.500** | **€193.800** | **−€32.700, −14,4%** |

**Read this honestly.** The saving is 34% on stills and 14% on TVC because on TVC the crew, trucks, catering and base camp are irreducible physical cost. **Stills is where the model wins.** That is also the market James already sells into. Lead with stills; treat TVC as the follow-on, not the opening pitch.

---

## 5. Data model

Hybrid. PostgreSQL relational for anything financial, temporal or contractual. Vector embeddings **only** where natural language or visual interpretation is genuinely required.

### Relational core
```
Project (1) ──< (N) CrewRole       (convenio tier, rates)
Project (1) ──< (N) EquipmentLine  (alias, mount, ballast) ──> (1) SupplierItem
Location   (PostGIS coords, curfews, base fees)
PermitOrdinance (municipality rules, lead times, fee formulas)
```

### Entities

- **Supplier** — UUID, legal name, trade name, CIF/NIF, vertical ENUM, region array, negotiated trade-discount %, payment terms, contact endpoints, API-availability flag (near-universally false, see §2).
- **EquipmentItem** (hybrid) — UUID, FK Supplier, canonical title, **text array of shorthand aliases**, department ENUM, base day rate EUR, JSONB technical params (lens mount, power draw, ballast dependencies), embedding vector.
- **Location** (hybrid spatial) — UUID, title, ownership ENUM, territory ENUM, PostGIS point, base daily hire fee, heavy-vehicle parking capacity, generator access flag, night-curfew timestamp, statutory permit lead time, visual embedding, free-text operational notes.
- **CrewProfile** — UUID, legal name, convenio tier ENUM (Grupos 1–5), role, engagement classification ENUM, base 10-hr rate, agreed OT rate, home region, English fluency flag, contact.
- **PermitOrdinance** (relational + rules engine) — UUID, municipality, governing ordinance ref, min statutory lead time in business days, base admin fee, daily linear-metre occupancy rate, police-escort-required flag, weekend permission, JSONB curfew constraints.

### Retrieval discipline — where the LLM is allowed

**Vector/semantic, yes:**
- visual location discovery — client moodboard → location photos
- kit-list normalisation — "C-Stand w/ arm", "2x M90", "Phase One 150" → canonical records
- knowledge retrieval across historic wrap post-mortems and location access notes

**Deterministic relational + rules engine, no LLM:**
- **all pricing, markup, VAT localisation and invoicing** — never probabilistic generation
- convenio compliance: wage minimums, 12h inter-day rest, progressive OT tiers per BOE-A-2025-18060
- permit feasibility: does the shoot date clear the municipal lead-time window and parking capacity

This is the same seam discipline as the Fixer (`lib/ai.ts`): one swappable intelligence function, everything load-bearing stays deterministic.

---

## 6. Data sourcing — what is legally ingestible

| Source | Reusable? | Notes |
|---|---|---|
| **BORME / Registro Mercantil** | **Yes** | CNAE 5912 post-production, 5915 production, 7739 equipment rental. Reuse expressly lawful under Ley 37/2007 + EU Directive 2019/1024, subject to GDPR. |
| **ICAA administrative registry** | **Yes** | Registered production/service companies, via Ministry of Culture open-data portal. |
| Film Commission location directories (BFC, Madrid, Andalucía, Canary, Mallorca, Basque, Valencia) | **No** | All seven: public searchable, **none licensable**. Photo assets under third-party IP; scraping prohibited by ToS. Status: **Contradicted** as a bulk-ingest source. |
| Trade rosters (APCP, PROFILM, AEC, APPA) | Manual only | Benchmarking + vendor mapping baseline. |
| Manufacturer catalogues (ARRI, RED, Sony, Profoto, Cooke) | Yes | Seeds EquipmentItem + alias tables. |
| Municipal ordinances | Hand-entry | Monitor BOP / DOGC / BOCM for fee revisions. |

**The BORME route is the same infrastructure as option A in `SIDE_BUSINESS_MERGED_PLAN_2026-08-21.md`.** One scraper, two businesses. That is a genuine reason to build the BORME pull regardless of which idea wins.

**Location library is the expensive entity** — "Moderate to High, requires continuous curation". Everything else is Low. Enrich it from post-shoot recce reports rather than trying to buy or scrape it.

---

## 7. Permits — the operational knowledge that is actually the moat

### Barcelona
Barcelona Film Commission + 10 Gerències de Districte + Guàrdia Urbana (UT1). Filed via **OEP/OGE** portal.
- Comunicat d'activitat (simple): **3–5 business days**
- Permís d'ocupació (technical vehicles, gennys, rolling closures): **10–15 business days**
- Fees under **Ordenança Fiscal 3.10**: technical parking €0,60–1,20/m²/day [unverified] + €50–120 admin per application
- Stills/small-crew notifications typically exempt from occupancy tax
- Ciutat Vella (Gòtic, Born, Raval) and Sagrada Família strictly regulated; **night filming with structural lighting or genny noise prohibited after 22:00** near residential

### Madrid
Madrid Film Office (municipal) + Film Madrid (regional), via Sede Electrónica.
- *Acto Comunicado* (crews under ~10–15, handheld, no reserved parking): **2–3 business days**
- *Permiso Ordinario*: **7–15 business days**
- Base admin fee **€48,65** [verified — Madrid Film Office]
- Vehicle space reservation **€0,58 per linear metre per day** [verified — Madrid Film Office]

### Andalucía
Municipal film offices + Andalucía Film Commission. Standard urban **5–10 business days**. Heritage monuments (Patronato de la Alhambra y Generalife, Real Alcázar) **15–30 business days** plus preservation fees. **Beaches require Dirección General de Costas, 2–4 weeks minimum.**

### Canary Islands
Cabildos Insulares + Ayuntamientos + Medio Ambiente. Urban **5–10 business days**; Espacios Naturales Protegidos and Parque Nacional del Teide **15–20 business days** with environmental evaluation. Urban fees €30–100; **national-park environmental security bonds €1.000–6.000, refundable on post-shoot inspection** [unverified].

> This table **is** the defensible asset — alongside verified trade-discount structures and client trust. Not the software. Generic workflow UIs and form builders are reproducible in a weekend; the research says so explicitly.

---

## 8. Compliance — the things that can end the business

### Falsos autónomos — the biggest operational risk
Under Estatuto de los Trabajadores Art. 1.1 / 8.1 and the audiovisual convenio, on-set technicians work within the production company's *ámbito de organización y dirección*. The ITSS **actively audits sets**. Sparks, grips, PAs and camera assistants must be hired on **contrato temporal por circunstancias de la producción** and registered in Régimen General **before call time**.

Exposure under LISOS:
- retroactive employer SS quotas (~31,5–33% of base) + surcharges of 20–35%
- fines **€3.750–12.000 per misclassified worker**

Only genuine HODs with independent business infrastructure, own registered kit, staff and multi-client B2B operations can invoice as autónomos safely. Status: **Supported** [verified — BOE-A-2024-6846; ET Art. 1.1].

**This kills the naive "one person + freelancers" model.** Payroll and Sistema RED alta capability is not optional — it is a precondition. It also means the €56.000 crew line in Scenario B genuinely cannot be compressed.

### Cross-border VAT (Ley 37/1992)
- **EU B2B (Germany, Nordics):** valid VAT ID verified in VIES → 0% VAT, reverse charge, *inversión del sujeto pasivo* Art. 84.Uno.2º. Declare on **Modelo 349** + quarterly **303**.
- **Non-EU B2B (UK, US):** generally not subject to Spanish VAT, Art. 69.Uno.1º.
- **The trap — Art. 70.Dos "use and enjoyment":** advertising services billed to a non-EU entity but where the ad is **exclusively** broadcast and consumed in Spain can be reassessed at 21% Spanish VAT retroactively. International/pan-European campaigns keep 0%. Status: **Supported**.

### Insurance stack
- Public liability (RC General): **mandatory for every municipal permit.** €1,5–3M stills/small commercial; €6–10M major TVC/urban.
- Employer's liability (RC Patronal): €300–600k per victim [unverified]
- Equipment all-risks: €100k–1M+
- Cast non-appearance / production interruption (*seguro de buen fin*)
- Weather (parametric or indemnity)
- Underwriters in Spain: Chubb European Group, Hiscox España, Circle Group/Cinevent, Berkley España, AGCS

### Holding-company procurement — the onboarding wall
WPP, Omnicom, Publicis, IPG, Havas require: escrituras de constitución, CIF, UBO proof, bank ownership certificate, **2–3 years of filed corporate balance sheets**, certificados de estar al corriente with AEAT and Seguridad Social, signed CoBE + anti-bribery/AML/whistleblower/sanctions screening, GDPR/LOPDGDD guarantees, often **cyber liability €1–2M**, plus **AdGreen** carbon tracking (mandatory across UK/EU/US agencies) and **BAFTA albert** for UK broadcast hybrid.

> "Holding company procurement allows unvetted or low-capitalised startups to onboard as primary vendors" — Status: **Contradicted**.
>
> **The 2–3 years of filed balance sheets is a hard gate.** A newly formed S.L. cannot clear it. This is the single most important constraint on go-to-market and it argues for entering below procurement level — direct with production companies and photographers, who buy on relationship — rather than pitching holding-company rosters first.

---

## 9. The counter-thesis, stated fairly

Why agencies keep paying Palma Pictures, Twenty Four Seven and Fresco Film a premium:

1. **Working capital.** They cash-flow €500k+ productions — location deposits, hotel blocks, weekly crew payroll — long before agency milestones clear. We cannot.
2. **Total indemnity.** On-set incident, revoked permit, owner damage suit: their insurance, legal team and reserves shield the client.
3. **24/7 crisis resolution.** Location falls through, camera package fails, weather hits — deep local roster deploys backups immediately.
4. **Procurement compliance.** Bypassing an approved tier-1 vendor creates a compliance problem inside the client's own organisation.

Nothing in the automation thesis addresses 1, 2 or 4. **What clients buy from incumbents is risk transfer, not coordination.** Automation attacks the cost of coordination, which is the part they were never really paying for.

**Therefore the honest positioning is not "cheaper Palma Pictures."** It is: smaller stills and low-mid commercial jobs, below the procurement threshold, where the client is a production company or photographer buying on relationship and the €7k saving on a €21k job is material to whether the job happens at all.

---

## 10. Phased plan with stop conditions

| Phase | Months | Delivered | Stop condition |
|---|---|---|---|
| **1. RFQ wedge** | 1–3 | Kit-list parser (stills + motion); mapping to supplier catalogue; RFQ dispatch to BCN/Madrid/Málaga rental houses; cost comparison matrix | **<85% zero-shot parse precision on raw PDFs → stop** |
| **2. Locations + permits** | 4–6 | Spatial location catalogue with visual search; auto-generated permit packages (OEP/OGE Barcelona, Sede Madrid); occupancy-tax and parking-footprint calculation | **>15% of automated permit submissions rejected or flagged → halt auto-generation, revert to human coordinator** |
| **3. Full engine** | 7–9 | Brief intake → crew routing → call sheets → travel grid → cross-border billing with VIES + reverse charge | **One EP cannot run 3 concurrent productions without errors, overruns or delays → thesis invalidated** |

Automation ranking, highest ROI first: **RFQ parsing (1) → call sheets/movement orders (2) → VAT & invoicing (3) → contract/release assembly (4) → permit assembly (5) → autonomous scouting (6, lowest).**

---

## 11. Immediate next actions

1. **Fix the tax-incentives section on `index.html`** — it advertises a rebate our entire client base is excluded from. Highest-priority, lowest-effort, live-reputation item.
2. **Reconcile `pricing.md` against the market bands in §3** — deliberately, with a note on why each rate sits where it does.
3. **Build the alias table first**, not the app. A CSV of shorthand → canonical product code for the ~200 items that appear on real stills and commercial riders. It is the parser's ceiling, and it can be built and tested with zero infrastructure.
4. **Test the 85% gate on real riders before writing a line of app code** — James has real kit lists in his own email from actual shoots. That is a same-week test.
5. **Do not build the location library yet.** Highest curation cost, lowest automation ROI, and legally the hardest to seed.
6. **Decide the entity question.** Falsos autónomos exposure and permit-mandatory public liability both require a real vehicle. The S.L. plan in `business_plan.md` predates this research and now has stronger justification than it did.

## 12. Cross-references

- `GEMINI_DEEP_RESEARCH_PROMPT.md` — the commissioning prompt
- `research/RESEARCH_gemini_2026-08-21.md` — full 81KB report
- `business_plan.md`, `pricing.md` — predate this research; §1.1 and §11.2 flag the conflicts
- `~/Documents/Claude/memory/SIDE_BUSINESS_MERGED_PLAN_2026-08-21.md` — BORME infrastructure shared with side-business option A
- `~/Documents/Claude/projects/fixer/` — the seam pattern this build copies (`lib/ai.ts`)
