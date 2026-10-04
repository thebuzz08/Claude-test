# Data Intake Spec and Integration/Controls Architecture for an AI Dark-Factory Automation Planner

Scope: (a) what data an AI planning service has to collect from a manufacturing business (example: a custom apparel shop) to produce a credible automation plan, and which of it can be captured automatically; (b) how mixed machines, robots and software are tied together into a working lights-out factory: architecture, controls, legacy interfacing, safety and commissioning. Current as of 4 Oct 2026. US-focused, with EU notes.

Note on sourcing: several primary pages (controleng.com, automate.org) returned HTTP 403 when fetched, so some findings rest on search-result snippets of those pages. They are marked "(snippet)". Inferences marked "practitioner knowledge" come from general engineering practice and have no source in this session. Treat them as unverified.

---

## Q1. What data do automation engineers and integrators collect during feasibility/discovery?

### Takeaway
Integrators want the same core set every time. Process and time data: process maps/VSM, cycle time per step, takt, OEE, labor hours. Demand data: SKU mix, order profile, seasonality, changeovers. Physical-site data: floor plan, utilities, ceiling, floor loading. An equipment and IT/OT inventory. Quality data. Financial and safety constraints. Integrators also say that interviews and pulling in every department matter as much as the numbers.

### Cited Findings
- Control Engineering's "Best practices for effective automation applications, Part 1: data collection" (by integrator E Tech Group) recommends a full data-collection run for initial project design: personnel interviews, IT/OT risk assessments, equipment mapping, and input from every relevant department. (snippet; full page 403) — [Control Engineering](https://www.controleng.com/best-practices-for-effective-automation-applications-part-1-automation-effectiveness-through-data-collection); [E Tech Group repost](https://etechgroup.com/blog/uncategorized/best-practices-for-effective-automation-applications)
- Integrator feasibility services (e.g., DiFACTO Robotics on A3's integrator directory) list process analysis and cycle-time evaluation; labor, throughput and quality impact modeling; and capital cost and payback analysis as core feasibility deliverables. (snippet) — [A3 / DiFACTO](https://www.automate.org/system-integration/difacto-robotics-america-llc/automation-feasibility-and-roi-analysis)
- Feasibility checklists cover technical feasibility, cost considerations, process complexity and business objectives. — [checklist.gg](https://checklist.gg/templates/automation-feasibility-checklist)
- UNS/IIoT rollouts depend heavily on "asset documentation maturity, network complexity, and personnel availability". The equipment/asset inventory and network survey are therefore preconditions for estimating the integration timeline (Litmus, 26 Aug 2026). — [Litmus](https://litmus.io/blog/how-to-build-a-unified-namespace-architecture-timeline-and-failure-modes)
- Retrofitted machine data lets manufacturers calculate true OEE and expose hidden losses such as micro-stops, speed degradation and quality issues. Baseline OEE/downtime should therefore be measured, not estimated from interviews. — [ShopLogix](https://shoplogix.com/blog/retrofitting-sensors-for-machine-monitoring-modernize-without-replacement/)

### Inferences
- Proposed intake schema (practitioner knowledge, synthesized from the above plus standard Lean/integrator practice):
  1. **Business and demand:** order history (12–24 months, line-item level), SKUs and variants (garment blank × color × size × decoration method × locations), order-size distribution (share of 1-unit orders vs. bulk), seasonality and peak-week multiplier, promised lead times/SLA, growth forecast, price/margin per order class.
  2. **Process:** SIPOC, step-by-step process map/VSM including WIP queues, cycle time per step with distribution (not just the mean), takt from demand, changeover/setup time and frequency (screen setup, hooping, pretreat, DTF film), first-pass yield and defect Pareto per step, rework loops, labor hours and headcount per step and shift.
  3. **Equipment inventory:** make/model/serial/year per machine; control interface (none / I/O / RS-232 / Ethernet / OPC UA / vendor API / hot-folder); job-input method (USB, RIP queue, DST file); consumables and refill cadence; MTBF/MTTR history; maintenance contracts.
  4. **Facility:** dimensioned floor plan and 3D scan, column grid, aisle widths, door sizes, ceiling clear height, floor flatness and load rating (AMRs need it), power (voltage, phases, panel capacity), compressed air (CFM/psi), HVAC/humidity (affects pretreat and ink curing), dryer exhaust, network/Wi-Fi coverage, fire code.
  5. **IT/OT systems:** e-commerce (Shopify etc.), order/production software (Printavo, ShopVOX, DecoNetwork, OMS), ERP/accounting, shipping software, available API keys, artwork file formats and storage.
  6. **Quality/compliance:** inspection criteria, color tolerance, return reasons, OSHA log, chemical SDSs (pretreat, inks), insurance constraints.
  7. **Finance/strategy:** budget, ROI hurdle/payback target, labor cost fully burdened, labor availability/turnover, appetite for leasing/RaaS, timeline, which tasks must stay human.
- The biggest risk for an AI planner is variability data. Mean cycle times hide the long-tail SKUs and exceptions that break lights-out operation, so the intake should capture distributions and the exception log.

### Gaps
- I could not retrieve the full Control Engineering / E Tech Group checklist (403), and I found no published, standardized integrator discovery template (from CSIA or A3) to cite verbatim.
- No source found with apparel-decoration-specific discovery data requirements.

---

## Q2. Which data can be captured automatically, and how accurate is each method?

### Takeaway
Phone LiDAR (Polycam) and Matterport give floor plans to about 1–3 cm, good enough for layout concepts but not for final robot-cell or rack anchoring. Clamp-on current sensors and hardware adapters give machine run/idle/off state and OEE within hours to days, without touching the machine controls. Video action recognition can automate parts of time study on repetitive stations. API connectors can pull order history, but apparel-shop software API depth varies and is poorly documented publicly.

### Cited Findings
- **Phone LiDAR / photogrammetry:** Polycam states standard accuracy of ±½ inch (~1.3 cm) on standard interior captures. — [Polycam help center](https://learn.poly.cam/hc/en-us/articles/50434745985556-How-Accurate-Are-Polycam-Scans)
- iPhone-based floor plans are accurate to roughly 1–3 cm in normal interiors; accuracy depends on scan mode, lighting and clutter (vendor comparison, so potentially biased). — [Polycam blog](https://poly.cam/blog/best-floor-plan-software-compared-accuracy-speed-and-cost-for-every-budget)
- A 2023 community benchmark found Matterport Pro2 measurements matched a hand laser survey with no deviation, but it took the longest (50 min for the test area). A 360-camera (Ricoh Theta Z1) workflow averaged 1.47% deviation but needed only ~17 min. (forum benchmark, not peer reviewed) — [We Get Around Network](https://wegetaroundnetwork.com/topic/19262/benchmarking-floor-plans-matterport-zillow-cubicasa-and-urbanimmersive)
- AEC Magazine has reviewed Polycam for architecture/engineering/construction reality capture. — [AEC Magazine](https://aecmag.com/reality-capture-modelling/polycam-for-aec/)
- **Video-based time study / action recognition:** Drishti streams video from every station and uses AI action recognition to convert it into cycle data. In high-volume lines it can recognize the start and end of every cycle, and it revealed slowdowns at stations that were not the original focus. — [IndustryWeek](https://www.industryweek.com/technology-and-iiot/article/21124036/ai-based-action-recognition-technology-reaps-rewards)
- Academic work (MDPI Applied Sciences 2024; FSB Zagreb thesis) treats automated action detection as a remedy for the shortcomings of manual stopwatch/video time study. EuroHPC funds work on video-language models for time study and value analysis. — [MDPI](https://www.mdpi.com/2076-3417/14/3/1185); [EuroHPC](https://www.eurohpc-ju.europa.eu/developing-video-based-language-models-time-study-and-value-analysis-manufacturing_en)
- **IoT retrofit sensors:** CT (current transformer) clamps wrap around a power cable and read current without breaking the circuit. Non-invasive sensing can retrofit equipment "in minutes, not months". Optical sensors and computer vision are alternatives that also avoid touching the controller. — [Fabrico 2026 review](https://www.fabrico.io/blog/best-oee-software-legacy-equipment-retrofit-2026-review); [Guidewheel](https://www.guidewheel.com/blog/machine-monitoring-without-it-no-plc); [PulsarML](https://www.pulsarml.com/en/blog/machine-connectivity-legacy-equipment-no-plc)
- **Connector extraction (apparel):** DecoNetwork has an API and integrations with third parties (e.g., Zoho CRM, Wilcom embroidery software, Corel), plus blank-apparel supplier integrations and automated pricing. — [Software Advice](https://www.softwareadvice.com.au/software/123334/deconetwork); [DecoNetwork store builder](https://www.deconetwork.com/store-builder/)
- KornitX has a Shopify app (seller portal) that publishes products to Shopify stores and routes orders to fulfillment. — [Shopify App Store](https://apps.shopify.com/kornit-x-seller-portal)

### Inferences
- Accuracy tiering for the planner (practitioner knowledge): phone LiDAR (±1–3 cm) is fine for layout concept, AMR route feasibility and equipment footprint. Final cell design, fencing/scanner zones and conveyor elevations should be confirmed with a laser survey or terrestrial scanner. Ceiling and overhead obstructions (sprinklers, ducts) are often missed by quick scans.
- Current clamps give machine state (run/idle/off) and cycle counts from current signatures, but not job ID, SKU or quality. Pairing them with order-system timestamps is needed to get per-SKU cycle times.
- Video action recognition works best for repetitive, fixed-station tasks. High-mix apparel tasks (loading garments on platens, folding, bagging) are less structured, so expect lower accuracy and a need for labeled training data. Privacy and labor-relations issues require consent.
- Order data (Shopify Orders API, decoration-shop software) is the most reliable automatic source for demand profile, SKU mix and seasonality. It is usually the first connector to build.

### Gaps
- No peer-reviewed accuracy figures (e.g., % cycle-time error vs. stopwatch) were found for commercial video time-study tools.
- I could not verify the public API scope of Printavo, ShopVOX or Odoo/NetSuite for production-step timestamps. Search returned only freelancer listings. Check the vendors' developer docs directly.
- No source found on how accurate current-signature analysis is at inferring cycle counts on garment printers, heat presses or embroidery machines.

---

## Q3. Standard frameworks: readiness assessments, work measurement, ROI

### Takeaway
Use SIRI (16 dimensions × 6 bands) or the acatech Industrie 4.0 Maturity Index (6 stages, Computerisation → Adaptability) to score digital readiness. Use VSM for flow. Use MTM/MOST to estimate manual times where video or sensors are unavailable. These methods trade accuracy against effort.

### Cited Findings
- **SIRI (Singapore EDB):** three building blocks (Process, Technology, Organisation) and 8 pillars map onto 16 assessment dimensions, each scored in 6 progressive maturity bands. — [Singapore EDB](https://www.edb.gov.sg/en/news-and-resources/news/advanced-manufacturing-release.html); [Yokogawa-hosted SIRI white paper](https://web-material3.yokogawa.com/26/32928/tabs/The-smart-industry-readiness-index.pdf)
- **acatech Industrie 4.0 Maturity Index** (update 2020): six stages. Computerisation (isolated IT), Connectivity, Visibility (real-time sensor data, a "digital shadow"), Transparency (understanding why), Predictive Capacity, Adaptability (autonomous real-time optimization). — [acatech](https://en.acatech.de/publication/industrie-4-0-maturity-index-update-2020/download-pdf?lang=en); [RCR Wireless](https://rcrwireless.com/?p=216867)
- **MTM vs MOST:** BasicMOST uses TMUs like MTM but replaces MTM's 19 basic motions with 3 movement sequences, so analysis is much faster. Motions are recorded in tens of TMUs (MiniMOST: single TMUs; MaxiMOST: hundreds). — [Wikipedia: MOST](https://en.wikipedia.org/wiki/Maynard_operation_sequence_technique); [IMEKO comparison](https://imeko.org/index.php/proceedings/8389-comprehensive-comparison-of-mtm-and-basicmost-as-the-most-widely-applied-pmts-analysis-methods)
- Reported analysis effort and accuracy: MTM-1 about 250× cycle time to analyze; MTM-2 about 100×; MTM-3 about 35×. The accuracy figures in the snippet (±21%/±40%/±7%) look internally inconsistent: finer systems should be more accurate. Do not use them without checking the IMEKO paper directly. — [IMEKO TC10 2020 paper](https://imeko.info/publications/tc10-2020/IMEKO-TC10-2020-058.pdf)
- In one packaging study, MTM gave 9.10 s/unit and MOST gave 8.26 s/unit for the same task, roughly a 10% gap between methods. — [DOAJ / Industria journal 2015](https://doaj.org/article/a986937fdbc14a30b5043d4173166d1e)

### Inferences
- An AI planner could use SIRI/acatech-style scoring as the "readiness" output and VSM/takt as the "process" output. It could use MOST-style synthetic times as a fallback for steps it cannot observe, flagged ±10–20% uncertainty.
- ROI model (practitioner knowledge): include capex (equipment, integration typically comparable to or larger than hardware cost, safety, facility mods), opex (maintenance, software subscriptions, consumables, energy), labor savings at fully burdened rates across shifts (lights-out value comes mostly from 2nd/3rd-shift capacity), quality/rework savings, throughput/lead-time revenue, and a ramp-up curve (not day-one nameplate output). Report payback, NPV and IRR with sensitivity on volume.

### Gaps
- I did not retrieve A3's own automation ROI guidance or a published robot ROI calculator methodology to cite.
- Lean/VSM basics are standard but not sourced here.

---

## Q4. Reference integration architectures and interoperability standards

### Takeaway
The current consensus architecture has two parts. ISA-95 is the semantic hierarchy (enterprise/site/area/line/cell/device). A Unified Namespace (an MQTT broker plus Sparkplug B, now ISO/IEC 20237) serves as the event hub that replaces point-to-point links. Below it, OPC UA with companion specs (Robotics VDMA 40010, Vision 40100), MTConnect for machine tools, and PackML (ANSI/ISA-TR88.00.02-2022) standardize machine state and data. Mobile robots use VDA 5050 (v3.0.0, adopted Feb 2026) and/or the MassRobotics interoperability standard. Asset Administration Shell (IEC 63278-1:2023) and AutomationML (IEC 62714) standardize digital twins and engineering data.

### Cited Findings
- **UNS = MQTT + Sparkplug B + ISA-95.** MQTT is the lightweight pub/sub transport. Sparkplug B standardizes payloads (metrics, timestamps, data types, metadata) and adds birth/death certificates so applications know device state without polling. ISA-95 structures the topic hierarchy. — [Litmus (26 Aug 2026)](https://litmus.io/blog/how-to-build-a-unified-namespace-architecture-timeline-and-failure-modes); [HiveMQ](https://hivemq.com/resources/smart-manufacturing-using-isa95-mqtt-sparkplug-and-uns)
- UNS turns point-to-point "spaghetti" integrations into hub-and-spoke, with every system publishing and subscribing to a central broker. — [TeepTrak](https://teeptrak.com/en/unified-namespace-uns-mqtt-sparkplug-iiot-2027/)
- Litmus topic structure: enterprise/site/area/line/cell/device/metric. UNS is a semantic layer above existing PLC/SCADA/MES/ERP, not a replacement. Timeline: pilot 6–12 weeks, initial production 8–16 weeks, full scale 12–24 weeks; total 3–12 months, most projects 6–9 months. Five failure modes: governance gaps (no naming standards), scope creep, treating UNS as a SCADA/MES replacement, under-planned network segmentation/firewalls, and part-time staffing. — [Litmus](https://litmus.io/blog/how-to-build-a-unified-namespace-architecture-timeline-and-failure-modes)
- **Sparkplug 3.0** was published as international standard **ISO/IEC 20237** through the JTC 1 PAS fast-track. The Eclipse Foundation keeps stewardship. v3.0 clarified v2.2 ambiguities and added normative statements while staying backward compatible. — [Eclipse Foundation newsroom](https://newsroom.eclipse.org/node/39754); [ARC Advisory](https://www.arcweb.com/blog/sparkplug-now-official-isoiec-standard)
- **OPC UA Robotics companion spec** is VDMA 40010 (first released at automatica 2018). It gives a manufacturer-independent information model for robot data. Part 1 covers asset management, condition monitoring, preventive maintenance and vertical integration, which supports analytics and OEE. OPC UA Machine Vision is VDMA 40100. — [OPC Foundation press release](https://opcfoundation.org/news/press-releases/vdma-releases-opc-ua-companion-specifications-robotics-machine-vision/); [OPC 40100 reference](https://reference.opcfoundation.org/specs/OPC-40100-2/full)
- **MTConnect** is an open, royalty-free standard for interoperability between manufacturing devices and software. Hardware adapters (e.g., Memex Ax760-MTC) convert legacy FANUC I/O Link signals to MTConnect. — [Memex](https://memex.ca/?p=5263); [Fabrico](https://www.fabrico.io/blog/best-oee-software-legacy-equipment-retrofit-2026-review)
- **PackML:** ANSI/ISA-TR88.00.02-2022 is the current version. Changes include a revised state model diagram, removal of the "Remote" interface, and new PackTags that describe machine configuration to supervisory systems. PackTags standardize names for machine state, commands and data. Developed by the OMAC Packaging Workgroup. — [Control Engineering](https://www.controleng.com/articles/updated-packml-standard-released/); [Schneider Electric PackML state model](https://product-help.schneider-electric.com/Machine%20Expert/V2.2/en/PackMLli/PackMLli/TPC_PackMLli_FB_UnitModeManager2_StateModel.html)
- **VDA 5050 v3.0.0** was formally adopted by VDMA and VDA on 17 Feb 2026 (release March 2026). It now covers all mobile robot types, including AMRs (earlier versions were AGV-centric), after 3 years, 32 workshops and 243+ pull requests. — [idealworks](https://idealworks.com/en/news/vda5050-300-release-march-2026)
- VDA 5050 aims to let mixed-vendor AGVs/AMRs run under one master fleet controller, which sends orders and receives state. The MassRobotics AMR Interoperability Standard (US) focuses on sharing basic status/location data among fleets. The two do not conflict, and a robot can implement both. — [MiR](https://mobile-industrial-robots.com/blog/5-questions-and-answers-about-interoperability-of-amrs); [Robotics 24/7](https://robotics247.com/article/what_is_massrobotics_amr_interoperability_standard); [GetTransport blog](https://blog.gettransport.com/ar/trends-in-logistic/vda-5050-massrobotics-open-rmf-what-is-what-and-where-it-applies/)
- **Asset Administration Shell:** IEC 63278-1:2023 (EN IEC 63278-1:2024) defines the AAS structure, a standardized digital representation of an asset for secure information exchange between applications across the equipment hierarchy. **AutomationML** is IEC 62714, an XML-based format for exchanging engineering/planning data for production systems, and IEC 63278-1 references it. — [IEC Webstore](https://webstore.iec.ch/en/publication/65628); [arXiv 2510.00933](https://arxiv.org/pdf/2510.00933)

### Inferences
- Recommended reference stack for a planner's output (synthesis):
  - **L0–L1 (devices):** sensors, drives, robots, printers, presses, embroidery machines.
  - **L2 (control):** PLCs/robot controllers, each machine exposing a PackML-like state model through OPC UA (or a gateway).
  - **Edge:** gateway/DataOps (e.g., HighByte, Litmus, Ignition Edge) that normalizes tags into ISA-95 paths and publishes Sparkplug B to the broker.
  - **L3:** MES/WMS/fleet manager subscribing to and publishing on the UNS.
  - **L4:** ERP/e-commerce.
- Most apparel decoration equipment (DTG, DTF, embroidery, heat presses, dryers) has no OPC UA companion spec. Its integration surface is usually a RIP/hot folder or vendor cloud. The planner should therefore expect gateway/adapter work per machine.
- Use UNS for events and state. Use request/response APIs (REST/OPC UA methods) for commands that need acknowledgment, such as job dispatch.

### Gaps
- I found no evidence of an OPC UA companion specification for textile decoration, DTG or embroidery equipment. VDMA has textile-machinery OPC UA work (e.g., weaving), but I did not confirm a spec number or its applicability to apparel decoration.
- MassRobotics standard version number and 2025–2026 updates were not confirmed.
- IEC 61499 vs IEC 61131-3 adoption data not sourced (see Q5 gaps).

---

## Q5. Control layer and order-to-machine flow (PLCs, MES, WMS, apparel job tickets)

### Takeaway
For on-demand apparel, the order-to-machine backbone already exists commercially. KornitX takes Shopify orders, generates artwork, routes the order, runs factory workflow and ships it ("pixel to parcel"), driving Kornit DTG printers. DecoNetwork-style shop software handles quotes, art and production tracking. A dark factory needs a layer under these to orchestrate material handling (blanks picking, loading, curing, folding, bagging) through PLCs, robot controllers and fleet managers.

### Cited Findings
- KornitX is described as an end-to-end workflow between online stores and the production floor. Its six stages: Product Management, eCommerce Experiences, Auto-Artwork Generation, Order Routing, Fulfillment & Factory Workflow, and Product Shipping. — [KornitX "Six Stages" PDF (Sept 2021)](https://www.amayauk.com/wp-content/uploads/2021/11/KornitX-The-Six-Stages-of-On-Demand-Workflow-September-2021.pdf)
- GoCustom Clothing adopted Kornit Avalanche HD6 with the KornitX workflow platform to digitize on-demand production. — [Textile World (Oct 2021)](https://www.textileworld.com/textile-world/knitting-apparel/2021/10/gocustom-clothing-adopts-kornit-avalanche-hd6-kornitx-workflow-platform-for-digitized-production-efficiency-on-demand/)
- KornitX (formerly Custom Gateway) integrates with ERP-type systems such as MatTex for textile production digitalization. Gelato lists Kornit as a production partner. — [Textilegence](https://www.textilegence.com/en/digitalization-with-mattex-and-kornit-custom-gateway); [Gelato](https://www.gelato.com/connect/partners/kornit)
- DecoNetwork includes production-team tracking, artwork-creation monitoring and shipping through a central dashboard, and integrates with Wilcom (embroidery digitizing) and with Printavo for production management. — [Software Advice](https://www.softwareadvice.co.uk/software/123334/deconetwork)
- PackML state model and PackTags give a standard way for a supervisory system (MES/line controller) to command and monitor machines. — [Control Engineering](https://www.controleng.com/articles/updated-packml-standard-released/)

### Inferences
- Order-to-machine flow for an automated apparel factory (practitioner synthesis):
  1. Shopify/web-to-print order (webhook) goes to the OMS/production software (KornitX, DecoNetwork, Printavo, ShopVOX).
  2. MES or orchestration layer: splits orders into jobs and creates a job ticket (barcode/RFID) carrying blank SKU, print/embroidery file, placement and finishing.
  3. WMS: picks blanks from automated storage and sends a VDA 5050 order to the AMR fleet.
  4. Cell PLC/robot loads the garment onto a platen/hoop and scans the ticket. The RIP (DTG) or DST file (embroidery) is fetched by job ID through hot folder/API.
  5. Print → cure/dry → robotic unload → QC vision → fold/bag → label → ship (shipping API).
  6. Every state change is published to the UNS.
- Control hardware options (practitioner knowledge; not sourced this session): Rockwell ControlLogix/CompactLogix, Siemens S7-1500 (incl. F-safety variants), Beckhoff TwinCAT (PC-based/soft PLC), and soft PLCs such as CODESYS. IEC 61131-3 is the dominant PLC programming standard. IEC 61499 (event-driven, distributed function blocks) is used in emerging software-defined automation. MES candidates by size: Tulip (no-code apps, SMB-friendly), Plex/Rockwell, Critical Manufacturing, and open-source options.
- Garment loading onto platens/hoops and folding are the hardest steps to automate (see Q8). The planner should treat them as candidate human-in-the-loop stations.

### Gaps
- KornitX source is from 2021. I did not confirm 2025–2026 KornitX features or whether it exposes machine-level APIs to third-party MES.
- I did not source vendor docs for Tulip, Critical Manufacturing, Plex, Ignition, or IEC 61499 adoption figures.
- No public documentation found for DTG RIP hot-folder/API automation (e.g., Kornit QuickP, Epson Garment Creator) or Tajima/Barudan embroidery network job loading.

---

## Q6. Interfacing legacy machines that lack APIs

### Takeaway
Retrofit approaches, from least to most invasive: (1) clamp-on CT current sensors, optical stack-light sensors or camera-based monitoring for state/OEE. (2) Discrete I/O taps (start/stop/done signals) wired into a PLC or edge gateway. (3) Protocol hardware adapters (e.g., FANUC I/O Link to MTConnect). (4) Physical "robot as operator" approaches such as button pressing or HMI vision, as a last resort.

### Cited Findings
- IIoT retrofitting adds connectivity to existing machines through external sensors, edge gateways and signal taps instead of replacing equipment. — [Alumio](https://wordpress.alumio.com/?p=10577)
- Non-invasive tools (optical sensors, current clamps, computer vision) read the machine "without touching its brain". CT clamps read current without breaking the circuit. — [Fabrico](https://www.fabrico.io/blog/best-oee-software-legacy-equipment-retrofit-2026-review)
- Hardware adapters such as the Memex Ax760-MTC connect to the FANUC I/O Link bus and translate signals to MTConnect without disrupting the machine. — [Memex](https://memex.ca/?p=5263)
- Legacy machines with no PLC can be monitored by clamping on sensors and collecting data immediately. — [PulsarML](https://www.pulsarml.com/en/blog/machine-connectivity-legacy-equipment-no-plc); [Guidewheel](https://www.guidewheel.com/blog/machine-monitoring-without-it-no-plc)

### Inferences
- Monitoring retrofits give observability but not control. For a dark factory, each machine also needs a command path: a remote start input, a job-file path (hot folder), and done/fault outputs. Where the OEM will not provide this, options are OEM-sanctioned I/O kits, wiring through dry contacts on the panel (which may void warranty or require re-certification under NFPA 79/UL 508A), or a cobot actuating the HMI with a vision check. The last is brittle, and the planner should flag it as high-risk.
- The planner should rate each machine on an "integration tier" (Native API/OPC UA → Vendor cloud/hot-folder → I/O only → Monitoring only → Replace). That tier drives the capex split between replace and retrofit.

### Gaps
- No sources found on robotic button-pressing/HMI-vision retrofits in production use, or their reliability.
- No source on warranty/certification implications of I/O retrofits on DTG/embroidery machines.

---

## Q7. Safety architecture and regulation (US + EU)

### Takeaway
The robot safety landscape changed in 2025. ISO 10218-1/-2:2025 was published in February 2025 and absorbed ISO/TS 15066, making "collaborative" a property of the application, not the robot. It added robot classes, functional-safety requirements and cybersecurity. ANSI/A3 R15.06 was revised to match. In the US, OSHA has no robot-specific standard and enforces 1910.212 machine guarding plus the General Duty Clause, using consensus standards as evidence. In the EU, Machinery Regulation (EU) 2023/1230 applies from 20 Jan 2027 with no transition period and adds software, AI and cybersecurity requirements.

### Cited Findings
- ISO 10218-1:2025 and 10218-2:2025 were published in February 2025, the first major revision since 2011. — [A3](https://www.automate.org/robotics/news/updated-iso-10218-major-advancements-in-industrial-robot-safety-standards-now-available/aph); [Control Engineering](https://www.controleng.com/revised-industrial-robot-safety-standards-now-available/)
- ISO/TS 15066:2016 no longer stands alone. Its power-and-force-limiting and collaborative-application requirements were folded into ISO 10218, and "collaborative" is now a property of the application, not the robot. — [EVS Int (Apr 2026)](https://www.evsint.com/industrial-robot-safety-standards-iso-10218-ce-marking-2026/); [EVS Int cobot article](https://www.evsint.com/?p=9433)
- The 2025 revision adds robot classifications with matching functional-safety requirements, safety-related cybersecurity requirements, and end-effector guidance from ISO/TR 20218-1/-2. Part 1 grew from 50 to 95 pages; Part 2 from 72 to 223 pages. (secondary source) — [There's a Robot for That](https://theresarobotforthat.com/?p=1011); [A3](https://www.automate.org/robotics/news/updated-iso-10218-major-advancements-in-industrial-robot-safety-standards-now-available/aph)
- ANSI/A3 published a revised R15.06 industrial robot safety standard (US national adoption aligned to ISO 10218:2025). (snippet; pages 403) — [A3: ANSI/A3 publish revised R15.06](https://www.automate.org/robotics/industry-insights/ansi-a3-publish-revised-r15-06-industrial-robot-safety-standard/aph)
- OSHA: robots are machines and must be safeguarded like any hazardous remotely controlled machine. 29 CFR 1910.212 (General requirements for all machines) is the standard usually cited, regulating by hazard and motion, not machine type, and the General Duty Clause is the fallback. — [Control Design](https://www.controldesign.com/motion/robotics/article/11320134/articles/2016/robots-allowed-contact-with-humans); [OSHA 1910.212 interpretations](https://www.osha.gov/laws-regs/interlinking/standards/1910.212(a)/standard_interpretations); [EHS Insight](https://www.ehsinsight.com/blog/10-oshas-machine-guarding-standard-1)
- EU Machinery Regulation (EU) 2023/1230 becomes mandatory on 20 Jan 2027 and replaces Directive 2006/42/EC. It applies directly in all Member States and adds requirements for cybersecurity (protection against corruption/external attack), autonomous/AI systems, software and lifecycle. There is no transition period, and no EU DoC under the new Regulation can be issued before 20 Jan 2027. — [TÜV Nord](https://www.tuev-nord.de/en/services/audit-and-expertise/product-certification/machinery-regulation/); [Nemko](https://digital.nemko.com/regulations/eu-machinery-regulation); [Intertek (Jul 2025)](https://www.intertek.com/blog/2025/07-03-new-eu-machinery-regulation/); [SGS (Jun 2025)](https://www.sgs.com/en-us/news/2025/06/get-ready-for-eu-machinery-regulation-2023-1230-what-you-need-to-know-and-how-sgs-can-help)
- Industry associations have raised concerns about the cybersecurity/AI provisions. — [Joint industry position PDF](https://www.ibf-solutions.com/fileadmin/Dateidownloads/joint-industry-position-cybersecurity-ai-related-provisions.pdf)

### Inferences
- Safety architecture to output (practitioner knowledge, not sourced this session):
  - **Risk assessment:** per ISO 12100 and RIA TR R15.306 (task-based methodology).
  - **Required performance levels:** safety functions designed to ISO 13849-1 PL (typically PL d / Cat 3 for robot cell stops) or IEC 62061 SIL.
  - **Safety controller:** safety PLC (e.g., GuardLogix, S7-F, TwinSAFE) or safety relays.
  - **Guarding:** fencing per ISO 14120, distances per ISO 13855.
  - **Presence sensing:** area scanners and light curtains, robot safety-rated speed and position limiting.
  - **Mobile robots:** ANSI/A3 R15.08 for industrial mobile robots.
  - **Electrical:** NFPA 79 (industrial machinery electrical) and UL 508A for control panels in the US. NRTL listing is often required by local AHJ/insurers.
- Lights-out operation does not remove safety obligations. Maintenance, restocking and fault recovery bring humans into cells, and these tasks dominate risk assessments in automated plants.
- EU-bound integrators should plan CE conformity under 2023/1230 for any line placed in service after 20 Jan 2027, including substantial-modification rules for retrofits.

### Gaps
- I could not fetch the full A3/ANSI R15.06-2025 announcement (403), so the exact ANSI publication date and its differences from ISO were not confirmed.
- RIA TR R15.306 and R15.08 current editions, the ISO 13849-1:2023 edition, and NFPA 79 2024 edition were not verified this session.

---

## Q8. Commissioning practice, lights-out requirements, benchmarks and the residual human share

### Takeaway
Virtual commissioning against a digital twin is now standard practice. Vendor case studies report 40–70% shorter on-site commissioning, though these are vendor-published. Real "lights-out" exemplars run unattended in bounded windows (FANUC: up to 30 days) on low-mix, highly engineered product lines. Even they keep humans for supervision, QA, maintenance and exceptions: Philips Drachten had about 9 QA staff with 128 robots, Siemens Amberg is about 75% automated, and Xiaomi keeps a supervisory "war room". For a high-mix soft-goods line like apparel, a fully dark factory is much harder because fabric handling and sewing are still unsolved at scale.

### Cited Findings
- **Virtual commissioning results (vendor case studies):** Cleveland Systems Engineering cut design and commissioning time 50% (Siemens). Wipro PARI cut on-site commissioning 70% with Siemens Process Simulate. Kalypso reports 40%. Emulate3D (Rockwell) users report up to 50% shorter installation/commissioning. Digital twins let teams test PLC logic, device behavior, material flow, faults and operator scenarios before site. — [Siemens Cleveland Systems case](https://resources.sw.siemens.com/en-US/case-study-cleveland-systems-engineering); [Siemens Wipro PARI blog](https://blogs.sw.siemens.com/tecnomatix/wipro-pari-reduces-commissioning-time-by-70/); [Kalypso](https://kalypso.com/viewpoints/entry/reducing-commissioning-time-by-40-with-a-digital-twin); [HESCO (Emulate3D)](https://blog.hesconet.com/reducing-commissioning-time-with-digital-twins-lessons-from-real-emulate3d-applications); [ISA InTech (2020)](https://www.isa.org/intech-home/2020/march-april/features/blurring-the-boundaries-between-design-and-automat)
- **FANUC:** lights-out since 2001. Robots build about 50 robots per 24-hour shift and can run unsupervised for up to 30 days. A FANUC VP: "Not only is it lights-out, we turn off the air conditioning and heat too." — [Wikipedia: Lights out (manufacturing)](https://en.wikipedia.org/wiki/Lights_out_(manufacturing)); [Andrew Tobias / original press quote](https://andrewtobias.com/building-robots-in-the-dark)
- **Philips Drachten (shavers):** 128 robots handling most assembly, about 9 workers for quality assurance; lines reported to run unmanned up to 30 days; about 15M razors/year. (Aggregator sources; the 128 robots/9 workers figures trace back to a 2012 NYT report and may be outdated.) — [Standard Bots blog](https://standardbots.com/blog/lights-out-manufacturing); [Omron Drachten case](https://automatykaonline.pl/en/Companies/Omron/Future-proof-assembly-concept-for-high-end-shavers)
- **Siemens Amberg (EWA):** machines and computers handle about 75% of the value chain, with humans doing the rest. Quality figures vary by source and year: 0.0022% defects (~22 dpm), "15 defects per million" (Gartner 2010), and 99.999% at connection level. — [Develop3D](https://develop3d.com/develop3d-blog/the-internet-of-things-iot-and-automation-in-the-smart-factory/); [Engineers Ireland](https://engineersireland.ie/Engineers-Journal/Mechanical/the-smart-factory-and-intelligent-robots-should-we-be-scared)
- **Xiaomi Changping (Beijing) smart factory:** about 860,000 sq ft, 11 automated lines, about 10M phones/year, roughly one phone every 3 s, 100% of key processes automated, with self-diagnosis/optimization claimed by Xiaomi. A small team works in a supervisory "war room". (Claims are company-sourced and reported by press, not independently audited.) — [New Atlas](https://newatlas.com/robotics/xiaomi-dark-robotic-factory/); [DigiTimes (Jul 2024)](https://www.digitimes.com/news/a20240711PD219.html)
- **Apparel-specific limits:** fabric bends and stretches, so it needs constant micro-adjustment, and knits are harder than wovens. SoftWear Automation's CEO acknowledged problems with knitted fabrics. Sewbo's workaround temporarily stiffens fabric with PVA so standard robots can handle it. A 2025 arXiv paper proposes new fabric-handling/sewing approaches, which shows the problem remains open research. — [Business of Fashion](https://www.businessoffashion.com/articles/technology/why-robots-still-cant-do-one-of-fashions-most-important-jobs/); [Design News (Sewbo)](https://www.designnews.com/industrial-machinery/sewbo-robot-system-automates-fabric-sewing-3d); [IEEE Spectrum](https://spectrum.ieee.org/your-next-tshirt-will-be-made-by-a-robot); [arXiv 2503.00249](https://arxiv.org/pdf/2503.00249)

### Inferences
- **Lights-out readiness checklist for planner output (practitioner synthesis):**
  - Remote monitoring/alarming over the UNS with on-call escalation.
  - Condition-based/predictive maintenance on critical assets (vibration/current baselines).
  - Automatic material replenishment: blanks AS/RS + AMR; ink/pretreat bulk feed; film/thread supply sized to the unattended window.
  - Automated QC (vision) with a reject lane.
  - Exception handling: quarantine buffers so a single fault does not stop the line, and a "safe park" state for every machine (PackML Held/Stopped).
  - Fire and thermal monitoring for unattended dryers/curing ovens.
  - Cybersecurity segmentation (also required by the EU MR and ISO 10218:2025).
  - Unattended run window defined (e.g., one overnight shift), not "zero humans".
- **Commissioning sequence:** simulation/digital twin → virtual commissioning of PLC/MES logic → FAT at integrator site → SAT on site → staged ramp-up. Expect output below nameplate for weeks to months; the planner should model a ramp curve.
- **Realistic human fraction for a custom-apparel "dark" factory:** benchmarks show even showcase plants keep roughly 25% of value-chain tasks human (Amberg) or keep QA/supervision staff (Drachten, Xiaomi). Apparel decoration (print/cure/pack) is more automatable than cut-and-sew, but garment loading/unloading, art pre-flight, maintenance, replenishment and exception handling will likely stay human or semi-automated. A credible plan targets "lights-sparse" first-shift-staffed operation with unattended overnight runs, not 100% unmanned.

### Gaps
- No academic review found quantifying the typical residual human-task fraction across lights-out factories. The figures above are case anecdotes, partly from aggregators or company claims.
- Philips Drachten data is likely dated (2012 origin). No 2025–2026 update found.
- A claim surfaced in search that SoftWear's Sewbot had its "first factory in Bangladesh as of June 30, 2026". It was not verified against a primary source and is excluded.
- No data found on commercially deployed robotic garment loading for DTG platens. Check Kornit/Brother/Epson automation announcements separately.
