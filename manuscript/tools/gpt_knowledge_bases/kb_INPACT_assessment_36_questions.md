# Appendix DA-7: Agent Readiness Gap Analysis

**Book:** Trust Before Intelligence: Why 95% of Agent Projects Fail -and the Architecture Blueprint That Fixes Infrastructure in 90 Days  
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

**Cross-Functional Validation:** Scores should be validated by multiple stakeholders. Engineers may rate technical capability high while security rates governance low -both perspectives matter.

---

## The 36 Questions

### I  - INSTANT (6 Questions)

Measures infrastructure's ability to deliver sub-second responses that match conversational expectations.

---

**I-1: Response Time Capability**

*How quickly can your data infrastructure return query results for typical agent workloads?*

| Score | Criteria |
|-------|----------|
| 6 | Sub-1-second P99 latency for complex queries |
| 5 | Sub-2-second P95 latency, sub-5-second P99 |
| 4 | 2-5 second typical response, occasional delays |
| 3 | 5-10 second responses common |
| 2 | 10-30 second responses typical |
| 1 | Over 30 seconds, frequent timeouts |

**Evidence Sources:** APM dashboards, database query logs, load test results

**Echo Baseline (Week 0):** Score 1 - 9-13 second response times, overnight ETL

---

**I-2: Data Freshness**

*How current is the data available to your agents?*

| Score | Criteria |
|-------|----------|
| 6 | Sub-5-second freshness (streaming) |
| 5 | Sub-30-second freshness (real-time CDC) |
| 4 | 1-8 hour freshness (frequent batch) |
| 3 | 8-24 hour freshness (overnight batch) |
| 2 | 24-72 hour freshness (daily batch) |
| 1 | Over 72 hours (weekly or ad-hoc) |

**Evidence Sources:** CDC lag dashboards, ETL schedules, data timestamp analysis

**Echo Baseline (Week 0):** Score 1 - Overnight ETL, 8-24 hour data lag

---

**I-3: Caching Infrastructure**

*Do you have semantic caching that serves repeated or similar queries without full recomputation?*

| Score | Criteria |
|-------|----------|
| 6 | ML-powered predictive caching, 80%+ hit rate |
| 5 | Semantic caching operational, 60%+ hit rate |
| 4 | Basic caching, 40-60% hit rate |
| 3 | Simple key-value caching, under 40% hit rate |
| 2 | Minimal caching, under 20% hit rate |
| 1 | No caching infrastructure |

**Evidence Sources:** Cache analytics, Redis/Momento dashboards, application metrics

**Echo Baseline (Week 0):** Score 1 - No caching infrastructure

---

**I-4: Query Optimization**

*Is your storage layer optimized for agent query patterns (not just analyst workloads)?*

| Score | Criteria |
|-------|----------|
| 6 | Agent-specific optimization with continuous tuning |
| 5 | Optimized for agent patterns, regularly reviewed |
| 4 | Some optimization for common queries |
| 3 | Generic optimization, analyst-focused |
| 2 | Minimal optimization |
| 1 | No query optimization |

**Evidence Sources:** Query performance analysis, index configuration, optimization reviews

**Echo Baseline (Week 0):** Score 2 - Systems designed for analyst queries, not agent patterns

---

**I-5: Real-Time Data Pipelines**

*Do you have streaming or CDC pipelines that keep agent-accessible data current?*

| Score | Criteria |
|-------|----------|
| 6 | Enterprise-wide streaming with sub-second latency |
| 5 | CDC operational across primary systems |
| 4 | CDC for some systems, others batch |
| 3 | Limited streaming, mostly batch |
| 2 | Batch-only with some micro-batch |
| 1 | Overnight batch ETL only |

**Evidence Sources:** CDC configuration, streaming pipeline metrics, data freshness dashboards

**Echo Baseline (Week 0):** Score 1 - Overnight batch ETL only

---

**I-6: Performance Monitoring**

*Can you detect and respond to performance degradation in real-time?*

