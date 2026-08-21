# Gemini Deep Research prompt — Liquid Locations production-automation architecture

## Role
You are a research analyst with deep knowledge of international commercial stills and moving-image production. Your output will be used to design a software system, so be concrete, name real companies, real documents, real fee structures and real statutes. Where you cannot verify a figure, say so explicitly rather than estimating.

## Context
A bilingual British-Spanish production professional based in Barcelona is building a tech-enabled service company. It sells local production services in Spain to advertising agencies, brands and production companies in London, Germany (Hamburg, Berlin, Düsseldorf), the Nordics and the US.

The thesis: most of what a local "service production company" charges for is coordination, not craft. Sourcing crew, equipment, locations, permits, flights, hotels, transport, catering and insurance is a structured, repeatable, information-heavy workflow. If that workflow is captured in a retrieval database plus automation, one experienced executive producer can run productions that today need a producer, a production manager, a production coordinator, a location manager and a location scout — and therefore undercut incumbents on the production-fee line while paying local crew fairly.

Incumbent comparators in Spain to research explicitly: Palma Pictures (Mallorca), Twenty Four Seven Production (Barcelona/Mallorca), Fresco Film (Andalucía), Nostromo Pictures, Lee Films International, and the smaller Barcelona/Madrid stills-service fixers. Also research equivalents in other service markets for contrast: Cape Town (South Africa), Lisbon/Portugal, Athens/Greece, Canary Islands, Morocco, Mexico City, Buenos Aires.

## Part 1 — Map the actual workflow

Document, step by step and in chronological order, the end-to-end workflow of an inbound international production booking a shoot in Spain, from first enquiry to final invoice and wrap. For each step, state:
- who normally performs it (role title, and whether client-side or service-side)
- what the input artefact is and what the output artefact is (name the actual documents: brief, treatment, shot list, kit list, call sheet, movement order, risk assessment, carnet, purchase order, etc.)
- typical elapsed time and where the bottlenecks are
- what information is needed to complete it and where that information lives today
- how it fails when it fails

Cover both **stills/photography** and **film/TVC**, and be explicit where the two diverge — stills productions are smaller, faster-turnaround and lower-budget, and much of the published production literature is film-biased. Cover at minimum:
1. Enquiry, brief intake and the first budget/estimate ("ballpark") stage
2. Location sourcing, recce and options — including virtual/remote recce practice post-2020
3. Crew booking, rates and availability
4. Camera, digital-capture and lighting equipment sourcing
5. Permits and permissions
6. Travel: flights, ground transport, accommodation
7. Catering, welfare, facilities (honeywagons, unit base, tents)
8. Insurance, liability, risk assessment, health and safety
9. Legal, contracts, talent releases, location agreements, usage rights
10. Payroll, invoicing, VAT, tax and cash flow across borders
11. Shoot-day running, contingency and weather cover
12. Wrap, reconciliation and actualised cost report

## Part 2 — The money

- How is a Spanish service production company actually paid? Break down the real components: production fee/mark-up percentages, per-day rates, mark-up on crew, mark-up on equipment, commission on location fees, handling fees on travel. Give ranges and cite sources.
- What are current published or industry-standard day rates in Spain for: executive producer, line producer, production manager, production coordinator, location manager, location scout, production assistant/runner, driver, stills photographer's assistant, digital technician, lighting technician (gaffer/spark)? Cite APCP (Asociación de Productoras de Cine Publicitario), any applicable convenio colectivo (e.g. BOE-A-2024-6846 audiovisual), and real rate cards where they exist.
- Where is the margin in a typical Spanish service job, expressed as a percentage of total budget? Which line items are pure pass-through and which carry mark-up?
- Quantify the coordination overhead specifically: what proportion of a service production company's fee is attributable to the production-management labour that could plausibly be automated?
- Spain's audiovisual tax rebate: state precisely what it covers, what it excludes, the minimum spend thresholds, the regional variations (Navarra, País Vasco, Canarias), and confirm explicitly whether **stills/photography** productions qualify. Cite the statute.

## Part 3 — Locations, without scouts

- How does location sourcing actually work in Spain today? Who holds the inventory: film commissions, private location agencies, individual scouts, owner-direct?
- List the actual Spanish film commissions and location offices by region (Barcelona Film Commission, Madrid Film Office, Andalucía Film Commission, Canary Islands Film, Mallorca Film Commission, Basque, Galicia, Valencia, etc.), what each publishes, whether they operate a searchable public location database, and whether that data is licensable or reusable.
- Which private location libraries exist in Spain and Europe, what do they charge, and what are their terms?
- Assess honestly: **can a location scout be replaced by a database plus remote recce?** Where does that hold and where does it break down? What does a scout do that a database cannot — access negotiation, owner relationships, sun-path and light assessment, noise, power, parking, neighbour management, permit feasibility? Cite practitioners.
- What is the legal and permitting reality of shooting on private property, in public space, and in protected/heritage sites in Spain? Give the permit body, the process, the lead time and the fee scale for at least Barcelona, Madrid, Mallorca, Andalucía and the Canary Islands. Cite the ordinances.
- What is Barcelona's current position specifically — the city has restricted certain filming permits and locations. State the current rules and cite them.

## Part 4 — Suppliers and the data layer

