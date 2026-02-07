# INPACT™ Practitioner Reference
## Scoring Rubrics, Anti-Patterns, and Quick Reference

**Purpose:** Quick reference for scoring and implementing INPACT™
**Use:** Look up scoring criteria and avoid common mistakes during implementation
**For full framework details:** See Chapter 2

---

## INPACT™ at a Glance

| Need | What It Means | Target |
|------|---------------|--------|
| **I** - Instant | Sub-second response times | <2s (p95) |
| **N** - Natural | Business language understanding | 75-85% accuracy |
| **P** - Permitted | Dynamic authorization (ABAC + HITL) | <10ms policy evaluation |
| **A** - Adaptive | Continuous learning from feedback | Weekly improvements |
| **C** - Contextual | Cross-system data integration | 5-8+ sources |
| **T** - Transparent | Audit trails and explainable reasoning | 100% coverage |

**All six needs are required.** Missing even one significantly increases failure risk.

---

## Scoring Rubrics (1-6 per Need)

### I - Instant

| Score | Criteria | Primary Layers |
|-------|----------|----------------|
| **6** | <100ms response (with caching) | L1, L2, L4 |
| **5** | <1s response |  |
| **4** | 1-2s response |  |
| **3** | 2-5s response |  |
| **2** | 5-10s response |  |
| **1** | >10s response |  |

---

### N - Natural

| Score | Criteria | Primary Layers |
|-------|----------|----------------|
| **6** | >85% NLU accuracy (with fine-tuning) | L3, L4, L1 |
| **5** | 80-85% accuracy |  |
| **4** | 75-80% accuracy |  |
| **3** | 60-75% accuracy |  |
| **2** | 40-60% accuracy (keyword matching) |  |
| **1** | <40% accuracy |  |

---

### P - Permitted

| Score | Criteria | Primary Layers |
|-------|----------|----------------|
| **6** | ABAC + audit + HITL for critical decisions | L5, L6 |
| **5** | ABAC + 100% audit logging |  |
| **4** | ABAC operational (<10ms evaluation) |  |
| **3** | Basic ABAC (policies defined) |  |
| **2** | RBAC only (no contextual layer) |  |
| **1** | No access controls |  |

---

### A - Adaptive

| Score | Criteria | Primary Layers |
|-------|----------|----------------|
| **6** | Automated retraining (1-2% weekly gains) | L6, L2, L4 |
| **5** | Automated monitoring + continuous improvement |  |
| **4** | Weekly feedback review |  |
| **3** | Manual quarterly review |  |
| **2** | Feedback capture only (no action) |  |
| **1** | No feedback mechanism |  |

---

### C - Contextual

| Score | Criteria | Primary Layers |
|-------|----------|----------------|
| **6** | 10+ data sources, real-time | L2, L3, L1, L4 |
| **5** | 9-10 data sources |  |
| **4** | 7-8 data sources |  |
| **3** | 5-6 data sources |  |
| **2** | 3-4 data sources |  |
| **1** | 1-2 data sources |  |

---

### T - Transparent

| Score | Criteria | Primary Layers |
|-------|----------|----------------|
| **6** | Audit logs + citations + reasoning traces | L5, L6, L4, L3 |
| **5** | Audit logs + citations (source attribution) |  |
| **4** | Audit logs + trace IDs |  |
| **3** | Audit logs operational |  |
| **2** | Basic logs only |  |
| **1** | No audit trails |  |

---

## INPACT™ Scoring System

### Overall INPACT™ Score

**Total Score:** Sum of 6 dimensions (1-6 each) = **6 to 36 points**

**Interpretation:**
- **31-36 points (86-100%):** High Trust  - Production-ready
- **24-30 points (67-85%):** Good Trust  - Pilot-ready, minor gaps
- **18-23 points (50-66%):** Moderate Trust  - Significant work needed
- **12-17 points (33-49%):** Low Trust  - Major transformation required
- **6-11 points (<33%):** Very Low Trust  - Complete rebuild required

---

## INPACT™ Scoring Template

**Use this template to track progress:**

