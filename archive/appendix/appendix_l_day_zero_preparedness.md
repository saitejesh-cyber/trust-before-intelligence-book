# Appendix L: Day Zero Preparedness Checklist

**Book:** Trust Before Intelligence: Why 95% of Agent Projects Fail—and the Architecture Blueprint That Fixes Infrastructure in 90 Days  
**Author:** Ram Katamaraja, CEO, Colaberry Inc.  
**Appendix:** H of H  
**Version:** 1.0  
**Date:** December 2025  
**Target:** 8-10 pages | Pre-transformation readiness criteria

---

## Purpose

This appendix provides a comprehensive Day Zero checklist ensuring your organization is ready to begin the 90-day transformation. Completing these prerequisites prevents common delays and failures that occur when teams start building without proper foundation.

**67% of agent deployments fail in Week 1—not because of bad AI, but because of missing Day Zero preparation.**

**How to Use This Checklist:**

1. **Assess:** Complete all 50 items before Week 1 begins
2. **Resolve:** Address any "Not Ready" items as blockers
3. **Document:** Record evidence for each "Ready" item
4. **Align:** Ensure all stakeholders confirm readiness
5. **Commit:** Obtain formal approval to proceed

**Integration Points:**
- **Chapter 10:** Week 1 activities assume Day Zero complete
- **90-Day Tracker Tab 9:** Day Zero checklist tracking

---

## Checklist Overview

The Day Zero checklist spans five readiness domains:

| Domain | Items | Purpose |
|--------|-------|---------|
| **Stakeholder Alignment** | 10 | Ensure organizational commitment |
| **Technical Prerequisites** | 12 | Verify infrastructure access and capabilities |
| **Data Readiness** | 10 | Confirm data availability and quality |
| **Security & Compliance** | 10 | Validate regulatory and security posture |
| **Resource Commitment** | 8 | Secure budget, team, and timeline |

**Scoring:**
- **Ready (✅):** Complete with evidence
- **In Progress (🟡):** Underway, will complete before Week 1
- **Not Ready (❌):** Blocker requiring resolution
- **N/A:** Not applicable to your context

---

## Domain 1: Stakeholder Alignment

Organizational readiness determines transformation success more than technical capability. These items ensure leadership commitment and cross-functional alignment.

---

### SA-01: Executive Sponsor Identified

**Requirement:** Named executive sponsor with authority to allocate resources and resolve escalations.

**Evidence Required:**
- [ ] Executive sponsor name and title documented
- [ ] Sponsor has attended kickoff briefing
- [ ] Sponsor authority confirmed (budget, hiring, vendor)
- [ ] Weekly check-in scheduled with sponsor

**Echo Example:** Sarah Chen (CTO) served as executive sponsor with direct access to CEO and board.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-02: Business Case Approved

**Requirement:** Documented business case with expected ROI and success metrics approved by leadership.

**Evidence Required:**
- [ ] Business case document complete
- [ ] ROI projections reviewed and accepted
- [ ] Success metrics defined and measurable
- [ ] Approval signature obtained

**Echo Example:** Business case projected 477% three-year ROI, approved by CFO and board finance committee.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-03: Steering Committee Established

**Requirement:** Cross-functional steering committee with representatives from IT, business, security, and operations.

**Evidence Required:**
- [ ] Committee membership defined
- [ ] Meeting cadence established (weekly recommended)
- [ ] Decision-making authority documented
- [ ] First meeting scheduled

**Echo Example:** Steering committee included CTO, CDO, CISO, CMO, and CFO with bi-weekly meetings.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-04: Success Criteria Agreed

**Requirement:** Quantifiable success criteria aligned across all stakeholders.

**Evidence Required:**
- [ ] INPACT™ target score defined (recommend: 86/100)
- [ ] Timeline agreed (90 days or custom)
- [ ] Agent use cases prioritized (recommend: 2-3 initial)
- [ ] Go/No-Go criteria documented for each phase

**Echo Example:** Success = 86/100 INPACT™, 3 agents in production, 4.0/5 user satisfaction.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-05: Communication Plan Documented

