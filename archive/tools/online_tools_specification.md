# Online Tools Specification
## trustbeforeintelligence.com/tools

**Purpose:** Interactive digital companions to book appendixes  
**Version:** 3.0  
**Date:** January 2026  
**Status:** Specification (Pre-Development)

---

## Relationship to Book Appendixes

The book has two appendix tiers:
- **Print Appendixes (A-E):** In the physical book
- **Digital Appendixes (DA-1 through DA-8):** Accessed via QR code at trustbeforeintelligence.com/appendices

The online tools **complement** these appendixes by providing interactive, updateable versions. They do NOT duplicate the appendix content—they extend it.

### Print Appendixes (A-E)

| Appendix | Title | Pages | Online Tool |
|----------|-------|-------|-------------|
| **A** | Ch 1 Technical Deep-Dives | ~15 | — (reference only) |
| **B** | Ch 1 Pilot Case Studies | ~15 | — (reference only) |
| **C** | INPACT™ Framework Reference | ~18 | **INPACT™ Assessment** |
| **D** | Budget Methodology | ~8 | Budget Planning Worksheet |
| **E** | Quick Reference Card | ~8 | — (printable PDF) |

### Digital Appendixes (DA-1 through DA-8)

| Appendix | Title | Online Tool Companion |
|----------|-------|----------------------|
| **DA-1** | Technology Selection Guide | **Vendor Evaluation Scorecard** + **Live Vendor Database** |
| **DA-2** | GOALS™ Framework Reference | **GOALS™ Assessment** |
| **DA-3** | Healthcare Compliance Checklist | Contract Terms Checklist |
| **DA-4** | Intelligence Layers Tech Ref | — (reference only) |
| **DA-5** | INPACT™ Scoring Methodology | INPACT™ Assessment (scoring logic) |
| **DA-6** | Trust Patterns Catalog | — (reference only) |
| **DA-7** | Gap Analysis (36-Q) | **INPACT™ Assessment** (36 questions) |
| **DA-8** | Day Zero Preparedness | POC Test Plan Template |

**Principle:** Appendixes provide the **reference content**. Online tools provide the **interactive experience**.

---

## Tool Inventory (Priority Order)

| Priority | Tool | Primary Appendix | Format | Lead Capture |
|----------|------|------------------|--------|--------------|
| **1** | INPACT™ Assessment | C, DA-5, DA-7 | Web form → PDF | Required |
| **2** | GOALS™ Assessment | DA-2 | Web form → PDF | Required |
| **3** | Vendor Evaluation Scorecard | DA-1 | Interactive web app | Required |
| **4** | 90-Day Implementation Tracker | Chapter 10 | Excel/Google Sheets | Required |
| **5** | Live Vendor Database | DA-1 | Searchable web database | Required |
| **6** | Budget Planning Worksheet | D | Excel template | Optional |
| **7** | POC Test Plan Template | DA-8 | Downloadable DOCX/PDF | Optional |
| **8** | Contract Terms Checklist | DA-3 | Downloadable PDF | Optional |
| **9** | Build vs Buy Decision Matrix | Chapter 11 | Interactive web tool | Optional |

---

## Tool 1: INPACT™ Assessment (PRIORITY #1)

### Purpose
Interactive 36-question assessment to calculate organization's INPACT™ readiness score. This is the **primary lead generation tool** and should be prominently featured.

### Relationship to Appendixes
- **Appendix C (INPACT™ Framework Reference):** Provides dimension definitions
- **Appendix DA-5 (INPACT™ Scoring Methodology):** Provides 1-6 scoring rubrics
- **Appendix DA-7 (Gap Analysis):** Provides the 36 questions
- **Online Tool:** Interactive scoring, personalized PDF report, comparison to Echo baseline

### User Flow
1. Landing page with value proposition ("Discover your agent readiness score in 10 minutes")
2. User enters email, name, company, role to access
3. Context selection (healthcare, financial services, manufacturing, other)
4. 36 questions (6 per dimension) from Appendix DA-7
5. Scoring using rubrics from Appendix DA-5
6. Real-time score calculation
7. PDF report generation with:
   - Overall score (X/100)
   - Dimension breakdown radar chart
   - Trust band classification (from Appendix C)
   - Gap analysis with recommended chapters
   - Comparison to Echo Health baseline (28→89)
   - Next steps based on score

### Score Calculation (from DA-5)
```
Raw Score = Sum of all 36 answers (range: 36-216)
Normalized Score = ((Raw - 36) / 180) × 100 = 0-100

Trust Bands (from Appendix C):
- 86-100: High Trust (production-ready for healthcare)
- 67-85: Good Trust (targeted investment needed)
- 50-66: Moderate Trust (significant gaps)
- <50: Low Trust (full transformation required)
```

### Questions Source
All 36 questions come directly from **Appendix DA-7**. The tool implements the same questions with interactive UI and automatic scoring.

---

## Tool 2: GOALS™ Assessment

### Purpose
Interactive 25-question assessment to calculate organization's operational readiness.

### Relationship to Appendixes
- **Appendix DA-2 (GOALS™ Framework Reference):** Provides all content
- **Online Tool:** Interactive scoring, personalized PDF report, maturity classification

### User Flow
Same as INPACT™ Assessment but with 25 questions (5 per dimension).

### Score Calculation (from DA-2)
```
Raw Score = Sum of all 25 answers (range: 5-25)

Maturity Levels:
- 21-25: Production-Grade (enterprise-ready)
- 16-20: Adoption-Ready (stable, most workloads)
- 11-15: Emerging (proceed with caution)
- <11: Early-Stage (not production-ready)

Healthcare Requirement: ≥21/25 with G=5/5
```