| Need | Baseline | Week 4 | Week 7 | Week 10 | Week 12 |
|------|----------|--------|--------|---------|---------|
| **I** - Instant | ___/6 | ___/6 | ___/6 | ___/6 | ___/6 |
| **N** - Natural | ___/6 | ___/6 | ___/6 | ___/6 | ___/6 |
| **P** - Permitted | ___/6 | ___/6 | ___/6 | ___/6 | ___/6 |
| **A** - Adaptive | ___/6 | ___/6 | ___/6 | ___/6 | ___/6 |
| **C** - Contextual | ___/6 | ___/6 | ___/6 | ___/6 | ___/6 |
| **T** - Transparent | ___/6 | ___/6 | ___/6 | ___/6 | ___/6 |
| **TOTAL** | ___/36 | ___/36 | ___/36 | ___/36 | ___/36 |
| **Target** | Assess | ~15/36 | ~24/36 | ~31/36 | ~32/36 |

**Phase Targets (based on Echo Health journey):**
- **Phase 1 Exit (Week 4):** ~15/36 (42%)  - Foundation complete
- **Phase 2 Exit (Week 7):** ~24/36 (67%)  - Intelligence live
- **Phase 3 Exit (Week 10):** ~31/36 (86%)  - Governance complete, production-ready
- **Operations (Week 12):** ~32/36 (89%)  - Sustained high trust

---

## How INPACT™ Maps to Architecture

**The 7-layer architecture (Chapters 4-6) delivers the 6 INPACT™ needs:**

| INPACT™ Need | Primary Layers | Infrastructure Capability |
|--------------|----------------|---------------------------|
| **I** - Instant | L2, L1, L4, L7 | Sub-Second Response Architecture |
| **N** - Natural | L3, L4, L1 | Semantic Understanding |
| **P** - Permitted | L5, L6 | Dynamic Authorization + HITL |
| **A** - Adaptive | L6, L2, L4 | Continuous Learning |
| **C** - Contextual | L2, L3, L1, L4 | Cross-Domain Integration |
| **T** - Transparent | L5, L6, L4, L3 | Auditability & Explainability |

**Key Insight:** Every INPACT™ need requires **multiple layers working together**. No single layer solves any need alone.

---

## Common INPACT™ Anti-Patterns

### ❌ Anti-Pattern 1: "We Have a Vector DB, So We're Agent-Ready"

**Problem:** Vector DB alone only addresses part of "I" (Instant) and "N" (Natural). Missing: real-time data (C), governance (P), observability (A, T).

**Fix:** Build all 7 layers, not just Layer 1 (Storage).

---

### ❌ Anti-Pattern 2: "We'll Add HITL Later"

**Problem:** Starting without HITL means training users to trust agent recommendations. When you add HITL later, users resist human oversight.

**Fix:** Start with HITL for critical decisions from Week 1 (Layer 5 governance).

---

### ❌ Anti-Pattern 3: "Accuracy Will Improve Over Time Without Feedback"

**Problem:** Static agents degrade as data and business logic drift. Accuracy drops 1-2% per month without feedback loops.

**Fix:** Implement feedback capture (Week 9) and weekly review cycles (Adaptive need).

---

### ❌ Anti-Pattern 4: "Batch ETL is Fine for Agents"

**Problem:** Agents need real-time context. 24-hour-old data = wrong answers (e.g., "Is this patient still in the hospital?" using yesterday's data).

**Fix:** Implement CDC and streaming (Week 4, Layer 2) for <1 hour freshness.

---

### ❌ Anti-Pattern 5: "Users Don't Need to See Sources"

**Problem:** Black-box agents erode trust. "Because I said so" doesn't work for humans or agents.

**Fix:** Implement citations and reasoning traces (Transparent need, Layer 6).

---

## Reference

**For complete details on INPACT™, see Chapter 2.**

**For architecture that delivers INPACT™, see Chapters 4-6.**

**For implementation guidance, see Chapter 10.**

---

**© 2025-2026 Colaberry Inc. All rights reserved.**  
**INPACT™ is a trademark of Colaberry Inc.**

---

**END OF INPACT™ PRACTITIONER REFERENCE**
