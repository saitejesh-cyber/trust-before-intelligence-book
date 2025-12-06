# Appendix DA-6: Trust Patterns Catalog

**Book:** Trust Before Intelligence: Why 95% of Agent Projects Fail—and the Architecture Blueprint That Fixes Infrastructure in 90 Days  
**Author:** Ram Katamaraja, CEO, Colaberry Inc.  
**Appendix:** F of H  
**Version:** 1.0  
**Date:** December 2025  
**Target:** 10-12 pages | Reference material for production operations

---

## Purpose

This appendix catalogs 15 production-tested trust patterns observed across 40+ enterprise AI agent implementations. Each pattern addresses a specific trust challenge that causes agents to fail—not from inadequate AI, but from architectural gaps that undermine user confidence.

**How to Use This Catalog:**

1. **Diagnose:** Identify which anti-pattern your organization exhibits
2. **Select:** Choose the corresponding trust pattern
3. **Implement:** Follow the implementation guidance with layer references
4. **Validate:** Use the success metrics to confirm pattern effectiveness

**Integration Points:**
- **Chapter 6 (Transparency Layers):** Layer 5-6-7 implementations reference patterns by ID
- **Chapter 12 (Production Operations):** Production operations use patterns for incident response
- **90-Day Tracker Tab 8:** Pattern implementation tracking

---

## Pattern Organization

Patterns are organized by the INPACT™ dimension they primarily address. Each pattern includes:

- **Pattern ID:** Unique identifier (TP-XX)
- **Anti-Pattern:** The failure mode this pattern corrects
- **Trust Pattern:** The architectural solution
- **Layer(s):** Which 7-Layer Architecture components are involved
- **Implementation:** Specific technical guidance
- **Echo Example:** How Echo Health Systems applied this pattern
- **Success Metrics:** How to measure pattern effectiveness

---

## INSTANT Dimension Patterns

### TP-01: Semantic Cache Circuit

**Anti-Pattern:** Every query hits the full RAG pipeline, causing 8-15 second response times that destroy conversational flow.

**Trust Pattern:** Implement semantic caching with similarity-based retrieval for repeated and similar queries.

**Layer(s):** Layer 1 (Storage), Layer 4 (Intelligence)

**Implementation:**
1. Deploy Redis or Momento for semantic cache layer
2. Configure embedding similarity threshold (typically 0.92-0.95)
3. Set TTL based on data freshness requirements (15 min for real-time, 24hr for static)
4. Implement cache invalidation triggers from CDC pipeline
5. Monitor cache hit rates; target 60%+ for production workloads

**Echo Example:** Echo's Patient Navigator achieved 67% cache hit rate, reducing average response time from 4.2s to 1.8s. Cache invalidation triggered automatically when patient records updated via Debezium CDC.

**Success Metrics:**
- Cache hit rate >60%
- P95 latency <3s
- Cache staleness <configured TTL

---

### TP-02: Streaming Freshness Guarantee

**Anti-Pattern:** Batch ETL processes create 24-72 hour data lag, causing agents to provide outdated information that destroys credibility.

**Trust Pattern:** Implement Change Data Capture (CDC) with sub-minute propagation guarantees.

**Layer(s):** Layer 2 (Real-Time Data Fabric)

**Implementation:**
1. Deploy Debezium connectors on source databases
2. Configure Kafka/Event Hub for reliable message delivery
3. Implement watermark tracking for freshness SLAs
4. Create freshness dashboards with alerting
5. Design graceful degradation when freshness SLA breached

**Echo Example:** Echo reduced data freshness from 72 hours to 12 seconds for Epic EHR data. When CDC lag exceeded 30 seconds, agents displayed freshness warnings: "Data as of [timestamp]."

**Success Metrics:**
- CDC lag <30 seconds (P95)
- Zero data loss during failover
- Freshness SLA compliance >99.5%

---

### TP-03: Query Timeout Escalation

