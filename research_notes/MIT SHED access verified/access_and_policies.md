# MIT SHED (Safety Health Environmental Discovery Lab): Verified Access Guide and Usage Rules (as of 2026-10-01)

> **Method:** Unlike the earlier notes (`research_notes/MIT SHED makerspace access/access_and_policies.md`), which relied on search snippets, these notes come from **full page fetches (curl, HTTP 200) on 2026-10-01**:
> - Every URL in `https://shed.mit.edu/sitemap.xml` that bears on access: home, About, Capabilities, Courses, Network, Research, and Making the Makers.
> - The LibCal "EHS The SHED" calendar (calendar ID 19337), swept **day by day from 2023-09-01 to 2026-12-31** with LibCal's public list endpoint (`/ajax/calendar/list?c=19337&date=YYYY-MM-DD`).
> - Three individual SHED event pages.
> - make.mit.edu pages: home, `/m1t`, `/mentor`, `/makerspaces`.
>
> **"VERIFIED"** means I read it on the live page. **"INFERRED"** means my reasoning, not stated anywhere.
>
> **Main corrections to the earlier notes:**
> 1. The SHED's own site **has no trainings page, FAQ, policies page, hours page, or online access request form.** The official route is to **email SHED@mit.edu** (the "Become a User" button is a mailto link).
> 2. The SHED's LibCal calendar has held **only first-year M1T/MakerLodge device sessions** (Dec 2023 to Feb 2025). It has **no events at all after Feb 28, 2025**, and **none scheduled through Dec 31, 2026.** No "open hours" event has ever been posted there.
> 3. The equipment list the earlier notes flagged as uncertain (4- and 5-axis mills, waterjets, wire EDM, Beamworks femtosecond lasers) **is confirmed on the SHED's own Capabilities page.**
> 4. A dedicated contact email exists: **SHED@mit.edu**.
> 5. The SHED site is now a Webflow site. The old WordPress URLs redirect or are gone: `/spaces` redirects to `/page/capabilities`, and `/?page_id=6` serves the home page.

## 1. What the SHED is, where it is, and what is in it

### Takeaway
VERIFIED: The SHED is a multidisciplinary research and prototyping lab managed by MIT EHS. It is in Building N52, 4th floor, entered through the EHS office and lab area. It has four "core research nexus" areas: Chemistry, Biology (up to BSL-2+), Radiation & Nuclear, and Prototyping & Fabrication. These are spread over five named sub-spaces: Life Sciences Hub, Fabrication Node, Hygieneyx, Beamworks, and The Gray. The SHED presents itself first as a research lab that grants access, not as a drop-in student makerspace.

