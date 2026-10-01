# MIT Alternatives to the SHED for CNC Machining and Metal 3D Printing (verified, October 2026)

Research date: 2026-10-01. **Method:** this pass replaces the earlier snippet-only notes in `research_notes/MIT SHED makerspace access/metal_fab_alternatives.md`. Every official page cited below was fetched in full with curl through the proxy. For make.mit.edu, a JavaScript (Softr/Airtable) site, I rendered the pages in headless Chromium and downloaded the site's own data feeds: the full equipment database (674 records) and the makerspace directory (38 records). For The Deep, I downloaded its LibCal iCal feed (135 events, Sep 5 to Dec 18, 2026). "VERIFIED" means I read the claim on a full current page. "INFERRED" means it is my conclusion. Pages that failed to load (403/404/TLS error) are listed under Gaps.

**Biggest corrections to the earlier notes:**
1. **The Hobby Shop is now free for students.** The fee table says "Student: Gratis". This is part of a 2026-27 pilot.
2. **The Deep is no longer open to all MIT students.** As of fall 2026 it is "AeroAstro The Deep", open only to people tied to AeroAstro through classes, employment, or sponsored teams. Project Manus programming moved to Building 6C.
3. **There is a big March 2026 reorganization.** The Hobby Shop, Project Manus (Metropolis, The Deep) and the Edgerton Center shops are being merged into one organization under the Edgerton Center in GUE, effective by July 1, 2026.
4. **There IS an MIT "SHED".** make.mit.edu lists **"The SHED at EHS", N52-496**. The earlier note said no MIT SHED existed. That was wrong.
5. **The Edgerton 6C equipment list now names its machines:** a Haas CNC Super Mini Mill and a Haas CNC lathe.
6. **Metal 3D printers do exist on campus,** at APT (EOS M100 laser powder-bed fusion, InnoventX binder jet, Insstek directed energy deposition). The official access policy is "available to MIT community... managed directly by the faculty member... on an ad hoc basis". This is not a walk-in service. make.mit.edu's own FAQ says there is **no 3D printing service on campus**.

---

## Q1. Edgerton 6C Student Shop: equipment, training, eligibility, fees, hours

### Takeaway
The 6C Student Shop (basement of 6C, Room 6C-006A, next to Metropolis) is a staffed metal and plastic shop. It has one Haas CNC Super Mini Mill, one Haas CNC lathe, plus manual mills and lathes. Any registered MIT student can use it after 12 hours of training (four 3-hour sessions). No fee is published. The only posted hours are for spring 2026, so fall 2026 hours have to be confirmed by email.

