# Appendix DA-6: Patterns, Anti-Patterns & Failure Modes Catalog

**Book:** Trust Before Intelligence: Why 95% of Agent Projects Fail -and the Architecture Blueprint That Fixes Infrastructure in 90 Days
**Author:** Ram Katamaraja, CEO, Colaberry Inc.
**Date:** January 2026
**Target:** Comprehensive reference for diagnosing failures and implementing solutions

---

## Purpose

This appendix is the **single comprehensive reference** for understanding what can go wrong with enterprise AI agents and how to fix it. It consolidates:

1. **15 INPACT Trust Patterns**  - Architectural solutions for agent trust failures
2. **16 GOALS Failure Modes**  - What breaks when operational foundations fail
3. **16 Consolidated Anti-Patterns**  - Common mistakes to avoid

**How to Use This Catalog:**

1. **Diagnose:** Identify symptoms in your system
2. **Match:** Find the corresponding pattern, failure mode, or anti-pattern
3. **Implement:** Follow the fix with layer references
4. **Validate:** Use success metrics to confirm effectiveness

---

# Part 1: INPACT Trust Patterns

These 15 patterns address specific trust challenges organized by INPACT dimension.

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

**Success Metrics:**
- Confidence calibration error <5%
- User trust calibration (appropriate response to confidence levels)
- Overconfidence incidents: zero

---

# Part 2: GOALS Failure Modes

These 16 failure modes describe what breaks when each GOALS dimension fails. The "vital organs" metaphor is predictive -when one dimension fails, effects cascade through the system.

## G - Governance Failure Modes

### G1: ABAC Policy Bypass

**What Breaks:** Agent accesses data it shouldn't, violating HIPAA/GDPR requirements.

**How It Happens:**
- Policy misconfiguration during deployment
- Stale policies not updated when roles change
- Agent finds path around policy evaluation
- Emergency "break glass" access left open

**Impact:**
- Regulatory violations (HIPAA penalties up to $50,000+ per violation)
- Patient privacy breach
- Loss of trust with patients and partners
- Potential litigation

**Detection:** Audit log anomalies, unusual access patterns, compliance scanning

**Cascade Effects:**
- → O (Observability): Can't determine scope of unauthorized access if audit logs incomplete
- → S (Solid): Data integrity unknown -was data modified during unauthorized access?

---

### G2: HITL Escalation Failure

**What Breaks:** High-risk decisions execute without human review.

**How It Happens:**
- Escalation thresholds set too high
- Human reviewers overwhelmed, rubber-stamping approvals
- Escalation queue backed up, timeout triggers auto-approval
- Classification model fails to identify high-risk scenarios

**Impact:**
- Automated decisions cause patient harm
- Liability shifts to organization
- EU AI Act violations (Article 14 mandates human oversight for high-risk AI)
- Loss of clinical trust

**Detection:** HITL queue depth monitoring, approval rate anomalies, decision outcome tracking

**Cascade Effects:**
- → O (Observability): Without tracing, can't reconstruct decision path for post-incident review
- → L (Lexicon): If escalation triggered by query misinterpretation, Lexicon issues masked

---

### G3: Audit Trail Gap

**What Breaks:** Unable to reconstruct what happened during an incident.

**How It Happens:**
- Audit logging disabled for "performance"
- Log retention too short
- Log aggregation pipeline failure
- Incomplete trace IDs across services

**Impact:**
- Cannot prove compliance during audit
- Cannot determine breach scope
- Cannot identify root cause
- Regulatory fines for inadequate record-keeping

**Detection:** Log coverage monitoring, trace ID validation, audit completeness checks

**Cascade Effects:**
- → O (Observability): Observability depends on audit data; gaps blind the entire monitoring system
- → S (Solid): Cannot verify data integrity without audit trail of changes

---

### G4: Model Regression Without Rollback

**What Breaks:** New model deployment degrades quality; no ability to quickly revert.

**How It Happens:**
- Model updated without versioning
- Rollback procedure untested or nonexistent
- Quality regression not detected until widespread impact
- Deployment approval bypassed for "urgent" updates

**Impact:**
- Extended period of degraded answers
- User trust destruction
- Clinical risk if healthcare decisions affected
- Emergency manual intervention required

**Detection:** A/B quality comparison pre-deployment, automated regression testing, user feedback monitoring, rollback drill testing

