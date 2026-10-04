# Automation Technology for Custom Apparel & Textile Production (state as of Oct 2026)

Scope: step-by-step map of a custom apparel business (print/decorate, embroidery, cut-and-sew, handling, finishing, pack/ship) — what is automatable now, what is partial, what is hard; named machines, vendors, costs, throughput, readiness; what a near-lights-out custom apparel factory looks like in 2026. Research run 2026-10-04 with ~19 search/fetch calls; several vendor pages lack prices/throughput, and some web results were low-quality aggregators (flagged below).

Readiness shorthand used in Inferences: **Commercial** (buy it today, deployed widely) / **Early-commercial** (sold, few deployments) / **Pilot** / **Lab-demo**.

---

## 1. Printing: DTG, screen, DTF, sublimation — which systems load/unload garments automatically?

### Takeaway
Printing itself is fully automated; the bottleneck is **putting a floppy garment onto a pallet/platen**. As of 2026 no mainstream garment printer (Kornit, M&R, ROQ, Epson, Brother) loads garments fully autonomously from a bin — the best production systems (Kornit Apollo) are "semi-auto loading" where a human hands the shirt to a loader, plus fully automatic unloading to the dryer. Screen printing has mature auto-*unloaders* (M&R Passport, ~1,200 pcs/hr), but loading is still a human job. DTF is the most automation-friendly print path because the print is made on roll film (roll-to-roll print → powder → cure is unattended), moving the hard garment-handling step to a heat press.

