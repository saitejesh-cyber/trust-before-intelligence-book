<artifact identifier="colaberry-codex-lean" type="application/vnd.ant.code" language="markdown" title="The Colaberry Codex (TCC) - Lean Edition">
# The Colaberry Codex (TCC) - Lean Edition

**Writing Standards for "Enterprise Data Readiness for AI Agents"**

Version 1.2.0 | November 11, 2025 | Ram Katamaraja, CEO Colaberry Inc.

---

## Core Principles (The Non-Negotiables)

1. **Evidence-based:** Major claims need citations <18 months old
2. **URLs:** Every product gets official URL on first mention
3. **Academic rigor:** Prioritize peer-reviewed research and open academic sources (TCC-033)
4. **Healthcare-only:** All examples use Echo Health Systems
5. **No internal jargon:** Never use "VERT", "TCC", "Four-T" in reader content
6. **Standard terms:** Use exact terminology from glossary
7. **Healthcare context:** Patient (not customer), encounter (not transaction)
8. **Echo consistency:** Use exact figures from canonical reference
9. **Chapter flow:** Every chapter connects to previous and bridges to next
10. **Cite visuals:** Reference all tables/diagrams with exact titles
11. **Current tech:** Indicate maturity status (production-ready/maturing/experimental)

---

## Section 1: Evidence & Attribution

### TCC-001: Evidence Required
Every statistic, benchmark, or best practice needs a citation.

**Needs citation:**
- "95% of GenAI projects fail" → cite MIT NANDA study
- "ABAC evaluation <10ms" → cite NIST documentation
- "Semantic layer improves accuracy 60% → 85%" → cite vendor case study

**No citation needed:**
- Colaberry's own frameworks (7-layer architecture, INPACT™)
- Narrative storytelling
- Explanations of already-cited concepts

**Citation age limits:**
- Statistics/research: <18 months (prefer <12)
- Technology: <12 months
- Regulations: Current version only

### TCC-002: Attribution Format
```markdown
"[Finding from source], [context]. [#]"

Example:
"MIT NANDA examined 300+ GenAI initiatives. Finding: 95% fail to achieve ROI. [1]"

References:
[1] Challapally, A., et al. (2025, July). "The GenAI Divide." MIT NANDA. [URL]
```

### TCC-003: Colaberry IP
Attribute our frameworks clearly:
```markdown
"Colaberry's 7-layer agent-ready data architecture addresses six capabilities..."
"Ram Katamaraja synthesized these patterns from 30 years of implementations..."
```

---

## Section 2: Terminology (Use Exactly)

### TCC-010: Standard Terms

**Architecture:**
- "7-layer agent-ready data architecture" (never "7-layer framework")
- "INPACT™" OR "Six Agent Capabilities" (never "six requirements")
- "Multi-agent orchestration" (never "agent coordination")

**Layers (use exact names):**
- L1: Real-Time Data Fabric
- L2: Unified Semantic Layer
- L3: Multi-Modal Storage
- L4: Intelligent Retrieval (RAG)
- L5: Agent-Aware Governance
- L6: Observability & Feedback
- L7: Self-Service Data Products & Multi-Agent Orchestration

### TCC-011: Forbidden Terms (Reader-Facing Content)
Never use in published chapters:
- ❌ "VERT Council" / "VERT Ethics Audit" / "VERT score"
- ❌ "Four-T framework" (Truth, Trust, Traction, Thread)
- ❌ "TCC-compliant" / "The Colaberry Codex"
- ❌ Any reviewer persona names

Use instead: "independent ethics review" or omit entirely

### TCC-012: Healthcare Terminology

| Use This | Never This |
|----------|------------|
| Patient | Customer, client |
| Encounter, visit, appointment | Transaction, order |
| Service, procedure | Product |
| Admissions, encounters | Revenue, sales |
| Provider, physician, clinician | Employee, staff |
| EHR (Electronic Health Record) | Patient database |
| PHI (Protected Health Information) | Sensitive data |

---

