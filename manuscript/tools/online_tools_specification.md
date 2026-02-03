# Online Tools Specification
## trustbeforeintelligence.ai/tools

**Purpose:** Interactive digital companions to book content
**Version:** 5.0
**Date:** January 2026
**Status:** Specification (Pre-Development)

---

## Relationship to Book Content

### Print Book Appendix
| Appendix | Title |
|----------|-------|
| **INPACT™ Practitioner Reference** | Scoring rubrics, trust bands, anti-patterns |

### Interactive Tools (This Specification)
| Tool | Source | Type |
|------|--------|------|
| **INPACT™ Assessment** | 36-question assessment | Interactive scoring |
| **Build Your Stack Tool** | Layer gap analysis | Interactive web app |
| **Vendor Selector** | Vendor knowledge base | Conversational AI |
| **90-Day Tracker** | Chapter 10 + Day Zero | Web app with 8 tabs |
| **Compliance Navigator** | Regulatory frameworks | Interactive assessment |

### Downloadable Templates
| Template | Purpose |
|----------|---------|
| **Three-Pillar RFP Template** | Structure vendor evaluation requests |
| **POC Test Plan Template** | Two-week validation checklist |

**Principle:** Tools provide **interactive, living experiences**. Templates provide **customizable starting points**.

---

## Tool Inventory (Priority Order)

| Priority | Tool | Format | Lead Capture |
|----------|------|--------|--------------|
| **1** | INPACT™ Assessment (36-Q) | Web form → PDF | Required |
| **2** | Build Your Stack Tool | Interactive web app | Required |
| **3** | Vendor Selector | Conversational AI | Required |
| **4** | 90-Day Implementation Tracker | Web app (8 tabs: Day Zero + Weeks 1-12) | Required |
| **5** | Compliance Navigator | Interactive assessment (30 categories) | Optional |

**Note:** Day Zero Readiness Checklist is now integrated into the 90-Day Tracker as Tab 0 (gate for Week 1).

---

## Tool 1: INPACT™ Assessment (PRIORITY #1)

### Purpose
Interactive 36-question assessment to calculate organization's INPACT™ readiness score. This is the **primary lead generation tool**.

### Source Content
- **36-Question Assessment file** (in Tools folder)
- **INPACT™ Practitioner Reference** (INPACT™ Practitioner Reference) for scoring rubrics and trust bands

### User Flow
1. Landing page with value proposition ("Discover your agent readiness score in 10 minutes")
2. User enters email, name, company, role to access
3. Context selection (healthcare, financial services, manufacturing, other)
4. 36 questions (6 per dimension)
5. Real-time score calculation
6. PDF report generation with:
   - Overall score (X/100)
   - Dimension breakdown radar chart
   - Trust band classification
   - Gap analysis with recommended chapters
   - Comparison to Echo Health baseline (28→89)
   - Next steps based on score

### Score Calculation (Book-Consistent 6-36 System)
```
Per Dimension = Average of 6 questions (range: 1-6) → Normalize to %
Total INPACT™ Score = Sum of 6 dimension scores (range: 6-36) → Normalize to %
Overall Percentage = (Total / 36) × 100 = 0-100%

PRIMARY DISPLAY: Percentage (e.g., "Your INPACT™ Score: 67%")

Trust Bands (percentage-based):
- 86-100%: High Trust (production-ready for healthcare)
- 67-85%: Good Trust (targeted investment needed)
- 50-66%: Moderate Trust (significant gaps)
- 33-49%: Low Trust (major transformation required)
- <33%: Very Low Trust (complete rebuild required)
```

---

## Tool 2: Build Your Stack Tool (PRIORITY #2)

### Purpose
Personalized stack gap analysis -users input what they have, get recommendations for what they need.

### User Flow
1. **Input existing stack:** User selects what they already have per layer
   - Layer 1 (Storage): "We use Snowflake" / "We use Databricks" / "None"
   - Layer 2 (Real-Time): "We have Kafka" / "We have CDC" / "None"
   - ... for all 7 layers
2. **Context questions:**
   - Industry (healthcare, finance, retail, other)
   - Scale (users, data volume)
   - Compliance requirements (HIPAA, SOC2, GDPR)
   - Budget tier (Starter, Growth, Enterprise)
3. **Output:**
   - Visual stack diagram (layers you have vs. gaps)
   - Prioritized build order
   - Estimated investment by layer
   - Integration considerations
   - "Next: Use Vendor Selector to choose specific products"

### Key Differentiator
Shows users what they DON'T need to buy (layers already covered) vs what they DO need. Saves money and prevents over-purchasing.

---

## Tool 3: Vendor Selector (PRIORITY #3)