**Anti-Pattern:** Slow queries hang indefinitely, leaving users staring at spinners and abandoning interactions.

**Trust Pattern:** Implement tiered timeout strategy with progressive disclosure.

**Layer(s):** Layer 1 (Storage), Layer 7 (Orchestration)

**Implementation:**
1. Set aggressive initial timeout (2s) for cached/simple queries
2. Configure secondary timeout (8s) for complex retrieval
3. Implement partial response delivery at timeout thresholds
4. Provide status updates during long-running queries
5. Offer graceful degradation: "I'm still searching, but here's what I know so far..."

**Echo Example:** Echo's Revenue Cycle agent used three-tier timeouts: 2s (cache), 5s (standard RAG), 10s (complex multi-hop). At 5s, users saw: "Checking additional sources..." with preliminary results.

**Success Metrics:**
- User abandonment rate <5%
- P99 latency <10s
- Partial response rate <10% of queries

---

## NATURAL Dimension Patterns

### TP-04: Business Glossary Grounding

**Anti-Pattern:** Agents misinterpret domain terminology, confusing "admission" (hospital stay) with "admission" (confession) or "chart" (medical record) with "chart" (graph).

**Trust Pattern:** Ground all NLU processing in enterprise-curated business glossary.

**Layer(s):** Layer 3 (Semantic Layer)

**Implementation:**
1. Build glossary with domain SMEs (minimum 500 terms for healthcare)
2. Include synonyms, abbreviations, and context rules
3. Integrate glossary into embedding pipeline
4. Implement term disambiguation using context signals
5. Track glossary coverage and add terms from failed queries

**Echo Example:** Echo's semantic layer included 847 healthcare concepts with 2,100+ synonyms. "BP" resolved to "blood pressure" in clinical contexts, "business plan" in administrative contexts.

**Success Metrics:**
- NLU accuracy >92%
- Glossary coverage of queries >95%
- Disambiguation accuracy >88%

---

### TP-05: Intent Clarification Loop

**Anti-Pattern:** Agents guess at ambiguous queries and provide wrong answers confidently, training users to distrust all responses.

**Trust Pattern:** Implement explicit clarification requests for low-confidence intent detection.

**Layer(s):** Layer 4 (Intelligence), Layer 7 (Orchestration)

**Implementation:**
1. Set confidence threshold for direct response (typically 0.85)
2. Design clarification prompts that narrow intent efficiently
3. Limit clarification rounds (2 maximum before escalation)
4. Track clarification patterns to improve intent model
5. Implement "Did you mean...?" suggestions for near-miss intents

**Echo Example:** When confidence fell below 0.85, Echo's agents asked: "I want to make sure I understand. Are you asking about [Option A] or [Option B]?" This reduced misinterpretation by 34%.

**Success Metrics:**
- Clarification request rate <15% of queries
- Post-clarification accuracy >95%
- User satisfaction with clarifications >4.0/5

---

## PERMITTED Dimension Patterns

### TP-06: Attribute-Based Access Control (ABAC)

**Anti-Pattern:** Static role-based permissions force over-provisioning, exposing sensitive data to unauthorized users.

**Trust Pattern:** Implement dynamic authorization evaluating user, resource, action, and context attributes.

**Layer(s):** Layer 5 (Governance)

**Implementation:**
1. Deploy policy engine (Open Policy Agent, Cedar, or equivalent)
2. Define attribute schema (user role, department, data classification, time, location)
3. Write policies in declarative language with explicit deny rules
4. Implement policy caching for sub-10ms evaluation
5. Log all authorization decisions with full context

**Echo Example:** Echo's ABAC policies evaluated 8 attributes per request. Nurses could access patient vitals during their shift for assigned patients. The same nurse couldn't access the same data from home at midnight for an unassigned patient.

**Success Metrics:**
- Policy evaluation latency <10ms (P95)
- Zero unauthorized access incidents
- Policy coverage >99% of data assets

---

### TP-07: Human-in-the-Loop Escalation