- Enumerate the real supplier categories a production database would need to hold for Spain, and for each, name the significant suppliers in Barcelona, Madrid, Mallorca, Málaga/Andalucía, Canarias and Valencia: camera rental, lighting/grip rental, digital-capture/tethering, studios, generators, vehicles, unit base, catering, security, medics, drone operators, casting agencies, model agencies, stylists' assistants, hair/make-up, art department suppliers, prop houses, freight/carnet agents.
- For each supplier category: how are they normally approached, what does a request-for-quote actually contain, what turnaround do they give, and do any of them expose structured data (API, price list, online booking) rather than email-only?
- What structured public data sources exist that could seed such a database — film commission registries, ICAA registries, Spanish company registry (BORME) CNAE codes for audiovisual and equipment rental, chamber-of-commerce lists, trade association member lists (APCP, PROFILM, AEC)? For each, state whether reuse is legally permitted, and under what licence.
- Equipment: what is the standard structure of a photographic **kit list** and a **lighting list** as sent by a photographer or gaffer? Give real examples of the fields and conventions used, and identify how machine-parseable they typically are (PDF, email body, Excel, Google Sheet, Toggl/Yamdu/other tool export).
- What production-management software is already used in this market — Yamdu, Studiobinder, Scenechronize, Movie Magic, Sylvester, Farmers Wife, Hot Budget, Showbiz, Croogloo, Dramatify — and specifically what does each already automate? Where are the genuine gaps that a Spain-focused service layer would be filling rather than duplicating?

## Part 5 — Competitive and defensibility analysis

- Who is already attempting to automate or productise production services? Include marketplaces and platforms (e.g. Filmustage, Wrapbook, Yamdu, Peerspace, Giggster, Locationscout.net, Filmmakers/Set.a.light, ProductionHUB, Mandy, Backstage, The Location Guide, KFTV, Filmocracy), AI-scripted-breakdown tools, and any Spain-specific attempts. What works, what has failed, and why?
- Where has AI already been adopted in production workflows as of 2026 — script breakdown, budgeting, scheduling, call sheets, location matching by image, permit automation? Name real products and real evidence of adoption.
- What is genuinely defensible for a one-person operation here: the supplier data, the permit knowledge, the relationships, the client trust, or the software? Argue both sides.
- Give the strongest case AGAINST this business. Why do international clients keep using established service companies even when cheaper alternatives exist? What are they actually buying — insurance, indemnity, bonding, a named producer who answers the phone at 3am, prior relationship, agency procurement approval? Be brutal, and cite people who have said this.

## Part 6 — Risk and compliance

- What liability does a service production company carry in Spain? What insurance is mandatory versus expected: public liability, employer's liability, equipment all-risks, errors and omissions, weather/cast insurance? Give typical cover levels and who underwrites them.
- Employment law: when does a Spanish production have to employ crew rather than engage them as autónomos? What is the exposure to falsos autónomos rulings, and what have recent Spanish inspections/rulings held for the audiovisual sector? Cite them.
- Cross-border VAT: how does a Spanish S.L. invoice a UK, German or US client for production services? Reverse charge, place-of-supply rules post-Brexit, and where it commonly goes wrong.
- What does an international agency's procurement/vendor-onboarding process demand of a Spanish supplier — accreditations, insurance certificates, financial standing, anti-bribery, GDPR, sustainability (albert certification, AdGreen)? List the actual requirements from named holding companies where documented.

## Part 7 — The architecture game plan

Given everything above, propose a concrete build plan for a retrieval-augmented system that runs this workflow. Specifically:

1. **Data model.** Propose the entities, their fields and their relationships — suppliers, crew, locations, permits, rate cards, past jobs, quotes, clients. State which fields must be structured and which are free-text suited to embedding-based retrieval.
2. **Retrieval design.** Where is vector/semantic retrieval genuinely the right tool, and where is a plain relational query or a rules engine better? Be specific and sceptical — argue against over-using an LLM.
3. **The automation sequence.** Identify which workflow steps automate cleanly today, which need a human in the loop, and which should not be automated at all. Rank them by (value released ÷ effort to build).
4. **The wedge.** Name the single narrowest slice that delivers real value to a paying client fastest, and explain why. Consider — but do not assume — the "kit list email in → RFQ fan-out to rental houses → consolidated quote back to client" loop.
5. **Sourcing the data.** For each entity in the data model, state how it gets populated initially, how it stays current, and what it costs. Distinguish scraped, licensed, public-register, partner-supplied and hand-entered.
6. **Build phases.** Give a phased plan with what exists at the end of each phase, and a falsifiable test for each phase — the specific evidence that would say "stop, this does not work".
7. **Cost structure comparison.** Model, with sourced numbers, the cost base of a traditional Spanish service production company versus this automated model, on a representative stills job (2 shoot days, 8-person travelling team, 3 locations, Barcelona) and a representative TVC job (4 shoot days, 40 crew, 5 locations, Andalucía). Show where the savings actually come from and be honest about where they do not.

## Output requirements
- Cite sources inline with links throughout. Prefer primary sources: statutes, BOE, convenios, film commission pages, association rate cards, company terms, practitioner interviews.
- Mark every number as either **[verified — source]** or **[unverified]**. Do not present an estimate as a fact, and do not fill a gap with a plausible-looking figure.
- Where the literature is film-biased and the stills answer differs or is unknown, say so explicitly.
- Prioritise Spain, with Barcelona, Madrid, Mallorca, Andalucía and the Canary Islands treated in that order of depth.
- End with: the ten things that most need to be true for this business to work, each marked as currently supported, contradicted, or unknown by the evidence you found.
