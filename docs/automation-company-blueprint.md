# Automation Company Blueprint

## 1. The idea

An AI-driven engineering company that turns manual production businesses into automated ones.

A customer uploads their space, process, software flow and financials. Within about 48 hours we deliver a verified, priced, laid-out automation plan with before-and-after margins. We then buy the equipment, coordinate installation and run the software layer. Later we install with our own crews, and eventually we acquire manual businesses, automate them and sell them.

**The core asset is data, not a model.** The winner is whoever has the largest, cleanest and most verified equipment dataset, plus predicted-versus-actual results from real installs, behind an AI system that can reason over it under physical constraints.

**Beachhead:** custom apparel. Expand only into verticals where the data pack is built.

---

## 2. Customer flow

1. **Intake** (customer app, about 1–2 hours) plus a 30-minute engineer call.
2. **Current-state model.** Build a digital twin of the business as it runs today. It must reproduce last month's real output within about 10%, or the input data gets fixed first.
3. **Design sprint** (about 48 hours, AI-heavy). Produce three options:
   - **Bolt-on:** the fastest payback.
   - **Rebuild:** the main bottlenecks automated.
   - **Lights-sparse:** a staffed day shift and unattended nights.
4. **Plan delivery.** The plan includes:
   - a 3D layout in their scanned space;
   - a bill of materials with real, dated prices;
   - simulated throughput;
   - the before/after P&L, payback and scalability;
   - a risk list;
   - the integration and safety specs.
5. **Purchase.** We source and buy everything, through dealer accounts and financing partners.
6. **Install.** Equipment makers install their own machines. Partner integrators do conveyors, guarding and wiring. We do software and commissioning. Later, our own crews do it all.
7. **Operate.** A monitoring and orchestration subscription. Installed-line data feeds back into the system.

All plans are marked preliminary until a licensed engineer or integrator signs off.

---

## 3. Customer capture app

**Must capture:**
- **3D scan of the space.** Phone LiDAR, guided walk-through and auto-check for coverage. Target 1–3 cm accuracy; critical dimensions get confirmed on site.
- **Station videos.** Guided recording per station: several full cycles, one changeover, and one error or reprint. The app checks lighting, framing and duration.
- **Equipment list.** Photo of each machine and its nameplate; make, model and serial are auto-read by OCR.
- **Software flow.** A screen recording of one order going from store to art to production ticket to shipping. Plus OAuth connectors or exports from Shopify, Printavo, DecoNetwork, QuickBooks and similar.
- **Order history.** 12 months minimum: SKU mix, quantities, due dates, rushes and seasonality.
- **Financials.** P&L, staff list with wages, hours and burden; rent, utilities and consumables costs.
- **Facility.** Electrical panel photos (voltage, phase, amps), compressed air, ceiling height, door sizes, floor type and loading dock.
- **Goals.** Budget, financing appetite, growth target and constraints.

**Optional:** a 1–2 week sensor kit (cheap cameras plus clamp-on current sensors) for real cycle-time distributions and machine uptime.

**App requirements:**
- iOS-first (LiDAR), with a web portal for documents and connectors.
- Offline capture with resumable uploads.
- A completeness score, so the customer can't submit gaps.
- End-to-end encryption and per-customer data isolation.
- NDA and data-use terms accepted in-app.

---

## 4. Data engine (the core of the company)

### 4.1 Sources

| Channel | What it gets |
|---|---|
| Official APIs and feeds | Distributors (Digi-Key, Mouser, Nexar), blank suppliers (S&S, PromoStandards suppliers), Vention, CAD libraries under contract, manufacturer digital nameplates |
| Chinese marketplaces | Alibaba.com open platform; the 1688 API (requires a Chinese legal entity, so set up a China subsidiary or partner) |
| Customs records | Panjiva, ImportGenius, ImportYeti: which factories actually ship which machines to which US buyers. Finds suppliers that barely exist online. |
| Public web crawl | Manufacturer sites, spec PDFs, manuals, trade-show exhibitor lists, demo videos. Logged-out public pages only. No bypassing logins or anti-bot systems; get legal sign-off on crawl policy. |
| Dealer and partner accounts | OEM dealer price books and portals; integrator partners share past quotes in exchange for project flow |
| **RFQ engine** | Automatically sends structured quote requests to 10–50 suppliers per need, by email, Alibaba messaging and WeChat (through China agents). The LLM parses the replies. **Most of the real price, lead-time and minimum-order data will come from here.** |
| China sourcing team | WeChat-only vendors, factory video audits, third-party inspections (QIMA/SGS), samples |
| Test lab | Measured throughput, reliability and failure modes |
| Installed lines | Real performance, uptime and cost: the ground truth |