## Section 3: Examples & Case Studies

### TCC-020: Healthcare Context Only
ALL examples must use Echo Health Systems. No retail, banking, or mixed industry examples.

❌ **WRONG:**
```
"When a customer adds items to cart (like a patient booking appointment)..."
```

✅ **CORRECT:**
```
"When a care coordinator asks 'Show me patients needing diabetes follow-up', 
the semantic layer translates to diagnosis codes E11.*, HbA1c > 7.0..."
```

### TCC-021: Echo Canonical Reference
Use EXACT figures. Never round or approximate.

**Investment:** $1.23M (not ~$1.2M, not "about $1.2M")
**Duration:** 90 days (not "3 months", not "~90 days")
**Agents deployed:** 6 (not "several", not "multiple")
**ROI:** 477% (not "over 400%", not "~480%")
**Payback:** 10 weeks (not "about 3 months")
**Return:** $7.1M ($6.3M savings + $800K revenue)
**Start readiness:** 28/100 (BI-First archetype)
**End readiness:** 85/100
**SLOs:** Data freshness 25 seconds, NDCG 0.94, API availability 99.92%

Before writing Echo example: Check these figures. Copy exactly. Never vary.

---

## Section 4: URLs & Citations

### TCC-030: URLs Required
Every product/technology needs official URL on first mention per chapter.

```markdown
✅ CORRECT:
[Pinecone](https://www.pinecone.io) is a managed vector database optimized 
for semantic search.

[Apache Kafka](https://kafka.apache.org) is an open-source distributed 
event streaming platform.
```

Even if URL in Chapter 1, provide again in Chapter 5 (readers may skip chapters).

### TCC-031: Multiple Options
Provide 2-3 examples per category, not just one vendor.

```markdown
✅ CORRECT:
"Vector databases include [Pinecone](url) (managed), [Weaviate](url) 
(open-source), and [Qdrant](url) (high-performance)."

❌ WRONG:
"Use Pinecone for vector database."
```

### TCC-032: URL Testing
Before publication:
- Click every URL (100%)
- No 404s allowed
- Fix broken: Use web.archive.org or find replacement

### TCC-033: Citation Source Hierarchy (CRITICAL)

**Prioritize academic and research sources for maximum credibility and accessibility.**

### SOURCE PRIORITY RANKING

**TIER 1: Peer-Reviewed Academic Research (HIGHEST PRIORITY)**
Use these whenever available:
- University research: MIT, Stanford, CMU, Berkeley studies
- Academic journals with open access: arXiv, PLOS, open IEEE/ACM
- Government research: NIST technical reports, NIH studies, NSF-funded research
- Research consortiums: AI Index (Stanford), Partnership on AI
- Industry-academic partnerships: MIT-IBM Watson AI Lab, Stanford HAI

**Examples:**
- ✅ Stanford AI Index Report (peer-reviewed, annually updated)
- ✅ MIT NANDA research (university-backed, methodology disclosed)
- ✅ NIST technical publications (government standard-setting body)
- ✅ arXiv preprints from academic institutions (pre-peer review but credible)

---

**TIER 2: Government & Standards Bodies**
Authoritative and always freely accessible:
- Government agencies: NIST, HHS, FDA, SEC, FTC
- International standards: ISO, W3C, IETF, IEEE (open access)
- Regulatory bodies: OCR (HIPAA), FDA (medical devices)
- National labs: Lawrence Berkeley, Oak Ridge

**Examples:**
- ✅ NIST Cybersecurity Framework
- ✅ W3C Web Standards
- ✅ HHS HIPAA Guidance

---

**TIER 3: Industry Research & Technical Foundations**
Non-profit, open-access industry research:
- Linux Foundation research
- CNCF (Cloud Native Computing Foundation) reports
- Apache Software Foundation documentation
- Open-source project research (Kubernetes, Kafka studies)
- Non-profit associations: DAMA International, DataKitchen

**Examples:**
- ✅ DAMA DMBOK (Data Management Body of Knowledge)
- ✅ CNCF Annual Surveys
- ✅ Apache Project documentation

