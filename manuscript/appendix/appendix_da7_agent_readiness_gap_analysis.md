# Appendix DA-7: Agent Readiness Gap Analysis

**Book:** Trust Before Intelligence: Why 95% of Agent Projects Fail—and the Architecture Blueprint That Fixes Infrastructure in 90 Days  
**Author:** Ram Katamaraja, CEO, Colaberry Inc.  
**Appendix:** G of H  
**Version:** 1.0  
**Date:** December 2025  
**Target:** 10-12 pages | Complete assessment methodology

---

## Purpose

This appendix provides the complete INPACT™ assessment methodology, including all 36 questions, detailed scoring rubrics, gap identification patterns, and prioritization guidance. Use this appendix to conduct your own readiness assessment before beginning your transformation journey.

**How to Use This Appendix:**

1. **Prepare:** Gather stakeholders from data engineering, security, architecture, and business domains
2. **Assess:** Complete all 36 questions with evidence-based scoring
3. **Calculate:** Compute your INPACT™ score using the methodology provided
4. **Analyze:** Identify gap patterns and prioritize improvements
5. **Plan:** Map gaps to Chapter 10 phases for implementation roadmap

**Integration Points:**
- **Chapter 9:** Assessment methodology overview and Echo benchmark
- **Chapter 10:** Phase-by-phase implementation based on gap priorities
- **90-Day Tracker Tab 10:** Readiness gap heatmap tracking

---

## Assessment Methodology

### Scoring Scale (1-6)

Each question is scored on a six-point scale reflecting infrastructure capability:

| Score | Label | Description | Deployment Readiness |
|-------|-------|-------------|---------------------|
| **6** | Excellent | Best-in-class, exceeds requirements | Production + competitive advantage |
| **5** | Strong | Full production capability | Deploy with confidence |
| **4** | Functional | Adequate with minor gaps | Deploy with monitoring |
| **3** | Moderate | Basic capability, improvements needed | Pilot only |
| **2** | Significant Gap | Major gaps blocking progress | Not deployment-ready |
| **1** | Critical Gap | Inadequate, fundamental rebuild needed | Immediate remediation |

### Scoring Principles

**Evidence Required:** Every score must cite specific evidence. "We think we're a 4" is not acceptable. "Our P95 latency is 2.3 seconds based on last month's dashboard" is acceptable.

**Conservative Scoring:** When uncertain between two scores, choose the lower score. Optimistic assessments create downstream surprises.

**Cross-Functional Validation:** Scores should be validated by multiple stakeholders. Engineers may rate technical capability high while security rates governance low—both perspectives matter.

---

## The 36 Questions

### I — INSTANT (6 Questions)

Measures infrastructure's ability to deliver sub-second responses that match conversational expectations.

---

**I-1: Query Response Time**

*What is your P95 query response time for agent-relevant data?*

| Score | Criteria |
|-------|----------|
| 6 | <500ms P95, <100ms P50, consistent across query types |
| 5 | <1s P95, <300ms P50, occasional spikes under load |
| 4 | <3s P95, <1s P50, predictable performance |
| 3 | <5s P95, variable performance, load-dependent |
| 2 | 5-15s P95, frequent timeouts, unpredictable |
| 1 | >15s or frequent timeouts, unusable for conversation |

**Evidence Sources:** APM dashboards, database query logs, load test results

**Echo Baseline (Week 0):** Score 1 — 47-second average query time, 2-minute P95

---

**I-2: Data Freshness**

*How current is the data agents access?*

| Score | Criteria |
|-------|----------|
| 6 | Real-time (<1 minute), streaming architecture |
| 5 | Near real-time (<5 minutes), CDC operational |
| 4 | <1 hour freshness, reliable refresh cycles |
| 3 | <4 hours freshness, scheduled batch with monitoring |
| 2 | 4-24 hours freshness, overnight batch only |
| 1 | >24 hours or unknown freshness, no freshness SLA |