| Score | Criteria |
|-------|----------|
| 6 | Predictive alerting, auto-remediation |
| 5 | Real-time monitoring with immediate alerts |
| 4 | Near-real-time monitoring, manual response |
| 3 | Periodic monitoring, delayed alerts |
| 2 | Basic monitoring, reactive only |
| 1 | No performance monitoring |

**Evidence Sources:** Monitoring dashboards, alerting configuration, incident response history

**Echo Baseline (Week 0):** Score 1 - No real-time performance monitoring

---

### N  - NATURAL (6 Questions)

Measures infrastructure's ability to understand business language without technical translation.

---

**N-1: Semantic Layer Existence**

*Do you have a semantic layer that translates business terms to data structures?*

| Score | Criteria |
|-------|----------|
| 6 | Universal semantic layer covering all domains |
| 5 | Comprehensive coverage (80%+ of business concepts) |
| 4 | Functional coverage (core concepts mapped) |
| 3 | Partial coverage (limited domains) |
| 2 | Minimal semantic layer (basic glossary only) |
| 1 | No semantic layer |

**Evidence Sources:** Semantic layer configuration, business glossary documentation, coverage metrics

**Echo Baseline (Week 0):** Score 2 - No semantic layer, cryptic table names

---

**N-2: Natural Language Understanding Accuracy**

*What percentage of business questions does your system interpret correctly?*

| Score | Criteria |
|-------|----------|
| 6 | Over 90% accuracy with ambiguity handling |
| 5 | 75-90% accuracy on complex queries |
| 4 | 60-75% accuracy, single-table queries strong |
| 3 | 45-60% accuracy, simple queries only |
| 2 | 30-45% accuracy, frequent misinterpretation |
| 1 | Under 30% accuracy |

**Evidence Sources:** NLU testing results, production accuracy metrics, user feedback

**Echo Baseline (Week 0):** Score 2 - 40-60% understanding rate

---

**N-3: Business Glossary Coverage**

*How completely are business terms defined and mapped to data?*

| Score | Criteria |
|-------|----------|
| 6 | Complete glossary with automated maintenance |
| 5 | Comprehensive glossary (500+ terms), regularly updated |
| 4 | Functional glossary (200-500 terms) |
| 3 | Basic glossary (50-200 terms) |
| 2 | Minimal glossary (under 50 terms) |
| 1 | No business glossary |

**Evidence Sources:** Glossary documentation, term coverage analysis, update frequency

**Echo Baseline (Week 0):** Score 2 - Informal glossaries in spreadsheets

---

**N-4: Entity Resolution**

*Can your system resolve entities (customers, products, employees, accounts) across different naming conventions?*

| Score | Criteria |
|-------|----------|
| 6 | ML-powered entity resolution with confidence scores |
| 5 | Robust entity resolution across all systems |
| 4 | Entity resolution for primary entities |
| 3 | Basic entity resolution, manual rules |
| 2 | Limited entity resolution, frequent errors |
| 1 | No entity resolution |

**Evidence Sources:** Entity resolution accuracy metrics, cross-system matching analysis

**Echo Baseline (Week 0):** Score 2 - Limited entity resolution, frequent errors

---

**N-5: Query Understanding**

*Can agents handle multi-table joins, temporal logic, and complex business rules?*

| Score | Criteria |
|-------|----------|
| 6 | Handles complex queries with business rule inference |
| 5 | Multi-table joins, temporal logic, aggregations |
| 4 | Multi-table queries, simple temporal logic |
| 3 | Single-table queries, basic filters |
| 2 | Simple lookups only |
| 1 | Cannot interpret natural language queries |

**Evidence Sources:** Query complexity analysis, success rates by query type

**Echo Baseline (Week 0):** Score 2 - Simple lookups only, no complex query handling

---

**N-6: User Comprehension Feedback**

*Do you systematically capture and learn from cases where users were misunderstood?*