### 4.2 Schema: capability plus interfaces, not a product list

- **Capability:** what a station does, for example "press a DTF transfer onto a flat garment" or "move a 20 kg tote 30 m."
- **Product:** the model, with typed specs in normalized units:
  - throughput, cycle time, payload, reach and accuracy;
  - footprint, service clearance, weight and floor load;
  - power (voltage, phase, amps), compressed air, exhaust and HVAC;
  - communication protocols (OPC UA, Modbus, digital I/O, API), safety ratings, UL/CE certification;
  - maintenance intervals, consumables and US service availability.
- **Interface:** what goes in and what comes out: material form, size range, orientation, rate and signals. Lines mesh only when station A's output matches station B's input.
- **Offer:** price, date, shipping terms, minimum order, lead time, landed cost with tariffs, and the supplier. One product has many offers.
- **Evidence:** the source document, page and date for every value, with a trust tier:
  1. vendor claim
  2. third party
  3. measured by us
  4. field-proven
- **Supplier:** location, history, inspection results and risk flags (forced-labor import rules (UFLPA), sanctions, tariff exposure).
- **Entity resolution:** merge white-labeled duplicates (the same Chinese machine sold under many brands) using images, matching specs and factory addresses from customs data.

Use ECLASS and the Asset Administration Shell standard as the backbone where they exist; extend them for each vertical.

### 4.3 Pipeline

1. **Ingest:** raw files (PDFs, pages, quotes, videos) go into storage with a timestamp and source.
2. **Extract:** LLM extraction into typed fields.
3. **Validate:** physics and plausibility checks, for example payload versus machine weight, or power versus throughput.
4. **Resolve duplicates and score trust.**
5. **Human QA on a sample;** extraction error rates are tracked per source.
6. **Refresh** on a schedule per field:
   - stock: hourly to daily
   - prices: weekly
   - specs: quarterly
   - tariffs and regulations: on change

Missing data never blocks a plan. It triggers RFQs, and the item is flagged "quote pending."

### 4.4 New vertical onboarding

1. Research agents build a vertical pack: process steps, equipment categories, vendors (including from customs data), standards and regulations, and recent research.
2. A paid industry expert reviews it for 1–2 weeks.
3. Bulk-load the database, run the first RFQ round, and test-buy key machines.
4. Assemble a benchmark of 20–50 reference plants for the vertical.

---

## 5. AI system

### 5.1 Principle

The LLM reasons and coordinates. **Every number comes from the database, a solver or a simulation, never from the model's memory.** Every plan is verified before a human sees it.

### 5.2 Layers

| Layer | What it is |
|---|---|
| Orchestration | Frontier models (Claude, GPT, Gemini) behind a model-agnostic layer. The best model per task is chosen by our private benchmark, and re-run on every new model release. |
| Local / private models | Open-weight LLMs and vision models in our own cloud or the customer's, for sensitive raw video and CAD. Only abstracted specs go to external APIs. Check each provider's retention terms; some top-tier models retain data. |
| Perception | Machine and nameplate recognition from photos; station and action recognition from video (cycle timing); 3D scan segmentation (walls, columns, doors, existing equipment) |
| Plant model | One structured representation of the customer's business: geometry, utilities, process graph, demand, labor, finances and constraints. Every tool reads and writes it. |
| Engineering tools | Constraint filtering over the database; layout solver; discrete-event simulation (SimPy or Plant Simulation); robot reach and cycle simulation (Isaac Sim or RoboDK); code-based CAD; cost and financial models |
| Verification | Physics and constraint checks, simulation-in-the-loop, and reviewer agents (safety, cost, maintainability, buildability), followed by sign-off from a human engineer |

### 5.3 How the planner works

1. **Decompose** the customer's process into tasks, using the plant model.
2. **Map** each task to capabilities.
3. **Generate many candidate line architectures:** different processes (for example DTF versus screen), different levels of automation, and different equipment combinations.
4. **Prune** candidates on hard constraints:
   - fit in the 3D space, including the delivery path and door widths;
   - utilities and floor load;
   - interface matching between stations;
   - safety;
   - budget.