**Anti-Pattern:** Agents make high-stakes decisions autonomously, creating liability exposure and catastrophic failure potential.

**Trust Pattern:** Implement confidence-based escalation to human reviewers for high-risk decisions.

**Layer(s):** Layer 5 (Governance), Layer 6 (Observability)

**Implementation:**
1. Define decision categories with risk thresholds
2. Configure confidence thresholds by category (e.g., 0.95 for clinical, 0.85 for administrative)
3. Build escalation queue with SLA tracking
4. Train human reviewers on override documentation
5. Feed reviewer decisions back into model improvement

**Echo Example:** Echo escalated 8% of interactions (240 daily) to human review. Clinical recommendations below 0.92 confidence always escalated. Average HITL resolution: 23 seconds. No clinical errors in first 90 days.

**Success Metrics:**
- Escalation rate 5-15% (too low = risk, too high = inefficiency)
- HITL resolution time <30 seconds (P95)
- Override rate stable or declining

---

### TP-08: Minimum Necessary Access

**Anti-Pattern:** Agents retrieve entire records when they need single fields, exposing unnecessary PHI and creating compliance violations.

**Trust Pattern:** Implement field-level access control with purpose-based data minimization.

**Layer(s):** Layer 5 (Governance), Layer 4 (Intelligence)

**Implementation:**
1. Classify data fields by sensitivity level
2. Define purpose categories requiring specific fields
3. Implement query rewriting to filter unnecessary fields
4. Log field-level access for audit
5. Alert on anomalous access patterns

**Echo Example:** When answering "What's the patient's next appointment?", Echo's agent retrieved only appointment fields—not diagnoses, medications, or notes. PHI exposure reduced 73% compared to full-record retrieval.

**Success Metrics:**
- Field exposure ratio <0.1 (fields accessed / fields available)
- Zero minimum-necessary violations in audit
- Query efficiency improvement >30%

---

## ADAPTIVE Dimension Patterns

### TP-09: Feedback Loop Automation

**Anti-Pattern:** User corrections and preferences disappear into a void, forcing repeated corrections and eroding trust.

**Trust Pattern:** Implement closed-loop feedback capture with automated model updates.

**Layer(s):** Layer 6 (Observability), Layer 4 (Intelligence)

**Implementation:**
1. Capture implicit feedback (thumbs, regeneration, abandonment)
2. Capture explicit feedback (corrections, ratings)
3. Aggregate feedback into retraining datasets weekly
4. Implement A/B testing for model updates
5. Monitor for feedback gaming and adversarial inputs

**Echo Example:** Echo's agents improved 1.2% accuracy weekly through feedback loops. When nurses consistently corrected medication formatting, the semantic layer updated automatically within 48 hours.

**Success Metrics:**
- Feedback capture rate >40% of interactions
- Weekly accuracy improvement >0.5%
- Correction persistence (same correction not needed twice)

---

### TP-10: Drift Detection and Alerting

**Anti-Pattern:** Model performance degrades silently over months until catastrophic failure triggers emergency response.

**Trust Pattern:** Implement continuous monitoring for data drift, concept drift, and performance degradation.

**Layer(s):** Layer 6 (Observability)

**Implementation:**
1. Establish baseline distributions for key features
2. Configure statistical tests (KS test, PSI) for drift detection
3. Set multi-tier alerts (warning at 1σ, critical at 2σ)
4. Automate retraining triggers for drift beyond threshold
5. Maintain drift dashboard with trend visualization

**Echo Example:** Echo detected 91% of potential drift events before they impacted users. When ICD-10 code distributions shifted (new billing codes), alerts fired within 4 hours, triggering retraining that completed overnight.

**Success Metrics:**
- Drift detection rate >90%
- Mean time to detection <24 hours
- Zero production incidents from undetected drift

---

## CONTEXTUAL Dimension Patterns

### TP-11: Cross-System Entity Resolution