---

## Tool 3: Vendor Evaluation Scorecard

### Purpose
Interactive tool for evaluating vendors against INPACT™ and GOALS™ frameworks.

### Relationship to Appendixes
- **Appendix DA-1 (Technology Selection Guide):** Provides reference vendor scores
- **Online Tool:** Allows users to score their own vendor evaluations

### Key Feature: Separate Scoring
INPACT™ and GOALS™ are scored **independently** (not combined). Tool enforces this by:
- Showing separate pass/fail indicators for each framework
- Requiring both to pass for "Recommended" verdict
- Highlighting which framework failed if one passes and one fails

### Scoring Logic (from Chapter 11)
```
INPACT™ Score = Sum of relevant dimension scores (max 36)
INPACT™ Pass = Score ≥ 24/36 (67%) for enterprise, ≥28/36 for healthcare

GOALS™ Score = Sum of dimension scores (max 25)
GOALS™ Pass = Score ≥ 18/25 (72%) for enterprise, ≥20/25 for healthcare

Verdict:
- Both pass → "Recommended" (green)
- One pass, one fail → "Proceed with Caution" (yellow) + identify which failed
- Both fail → "Not Recommended" (red)
```

---

## Tool 4: 90-Day Implementation Tracker

### Purpose
Weekly progress tracker for transformation projects.

### Relationship to Content
- **Chapter 10:** Provides week-by-week activities
- **Appendix DA-7:** Provides gap tracking
- **Online Tool:** Ongoing tracking, progress visualization

### Format
Google Sheets (shareable) or Excel with these tabs:
1. **Weekly Progress** - Status by week (1-12)
2. **INPACT™ Tracking** - Score progression week-over-week
3. **GOALS™ Tracking** - Score progression week-over-week
4. **Layer Status** - Which of 7 layers complete
5. **Risks** - Risk register with mitigations
6. **Budget** - Actual vs planned spending

### Echo Benchmark Integration
- Pre-populated with Echo's trajectory: Week 0 (28), Week 4 (42), Week 7 (67), Week 10 (86), Week 12 (89)
- User's scores overlay on same chart for visual comparison

---

## Tool 5: Live Vendor Database

### Purpose
Searchable, updateable database of vendors by layer—the "living" version of Appendix DA-1.

### Relationship to Appendixes
- **Appendix DA-1:** Provides point-in-time vendor analysis as of publication
- **Online Tool:** Quarterly updates, new vendors, community reviews, price changes

### Features
- **Search:** By vendor name, layer, category
- **Filter:** By BAA availability, budget tier, cloud platform
- **Sort:** By INPACT™ score, GOALS™ score, price
- **Details:** Vendor card with separate INPACT™ and GOALS™ scores
- **Updates:** Quarterly refresh with changelog
- **Community:** User ratings and reviews (moderated, premium feature)

### Key Difference from DA-1
DA-1 is static (publication date). Online database updates quarterly and can add new vendors immediately.

---

## Tools 6-9: Downloadable Templates

These tools are simpler downloadable templates that extend the book appendixes:

### Tool 6: Budget Planning Worksheet (Appendix D companion)
- Excel template with formulas
- Three-tier scenarios (Starter, Growth, Enterprise)
- Phase breakdown matching Chapter 10
- Echo benchmark comparison

### Tool 7: POC Test Plan Template (Appendix DA-8 companion)
- Word document with fillable fields
- Week 1 INPACT™ validation tests
- Week 2 GOALS™ + integration tests
- Pass/fail tracking

### Tool 8: Contract Terms Checklist (Appendix DA-3 companion)
- PDF checklist based on DA-3 content
- Must-have terms (BAA, SLA, exit clause, etc.)
- Negotiable terms
- Red flags

### Tool 9: Build vs Buy Decision Matrix (Chapter 11 companion)
- Simple interactive flowchart
- 5 decision questions from Chapter 11, Part 1.3
- Recommendation with rationale

---

## Lead Capture Strategy

### Required Fields by Tool Type

**Assessments (INPACT™, GOALS™):**
- Email (required)
- Name (required)
- Company (required)
- Role (required)
- Industry (optional)

**Interactive Tools (Scorecard, Database):**
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

### Phase 1: Core Assessments (Month 1-2)
- **INPACT™ Assessment** ← PRIORITY #1
- **GOALS™ Assessment**
- Landing page with email capture
- Basic analytics

### Phase 2: Evaluation Tools (Month 3-4)
- Vendor Evaluation Scorecard
- 90-Day Tracker template
- Build vs Buy Matrix

### Phase 3: Vendor Database (Month 5-6)
- Searchable database (extends DA-1)
- Quarterly update process
- Downloadable templates (Budget, POC, Contract)

### Phase 4: Community Features (Month 6+)
- User reviews (moderated)
- Premium access tier
- Certified practitioner integration

---

## Success Metrics

| Metric | Target (6 months) |
|--------|-------------------|
| INPACT™ Assessment completions | 1,000 |
| GOALS™ Assessment completions | 500 |
| Email captures (total) | 3,000 |
| Template downloads | 1,500 |
| Vendor database searches | 5,000 |
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
© 2025 Colaberry Inc. All rights reserved.
INPACT™ and GOALS™ are trademarks of Colaberry Inc.
From "Trust Before Intelligence" by Ram Katamaraja
```

### Appendix Cross-References
Each tool should reference its companion appendix:
- "For complete scoring rubrics, see Appendix DA-5"
- "For 36-question details, see Appendix DA-7"
- "For point-in-time vendor analysis, see Appendix DA-1"
- "For GOALS™ framework details, see Appendix DA-2"

---

**© 2025 Colaberry Inc. All rights reserved.**