**Requirement:** Stakeholder communication plan with defined audiences, cadence, and content.

**Evidence Required:**
- [ ] Stakeholder map complete (who needs to know what)
- [ ] Communication cadence defined (daily, weekly, monthly)
- [ ] Escalation path documented
- [ ] Communication owners assigned

**Echo Example:** Daily standup (team), weekly update (stakeholders), bi-weekly dashboard (executives), monthly board brief.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-06: Change Management Plan

**Requirement:** Plan for managing organizational change, including training and adoption support.

**Evidence Required:**
- [ ] Impact assessment complete (who is affected)
- [ ] Training plan drafted
- [ ] Resistance management approach defined
- [ ] Champions identified in each department

**Echo Example:** 50 pilot users identified, training curriculum developed, clinical champion in each unit.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-07: Risk Tolerance Defined

**Requirement:** Explicit agreement on acceptable risk levels and mitigation expectations.

**Evidence Required:**
- [ ] Risk categories identified (technical, security, timeline, budget)
- [ ] Tolerance thresholds defined per category
- [ ] Mitigation requirements documented
- [ ] Risk owner assigned

**Echo Example:** Zero tolerance for patient safety risks; 15% budget variance acceptable; 2-week timeline slip acceptable.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-08: Legal Review Complete

**Requirement:** Legal review of AI deployment, including liability, intellectual property, and vendor agreements.

**Evidence Required:**
- [ ] AI liability framework reviewed
- [ ] Vendor contracts reviewed for AI-specific terms
- [ ] IP ownership clarified (models, data, outputs)
- [ ] Terms of service updated for AI features

**Echo Example:** Legal approved AI use in clinical decision support with HITL requirement for prescribing.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-09: Union/Employee Notification

**Requirement:** Appropriate notification to employees and unions (if applicable) regarding AI deployment.

**Evidence Required:**
- [ ] Employee communication plan approved
- [ ] Union consultation complete (if applicable)
- [ ] Job impact assessment documented
- [ ] Reskilling commitments documented (if applicable)

**Echo Example:** Town hall held with nursing staff; no union; commitment that AI augments, not replaces, staff.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SA-10: Board Awareness

**Requirement:** Board of directors briefed on AI initiative, risks, and governance.

**Evidence Required:**
- [ ] Board briefing scheduled or complete
- [ ] Board questions addressed
- [ ] Ongoing reporting cadence established
- [ ] Board approval for investment (if required)

**Echo Example:** Board briefed Week 0; quarterly reporting established; final presentation Week 12.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

## Domain 2: Technical Prerequisites

Technical infrastructure must be accessible and capable of supporting the transformation. These items prevent the most common technical delays.

---

### TP-01: Source System Access

**Requirement:** Confirmed access to all source systems that will feed agent infrastructure.

**Evidence Required:**
- [ ] Source systems inventoried
- [ ] Admin access confirmed for each system
- [ ] API availability verified (or CDC access)
- [ ] Rate limits documented

**Echo Example:** Epic (admin), Salesforce (API), Billing (database), Document Management (API) access confirmed.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-02: Cloud Environment Provisioned

**Requirement:** Cloud environment ready for transformation workloads with appropriate capacity.

**Evidence Required:**
- [ ] Cloud account active (AWS/Azure/GCP)
- [ ] Initial capacity provisioned (Phase 1 requirements)
- [ ] Network configuration complete
- [ ] Cost monitoring enabled

**Echo Example:** Azure environment provisioned with $50K initial capacity, ExpressRoute to data center.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-03: Development Environment Ready

**Requirement:** Development environment configured for team productivity.

**Evidence Required:**
- [ ] Dev/staging environments separate from production
- [ ] CI/CD pipeline configured
- [ ] Code repository established
- [ ] Development workstations configured

**Echo Example:** GitHub Enterprise, Azure DevOps pipelines, dev/staging/prod environments isolated.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-04: Monitoring Infrastructure

**Requirement:** Observability tools deployed and configured for baseline measurement.