**Cascade Effects:**
- → S (Solid): Quality degradation appears as data quality issue
- → L (Lexicon): Model regression may affect query interpretation
- → O (Observability): Without baseline comparison, regression hard to detect

---

## O - Observability Failure Modes

### O1: Blind Spots in Tracing

**What Breaks:** Cannot diagnose failures or understand agent behavior.

**How It Happens:**
- New service deployed without instrumentation
- Trace sampling drops critical requests
- Cross-service correlation IDs not propagated
- LLM calls not captured in trace

**Impact:**
- Extended mean time to resolution (MTTR)
- Repeated incidents from same root cause
- Cost overruns undetected
- Performance degradation unnoticed

**Detection:** Trace coverage metrics, orphan span detection, instrumentation audits

**Cascade Effects:**
- → G (Governance): Cannot verify governance policies are enforced
- → A (Availability): Cannot identify latency bottlenecks
- → S (Solid): Cannot correlate data quality issues with source

---

### O2: Alert Fatigue

**What Breaks:** Real problems ignored because teams desensitized to alerts.

**How It Happens:**
- Too many low-priority alerts
- Thresholds not tuned to actual impact
- Same alert fires repeatedly without resolution
- No clear ownership of alert response

**Impact:**
- Critical alerts missed or delayed
- Team burnout and turnover
- Extended incident duration
- False confidence in monitoring

**Detection:** Alert-to-incident ratio, response time tracking, alert acknowledgment rates

**Cascade Effects:**
- → All Dimensions: If alerts ignored, failures in G/A/L/S go undetected

---

### O3: Cost Visibility Failure

**What Breaks:** LLM costs spiral out of control undetected.

**How It Happens:**
- No per-query cost attribution
- Runaway retry loops on failed queries
- Expensive model used for simple queries
- Cache miss rate increases unnoticed

**Impact:**
- Budget overruns (potentially 10-100x expected costs)
- Project cancellation due to unsustainable economics
- Inability to optimize spending

**Detection:** Cost anomaly detection, per-query cost tracking, budget threshold alerts

**Cascade Effects:**
- → A (Availability): Cost controls may throttle availability
- → L (Lexicon): May force downgrade to cheaper, less capable models

---

## A - Availability Failure Modes

### A1: Response Time Degradation

**What Breaks:** Agent responses too slow for practical use; users abandon system.

**How It Happens:**
- Database queries unoptimized as data grows
- LLM provider latency increases
- Network congestion between services
- Cache effectiveness degrades

