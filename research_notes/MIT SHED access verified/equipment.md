# MIT SHED (Safety Health Environmental Discovery lab, N52 4th floor): Verified Equipment Inventory, Focus on Metal 3D Printing and CNC

Research date: 2026-10-01. Method: unlike the earlier pass, every page here was **fetched in full** with curl (all 200 OK): every URL in shed.mit.edu/sitemap.xml (24 pages, text plus every `<img alt>`), the make.mit.edu public Airtable/Softr data endpoints behind /equipment and /makerspaces (all 674 equipment records and 38 makerspace records pulled and searched), the SHED LibCal calendar, the SHED iCal feed and SHED event pages, and the MIT News and NSE articles that shed.mit.edu links to. "Verified" below means I read it in the full page or raw data. "Inferred" means it is my interpretation.

**Bottom line:** no public source names the manufacturer or model of any SHED fabrication machine (metal printer, 4/5-axis mills, lathes, waterjets, wire EDM, laser cutters, FDM/SLS/DLP/PolyJet printers, vacuum formers). The SHED's own site lists categories only. make.mit.edu's equipment database has a SHED record, but its equipment field is **empty**. The only public make/brand clue is an MIT News line that 16.811 impellers were printed "at the MIT SHED … and by industry collaborators at Desktop Metal". That sentence does not establish that the SHED owns a Desktop Metal machine.

## Q1: What does shed.mit.edu publish? (full crawl, sitemap, alt text)

### Takeaway
shed.mit.edu is a Webflow site with 24 pages in its sitemap, and none has an equipment or tools page. The Capabilities page is the only equipment statement, and it lists technology categories with **no makes/models**. All content images have empty alt text (`alt=''`), so alt text adds nothing. The page also names five physical sub-spaces, including a separate **"Fabrication Node"** for machining and metal work.

