# AI/Technical Architecture for an Automation-Planning System: Custom Model vs. Frontier LLM + Retrieval + Tools

Research date: 2026-10-04. Scope: whether a well-funded team should train/fine-tune a custom model or build on frontier LLMs (Claude/GPT/Gemini) with prompts, retrieval and tools, for a system that ingests manufacturer data (text, photos, video, floor plans, CAD, ERP exports) and outputs engineering-grade automation plans (equipment selection, robotic cell design, layout, throughput simulation, ROI, BOM, integration specs). Budget/skills are not a constraint; the only question is which approach actually performs better.

Overall verdict (opinion, supported by findings below): **Use a frontier LLM as the reasoning/orchestration layer, surrounded by (a) a structured component knowledge graph and retrieval, (b) deterministic engineering tools (solvers, DES, robot simulators, CAD kernels) that produce the numbers, (c) narrow specialist perception models where pixels/video/3D are involved, and (d) verification loops plus human engineer sign-off.** Do not pretrain a custom "manufacturing LLM". Fine-tune/train narrow models (perception, cost/cycle-time estimators, ranking) once proprietary labeled project data exists. Every domain-model-vs-frontier comparison found shows that general reasoning ability wins over domain pretraining. Fine-tuning wins only on narrow, fixed-schema tasks.

---

## 1. Evidence: domain-specific/custom models vs. frontier general models (and fine-tuning vs. RAG)

### Takeaway
Across finance, medicine and law, frontier generalist models given good prompts, retrieval and tools matched or beat purpose-trained domain models on reasoning-heavy tasks, and each new frontier generation made the domain models obsolete. Fine-tuned or specialist models still win on narrow structured-prediction or classification tasks with fixed taxonomies/schemas (NER, fixed-label classification, vulnerability detection). For knowledge injection, RAG beats unsupervised fine-tuning by a wide margin. Supervised fine-tuning gives modest gains that add on top of RAG.