---

**TIER 4: Vendor Research & Whitepapers**
Use when vendor is subject matter expert:
- Cloud provider research: AWS, Azure, GCP whitepapers
- Technology vendor research: Databricks, Snowflake, MongoDB studies
- Major tech company research: Google Research, Microsoft Research, Meta AI
- Always freely accessible vendor documentation

**Examples:**
- ✅ Google "Attention Is All You Need" paper (transformer architecture)
- ✅ AWS Well-Architected Framework
- ✅ Databricks DBRX technical documentation

**Note:** Vendor research acceptable when:
- Published as open research (not gated marketing)
- Contains methodology and data
- Citable by DOI or permanent URL
- Not purely promotional

---

**TIER 5: Industry Analyst Reports (USE SPARINGLY)**
Only when freely accessible:
- McKinsey & Company (some reports are open access)
- Deloitte Insights (free registration sometimes required)
- Accenture Research (mixed accessibility)

**⚠️ CAUTION:** Verify accessibility before citing
- ✅ If freely downloadable without account: OK
- ⚠️ If requires free registration: Note "(free registration required)"
- ❌ If behind paywall: Skip to Tier 1-4 alternatives

**Examples:**
- ✅ McKinsey "State of AI" (annual report, freely accessible)
- ❌ Gartner Magic Quadrant (subscription only - DO NOT USE)
- ❌ Forrester Wave (subscription only - DO NOT USE)

---

**AVOID ENTIRELY:**
- ❌ Gartner (subscription required)
- ❌ Forrester (subscription required)
- ❌ IDC (subscription required)
- ❌ Academic journals requiring institutional access (use open access alternatives)
- ❌ "Contact sales for whitepaper" gated content
- ❌ LinkedIn posts or social media (not authoritative)
- ❌ Medium articles (not peer-reviewed)
- ❌ Blog posts (unless from recognized research institution)

---

### REPLACEMENT STRATEGY

**When tempted to cite Tier 5 or lower:**

1. **Find the academic source:**
   - Industry analyst citing a study? → Find original academic paper
   - Example: Gartner "80% will adopt X" → Stanford AI Index has similar data

2. **Use government/standards body:**
   - Forrester "API management trends" → W3C API standards + NIST guidelines
   - Gartner "data quality" → DAMA DMBOK (free, more comprehensive)

3. **Cite multiple vendor sources:**
   - Instead of one analyst report → 2-3 vendor whitepapers + academic study
   - Example: "Multiple sources report..." [AWS whitepaper, Google Research, Stanford study]

4. **Use recent books from academic presses:**
   - MIT Press, O'Reilly (some open access)
   - University press publications

---

### CITATION ACCESSIBILITY VERIFICATION

**Before including ANY citation, verify:**
- [ ] Opens in incognito browser window (no cookies, not logged in)
- [ ] No "subscribe to continue" or "sign in to read" message
- [ ] No "X free articles remaining this month" counter
- [ ] No "institutional access required" message
- [ ] Full content visible without registration
- [ ] PDF downloads without login (if applicable)
- [ ] **BONUS:** Source is peer-reviewed or from recognized research institution

**If citation fails these checks:**
- Use Tier 1-3 alternatives
- Never compromise on accessibility
- Academic rigor > industry brand recognition

---

### CITATION QUALITY HIERARCHY

**For any given claim, prefer in this order:**

1. **Peer-reviewed journal article** (Tier 1)
2. **University research report** (Tier 1)
3. **Government technical standard** (Tier 2)
4. **Open-source foundation research** (Tier 3)
5. **Major tech company research** (Tier 4)
6. **Vendor whitepaper with methodology** (Tier 4)
7. **Open-access industry analyst report** (Tier 5, with caution)

**Never:**
8. ❌ Paywalled analyst report
9. ❌ Social media or blog posts
10. ❌ Uncited claims

---

### WHY THIS MATTERS