### Cited Findings
- VERIFIED: "Students can access training and a wide range of fabrication tools, including CNC milling machines and lathes." The shop is "Funded by MIT, with capital-equipment acquisitions covered by an endowed gift from the Lemelson Foundation". It offers "intensive training classes of 12 hours per student" and is "primarily a metal- and plastic-working shop" — [Edgerton 6C Student Shop](https://edgerton.mit.edu/for-MIT-students/student-shops/edgerton-6c-student-shop)
- VERIFIED: Location: "in the basement of 6C, just off the Infinite Corridor... The MakerLodge Metropolis Shop is next door" — [same page](https://edgerton.mit.edu/for-MIT-students/student-shops/edgerton-6c-student-shop). The make.mit.edu directory gives the room as **6C-006A** ("Edgerton Machine Shop") — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces)
- VERIFIED: Training format: "Full training for the shop takes four 3-hour-long sessions. We schedule one or two trainings a month, and each training accommodates six to eight students. So, it may take a while before we can schedule you in." If your need is urgent, email shop manager **Mark Belanger (mdbelang@mit.edu, 617-258-7728)**. Sign-up form: https://forms.gle/9oZxU479qGAsUcGFA — [Edgerton 6C Student Shop](https://edgerton.mit.edu/for-MIT-students/student-shops/edgerton-6c-student-shop)
- VERIFIED: "The monthly training program is conducted in the evenings and consists of 12 hours of hands-on instruction. Students learn the basics of milling and lathe work by making two small parts and ultimately fabricating their own steel flashlight." **Fast track:** "If you are a registered MIT student, have a well rounded familiarity with machine safety, use, tooling and proper setup, you can schedule a meeting with an instructor to gain access by taking a safety lecture, which is offered every few weeks as needed." The training page links a different sign-up form: https://forms.gle/S2ADc6wUJCTPZnFu5 — [6C Training page](https://edgerton.mit.edu/for-MIT-students/student-shops/edgerton-6c-student-shop/training)
- VERIFIED: Official equipment list: "Variety of Hand Tools", "**HAAS CNC Super Mini Mill** — The Student Shop has one Haas Super Mini Mill", "**HAAS CNC Lathe** — The Student Shop has one Haas CNC Lathe", "Dimension Elite 3D Printer" — [6C Tools & Equipment](https://edgerton.mit.edu/for-MIT-students/student-shops/edgerton-6c-student-shop/tools-equipment)
- VERIFIED: make.mit.edu's equipment database lists the "Edgerton Machine Shop [6C-006A]" with a **Bridgeport EZTrak mill, Haas Super Mini Mill, Monarch EE lathe** and a Stratasys Dimension Elite printer. It does **not** list the Haas CNC lathe, so the two official sources partly disagree — [make.mit.edu/equipment](https://make.mit.edu/equipment) (data pulled from the page's Airtable feed)
- VERIFIED: Hours. The only posted hours are a "Spring Term Calendar: Through Friday, April 17": Fri Apr 10 12:00–5:30 PM, Mon Apr 13 10:00 AM–5:30 PM, Tue Apr 14 10–11 AM / noon–1:30 / 2:30–5:30 PM, Wed Apr 15 11:00 AM–5:30 PM, Thu Apr 16 10:00 AM–5:30 PM, Fri Apr 17 12:00–5:30 PM. "No jobs may be started within 1 hour of closing." Student Shop Assistants sometimes open "Pop-Up Hours", announced on the Moira list **6cpopupusers** (questions to Dr. Jim Bales, bales@mit.edu) — [Edgerton 6C Student Shop](https://edgerton.mit.edu/for-MIT-students/student-shops/edgerton-6c-student-shop)
- VERIFIED: Usage: "Approximately 150 students used the Edgerton Student Machine Shop in Building 6C" in FY2025. The Edgerton Center manages "five student machine shops and makerspaces" and is "Open to any MIT student" — [GUE Report to the President, FY ended June 30, 2025 (PDF)](https://gue.mit.edu/wp-content/uploads/2026/01/OVC-annualreport-2025.pdf)
- VERIFIED: The shop is one of the "open-to-all" makerspaces being merged under the Edgerton Center in GUE (see Q2) — [VC for GUE letter, "Strengthening MIT's Makerspace Ecosystem", Mar 5, 2026](https://orgchart.mit.edu/letters/strengthening-mits-makerspace-ecosystem)

### Inferences
- The posted spring hours are stale as of Oct 1, 2026. April 10 fell on a Friday in 2026, so they are most likely spring 2026 hours. Fall 2026 hours are not posted; email Mark Belanger.
- I found **no fee** on any Edgerton page, and the shop says it is "Funded by MIT". So it is most likely free to students, apart from personal materials. This is inferred; no page says "free" outright.
- The page's "12 hours" is the same training as the "four 3-hour sessions". The earlier note was right on this point.

### Gaps
- Fall 2026 hours and the next training date. Neither is posted.
- Whether students pay for stock or materials.
- Whether the Haas CNC lathe is still in service, given the conflicting make.mit.edu list.

---

## Q2. The Deep, Metropolis and MAD Making (formerly Project Manus): CNC, waterjet and metal equipment; the Met Warehouse; access steps; M1T

### Takeaway
**The Deep (37-072) has left the open-to-all system.** A March 5, 2026 GUE letter moved The Deep's "function and programming" to the basement of 6C starting in summer 2026. Its fall 2026 calendar now calls it **"AeroAstro The Deep"**, "open to anyone affiliated with the department via curriculum, employment, or sponsored teams (Rocket, DBF, Satellite)". It still has a waterjet, CNC-capable ProtoTRAK mills and lathes. **Metropolis (6C-006B)** stays open to the whole MIT community. It has welding, a slip roll and a tubing roller, but **no metal-cutting CNC mill and no waterjet**. **The Met Warehouse** opened in August 2026 as the home of SA+P, and MAD is moving there too. I found **no evidence** that The Deep or Metropolis moved to the Met. Only a "MAD MET Shops" calendar exists, which looks like the old N52 MAD fabrication shop. **M1T** is a 2-hour digital or manual-fab class plus a 30-minute orientation. It does not include CNC or metal machining.

### Cited Findings
**Reorganization (official)**
- VERIFIED: GUE letter, dated March 5, 2026: MIT will integrate "the Hobby Shop (currently in the Division of Student Life), Project Manus (in the Morningside Academy for Design), and the Edgerton Center (in ... GUE) into a single organization housed within GUE". The student letter says they will be brought together "into one organization and one team **under the Edgerton Center** within ... GUE". That organization covers the Edgerton Student Machine Shop, Electronics Mezzanine, Project Lab and Area 51; the Hobby Shop; and Project Manus (Metropolis and The Deep) — [orgchart.mit.edu letter](https://orgchart.mit.edu/letters/strengthening-mits-makerspace-ecosystem)
- VERIFIED: "in June we will begin transitioning much of the function and programming of the Project Manus shop known as The Deep (37-072) to the basement of Building 6C". "The Deep, 806 sq. ft., amounts to ~6% of the total makerspace." "the operations of The Deep (37-072), including its student mentorship model, will transition to the basement of Building 6C". The restructuring was targeted "by July 1, 2026". GUE is redirecting about $400k of endowment to the open-to-all makerspaces. A new governance committee will be formed. Feedback goes to makerspaces-feedback@mit.edu — [same letter](https://orgchart.mit.edu/letters/strengthening-mits-makerspace-ecosystem)

**The Deep, fall 2026**
- VERIFIED: The Deep's LibCal calendar is titled **"AeroAstro The Deep — Departmental makerspace with mills, lathes, waterjet, etc."** — [project-manus.libcal.com/calendar/thedeep](https://project-manus.libcal.com/calendar/thedeep)
- VERIFIED: Fall 2026 event text (iCal feed, cal id 9476): "Everyone please attend a new Deep Orientation, before or during your first visit, even if you were a member when we were part of Project Manus. **The Deep in AeroAstro is open to anyone affiliated with the department via curriculum, employment, or sponsored teams (Rocket, DBF, Satellite).**" "Orientation is Step 1 to making in The Deep... Tool-specific training or checkoff is separate, and can often be done in open hours right after orientation." Location: "The Deep 37-072" — [The Deep LibCal iCal feed](https://project-manus.libcal.com/ical_subscribe.php?src=p&cid=9476)
- VERIFIED (from the iCal feed, converted to Eastern time): the October 2026 open-hours pattern is Mon 10:00–14:00, Tue 16:00–20:00, Thu 11:00–15:00 and 19:00–22:00, Fri 10:00–14:00, Sat 11:30–14:30, Sun 9:00–11:00. Orientations are Mon 10:30, Tue 16:30 and Fri 13:00. It is closed Oct 12 (Indigenous Peoples Day), over Thanksgiving break and during finals week — [The Deep iCal feed](https://project-manus.libcal.com/ical_subscribe.php?src=p&cid=9476)
- VERIFIED: make.mit.edu directory entry: "The Deep is a makerspace for AeroAstro students, staff, faculty, and department supported build teams... in the basement of Building 37 run by student mentors and AeroAstro tech instructors." Equipment: **OMAX ProtoMAX waterjet, ProtoTRAK 1630 SX lathe (×2), TRAK DPM SX2P / ProtoTRAK SMX mill (×2)**, horizontal and vertical bandsaws, drill press, resin casting bench. The entry gives the location as "37-027", which looks like a typo for 37-072 — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces) (Airtable feed)
- CONFLICT: Several pages still describe the old open-to-all policy. make.mit.edu's Help FAQ says "Metropolis and The Deep ... are open to any current MIT student, staff, faculty, associate, or affiliate with an active MIT email address... and an MIT ID card" (no: general public, most alumni, Lincoln Lab employees) — [make.mit.edu/help](https://make.mit.edu/help). make.mit.edu/start says the orientation gives "instant access to both makerspaces" — [make.mit.edu/start](https://make.mit.edu/start). MAD pages say The Deep "is open to all members of the MIT community" — [design.mit.edu/about/making](https://design.mit.edu/about/making); [design.mit.edu/about/mad-making](https://design.mit.edu/about/mad-making).

**Metropolis (6C-006B)**
- VERIFIED: "Metropolis and the Electronics Mezzanine are makerspaces open to the entire MIT Community." To find it, go down from the Infinite Corridor where Building 8 meets Building 4 and follow the teal Metropolis sign — [make.mit.edu/metropolis](https://make.mit.edu/metropolis)
- VERIFIED: Metropolis features: welding, laser cutting, FDM 3D printing, basic electronics, sewing, woodworking tools, small screen printing — [design.mit.edu/about/making](https://design.mit.edu/about/making). make.mit.edu's equipment feed adds a Miller Dynasty 210DX TIG, Millermatic 211 MIG, Miller spot welder, slip roll, tubing roller, "Othermill CNC Circuit Mill" (PCB/benchtop) and ShopBot Desktop router, but **no metal-cutting CNC mill, lathe or waterjet** — [make.mit.edu/equipment](https://make.mit.edu/equipment)
- VERIFIED: Sample day (Oct 1, 2026) on the "Open-to-All Makerspaces" calendar: Metropolis Open Hours 8–10, 11–1, 3–5, 4–6 and 5:30–9:30 PM (the last one including "Metropolis Hotwork 6C-006c" and the Electronics Mezzanine 6C-006A), plus a 30-minute "Metropolis Orientation... required before using Metropolis" — [LibCal Open-to-All Makerspaces, cal 11833](https://project-manus.libcal.com/ajax/calendar/list?c=11833&date=2026-10-01&perpage=40&page=1) (LibCal's JSON list endpoint)

**Met Warehouse**
- VERIFIED: "The Metropolitan Storage Warehouse... is opening as the new home of MIT's School of Architecture and Planning" (MIT News, Peter Dizikes, Aug 12, 2026). "The MIT Morningside Academy for Design (MAD)... will also be located in the Met Warehouse". The article does not mention The Deep, Metropolis or Project Manus moving there — [MIT News, Aug 12, 2026](https://news.mit.edu/2026/met-warehouse-opens-new-home-mit-school-architecture-planning-0812); mirrored at [design.mit.edu](https://design.mit.edu/news/met-warehouse-new-home-of-mit-school-of-architecture-and-planning)
- VERIFIED: The MIT Making LibCal has a calendar category named **"MAD MET Shops"** (cal id 19634). Its iCal feed had 0 events when I fetched it. The MAD "Making" page links the **N52 fabrication shop's** hours to this same calendar id (cid=19634, "madshops") — [LibCal calendar selector](https://project-manus.libcal.com/calendar/thedeep); [design.mit.edu/about/making](https://design.mit.edu/about/making)
- VERIFIED: MAD N52 Fabrication Shop (3rd floor, N52) is "open to the MIT community (students, faculty, and staff) after completing a general orientation". Equipment includes FDM/SLS/SLA printing, laser cutters and "Milling machines" — [design.mit.edu/about/making](https://design.mit.edu/about/making). The make.mit.edu feed lists small benchtop machines there: Little Machine Shop 3900 mill, 4100 lathe, Othermill, and ShopBot routers — [make.mit.edu/equipment](https://make.mit.edu/equipment)

**MAD Making identity and M1T**
- VERIFIED: "MAD Making, formerly known as Project Manus... operates two staffed makerspaces on campus — The Deep (Building 37) and Metropolis (Building 6C)" — [design.mit.edu/about/mad-making](https://design.mit.edu/about/mad-making). This page predates or ignores the March 2026 reorganization.
- VERIFIED: make.mit.edu footer: "Made with ❤️ by the Project Manus team **at the MIT Edgerton Center**. Copyright 2026" — [make.mit.edu](https://make.mit.edu/)
- VERIFIED: M1T has three steps. (1) A 30-minute safety orientation at Metropolis. (2) A 2-hour First Year training, either Digital Fab ("FDM 3D Printer and a Laser Cutter") or Manual Fab ("Bandsaw, the Drill Press, and Sanders"). (3) A quiz. After that you get access to Metropolis (6C-006B) and the Electronics Mezzanine (6C-006A), plus tools, a T-shirt and Makerbucks — [make.mit.edu/m1t](https://make.mit.edu/m1t). make.mit.edu/start gives the Makerbucks as "$50", and says non-first-years "can get all the same access and training" except the free toolbox and shirt — [make.mit.edu/start](https://make.mit.edu/start)

### Inferences
- **For a non-AeroAstro student, The Deep's waterjet and ProtoTRAKs are effectively no longer an open-access route as of fall 2026.** The letter says Project Manus programming and mentors moved to 6C, and the room at 37-072 continues as an AeroAstro departmental shop. I infer this by combining the letter and the LibCal text.
- The "MAD MET Shops" calendar suggests that MAD's own fabrication shop is moving, or has moved, from N52 into the Met Warehouse. That shop has only benchtop mills and lathes and no waterjet. Not confirmed.
- make.mit.edu/help, make.mit.edu/start and the design.mit.edu pages are stale about The Deep.

### Gaps
- Which Deep equipment, if any (waterjet, ProtoTRAKs), physically moved to 6C, and whether Metropolis now offers mill, lathe or waterjet training. No 6C page lists new machines.
- Current location, hours and equipment of the "MAD MET Shops". The calendar was empty and no MAD page describes them.
- Whether an AeroAstro affiliation can be gained by taking a single Course 16 class (the LibCal text says "via curriculum", which suggests yes).

---

## Q3. Hobby Shop (N51): student fee, CNC equipment, hours

### Takeaway
The Hobby Shop (N51-120, the old MIT Museum space, 265 Massachusetts Ave) is **free for MIT students** ("Gratis") in fall, spring and summer. This is a 2026-27 pilot. It has a full metal side, including a Haas Mini Mill 2, a ProtoTRAK DPM2 mill, a ProtoTRAK TRL 1630 SX lathe, an OMAX MicroJet waterjet, and MIG/TIG welders. It also has CNC wood routers. You join through a 1-hour orientation. The last fall 2026 orientation is **Friday, October 23**.

### Cited Findings
- VERIFIED: Membership fees (per term: Fall / Spring / Summer): **Student: Gratis / Gratis / Gratis**; Staff $100 / $100 / $75; Faculty $150 / $150 / $125; Alumni $225 / $225 / $200. "We accept membership fees via Cash, TechCash, Check, and Internal Requisition. We do not accept credit cards or debit cards." "We do not pro-rate term fees." — [studentlife.mit.edu Hobby Shop](https://studentlife.mit.edu/campus-communities/hobby-shop/)
- VERIFIED: "Starting in the 2026-2027 academic year, we will pilot the elimination of the Hobby Shop's student membership fee to broaden access and utilization of that shop." — [GUE letter, Mar 5, 2026](https://orgchart.mit.edu/letters/strengthening-mits-makerspace-ecosystem)
- VERIFIED: Eligibility: "open to MIT students, staff, faculty, and alumni... you must have a current, up-to-date MIT ID." Terms: Fall Sep 1–Jan 31, Spring Jan 1–May 31, Summer Jun 1–Aug 31 — [studentlife.mit.edu Hobby Shop](https://studentlife.mit.edu/campus-communities/hobby-shop/)
- VERIFIED: Joining: (1) email Hayami or Charlotte (hayami@mit.edu, creiter@mit.edu) to get access to the online scheduler "Calira"; (2) attend a one-hour in-person orientation, held Wednesdays 1:00–2:00 PM and Fridays 3:00–4:00 PM "during the first seven weeks of the term". "The last orientation for the Fall 2026 Semester will be Friday, October 23." Tours run Mondays 12:00–12:30 — [same page](https://studentlife.mit.edu/campus-communities/hobby-shop/)
- VERIFIED: Weekly hours: Mon 10–5; Tue 10–8; Wed 10–7; Thu 10–8; Fri 10–5; Sat 10–2; Sun closed. Holiday closures: Oct 10–12, 2026; Nov 11, 2026; Nov 26–28, 2026 — [same page](https://studentlife.mit.edu/campus-communities/hobby-shop/)
- VERIFIED: Location: "N51 – 120 (the old MIT Museum), 265 Massachusetts Avenue" — [same page](https://studentlife.mit.edu/campus-communities/hobby-shop/)
- VERIFIED: Metal-side machines: **Omax Micro Jet waterjet**, Do All 24" band saw, Menig Micro Mill, **ProtoTRAK TRL 1630 SX lathe**, **ProtoTRAK DPM 2 mill**, **Haas Mini Mill 2**, Bridgeport J-head mill ('70), Clausing drill press, Millermatic MIG, Miller TIG, Baileigh 14" cold saw. Wood-side machines include a **Laguna Swift 8'×4'×8" CNC router**, a ShopBot Buddy CNC router (48"×8" rotary), an Epilog Fusion 120 W laser (40"×28") and a Bridgeport M-head mill — [same page](https://studentlife.mit.edu/campus-communities/hobby-shop/)
- VERIFIED: The make.mit.edu feed for the Hobby Shop [N51-120] still lists a TechnoCNC LC 4896 router, a Harrison Alpha 330 Plus lathe, an Omax MicroMAX waterjet, a Miller 350P MIG and a Lincoln V311-T TIG — [make.mit.edu/equipment](https://make.mit.edu/equipment). These differ in places from the Hobby Shop's own list.
- VERIFIED: Instruction model: "We provide one-on-one training for every tool you'll need, tailored to your project" — [studentlife.mit.edu Hobby Shop](https://studentlife.mit.edu/campus-communities/hobby-shop/)

### Inferences
- For a student who is not on a team or in AeroAstro or MechE, the Hobby Shop is now probably the **best-equipped free option for CNC metal work plus waterjet**. It has the most generous posted hours (including Saturday) and one-on-one tool training. A student joining this term must catch an orientation by Oct 23, 2026.
- The earlier note's alumni price ($200/term) is out of date. It is now $225 for fall and spring and $200 for summer.
- The Techno CNC router in the earlier note may have been replaced by the Laguna Swift. The Hobby Shop's own page is the more authoritative source.

### Gaps
- How long the "Gratis" student pilot lasts beyond 2026-27.
- Whether students pay for materials or waterjet garnet.

---

## Q4. MITERS, Area 51, MakerWorkshop, Pappalardo, LMP/APT (and the Central Machine Shop): equipment and eligibility

### Takeaway
- **MITERS** (N52-115): open to everyone in the MIT community including former students; no fees; a small CNC mill.
- **Area 51** (N51-144): the most capable shop here (5-axis Haas, Haas VMC, OMAX 5555 waterjet), but limited to registered students active on an Edgerton club or team.
- **MakerWorkshop** (35-122; has not moved): CNC ProtoTRAK mill and OMAX 2626 waterjet, but limited to Course 2 or 16 affiliates, D-Lab, ProtoWorks members and accepted first-years.
- **Pappalardo** (3-050): class use only.
- **LMP Shop** (35-125): cost object required; consultations paused from Sep 1, 2026 to spring 2027.
- **MIT Central Machine Shop** (38-001): a paid, staffed **job shop open to any member of MIT**. Students can submit machining jobs there.

### Cited Findings
**MITERS**
- VERIFIED: "MITERS is open to everyone in the MIT community – that's current and former students, staff, and faculty. **There's no membership process or fees**; to join, just show up with a project in mind." Keyholders supervise the space. Officers (2026-27): President Maddie Beasley '27 — [miters.mit.edu/membership](https://miters.mit.edu/membership.html)
- VERIFIED: Location: "N52-115, in the same building as the MIT museum". Hours are on a calendar, and a door-status chart shows whether the shop is open ("MITERS DOOR IS CLOSED!" at the time I fetched it). Phone (617) 253-2060 — [miters.mit.edu](https://miters.mit.edu/)
- VERIFIED: Mechanical equipment: Bridgeport and Victor vertical knee mills (with DROs), Hardinge HLV 11×18" lathe, Clausing 6918 14×48" lathe, **Dyna Myte 1007 CNC mill (10×7", converted to LinuxCNC)**, vertical and horizontal metal bandsaws, and FDM printers (Zortrax M200, UP! Plus, Stratasys uPrint). "We can do frequent one-on-one trainings" — [miters.mit.edu/equipment](https://miters.mit.edu/equipment.html)
- VERIFIED: make.mit.edu adds: "MITERS often has non-standard hours, contact: keyholding@mit.edu to see if they might be currently open" — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces)

**Area 51 CNC Shop (Edgerton)**
- VERIFIED: "a central fabrication facility with CNC lathes and milling machines, an injection molding machine, and a water jet cutter" — [Area 51 Shop](https://edgerton.mit.edu/for-MIT-students/student-shops/area-51-shop)
- VERIFIED: Eligibility: "Training is available to currently registered MIT students who are actively participating on an Edgerton Center club or team... by fabricating components for their club or team projects." Contact Pat McAtamney, patmca@mit.edu, 617-324-7577. **Correction:** the current page does **not** mention D-Lab or the International Design Center community, as the earlier snippet claimed — [Area 51 Shop](https://edgerton.mit.edu/for-MIT-students/student-shops/area-51-shop); [Area 51 Training](https://edgerton.mit.edu/mit-students/student-shops/area-51-shop/training)
- VERIFIED: Equipment: **ProtoTRAK TRL 1630SX lathes (2)**, **ProtoTRAK DPM SX2P bed mills (2)**, **OMAX 5555 waterjet** (4'7"×4'7" X-Y travel, ±0.003"), **Haas Super Mini Mill with 5th axis**, **Haas CNC vertical machining center with 4th axis**, Battenfeld 25-ton injection molder — [Area 51 Tools & Equipment](https://edgerton.mit.edu/mit-students/student-shops/area-51-shop/tools-equipment). The make.mit.edu feed names the VMC as a **Haas VF2** and the room as **N51-144** — [make.mit.edu/equipment](https://make.mit.edu/equipment)
- VERIFIED: Rules: at least one other person must be present and no working alone; the manager must approve you on each machine; use is generally limited to staffed hours, and off-hours use needs case-by-case written permission; no machine-tool use from midnight to 6 AM — [Area 51 Rules of use](https://edgerton.mit.edu/mit-students/student-shops/area-51-shop/rules-use)

**MIT MakerWorkshop**
- VERIFIED: Still at **35-122**. The old makerworks.mit.edu domain no longer resolves (DNS failure); the current site is makerworkshop.mit.edu. "A student-run makerspace... We welcome all types of projects (hobby, research, class, entrepreneurship)" — [makerworkshop.mit.edu](https://makerworkshop.mit.edu/)
- VERIFIED: Eligibility (you need at least one): be a MakerWorks mentor; be affiliated with **Course 2** or in a Course 2 class; be affiliated with **Course 16** or in a Course 16 class; be a member of the sister shop **MIT ProtoWorks** (Trust Center); be in **D-Lab** or a D-Lab class; or be a first-year in MakerLodge accepted by application. Orientation is "Maker Monday", every other Monday 6–7 PM, or ad hoc with a mentor (mw-exec@mit.edu) — [Maker Monday](https://makerworkshop.mit.edu/maker-monday/)
- VERIFIED: Machines: **ProtoTRAK CNC mill**, Summit 14×40 manual lathe, **OMAX 2626 waterjet (24"×24" bed)**, Universal VLS3.50 and Epilog Fusion 40 lasers, ShopBot Desktop CNC router, 3D printers (4 Prusa MK3S+, 2 Bambu X1 Carbon), Grizzly bandsaw, Jet cold saw — [makerworkshop.mit.edu/machines](https://makerworkshop.mit.edu/machines/)
- VERIFIED: Costs: **waterjet free for 15 minutes, then $3/min** ("for usage of garnet"); 3D printing free; aluminum plate $4–$16/sq ft by thickness; round aluminum stock $1.50–$10/ft — [makerworkshop.mit.edu/costs](https://makerworkshop.mit.edu/costs/)

**Pappalardo Machine Shop (MechE)**
- VERIFIED: make.mit.edu entry, "Pappalardo Machine Shop [3-050]": "Pappalardo covers several project classes at MIT: 2.009 in the fall, 2.670 in IAP, 2.007 in the spring, and WTP in the summer." Its listed equipment includes Bridgeport-Romi EZ-Path SD and Tormax lathes, mills, MIG/TIG/spot welders, shears, brakes and a laser cutter — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces); [make.mit.edu/equipment](https://make.mit.edu/equipment)
- Search-snippet only (not fully verified): "The shop isn't for personal projects, only for class related stuff" — [web.mit.edu/mact Machine Shops at MIT](https://web.mit.edu/mact/www/Blog/MachineShops/MachineShopIndex.html). The Pappalardo Apprentice Program places apprentices who help 2.007 students — [MechE, Pappalardo Lab Apprentice](https://meche.mit.edu/featured-classes/pappalardo-lab-apprentice)

**LMP Shop**
- VERIFIED: "**The LMP Shop will be pausing researcher consultations starting September 1, 2026 until the start of the Spring 2027 term.**" "Most users will gain access... through attending classes." "Use of the water jet and 3D printers requires a cost object." CNC mills and lathes "may require extensive training". The shop "must prioritize support of the Mechanical Engineering Department". Location 35-125; hours M–F 8 AM–4:45 PM; lmp-shop@mit.edu — [lmp-shop.mit.edu](https://lmp-shop.mit.edu/)
- VERIFIED: Waterjet: OMAX 2652, **$7.00/min of cutting time, cost object required** — [LMP Waterjet specs](https://lmp-shop.mit.edu/waterjet-specs/). 3D printers (plastic only: Form 3L, Form 3+ ×4, Fortus 450mc): SLA $15 + $0.60/mL; FFF/FDM $15 flat; cost object required — [LMP 3D printer specs](https://lmp-shop.mit.edu/3d-printer-specs/)
- VERIFIED: make.mit.edu describes LMP's capabilities as "Manual and CNC Lathes, Manual and CNC Mills, Injection Molding Machines, Thermoforming Equipment, Waterjets, a CMM, 3D and 2D Printers, Sheet Metal Cutting and Bending" — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces)

**APT**: see Q5.

**MIT Central Machine Shop**
- VERIFIED: "All members of the Institute have equal access to the shop." It "provides convenient, flexible and cost effective machine shop services to the MIT research community and acts as a clearing house for sending appropriate jobs to external shops. ... personnel will work from a spectrum of rough sketches to machine drawings to create the machined product you require." It is operated by the Laboratory for Nuclear Science. Hours: 7:00 AM–3:30 PM, Mon–Fri; drop-ins welcome. Location: **Building 38-001**. Supervisor: Andrew Ryan (airyan@mit.edu, 617-324-3021); also Ernest Johnson (ej3rd@mit.edu, 617-258-0789) — [MIT Central Machine Shop](https://web.mit.edu/cmshop/); [About](https://web.mit.edu/cmshop/about.html)
- VERIFIED: make.mit.edu's outsource page lists "**MIT Central Machine Shop (On Campus)**" under "Machining / Routing" — [make.mit.edu/outsource](https://make.mit.edu/outsource)
- Search-snippet only: "For a fee based on hours worked, shop personnel will work in consultation with shop users from start to finish" — [MIT News 2016](https://news.mit.edu/2016/central-machine-shop-0222)

### Inferences
- Open to any student: **MITERS** (free, small CNC mill), **Hobby Shop** (free for students in 2026-27, Haas Mini Mill plus waterjet), **Edgerton 6C** (12-hour training, Haas mill and lathe), and the **Central Machine Shop** (paid; staff make the part).
- Open only with an affiliation: **Area 51** (Edgerton teams), **MakerWorkshop** (Course 2/16, D-Lab, ProtoWorks), **The Deep** (AeroAstro), **Pappalardo** (classes), **LMP** (cost object, MechE priority; paused this fall).
- The Central Machine Shop is the only on-campus "submit a job" route for CNC-machined metal parts that I found. Its hourly rate is not published.

### Gaps
- Central Machine Shop hourly rate and payment methods (e.g., whether students can pay personally rather than by cost object). Not on the fetched pages.
- An official current Pappalardo page. meche.mit.edu URLs returned 404 and web.mit.edu/pappalardolab returned 403.
- MITERS calendar hours (embedded Google Calendar, not parsed).

---

## Q5. Can students use, or submit jobs to, a metal 3D printer at MIT? (make.mit.edu, APT/LMP, CBA, MIT.nano, Beaver Works)

### Takeaway
**There is no open-access or service-bureau metal 3D printing for students at MIT.** make.mit.edu states plainly that "there is no 3D printing service on campus". Its equipment database (674 records across about 38 spaces) lists **no metal additive machine at all**. The only campus metal AM I found is at **APT (MIT Center for Advanced Production Technologies)**: an EOS M100 L-PBF (DMLS/SLM) machine, a Desktop Metal/ExOne InnoventX binder jetter and an Insstek MX-Lab directed energy deposition (DED) system. Each one "is located in an individual faculty laboratory", with access "available to MIT community" but "managed directly by the faculty member and their research staff on an ad hoc basis". APT takes requests through an intake form on apt.mit.edu.

### Cited Findings
- VERIFIED: make.mit.edu FAQ "Is there a 3D printing service on campus?": "**No, there is no 3D printing service on campus**, but there are many 3D printing services available commercially. We maintain a partial list at: https://make.mit.edu/outsource... There used to be an experimental 3D printing service managed by Project Manus and CopyTech. It was discontinued due to low volume and high availability of 3D printers outside the service." — [make.mit.edu/help](https://make.mit.edu/help)
- VERIFIED (my own analysis of the full make.mit.edu equipment feed, 674 records): a search for metal printing, DMLS, SLM, laser powder bed, binder jet, Desktop Metal, Metal X, Markforged metal, EOS, sinter, DED or cold spray returned **0 records**. The 69 "3D printer" records are all FDM, SLA/resin, PolyJet/Objet, Z-Corp powder or composite printers. The closest are MakerWorkshop's Markforged Mark One (Kevlar, carbon fiber, fiberglass) and a similar composite printer at MAD N52 — [make.mit.edu/equipment](https://make.mit.edu/equipment). Caveat: the database includes stale entries, such as the closed CopyTech service.
- VERIFIED: APT now calls itself "**The MIT Center for Advanced Production Technologies (APT)**". It "operates state-of-the-art advanced manufacturing facilities on campus, with a core focus on additive manufacturing". "If you'd like to access our tools, tap in to our expertise, or simply learn more, please contact us here [intake form]." It also mentions "multi-axis machining centers" — [apt.mit.edu](https://apt.mit.edu/)
- VERIFIED: **L-PBF: EOS M100** ("DMLS" or "SLM"). Circular build plate, 100 mm diameter × 97 mm height; ~45 µm minimum feature; "Nitrogen-compatible L-PBF materials (e.g. stainless steels)". "**Access and Training: System is located in an individual faculty laboratory. Access is available to MIT community and is managed directly by the faculty member and their research staff on an ad hoc basis.**" — [apt.mit.edu](https://apt.mit.edu/)
- VERIFIED: **Binder Jetting: Desktop Metal/ExOne InnoventX**. Build 160 × 65 × 65 mm; metals and ceramics (X-Series materials); "Debinding is done on-site at MIT. Sintering is done off-site using local vendors"; "Small, one-off prototype parts or material development exercises are ideal". Same faculty-lab, ad hoc access — [apt.mit.edu](https://apt.mit.edu/)
- VERIFIED: **DED: Insstek MX-Lab**. Build 150 × 150 × 150 mm; "predominately used for materials exploration and process research rather than part manufacturing". Same faculty-lab, ad hoc access — [apt.mit.edu](https://apt.mit.edu/)
- VERIFIED: **Cold spray: VRC GenIII and Raptor** are "owned and maintained by APT collaborators at the University of Massachusetts-Amherst", and work is available "on an ad hoc basis" — [apt.mit.edu](https://apt.mit.edu/)
- VERIFIED: APT's other printers are polymer only. The Fortus 450mc, Bambu H2D/P2S and Formlabs units need 1–1.5 h of familiarization training and are available only during business hours (8–12, 1–5). Mimaki, Stratasys OriginOne, BMF and UpNano units are at **MIT.nano's "5th floor prototyping"** facility. They require MIT.nano user registration and "Fab.nano" training, then allow 24/7 unsupervised use — [apt.mit.edu](https://apt.mit.edu/). So MIT.nano has **no metal AM** listed.
- VERIFIED: The LMP Shop's 3D printers are plastic only (Formlabs, Stratasys Fortus) and need a cost object — [LMP 3D printer specs](https://lmp-shop.mit.edu/3d-printer-specs/)
- VERIFIED (make.mit.edu feed): the **Center for Bits and Atoms (E15-401)** lists no metal printer. It does list strong metal subtractive tools: a Hurco VM10U 5-axis mill, Sodick SL-400G wire EDM, OMAX 5555 waterjet, FabLight 3000 metal laser cutter, Harrison lathe, and ProtoTRAK SMX mill. **Beaver Works (NE45-205)** lists only a Stratasys FDM printer, a ProtoTRAK K3 mill and a Logan lathe, and notes "Regular building access requires card provided by Alexandria Real Estate" — [make.mit.edu/equipment](https://make.mit.edu/equipment); [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces)

### Inferences
- A student's realistic routes to a **metal printed part** are: (a) an **external DMLS/binder-jet service** from make.mit.edu/outsource (Xometry, Protolabs, Craftcloud and others); or (b) through a **research connection**, such as a UROP, thesis or class in an APT-affiliated faculty lab, contacting APT through its intake form. Access to the M100 or InnoventX is at the faculty member's discretion. There is no published walk-in or job-submission process and no published rate.
- The InnoventX workflow sends sintering off-site. Even internal binder-jet parts depend on outside vendors.
- CBA has strong metal subtractive capability, but its student access policy was not verified.

### Gaps
- APT recharge rates and turnaround, and whether APT will run a one-off student job without a cost object. The intake form is not public.
- Which faculty lab houses the M100 and InnoventX. The APT page names faculty (e.g., John Hart, Cem Tasan, Elsa Olivetti) but does not map machines to labs.
- Student-team metal printers (e.g., Rocket Team). None appear in make.mit.edu.
- MIT.nano's prototyping page returned 403/404, so I relied on APT's description.

---

## Q6. make.mit.edu: what it is now, whether it replaced Mobius, and the outsource list for metal printing

### Takeaway
make.mit.edu is MIT's live maker hub, a Softr site backed by Airtable and run by "the Project Manus team at the MIT Edgerton Center" (copyright 2026). It holds the makerspace directory (38 spaces, **including "The SHED at EHS", N52-496**), the equipment search, calendars, payments and M1T sign-up. **Mobius has effectively been replaced.** The old Project Manus site, which documented Mobius, is labelled a "historical archive... no longer kept up-to-date" and points to make.mit.edu, and the Mobius app host (mitmobius.mit.edu) did not resolve. The outsource page lists 3D-printing vendors (Shapeways, 3D Hubs, Materialise, Staples, Sculpteo, Protolabs, Stratasys, Craftcloud, Xometry) **without saying which ones do metal**. It also lists the on-campus Central Machine Shop for machining.

### Cited Findings
- VERIFIED: Footer: "Made with ❤️ by the Project Manus team at the MIT Edgerton Center. Copyright 2026 Massachusetts Institute of Technology. Contact us at make at mit dot edu." Navigation includes /makerspaces, /equipment, /calendar, /credentials (MIT Touchstone sign-in), /pay, /m1t, /outsource, /free, /sources-materials, /map and /help — [make.mit.edu](https://make.mit.edu/)
- VERIFIED: "Through make.mit.edu, students and researchers can find available tools, learn how to use them, and connect with communities... a network of over 35 makerspaces across campus" — [design.mit.edu/about/mad-making](https://design.mit.edu/about/mad-making)
- VERIFIED: Payments: "Pay with Credit Card or TechCash/Makerbucks... using the new Makerspace payment web app" — [make.mit.edu/pay](https://make.mit.edu/pay)
- VERIFIED: Mobius status: the project-manus.mit.edu Mobius page now says "This is an historical archive of the Project Manus team site... no longer kept up-to-date... The Project Manus team has transitioned to the MIT Morningside Academy for Design, and up-to-date information on Making and Makerspaces at MIT can be found on our maker hub make.mit.edu." It still describes Mobius as a "mobile-friendly web-based portal" at mitmobius.mit.edu — [project-manus.mit.edu/mobius/overview.html](https://project-manus.mit.edu/mobius/overview.html). My request to https://mitmobius.mit.edu/ failed (could not connect).
- VERIFIED: make.mit.edu makerspace directory (38 entries) includes **"The SHED at EHS"**, MIT location **N52-496**: "The SHED is a special makerspace which aims to proactively integrate research, applied problem-solving and core Environmental, Health, and Safety (EHS) expertise to develop knowledge and processes that accelerate safe and broad access to advanced technologies that empower members of the MIT community". No equipment is listed for it. The MIT Making LibCal also has an "EHS The SHED" calendar (cal id 19337), which had 0 events when fetched — [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces) (Airtable feed); [LibCal calendar selector](https://project-manus.libcal.com/calendar/thedeep)
- VERIFIED: Full outsource list (page last published Sep 28, 2026): "A non-exhaustive list of vendors who will fabricate on demand and have done business with MIT."
  - **3D Printing:** Shapeways, 3D Hubs, materialise, Staples, sculpteo, Protolabs, Stratasys, Craftcloud, Xometry
  - **Laser / Waterjet Cutting:** ACP Waterjet (Local, lasers too), Boston Lasers (Local), Altec Plastics (Local), SendCutSend, Big Blue Saw, OSHCUT, Ponoko, Pololu
  - **Electronics:** OSH Park, Ninja Circuits, JLCPCB, Advanced Circuits, UPVERTER, seeed
  - **Machining / Routing:** **MIT Central Machine Shop (On Campus)**, Altec Plastics (Local), Boston Lasers (Local), 3D Hubs, Protolabs, PRINTFORM, Xometry, STAR RAPID, eMachineShop, SuNPe
  — [make.mit.edu/outsource](https://make.mit.edu/outsource)
- Correction to the earlier note: **SendCutSend IS on the MIT outsource list**, under laser/waterjet cutting — [make.mit.edu/outsource](https://make.mit.edu/outsource)
- Not verified this session (vendor sites not re-fetched; the earlier note cited them): Xometry offers DMLS metal printing — [Xometry](https://www.xometry.com/capabilities/3d-printing-service/); Protolabs offers DMLS — [Protolabs DMLS](https://www.protolabs.com/services/3d-printing/direct-metal-laser-sintering/)

### Inferences
- make.mit.edu replaced both Mobius and the Project Manus website as the "front door". Credentials appear behind Touchstone at /credentials. I infer that Mobius has been retired, based on the archive banner and the unreachable host.
- The outsource page does not mark metal capability. Among the listed vendors, Protolabs, Xometry, Craftcloud (a marketplace), Materialise, Sculpteo and 3D Hubs are the plausible metal-AM sources. This comes from general knowledge of the vendors, not from the MIT page.
- The earlier note's warning that "MIT SHED" might be RIT's SHED is out of date. An MIT SHED exists (EHS, N52-496). Its details belong to the separate SHED research thread.

### Gaps
- What /credentials shows after login (requires Touchstone).
- shed.mit.edu: the proxy log showed an earlier CONNECT to shed.mit.edu refused with 403. I did not fetch it, as it is outside this note's scope.