**Anti-Pattern:** Agents treat "John Smith" in Epic differently from "Smith, John" in Salesforce, providing fragmented and contradictory information.

**Trust Pattern:** Implement master data management with probabilistic entity matching.

**Layer(s):** Layer 1 (Storage), Layer 3 (Semantic Layer)

**Implementation:**
1. Define entity types requiring resolution (patient, provider, product)
2. Implement matching algorithms (fuzzy, phonetic, ML-based)
3. Configure confidence thresholds for auto-merge vs. human review
4. Maintain entity master with source system mappings
5. Propagate entity IDs to all downstream systems

**Echo Example:** Echo unified patient identities across Epic (MRN), Salesforce (Contact ID), and billing (Account). 98.4% of patients resolved automatically; 1.6% flagged for manual review.

**Success Metrics:**
- Auto-resolution rate >95%
- False positive rate <0.1%
- Query accuracy for multi-system entities >96%

---

### TP-12: Universal Context Window

**Anti-Pattern:** Agents respond using only the current message, ignoring conversation history and prior interactions that would improve accuracy.

**Trust Pattern:** Implement hierarchical context management with relevance-weighted retrieval.

**Layer(s):** Layer 4 (Intelligence), Layer 7 (Orchestration)

**Implementation:**
1. Define context types (immediate, session, historical, organizational)
2. Configure context window sizes by type (4K immediate, 16K session, 100K historical)
3. Implement relevance scoring for context selection
4. Design context compression for token efficiency
5. Maintain context persistence across sessions

**Echo Example:** Echo's agents maintained context across: current conversation (full), prior sessions (summarized), patient history (relevant excerpts), and organizational knowledge (as-needed). Response relevance improved 28%.

**Success Metrics:**
- Context utilization rate >70%
- Cross-session continuity score >4.2/5
- Token efficiency (relevant context / total context) >0.6

---

## TRANSPARENT Dimension Patterns

### TP-13: Citation and Provenance

**Anti-Pattern:** Agents provide answers without sources, forcing users to either blindly trust or independently verify every response.

**Trust Pattern:** Implement mandatory source citation with direct linking to authoritative records.

**Layer(s):** Layer 6 (Observability), Layer 4 (Intelligence)

**Implementation:**
1. Track provenance through entire RAG pipeline
2. Generate citations in consistent format (source, timestamp, confidence)
3. Implement deep linking to source systems where possible
4. Display citations by default, not on request
5. Track citation verification clicks to measure trust building

**Echo Example:** Every Echo response included citations: "Based on [Patient Chart, updated 2 mins ago] and [Clinical Protocol CP-2024-103]." Physicians clicked citations 23% of the time, building verification habits.

**Success Metrics:**
- Citation coverage 100% of factual claims
- Deep link success rate >95%
- Citation click-through rate 15-30% (indicates healthy verification)

---

### TP-14: Decision Audit Trail

**Anti-Pattern:** When something goes wrong, no one can reconstruct what the agent "thought" or why it made a particular decision.

**Trust Pattern:** Implement comprehensive decision logging with reasoning chain preservation.

**Layer(s):** Layer 6 (Observability), Layer 5 (Governance)

**Implementation:**
1. Log every decision point with inputs, outputs, and confidence
2. Preserve reasoning chains (chain-of-thought) for complex decisions
3. Implement trace correlation across distributed components
4. Design audit query interface for compliance review
5. Set retention policies aligned with regulatory requirements (7 years for HIPAA)

**Echo Example:** Echo's audit trail answered: "Why did the agent recommend Drug X?" with full reasoning: retrieval results, ranking scores, policy evaluations, and confidence thresholds. Average audit query: 3.2 seconds.

**Success Metrics:**
- Trace coverage 100% of interactions
- Audit query latency <5 seconds
- Compliance audit pass rate 100%

---

### TP-15: Uncertainty Communication

**Anti-Pattern:** Agents present low-confidence answers with the same authority as high-confidence answers, misleading users about reliability.