5. **Simulate the survivors** against the customer's real order history, including rush jobs, product-mix swings and breakdowns.
6. **Optimize** layout and buffers, trading off total cost of ownership, throughput, payback, risk, lead time and flexibility.
7. **Critique.** Reviewer agents attack each plan, and plans are revised and re-simulated.
8. **Explain.** The output is three options with clear tradeoffs, every number linked to its source.

Default rule: **automate bottlenecks first and never over-automate.** High-mix shops get flexibility stress tests, the lesson from Tesla's 2018 over-automation and Adidas' Speedfactory.

### 5.4 Custom models: what we train, and when

**Not built:** a custom manufacturing LLM pretrained from scratch. General frontier models have beaten domain-trained LLMs on open-ended reasoning.

| When | Train |
|---|---|
| Day 1 | Nothing. Prompts, retrieval over our data, tools, and the benchmark. |
| After hundreds of capture sessions | Perception models: machine recognition and station timing from video. Fine-tuned open models running locally. |
| After thousands of documents and quotes | A cheap extraction model distilled from frontier-model outputs; price and lead-time estimators |
| After dozens to hundreds of installs | Cost, cycle-time and uptime predictors trained on predicted-versus-actual data; a ranker trained on engineer choices plus outcomes |
| Once the benchmark proves a gain | Reinforcement fine-tuning of the planner on graded plans |
| Own robot cells | Fine-tune open robotics foundation models (π0, GR00T family) on our own cell data. Don't build these from scratch. |

These volume thresholds are working heuristics, not proven figures. The test for every custom model is the same: it ships only if it beats the frontier baseline on our private benchmark.

---

## 6. 3D modeling and physical constraints

- **Space:** the phone scan becomes a mesh, which is segmented into a simplified building model: walls, columns, doors, ceiling, drains, panels and air drops.
- **Equipment:** vendor STEP/CAD files where available, otherwise parametric envelopes (footprint, height, clearance, service zones).
- **Scene:** everything is assembled in OpenUSD (Omniverse / Isaac Sim) for:
  - layout;
  - robot reach and collision checks;
  - mobile-robot paths;
  - safety zones;
  - a walk-through render for the customer.
- **Hard checks:**
  - aisle widths, egress and fire code;
  - floor load and power per drop;
  - air and exhaust;
  - ISO 13855 separation distances;
  - the install path, so the machine fits through the door.
- **Final layouts** are field-verified before purchase.

---

## 7. Integration architecture (what we install)

- **Data backbone:** a Unified Namespace: an MQTT broker with Sparkplug B payloads, organized by the ISA-95 hierarchy (enterprise, site, area, line, cell).
- **Machine layer:**
  - OPC UA (robotics and vision companion specs) wherever available;
  - PackML for standard machine states;
  - MTConnect or I/O adapters for legacy machines;
  - VDA 5050 / MassRobotics for mobile robots.
- **Integration tier per machine:**
  1. native API
  2. protocol adapter
  3. I/O tap
  4. vision monitoring
  5. manual step left in place
- **Software flow:** storefront → order system → our MES/orchestrator → machine job tickets (print software, embroidery files, hot folders) → robot transport → QC by vision → pack and ship. The automation plan specifies all of it.
- **Lights-out readiness:**
  - remote monitoring and alerting;
  - automatic reorder of consumables and blanks;
  - exception queues;
  - predictive maintenance;
  - restart procedures.
- **Safety:**
  - ISO 10218-1/-2:2025 and ANSI/A3 R15.06;
  - ISO 13849 performance levels and ISO 12100 risk assessment;
  - NFPA 79 / UL 508A for electrical;
  - lockout/tagout;
  - OSHA 1910.212.
  - Final safety design is done by licensed engineers and partner integrators.

---

## 8. Physical testing lab

- **Purpose:** turn vendor claims into measured data, and validate whole line configurations before customers buy them.
- **Setup:** a warehouse with the top candidate machines for each vertical, bought new, used or at auction.
- **Standard test protocols:**
  - throughput at real product mix;
  - changeover time;
  - first-pass yield;
  - failure modes and mean time between failures;
  - power and air consumption;
  - noise;
  - ease of integration.