**Evidence Required:**
- [ ] APM tool deployed (Datadog, New Relic, etc.)
- [ ] Log aggregation configured
- [ ] Alert channels established
- [ ] Baseline metrics being captured

**Echo Example:** Datadog deployed Week 0, capturing baseline metrics before any changes.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-05: Database Performance Baseline

**Requirement:** Current database performance documented as transformation baseline.

**Evidence Required:**
- [ ] Query performance metrics captured (P50, P95, P99)
- [ ] Database resource utilization documented
- [ ] Slow query analysis complete
- [ ] Index health assessed

**Echo Example:** SQL Server: 47s average query, 2min P95; Oracle: 12s average, 45s P95.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-06: Network Architecture Documented

**Requirement:** Current network architecture documented with capacity and latency baselines.

**Evidence Required:**
- [ ] Network topology documented
- [ ] Latency between key components measured
- [ ] Bandwidth utilization documented
- [ ] Firewall rules understood

**Echo Example:** 15ms latency data center to cloud; 100Mbps ExpressRoute 40% utilized.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-07: Authentication Integration

**Requirement:** Enterprise authentication (SSO, identity provider) accessible for integration.

**Evidence Required:**
- [ ] Identity provider documented (Okta, Azure AD, etc.)
- [ ] Service account process understood
- [ ] SAML/OIDC integration capabilities confirmed
- [ ] MFA requirements documented

**Echo Example:** Azure AD with SAML; service account provisioning via ServiceNow; MFA required for admin.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-08: API Gateway Available

**Requirement:** API gateway available or planned for agent traffic management.

**Evidence Required:**
- [ ] API gateway deployed or in roadmap
- [ ] Rate limiting capabilities confirmed
- [ ] Authentication integration planned
- [ ] Monitoring integration confirmed

**Echo Example:** Azure API Management deployed; Kong considered as alternative.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-09: Container/Orchestration Platform

**Requirement:** Container platform available for deploying agent workloads.

**Evidence Required:**
- [ ] Kubernetes or alternative deployed
- [ ] Container registry available
- [ ] Deployment automation configured
- [ ] Scaling policies defined

**Echo Example:** Azure Kubernetes Service (AKS) with autoscaling; Azure Container Registry.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-10: LLM Provider Access

**Requirement:** Access to LLM providers (OpenAI, Anthropic, etc.) with appropriate agreements.

**Evidence Required:**
- [ ] LLM provider accounts active
- [ ] Enterprise agreements in place (not consumer tier)
- [ ] Rate limits understood
- [ ] Data processing agreements signed

**Echo Example:** OpenAI Enterprise with Azure private endpoint; Anthropic as backup.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-11: Vector Database Selected

**Requirement:** Vector database selected and accessible for RAG implementation.

**Evidence Required:**
- [ ] Vector database selected (Pinecone, Weaviate, pgvector, etc.)
- [ ] Account/deployment ready
- [ ] Capacity requirements estimated
- [ ] Backup strategy defined

**Echo Example:** Pinecone Enterprise with 10M vector capacity; Azure Cognitive Search as alternative.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### TP-12: Backup Vendor Options

**Requirement:** Backup vendors identified for critical components to avoid single-vendor lock-in.

**Evidence Required:**
- [ ] LLM backup provider identified
- [ ] Vector database alternative identified
- [ ] Cloud provider alternative considered
- [ ] Migration path documented (if needed)

**Echo Example:** Anthropic Claude backup for OpenAI; pgvector backup for Pinecone.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

## Domain 3: Data Readiness

Data is the foundation of agent intelligence. These items ensure data is available, understood, and usable.

---

### DR-01: Data Inventory Complete

**Requirement:** Comprehensive inventory of data assets relevant to agent use cases.

**Evidence Required:**
- [ ] Data catalog exists or created
- [ ] Key tables/entities documented
- [ ] Data ownership identified
- [ ] Update frequency documented

**Echo Example:** 340 tables across 5 systems cataloged; 89 priority tables for agent access.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-02: Data Quality Assessment

**Requirement:** Data quality assessment complete for priority data assets.