**Trust Pattern:** Implement calibrated confidence display with appropriate hedging language.

**Layer(s):** Layer 4 (Intelligence), Layer 7 (Orchestration)

**Implementation:**
1. Calibrate model confidence to actual accuracy
2. Define confidence bands with corresponding language
3. Implement visual confidence indicators (not just text)
4. Train agents to hedge appropriately: "Based on available data..." vs. "Definitely..."
5. Track user trust calibration (do they appropriately discount low-confidence answers?)

**Echo Example:** Echo used three confidence tiers: High (>0.9): direct statements; Medium (0.7-0.9): "Based on available information..."; Low (<0.7): "I'm not certain, but..." with HITL escalation offered.

**Success Metrics:**
- Confidence calibration error <5%
- User trust calibration (appropriate response to confidence levels)
- Overconfidence incidents: zero

---

## Anti-Pattern Quick Reference

| ID | Anti-Pattern | Trust Pattern | Primary Dimension |
|----|--------------|---------------|-------------------|
| TP-01 | Slow RAG responses | Semantic Cache Circuit | Instant |
| TP-02 | Stale data (24-72hr lag) | Streaming Freshness Guarantee | Instant |
| TP-03 | Hanging queries | Query Timeout Escalation | Instant |
| TP-04 | Domain term confusion | Business Glossary Grounding | Natural |
| TP-05 | Confident wrong answers | Intent Clarification Loop | Natural |
| TP-06 | Over-provisioned access | ABAC Implementation | Permitted |
| TP-07 | Autonomous high-risk decisions | HITL Escalation | Permitted |
| TP-08 | Excessive data retrieval | Minimum Necessary Access | Permitted |
| TP-09 | Lost user corrections | Feedback Loop Automation | Adaptive |
| TP-10 | Silent model degradation | Drift Detection and Alerting | Adaptive |
| TP-11 | Fragmented entity views | Cross-System Entity Resolution | Contextual |
| TP-12 | Context-blind responses | Universal Context Window | Contextual |
| TP-13 | Unsourced answers | Citation and Provenance | Transparent |
| TP-14 | Unexplainable decisions | Decision Audit Trail | Transparent |
| TP-15 | Overconfident responses | Uncertainty Communication | Transparent |

---

## Implementation Priority Matrix

Based on 40+ enterprise implementations, prioritize patterns by impact and effort:

**Quick Wins (High Impact, Low Effort):**
- TP-01: Semantic Cache Circuit
- TP-05: Intent Clarification Loop
- TP-13: Citation and Provenance

**Strategic Investments (High Impact, High Effort):**
- TP-06: ABAC Implementation
- TP-11: Cross-System Entity Resolution
- TP-14: Decision Audit Trail

**Foundation Builders (Medium Impact, Low Effort):**
- TP-02: Streaming Freshness Guarantee
- TP-04: Business Glossary Grounding
- TP-15: Uncertainty Communication

**Operational Excellence (Medium Impact, Medium Effort):**
- TP-07: HITL Escalation
- TP-09: Feedback Loop Automation
- TP-10: Drift Detection and Alerting

---

## Integration with 90-Day Tracker

The 90-Day Tracker (Tab 8) includes pattern implementation tracking:

| Week | Recommended Patterns | Phase |
|------|---------------------|-------|
| 1-4 | TP-01, TP-02, TP-03 | Foundation |
| 5-7 | TP-04, TP-05, TP-11, TP-12 | Intelligence |
| 8-10 | TP-06, TP-07, TP-08, TP-13, TP-14, TP-15 | Trust |
| 11-12 | TP-09, TP-10 | Operations |

---

**Pedagogical Disclaimer:** Echo Health Systems is a fictional teaching case. Pattern examples are illustrative of real implementation patterns observed across multiple deployments.

---

© 2025 Colaberry Inc. All Rights Reserved.

INPACT™ and GOALS™ are trademarks of Colaberry Inc.

---

**END OF APPENDIX F**
