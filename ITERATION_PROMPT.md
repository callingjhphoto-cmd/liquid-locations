# Liquid Locations — Iteration Prompt

_Paste into a fresh session (Claude, Gemini Deep Research, or a subagent) to push the idea further. Written 21 Aug 2026._

---

## How to use this file

- **Section A** is the standing context. Include it every time.
- **Sections B–G** are separate iteration tracks. **Pick ONE per session.** They are ordered by what unblocks the most.
- Section H is the standing rules — include every time.

---

## A. Standing context — include in every iteration

> I am building **Liquid Locations**, a software-automated production service company in Spain. It sells local production services to advertising agencies, brands and production companies in London, Hamburg, Berlin, Düsseldorf, Stockholm and New York.
>
> **The thesis:** most of what a Spanish *productora de servicios* charges for is coordination, not craft — sourcing crew, kit, locations, permits, travel, catering and insurance is a repeatable, information-heavy workflow. Coordination is 20–33% of the client invoice. Captured in a structured database plus automation, one experienced executive producer replaces a line producer, a production manager, a coordinator and most of a location scout — undercutting incumbents on the production fee while paying local crew properly.
>
> **I am that EP.** Bilingual British-Spanish, Barcelona-based, working commercial stills sets as a digital technician. I know the workflow from inside it.
>
> **Incumbents:** Palma Pictures, Twenty Four Seven, Fresco Film, Nostromo Pictures, Lee Films International.
>
> **Established, do not re-derive:**
> - The wedge is the **equipment RFQ engine**: kit list in → parse → normalise → RFQ fan-out to rental houses → consolidated cost/margin matrix out. Ranked Rank 1 of 6 on value ÷ effort.
> - **No Spanish rental house has a public API.** EPC, Aluzine, Cinelux, Ovide, Servicevision all quote manually from internal ERPs, 12–24h turnaround, static PDF/Excel out. The engine emits **email**, and parses email back.
> - **Stills saves ~34%, TVC only ~14%** — on TVC the crew, trucks, catering and base camp are irreducible. Lead with stills.
> - **Article 36.2 rebate excludes commercials and stills.** Ley 27/2014; AEAT V1746-15, V2300-21. Never pitch it to this client base.
> - **Falsos autónomos:** on-set technicians must be on *contrato temporal* and registered in Régimen General before call time. €3.750–12.000 per misclassified worker plus retroactive SS. Payroll capability is a precondition.
> - **Holding-company procurement needs 2–3 years of filed balance sheets.** A new S.L. can't clear it. Enter below procurement level.
> - **The moat is supplier data, the permit knowledge graph and client trust — not the software.**
> - **What clients buy from incumbents is risk transfer** — working capital, indemnity, 24/7 crisis resolution, procurement compliance. Automation addresses none of it.
>
> **Full context:** `STATE_OF_PLAY.md`, `BUILD_PLAN.md`, `research/RESEARCH_gemini_2026-08-21.md`.

---

## B. Track 1 — Build the alias table _(do this first)_

The parser's ceiling is the alias table, and it needs zero infrastructure.

> Build the canonical equipment alias table for the RFQ parser: a CSV of `shorthand_alias, canonical_product, manufacturer, department, implicit_dependencies, typical_day_rate_eur, rate_source`.
>
> Cover the ~200 items that actually appear on commercial stills and TVC riders in Spain. Start from this real rider vocabulary:
>
> **Stills:** Phase One IQ4 150MP, XF body, Schneider Kreuznach 55mm / 110mm LS f/2.8 Blue Ring, TetherPro USB-C, Inovativ Scout 37 digi-cart, Apple Studio Display, Profoto Pro-11 2400 AirTTL, ProHead Plus, Briese Focus 140, C-stands, sandbags.
>
> **Motion:** ARRI Alexa 35 LPL, Cooke Panchro/i Classic FF, ARRI Hi-5, SmallHD Cine 13, Teradek Bolt 6 XT, Anton Bauer, O'Connor 2575D, ARRI SkyPanel X21, ARRI M90 9kW HMI, Astera Titan Tube 8-set, Creamsource Vortex8, Matthews 12x12 with Ultra Bounce/Grid, Honda EU70is.
>
> **The `implicit_dependencies` column is the valuable one.** Riders name the head and omit what it needs — an ARRI M90 requires a head-to-ballast cable, a 63A or 32A breakout distro, a ballast mount and safety bonds. A SkyPanel X21 requires stands and distribution. Encode every one of those.
>
> For each alias, list every shorthand a real gaffer or DoP would actually write: "M90", "2x M90", "Titan Tubes", "Panchros", "SkyPanel", "OConnor", "Phase One 150", "C-Stand w/ arm".
>
> Day rates: cite the rental house and date, or mark `[unverified]` and leave the figure blank. Never estimate a rate.
>
> Output the CSV plus a short note on which items were hardest to alias and why.