**Evidence Sources:** CDC lag dashboards, ETL schedules, data timestamp analysis

**Echo Baseline (Week 0):** Score 1 — 72-hour batch refresh cycle

---

**I-3: Cache Effectiveness**

*What is your semantic cache hit rate for repeated queries?*

| Score | Criteria |
|-------|----------|
| 6 | >70% hit rate, <10ms cache response, intelligent invalidation |
| 5 | 60-70% hit rate, <50ms cache response, TTL-based invalidation |
| 4 | 50-60% hit rate, <100ms cache response, manual invalidation |
| 3 | 30-50% hit rate, >100ms cache response, basic caching |
| 2 | <30% hit rate or no semantic caching, only exact match |
| 1 | No caching layer, every query hits full pipeline |

**Evidence Sources:** Cache analytics, Redis/Momento dashboards, application metrics

**Echo Baseline (Week 0):** Score 1 — No caching infrastructure

---

**I-4: Concurrent Query Handling**

*How many concurrent agent queries can your infrastructure handle?*

| Score | Criteria |
|-------|----------|
| 6 | >10,000 concurrent, auto-scaling, no degradation |
| 5 | 5,000-10,000 concurrent, auto-scaling with minor latency increase |
| 4 | 1,000-5,000 concurrent, manual scaling available |
| 3 | 500-1,000 concurrent, queue-based overflow handling |
| 2 | 100-500 concurrent, degradation under load |
| 1 | <100 concurrent or unknown capacity, frequent overload |

**Evidence Sources:** Load testing results, production traffic analysis, scaling configurations

**Echo Baseline (Week 0):** Score 2 — Systems designed for analyst queries, not agent volume

---

**I-5: API Latency**

*What is the end-to-end latency for agent API calls?*

| Score | Criteria |
|-------|----------|
| 6 | <200ms P95, optimized network path, edge deployment |
| 5 | <500ms P95, minimal network hops, regional deployment |
| 4 | <1s P95, standard cloud deployment |
| 3 | 1-3s P95, multiple service hops |
| 2 | 3-10s P95, legacy integration overhead |
| 1 | >10s P95 or synchronous blocking, unusable for agents |

**Evidence Sources:** API gateway metrics, distributed tracing, network analysis

**Echo Baseline (Week 0):** Score 2 — Legacy middleware adding 5+ seconds

---

**I-6: Timeout and Retry Strategy**

*How does your infrastructure handle slow or failed queries?*

| Score | Criteria |
|-------|----------|
| 6 | Intelligent timeouts, circuit breakers, graceful degradation, partial results |
| 5 | Tiered timeouts, automatic retry with backoff, fallback responses |
| 4 | Configurable timeouts, basic retry logic, error responses |
| 3 | Fixed timeouts, manual retry, generic error handling |
| 2 | Inconsistent timeout handling, retry storms possible |
| 1 | No timeout strategy, queries hang indefinitely |

**Evidence Sources:** Error handling code, resilience patterns documentation, incident history

**Echo Baseline (Week 0):** Score 1 — No timeout strategy, queries blocked until completion or crash

---

### N — NATURAL (6 Questions)

Measures infrastructure's ability to understand business language without technical translation.

---

**N-1: NLU Accuracy**

*What is your Natural Language Understanding accuracy for business queries?*

| Score | Criteria |
|-------|----------|
| 6 | >95% accuracy, handles ambiguity, multi-intent recognition |
| 5 | 92-95% accuracy, good disambiguation, reliable intent detection |
| 4 | 88-92% accuracy, handles common queries well |
| 3 | 80-88% accuracy, struggles with complex or ambiguous queries |
| 2 | 60-80% accuracy, frequent misinterpretation |
| 1 | <60% accuracy or no NLU capability, requires structured input |

**Evidence Sources:** NLU testing results, production accuracy metrics, user feedback