### Cited Findings
**Kornit (DTG, industrial)**
- Kornit Apollo (announced June 2023): built on Kornit MAX technology, designed to decorate **400 unique garments per hour**; "automated loading and unloading, integrated smart curing, and inline garment type adjustment" — [Impressions Magazine](https://impressionsmagazine.com/news/kornit-digital-unveils-new-apollo-platform-and-enhanced-atlas-max-plus/39113/); [TexIntel press release](https://www.texintel.com/press-room/kornit-digitals-new-apollo-platform-introduces-sustainable-on-demand-production-at-scale)
- Apollo detail: **automatic unloader** removes the shirt from the pallet and places it on the dryer conveyor; loading is **semi-automatic** — "the operator hand[s] the garment to the semi-automatic loader that loads the shirt onto the pallet" — [Kornit Apollo brochure (Oct 2023, PDF)](https://www.kornit.com/wp-content/uploads/2023/10/Apollo_brochure_15-Oct-23_DIGITAL_V06.pdf); [Printweek "Star product: Kornit Apollo"](https://www.printweek.com/content/features/star-product-kornit-apollo)
- Kornit Atlas MAX PLUS: up to **150 garments/hour**, integrated Smart Curing, Rapid Size Shifter pallets, autonomous calibration (manual loading) — [Impressions Magazine](https://impressionsmagazine.com/news/kornit-digital-unveils-new-apollo-platform-and-enhanced-atlas-max-plus/39113/)
- Kornit Atlas MAX Poly variant introduced for polyester garments — [Printwear & Promotion](https://printwearandpromotion.co.uk/kornit-digital-introduces-the-atlas-max-poly/)
- Kornit positions 2026 DTG as "connected systems … end-to-end workflow integration that reduces manual steps" (vendor marketing) — [Kornit magazine, DTG trends 2026](https://www.kornit.com/magazine/top-trends-tshirt-printing-dtg-jsuh/)
- Kornit DTG integrates with POD platforms (e.g., Gelato Connect partner listing) — [Gelato/Kornit](https://www.gelato.com/connect/partners/kornit)

**Screen printing (M&R, ROQ)**
- M&R **Passport** automatic t-shirt unloader: cycle rates "up to **100 dozen per hour**" (~1,200 pcs/hr); four patented grippers lift garments straight up; inline and side-takeoff versions; works with all M&R automatic presses and most gas/electric conveyor dryers; pallets 10"x10" to 24"x30"; customer testimonial ROI <1 year. The page lists **no automatic garment loader** — [M&R Passport page](https://www.mrprint.com/equipment/passport-automatic-t-shirt-unloader)
- M&R also sells DTF, DTG, hybrid and screen equipment and introduced the STRYKER automatic press — [M&R home](https://www.mrprint.com/); [Screen Printing Mag](https://screenprintingmag.com/mr-introduces-stryker-automatic-screen-printing-press/)
- ROQ 2026 innovations: new click-in off-contact mechanism and **auto platen load/unload** (one-button platen swap mode, sequential platen removal/replacement, automatic locking) — this is changeover automation of *platens*, not garment loading; no prices or throughput given, availability "later this year" — [ROQ blog, "What's New on ROQ … in 2026"](https://www.roq.us/post/what-s-new-on-roq-automatic-screen-printing-presses-in-2026)
- ROQ press lineup: ROQ NEXT, ROQ YOU (Geneva Ball Drive, single/dual operator), ROQ E — [ROQ presses](https://www.roq.us/roq-automatic-screenprinting-presses); [ScreenPrinting.com ROQ NEXT](https://www.screenprinting.com/products/roq-next-automatic-screen-printing-press); [Embellishr ROQ YOU](https://embellishr.com/products/new-roq-you-m-automatic-press)
- Screen labor rule of thumb: single-color print ~1–2 min/shirt and 4-color 3–5 min/shirt plus setup (vendor/blog pricing guidance, not a rigorous study) — [Print & Promo Marketing pricing guide](https://printandpromomarketing.com/article/pricing-strategies-for-screen-printing/)

**DTF (roll-to-roll)**
- Roland TY-300 30" DTF printer + RDTFS800 shaker bundle: **$28,995**; RDTFS800 shaker alone **$6,795**; continuous roll-to-roll with dual catch trays "for unattended production," built-in HEPA fume extraction — [Airmark bundle listing](https://www.airmark.com/products/roland-ty-300-30-dtf-printer-and-rdtfs800-shaker-bundle); [McLogan TY-300](https://mclogan.com/products/ty-300)
- BMAC Super Shaker (third-party): **$9,995** — [Airmark](https://www.airmark.com/products/roland-ty-300-30-dtf-printer-and-rdtfs800-shaker-bundle)
- Mimaki TxF300-75 (32"/30–36" DTF) pairs with Miro 36 automated powder shaker with air purification — [GJS / Roland shaker listing & Mimaki bundle results](https://gjs.co/equipment/new/p4895/roland-dg-dtf-powder-shaker-unit)

**Industry adoption of robotics around print**
- Keypoint Intelligence (2025 recap / 2026 outlook): robots "beginning to appear in select environments for loading, unloading, pallet movement, and internal logistics," but most print providers were still evaluating; nearly half of in-plant respondents *planning* to invest rather than already using; 2026 predicted as move "from exploratory pilots to structured early adoption" — [Keypoint Intelligence](https://keypointintelligence.com/news/keypoint-intelligence-recaps-2025-industry-trends-and-predicts-2026)
- Patents exist for robotic garment handling in DTG: robot arms moving garments from dryers to DTG printers, autonomous robots moving garments through retrieval/pretreat/print/dry stages, and garment-personalization kiosks with robotic retrieval — [US 11491812 "Garment personalization with autonomous robots"](https://patents.justia.com/patent/11491812); [US 11623823 kiosk](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11623823); [US 11833809 kiosk](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11833809); [US 11413891](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11413891)
- A claim that Printful deployed 15 Kornit Atlas MAX units in Charlotte and 10 in Barcelona with 20 more by Q3 2026 appears only on an SEO-style printer-vendor site — **treat as unverified** — [xinflyinggroup.com](https://xinflyinggroup.com/dtg-ecommerce-fulfillment-sales-growth/)

### Inferences
- **Step map: printing**
  - *Fully automated today:* print execution (DTG/screen/DTF/sublimation), DTF roll print+powder+cure (Commercial, ~$29k for 30" entry industrial), screen unloading to dryer (M&R Passport, Commercial), DTG unloading to dryer (Kornit Apollo, Commercial but high-end), conveyor curing, inline pretreat (Kornit has pretreat inline in its industrial systems).
  - *Partially automated:* garment loading (Apollo semi-auto loader: human still hands garment), screen setup (ROQ auto platen swap; pre-registration systems), DTF application (heat press needs human placement of garment + transfer).
  - *Hard / human:* picking a single blank from a bin and dressing it squarely on a platen; screen making/reclaim (partially automated by CTS and auto-reclaim machines — not researched in this run); ink mixing/colour matching for screen.
- Kornit Apollo at 400 gph with ~1 loader operator is the closest thing to a "lights-sparse" DTG cell; implies print labor per shirt falls to roughly (1–2 operators)/400 per hour.
- For an AI automation planner, DTF + roll-to-roll + automated heat-press placement is the most tractable path to near-lights-out *print* production; the garment-dressing step remains the main robotics frontier.

### Gaps
- No public pricing found for Kornit Apollo or Atlas MAX PLUS (industry chatter suggests high six to seven figures but not verified in this run).
- Did not verify Epson SureColor F-series / Brother GTX Pro automation features (neither appears to offer automatic garment loading, but unconfirmed this run).
- No verified source found for a fully autonomous robotic garment *loader* in commercial DTG/screen use (e.g., from Fizyr, Covariant, Ambi Robotics — these firms target parcels/e-commerce picking, not platen dressing; not confirmed).
- MHM press automation and sublimation calendar-line (roll-to-roll heat transfer) specs not researched.
- Printful/Custom Ink/Gooten/Swag.com/Fulfill Engine internal automation details: no credible public sources found.

---

## 2. Embroidery: Tajima, Barudan, ZSK; hooping and thread change

### Takeaway
Embroidery machines are highly automated once hooped (auto color change across 12–15 needles, auto trim, thread-tension management, hoop recognition), but **hooping is still manual** in practice; the mainstream "automation" of hooping is magnetic hoops and hooping stations that cut hooping time ~3 min → ~30 s. No commercial robotic hooping system was found.

### Cited Findings
- Tajima TMEZ-SC1501: i-TM (Intelligent Thread Management) automatically sets thread supply from fabric thickness/stitch type; DCP (Digitally Controlled Presser foot) auto-adjusts height; 1,200 RPM; claimed up to 30% fewer defects (accessory-vendor blog, not Tajima directly) — [HoopTalent blog](https://www.hooptalent.com/blogs/news/tajima-tmez-sc1501-complete-guide-to-features-performance-and-smart-automation)
- ZSK: automatic thread trimming, color changes, hoop recognition; T8 controller with 80M stitch memory and RFID tracking (accessory-vendor blog) — [MagneticHoop: ZSK vs Tajima 2025](https://www.magnetichoop.com/blogs/news/zsk-vs-tajima-2025-expert-analysis-for-commercial-embroidery-success); [MaggieFrame ZSK review](https://maggieframestore.com/blogs/maggieframe-news/zsk-embroidery-machine-review-in-depth-analysis-for-commercial-and-small-business-users)
- Magnetic hoops: hooping time "often drops from about 3 minutes to 30 seconds — roughly a 90% reduction" (claim from a magnetic-hoop seller; treat as marketing) — [MagneticHoop Tajima guide](https://www.magnetichoop.com/blogs/news/tajima-america-corporation-industrial-embroidery-machines-2025-buyers-guide-expert-insights)
- Search for automated/robotic hooping found that vendor automation focuses on thread management, fabric control, and hoop recognition "rather than fully automated robotic hooping systems" — [same search results; MagneticHoop / MaggieFrame blogs above]

### Inferences
- *Fully automated:* stitching, color change, trims, tension (Commercial).
- *Partial:* hooping (magnetic hoops, hooping stations like HoopMaster — Commercial, human-operated jig); digitizing (AI auto-digitizing exists in software, quality varies — not verified this run).
- *Hard:* robotic hooping of caps/finished garments; thread-break recovery is detected automatically but re-threading is human.
- Multi-head embroidery (e.g., 12–20 heads) means one operator can tend many heads; labor is dominated by hooping/unhooping, trimming, and backing removal.

### Gaps
- No source found for commercial robotic hooping; academic work not found in this run.
- Barudan automation features and machine prices not verified.

---

## 3. Cut-and-sew: automated cutting, robotic sewing, research status

### Takeaway
**Cutting is fully automated and mature** (Gerber/Lectra multi-ply and single-ply digital cutters). **Sewing remains the hardest step**: SoftWear Automation's Sewbots are the only notable commercial autonomous worklines (T-shirts, towels, mats, denim), raised $20M in Aug 2025 (BESTSELLER-led), with a 3rd-gen T-shirt Sewbot targeted for H1 2026 commercial availability; Sewbo's stiffening approach remains niche. For a *custom decoration* shop (which buys blanks), cut-and-sew is usually out of scope.

### Cited Findings
- Gerber Atria (Lectra): "fully integrated cutting solution for mass production … most advanced digital multi-ply fabric cutter"; claims up to 40% less fabric waste with zero-buffer cutting and AI, up to 30% faster — [Lectra Gerber Atria](https://www.lectra.com/en/products/gerber-atria-fashion)
- Lectra Virga: integrated single-ply digital fabric cutting line for on-demand, one-off production (marketed for upholstered furniture), automated loading/unloading — [DirectIndustry / Lectra results](https://www.directindustry.com/prod/gerber-technology-a-lectra-company/product-55072-2836568.html)
- Used Lectra Vector multi-ply cutters trade on secondary markets (e.g., Vector Q25, 2022) — [Exapro](https://www.exapro.com/lectra-q25-p260202052/); [Surplus Record](https://surplusrecord.com/listing/lectra-vt-fu-q25-72-multi-ply-fabric-cutting-machine-vector-q25-672-w-2022-1047277/)
- SoftWear Automation closed **$20M Series B1 on Aug 11, 2025**, led by BESTSELLER (Jack & Jones, Vero Moda, ONLY); SEWBOT worklines initially piloted on bath mats/towels, now "power local T-shirt factories, home textiles, and denim production lines for major global brands" — [SoftWear press release](https://softwearautomation.com/softwear-automation-secures-20-million-in-series-b1-funding-round-led-by-strategic-partnership-with-bestseller/); [Textile World, Aug 2025](https://www.textileworld.com/textile-world/knitting-apparel/2025/08/softwear-automation-secures-20-million-in-series-b1-funding-round-led-by-strategic-partnership-with-bestseller/)
- Sewbot tech: high-speed vision tracks the needle and makes micro-corrections to fabric movement in real time — [SoftWear Sewbots page](https://softwearautomation.com/sewbots/)
- 3rd-gen T-shirt Sewbot "expected to reach commercial availability in H1 2026"; claim: one finished T-shirt every **22 seconds**, labor cost as low as **$0.33/shirt** vs $1+ manual; nearly 2x the output in 8 hrs of a manual line in 24 hrs (secondary coverage of company claims; not independently verified) — [RetailBoss](https://retailboss.co/sewbot-technology-drives-softwear-automation-bestseller-20-million-dollar-apparel-revolution/)
- Sewbo: stiffens fabric with water-soluble thermoplastic so standard industrial robots can handle it like cardboard; dissolved in hot water after sewing; validated with cotton at **Bluewater Defense** and denim at Levi's research facility — [arXiv 2503.00249 (Mar 2025), "Robotic Automation in Apparel Manufacturing"](https://arxiv.org/html/2503.00249v1); [Fast Company (2016)](https://www.fastcompany.com/3064001/meet-the-garment-sewing-robot-that-could-disrupt-the-fashion-industry)

### Inferences
- *Fully automated:* nesting/marker making, single- and multi-ply cutting, cut-part labeling (Commercial).
- *Partial:* sewing of simple flat products (towels, mats, pillowcases) and basic T-shirts via Sewbot worklines (Early-commercial; few deployments, mostly large brands); automated pocket setters/hemmers/buttonholers are long-established single-operation automats.
- *Hard:* general sewing of 3D garments with curved seams, sleeves, collars; variety and small batches (the custom market) make dedicated worklines uneconomic.
- For the AI planner's beachhead (custom decoration on blanks), recommend treating cut-and-sew as "buy blanks" except for cut-and-sew sublimation (all-over print), where roll sublimation → automated cut (vision-based contour cutter) → human sewing is the realistic 2026 flow.

### Gaps
- Siemens/Henderson Sewing robotic sewing work: no 2025–26 source found in this run.
- Georgia Tech / MIT robotic sewing research status not retrieved.
- Gerber/Lectra cutter prices not found (used-market listings exist but no prices captured).

---

## 4. Garment handling, deformable manipulation, folding/bagging, intralogistics

### Takeaway
Folding of known items by AI-driven bimanual robots crossed from lab demo to early commercial service in 2025–2026 (Dyna Robotics in hotels/laundries; >99% internal success claim; DYNA 2.1/Taku laundry demos in late Sept 2026). Separately, dedicated **folding+bagging machines are cheap commercial products** ($4k–$30k, 400–500 pcs/hr claimed) — a human just lays the shirt on. "Pick a random shirt from a bin and dress it on a platen" remains unsolved commercially.

### Cited Findings
- Physical Intelligence's pi0 VLA model launched with a video of a robot folding clothes after unloading a dryer/washer — [Chris Paxton, "Why is Everyone's Robot Folding Clothes?" (Aug 14, 2025)](https://itcanthink.substack.com/p/why-is-everyones-robot-folding-clothes)
- Paxton: folding became the benchmark because "we basically couldn't do this before" (prior methods "extremely brittle, extremely slow"), plus low force, error tolerance, repeatability and easy data collection; companies demoing folding include Weave Robotics, Figure (F02), PI, Google (ALOHA Unleashed), 7X Tech, Dyna (18 hours of continuous napkin folding) — [Paxton substack](https://itcanthink.substack.com/p/why-is-everyones-robot-folding-clothes)
- Dyna Robotics at **CES 2026**: two fixed arms grip, align and fold garments; **>99% success** in internal tests; robots already in hotels, laundries, service businesses running up to **16 hours/day** — [heise (Jan 2026)](https://www.heise.de/en/news/Dyna-robot-folds-laundry-by-itself-11133562.html)
- DYNA 2.1 humanoid completes laundry shifts with error recovery; Taku wheeled two-arm robot took laundry washer-to-shelf in a one-hour demo, unveiled **Sept 29 (2026)** — [Interesting Engineering](https://interestingengineering.com/ai-robotics/watch-new-humanoid-robot-unloads-laundry-and-folds-towels-without-human-help); [The Rundown](https://www.therundown.ai/news/dyna-taku-laundry-robot)
- Humanoids folding laundry shown at CES 2026 — [Robb Report](https://robbreport.com/gear/personal-technology/humanoid-robots-ces-1237497312/)
- Academic: FoldNet / FoldNet++ synthetic datasets for T-shirt folding/unfolding (2025–2026); UniFolding; Cloth Funnels; ICRA 2024 Cloth Competition dataset for unfolding grasp selection — [FoldNet++ arXiv 2609.12433](https://arxiv.org/pdf/2609.12433); [FoldNet arXiv 2505.09109](https://arxiv.org/pdf/2505.09109); [UniFolding arXiv 2311.01267](https://arxiv.org/pdf/2311.01267); [Cloth Funnels arXiv 2210.09347](https://arxiv.org/pdf/2210.09347); [ICRA 2024 Cloth Competition arXiv 2508.16749](https://arxiv.org/pdf/2508.16749)
- Laundromat-operator guide to folding robots (market overview) — [Cents](https://www.trycents.com/our-2-cents/laundry-folding-robots)
- **Folding/bagging machines** (human feeds flat garment): DTF Station Tee-Folder Pro auto fold+bag **$9,995** — [EcoFreen](https://www.ecofreen.us/products/dtf-station-tee-folder-pro-automatic-shirt-folding-and-bagging-machine); Chinese fold-bag-seal machine **$4,250, ~400 pcs/hr**, 40-pc stack — [Made-in-China/Beyao](https://beyaomachinery.en.made-in-china.com/product/GtrYcdHvgehT/China-Automatic-Full-Electric-Laundry-T-Shirt-Clothes-Folding-Bagging-Machine.html); industrial fold-bag-seal **$13,800, ~500 pcs/hr**, handles tees, long sleeves, sweaters, pants, jackets — [Made-in-China/Beyao](https://beyaomachinery.en.made-in-china.com/product/DQZpeaPxJBcu/China-Automatic-Garment-Apparel-Clothes-T-Shirt-Folding-Bagging-Machine.html); US eBay listing **$29,999.99** — [eBay](https://www.ebay.com/itm/135375264925); commercial folder — [WM Machinery](https://wmmachinery.com/products/automatic-clothes-folder)
- Warehouse robotics overview 2026 (AMRs, goods-to-person, Digit/Stretch) — [RBTX](https://learn.rbtx.com/knowledge-resource/warehouse-robots/); [iFactory playbook (aggregator)](https://ifactoryapp.com/industries/delivery-operations-management/warehouse-fulfillment-robot-digit-stretch-goods-to-person)

### Inferences
- *Fully automated:* fold+bag+seal once garment is placed flat (Commercial, $4k–$30k); label printing/applying and auto-bagging/box-on-demand for shipping (Commercial — Sealed Air/Autobag, Packsize, Ranpak are standard e-com packaging vendors, though specs not pulled this run); AMR tote transport (Locus, OTTO/Rockwell, MiR — Commercial).
- *Partial / early-commercial:* AI bimanual folding of laundry (Dyna) — transferable to post-print folding but slower and costlier than fold-bag machines when a person is already present.
- *Hard:* singulating one garment from a bin of crumpled blanks, unfolding, orienting, and dressing it on a platen/hoop with mm alignment. This is the single highest-value unsolved step for a dark custom-apparel factory. Workaround: keep blanks **pre-folded/flat in known orientation** (as delivered from mills in folded dozens) so a robot can pick flat stock with suction/needle grippers rather than solve cloth singulation.
- Historical cautions (from background knowledge, not re-verified this run): Seven Dreamers' Laundroid folding machine company went bankrupt in 2019; FoldiMate consumer folder did not reach mass market. These support "dedicated cloth-handling hardware has a poor track record; AI-generalist bimanual robots are the newer bet."

### Gaps
- No commercial "bin-pick and dress on platen" product found from Fizyr, Covariant, Ambi, or Kornit automation partners.
- Sheng/Jaguar folding machine specs, Sealed Air/Packsize/Ranpak pricing, AMR pricing not retrieved.
- Dyna pricing/RaaS rates and throughput (items/hr) not found.

---

## 5. Existing near-dark apparel microfactories and lessons

### Takeaway
No verified fully dark custom apparel factory exists as of Oct 2026. Most automated examples are "lights-sparse": Kornit-style on-demand DTG lines (one loader per 400 gph), POD fulfillment centers, and Sewbot worklines. Adidas Speedfactory (2016–2020) is the cautionary tale: automation alone didn't overcome cost, scalability, and supplier-ecosystem issues.

### Cited Findings
- Adidas Speedfactory: origin in Germany's Autonomik 4.0 program (2013) through closure in 2020; achieved rapid small-batch production and brand visibility but "failed to deliver scalable, cost-effective re-shoring" — [ResearchGate case study (2025)](https://www.researchgate.net/publication/392398739_Re-Shoring_Robots_and_Reality_Case_Study_adidas_SPEEDFACTORY)
- Adidas closed Ansbach (Germany) and Atlanta Speedfactories, moving the technology to Asian suppliers (announced Nov 2019) — [Supply Chain Dive](https://www.supplychaindive.com/news/adidas-moves-high-tech-speedfactory-asia-factory-us-germany/567137/); [Quartz](https://qz.com/1746152/adidas-is-shutting-down-its-speedfactories-in-germany-and-the-us)
- Lessons: re-shoring requires rethinking the whole supply chain (dense supplier web refined over decades); high costs, limited scalability, complex processes robots couldn't handle; customization ended up as localized variants, not mass custom — [Supply Chain Dive "Learning from Adidas' Speedfactory blunder"](https://www.supplychaindive.com/news/adidas-speedfactory-blunder-distributed-operations/571678/); [Supply Chain Nuggets](https://supplychainnuggets.com/why-the-adidas-speed-factory-experiment-failed/); [3DPrint.com](https://3dprint.com/261544/the-adidas-speedfactory-a-hyped-up-failure-or-a-supply-chain-success/)
- Unspun Vega: compact microfactory concept, yarn-to-garment 3D weaving co-located with limited finishing for local production loops (referenced in an academic paper) — [arXiv 2601.02792 "Textile IR"](https://arxiv.org/pdf/2601.02792)

### Inferences
- **Realistic 2026 near-lights-out custom apparel factory (blanks-based POD/custom):**
  1. Order intake, art prep, imposition, routing — fully software-automated (AI art checks, auto-nesting for DTF gang sheets).
  2. Blank storage: AMR goods-to-person or vertical carousels deliver *flat, pre-folded* blanks by SKU/size (Commercial).
  3. Load: **human or semi-auto loader** (Kornit Apollo style) — still ~1 person per line; this is the residual labor.
  4. Print → auto-unload → cure (Kornit Apollo / M&R Passport), or DTF roll-to-roll unattended overnight.
  5. QC: camera inspection is feasible on platen/conveyor (vision QC vendors not researched).
  6. Fold-bag-seal machine with human/robot feed; auto-label and on-demand box/bag; AMR to shipping.
  7. Exceptions (misprints, thread breaks, jams, odd items like hoodies with pockets, caps) handled by a small roaming team.
  - Net: labor falls from many touches per garment to ~1–2 touches (load + exception/folding feed); "lights-out" nights are realistic only for DTF film printing, embroidery runs already hooped, and AMR replenishment.
- Speedfactory lesson for the AI planner: automate the *bottleneck* and keep flexibility; avoid bespoke robotic cells whose economics depend on volume that custom work doesn't have.

### Gaps
- Amazon Merch on Demand production facility automation: no public source retrieved.
- Shein/Zozo, Bangladesh/China automated lines: not researched in this run.
- Unspun commercial status/funding in 2025–26 not verified.

---

## 6. Labor cost structure of a US custom apparel shop

### Takeaway
Only weak benchmarks were found: print-for-pay shops average ~28.6% of revenue in labor (general printing, not apparel-specific). Screen printing labor is dominated by setup (screens, registration) and press loading; per-shirt run time is minutes for multicolor.

### Cited Findings
- Print-for-pay shops reported labor costs averaging **28.6% of revenue** (general commercial printing benchmark, year not clear) — [Printing Impressions / InfoTrends benchmark](https://piworld.com/article/infotrends-survey-gives-printing-firms-operational-technology-benchmarks/11)
- Screen-print job costing should include screen prep, press setup, printing, post-production; shops should run time studies; 1-color ~1–2 min/shirt, 4-color 3–5 min/shirt plus setup — [Print & Promo Marketing pricing guides](https://printandpromomarketing.com/article/pricing-strategies-for-screen-printing/); [comprehensive guide](https://printandpromomarketing.com/?p=161473)
- SoftWear claims manual sewing labor cost of $1+/T-shirt in traditional factories vs $0.33 with Sewbots — [RetailBoss](https://retailboss.co/sewbot-technology-drives-softwear-automation-bestseller-20-million-dollar-apparel-revolution/)

### Inferences
- Labor-hour hotspots by process (inferred from equipment design and the above): screen — screen making/reclaim, setup/registration, loading; DTG — pretreat (if not inline), loading, curing handling; DTF — weeding none, but heat-press placement; embroidery — hooping/unhooping and trimming; all — pick/pack/fold/bag and customer-service/art.
- Loading/unloading and pick/fold/pack plausibly account for the majority of direct touch labor in a DTG/POD shop, which is why auto-unloaders and fold-bag machines have <1-yr paybacks.

### Gaps
- No apparel-specific labor-share benchmark (e.g., from Printwear/Impressions State of the Industry) found in this run; recommend the report writer flag this as unknown or source from other researchers.

---

## 7. Humanoid / general-purpose robot readiness for apparel work (2026–2028)

### Takeaway
As of mid/late 2026, humanoids are in paid pilots doing tote/material moves (Agility Digit at Amazon/Toyota; Figure at BMW; Apptronik at Mercedes); none are known to be doing garment dressing/printing work. Dexterous cloth tasks are being demonstrated by bimanual AI systems (PI, Dyna, Figure), but with speed/reliability below what a print line needs. Expect 2027–2028 for credible pilots in garment loading.

### Cited Findings (mostly secondary aggregators — moderate reliability)
- Agility Digit: described as the only US humanoid with sustained commercial deployment in paying facilities as of mid-2026; tote handling at Amazon; year-long Toyota pilot; RoboFab (Salem, OR) 10,000-unit annual capacity; **Digit5 unveiled Sept 15, 2026**, early access H1 2027 (aggregator claims; not verified against Agility primary) — [theresarobotforthat.com](https://theresarobotforthat.com/blog/humanoid-robot-companies-2026-complete-guide/); [jaredwatkins.com](https://www.jaredwatkins.com/research/robotics/humanoid/us-companies/); [robozaps](https://blog.robozaps.com/b/best-humanoid-robots)
- Figure 03 at BMW Spartanburg with Helix AI; Apptronik Apollo moving kits at Mercedes; Apptronik 90,000 sq ft "Robot Park" (July 2026) training Gemini Robotics, Apollo 3 targeted 2027; Tesla Optimus in internal testing, external sales forecast 2027 (aggregators) — [solidmarketresearch](https://www.solidmarketresearch.com/post/humanoid-robots-cross-the-pilot-threshold-where-factory-deployment-actually-stands-in-2026); [evsint](https://www.evsint.com/top-8-humanoid-robot-companies-2026/); [iFactory](https://ifactoryapp.com/industries/manufacturing-plant/humanoid-robots-manufacturing-floors-2026)
- Humanoids demonstrated laundry folding at CES 2026; DYNA 2.1 humanoid running laundry shifts with error recovery (Sept 2026) — [Robb Report](https://robbreport.com/gear/personal-technology/humanoid-robots-ces-1237497312/); [Interesting Engineering](https://interestingengineering.com/ai-robotics/watch-new-humanoid-robot-unloads-laundry-and-folds-towels-without-human-help)

### Inferences
- Readiness for apparel tasks: tote/blank transport — Pilot→Early-commercial (humanoids) but AMRs are cheaper and Commercial; folding — Early-commercial (fixed bimanual stations, e.g., Dyna); platen loading/hooping — Lab-demo/Pilot at best by 2026; likely pilots 2027–2028.
- For a small/mid custom shop, a fixed bimanual AI arm station (non-humanoid) at the load point is the more likely first deployment than a humanoid.

### Gaps
- No primary-source confirmation (company press releases) for Digit5, Apptronik Robot Park, or Figure BMW scale in this run; 1X and Unitree apparel relevance not researched.
- No public data on humanoid/VLA cycle times for garment loading.

---

## Summary step map (for report writer)

| Step | Fully automatable today | Partially | Hard | Example kit / cost / throughput | Readiness |
|---|---|---|---|---|---|
| Order/art/routing | Yes | AI art QA | — | Software | Commercial |
| Blank storage/retrieval | AMR / carousel to station | — | Bin singulation of loose blanks | Locus/OTTO/MiR (cost not sourced) | Commercial |
| Garment load on platen | — | Kornit Apollo semi-auto loader | Autonomous pick+dress | Apollo 400 gph | Early-commercial (semi) |
| DTG print + pretreat + cure | Yes | — | — | Kornit Atlas MAX PLUS 150 gph; Apollo 400 gph | Commercial |
| Screen print | Print + unload | ROQ auto platen swap; screen making | Loading, ink mixing, setup | M&R Passport ~1,200 pcs/hr unload | Commercial |
| DTF film | Print+powder+cure unattended | Heat-press application | Placing garment/transfer | Roland TY-300+shaker $28,995 | Commercial |
| Embroidery | Stitching, color change, trims | Hooping (magnetic hoops ~30 s) | Robotic hooping | Tajima/ZSK multi-head | Commercial / hooping manual |
| Cutting | Yes | — | — | Gerber Atria, Lectra Virga | Commercial |
| Sewing | Simple flat goods; basic tees (Sewbot) | — | General 3D garments, small batches | Sewbot: 22 s/shirt claim, 3rd gen H1 2026 | Early-commercial |
| QC | Vision inspection feasible | — | Subjective defects | not sourced | Pilot/Commercial (unverified) |
| Fold + bag + seal | Yes (human/robot feed) | AI bimanual folding (Dyna) | Unstructured garments | $4k–$30k, 400–500 pcs/hr | Commercial |
| Label/pack/ship | Yes | — | — | Autobag/Packsize (not sourced) | Commercial |