| Score | Criteria |
|-------|----------|
| 6 | Automated learning from misunderstanding patterns |
| 5 | Systematic feedback collection, regular model updates |
| 4 | Feedback captured, periodic review |
| 3 | Ad-hoc feedback collection |
| 2 | Feedback captured but not analyzed |
| 1 | No feedback mechanism |

**Evidence Sources:** Feedback collection system, model update frequency, improvement metrics

**Echo Baseline (Week 0):** Score 2 - Feedback captured but not analyzed

---

### P  - PERMITTED (6 Questions)

Measures infrastructure's ability to enforce dynamic authorization and access control.

---

**P-1: Authorization Model**

*What authorization approach governs agent data access?*

| Score | Criteria |
|-------|----------|
| 6 | Zero-trust ABAC with ML anomaly detection |
| 5 | Comprehensive ABAC (40+ policies), sub-10ms evaluation |
| 4 | ABAC operational with core attributes |
| 3 | RBAC with some attribute-based rules |
| 2 | Static RBAC only, shared service accounts |
| 1 | No authorization or open access |

**Evidence Sources:** Access control architecture, policy engine configuration, provisioning workflow

**Echo Baseline (Week 0):** Score 1 - RBAC only, no contextual ABAC layer

---

**P-2: Human-in-the-Loop (HITL)**

*Do you have workflows for human review of high-risk agent decisions?*

| Score | Criteria |
|-------|----------|
| 6 | ML-powered risk scoring, adaptive escalation |
| 5 | HITL workflows operational, under 15% escalation rate |
| 4 | HITL defined for critical decisions |
| 3 | Manual escalation process exists |
| 2 | Ad-hoc escalation, no formal process |
| 1 | No HITL capability |

**Evidence Sources:** HITL workflow documentation, escalation metrics, queue configuration

**Echo Baseline (Week 0):** Score 1 - No HITL capability

---

**P-3: Audit Logging**

*How completely do you capture who accessed what, when, and why?*

| Score | Criteria |
|-------|----------|
| 6 | Complete audit with ML-powered analysis |
| 5 | 100% coverage, 7+ year retention, trace IDs |
| 4 | Comprehensive logging, partial trace correlation |
| 3 | User identity captured, limited context |
| 2 | Basic database logs only |
| 1 | No audit logging |

**Evidence Sources:** Logging configuration, retention policies, audit query capability

**Echo Baseline (Week 0):** Score 1 - Basic query logs, no reasoning chain capture

---

**P-4: Compliance Coverage**

*How well does your authorization system address regulatory requirements (e.g., GDPR, SOC 2, HIPAA, PCI-DSS, SOX)?*

| Score | Criteria |
|-------|----------|
| 6 | Automated compliance reporting, continuous validation |
| 5 | Full compliance coverage, audit-ready |
| 4 | Major regulations addressed |
| 3 | Partial compliance, gaps documented |
| 2 | Compliance gaps, remediation needed |
| 1 | Non-compliant, deployment blocked |

**Evidence Sources:** Compliance audit results, regulatory documentation, gap analysis

**Echo Baseline (Week 0):** Score 1 - HIPAA gaps, deployment blocked

---

**P-5: Context-Aware Permissions**

*Do permissions adapt based on context (time, location, purpose, customer relationship)?*

| Score | Criteria |
|-------|----------|
| 6 | Full context awareness with predictive access |
| 5 | Rich context attributes (10+) in policy evaluation |
| 4 | Core context attributes (role, time, location) |
| 3 | Limited context (role + department) |
| 2 | Role-only, no context adaptation |
| 1 | Static permissions, no context |

**Evidence Sources:** Policy engine configuration, attribute definitions, context evaluation logs

**Echo Baseline (Week 0):** Score 1 - Static permissions, no context awareness

---

**P-6: Escalation Protocols**

*Are escalation paths clearly defined for permission denials and edge cases?*

| Score | Criteria |
|-------|----------|
| 6 | Automated escalation with SLA tracking |
| 5 | Defined protocols, measured response times |
| 4 | Escalation paths documented |
| 3 | Informal escalation process |
| 2 | Ad-hoc escalation |
| 1 | No escalation process |