**Evidence Required:**
- [ ] Completeness measured (% null values)
- [ ] Accuracy assessed (sample validation)
- [ ] Consistency evaluated (cross-system matching)
- [ ] Timeliness documented (freshness)

**Echo Example:** Priority tables averaged 94% completeness, 97% accuracy, 89% consistency.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-03: Schema Documentation

**Requirement:** Database schemas documented and understood by implementation team.

**Evidence Required:**
- [ ] ERD diagrams available
- [ ] Column descriptions documented
- [ ] Relationships mapped
- [ ] Business context documented

**Echo Example:** Epic schema documented via vendor materials; Salesforce self-documenting; billing schema reverse-engineered.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-04: Business Glossary Draft

**Requirement:** Initial business glossary with domain terminology for semantic layer.

**Evidence Required:**
- [ ] 100+ terms defined (minimum starting point)
- [ ] Synonyms captured
- [ ] SME review scheduled
- [ ] Update process defined

**Echo Example:** 200-term draft glossary from clinical informatics team; expanded to 847 by Week 6.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-05: Sample Data Available

**Requirement:** Representative sample data available for development and testing.

**Evidence Required:**
- [ ] Sample datasets extracted
- [ ] PHI/PII de-identified (if applicable)
- [ ] Sample covers key use cases
- [ ] Refresh process defined

**Echo Example:** 10,000-patient de-identified sample for development; monthly refresh from production.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-06: Document Corpus Identified

**Requirement:** Unstructured documents for RAG identified and accessible.

**Evidence Required:**
- [ ] Document types inventoried
- [ ] Storage locations documented
- [ ] Access method confirmed
- [ ] Volume estimated

**Echo Example:** Clinical protocols (500), policies (200), guidelines (150) in SharePoint and document management system.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-07: Historical Data Available

**Requirement:** Historical data available for trend analysis and context.

**Evidence Required:**
- [ ] History retention policy documented
- [ ] 2+ years history available (recommended)
- [ ] Archive access method confirmed
- [ ] Performance acceptable for historical queries

**Echo Example:** 3 years EHR history online; 7 years in archive with 24-hour retrieval.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-08: CDC Feasibility Confirmed

**Requirement:** Change Data Capture feasibility confirmed for real-time requirements.

**Evidence Required:**
- [ ] CDC support confirmed for source databases
- [ ] Debezium/alternative compatibility verified
- [ ] Transaction log access available
- [ ] Performance impact assessed

**Echo Example:** SQL Server CDC native; Epic via HL7 FHIR feeds; Salesforce via streaming API.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-09: Data Lineage Mapped

**Requirement:** Data lineage documented for priority data flows.

**Evidence Required:**
- [ ] Source-to-target mappings documented
- [ ] Transformation logic documented
- [ ] Key derivations understood
- [ ] Impact analysis capability exists

**Echo Example:** dbt lineage graphs for analytics; manual documentation for legacy ETL.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### DR-10: Master Data Status Known

**Requirement:** Master data management status documented for key entities.

**Evidence Required:**
- [ ] Master entities identified (customer, patient, product, etc.)
- [ ] Golden record source identified (or gap documented)
- [ ] Duplicate rate estimated
- [ ] Resolution approach defined

**Echo Example:** Patient MDM via MPI with 98% auto-resolution; provider MDM needed.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

## Domain 4: Security & Compliance

Agent deployment in regulated environments requires security and compliance preparation.

---

### SC-01: Regulatory Requirements Documented

**Requirement:** All applicable regulations documented with compliance requirements.

**Evidence Required:**
- [ ] Regulations inventoried (HIPAA, GDPR, SOX, etc.)
- [ ] Specific requirements for AI documented
- [ ] Compliance officer engaged
- [ ] Audit schedule understood

**Echo Example:** HIPAA (primary), HITECH, state privacy laws, FDA guidance for clinical decision support.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-02: Data Classification Complete

**Requirement:** Data classification scheme defined and applied to priority assets.

**Evidence Required:**
- [ ] Classification taxonomy defined
- [ ] Priority data classified
- [ ] Classification labels implemented
- [ ] Classification policy approved