### Purpose
Living advisory tool that helps users select vendors for each layer. Unlike static comparison tables, this chatbot:
- Stays current as vendors launch, pivot, or retire
- Asks about user's context and personalizes recommendations
- Explains trade-offs dynamically
- Compares vendors on demand

### Knowledge Base
- `kb_vendor_advisor.md` (~97,000 words of vendor evaluation data)
- Quarterly updates with new vendors, pricing changes, feature updates

### User Flow
1. User asks: "What vector database should I use?"
2. Chatbot asks clarifying questions:
   - "What's your budget tier?"
   - "Do you need HIPAA BAA?"
   - "Are you on AWS, Azure, or GCP?"
3. Chatbot provides recommendations:
   - "For healthcare on AWS with mid-tier budget, I recommend Pinecone or Weaviate..."
   - "Here's why: [trade-off explanation]"
4. User can ask follow-ups:
   - "How does Pinecone compare to Weaviate for real-time updates?"
   - "What about Chroma for a POC?"

### Synergy with Build Your Stack
- Build Your Stack identifies gaps → Chatbot helps select specific vendors
- "Build Your Stack says you need Layer 3. Let me help you choose a semantic layer product."

### Output: Vendor Evaluation Scorecard
Users can request a PDF scorecard comparing their shortlisted vendors:
- Side-by-side INPACT™ scores (dimensions relevant to that layer)
- GOALS™ operational readiness scores (25 points)
- Weighted total based on user's priorities
- Pros/cons summary for each vendor
- Recommended selection with rationale

---

## Tool 4: 90-Day Implementation Tracker

### Purpose
Complete implementation tracking from Day Zero readiness through 90-day transformation.

**Key Insight:** 67% of agent deployments fail in Week 1, not because of bad AI, but because of missing Day Zero preparation. This tool gates Week 1 access until Day Zero readiness is confirmed.

### Format
Web-based application with 8 tabs:
1. **Tab 0: Day Zero Readiness** ⭐ -50-item checklist across 5 domains (GATE for Week 1)
2. **Tab 1: Weekly Progress** -Status by week (1-12)
3. **Tab 2: INPACT™ Tracking** -Score progression week-over-week
4. **Tab 3: GOALS™ Tracking** -Score progression week-over-week
5. **Tab 4: Layer Status** -Which of 7 layers complete
6. **Tab 5: Risks** -Risk register with mitigations
7. **Tab 6: Communications** -Stakeholder communication log
8. **Tab 7: Budget** -Actual vs planned spending

### Day Zero Gate Logic
- **Readiness ≥ 90%** with no critical blockers → Unlock Week 1
- **Readiness < 90%** or critical blockers exist → Show remediation guidance, keep Week 1 locked

### Day Zero Domains (50 items)
| Domain | Items | Critical Items |
|--------|-------|----------------|
| Stakeholder Alignment | 10 | 5 |
| Technical Prerequisites | 12 | 5 |
| Data Readiness | 10 | 3 |
| Security & Compliance | 10 | 4 |
| Resource Commitment | 8 | 4 |

### Echo Benchmark Integration
- Pre-populated with Echo's trajectory: Week 0 (28), Week 4 (42), Week 7 (67), Week 10 (86), Week 12 (89)
- User's scores overlay on same chart for visual comparison

### Source
- Day Zero Preparedness Checklist -integrated as Tab 0
- Chapter 10 (90-Day Transformation)

---

## Tool 5: Compliance Navigator

### Purpose
Universal compliance assessment covering 30 categories and 200+ regulatory frameworks. Helps organizations identify which compliance requirements apply to their AI agent initiatives.

### Categories (30 Total)
Expanded from healthcare-only to universal coverage:

| Category Group | Examples |
|---------------|----------|
| **Data Privacy** | GDPR, CCPA, LGPD, POPIA |
| **Health Data** | HIPAA, HITECH, FDA 21 CFR Part 11 |
| **Financial Data** | SOX, PCI-DSS, GLBA, Basel III |
| **AI-Specific** | EU AI Act, NIST AI RMF, ISO 42001 |
| **Industry Standards** | ISO 27001, SOC 2, NIST CSF |
| **Government** | FedRAMP, FISMA, ITAR |
| **And 24 more...** | Education, Insurance, Telecom, etc. |

### User Flow
1. **Profile-based filtering:** Select geography, industry, data types
2. **Applicable framework identification:** Which regulations apply
3. **Gap assessment:** Compliance status per framework
4. **Risk scoring:** Penalty exposure calculation
5. **Remediation guidance:** Priority-ordered actions