**Echo Baseline (Week 0):** Score 2 — Basic keyword matching, no semantic understanding

---

**N-2: Business Glossary Coverage**

*What percentage of domain terminology is captured in your semantic layer?*

| Score | Criteria |
|-------|----------|
| 6 | >95% coverage, 500+ terms, synonyms, context rules, continuous updates |
| 5 | 90-95% coverage, 300+ terms, synonyms included |
| 4 | 80-90% coverage, 200+ terms, basic synonyms |
| 3 | 60-80% coverage, 100+ terms, limited synonyms |
| 2 | 30-60% coverage, <100 terms, no synonyms |
| 1 | No business glossary or <30% coverage |

**Evidence Sources:** Glossary documentation, semantic layer configuration, coverage analysis

**Echo Baseline (Week 0):** Score 2 — Informal glossaries in spreadsheets, no system integration

---

**N-3: Text-to-SQL Accuracy**

*What is your accuracy for translating natural language to data queries?*

| Score | Criteria |
|-------|----------|
| 6 | >85% execution accuracy, handles joins/aggregations/filters |
| 5 | 80-85% execution accuracy, reliable for common patterns |
| 4 | 70-80% execution accuracy, works for simple queries |
| 3 | 60-70% execution accuracy, requires query validation |
| 2 | 40-60% execution accuracy, frequent errors |
| 1 | <40% accuracy or no text-to-SQL capability |

**Evidence Sources:** Text-to-SQL benchmark results, production query success rates

**Echo Baseline (Week 0):** Score 2 — Users must write SQL directly

---

**N-4: Semantic Search Quality**

*How relevant are your vector search results for natural language queries?*

| Score | Criteria |
|-------|----------|
| 6 | >90% relevance (top-5), hybrid search, reranking, metadata filtering |
| 5 | 85-90% relevance (top-5), vector + keyword hybrid |
| 4 | 80-85% relevance (top-5), pure vector search |
| 3 | 70-80% relevance (top-5), basic embeddings |
| 2 | 50-70% relevance, keyword search only |
| 1 | <50% relevance or no semantic search capability |

**Evidence Sources:** Retrieval evaluation metrics (MRR, NDCG), user satisfaction with search

**Echo Baseline (Week 0):** Score 2 — Keyword search only, no vector capability

---

**N-5: Multi-Turn Conversation Handling**

*Can your infrastructure maintain context across conversation turns?*

| Score | Criteria |
|-------|----------|
| 6 | Full context preservation, cross-session memory, relevance weighting |
| 5 | Session context preserved, reference resolution, 10+ turns |
| 4 | Session context preserved, 5-10 turns, basic reference resolution |
| 3 | Limited context (3-5 turns), some reference resolution |
| 2 | Minimal context (1-2 turns), frequent context loss |
| 1 | No conversation context, every query treated independently |

**Evidence Sources:** Conversation logs, context window configuration, user experience testing

**Echo Baseline (Week 0):** Score 2 — Each query independent, no conversation state

---

**N-6: Language Localization**

*Does your infrastructure support multiple languages and regional variations?*

| Score | Criteria |
|-------|----------|
| 6 | Full multilingual support, regional variations, cultural context |
| 5 | 5+ languages, regional terminology handling |
| 4 | 2-4 languages, basic translation |
| 3 | English + 1 language, limited regional support |
| 2 | English only with international user base |
| 1 | English only, appropriate for user base (or no language capability) |

**Evidence Sources:** Language configuration, translation quality metrics, user demographics

**Echo Baseline (Week 0):** Score 3 — English + Spanish for patient-facing, adequate for Echo's demographics

---

### P — PERMITTED (6 Questions)

Measures infrastructure's ability to enforce dynamic authorization and access control.

---

**P-1: Access Control Model**

*What access control model does your infrastructure implement?*