**Evidence Sources:** Escalation workflow documentation, SLA metrics, response time analysis

**Echo Baseline (Week 0):** Score 1 - No escalation process

---

### A  - ADAPTIVE (6 Questions)

Measures infrastructure's ability to learn and improve from feedback and changing conditions.

---

**A-1: Feedback Loop Existence**

*Do you have infrastructure to capture user feedback on agent responses?*

| Score | Criteria |
|-------|----------|
| 6 | Multi-channel feedback with sentiment analysis |
| 5 | Systematic feedback capture, integrated with training |
| 4 | Feedback collection operational |
| 3 | Basic feedback mechanism |
| 2 | Feedback captured but not connected |
| 1 | No feedback infrastructure |

**Evidence Sources:** Feedback pipeline, collection mechanisms, integration points

**Echo Baseline (Week 0):** Score 2 - No feedback loops, quarterly reviews only

---

**A-2: Model Retraining Cadence**

*How frequently can you update models based on new data and feedback?*

| Score | Criteria |
|-------|----------|
| 6 | Continuous deployment with A/B testing |
| 5 | Weekly retraining with validation |
| 4 | Monthly retraining cycle |
| 3 | Quarterly updates |
| 2 | Annual or ad-hoc updates |
| 1 | No retraining capability |

**Evidence Sources:** Retraining schedule, MLOps pipeline, update frequency metrics

**Echo Baseline (Week 0):** Score 2 - Quarterly manual reviews only

---

**A-3: Drift Detection**

*Can you detect when model performance degrades due to data or concept drift?*

| Score | Criteria |
|-------|----------|
| 6 | Real-time drift detection with auto-remediation |
| 5 | Automated drift alerts, defined response |
| 4 | Regular drift monitoring |
| 3 | Periodic manual drift checks |
| 2 | Ad-hoc drift assessment |
| 1 | No drift detection |

**Evidence Sources:** Monitoring dashboards, alert configuration, drift detection algorithms

**Echo Baseline (Week 0):** Score 2 - No drift detection, issues discovered through complaints

---

**A-4: Continuous Improvement Process**

*Do you have a defined process for turning feedback into improvements?*

| Score | Criteria |
|-------|----------|
| 6 | Automated improvement pipeline |
| 5 | Weekly improvement cycle with measured outcomes |
| 4 | Regular improvement reviews |
| 3 | Ad-hoc improvement process |
| 2 | Improvements when critical issues arise |
| 1 | No improvement process |

**Evidence Sources:** Improvement workflow documentation, cycle time metrics, outcome tracking

**Echo Baseline (Week 0):** Score 2 - No defined improvement process

---

**A-5: Learning Automation**

*How automated is your feedback-to-improvement pipeline?*

| Score | Criteria |
|-------|----------|
| 6 | Fully automated with human oversight |
| 5 | Largely automated, manual approval gates |
| 4 | Semi-automated, significant manual work |
| 3 | Mostly manual with some automation |
| 2 | Manual process |
| 1 | No automation |

**Evidence Sources:** MLOps infrastructure, automation metrics, pipeline documentation

**Echo Baseline (Week 0):** Score 1 - No ML automation infrastructure

---

**A-6: Performance Trend Tracking**

*Do you track agent performance metrics over time to identify degradation?*

| Score | Criteria |
|-------|----------|
| 6 | Predictive trend analysis with alerting |
| 5 | Comprehensive trend dashboards, anomaly detection |
| 4 | Key metrics tracked over time |
| 3 | Basic trend tracking |
| 2 | Point-in-time metrics only |
| 1 | No performance tracking |

**Evidence Sources:** Performance dashboards, trend analysis tools, alerting configuration

**Echo Baseline (Week 0):** Score 1 - No performance trend tracking

---

### C  - CONTEXTUAL (6 Questions)

Measures infrastructure's ability to synthesize knowledge across systems and domains.

---

**C-1: System Integration Count**

*How many source systems feed your agent-accessible data layer?*