### Cited Findings
- The sitemap lists exactly these pages: /, /search, /style-guide, /about-the-shed, /page/capabilities, /page/courses, 15 research /page/ entries (bioactive-vascular-implants, boiling-heat-transfer, brain-tissue-imaging, cell-active-bioinks, environmental-fluid-mechanics, health-informatics, hybrid-bioprinting, integrated-biofabrication, large-scale-perfusable-sla-printed-constructs-for-tissue-engineering, making-the-makers, microfluidics-laser-processing, neutron-scintillators, organs-ai, research-abstracts, silent-stage-malaria), and /tile-page/network, /tile-page/publications-patents, /tile-page/research. /wp-sitemap.xml and /sitemap_index.xml return 404 — [shed.mit.edu/sitemap.xml](https://shed.mit.edu/sitemap.xml)
- Guessed slugs for sub-space or equipment pages (/page/prototyping, /page/fabrication, /page/equipment, /equipment, /page/biofabrication, /page/spaces, /page/fabrication-node, /page/beamworks, /page/hygieneyx, /news) all return **404**. The old URL /spaces redirects to /page/capabilities — probed directly on shed.mit.edu (e.g., [https://shed.mit.edu/spaces](https://shed.mit.edu/spaces))
- **Prototyping & Fabrication (verbatim):** "Designed as an engineering lab, which aims to enable rapid prototyping, iteration, and production across various materials. The prototyping space includes a variety of hand tools, section for electronics work, supports digital design & modeling and enables additive manufacturing through a suite of FDM/ SLS / DLP / PolyJet / Metal 3D printers. The fabrication space enables CNC machining and subtractive manufacturing by 4-axis & 5-axis mills, lathes, waterjets, vacuum formers, laser cutters & engraves and wire EDM. The core capabilities are curated to complement the research projects in life sciences as wells as microfluidics, electronics, robotics, and automation." — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- **Site map of SHED sub-spaces (verbatim captions from the capabilities page map graphic):** "Life Sciences Hub — Main lab location for life sciences research, radio-analytics and prototyping sections." "**Fabrication Node — Dedicated space for machining, fabrication and metal works.**" "Hygieneyx — Dedicated industrial hygiene lab for material testing and analysis." "Beamworks — Laser labs for hands on training and high-power laser research." "The Gray — Gamma and X-ray based irradiators used for life sciences and materials radiation research." — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- **Chemistry:** wet-chemistry space with "chemical fume hoods, specially designed perchloric acid fume hood with wash-down capability, benches fitted with compressed air, natural gas and deionized water and full array of lab equipment". Hygieneyx is the IH lab ("Airborne Contaminants & Silica Testing, Metals, Organic Compound & Microbial Analysis and Asbestos Identification") — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- **Biology:** BSL-2+ space with "a dedicated biofabrication suite with Bioreactors, 3D Bio printers, biosafety cabinets…" — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- **Radiation & Nuclear:** "high-purity germanium detectors, sodium-iodide detectors, gas flow proportional detectors, liquid scintillation counters, alpha and gamma spectroscopy systems, dosimetry systems and various portable detection systems". Beamworks has an optics/lasers/stages training section and "high power laser research space fitted with femto second laser systems". It is "connected to MIT's nuclear sciences research ecosystem including the Nuclear Reactor Lab" — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- NSE News confirms the SHED's radiation instruments: "liquid scintillation counters (LSCs) with both beta and alpha spectroscopy capabilities… and High-Purity Germanium (HPGe) semiconductor detector" (makes not given) — [MIT NSE News, 2024](https://web.mit.edu/nse/news/2024/radiation-measurement-and-protection.html)
- A grep of all 24 pages for brands (Markforged, Desktop Metal, EOS, Xact, Velo3D, Haas, Tormach, DMG, Kern, Datron, Pocket NC/Penta, OMAX/ProtoMAX/Flow/Wazer, Sodick/Mitsubishi/Fanuc/Charmilles, Formlabs, Stratasys/Objet/J-series, Prusa/Bambu/Ultimaker, Epilog/Trotec/Universal, Formech/Mayku, Cellink/Allevi/Regemat) returned **zero hits** — all pages listed in [shed.mit.edu/sitemap.xml](https://shed.mit.edu/sitemap.xml)
- The Capabilities page's content images have empty alt text. Their file names (e.g., `mit080123_EHS_0031.jpg`, `Capabilities-04.png`, `shed_map3.png`) carry no equipment information — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- Webflow publish stamp on the 404 template: "Last Published: Thu Jul 16 2026", so the site is actively maintained as of mid-2026 — [shed.mit.edu (404 page source)](https://shed.mit.edu/wp-sitemap.xml)

### Inferences
- The capabilities text is the SHED's only public machine statement, and it is written as a capability claim, not an inventory. Plurals ("waterjets", "lathes", "Metal 3D printers") may be generic phrasing and need not mean multiple units.
- The "Fabrication Node" is described as a separate "dedicated space for machining, fabrication and metal works", so the CNC, waterjet, and EDM equipment is probably not in the main N52-4th-floor Life Sciences Hub where M1T runs. Its location is not published. This is inference from the map captions.

### Gaps
- No equipment list, model names, or per-machine pages exist on shed.mit.edu.
- The physical location of the Fabrication Node, Beamworks, and The Gray is not given.

## Q2: Does make.mit.edu list SHED equipment? (Softr/Airtable data inspected)

### Takeaway
make.mit.edu is a Softr app backed by Airtable base `appFhdhKmHkXVmAlE`. Its equipment and makerspace data is **publicly readable without login** through Softr's datasource endpoint. The Makerspaces table includes **"The SHED at EHS", location N52-496, with an empty Equipment field**. None of the 674 equipment records is assigned to the SHED or sits on N52's 4th floor.

### Cited Findings
- The /equipment page embeds a list block reading Airtable table `Equipment`, view "All Equipment (unfiltered)", with fields Equipment Model, Local Equipment Type, Makerspace, Location, Materials, In Situ Photo — [make.mit.edu/equipment](https://make.mit.edu/equipment) (page source)
- Public data endpoint (POST, no auth): `https://make.mit.edu/v1/datasource/airtable/0db7e5d4-e93c-4d18-bb31-b2e6e95a216a/19b5f9f2-97c8-4186-bf38-b4a15c5cbaca/52d13b85-bead-467f-ac8b-76532d86dc1d/3d5c1dba-20b3-47ee-aa3f-4fc9c58761c8/data` returned **674 equipment records** across 38 makerspaces. **No record has Makerspace = SHED**. — [make.mit.edu/equipment](https://make.mit.edu/equipment)
- The Makerspaces table (via the /makerspaces block) returned 38 records, including: Name "**The SHED at EHS**", MIT Location "**N52-496**", Description "The SHED is a special makerspace which aims to proactively integrate research, applied problem-solving and core Environmental, Health, and Safety (EHS) expertise…", **Equipment: "" (empty), Equipment Type: "" (empty)** — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces)
- Every N52 location in the equipment DB is MITERS (N52-115) or MAD's N52 shop (N52-342A, 3rd floor). Examples: MAD has Epilog Legend EXT, Stratasys Objet24, Stratasys Dimension 1200es, Formlabs Form 2, ShopBot 2 / ShopBot Desktop, Othermill, Little Machine Shop 3900 mill / 4100 lathe. **None is on the 4th floor, and none belongs to the SHED** — [make.mit.edu/equipment](https://make.mit.edu/equipment)
- 14 equipment records have no makerspace and no location (Formech 450DT vacuformer, Universal VLS 3.50 laser cutter, Stratasys uPrint SE, Ultimaker S5, Zortrax M200, Freedom Machine Tool 4x8 router, Little Machine Shop 7x12 lathe, Jet/Clausing drill presses, Jet bandsaw/sander, Brother/Singer sewing, Silhouette CAMEO). Nothing ties them to the SHED — [make.mit.edu/equipment](https://make.mit.edu/equipment)
- For contrast, other MIT shops list metal-capable machines with models: OMAX 5555 waterjet and Sodick SL-400G wire EDM at Center for Bits and Atoms (E15-401), Charmilles Robofil 1020SI wire EDM at BioInstrumentation Lab (3-147), OMAX 2652 waterjet at Gelb Lab (33-009) — [make.mit.edu/equipment](https://make.mit.edu/equipment)
- The make.mit.edu M1T page links its first-year training calendar to `project-manus.libcal.com/calendar/shed?cid=11833…` — [make.mit.edu/m1t](https://make.mit.edu/m1t) (page source)

### Inferences
- The SHED is registered as a makerspace on make.mit.edu, but it has never filled in an equipment inventory there. The public equipment DB therefore can't settle the models, and the empty field suggests the SHED does not publish model-level inventory anywhere. Login would not help: these records come back unauthenticated, and the SHED field is empty.
- Room N52-496 is the SHED's listed room. It matches "N52 4th floor" in LibCal.

### Gaps
- Whether the SHED's machines appear in some separate, login-gated system (e.g., an EHS internal inventory or a SHED-specific booking tool): not found.

## Q3: Exact metal 3D printer make/model, technology, and access rules

### Takeaway
**Not published.** The SHED confirms "Metal 3D printers" as a category only. The one public clue is MIT News (Mar 28, 2025): 16.811 turbopump impellers "were printed at the MIT SHED … with support from Tolga Durak … and by industry collaborators at Desktop Metal." The wording is ambiguous: it may mean that Desktop Metal printed some parts, or that it supported printing at the SHED. It does **not** state that the SHED owns a Desktop Metal system. No access rules for metal AM are published.

### Cited Findings
- "…enables additive manufacturing through a suite of FDM/ SLS / DLP / PolyJet / Metal 3D printers." — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- "Impellers were printed at the MIT SHED (Safety Health Environmental Discovery lab), with support from Tolga Durak, managing director of environment, health and safety, and by industry collaborators at Desktop Metal." (article dated March 28, 2025) — [MIT News: Preparing for a career at the forefront of the aerospace industry](https://news.mit.edu/2025/preparing-career-forefront-aerospace-industry-0328)
- The same article quotes Prof. Zachary Cordero: "Students in this class gain that experience through exposure to cutting-edge design and manufacturing tools, like metal 3D printing". It also says machine-shop training was in "the Arthur and Linda Gelb Laboratory", not the SHED — [MIT News, 2025-03-28](https://news.mit.edu/2025/preparing-career-forefront-aerospace-industry-0328)
- The SHED lists the course as "16.S811: Advanced Manufacturing for Aerospace Engineers" (MIT News calls it 16.811) — [SHED Courses](https://shed.mit.edu/page/courses)
- A web search pairing the SHED/Durak with Desktop Metal or Markforged returned no relevant MIT result — [WebSearch, 2026-10-01; no MIT hits]

### Inferences
- The 16.811 impellers were metal or high-performance printed parts made at least partly at the SHED. That makes it plausible the SHED's metal AM is used in course and research work through staff or collaborators, not student self-service. If the SHED owns a bound-metal system (Desktop Metal Studio/Shop or Markforged Metal X type), the Desktop Metal mention would fit, but **this is speculation and not verified**.
- Access is most likely through a research or course project, run by SHED staff, mentors, or collaborators. No public source says this.

### Gaps
- Make, model, and technology (bound-metal extrusion, binder jet, or powder-bed LPBF): **not published anywhere public that I could find.**
- Student operating rules, training credential, cost: not published.
- The best direct route is to email SHED@mit.edu ("Become a User" on the site is a mailto link) — [MIT SHED](https://shed.mit.edu/)

## Q4: Exact CNC mill (4-/5-axis), lathe, waterjet, wire EDM models and training levels

### Takeaway
**Not published.** The categories are verified (4-axis & 5-axis mills, lathes, waterjets, wire EDM, plus vacuum formers and laser cutters/engravers) and are said to sit in a "Fabrication Node … for machining, fabrication and metal works". No brand, model, or training tier appears on shed.mit.edu, make.mit.edu, LibCal, MIT News, or EHS pages.

### Cited Findings
- "The fabrication space enables CNC machining and subtractive manufacturing by 4-axis & 5-axis mills, lathes, waterjets, vacuum formers, laser cutters & engraves and wire EDM." — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- "Fabrication Node — Dedicated space for machining, fabrication and metal works." — [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- The make.mit.edu SHED record has an empty Equipment field. None of the 674 equipment DB records (including every OMAX waterjet, Sodick/Charmilles EDM, and ProtoTRAK entry) is attributed to the SHED — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces); [make.mit.edu/equipment](https://make.mit.edu/equipment)
- The MIT EHS Shops & Makerspaces guidance page links to "SHED Lab" (shed.mit.edu) as a resource but lists no SHED equipment — [MIT EHS Shops and Makerspaces](https://ehs.mit.edu/workplace-safety-program/shops-and-makerspaces/)
- SHED LibCal calendar (cid 19337): no upcoming events, and the iCal feed contains 0 events. The only SHED events found are M1T variants — [LibCal EHS The SHED](https://project-manus.libcal.com/calendar/shed); [SHED iCal feed](https://project-manus.libcal.com/ical_subscribe.php?src=p&cid=19337)

### Inferences
- Because no CNC, waterjet, or EDM training events are published for the SHED, these machines are probably not on an open student checkout track. They are likely mentor- or staff-operated, or used inside research and course projects. This is inference only.

### Gaps
- Mill models (e.g., whether the 5-axis is Haas UMC, Pocket NC/Penta, DMG, Kern), lathe type (CNC vs manual), waterjet make, and wire EDM make: **not published publicly.**
- Training levels for any SHED CNC tool: not published.

## Q5: Who may operate what? (student after training vs mentor/staff vs research-only)

### Takeaway
The only **verified student-operable** SHED equipment is the **laser cutter, 3D printer (presumably FDM), electronics, and soldering**, used in the SHED's M1T variants, which award "novice laser cutter and 3D printing credentials". Everything else has no published operator policy. The SHED's model is mentor-supported, research-oriented "user" access requested through SHED@mit.edu.

### Cited Findings
- M1T at the SHED: "It introduces a different set of equipment and skills to complete the device (laser cutter, 3D printer, electronics, and soldering)… students will receive the same M1T completion credit (50 Makerbucks, a T-Shirt, and tools) as well as novice laser cutter and 3D printing credentials." The course runs as two 2-hour parts. Location: "The SHED N52-4th Floor". The Zoetrope event was dated Dec 6, 2024; organizer Jack Greenfield — [LibCal event 13637298](https://project-manus.libcal.com/event/13637298)
- The same wording appears for the Lixie Clock variant, dated Feb 24, 2025 — [LibCal event 14128285](https://project-manus.libcal.com/event/14128285)
- "Mentors — Student and researcher mentors are the SHED's community leaders, from designing trainings to hosting events and open hours to determining future direction and priorities for the space. They represent every area of interest and are prepared to support users in the intricacies of every equipment, tool and process." The page lists 34 active mentors and a 7-person SHED EHS team (Aalaei, Casavant, Kalil, Kirby, MacLeod, Marketon, Sain) — [About the SHED](https://shed.mit.edu/about-the-shed)
- "Users — Diverse group of individuals who seek to advance knowledge across various disciplines leveraging SHED's resources and expertise to achieve their research and innovation goals." The "Become a User" link is mailto:SHED@mit.edu — [About the SHED](https://shed.mit.edu/about-the-shed); [SHED Capabilities](https://shed.mit.edu/page/capabilities)
- Course-based access is published: 2.007, 2.009, 2.797, 16.S811, 22.015, 22.033, 22.09 — [SHED Courses](https://shed.mit.edu/page/courses). In 2.797/2.798, "students visit the SHED makerspace to learn about 3D bio-printing" — [MIT News, 2025-05-28](https://news.mit.edu/2025/mechanical-engineering-course-invites-students-build-with-biology-0528)
- Bioprinting is research-integrated: an AI monitoring platform "has already been integrated into the 3D bioprinting facilities in The SHED" — [MIT News, 2025-09-17](https://news.mit.edu/2025/new-3d-bioprinting-technique-may-improve-production-engineered-tissue-0917). The SHED also supported the MagMix bioprinting work — [MIT News, 2026-02-10](https://news.mit.edu/2026/magnetic-mixer-improves-3d-bioprinting-0210). Bioprinter makes are not named.

### Inferences
- Suggested access tiers for the report writer, with the verified/inferred status stated for each:
  - Student after training (verified): laser cutter, 3D printer (novice credential), electronics/soldering.
  - Course- or research-mediated (verified that courses use it, operator not stated): bioprinters (2.797), metal AM (16.811 impellers).
  - Mentor/staff/research only (inferred, unverified): metal 3D printers, SLS, PolyJet, 4/5-axis mills, lathes, waterjets, wire EDM, femtosecond lasers, irradiators (The Gray), radiation counting.

### Gaps
- No published per-machine access policy, credential ladder, hours, or rates.
- I did not attempt the LinkedIn page (linkedin.com/company/the-shed-at-mit), which is login-gated. Equipment photos or posts there could name models.
- Recommended verification: email SHED@mit.edu asking for the model list of the metal printer(s), 5-axis mill, waterjet, and wire EDM, plus the access tier for each.