| Score | Criteria |
|-------|----------|
| 6 | Full ABAC with 8+ attributes, real-time evaluation, purpose binding |
| 5 | ABAC with 5-7 attributes, sub-second evaluation |
| 4 | ABAC with 3-4 attributes or enhanced RBAC with context |
| 3 | RBAC with role hierarchy, manual provisioning |
| 2 | Basic RBAC, static roles, slow provisioning |
| 1 | Shared credentials or no access control |

**Evidence Sources:** Access control architecture, policy engine configuration, provisioning workflow

**Echo Baseline (Week 0):** Score 1 — Shared database credentials, no granular control

---

**P-2: Policy Evaluation Latency**

*How quickly can your system evaluate access control policies?*

| Score | Criteria |
|-------|----------|
| 6 | <5ms P95, cached policies, distributed evaluation |
| 5 | <10ms P95, policy caching, centralized evaluation |
| 4 | <50ms P95, acceptable for most queries |
| 3 | 50-200ms P95, noticeable latency |
| 2 | 200ms-1s P95, significant overhead |
| 1 | >1s or synchronous database lookup for every request |

**Evidence Sources:** Policy engine metrics, authorization logs, performance testing

**Echo Baseline (Week 0):** Score 1 — No dynamic policy evaluation

---

**P-3: Human-in-the-Loop Capability**

*Can your infrastructure escalate decisions to human reviewers?*

| Score | Criteria |
|-------|----------|
| 6 | Full HITL with SLA tracking, feedback loops, analytics |
| 5 | HITL workflows with routing and queuing |
| 4 | Basic HITL for high-risk decisions |
| 3 | Manual escalation process, no automation |
| 2 | Escalation possible but no defined workflow |
| 1 | No escalation capability, fully autonomous or fully manual |

**Evidence Sources:** HITL workflow documentation, escalation metrics, queue configuration

**Echo Baseline (Week 0):** Score 1 — No escalation workflow

---

**P-4: Audit Trail Completeness**

*How complete are your audit trails for agent decisions?*

| Score | Criteria |
|-------|----------|
| 6 | 100% coverage, reasoning chains preserved, 7+ year retention, queryable |
| 5 | 100% coverage, key decision points logged, 5+ year retention |
| 4 | >95% coverage, decisions logged, 3+ year retention |
| 3 | >80% coverage, basic logging, 1+ year retention |
| 2 | Partial logging, inconsistent, short retention |
| 1 | No audit trail or <50% coverage |

**Evidence Sources:** Logging configuration, retention policies, audit query capability

**Echo Baseline (Week 0):** Score 1 — Application logs only, no decision audit trail

---

**P-5: Data Classification**

*Is your data classified and labeled for access control?*

| Score | Criteria |
|-------|----------|
| 6 | Full classification taxonomy, automated labeling, 100% coverage |
| 5 | Comprehensive classification, >95% coverage, regular review |
| 4 | Classification schema exists, >80% coverage |
| 3 | Basic classification (public/internal/confidential), 60-80% coverage |
| 2 | Informal classification, <60% coverage |
| 1 | No data classification |

**Evidence Sources:** Data catalog, classification policy, coverage metrics

**Echo Baseline (Week 0):** Score 2 — HIPAA awareness but no systematic classification

---

**P-6: Consent Management**

*Can your infrastructure respect and enforce user consent preferences?*

| Score | Criteria |
|-------|----------|
| 6 | Real-time consent enforcement, granular preferences, audit trail |
| 5 | Consent enforcement at query time, preference management |
| 4 | Consent captured and respected, manual enforcement |
| 3 | Basic consent capture, inconsistent enforcement |
| 2 | Consent captured but not enforced programmatically |
| 1 | No consent management |

**Evidence Sources:** Consent database, enforcement logic, compliance audit results

**Echo Baseline (Week 0):** Score 2 — HIPAA consent on file, not enforced by agents

---

### A — ADAPTIVE (6 Questions)

Measures infrastructure's ability to learn and improve from feedback and changing conditions.