| Score | Criteria |
|-------|----------|
| 6 | 10+ systems with automated discovery |
| 5 | 7-10 systems integrated |
| 4 | 4-6 systems integrated |
| 3 | 2-3 systems integrated |
| 2 | Single system only |
| 1 | No integration |

**Evidence Sources:** Integration inventory, data flow diagrams, API catalog

**Echo Baseline (Week 0):** Score 3 - Siloed systems, no cross-domain synthesis

---

**C-2: Cross-System Data Freshness**

*How current is data from your integrated systems?*

| Score | Criteria |
|-------|----------|
| 6 | Sub-15-second freshness across all systems |
| 5 | Sub-30-second freshness for primary systems |
| 4 | Hourly freshness across systems |
| 3 | Daily freshness |
| 2 | Multi-day lag for some systems |
| 1 | Weekly or longer lag |

**Evidence Sources:** CDC lag dashboards, cross-system freshness analysis

**Echo Baseline (Week 0):** Score 2 - Weekly batch jobs between systems

---

**C-3: Entity Resolution Cross-Domain**

*Can you resolve the same entity (customer, employee, account) across different systems?*

| Score | Criteria |
|-------|----------|
| 6 | Universal entity resolution with confidence scoring |
| 5 | Robust cross-system entity resolution |
| 4 | Entity resolution for primary entities |
| 3 | Basic cross-system matching |
| 2 | Limited cross-system resolution |
| 1 | No cross-system entity resolution |

**Evidence Sources:** Entity resolution accuracy metrics, cross-system matching analysis

**Echo Baseline (Week 0):** Score 2 - Limited cross-system resolution

---

**C-4: Context Synthesis Capability**

*Can agents combine information from multiple systems to answer questions?*

| Score | Criteria |
|-------|----------|
| 6 | Intelligent context assembly with relevance ranking |
| 5 | Multi-system queries with unified response |
| 4 | Cross-system queries with some limitations |
| 3 | Basic cross-system queries |
| 2 | Single-system queries only |
| 1 | Cannot synthesize context |

**Evidence Sources:** Query capabilities, federation layer, cross-system testing

**Echo Baseline (Week 0):** Score 3 - Basic cross-system queries

---

**C-5: Cross-System Querying**

*Can a single agent query span multiple source systems transparently?*

| Score | Criteria |
|-------|----------|
| 6 | Transparent multi-system queries with optimization |
| 5 | Multi-system queries with sub-3-second response |
| 4 | Multi-system queries, some performance impact |
| 3 | Limited cross-system capability |
| 2 | Manual system selection required |
| 1 | Single-system queries only |

**Evidence Sources:** Query capabilities, federation layer, cross-system testing

**Echo Baseline (Week 0):** Score 3 - Limited cross-system capability

---

**C-6: Universal Context Availability**

*What percentage of business questions can be answered with available integrated data?*

| Score | Criteria |
|-------|----------|
| 6 | Over 95% question coverage |
| 5 | 80-95% question coverage |
| 4 | 60-80% question coverage |
| 3 | 40-60% question coverage |
| 2 | 20-40% question coverage |
| 1 | Under 20% question coverage |

**Evidence Sources:** Question coverage analysis, data availability assessment

**Echo Baseline (Week 0):** Score 3 - 40-60% question coverage

---

### T  - TRANSPARENT (6 Questions)

Measures infrastructure's ability to explain decisions and provide audit trails.

---

**T-1: Audit Trail Completeness**

*How completely do you capture the reasoning chain from question to answer?*

| Score | Criteria |
|-------|----------|
| 6 | Complete trails with ML-powered analysis |
| 5 | 100% coverage, end-to-end trace IDs, 7+ year retention |
| 4 | Comprehensive trails, partial correlation |
| 3 | Basic audit trails, user identity captured |
| 2 | Database query logs only |
| 1 | No audit trails |

**Evidence Sources:** Audit log configuration, trace infrastructure, retention policies

**Echo Baseline (Week 0):** Score 1 - No audit trails

---

**T-2: Explainability Capability**