**Echo Example:** PHI, PII, Confidential, Internal, Public taxonomy; 89 priority tables classified.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-03: Security Architecture Review

**Requirement:** Security architecture reviewed for agent deployment requirements.

**Evidence Required:**
- [ ] Security architecture documented
- [ ] Agent-specific risks identified
- [ ] Control gaps documented
- [ ] Remediation plan drafted

**Echo Example:** Security review identified ABAC gap, API authentication gap, audit trail gap.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-04: Privacy Impact Assessment

**Requirement:** Privacy impact assessment complete for AI data processing.

**Evidence Required:**
- [ ] PIA template completed
- [ ] Data flows analyzed for privacy
- [ ] Privacy risks documented
- [ ] Mitigation measures identified

**Echo Example:** PIA identified patient data aggregation risk; mitigation: minimum necessary access pattern.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-05: Vendor Security Assessment

**Requirement:** Security assessments complete for all new AI vendors.

**Evidence Required:**
- [ ] Vendor security questionnaires complete
- [ ] SOC 2 / ISO 27001 certifications verified
- [ ] Data processing agreements signed
- [ ] Subprocessor list obtained

**Echo Example:** OpenAI SOC 2 Type II verified; Azure BAA in place; Pinecone security questionnaire complete.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-06: Access Control Foundation

**Requirement:** Existing access control system documented and integration path defined.

**Evidence Required:**
- [ ] Current access control model documented
- [ ] Role definitions extracted
- [ ] Integration points identified
- [ ] ABAC roadmap defined

**Echo Example:** Current RBAC with 47 roles; integration via Azure AD; OPA deployment planned Phase 3.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-07: Audit Logging Requirements

**Requirement:** Audit logging requirements defined for compliance.

**Evidence Required:**
- [ ] Logging requirements documented per regulation
- [ ] Retention periods defined
- [ ] Log format standardized
- [ ] Storage solution identified

**Echo Example:** HIPAA requires 7-year audit retention; log format per OWASP standards; Azure Log Analytics storage.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-08: Incident Response Updated

**Requirement:** Incident response plan updated for AI-specific scenarios.

**Evidence Required:**
- [ ] AI incident types defined (hallucination, bias, breach)
- [ ] Response procedures documented
- [ ] Communication templates prepared
- [ ] Tabletop exercise scheduled

**Echo Example:** "Agent Error" runbook created; regulatory notification procedures added; Q2 tabletop planned.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-09: Third-Party Risk Assessment

**Requirement:** Third-party risk assessment complete for AI supply chain.

**Evidence Required:**
- [ ] AI supply chain mapped (models, hosting, data)
- [ ] Concentration risks identified
- [ ] Alternative providers documented
- [ ] Contractual protections verified

**Echo Example:** OpenAI concentration risk mitigated by Anthropic backup; model portability assessed.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### SC-10: HITL Authority Defined

**Requirement:** Human-in-the-Loop authority and escalation defined for high-risk decisions.

**Evidence Required:**
- [ ] Decision categories requiring HITL identified
- [ ] Escalation authority defined
- [ ] Response time SLAs defined
- [ ] Training plan for reviewers

**Echo Example:** Clinical recommendations require physician review; 30-second SLA; 12 reviewer pool trained.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

## Domain 5: Resource Commitment

Transformation requires committed resources. These items prevent the mid-project resource shortfalls that derail implementations.

---

### RC-01: Budget Approved

**Requirement:** Full transformation budget approved and allocated.

**Evidence Required:**
- [ ] Phase 1-4 budget approved ($1.2M+ typical)
- [ ] Ongoing operations budget approved ($50K/month typical)
- [ ] Contingency reserve defined (15-20% recommended)
- [ ] Finance signoff obtained

**Echo Example:** $1.23M implementation approved; $52K/month operations; 15% contingency.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-02: Core Team Identified

**Requirement:** Core implementation team identified with confirmed availability.

**Evidence Required:**
- [ ] Team roster complete
- [ ] Manager approvals for allocation
- [ ] Backfill plan for vacated responsibilities
- [ ] Start dates confirmed