---

**A-1: Feedback Loop Implementation**

*How effectively does your infrastructure capture and use feedback?*

| Score | Criteria |
|-------|----------|
| 6 | Closed-loop automation, weekly model updates, A/B testing |
| 5 | Automated feedback capture, monthly retraining, metrics tracking |
| 4 | Feedback capture, quarterly retraining cycle |
| 3 | Manual feedback collection, ad-hoc retraining |
| 2 | Feedback captured but not used systematically |
| 1 | No feedback capture mechanism |

**Evidence Sources:** Feedback pipeline, retraining schedule, improvement metrics

**Echo Baseline (Week 0):** Score 2 — User complaints tracked but not connected to improvement

---

**A-2: Drift Detection**

*Can your infrastructure detect when model performance degrades?*

| Score | Criteria |
|-------|----------|
| 6 | Real-time drift detection, automated alerts, retraining triggers |
| 5 | Daily drift monitoring, alerts on threshold breach |
| 4 | Weekly drift analysis, manual review process |
| 3 | Monthly performance review, reactive detection |
| 2 | Quarterly review or incident-triggered only |
| 1 | No drift detection |

**Evidence Sources:** Monitoring dashboards, alert configuration, drift detection algorithms

**Echo Baseline (Week 0):** Score 2 — Performance issues discovered through user complaints

---

**A-3: Model Versioning**

*How do you manage model versions and rollback capability?*

| Score | Criteria |
|-------|----------|
| 6 | Full versioning, instant rollback, A/B deployment, version analytics |
| 5 | Version control, <1 hour rollback, deployment automation |
| 4 | Version tracking, same-day rollback capability |
| 3 | Basic versioning, multi-day rollback process |
| 2 | Informal versioning, rollback requires rebuild |
| 1 | No versioning, rollback not possible |

**Evidence Sources:** MLOps tooling, version history, rollback procedures

**Echo Baseline (Week 0):** Score 2 — No model versioning infrastructure

---

**A-4: Context Personalization**

*Can your infrastructure adapt to individual user preferences and context?*

| Score | Criteria |
|-------|----------|
| 6 | Real-time personalization, preference learning, context adaptation |
| 5 | Session-based personalization, preference storage |
| 4 | Basic personalization based on role/department |
| 3 | Limited personalization, manual configuration |
| 2 | One-size-fits-all with minor customization |
| 1 | No personalization capability |

**Evidence Sources:** Personalization features, user profile system, adaptation metrics

**Echo Baseline (Week 0):** Score 2 — Static reports, no personalization

---

**A-5: Continuous Learning Pipeline**

*Is there infrastructure for continuous model improvement?*

| Score | Criteria |
|-------|----------|
| 6 | Fully automated pipeline, daily improvement cycles |
| 5 | Automated pipeline, weekly improvement cycles |
| 4 | Semi-automated pipeline, monthly cycles |
| 3 | Manual pipeline, quarterly updates |
| 2 | Ad-hoc updates, no defined pipeline |
| 1 | No learning pipeline |

**Evidence Sources:** MLOps infrastructure, training pipelines, update frequency

**Echo Baseline (Week 0):** Score 1 — No ML infrastructure

---

**A-6: Experimentation Capability**

*Can you run controlled experiments on agent behavior?*

| Score | Criteria |
|-------|----------|
| 6 | Full A/B testing, multi-variate, statistical rigor, auto-analysis |
| 5 | A/B testing framework, manual analysis |
| 4 | Basic A/B capability, limited traffic |
| 3 | Shadow mode testing, no production A/B |
| 2 | Manual testing only, no controlled experiments |
| 1 | No experimentation capability |

**Evidence Sources:** Experimentation platform, experiment history, statistical methodology

**Echo Baseline (Week 0):** Score 1 — No experimentation infrastructure

---

### C — CONTEXTUAL (6 Questions)