*Can agents explain their reasoning in terms users understand?*

| Score | Criteria |
|-------|----------|
| 6 | Natural language explanations with confidence levels |
| 5 | Structured explanations with reasoning steps |
| 4 | Basic explainability, data sources shown |
| 3 | Limited explainability |
| 2 | Technical explanations only |
| 1 | No explainability |

**Evidence Sources:** Explainability features, user testing, explanation samples

**Echo Baseline (Week 0):** Score 1 - No explainability

---

**T-3: Citation Provision**

*Do agent responses include citations to source data?*

| Score | Criteria |
|-------|----------|
| 6 | Inline citations with confidence and freshness |
| 5 | Citations for all claims with source links |
| 4 | Citations for key claims |
| 3 | Occasional citations |
| 2 | Source system mentioned, no specifics |
| 1 | No citations |

**Evidence Sources:** Response samples, citation configuration, link verification

**Echo Baseline (Week 0):** Score 1 - No citations

---

**T-4: Decision Traceability**

*Can you trace any agent decision back to the data and logic that produced it?*

| Score | Criteria |
|-------|----------|
| 6 | Full traceability with replay capability |
| 5 | Complete traceability, query replay |
| 4 | Traceability for most decisions |
| 3 | Limited traceability |
| 2 | Partial traceability |
| 1 | No traceability |

**Evidence Sources:** Tracing infrastructure, trace examples, coverage metrics

**Echo Baseline (Week 0):** Score 1 - No traceability

---

**T-5: Compliance Reporting**

*Can you generate compliance reports showing appropriate data access?*

| Score | Criteria |
|-------|----------|
| 6 | Automated compliance reporting with alerts |
| 5 | On-demand compliance reports, audit-ready |
| 4 | Compliance reports with manual effort |
| 3 | Basic compliance data available |
| 2 | Limited compliance visibility |
| 1 | No compliance reporting |

**Evidence Sources:** Report samples, compliance dashboards, audit history

**Echo Baseline (Week 0):** Score 2 - Limited compliance visibility

---

**T-6: User Trust in Transparency**

*Do users report understanding and trusting agent explanations?*

| Score | Criteria |
|-------|----------|
| 6 | Over 90% user trust in explanations |
| 5 | 75-90% user trust |
| 4 | 60-75% user trust |
| 3 | 40-60% user trust |
| 2 | Under 40% user trust |
| 1 | No user trust measurement |

**Evidence Sources:** User surveys, trust metrics, feedback analysis

**Echo Baseline (Week 0):** Score 1 - No user trust measurement

---

## Calculating Your Score

### Step 1: Calculate Dimension Scores (1-6 each)

For each dimension, average the 6 question scores:

**I:** (___ + ___ + ___ + ___ + ___ + ___) ÷ 6 = ___
**N:** (___ + ___ + ___ + ___ + ___ + ___) ÷ 6 = ___
**P:** (___ + ___ + ___ + ___ + ___ + ___) ÷ 6 = ___
**A:** (___ + ___ + ___ + ___ + ___ + ___) ÷ 6 = ___
**C:** (___ + ___ + ___ + ___ + ___ + ___) ÷ 6 = ___
**T:** (___ + ___ + ___ + ___ + ___ + ___) ÷ 6 = ___

### Step 2: Calculate Total INPACT™ Score (6-36)

**Total INPACT™ Score:** Sum of 6 dimension scores = ___/36

### Step 3: Convert to Percentage

**INPACT™ Percentage = (Total Score ÷ 36) × 100**

Example: Echo Week 0 = (10 ÷ 36) × 100 = 28%

### Step 4: Identify Trust Band

| Score | Percentage | Trust Band |
|-------|------------|------------|
| 31-36 | 86-100% | 🟢 High Trust |
| 24-30 | 67-85% | 🟡 Good Trust |
| 18-23 | 50-66% | 🟠 Moderate Trust |
| 12-17 | 33-49% | 🔴 Low Trust |
| 6-11 | <33% | ⚫ Very Low Trust |

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