---

## C. Track 2 — Test the 85% gate

The Phase 1 stop condition. Nothing else matters until it passes.

> Design and run the parse-precision test for the RFQ engine.
>
> **The gate:** ≥85% zero-shot precision converting a raw PDF or email kit list into valid supplier line items, without manual correction. Below 85%, the project stops — verification overhead exceeds a coordinator's cost.
>
> Specify:
> 1. **What counts as a correct parse.** Is a correctly-identified item with the wrong quantity a pass or a fail? What about a correctly-identified item missing an implicit dependency? Define the scoring rubric before running anything — a rubric written after seeing results is worthless.
> 2. **The test corpus.** How many riders, what mix of stills and motion, what mix of flattened PDF / Excel / email body. State the minimum n for the result to mean anything.
> 3. **The failure taxonomy.** Categorise every miss: unknown alias, quantity error, hierarchy miss, OCR failure, ambiguous item. The distribution tells you what to fix.
> 4. **The honest read.** If it lands at 80%, what specifically would have to improve, and is that improvement a fixed cost (a bigger alias table) or an unbounded one (better OCR on arbitrary PDFs)?
>
> Do not tune the rubric to pass. The gate exists to kill the project cheaply if the technique doesn't work.

---

## D. Track 3 — Prove it on one real job

The most valuable iteration available, and it needs no software.

> Take a single real commercial stills job in Barcelona — 2 shoot days, 8-person inbound team, 3 locations — and produce the complete quote **by hand**, exactly as the automated system would.
>
> Then time every step and record which ones the engine would actually remove.
>
> The claim under test is Scenario A: €21.100 traditional → €13.910 automated, a 34,1% saving, built from:
> - scouting 4 days → 2 targeted verification days
> - LP + coordinator + runner + EP fee → EP + 1 runner
> - 20% equipment trade discount passed through
> - 10% travel handling fee removed
> - production fee 17,5% → 10%
>
> For each line: is the saving real, and would a client accept the reduced service? Be specific about what gets worse, not just cheaper.
>
> **The 20% trade discount is doing heavy lifting and is not yet secured with any rental house.** Say plainly what it would take to actually get it, and what the model looks like at 10% or at zero.
>
> Output: the hand-built quote, the timing log, and a corrected saving figure with each component sourced.

---

## E. Track 4 — Find the first client

The business has zero clients and 48 unsent drafts. This is the real bottleneck.

> Design the go-to-market for a Spanish production service company that cannot clear holding-company procurement.
>
> **The constraint:** WPP, Omnicom, Publicis, IPG and Havas require 2–3 years of filed corporate balance sheets, AEAT and Seguridad Social clearance, UBO proof, anti-bribery and AML compliance, GDPR guarantees, often €1–2M cyber liability, and AdGreen carbon tracking. A new S.L. clears none of it.
>
> So the first clients cannot be agencies directly. Work out who they *can* be:
> - production companies who already hold the agency relationship and sub-contract Spanish execution
> - photographers and their agents booking their own Spanish shoots
> - smaller brands shooting direct without an agency
> - other service companies needing overflow capacity
>
> For each: what do they buy on, what does the first conversation look like, and what proof do they need that a one-person operation can execute?
>
> **James's own pattern is the risk.** He has built and not sold before — 372 HHT venues classified with zero outreach executed; 48 London drafts written and unsent. Design the go-to-market so that the first step is a conversation, not a build.
>
> Output: the target list with reasoning, the opening approach, and the single smallest commitment that would prove demand.