Measures infrastructure's ability to synthesize knowledge across systems and domains.

---

**C-1: System Integration Breadth**

*How many source systems feed your agent infrastructure?*

| Score | Criteria |
|-------|----------|
| 6 | 10+ systems, unified access layer, real-time sync |
| 5 | 7-10 systems, integrated with some latency |
| 4 | 5-6 systems, batch integration |
| 3 | 3-4 systems, manual integration points |
| 2 | 1-2 systems, siloed data |
| 1 | Single system or no integration |

**Evidence Sources:** Integration inventory, data flow diagrams, API catalog

**Echo Baseline (Week 0):** Score 3 — Epic, Salesforce, and billing only

---

**C-2: Entity Resolution**

*Can your infrastructure resolve entities across systems?*

| Score | Criteria |
|-------|----------|
| 6 | Real-time resolution, >99% accuracy, ML-based matching |
| 5 | Near real-time resolution, >97% accuracy |
| 4 | Batch resolution, >95% accuracy |
| 3 | Manual resolution, 90-95% accuracy |
| 2 | Partial resolution, <90% accuracy |
| 1 | No cross-system entity resolution |

**Evidence Sources:** MDM platform, resolution accuracy metrics, duplicate analysis

**Echo Baseline (Week 0):** Score 3 — MPI for patients, no other entity resolution

---

**C-3: Knowledge Graph Implementation**

*Do you have a knowledge graph representing domain relationships?*

| Score | Criteria |
|-------|----------|
| 6 | Production knowledge graph, real-time updates, >10M nodes |
| 5 | Knowledge graph, batch updates, 1-10M nodes |
| 4 | Basic knowledge graph, <1M nodes |
| 3 | Ontology without graph implementation |
| 2 | Informal relationships, no formal graph |
| 1 | No knowledge representation |

**Evidence Sources:** Graph database, ontology documentation, node/edge counts

**Echo Baseline (Week 0):** Score 2 — Healthcare ontologies (SNOMED, ICD-10) but no graph

---

**C-4: Cross-Domain Query Capability**

*Can agents query across multiple domains in a single request?*

| Score | Criteria |
|-------|----------|
| 6 | Seamless multi-domain, optimized query planning, sub-second |
| 5 | Multi-domain queries, some latency, unified results |
| 4 | Multi-domain possible, requires multiple queries |
| 3 | Limited cross-domain, manual joining |
| 2 | Single domain per query only |
| 1 | No cross-domain capability |

**Evidence Sources:** Query capabilities, federation layer, cross-domain testing

**Echo Baseline (Week 0):** Score 3 — Manual joins required for cross-system queries

---

**C-5: Temporal Context**

*Can your infrastructure provide historical context and trends?*

| Score | Criteria |
|-------|----------|
| 6 | Full temporal support, trend analysis, forecasting |
| 5 | Historical queries, basic trends |
| 4 | Point-in-time queries, limited history |
| 3 | Current state only, some history available |
| 2 | Current state only, no history |
| 1 | Snapshot data, no temporal capability |

**Evidence Sources:** Temporal data model, history retention, query capabilities

**Echo Baseline (Week 0):** Score 4 — EHR has history, limited trend capabilities

---

**C-6: Document Understanding**

*Can your infrastructure extract and integrate unstructured content?*

| Score | Criteria |
|-------|----------|
| 6 | Full document understanding, multi-format, entity extraction |
| 5 | Document parsing, text extraction, basic entity recognition |
| 4 | PDF/Word extraction, limited entity recognition |
| 3 | Basic text extraction only |
| 2 | Metadata only, no content extraction |
| 1 | No unstructured content capability |

**Evidence Sources:** Document processing pipeline, extraction accuracy, format support

**Echo Baseline (Week 0):** Score 3 — Basic OCR for scanned documents

---

### T — TRANSPARENT (6 Questions)

Measures infrastructure's ability to explain decisions and provide audit trails.