### Cited Findings
**BloombergGPT vs GPT-4 (finance)**
- BloombergGPT is a 50B-parameter model trained on a mix of financial and general data. Bloomberg reported it significantly outperformed existing models on financial tasks — [BloombergGPT paper summary](https://deepai.org/publication/bloomberggpt-a-large-language-model-for-finance)
- Li et al. (EMNLP 2023 Industry track, "Are ChatGPT and GPT-4 General-Purpose Solvers for Financial Text Analytics?") tested 8 datasets across 5 task types. Conclusion: "ChatGPT and GPT-4 significantly outperforms others in almost all datasets except the NER task… both models perform better on financial NLP tasks than BloombergGPT, which was specifically trained on financial corpora." — [arXiv 2305.05862](https://arxiv.org/pdf/2305.05862)
- On ConvFinQA, ChatGPT (GPT-3.5) scored 59.86% vs BloombergGPT 43.41%. On FinQA, GPT-4 zero-shot scored 68.79%. Chain-of-thought added roughly 15 points for GPT-4, and the best GPT-4 result "exceeds the fine-tuned FinQANet model with a quite significant margin" — [arXiv 2305.05862](https://arxiv.org/pdf/2305.05862)
- Exceptions where specialists won: on financial NER, "GPT-4 is less effective than BloombergGPT". A CRF model trained on in-domain data (FIN5) "performs better than all the other models", although the CRF degrades badly under domain shift. On FPB sentiment, few-shot GPT-4 was only "comparable to fine-tuned FinBert" — [arXiv 2305.05862](https://arxiv.org/pdf/2305.05862)
- The authors also noted that GPT-4's 70%+ QA accuracy "still cannot match that of professionals" — [arXiv 2305.05862](https://arxiv.org/pdf/2305.05862)

**Medicine: Medprompt vs Med-PaLM 2**
- Microsoft's "Can Generalist Foundation Models Outcompete Special-Purpose Tuning? Case Study in Medicine" (Nov 2023): GPT-4 with Medprompt (a combination of prompting strategies: dynamic few-shot retrieval, self-generated CoT, choice-shuffle ensembling) reached SOTA on all 9 MultiMedQA datasets. It beat specialist Med-PaLM 2 "by a large margin with an order of magnitude fewer calls". It cut MedQA error by 27% and passed 90% for the first time — [Microsoft Research](https://www.microsoft.com/en-us/research/publication/can-generalist-foundation-models-outcompete-special-purpose-tuning-case-study-in-medicine/); [arXiv 2311.16452](https://arxiv.org/html/2311.16452v1)
- The same strategy also worked on electrical engineering, ML, accounting, law, nursing and clinical psychology exams — [arXiv 2311.16452](https://arxiv.org/html/2311.16452v1)

**Legal: Harvey's trajectory (an important case study)**
- In 2024, Harvey partnered with OpenAI on a custom-trained case-law model. OpenAI's account: "Foundation models were strong at reasoning, but lacked the knowledge required for legal work". Harvey had tried API fine-tuning and RAG and "ran into limitations" — [OpenAI customer story](https://openai.com/index/harvey)
- In 2025, Harvey expanded to Anthropic and Google models (via AWS Bedrock and Google Vertex) after internal benchmarks showed different models excel at different legal tasks. Its public BigLaw Bench showed Gemini 2.5 Pro strong at drafting but weaker at trial prep, where o3 and Claude 3.7 Sonnet were stronger — [Harvey blog](https://www.harvey.ai/blog/expanding-harveys-model-offerings); [Maginative](https://www.maginative.com/article/harvey-ai-now-offers-anthropic-and-google-models/)

**RAG vs fine-tuning studies**
- Ovadia et al. (Microsoft Israel, EMNLP 2024, "Fine-Tuning or Retrieval? Comparing Knowledge Injection in LLMs") found RAG consistently outperformed unsupervised fine-tuning, for both knowledge already seen in training and entirely new knowledge. LLMs "struggle to learn new factual information through unsupervised fine-tuning". Exposing the model to many paraphrases of each fact helps — [arXiv 2312.05934](https://export.arxiv.org/abs/2312.05934?context=cs); [ACL Anthology](https://preview.aclanthology.org/setup/2024.emnlp-main.15)
- On the post-cutoff current-events task, the secondary summary reports RAG at about 0.875 accuracy vs fine-tuning with paraphrases at about 0.50–0.51 (base about 0.35–0.48) — [Beancount research log summary](https://beancount.io/bean-labs/research-logs/2026/05/20/fine-tuning-or-retrieval-knowledge-injection-llms) (secondary; consistent with the paper's headline claim)
- Microsoft "RAG vs Fine-tuning: Pipelines, Tradeoffs, and a Case Study on Agriculture" (Balaguer et al., Jan 2024; Llama2-13B, GPT-3.5, GPT-4): fine-tuning added more than 6 percentage points of accuracy, and "this is cumulative with RAG, which increases accuracy by 5 p.p. further" — [arXiv 2401.08406](https://arxiv.org/html/2401.08406v2); [Microsoft Research](https://www.microsoft.com/en-us/research/?p=1008486)

**Recent (2025–2026) evidence on when specialists win**
- Security document classification (2026): a fine-tuned local LLM beat frontier models by 15–20 pp on fixed-taxonomy benchmarks and by 7.4 pp on real-data external validation — [arXiv 2605.20368](https://arxiv.org/pdf/2605.20368)
- Cybersecurity vulnerability benchmarks (2026): a domain-specialized model had the best F1 (0.873) and beat every frontier model tested — [arXiv 2605.23243](https://arxiv.org/html/2605.23243v3)
- Counter-example, seed science (SeedBench, 2025): domain fine-tuned 7B/13B models (PLLaMa, Aksara) did worse than general-purpose models, partly because fine-tuning eroded instruction-following — [arXiv 2505.13220](https://arxiv.org/pdf/2505.13220)
- One synthesis of these benchmarks: tasks that demand strict adherence to fixed schemas/output protocols favor fine-tuned models. General models produce more schema-violating outputs — [arXiv 2605.20368](https://arxiv.org/pdf/2605.20368); [Kili Technology 2026 vertical AI map](https://kili-technology.com/blog/domain-specific-llm-benchmarks-guide) (secondary)

### Inferences
- **Custom models lose** on open-ended multi-step reasoning, breadth and synthesis. Automation planning is exactly that kind of work: interpreting messy customer data, trading off cycle time, cost, floor space and safety, and writing integration specs. Domain-pretraining a model on manufacturing text would repeat BloombergGPT. The model would be overtaken by the next frontier release within 6–12 months while costing large sums.
- **Custom models win** on (1) narrow perception (detecting machines and workstations in photos, recognizing operator actions in video), (2) fixed-schema structured prediction (mapping a part description to an ECLASS class, classifying a process step), (3) numerical regressors trained on proprietary outcome data (cost, cycle time, ROI realization), and (4) latency/cost at very high volume. Of these, only (1)–(3) matter here, because planning volumes are low (hundreds to thousands of projects, not billions of calls).
- Model choice is not a one-time decision. Harvey went from a custom OpenAI model to a multi-provider platform. That argues for a model-agnostic orchestration layer with the team's own eval suite (a "Factory Automation Bench").
- Fine-tuning and RAG are complementary rather than either/or (Balaguer et al.). Fine-tuning is most useful for teaching output format, house style and tool-use behaviour. It is weak at injecting facts, which belong in retrieval and the knowledge graph.

### Gaps
- I found no head-to-head study of a manufacturing/industrial-engineering domain LLM vs a frontier LLM on plant-design tasks. No public "automation planning" benchmark exists; the team would need to build one.
- I could not verify a published BloombergGPT follow-up (e.g., whether Bloomberg moved to frontier models). That claim is folklore and should not be repeated without a source.
- No source found quantifying 2026 frontier models (e.g., GPT-5.x, Claude Opus/Mythos-class, Gemini 3) vs fine-tuned models on engineering-design tasks specifically.

---

## 2. Which sub-tasks need specialized (non-LLM) models or engines

### Takeaway
LLMs should orchestrate and explain. The engineering numbers should come from purpose-built engines: perception models for photos/video/3D, CAD kernels and code-CAD for geometry, optimization solvers for layout, discrete-event simulation for throughput, and robot simulators for reach and cycle time. Text-to-CAD is improving fast but is still unreliable for multi-component assemblies.

### Cited Findings
**Video time-and-motion / action recognition**
- Drishti (founded 2016) streams video at every station and uses "proprietary AI networks" (action recognition) to turn video into cycle-time data. It positions this as replacing manual time-and-motion studies. Outputs include average cycle/job time, line efficiency, bottleneck detection and step verification. Neural nets produce cycle time data "within a few days" — [BusinessWire 2022](https://www.businesswire.com/news/home/20220324005268/en); [Gateway House](https://gatewayhouse.in/drishti-foresight-to-digital-manufacturing)
- Vendors in this category use trained, proprietary vision networks rather than general LLMs. Their value rests on labeled factory video — [BusinessWire 2022](https://www.businesswire.com/news/home/20220324005268/en)

**Text-to-CAD**
- Code-based CAD (Python/CadQuery) lets models reuse their pretrained code-generation skill. It yields "substantial improvements over command sequences in both execution validity and geometric accuracy" — [Text2CAD-Bench, arXiv 2605.18430](https://arxiv.org/pdf/2605.18430)
- Text-to-CadQuery (2025): fine-tuned models reach 69.3% top-1 exact match (up from 58.8%) and cut Chamfer distance by 48.6% — [arXiv 2505.06507](https://arxiv.org/html/2505.06507v1)
- CAD-Coder (2025, RL-trained): mean Chamfer distance 6.54 (×10⁻³) vs Text2CAD 29.29 — [alphaXiv 2505.19713](https://www.alphaxiv.org/abs/2505.19713.md)
- MUSE (2026), a benchmark for manufacturable, functional and assemblable text-to-CAD: generating executable CadQuery remains hard. Overlap-free (multi-component) constraints drop most sharply, which shows "multi-component spatial reasoning is a major bottleneck" — [arXiv 2605.28579](https://arxiv.org/pdf/2605.28579)
- BenchCAD contains 17,900 execution-verified CadQuery programs across 106 industrial part families — [search summary of BenchCAD](https://arxiv.org/pdf/2605.18430) (exact source attribution uncertain)

**Layout / robotic cell optimization**
- Research on robotic cell layout optimization uses simulation-based and multi-agent methods built on digital twins (e.g., Visual Components + TwinCAT), not LLMs — [PMC 12089245](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC12089245/); [Simulation-based robotic cell layout optimisation](https://observatorio-cientifico.ua.es/documentos/6a651af5e349fb07c9bfcc60)
- In adjacent engineering domains, LLMs are being used as planners, code synthesizers and supervisors over control and optimization tooling. Example: an LLM-assisted multi-agent controller design for roll-to-roll manufacturing, with sim-to-real adaptation — [arXiv 2511.22975](https://arxiv.org/pdf/2511.22975)
- "Frontier Large Language Models Rival State-of-the-Art Planners" (2025) is evidence that frontier LLM planning ability is improving. Classical planners/solvers remain the benchmark — [arXiv 2511.09378](https://arxiv.org/html/2511.09378v2)

**Robot / physical simulation ecosystem**
- At GTC 2026, ABB, FANUC, KUKA and Yaskawa all announced integrating NVIDIA Omniverse and Isaac simulation into their virtual-commissioning workflows — [A3 / automate.org](https://www.automate.org/ai/industry-insights/nvidia-declares-big-bang-of-physical-ai-at-gtc-2026); [NVIDIA newsroom](https://nvidianews.nvidia.com/news/nvidia-and-global-robotics-leaders-take-physical-ai-to-the-real-world)

### Inferences
Recommended engine per sub-task (based on the findings above plus general engineering practice; no head-to-head sources were gathered for most rows):
| Sub-task | Recommended engine | LLM role |
|---|---|---|
| Recognize machines/workstations/assets in photos | Fine-tuned detector/segmenter (open-vocabulary VLM + custom fine-tune on a proprietary equipment image set); frontier VLM as fallback/zero-shot | Interpret, reconcile with ERP asset list |
| Time-and-motion from video | Specialized temporal action-segmentation models (Drishti-style), plus frontier video-VLM for zero-shot first pass | Turn segments into a process map and bottleneck narrative |
| 3D floor capture | Photogrammetry / LiDAR (iPhone LiDAR, Matterport) / Gaussian splatting → mesh/point cloud → floor-plan vectorization | None for geometry; QA and annotation |
| Floor plans / DWG / CAD ingest | CAD kernel parsers (DXF/STEP/IFC), raster floor-plan vectorization models | Semantic labeling |
| New part/fixture/gripper geometry | Code-CAD (CadQuery/build123d) generated by LLM, executed and checked in a kernel; parametric template library for standard items | Generates code; geometry is verified |
| Layout | MIP/CP-SAT facility-layout formulations, GA/simulated annealing, possibly RL; constraint checkers (aisles, safety zones, ISO 10218/13855 distances) | Sets up the problem, reads results |
| Throughput | DES (SimPy for programmatic/internal use; Siemens Plant Simulation / FlexSim / AnyLogic when customers require them) | Generates model config from structured spec |
| Robot reach/cycle time | RoboDK / vendor OLP (RobotStudio, ROBOGUIDE) for vendor-accurate cycle times; Isaac Sim / MuJoCo for physics, grasping and synthetic data | Picks candidates, interprets results |
| ROI/BOM | Deterministic calculators over catalog prices; later learned cost estimators | Narrative, assumptions, sensitivity |
- A frontier LLM should never compute cycle times, reach or ROI "in its head". Every number in an engineering-grade deliverable should trace back to a tool run.
- Text-to-CAD is good enough for simple parts (fixtures, brackets, guards) when outputs are executed and checked. It is not yet good enough for multi-body assemblies (MUSE finding). Catalog CAD (vendor STEP files) plus parametric templates should cover most cell geometry.

### Gaps
- No primary sources gathered on Retrocausal's specific approach, Zoo.dev's model, or Autodesk Project Bernini's current status as of Oct 2026.
- No published accuracy figures found for photo-based machine recognition in factories, or for phone-scan floor accuracy (NeRF/GS vs LiDAR) vs survey-grade measurement.
- No published benchmark of surrogate ML throughput models vs full DES accuracy was gathered. The general practice (surrogates for fast design-space screening, DES for final validation) is an inference.
- Cycle-time accuracy of RoboDK vs vendor OLP vs Isaac Sim against real robots is not sourced here.

---

## 3. Agentic architectures for engineering design: reliability and verification

### Takeaway
The best-documented pattern in industrial code/design generation is an LLM inside a closed loop with formal and executable verifiers (compilers, model checkers, simulators) plus human review. Verification loops produced the largest quality gains, larger than the gain from fine-tuning. Industrial incumbents (Siemens) are shipping exactly this orchestrator-plus-specialist-agent pattern.

### Cited Findings
- LLM4PLC (UC Irvine, ICSE-SEIP 2024): a user-guided iterative pipeline with grammar checkers, compilers and SMV model checkers in the loop. It raised generation success from 47% to 72% and expert-rated code quality from 2.25/10 to 7.75/10. It was tested on GPT-3.5, GPT-4, Code Llama 7B/34B and fine-tuned Code Llama variants, and validated on a FischerTechnik manufacturing testbed — [arXiv 2401.05443](https://arxiv.org/abs/2401.05443v1); [ICSE 2024](https://conf.researchr.org/details/icse-2024/icse-2024-software-engineering-in-practice/32/LLM4PLC-Harnessing-Large-Language-Models-for-Verifiable-Programming-of-PLCs-in-Indus)
- Agents4PLC extends this to closed-loop multi-agent PLC code generation and verification — [Moonlight review](https://themoonlight.io/fr/review/agents4plc-automating-closed-loop-plc-code-generation-and-verification-in-industrial-control-systems-using-llm-based-agents)
- Siemens Industrial Copilot / Engineering Copilot TIA: generates and modifies TIA Portal project elements (SCL code) from natural language. Delivered as a managed service, with a beta integrated with TIA Portal V19/V20 — [Automation World, SPS 2025](https://automationworld.com/factory/digital-transformation/news/55332816/siemens-ag-siemens-unveils-generative-ai-copilot-for-autonomous-engineering-at-sps-2025); [IoT M2M Council](https://iotm2mcouncil.org/iot-library/news/connected-industries-news/siemens-ai-agents-for-industrial-automation/)
- Siemens' 2025 AI-agent architecture uses "an orchestrator that incorporates a toolbox of specialised agents", accessing external tools and other agents. Planning Copilot (production planning/scheduling) was in pre-release, with Operations Copilot planned — [Siemens press release](https://news.siemens.com/en-us/ai-agents-manufacturing); [ARC Advisory](https://www.arcweb.com/blog/siemens-introduces-ai-agents-industrial-automation)
- AAS generation by LLM agents (with RAG over the ECLASS dictionary) reached a 62–79% "effective generation rate". That is useful, but it means 20–40% of outputs still need correction — [arXiv 2403.17209](https://arxiv.org/pdf/2403.17209)

### Inferences
- **Reference loop:** (1) Ingest and normalize into a structured "plant model" (the JSON/graph source of truth). (2) The LLM planner proposes concepts (cell types, equipment candidates) via retrieval from the component graph. (3) Solvers and simulators evaluate them: layout optimizer, DES, robot reach/cycle, safety-distance checker, BOM/cost calculator. (4) Constraint/verification agents check outputs against hard rules (payload, reach, takt, footprint, utilities, standards) and send violations back to the planner. (5) A critic model (possibly a different frontier model) reviews assumptions. (6) A human automation engineer signs off. (7) Outcomes are logged for the data flywheel.
- The evidence (LLM4PLC: 47→72% success) suggests verifier quality matters more than which model is used. Investment should go first into simulators, checkers and test suites, and only then into fine-tuning.
- Engineering-grade output requires that each claim in the plan (cycle time, reach, ROI) has a provenance pointer to a tool run or catalog record. The LLM authors the narrative and the integration specs, which are partly templated.
- Siemens' entry is a competitive signal. Its copilots sit inside its own toolchain (TIA, Plant Simulation, Process Simulate). A vendor-neutral planner could differentiate on cross-vendor equipment selection.

### Gaps
- No public "text-to-robot-cell" end-to-end system with measured accuracy vs human engineers was found in this pass.
- Rockwell/Microsoft FactoryTalk Design Studio copilot details and any accuracy metrics were not verified.
- No sourced data on error rates of LLM-generated DES models (LLM writes SimPy/Plant Simulation models).

---

## 4. Knowledge base design: component catalog/ontology, knowledge graph vs vector RAG, standards

### Takeaway
Use a typed, structured component knowledge graph/database (specs as numeric attributes keyed to ECLASS/AAS semantics) as the source of truth for equipment selection, and use vector RAG only for unstructured documents (manuals, application notes, past proposals). Engineering selection is mostly constraint filtering on numbers (payload, reach, repeatability, IP rating, price), which suits structured queries and does not suit embedding similarity.

### Cited Findings
- LLM-agent pipelines can generate Asset Administration Shell (AAS) instances from text datasheets. They use RAG over the ECLASS dictionary, with semantic-search agents using embeddings to find matching ECLASS entries. The effective generation rate is 62–79% — [arXiv 2403.17209](https://arxiv.org/pdf/2403.17209); [GitHub AASbyLLM](https://github.com/YuchenXia/AASbyLLM)
- Event-driven architectures load AAS content into a Neo4j knowledge graph so that relationship-oriented Cypher queries are possible. A proof-of-concept LLM agent queries this graph through MCP — [search result summary; Fraunhofer publica](https://publica.fraunhofer.de/handle/publica/490383) (exact attribution of the Neo4j/MCP work to this handle is uncertain)
- A 2025 journal article proposes using AAS to build standardized information models for assets and knowledge to improve RAG, and fine-tuning open LLMs with a contrastive selection loss to refine retrieval — [DFKI publication](https://www.dfki.de/web/forschung/projekte-publikationen/publikation/16126) (as summarized by search; not opened)

### Inferences
- Recommended schema: Component (robot, gripper, conveyor, AMR, vision sensor, PLC, safety device, machine tool) → typed properties using ECLASS IRDIs/AAS submodels (Technical Data, Nameplate). Relations: compatible-with (robot↔tool flange↔gripper, PLC↔fieldbus), requires (utilities, safety), substitutes, vendor, price/lead-time history. Geometry assets (STEP, URDF) are linked for simulation.
- AutomationML (IEC 62714) works well as the interchange format for exporting cell/layout designs to customers' engineering tools. AAS works well as the per-component digital datasheet format. Both are inferences from their standard roles; neither was benchmarked here.
- Populate the catalog with LLM extraction from datasheets, checked by schema validators and human QA (given the 62–79% automatic rate). This is an LLM job, not a reason to train a model.
- Use hybrid retrieval: graph/SQL filters for hard constraints, then vector search over application notes and past projects ("similar cells we've built"), then LLM reranking/justification.
- Pricing is the hardest data to obtain (distributor quotes, negotiated prices). It is a proprietary data asset.

### Gaps
- No quantitative study found comparing KG-RAG vs vector-RAG accuracy on industrial component selection.
- ECLASS coverage depth for robots/grippers/AMRs and AAS submodel adoption by major robot OEMs as of 2026 were not verified.

---

## 5. Data flywheel, moat, and when to fine-tune/train proprietary models (post-training options in 2026)

### Takeaway
The moat is the proprietary data loop, not model weights: labeled factory video and photos, completed projects with predicted vs actual cycle time, cost and ROI, engineer edits to AI drafts, and real quotes and prices. Use that data first as retrieval and eval sets. Train narrow models (perception, cost/cycle-time regressors, rankers) when there are hundreds to thousands of labeled outcomes. Use RL/preference fine-tuning of an LLM only when a reliable automated grader exists and frontier prompting has plateaued.

### Cited Findings
- OpenAI's Reinforcement Fine-Tuning (grader-based RL on o-series reasoning models) moved beyond alpha and became generally available around May 2025. Sources conflict on which models are currently supported (o4-mini was the initial flagship) — [OpenAI RFT use-cases docs](https://platform.openai.com/docs/guides/rft-use-cases); [TheNeuralBase](https://theneuralbase.com/openai-fine-tuning/learn/advanced/o1-and-o3-fine-tuning-availability/) (secondary, inconsistent)
- Claude fine-tuning was offered only through Amazon Bedrock, for Claude 3 Haiku (GA Nov 2024, US West Oregon). No evidence was found of fine-tuning for frontier Claude models — [AWS What's New](https://aws.amazon.com/about-aws/whats-new/2024/11/fine-tuning-anthropics-claude-3-haiku-amazon-bedrock); [AWS blog](https://aws.amazon.com/blogs/aws/fine-tuning-for-anthropics-claude-3-haiku-model-in-amazon-bedrock-is-now-generally-available/)
- Harvey's experience: API fine-tuning plus RAG hit limits for open-ended legal work, which led to a deep custom-model partnership with OpenAI (access most companies do not have). Harvey later still went multi-model — [OpenAI](https://openai.com/index/harvey); [Harvey](https://www.harvey.ai/blog/expanding-harveys-model-offerings)
- Fine-tuning gains add on top of RAG (+6 pp FT, +5 pp RAG in the agriculture study) — [arXiv 2401.08406](https://arxiv.org/html/2401.08406v2)
- Domain fine-tuning can degrade instruction-following (SeedBench) — [arXiv 2505.13220](https://arxiv.org/pdf/2505.13220)

### Inferences
- **Flywheel assets, ranked by moat value:**
  1. Predicted vs actual outcomes per deployed cell (cycle time, OEE, uptime, cost overrun, ROI realization). Nobody else has these, and they are needed to calibrate estimators.
  2. Engineer edits and accept/reject decisions on AI drafts. These are preference data for ranking and for RL.
  3. Labeled factory video/photos (operations, machine types).
  4. Real quotes, prices and lead times.
  5. Library of validated cell designs (CAD + sim models) as reusable templates.
- **Thresholds (heuristic, not sourced):** Gradient-boosted cost/cycle-time estimators can beat LLM guesses with roughly 100–500 well-labeled projects per cell family. Fine-tuned detectors need roughly 1k–10k labeled images per class family. Preference/RL fine-tuning of an LLM planner needs an automatic grader (simulation pass/fail, constraint satisfaction, engineer score) and thousands of graded episodes.
- **Post-training options in Oct 2026:** (a) closed-model RFT/SFT where offered (OpenAI RFT; Bedrock for limited Claude models; Vertex for Gemini), (b) open-weight models (Llama, Qwen, DeepSeek families) fine-tuned with SFT/DPO/GRPO in the team's own VPC when full control or on-prem is needed, (c) distilling frontier outputs into small open models for high-volume subtasks (e.g., datasheet extraction to AAS, ECLASS classification), where fixed-schema evidence favors fine-tuned models.
- Do not post-train the core planner early. Frontier releases (roughly every 3–6 months) will likely wipe out the gains, as happened with BloombergGPT. Keep the eval set proprietary and re-run it on each new frontier model.

### Gaps
- Current (Oct 2026) list of OpenAI models supporting SFT/RFT, Gemini tuning availability on Vertex, and whether any frontier Claude model supports customer fine-tuning were not verified from primary docs.
- No a16z/Sequoia moat essays were retrieved in this pass. Moat claims above are my inference.
- No sourced data on how many projects vertical-AI firms needed before proprietary models beat frontier prompting.

---

## 6. Data security / IP: manufacturer data to LLM APIs; VPC/on-prem; zero data retention

### Takeaway
Manufacturers' CAD, process video and ERP data are sensitive IP. All major providers offer enterprise no-training terms and cloud-hosted deployment (Bedrock, Vertex, Azure) with some form of zero data retention (ZDR). But as of mid-2026, ZDR is not on by default, mechanisms differ, and Anthropic's most capable "covered" models carry mandatory 30-day retention. The architecture should therefore route data by sensitivity, and the ability to run open-weight models in-VPC or on-prem is a real requirement for some customers.

### Cited Findings
- Anthropic's "Covered Models" policy, in effect June 9, 2026: prompts and outputs for covered (Mythos-class) models are retained for 30 days "to support safety work, on every platform where these models are offered". Existing ZDR does not apply. Access is logged in a tamper-proof log. Currently covered models are reported as Claude Mythos 5 and Claude Fable 5 — [Anthropic support: Covered Models](https://support.claude.com/en/articles/15425695-covered-models); [Anthropic: Data retention practices for covered models](https://support.claude.com/en/articles/15425996-data-retention-practices-for-covered-models)
- As of Aug 2026, OpenAI, Anthropic, Google and Microsoft all offer some form of ZDR. None is enabled by default, and each uses a different mechanism — [wecallshotgun comparison](https://wecallshotgun.com/blog/zero-data-retention-ai-models-comparison) (secondary, cites primary docs)
- OpenAI (Aug 19, 2026) announced ZDR for frontier models with a "Private Safety Processing" preview. ZDR is applied per endpoint and excludes Assistants, Files, fine-tuning and Batches — [OpenAI announcement as cited](https://openai.com/index/offering-zero-data-retention-for-frontier-models/) (via secondary summary; not opened directly)
- Google Vertex AI ZDR requires disabling context caching (24-hour retention by default) and requesting an abuse-monitoring exception — [Google Cloud docs as cited](https://cloud.google.com/vertex-ai/generative-ai/docs/vertex-ai-zero-data-retention) (via secondary summary)
- Azure OpenAI ZDR is obtained through "modified abuse monitoring" (Limited Access, EA/MCA-E, per subscription) — [Microsoft Learn as cited](https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/abuse-monitoring) (via secondary summary)
- Harvey runs Anthropic and Google models through AWS Bedrock and Google Vertex "with the same security and privacy guarantees" — an example of the cloud-hosted pattern used by regulated-industry vertical AI — [Harvey](https://www.harvey.ai/blog/expanding-harveys-model-offerings)

### Inferences
- Design a sensitivity router. (1) Highly sensitive raw assets (customer CAD, video of proprietary processes) are processed by in-VPC perception models and open-weight LLMs, or by frontier models under ZDR. (2) Derived, abstracted structured specs (cycle times, part envelopes, throughput targets) go to the strongest frontier model. (3) Covered/30-day-retention models are used only where the customer contract allows it.
- Keep the stack multi-provider (Bedrock + Vertex + Azure + self-hosted open weights) so that strict customers (defense, pharma, automotive suppliers) can be served without redesign.
- Video and CAD often require customer-site or customer-cloud deployment. Packaging the perception and simulation stack as deployable containers is worth it.

### Gaps
- Primary text of the OpenAI Aug 2026 ZDR announcement was not opened directly.
- Exact ZDR eligibility of non-covered Claude models (e.g., Sonnet/Haiku/Opus tiers) on Bedrock vs the first-party API as of Oct 2026 was not confirmed.
- No survey data gathered on manufacturers' actual willingness to send CAD/video to cloud LLMs.

---

## 7. Physical AI foundation models (execution layer) — build or not?

### Takeaway
Physical-AI foundation models (NVIDIA Cosmos/GR00T, Physical Intelligence π0/π0.5, Gemini Robotics) are advancing quickly and are being adopted by the big robot OEMs as simulation/commissioning infrastructure. They are capital-intensive platform plays dominated by NVIDIA, Google DeepMind and heavily funded startups. A planning company should consume them (as simulation, synthetic data, and optional "flexible cell" options in its catalog), not build them.

### Cited Findings
- Physical Intelligence released π0.5, a vision-language-action model with open-world generalization, in April 2025 — [awesome-physical-ai list](https://github.com/keon/awesome-physical-ai)
- NVIDIA GR00T N1.7 (April 2026): a 3B-parameter open VLA on a Cosmos-Reason2-2B backbone, pretrained on more than 20,000 hours of human egocentric video. Early access with commercial licensing — [NVIDIA newsroom](https://nvidianews.nvidia.com/news/nvidia-and-global-robotics-leaders-take-physical-ai-to-the-real-world); [buildfastwithai review](https://www.buildfastwithai.com/blogs/nvidia-cosmos-3-isaac-groot-physical-ai-2026) (secondary)
- NVIDIA Cosmos 3 (May 31, 2026) is described as an open Physical-AI "omnimodel" (16B Nano, 64B Super on Hugging Face) — [buildfastwithai](https://www.buildfastwithai.com/blogs/nvidia-cosmos-3-isaac-groot-physical-ai-2026) (secondary; not verified against NVIDIA primary)
- Gemini Robotics-ER 1.6 reportedly achieved 93% success on industrial instrument reading using agentic vision — [search summary](https://www.automate.org/ai/industry-insights/nvidia-declares-big-bang-of-physical-ai-at-gtc-2026) (attribution uncertain; verify)
- ABB, FANUC, KUKA and Yaskawa announced Omniverse/Isaac integration for virtual commissioning at GTC 2026 — [A3](https://www.automate.org/ai/industry-insights/nvidia-declares-big-bang-of-physical-ai-at-gtc-2026)

### Inferences
- **Don't build:** training VLAs or world models needs huge robot/egocentric datasets and compute, and NVIDIA open-sources competitive models. A planning company has no data advantage there.
- **Do integrate:** (1) Omniverse/Isaac Sim (OpenUSD) as the 3D/physics digital-twin substrate for cell validation and customer visualization, aligned with the big-4 OEM commissioning workflows. (2) Cosmos-type world models for synthetic training data for the perception models (rare machine types, occlusions). (3) Catalog entries for VLA-enabled flexible cells (e.g., high-mix kitting, machine tending) with honest maturity ratings. Most dark-factory automation in 2026 still uses deterministic, programmed robots for high-volume tasks. This is an inference; no deployment-share data was found.
- An option for later: if the company deploys many cells, its fleet data (cycle logs, failures) could become valuable for fine-tuning VLAs on specific tasks. That is a phase-3 consideration.

### Gaps
- Several 2026 physical-AI specifics (Cosmos 3 sizes, GR00T N1.7 details, Gemini Robotics-ER 1.6 metric) come from secondary sources and should be checked against NVIDIA/DeepMind primary pages.
- No reliable data on production deployment rates of VLA-driven robots in factories vs pilots.
- Skild AI status and π0.5/π0.6 industrial deployments were not researched.

---

### Recommended reference architecture (summary for the report writer; synthesis of the sections above)
1. **Ingestion & perception layer (specialist models, in-VPC capable):** document/ERP parsers; photo asset detection (fine-tuned detector + frontier VLM fallback); video action segmentation for time-and-motion; 3D capture → point cloud/mesh → floor-plan vectorization; CAD/DXF/STEP/IFC parsers. Output: a structured **Plant Model** (graph/JSON; AAS/AutomationML aligned).
2. **Knowledge layer:** component knowledge graph (ECLASS/AAS-typed specs, compatibility edges, prices/lead times, STEP/URDF assets) + vector index over manuals and past projects + library of validated cell templates.
3. **Reasoning/orchestration layer:** frontier LLM(s), multi-provider, with tool calling (MCP), a planner/critic split, and a long-context project dossier. Prompt plus retrieval, no domain pretraining.
4. **Engineering tool layer (sources of all numbers):** layout optimizer (MIP/CP-SAT/GA), DES (SimPy plus commercial export), robot sim/OLP (RoboDK/vendor OLP; Isaac Sim for physics), code-CAD (CadQuery/build123d), safety/standards checker, BOM/cost/ROI calculator, PLC/integration spec templating (LLM4PLC-style verified generation if code is produced).
5. **Verification layer:** constraint checks, simulation-in-the-loop iteration, cross-model critique, provenance for every number, human automation-engineer sign-off.
6. **Learning layer (flywheel):** log designs, edits and real-world outcomes → proprietary eval benchmark → train narrow models (perception, estimators, rankers) → selectively RFT/distill when graders exist.