**Impact:**
- User abandonment (Echo Health's original 92% abandonment at 9-13 seconds)
- Workflow disruption
- Shadow IT adoption (users find workarounds)
- Project perceived as failure despite correct answers

**Detection:** p95/p99 latency monitoring, user session tracking, timeout rate monitoring

**Cascade Effects:**
- → L (Lexicon): Users simplify queries to get faster responses, reducing Lexicon effectiveness
- → S (Solid): Pressure to skip validation steps to improve speed

---

### A2: Data Freshness Lag

**What Breaks:** Agent provides stale information; users lose trust.

**How It Happens:**
- ETL pipeline delays
- Real-time sync failures
- Database replication lag
- Cache TTL too long

**Impact:**
- Wrong answers based on outdated data
- Clinical decisions based on stale lab results
- Compliance violations (reporting with outdated data)
- Trust destruction faster than any other failure mode

**Detection:** Data freshness monitoring, pipeline lag alerts, staleness checks on query

**Cascade Effects:**
- → S (Solid): Stale data may appear as data quality issue
- → G (Governance): Decisions based on stale data may violate policies

---

### A3: Scale Failure Under Load

**What Breaks:** System collapses during peak usage.

**How It Happens:**
- Autoscaling too slow
- Resource limits hit (connections, memory, CPU)
- Thundering herd after partial recovery
- No load shedding / graceful degradation

**Impact:**
- Complete service outage
- Cascading failures across dependent systems
- Extended recovery time
- Loss of confidence in platform reliability

**Detection:** Capacity utilization trending, load testing, chaos engineering

**Cascade Effects:**
- → O (Observability): Observability infrastructure may also fail under load
- → G (Governance): Emergency access procedures may bypass normal controls

---

## L - Lexicon Failure Modes

### L1: Entity Resolution Failure

**What Breaks:** Agent retrieves data for wrong entity (wrong patient, wrong provider, wrong facility).

**How It Happens:**
- Ambiguous references ("Dr. Martinez" matches three providers)
- Name changes not propagated
- Merged/split entities not handled
- Context insufficient for disambiguation

**Impact:**
- Wrong patient data accessed (HIPAA violation)
- Incorrect information provided
- Clinical safety risk
- Fundamental trust destruction

**Detection:** Entity resolution confidence scoring, disambiguation failure tracking, user correction monitoring

**Cascade Effects:**
- → G (Governance): Access controls assume correct entity -wrong entity = unauthorized access
- → S (Solid): Data quality metrics may pass while serving wrong data

---

### L2: Terminology Mapping Failure

**What Breaks:** Agent doesn't understand business/clinical terminology.

**How It Happens:**
- New terminology not added to ontology
- Regional/specialty variations not captured
- Abbreviations ambiguous ("MS" = multiple sclerosis or mental status?)
- Slang/informal terms not mapped

**Impact:**
- Query returns wrong results
- User gives up on system
- Workarounds emerge (users learn "magic words" that work)
- Ontology debt accumulates

**Detection:** Query failure analysis, zero-result query tracking, user reformulation patterns

**Cascade Effects:**
- → A (Availability): Bad queries may be expensive (long-running searches that find nothing)
- → O (Observability): Without query intent tracking, can't identify terminology gaps

---

### L3: Query Interpretation Drift

**What Breaks:** Accuracy degrades over time as language patterns change.

**How It Happens:**
- New use cases not reflected in training
- User population changes (new departments onboarded)
- Business terminology evolves
- Seasonal patterns not captured

**Impact:**
- Gradual accuracy decline goes unnoticed
- Users lose confidence slowly
- Expensive retraining needed

**Detection:** Interpretation accuracy trending, user feedback analysis, A/B testing against baseline

**Cascade Effects:**
- → O (Observability): Drift detection requires baseline observability
- → S (Solid): Drift may be misattributed to data quality issues

---

## S - Solid (Data Quality) Failure Modes

### S1: Silent Data Corruption

**What Breaks:** Data becomes incorrect without detection; agent confidently provides wrong answers.

**How It Happens:**
- Upstream system bug writes incorrect values
- Integration mapping error
- Character encoding issues
- Timezone handling bugs

**Impact:**
- Wrong answers with high confidence (worst case)
- Clinical decisions based on incorrect data
- Trust destroyed when discovered
- Difficult to determine scope of corruption

**Detection:** Statistical anomaly detection, cross-system reconciliation, data validation rules

**Cascade Effects:**
- → L (Lexicon): Semantic layer may cache/index corrupted data
- → G (Governance): Compliance reports based on corrupted data
- → O (Observability): Metrics calculated from corrupted data misleading

---

### S2: Completeness Degradation

**What Breaks:** Required data fields become empty; agent can't fulfill queries.

**How It Happens:**
- Upstream system changes remove fields
- Integration pipeline filter misconfigured
- Optional fields become required
- Source system data entry declining

**Impact:**
- Queries fail or return partial results
- Biased results (only complete records returned)
- Calculations incorrect (averages skewed by missing values)

**Detection:** Completeness monitoring by field, null rate trending, query failure analysis

**Cascade Effects:**
- → A (Availability): Incomplete data may cause query timeouts
- → L (Lexicon): Entity resolution harder with missing attributes

---

### S3: Cross-System Inconsistency

**What Breaks:** Same data has different values in different systems; agent provides contradictory answers.

**How It Happens:**
- Master data management failures
- Synchronization timing issues
- System-specific transformations
- Manual updates in one system only

**Impact:**
- Contradictory answers based on query routing
- User confusion and lost trust
- Compliance risk (which value is "official"?)
- Debugging nightmare (intermittent "wrong" answers)

**Detection:** Cross-system reconciliation, consistency scoring, golden record comparison

**Cascade Effects:**
- → L (Lexicon): Which source of truth should entity resolution use?
- → G (Governance): Audit trail shows different values -which is authoritative?

---

# Part 3: Consolidated Anti-Patterns

These 16 anti-patterns are common mistakes observed across enterprise AI agent implementations. They're organized by source framework.

## INPACT Anti-Patterns

### ❌ AP-01: "We Have a Vector DB, So We're Agent-Ready"

**Problem:** Vector DB alone only addresses part of "I" (Instant) and "N" (Natural). Missing: real-time data (C), governance (P), observability (A, T).

**Fix:** Build all 7 layers, not just Layer 1 (Storage).

---

### ❌ AP-02: "We'll Add HITL Later"

**Problem:** Starting without HITL means training users to trust agent recommendations. When you add HITL later, users resist human oversight.

**Fix:** Start with HITL for critical decisions from Week 1 (Layer 5 governance).

---

### ❌ AP-03: "Accuracy Will Improve Over Time Without Feedback"

**Problem:** Static agents degrade as data and business logic drift. Accuracy drops 1-2% per month without feedback loops.

**Fix:** Implement feedback capture (Week 9) and weekly review cycles (Adaptive need).

---

### ❌ AP-04: "Batch ETL is Fine for Agents"

**Problem:** Agents need real-time context. 24-hour-old data = wrong answers (e.g., "Is this patient still in the hospital?" using yesterday's data).

**Fix:** Implement CDC and streaming (Week 4, Layer 2) for <1 hour freshness.

---

### ❌ AP-05: "Users Don't Need to See Sources"

**Problem:** Black-box agents erode trust. "Because I said so" doesn't work for humans or agents.

**Fix:** Implement citations and reasoning traces (Transparent need, Layer 6).

---

## GOALS Anti-Patterns

### ❌ AP-06: "We Have Good Governance, So We're Ready"

**Problem:** G=5/5 but O=2/5 (no observability). Can't see when governance policies fail or when agents misbehave.

**Fix:** Build all five GOALS, not just one. They're interdependent like vital organs.

---

### ❌ AP-07: "We'll Add Observability After Launch"

**Problem:** Launching blind. When issues occur (and they will), you can't diagnose or fix them quickly.

**Fix:** Observability (O) must be operational before production launch (Week 9).

---

### ❌ AP-08: "Fast Responses Mean We're Production-Ready"

**Problem:** A=5/5 (fast responses) but S=2/5 (poor data quality). Fast wrong answers are worse than slow right answers.

**Fix:** Balance Availability with Solid. Speed without accuracy destroys trust.

---

### ❌ AP-09: "Our Semantic Layer Understands Everything"

**Problem:** L=4/5 (good semantic coverage) but no feedback loop. Lexicon doesn't improve when agents misunderstand queries.

**Fix:** Integrate Observability with Lexicon. Track query interpretation failures and expand ontology based on real usage.

---

### ❌ AP-10: "We Measure Data Quality Quarterly"

**Problem:** S=3/5 measured quarterly, but data quality can degrade in days. By the time you measure, agents have been giving wrong answers for weeks.

**Fix:** Continuous data quality monitoring integrated with Observability. Alert when quality metrics drop.

---

## Healthcare-Specific Anti-Patterns

### ❌ AP-11: No HITL for Clinical Decisions

**Bad:** Agent makes diagnosis/treatment recommendations without clinician review.

**Risk:** Malpractice liability, patient harm.

**Fix:** All clinical decisions require human confirmation (HITL).

---

### ❌ AP-12: Shared Database Across Patients

**Bad:** All patient data in one vector index with soft-delete only.

**Risk:** Data leakage (Patient A sees Patient B's info).

**Fix:** Tenant isolation (separate namespaces) or strict row-level security.

---

### ❌ AP-13: No Purpose-of-Use in ABAC

**Bad:** ABAC policy = `if user.role == 'doctor' then allow`

**Risk:** Doctors access unrelated patient records (HIPAA violation).

**Fix:** Require purpose: `if user.role == 'doctor' AND purpose == 'treatment' AND patient IN user.patients`

---

### ❌ AP-14: Logging PHI in Plain Text

**Bad:** Logs contain `"Patient John Smith, SSN 123-45-6789, has diabetes"`

**Risk:** Log aggregation platforms = PHI breach.

**Fix:** Log UUIDs only: `"Patient abc-123 accessed"` (no names, no SSNs).

---

### ❌ AP-15: No Bias Testing

**Bad:** Agent deployed without testing across demographics.

**Risk:** Worse outcomes for underrepresented groups (legal liability).

**Fix:** Test on stratified samples (age, race, gender, income), document results.

---

### ❌ AP-16: "We'll Add Compliance Later"

**Bad:** Build agent first, add ABAC/audit/encryption in Phase 3.

**Risk:** Technical debt, re-architecture required, delays.

**Fix:** Start with Layer 5 (Governance) in Week 1.

---

# Part 4: Quick Reference Tables

## INPACT Trust Patterns Summary

| ID | Anti-Pattern | Trust Pattern | Dimension | Layer(s) |
|----|--------------|---------------|-----------|----------|
| TP-01 | Slow RAG responses | Semantic Cache Circuit | Instant | L1, L4 |
| TP-02 | Stale data (24-72hr lag) | Streaming Freshness Guarantee | Instant | L2 |
| TP-03 | Hanging queries | Query Timeout Escalation | Instant | L1, L7 |
| TP-04 | Domain term confusion | Business Glossary Grounding | Natural | L3 |
| TP-05 | Confident wrong answers | Intent Clarification Loop | Natural | L4, L7 |
| TP-06 | Over-provisioned access | ABAC Implementation | Permitted | L5 |
| TP-07 | Autonomous high-risk decisions | HITL Escalation | Permitted | L5, L6 |
| TP-08 | Excessive data retrieval | Minimum Necessary Access | Permitted | L4, L5 |
| TP-09 | Lost user corrections | Feedback Loop Automation | Adaptive | L4, L6 |
| TP-10 | Silent model degradation | Drift Detection and Alerting | Adaptive | L6 |
| TP-11 | Fragmented entity views | Cross-System Entity Resolution | Contextual | L1, L3 |
| TP-12 | Context-blind responses | Universal Context Window | Contextual | L4, L7 |
| TP-13 | Unsourced answers | Citation and Provenance | Transparent | L4, L6 |
| TP-14 | Unexplainable decisions | Decision Audit Trail | Transparent | L5, L6 |
| TP-15 | Overconfident responses | Uncertainty Communication | Transparent | L4, L7 |

## GOALS Failure Modes Summary

| ID | Failure Mode | Dimension | Severity | Cascade Risk |
|----|--------------|-----------|----------|--------------|
| G1 | ABAC Policy Bypass | Governance | Critical | High |
| G2 | HITL Escalation Failure | Governance | Critical | High |
| G3 | Audit Trail Gap | Governance | High | High |
| G4 | Model Regression Without Rollback | Governance | High | High |
| O1 | Blind Spots in Tracing | Observability | High | Very High |
| O2 | Alert Fatigue | Observability | Medium | High |
| O3 | Cost Visibility Failure | Observability | Medium | Medium |
| A1 | Response Time Degradation | Availability | High | Medium |
| A2 | Data Freshness Lag | Availability | High | High |
| A3 | Scale Failure Under Load | Availability | Critical | High |
| L1 | Entity Resolution Failure | Lexicon | Critical | High |
| L2 | Terminology Mapping Failure | Lexicon | Medium | Medium |
| L3 | Query Interpretation Drift | Lexicon | Medium | Medium |
| S1 | Silent Data Corruption | Solid | Critical | Very High |
| S2 | Completeness Degradation | Solid | Medium | Medium |
| S3 | Cross-System Inconsistency | Solid | High | High |

## Anti-Patterns Summary

| ID | Anti-Pattern | Source | Fix Reference |
|----|--------------|--------|---------------|
| AP-01 | Vector DB = Agent-Ready | INPACT | Build all 7 layers |
| AP-02 | Add HITL Later | INPACT | TP-07 |
| AP-03 | Accuracy Improves Without Feedback | INPACT | TP-09 |
| AP-04 | Batch ETL is Fine | INPACT | TP-02 |
| AP-05 | Users Don't Need Sources | INPACT | TP-13 |
| AP-06 | Good Governance = Ready | GOALS | Build all 5 GOALS |
| AP-07 | Add Observability After Launch | GOALS | O1-O3 prevention |
| AP-08 | Fast = Production-Ready | GOALS | Balance A with S |
| AP-09 | Semantic Layer Understands All | GOALS | L1-L3 prevention |
| AP-10 | Quarterly Data Quality | GOALS | S1-S3 prevention |
| AP-11 | No HITL for Clinical | Healthcare | TP-07, G2 |
| AP-12 | Shared Patient Database | Healthcare | L1, G1 |
| AP-13 | No Purpose-of-Use | Healthcare | TP-06, G1 |
| AP-14 | PHI in Plain Text Logs | Healthcare | G3 |
| AP-15 | No Bias Testing | Healthcare | TP-09 |
| AP-16 | Compliance Later | Healthcare | Week 1 Layer 5 |

---

## Implementation Priority

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

---

**Pedagogical Disclaimer:** Echo Health Systems is a fictional teaching case. Pattern examples are illustrative of real implementation patterns observed across multiple deployments.