### Cited Findings
- **Self-description:** "The SHED serves as a multidisciplinary laboratory dedicated to prototyping, fabrication, and scientific discovery at MIT, offering equitable access to advanced technologies for the broader community." — [About the SHED](https://shed.mit.edu/about-the-shed)
- **Mission:** "The SHED proactively integrates research, applied problem-solving and core Environment, Health and Safety expertise to develop knowledge and processes that accelerate safe and broad access to advanced technologies that empower members of the MIT community in furtherance of the Institution's mission." — [About the SHED](https://shed.mit.edu/about-the-shed)
- **Operator (LibCal wording):** "The SHED (Safety Health Environmental Discovery lab) is a makerspace managed by MIT EHS, accelerating safe and broad access to advanced technologies." The calendar is titled "EHS The SHED." — [LibCal EHS The SHED](https://project-manus.libcal.com/calendar/shed)
- **Leadership (VERIFIED on About page):**
  - Tolga Durak, "Founding Director, Principal Investigator."
  - Faculty Advisors: Martin Culpepper, Moungi Bawendi, Anne White, Peter Dedon, Susan Silbey.
  - Source: [About the SHED](https://shed.mit.edu/about-the-shed)
- **"The SHED EHS Team" (VERIFIED):** Aalaei, Iraj; Casavant, Alec; Kalil, Andy; Kirby, Bob; MacLeod, Joe; Marketon, Melanie; Sain, Chris — [About the SHED](https://shed.mit.edu/about-the-shed)
- **Location and directions (VERIFIED, quoted from event pages):** "Directions: Building N52, 4th Floor. Enter N52 from the 265 Massachusetts Ave / Front St entrance. Take the elevator or stairs to the 4th floor and enter the EHS office and lab area. Proceed straight from the EHS entrance to the SHED." Location field: "The SHED N52-4th Floor … MIT Cambridge." — [LibCal event 13637298](https://project-manus.libcal.com/event/13637298); [LibCal event 14125842](https://project-manus.libcal.com/event/14125842)
- **Mailing address in site footer:** "Safety Health Environmental Discovery Lab, Massachusetts Institute of Technology, 77 Massachusetts Avenue, Cambridge, MA, USA" (generic MIT address) — [shed.mit.edu](https://shed.mit.edu/)
- **Capabilities, Chemistry (VERIFIED):** "Designed as a wet-chemistry space. The section includes chemical fume hoods, specially designed perchloric acid fume hood with wash-down capability…" Hygieneyx is "an industrial hygiene testing lab" — [Capabilities](https://shed.mit.edu/page/capabilities)
- **Capabilities, Biology (VERIFIED):** "can accommodate experiments up to biosafety level 2+," with "a dedicated biofabrication suite with Bioreactors, 3D Bio printers, biosafety cabinets" — [Capabilities](https://shed.mit.edu/page/capabilities)
- **Capabilities, Radiation & Nuclear (VERIFIED):**
  - "connected to MIT's nuclear sciences research ecosystem including the Nuclear Reactor Lab."
  - Equipment: HPGe and NaI detectors, liquid scintillation counters, alpha/gamma spectroscopy, and more.
  - "Beamworks includes a dedicated training section for hands-on training on the user of optics, lasers and stages and dedicated high power laser research space fitted with femto second laser systems."
  - Source: [Capabilities](https://shed.mit.edu/page/capabilities)
- **Capabilities, Prototyping & Fabrication (VERIFIED, resolves an earlier gap):**
  - "The prototyping space includes a variety of hand tools, section for electronics work, supports digital design & modeling and enables additive manufacturing through a suite of FDM/ SLS / DLP / PolyJet / Metal 3D printers."
  - "The fabrication space enables CNC machining and subtractive manufacturing by 4-axis & 5-axis mills, lathes, waterjets, vacuum formers, laser cutters & engraves and wire EDM."
  - Source: [Capabilities](https://shed.mit.edu/page/capabilities)
- **Named sub-spaces (VERIFIED):**
  - "Life Sciences Hub – Main lab location for life sciences research, radio-analytics and prototyping sections"
  - "Fabrication Node – Dedicated space for machining, fabrication and metal works"
  - "Hygieneyx – Dedicated industrial hygiene lab for material testing and analysis"
  - "Beamworks – Laser labs for hands on training and high-power laser research"
  - "The Gray – Gamma and X-ray based irradiators used for life sciences and materials radiation research"
  - Source: [Capabilities](https://shed.mit.edu/page/capabilities)
- **Courses supported (VERIFIED list):** 2.007, 2.009, 2.797 (meets with 20.310), 16.S811, 22.015, 22.033, 22.09. The page says the SHED offers "a range of courses from the MIT School of Engineering" — [Courses](https://shed.mit.edu/page/courses); [home](https://shed.mit.edu/)
- **SHED Network (VERIFIED):** MIT internal contributors include Beaver Works, BioMakers, DMSE Breakerspace, EHS, Trust Center, IMES, NSE, MIT.nano, the Nuclear Reactor Lab, PSFC, RLE, and SMART. External partners include the Stanford PRL, Harvard i-lab, UCL Institute of Making, Yale CEID, and others — [Network](https://shed.mit.edu/tile-page/network)
- **Site map (VERIFIED):** `sitemap.xml` lists only home, search, style-guide, about-the-shed, capabilities, courses, research project pages, network, and publications-patents. It has **no** trainings, FAQ, hours, policies, people/mentors, or contact page. `/faq`, `/contact`, and `/page/people` return 404 — [sitemap](https://shed.mit.edu/sitemap.xml)

### Inferences
- INFERRED: Because the SHED's hazard classes include BSL-2+, perchloric acid, radioactive sources and irradiators, and high-power lasers, access to those areas is almost certainly governed by the matching EHS lab-specific programs (biosafety, radiation protection, laser safety), not by a generic makerspace orientation. No SHED page states this.
- INFERRED: The SHED is not on the Project Manus "Open-to-All Makerspaces" LibCal calendar; its calendar is separate. It should not be assumed to work like Metropolis, where a 30-minute orientation gives access.

### Gaps
- No floor plan, room numbers for each sub-space, or opening date on any SHED page. The earlier "N52-496" figure is Durak's office per the earlier notes and is not re-verified here.

## 2. Who is eligible, and are there fees?

### Takeaway
VERIFIED: The SHED says it offers access to "MIT faculty, staff, researchers, students, and thought leaders." The only published way to become a user is to **email SHED@mit.edu**. **No eligibility criteria, fees, membership tiers, or course requirements are published** on shed.mit.edu.

### Cited Findings
- **"Get Involved" (VERIFIED, quoted):** "We offer access to MIT faculty, staff, researchers, students, and thought leaders, knowing that participation from a broad mix of people and experience is the most effective way to rapidly develop better risk management, safer use, and more equitable access across campus." The buttons below are "Become a User" → `mailto:SHED@mit.edu` and "Join the Network" → `mailto:SHED@mit.edu` — [shed.mit.edu home](https://shed.mit.edu/)
- **Capabilities page:** Also ends with a "Become a User" button → `mailto:SHED@mit.edu` — [Capabilities](https://shed.mit.edu/page/capabilities)
- **Who users are (VERIFIED):** "Users: Diverse group of individuals who seek to advance knowledge across various disciplines leveraging SHED's resources and expertise to achieve their research and innovation goals." — [About the SHED](https://shed.mit.edu/about-the-shed)
- **First-year M1T at the SHED (VERIFIED):** First-years can take an alternative version of M1T at the SHED. Students "will receive the same M1T completion credit (50 Makerbucks, a T-Shirt, and tools) as well as novice laser cutter and 3D printing credentials." — [LibCal event 13637298](https://project-manus.libcal.com/event/13637298)

### Inferences
- INFERRED: The "users" framing ("research and innovation goals") suggests access is granted case by case, based on a project or research need, after the email inquiry. It does not look like a general drop-in membership.
- INFERRED: No fees are published. Whether materials or machine time are charged, for example through Mobius or a cost object, is unknown.

### Gaps
- No published eligibility rules (undergrad vs. grad), fee schedule, or personal vs. coursework project policy. A student must ask SHED@mit.edu.

## 3. How a student gets access, step by step (trainings, credentials, Mobius)

### Takeaway
VERIFIED: The SHED publishes **no step-by-step access procedure, no list of required trainings, and no online request form.** The official entry point is an email to SHED@mit.edu. The one documented pathway with published training content is the **first-year M1T device track** that ran at the SHED from Dec 2023 to Feb 2025. It awarded novice laser cutter and 3D printing credentials. That track has not appeared on the SHED calendar since Feb 2025.

### Cited Findings
- **Entry point (VERIFIED):** "Become a User" = `mailto:SHED@mit.edu` — [shed.mit.edu](https://shed.mit.edu/); [Capabilities](https://shed.mit.edu/page/capabilities)
- **Who designs trainings (VERIFIED):** "Student and researcher mentors are the SHED's community leaders, from designing trainings to hosting events and open hours to determining future direction and priorities for the space. They represent every area of interest and are prepared to support users in the intricacies of every equipment, tool and process." — [About the SHED](https://shed.mit.edu/about-the-shed)
- **M1T at the SHED: format (VERIFIED, quoted):** "This is a new alternative version of Makerspace First Year Training taught at the SHED makerspace. It is a slightly more in-depth program which takes about twice the time of traditional M1T (4 hours instead of 2 hours) but steps First Years through making a complete device (either a Lixie Clock or a Zoetrope). It introduces a different set of equipment and skills to complete the device (laser cutter, 3D printer, electronics, and soldering)." Also: "consists of TWO 2-hour PARTS. You need to sign up for and attend both PART 1 and PART 2." — [LibCal event 14125842](https://project-manus.libcal.com/event/14125842)
- **M1T at the SHED: credentials (VERIFIED):** Completers receive "novice laser cutter and 3D printing credentials" in addition to standard M1T completion credit — [LibCal event 13637298](https://project-manus.libcal.com/event/13637298)
- **M1T attendance rules (VERIFIED, quoted from SHED event pages):**
  - "If you don't show up to your training session you will NOT be able to sign up for another session without a reasonable explanation or a note from S^3. If you cancel the day of your training session without a reasonable explanation, you will also NOT be able to signup for another training session. Please contact ml-questions@mit.edu if you have questions about this policy."
  - "Please be on time… Training will begin, at the latest, 5 minutes after the scheduled start time."
  - Source: [LibCal event 14128285](https://project-manus.libcal.com/event/14128285)
- **Event organizer** listed on these SHED M1T events: "Jack Greenfield" — [LibCal event 13637298](https://project-manus.libcal.com/event/13637298)
- **Current M1T calendar link (VERIFIED in page source):** make.mit.edu/m1t's "Open FIRST YEAR TRAINING CALENDAR" button links to `https://project-manus.libcal.com/calendar/shed?cid=11833&t=m&d=0000-00-00&cal=11833&ct=39906&inc=0`. The path says "shed," but the `cid=11833` parameter selects a different calendar, and its fall-2026 events are Metropolis/Edgerton events, not SHED events — [make.mit.edu/m1t](https://make.mit.edu/m1t); [LibCal](https://project-manus.libcal.com/calendar/shed?cid=11833&t=m&d=0000-00-00&cal=11833&ct=39906&inc=0)
- **Mobius / make.mit.edu (VERIFIED):** `https://mobius.mit.edu/` now redirects to `https://make.mit.edu/` (title "MIT MAKE"). The site is a JavaScript-rendered Softr app; its static HTML holds no SHED space listing. `/makerspaces` returned 200 but the space list loads client-side, so I could not read it. No Touchstone redirect happened on the public pages fetched — [make.mit.edu](https://make.mit.edu/); [make.mit.edu/makerspaces](https://make.mit.edu/makerspaces)

### Inferences (most likely student path, INFERRED, not published)
1. **First-year undergrad:** Check the M1T training calendar (linked from [make.mit.edu/m1t](https://make.mit.edu/m1t)) for any "M1T Device … at the SHED" sessions. None are posted for fall 2026 as of 2026-10-01. Otherwise take standard M1T at Metropolis.
2. **Any student:** Email **SHED@mit.edu** ("Become a User"). Describe your project or research need, which equipment or sub-space you need (for example Fabrication Node, Beamworks, or the bio suite), your department or PI, and any course link (2.007, 2.009, 22.09, and so on).
3. Expect EHS-assigned trainings in Atlas that match the hazards involved: shop safety, laser, biosafety, or radiation. Then expect a hands-on checkout with SHED mentors or EHS staff. This is inferred from the EHS-run, multi-hazard nature of the space and the "mentors … designing trainings" wording. The SHED does not list specific Atlas courses.
4. Credentials are probably recorded in Mobius/make.mit.edu like other MIT shops, since M1T-at-SHED awarded "novice laser cutter and 3D printing credentials." This is not verified for SHED-specific equipment.

### Gaps
- No SHED-specific Atlas course list, orientation, machine checkout list, card-access procedure, or request form exists on any public page.
- Whether the SHED appears as a space in make.mit.edu/Mobius could not be checked: the space list renders client-side and logged-in views need MIT credentials.

## 4. Hours, staffed vs. unstaffed use, 24/7 access, reservations

### Takeaway
VERIFIED: No SHED page publishes hours, a card-access policy, or a reservation system. The SHED's About page says mentors host "events and open hours," but **the LibCal SHED calendar has never posted an open-hours event.** Its entire history (100 events, Dec 13, 2023 to Feb 28, 2025) is first-year M1T/MakerLodge device sessions. **Nothing is scheduled from Mar 2025 through Dec 31, 2026.**

### Cited Findings
- **Open hours mentioned (VERIFIED):** Mentors host "events and open hours." — [About the SHED](https://shed.mit.edu/about-the-shed)
- **LibCal SHED calendar (ID 19337) day-by-day sweep, 2023-09-01 to 2026-12-31 (VERIFIED via the public list API behind [the calendar page](https://project-manus.libcal.com/calendar/shed)):**
  - **Dec 13, 2023 to Apr 12, 2024:** 32 events, all "FIRST YEARS: MakerLodge Device LIXIE CLOCK Project at the SHED (PART 1/PART 2)."
  - **Sep 9 to Dec 10, 2024:** about 60 events, "FIRST YEARS: M1T Device LIXIE CLOCK Project at the SHED" and "… ZOETROPE Project at the SHED" (Parts 1 and 2), each 2 hours. Example: Sep 9, 2024, 1:00–3:00 pm ([event 13118320](https://project-manus.libcal.com/event/13118320)); Dec 6, 2024, 1:00–3:00 pm ([event 13637298](https://project-manus.libcal.com/event/13637298)); Dec 10, 2024, 5:00–7:00 pm ([event 13690609](https://project-manus.libcal.com/event/13690609)).
  - **Feb 18 to Feb 28, 2025:** 9 events. Examples: ZOETROPE Part 1 on Feb 18, 2025, 10 am–12 pm ([event 14125837](https://project-manus.libcal.com/event/14125837)) and Feb 20, 2025, 3–5 pm ([event 14125842](https://project-manus.libcal.com/event/14125842)); LIXIE CLOCK Part 2 on Feb 24, 2025, 3–5 pm ([event 14128285](https://project-manus.libcal.com/event/14128285)); ZOETROPE Part 2 on Feb 28, 2025, 11 am–1 pm ([event 14125868](https://project-manus.libcal.com/event/14125868)). **This is the last SHED event.**
  - **Mar 1, 2025 to Dec 31, 2026:** **zero events** on the SHED calendar.
  - The iCal feed (`ical_subscribe.php?src=p&cid=19337`) also contains 0 VEVENTs.
  - Event category used: "M1T" (category 39906).
- **Fall 2026 cross-check (VERIFIED):** All 737 events across all MIT Making LibCal calendars from Aug 15 to Dec 31, 2026 were checked. **None are located at the SHED or N52.** Text matches for "shed" or "ehs" were all Edgerton Student Shop (6C-006A) or Metropolis Electronics Mezzanine events. The calendars listed on LibCal are AeroAstro The Deep, Arch Shops, EHS The SHED, MAD MET Shops, Maker Events, Open-to-All Makerspaces, and The Voxel Lab at iHQ — [MIT Making LibCal](https://project-manus.libcal.com/calendar/shed)

### Inferences
- INFERRED: The SHED sits inside the EHS office and lab suite. It holds BSL-2+, radiological, and high-power laser areas, and posts no public hours. So access is almost certainly arranged by appointment or project with SHED/EHS staff, not 24/7 or unstaffed card access. Do not tell students they can drop in.
- INFERRED: The M1T-at-SHED program appears to have paused or ended after spring 2025, or moved off this calendar. I cannot tell which.

### Gaps
- No hours, card-access, working-alone/buddy, or reservation rules are published anywhere I could reach. Students must ask SHED@mit.edu.

## 5. Contact and becoming a mentor

### Takeaway
VERIFIED: **SHED@mit.edu** is the single published contact for becoming a user, joining the network, becoming a mentor, and general questions. The About page lists 34 active student and researcher mentors. Other contacts: LinkedIn "SHED at MIT"; ml-questions@mit.edu for M1T attendance-policy questions; makerspace-questions@mit.edu for LibCal tech support.

### Cited Findings
- **Footer (VERIFIED):** "SHED@mit.edu," "Contact Us" (mailto:SHED@mit.edu), and "LinkedIn: SHED at MIT" (https://www.linkedin.com/company/the-shed-at-mit/) — [shed.mit.edu](https://shed.mit.edu/)
- **"Become a Mentor"** button → `mailto:SHED@mit.edu` — [About the SHED](https://shed.mit.edu/about-the-shed)
- **"Active Mentors" (VERIFIED, 34 names):** Afghah, Bai, Barakat, Beatie, Bawa, A. Chen, An. Chen, Chih, Forsgren, Gazdus, George-Akpenyi, Greene, Haile, Hines, Jebran, John, Ladd, Lin, Macon, Marschner, McCoy, Mohammed, Ortiz, Qu, Reyes, Rupani, Sawhney, Schwendeman, Tang, Tjong, Ye, Yong, Zhang, Zhu — [About the SHED](https://shed.mit.edu/about-the-shed)
- **M1T policy contact (VERIFIED):** "Please contact ml-questions@mit.edu if you have questions about this policy." — [LibCal event 14128285](https://project-manus.libcal.com/event/14128285)
- **LibCal footer (VERIFIED):** "Report a tech support issue" → makerspace-questions@mit.edu — [LibCal](https://project-manus.libcal.com/calendar/shed)
- **Project Manus mentor program (separate from SHED):** [make.mit.edu/mentor](https://make.mit.edu/mentor) returned 200, but its content renders client-side. I did not verify its text this round. The earlier notes quoted it as saying mentors "get off-hours access … as well as a materials allowance," but that applies to Project Manus, not the SHED.

### Inferences
- INFERRED: Several SHED mentors (Tjong, Zhang, Hines, McCoy, Barakat) also appear on the "Making the Makers" research team. This suggests the mentor corps overlaps with SHED-housed research on maker training — [Making the Makers](https://shed.mit.edu/page/making-the-makers)

### Gaps
- No published mentor requirements, pay or benefits, or application timeline for the SHED. Ask via SHED@mit.edu.
- The page date and last-updated date of the mentor list are not shown. The sitemap has no `<lastmod>` values.