- **Reference lines:** fully assembled reference lines run continuously as the proof of uptime and as the sales demo.
- **Gap engineering, later:** build our own cells only where no product exists (for example garment-to-pallet loading), after the core business works.
- **Data:** every result goes into the database as trust tier 3, "measured by us."

---

## 9. Business model and phases

| Phase | Offer | Revenue |
|---|---|---|
| 1. Software | Automation plans for owners, plus automation-upside diligence reports for buyers of manufacturers (PE firms, search funds) | Plan fees, credited toward the build |
| 2. Procurement and install | We buy the equipment (dealer margin), arrange financing, and coordinate OEM and integrator installs | Hardware margin, project fees |
| 3. Operate | Monitoring and orchestration software; rental of our own robot cells | Recurring subscription |
| 4. Own crews | In-house install and commissioning teams | Full project margin |
| 5. Capital | Acquire manual businesses, automate them with our playbook, hold or sell. Start deal by deal, then raise a fund. | Equity returns |

**Install partners:** use equipment-maker install teams plus regional integrators until we have our own crews. Robot-rental companies (Formic, RobCo) only deploy their own narrow applications, so they are not general install partners.

---

## 10. Team

- **Automation and controls engineers** with integrator backgrounds, plus licensed PEs.
- **Industrial engineers:** simulation, layout and lean.
- **Functional-safety lead.**
- **Data operations:** extraction QA, entity resolution, freshness. This is the largest team.
- **Crawling and data engineering.**
- **China sourcing agents** in Shenzhen, Guangzhou and Yiwu.
- **RFQ / procurement operations.**
- **ML and agent engineering:** orchestration, the benchmark, and perception and local models.
- **3D and simulation engineers:** OpenUSD, Isaac Sim, RoboDK.
- **Mobile and app engineers:** capture app, connectors.
- **Test-lab technicians and field deployment crew.**
- **Industry operators** from each vertical (for example former print-shop plant managers).
- **Partnerships:** equipment makers, dealers, integrators, financing.
- **Later:** M&A and portfolio operations.

---

## 11. Roadmap

| Window | Build | Proof point |
|---|---|---|
| 0–6 months | Schema; apparel vertical pack; capture app v1; RFQ engine; current-state twin; first test lab; plans done mostly by hand for 5–10 shops | Twin matches real output within 10%; engineers rate the plans as good as a paid study |
| 6–18 months | 48-hour automated sprint; dealer and financing partners; first installs; customs-data and 1688 pipelines; perception models v1 | 30+ paid plans; 25%+ convert to installs; installs hit predicted payback |
| 18–36 months | Own install crews; orchestration subscription; 2–3 new verticals; trained estimators | Predicted versus actual capex and cycle time within ±15% |
| 36+ months | First acquisitions; fund; reinforcement fine-tuned planner; own robot cells | Acquired plants show the margin lift the plans predicted |

---

## 12. Metrics

- **Predicted-versus-actual error** on capex, throughput and payback. This is the master metric.
- **Share of plan numbers with a sourced, dated record.** Target 100%.
- **Database coverage and freshness** per vertical.
- **RFQ response rate and turnaround.**
- **Time from capture to plan.** Target 48 hours.
- **Conversion:** plans to installs.
- **Customer payback, achieved versus promised.**
- **Unattended hours per week** in installed lines.
- **Private benchmark score** per model release.

---

## 13. Key risks

| Risk | Mitigation |
|---|---|
| Wrong plans, leading to liability | Every number sourced; simulation and verification; "preliminary" labeling; PE sign-off; errors-and-omissions insurance |
| Thin or stale data | Eight data channels, with RFQs and the test lab as the backstop; per-field freshness rules |
| Scraping or legal exposure | Logged-out public data only; licensed feeds; dealer accounts; legal review |
| Over-automation | Bottleneck-first rule; flexibility stress tests; staged options |
| Customer data sensitivity | Local and private models for raw data; encryption; data-use terms |
| Tariffs, lead times, supply shocks | Landed-cost engine; second sources; lead-time-aware planning |
| Competitors widen scope (Robotiq IQ, Vention, integrators, RaaS) | Vendor neutrality; the full facility plus purchase plus install loop; outcome data |
| Model churn | Model-agnostic orchestration; benchmark-gated model choices |