**Academic Rigor:**
- Peer review process ensures quality
- Methodology is transparent
- Data is reproducible
- Citations build on verified research

**Reader Trust:**
- Can verify every claim
- No "trust us, we paid for this report" barrier
- Encourages critical thinking
- Supports independent research

**Long-term Validity:**
- Academic sources remain accessible
- No link rot from expired subscriptions
- Permanent DOIs for papers
- Institutional preservation

**Competitive Advantage:**
- Most business books cite Gartner/Forrester heavily
- Using Tier 1-2 sources positions book as research-backed
- Appeals to technical audience who values rigor
- Differentiates from marketing-heavy competitors

---

### EXAMPLES: GOOD VS BAD

**❌ BAD (Industry Analyst Paywall):**
```markdown
Gartner predicts 80% of enterprises will adopt semantic layers by 2026. [1]

[1] Smith, J. (2024). "The Future of Data Architecture." Gartner Research. 
https://www.gartner.com/document/12345 (requires subscription)
```

**✅ GOOD (Academic Research):**
```markdown
Stanford's AI Index Report shows 75% of enterprises are evaluating semantic 
layer adoption as foundational infrastructure for AI readiness. [1]

[1] Stanford HAI (2024). "Artificial Intelligence Index Report 2024." 
Stanford University. https://aiindex.stanford.edu/report/ 
(peer-reviewed, open access)
```

---

**❌ BAD (Vendor Blog):**
```markdown
Databricks blog says lakehouse architecture is the future. [2]
```

**✅ GOOD (Academic + Vendor Research):**
```markdown
The lakehouse architecture pattern, first formalized by UC Berkeley researchers 
and implemented at scale by Databricks, combines data warehouse and data lake 
capabilities in a unified platform. [2][3]

[2] Armbrust, M., et al. (2021). "Lakehouse: A New Generation of Open Platforms 
that Unify Data Warehousing and Advanced Analytics." CIDR Conference.
[3] Databricks (2023). "Lakehouse Technical Architecture." 
https://www.databricks.com/research/lakehouse
```

---

**❌ BAD (No Source):**
```markdown
Most healthcare organizations struggle with data readiness for AI.
```

**✅ GOOD (Government Research):**
```markdown
HHS research finds 73% of healthcare organizations cite data infrastructure 
gaps as the primary barrier to AI adoption. [4]

[4] Office of the National Coordinator for Health IT (2024). 
"Healthcare AI Readiness Assessment." HHS.gov.
```

---

### PENALTY FOR VIOLATION

**If low-quality or inaccessible citations found:**
- VERT score automatically drops to <7/10 (Yellow/Red)
- Must be replaced with Tier 1-3 sources before publication
- Chapter cannot be certified until fixed

**VERT Certification Requirements:**
- 80%+ citations from Tier 1-2 (academic/government) = GREEN (9-10/10)
- 60-79% citations from Tier 1-2 = YELLOW (7-8/10)
- <60% citations from Tier 1-2 = RED (<7/10) - requires revision

---

## Section 5: Technology Guidance

### TCC-040: Selection Criteria
Never just recommend one tool. Show options, criteria, trade-offs.

**Pattern:**
```markdown
Vector Database Selection:

Options:
- [Pinecone](url): Managed, auto-scaling, higher cost
- [Weaviate](url): Self-hosted, flexible, ops overhead
- [Qdrant](url): High-performance, Rust-based, newer

Choose based on:
- Prioritize hands-off → Pinecone
- Prioritize flexibility → Weaviate
- Prioritize performance → Qdrant

Trade-offs:
- Managed: Easy but less control, higher cost
- Self-hosted: Control but ops complexity
- Performance: Fast but less mature ecosystem
```

### TCC-041: Version Neutrality
Avoid specific version numbers unless critical.

✅ "Use current stable release of Apache Kafka"
✅ "As of October 2025, Pinecone offers managed services..."
❌ "Install Apache Kafka v3.4.2"

### TCC-042: Technology Maturity Status
Indicate status clearly:

- **Production-ready:** LangGraph, CrewAI, AutoGen
- **Rapidly maturing:** MCP (mainstream adoption but requires security expertise)
- **Experimental:** Alpha releases, limited production use
- **Deprecated:** Avoid for new projects

For MCP (Oct 2025): Note mainstream adoption + security considerations required.

---

## Section 6: Visual Elements

### TCC-050: Diagrams Required
Complex concepts need diagrams:
- Multi-component architectures
- Process flows
- Comparisons (BI vs Agent)
- Relationships (entity resolution)

### TCC-051: Generic vs Specific
Use generic terms in diagrams UNLESS comparing specific vendors.

Generic: "Vector Database" → "Query Results" → "LLM"
Specific: Only when showing "Pinecone vs Weaviate vs Qdrant"

### TCC-052: Reference All Visuals
All diagrams and tables must be:
1. Numbered and titled
2. Referenced in text with exact title

```markdown
**Diagram 1: Seven-Layer Architecture**

[diagram content]

In text: "The seven-layer stack (Diagram 1: Seven-Layer Architecture) shows..."
```

---

## Section 7: Chapter Integration

### TCC-060: Opening Connection
Every chapter connects to previous:

```markdown
✅ CORRECT:
"Chapter 0 established that agents require six capabilities: sub-second response, 
natural language understanding, cross-domain context, dynamic authorization, 
continuous learning, trustability.

The question becomes: What architecture delivers all six?

This chapter presents the answer..."
```

### TCC-061: Bridge to Next
Every chapter ends with explicit bridge:

```markdown
Template:
In [current chapter], we [established] [key points].

[Next chapter] builds on this by [what's next].

[Transition question creating momentum]

Let's [action verb] [topic]...
```

### TCC-062: No Contradictions
- Same terminology across all chapters
- Same Echo figures across all chapters
- Same framework names (established in Ch 0/1)
- No conflicting statistics

---

## Section 8: Voice & Audience

### TCC-070: Professional but Accessible
Target: CDOs, CTOs, VPs Data, Data Architects

✅ **Good:**
```
"Your data systems were built for patience. Overnight batch jobs. Queries 
taking 9-13 seconds. That worked when humans analyzed reports over coffee. 
It fails when agents must respond at conversation speed."
```

❌ **Too academic:**
```
"Contemporary enterprise data architectures exhibit temporal latency 
characteristics incompatible with real-time agentic requirements..."
```

❌ **Too casual:**
```
"So your data warehouse is like, totally not ready for AI, right? LOL 🚀"
```

### TCC-071: Acronyms
Define on first use per chapter. Add acronym list at chapter end.

```markdown
First use: "Attribute-Based Access Control (ABAC) evaluates..."
Later: "The ABAC policy engine..."

Chapter end:
## Acronyms
- ABAC: Attribute-Based Access Control
- CDC: Change Data Capture
- RAG: Retrieval-Augmented Generation
```

---

## Pre-Publication Checklist

Run this before EVERY chapter submission:

**Critical (Must Pass):**
- [ ] All major claims have citations <18 months old
- [ ] Every product has URL on first mention
- [ ] All examples use healthcare (Echo)
- [ ] No VERT/TCC/internal jargon in reader content
- [ ] Terminology matches TCC glossary exactly
- [ ] Echo figures match canonical reference (see TCC-021)
- [ ] Chapter connects to previous and bridges to next
- [ ] All tables/diagrams numbered, titled, referenced in text
- [ ] **80%+ citations from Tier 1-2 sources (TCC-033)**

**High Priority:**
- [ ] URLs tested (no 404s)
- [ ] **All citations accessible in incognito browser (TCC-033)**
- [ ] **Majority of citations are peer-reviewed or government sources (TCC-033)**
- [ ] Product categories have 2-3 examples
- [ ] Technology includes selection criteria + trade-offs
- [ ] Acronyms defined first use
- [ ] No retail/banking/mixed examples