### Source
- Healthcare compliance content expanded to 30 universal categories
- INPACT™ Practitioner Reference for scoring rubrics

---

## Downloadable Templates

In addition to interactive tools, the following templates are available for download:

### Template 1: Three-Pillar RFP Template

**Purpose:** Structure vendor evaluation requests using the INPACT™ + Architecture Fit + GOALS™ methodology from Chapter 11.

**Format:** Word document (.docx)

**Contents:**
1. **Introduction section** -Project context, timeline, budget tier
2. **Pillar 1: INPACT™ Questions** -Questions per dimension (I, N, P, A, C, T) relevant to the layer being evaluated
3. **Pillar 2: Architecture Fit Questions** -Layer integration, cloud compatibility, existing stack alignment
4. **Pillar 3: GOALS™ Questions** -Operational readiness (G, O, A, L, S) for production deployment
5. **Response format requirements** -Scoring rubric explanation, demo request, reference requirements
6. **Evaluation criteria** -How responses will be scored and weighted

**Customization:** Users select their layer (1-7) and the template pre-populates relevant questions.

---

### Template 2: POC Test Plan Template

**Purpose:** Structure the two-week Proof of Concept validation from Chapter 11's evaluation process.

**Format:** Word document (.docx) + Excel checklist (.xlsx)

**Contents:**

**Week 1: INPACT™ Validation**
| Day | Focus | Success Criteria |
|-----|-------|------------------|
| 1-2 | Instant (I) | Response time <2s under load |
| 3 | Natural (N) | Query accuracy >75% on test set |
| 4 | Permitted (P) | ABAC policies enforce correctly |
| 5 | Adaptive (A) | Feedback loop captures corrections |

**Week 2: GOALS™ Validation**
| Day | Focus | Success Criteria |
|-----|-------|------------------|
| 6 | Governance (G) | Audit logs capture all decisions |
| 7 | Observability (O) | Metrics visible in dashboard |
| 8 | Availability (A) | Handles 10x expected load |
| 9 | Lexicon (L) | Business terms resolve correctly |
| 10 | Solid (S) | Data quality checks pass |

**Includes:**
- Test case templates for each dimension
- Pass/fail criteria with thresholds
- Stakeholder sign-off checklist
- Go/No-Go decision matrix

---

## Lead Capture Strategy

### Required Fields by Tool Type

**Assessments (INPACT™):**
- Email (required)
- Name (required)
- Company (required)
- Role (required)
- Industry (optional)

**Interactive Tools (Build Your Stack, Vendor Chatbot):**
- Email (required)

**Downloadable Templates:**
- Email (optional, but prominently requested)

### Follow-up Sequence
1. **Immediate:** PDF report/template delivery
2. **Day 3:** "How to interpret your results" email
3. **Day 7:** Related chapter excerpt
4. **Day 14:** Echo case study
5. **Day 30:** Consultation offer

---

## Launch Plan

### Phase 1: Core Assessment (Month 1-2)
- **INPACT™ Assessment** ← PRIORITY #1
- Landing page with email capture
- Basic analytics

### Phase 2: Stack Tools (Month 3-4)
- Build Your Stack Tool
- 90-Day Tracker (with integrated Day Zero as Tab 0)

### Phase 3: Vendor Chatbot (Month 5-6)
- Vendor Selector (conversational AI)
- Knowledge base with quarterly update process
- Compliance Navigator (30-category universal assessment)

### Phase 4: Community Features (Month 6+)
- User reviews (moderated)
- Premium access tier
- Certified practitioner integration

---

## Success Metrics

| Metric | Target (6 months) |
|--------|-------------------|
| INPACT™ Assessment completions | 1,000 |
| Build Your Stack analyses | 500 |
| Vendor Chatbot conversations | 2,000 |
| Email captures (total) | 3,000 |
| Template downloads | 1,500 |
| Consultation requests | 75 |

---

## Branding Requirements

### Visual Identity
- Book cover colors (teal, white, dark gray)
- Colaberry logo
- "Trust Before Intelligence" wordmark
- INPACT™ and GOALS™ trademark symbols (™)

### Footer
```
© 2026 Colaberry Inc. All rights reserved.
INPACT™ and GOALS™ are trademarks of Colaberry Inc.
From "Trust Before Intelligence" by Ram Katamaraja
```

### Cross-References
Each tool should reference its companion content:
- "For INPACT™ scoring details, see the INPACT™ Practitioner Reference appendix"
- "For implementation guidance, see Chapters 4-6 (Architecture) and Chapter 10 (90-Day Roadmap)"
- "For vendor selection methodology, see Chapter 11"

---

**© 2026 Colaberry Inc. All rights reserved.**