**Echo Example:** 2 data engineers, 1 architect, 1 ML engineer committed full-time Week 1.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-03: Consulting Support Contracted

**Requirement:** External consulting support contracted where internal skills gap exists.

**Evidence Required:**
- [ ] Skill gap analysis complete
- [ ] Consulting contracts signed
- [ ] SOWs with deliverables defined
- [ ] Start dates confirmed

**Echo Example:** Databricks consulting (40hr), CDC implementation (80hr), security review (40hr) contracted.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-04: SME Availability Confirmed

**Requirement:** Subject matter expert availability confirmed for semantic layer and testing.

**Evidence Required:**
- [ ] SMEs identified by domain
- [ ] Availability commitment (hrs/week)
- [ ] Manager approval obtained
- [ ] Engagement schedule defined

**Echo Example:** Clinical informaticist 10hr/week; billing SME 5hr/week; ops SME 5hr/week.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-05: Training Plan Funded

**Requirement:** Training budget allocated for team skill development.

**Evidence Required:**
- [ ] Training needs assessment complete
- [ ] Training budget allocated
- [ ] Vendor certifications planned
- [ ] Training schedule drafted

**Echo Example:** $15K training budget: Databricks certification (2), LLM workshop (team), security training (2).

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-06: Timeline Commitments

**Requirement:** 12-week timeline committed with key milestone dates.

**Evidence Required:**
- [ ] Week 1 start date confirmed
- [ ] Phase gate dates scheduled
- [ ] Final production date targeted
- [ ] Key stakeholder calendars blocked

**Echo Example:** Sept 2 start; Phase 1 gate Oct 2; Phase 2 gate Oct 23; Production Nov 13.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-07: Escalation Path Tested

**Requirement:** Escalation path tested and confirmed working.

**Evidence Required:**
- [ ] Escalation contacts documented
- [ ] Response time expectations set
- [ ] Test escalation executed
- [ ] On-call rotation defined (if 24/7 needed)

**Echo Example:** CTO reachable <2hr business hours; on-call rotation for critical issues.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

### RC-08: War Room Established

**Requirement:** Physical or virtual war room available for team collaboration.

**Evidence Required:**
- [ ] Space or virtual room allocated
- [ ] Equipment available (whiteboards, screens)
- [ ] Collaboration tools configured
- [ ] Standing meeting schedule set

**Echo Example:** Conference room C-204 dedicated; Teams channel for async; daily standup 9 AM.

**Status:** ☐ Ready ☐ In Progress ☐ Not Ready ☐ N/A

---

## Day Zero Summary Scorecard

### Domain Scores

| Domain | Items | Ready | In Progress | Not Ready | N/A |
|--------|-------|-------|-------------|-----------|-----|
| Stakeholder Alignment | 10 | | | | |
| Technical Prerequisites | 12 | | | | |
| Data Readiness | 10 | | | | |
| Security & Compliance | 10 | | | | |
| Resource Commitment | 8 | | | | |
| **TOTAL** | **50** | | | | |

### Readiness Decision

**Proceed if:**
- Zero "Not Ready" items, OR
- "Not Ready" items have confirmed resolution before Week 1

**Delay if:**
- Any "Not Ready" in Stakeholder Alignment (organizational risk)
- Any "Not Ready" in Security & Compliance (regulatory risk)
- >3 "Not Ready" items without resolution path

**Escalate if:**
- Budget not approved (RC-01)
- Executive sponsor missing (SA-01)
- Regulatory blockers identified (SC-01 through SC-05)

---

## Integration with 90-Day Tracker

The 90-Day Tracker (Tab 9) provides:

- **Pre-kickoff tracking** of all 50 items
- **Dependency mapping** between items
- **Resolution workflow** for "Not Ready" items
- **Approval workflow** for Day Zero signoff

---

**Pedagogical Disclaimer:** Echo Health Systems is a fictional teaching case. Checklist items reflect real preparation requirements observed across multiple enterprise deployments.

---

© 2025 Colaberry Inc. All Rights Reserved.

INPACT™ and GOALS™ are trademarks of Colaberry Inc.

---

**END OF APPENDIX H**