**Medium Priority:**
- [ ] Complex concepts have diagrams
- [ ] Diagrams use generic terms (unless comparing vendors)
- [ ] Spell check + grammar check complete

**Status:** [ ] PASS / [ ] FAIL

---

## Quick Reference: Common Patterns

**Product with URL:**
```markdown
[Product Name](https://official-url.com) - Brief description
```

**Citation (prioritize academic):**
```markdown
"[Finding from peer-reviewed research]. [Context]. [#]"

[#] Author, A., et al. (Year). "Title." Institution/Journal. URL (peer-reviewed)
```

**Technology selection:**
```markdown
Options: [A](url) (use case), [B](url) (use case), [C](url) (use case)
Choose based on: Priority X → A, Priority Y → B
Trade-offs: A pros/cons, B pros/cons
```

**Chapter bridge:**
```markdown
In [current], we [accomplished]. [Next] builds on this by [what's next]. 
[Question]. Let's [action]...
```

---

## LLM Self-QA Protocol

**Before delivering content, verify:**

1. Claims have citations? (TCC-001)
2. Products have URLs? (TCC-030)
3. **80%+ citations from Tier 1-2 (academic/government)? (TCC-033)**
4. **All citations freely accessible? (TCC-033)**
5. Examples healthcare only? (TCC-020)
6. No VERT/TCC terms? (TCC-011)
7. Terminology matches glossary? (TCC-010)
8. Echo figures exact? (TCC-021)
9. Chapter connects to previous? (TCC-060)
10. Bridges to next? (TCC-061)

If ANY fail: Fix before delivery. Note corrections made.

**Compliance Score:** [X]/10

- 10/10: ✅ Excellent, proceed
- 8-9/10: ⚠️ Acceptable, note gaps
- <8/10: ❌ Revise before delivery

---

## Priority Hierarchy (When Rules Conflict)

**Critical (Never Violate):**
- Evidence-based (TCC-001)
- **Academic/research citation priority (TCC-033)**
- URLs for products (TCC-030)
- Citation currency (TCC-001)
- Healthcare-only examples (TCC-020)
- Echo canonical consistency (TCC-021)
- No internal jargon (TCC-011)
- Standard terminology (TCC-010)
- Chapter integration (TCC-060, TCC-061)

**High (Strongly Follow):**
- Citation accessibility (TCC-033)
- Multiple product examples (TCC-031)
- Selection criteria (TCC-040)
- Visual references (TCC-052)
- Audience voice (TCC-070)

**Medium (Important):**
- Diagram completeness (TCC-050)
- Acronym management (TCC-071)
- Version neutrality (TCC-041)

---

## Rule Index (Alphabetical)

- TCC-001: Evidence Required
- TCC-002: Attribution Format
- TCC-003: Colaberry IP
- TCC-010: Standard Terms
- TCC-011: Forbidden Terms
- TCC-012: Healthcare Terminology
- TCC-020: Healthcare Context Only
- TCC-021: Echo Canonical Reference
- TCC-030: URLs Required
- TCC-031: Multiple Options
- TCC-032: URL Testing
- TCC-033: Citation Source Hierarchy (CRITICAL) - Prioritize Academic/Research
- TCC-040: Selection Criteria
- TCC-041: Version Neutrality
- TCC-042: Technology Maturity
- TCC-050: Diagrams Required
- TCC-051: Generic vs Specific
- TCC-052: Reference All Visuals
- TCC-060: Opening Connection
- TCC-061: Bridge to Next
- TCC-062: No Contradictions
- TCC-070: Professional Voice
- TCC-071: Acronyms

---

**END OF TCC LEAN EDITION**

Total: 23 rules
Version: 1.2.0 | November 11, 2025
Length: ~4,500 words (expanded for academic citation hierarchy)
Usability: Enhanced with research prioritization

**Key Improvement:** TCC-033 now emphasizes academic rigor and research quality rather than just avoiding paywalls. This positions the book as research-backed and credible while ensuring accessibility.

---

© 2025 Colaberry Inc.
</artifact>