---

## F. Track 5 — The permit knowledge graph

The second real moat asset, and the one most cheaply built.

> Build the structured permit database for Spanish filming, starting with Barcelona and Madrid.
>
> Schema per municipality: governing ordinance reference, application portal, permit types and their thresholds, minimum statutory lead time in business days, base administrative fee, occupancy rate per m² or linear metre per day, police-escort trigger, weekend permission, curfew constraints as structured JSON, and restricted zones.
>
> **Known starting points:**
> - **Barcelona** — BFC + 10 Gerències de Districte + Guàrdia Urbana UT1, via OEP/OGE. *Comunicat d'activitat* 3–5 business days; *Permís d'ocupació* 10–15. Ordenança Fiscal 3.10; technical parking €0,60–1,20/m²/day [unverified] + €50–120 admin. Night filming with structural lighting or generator noise prohibited after 22:00 near residential. Ciutat Vella and Sagrada Família strictly regulated.
> - **Madrid** — Madrid Film Office + Film Madrid, via Sede Electrónica. *Acto Comunicado* 2–3 business days; *Permiso Ordinario* 7–15. Admin fee €48,65 [verified]. Vehicle space €0,58/linear metre/day [verified].
>
> Verify every figure against the current municipal ordinance and cite it. Where the published figure has changed since August 2026, say so. Where you cannot verify, mark `[unverified]` and give no number.
>
> **Then answer the operational question:** which parts of a permit application can actually be auto-filled, and which need a human who knows the local film office? The Phase 2 stop condition is >15% of automated submissions rejected or flagged.

---

## G. Track 6 — Attack the thesis

Run this before committing real money or time.

> Argue as hard as you can that Liquid Locations should not be built.
>
> Steelman the automation thesis first, in its strongest form. Then take it apart.
>
> **Attack these specifically:**
> 1. The 20–33% coordination overhead is marked `[unverified]`. If it's really 12%, does the model still work?
> 2. The 20% equipment trade discount is unsecured. Rental houses give trade terms on volume; a company with no track record has no volume. Is the discount available at all in year one?
> 3. Stills jobs at €15k–40k support a 20–25% production fee precisely because they're small. Undercutting to 10% on a €21k job earns €2.000. **How many jobs a month does this need, and is that achievable solo?**
> 4. What clients buy is risk transfer — capital, indemnity, crisis cover, compliance. Can a one-person S.L. offer any of it credibly?
> 5. James's history is building without selling. What makes this different?
> 6. If the software works, what stops an incumbent with real client relationships from building the same thing and keeping their clients?
>
> **Then the counterfactual:** James earns €500/day as a digitech, a proven and immediate income. Every day on this is a day not earning. What return justifies it, and by when?
>
> Do not soften the conclusion. If the answer is "don't", say "don't" and name the single piece of evidence that would change your mind.

---

## H. Standing rules — include every time

> - **Zero fabrication.** Every number carries a named source or a shown derivation. No source → write `[unverified]` with **no number**. Never "approximately X" or "estimated X". "CANNOT VERIFY — would require fabricating X" is a better answer than a plausible figure.
> - **No paid API.** Everything runs on existing subscriptions. Any proposal requiring a metered API key is disqualified unless flagged explicitly as a blocked dependency.
> - **Cite primary sources** — BOE, statutes, convenios, municipal ordinances, film commission pages, company terms. Not summaries of summaries.
> - **Say when the literature is film-biased.** Most published production writing is about features and TV. Where the stills answer differs or is unknown, say so.
> - **No yes-man.** Steelman first, then critique hard. Flag the build-before-a-customer pattern whenever it appears.
> - **Falsifiable exits.** Every proposed phase ends with the specific evidence that would say *stop*.
> - **Spain first**, in this order of depth: Barcelona, Madrid, Mallorca, Andalucía, Canarias.