---

**T-1: Citation Generation**

*Can your infrastructure cite sources for agent responses?*

| Score | Criteria |
|-------|----------|
| 6 | 100% citation coverage, deep links, confidence scores, source freshness |
| 5 | >95% citation coverage, links to sources |
| 4 | >80% citation coverage, basic source attribution |
| 3 | Partial citations, inconsistent formatting |
| 2 | Occasional citations, no systematic approach |
| 1 | No citation capability |

**Evidence Sources:** Response samples, citation configuration, link verification

**Echo Baseline (Week 0):** Score 1 — No citation capability

---

**T-2: Reasoning Explainability**

*Can users understand why the agent made a decision?*

| Score | Criteria |
|-------|----------|
| 6 | Full reasoning chains, confidence breakdown, alternative paths |
| 5 | Step-by-step reasoning, key decision factors |
| 4 | Summary explanation, main factors identified |
| 3 | Basic explanation on request |
| 2 | Limited explanation, black box mostly |
| 1 | No explainability |

**Evidence Sources:** Explainability features, user testing, explanation samples

**Echo Baseline (Week 0):** Score 1 — No explanation capability

---

**T-3: Confidence Calibration**

*Is agent confidence aligned with actual accuracy?*

| Score | Criteria |
|-------|----------|
| 6 | <3% calibration error, dynamic adjustment, uncertainty quantification |
| 5 | <5% calibration error, regular calibration |
| 4 | <10% calibration error, periodic calibration |
| 3 | 10-20% calibration error, infrequent calibration |
| 2 | >20% calibration error or not measured |
| 1 | No confidence scores or severely miscalibrated |

**Evidence Sources:** Calibration metrics, confidence distribution analysis

**Echo Baseline (Week 0):** Score 1 — No confidence scoring

---

**T-4: Trace Correlation**

*Can you trace a request through all system components?*

| Score | Criteria |
|-------|----------|
| 6 | Full distributed tracing, <1s trace lookup, 100% coverage |
| 5 | Distributed tracing, >95% coverage |
| 4 | Request tracing, >80% coverage |
| 3 | Partial tracing, manual correlation required |
| 2 | Log correlation possible but difficult |
| 1 | No tracing capability |

**Evidence Sources:** Tracing infrastructure, trace examples, coverage metrics

**Echo Baseline (Week 0):** Score 1 — Application logs only, no correlation

---

**T-5: Compliance Reporting**

*Can you generate compliance reports for agent behavior?*

| Score | Criteria |
|-------|----------|
| 6 | Automated compliance reports, real-time dashboards, audit-ready |
| 5 | Regular compliance reports, dashboards, manual audit support |
| 4 | Periodic reports, basic metrics |
| 3 | Ad-hoc reports, manual data gathering |
| 2 | Limited reporting, significant manual effort |
| 1 | No compliance reporting |

**Evidence Sources:** Report samples, compliance dashboards, audit history

**Echo Baseline (Week 0):** Score 2 — Manual HIPAA audits, no agent-specific reporting

---

**T-6: Error Attribution**

*When something goes wrong, can you identify the cause?*

| Score | Criteria |
|-------|----------|
| 6 | Automated root cause analysis, <5 min MTTD, full context |
| 5 | Rapid diagnosis, <15 min MTTD, good context |
| 4 | Same-day diagnosis, adequate context |
| 3 | Multi-day diagnosis, limited context |
| 2 | Difficult diagnosis, requires extensive investigation |
| 1 | Cannot identify causes systematically |

**Evidence Sources:** Incident history, MTTD metrics, RCA documentation

**Echo Baseline (Week 0):** Score 1 — Multi-day investigation for any issue

---

## Calculating Your Score

### Step 1: Sum Raw Scores

Add all 36 scores:

**I:** ___ + ___ + ___ + ___ + ___ + ___ = ___/36  
**N:** ___ + ___ + ___ + ___ + ___ + ___ = ___/36  
**P:** ___ + ___ + ___ + ___ + ___ + ___ = ___/36  
**A:** ___ + ___ + ___ + ___ + ___ + ___ = ___/36  
**C:** ___ + ___ + ___ + ___ + ___ + ___ = ___/36  
**T:** ___ + ___ + ___ + ___ + ___ + ___ = ___/36  

**Total Raw Score:** ___/216

### Step 2: Calculate INPACT™ Score

**INPACT™ Score = (Total Raw Score ÷ 216) × 100**

Example: Echo Week 0 = (60 ÷ 216) × 100 = 28/100

### Step 3: Identify Trust Band

| Raw Score | Percentage | Trust Band |
|-----------|------------|------------|
| 186-216 | 86-100% | 🟢 High Trust |
| 144-185 | 67-85% | 🟡 Good Trust |
| 108-143 | 50-66% | 🟠 Moderate Trust |
| 72-107 | 33-49% | 🔴 Low Trust |
| 36-71 | 17-32% | ⚫ Very Low Trust |

---

## Gap Prioritization Matrix

### Identifying Critical Gaps

Gaps are most critical when:

1. **Dimension average <3:** Entire dimension is blocking production
2. **Any question scores 1:** Critical gap requiring immediate attention
3. **Dependency violations:** Low I/C scores block N/P/A/T improvements

### Priority Mapping to Phases

| Lowest Dimension | Priority Layers | Chapter 10 phase | Typical Timeline |
|------------------|-----------------|------------------|------------------|
| **I (Instant)** | L1, L2 | Phase 1: Foundation | Weeks 1-4 |
| **C (Contextual)** | L1, L2, L3 | Phase 1-2 | Weeks 1-7 |
| **N (Natural)** | L3, L4 | Phase 2: Intelligence | Weeks 5-7 |
| **P (Permitted)** | L5 | Phase 3: Trust | Weeks 8-10 |
| **T (Transparent)** | L5, L6 | Phase 3: Trust | Weeks 8-10 |
| **A (Adaptive)** | L4, L6 | Phase 3-4 | Weeks 8-12 |

---

## Common Gap Patterns

Based on 40+ enterprise assessments, these patterns recur:

### Pattern 1: "BI-Era Infrastructure"

**Signature:** I=1-2, C=3-4, others=1-2  
**Cause:** Infrastructure designed for batch reporting, not real-time agents  
**Remedy:** Full Phase 1-3 transformation (12+ weeks)

### Pattern 2: "Governance Gap"

**Signature:** I=4-5, N=3-4, P=1-2, T=1-2  
**Cause:** Good data infrastructure but no agent-aware security  
**Remedy:** Focus on Phase 3 (Weeks 8-10), accelerate governance

### Pattern 3: "Intelligence Gap"

**Signature:** I=4-5, N=1-2, P=3-4  
**Cause:** Modern data platform without semantic layer  
**Remedy:** Focus on Phase 2 (Weeks 5-7), build semantic capabilities

### Pattern 4: "Operations Gap"

**Signature:** I=4+, N=4+, P=4+, A=1-2, T=2-3  
**Cause:** Built agents but can't improve or explain them  
**Remedy:** Focus on Phase 4 (Weeks 11-12), operational excellence

---

## Integration with 90-Day Tracker

The 90-Day Tracker (Tab 10) provides:

- **Heatmap visualization** of gaps by dimension
- **Weekly progress tracking** against targets
- **Gap closure velocity** metrics
- **Dependency alerts** when sequence violations detected

---

**Pedagogical Disclaimer:** Echo Health Systems is a fictional teaching case. Scoring examples are illustrative of real assessment patterns observed across multiple enterprises.

---

© 2025 Colaberry Inc. All Rights Reserved.

INPACT™ and GOALS™ are trademarks of Colaberry Inc.

---

**END OF APPENDIX G**
