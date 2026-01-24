# Chapter 11: Choosing the Right Tools for Your Stack

**The Technology Selection Chapter — Your Methodology Guide**

---

<!-- CHAPTER OPENING GRAPHIC -->

```mermaid

 graph LR
    subgraph BEFORE["VENDOR HYPE"]
        direction TB
        B1["Feature-driven choices<br/><br/>Integration afterthought<br/><br/>Mismatched capabilities<br/><br/><b>Compliance gaps</b>"]
    end
    
    subgraph TRANSFORM["THREE-PILLAR TEST"]
        direction TB
        T1["INPACT™ + 7-Layer<br/>+ GOALS™"]
    end
    
    subgraph AFTER["VALIDATED STACK"]
        direction TB
        A1["Need-driven selection<br/><br/>Layer-by-layer fit<br/><br/>Unified architecture<br/><br/><b>Built-in compliance</b>"]
    end
    
    BEFORE --> TRANSFORM --> AFTER
    
    style BEFORE fill:#ffebee,stroke:#c62828,stroke-width:2px,color:#b71c1c
    style TRANSFORM fill:#f5f5f5,stroke:#666666,stroke-width:2px,color:#333333
    style AFTER fill:#e0f2f1,stroke:#00897b,stroke-width:2px,color:#004d40
    style B1 fill:#ffcdd2,stroke:#c62828,color:#b71c1c
    style T1 fill:#f5f5f5,stroke:#666666,color:#333333
    style A1 fill:#b2dfdb,stroke:#00897b,color:#004d40

```

> **Key Takeaway:** Every vendor must pass the three-pillar test. No exceptions.

<!-- END CHAPTER OPENING GRAPHIC -->

---

*Technology selection methodology determines success or failure. This chapter provides the criteria, frameworks, and processes to evaluate any vendor against the Architecture of Trust. Your roadmap (Chapter 10) shows when to build. This chapter shows how to decide what to build with.*

> **📚 Online Tools:** For interactive vendor evaluation scorecards, assessment templates, and current vendor comparisons, visit **trustbeforeintelligence.com/tools** — updated quarterly.

---

## Part 1: Selection Framework

### 1.1 Your Assessment Drives Your Stack

Your INPACT™ score from Chapter 9 determines your technology priorities. The mapping is direct:

| Low Score | Priority Layers | Selection Focus |
|-----------|-----------------|-----------------|
| **I (Instant)** | L1, L2 | Sub-100ms queries, <30s CDC latency |
| **N (Natural)** | L3, L4 | Semantic glossaries, embedding quality |
| **P (Permitted)** | L5 | ABAC engines, HITL workflows, audit platforms |
| **T (Transparent)** | L6 | LLM tracing, citation tracking, explainability |
| **A or C** | L2, L4, L7 | Feedback loops, cross-system integration |

*For complete INPACT™-to-Layer mapping, see Chapter 9, Part 1.3.*

**Three Selection Principles**

Every vendor evaluation follows three principles:

1. **INPACT™-First**: Does the technology help agents meet the six fundamental needs?
2. **GOALS™-Ready**: Can your team operate this technology with excellence?
3. **Layer-Aligned**: Does it fit the 7-Layer Architecture without gaps or overlaps?

**Chapter Structure**

- **Part 1:** Selection framework—three-pillar vendor test, build vs buy, budget tiers
- **Part 2:** Layer-by-layer selection criteria—what to evaluate, not whom to select
- **Part 3:** Evaluation process—RFP templates, POC approach, contract negotiation
- **Part 4:** Applying the methodology—Echo's selection process as example

---

### 1.2 The Three-Pillar Vendor Test

Every technology in a production stack must pass the same evaluation. Three pillars, separately scored, identify vendors that meet both agent needs and operational requirements.

**Diagram: The Three-Pillar Vendor Evaluation Framework**

```mermaid
graph TD
    subgraph VENDOR["VENDOR EVALUATION"]
        V["<b>Technology<br/>Candidate</b>"]
    end
    
    subgraph PILLAR1["PILLAR 1: INPACT™"]
        P1["<b>Agent Needs</b><br/><b>6 Dimensions</b><br/><b>Score: X/36</b>"]
    end
    
    subgraph PILLAR2["PILLAR 2: ARCHITECTURE"]
        P2["<b>Layer Fit</b><br/><b>7-Layer Integration</b><br/><b>Score: X/6</b>"]
    end
    
    subgraph PILLAR3["PILLAR 3: GOALS™"]
        P3["<b>Operations</b><br/><b>5 Dimensions</b><br/><b>Score: X/25</b>"]
    end
    
    V --> P1
    V --> P2
    V --> P3
    
    P1 --> EVAL["<b>Evaluate Separately</b><br/><b>INPACT™ ≥24/36</b><br/><b>GOALS™ ≥18/25</b>"]
    P2 --> EVAL
    P3 --> EVAL
    
    Copyright["<b>© 2025 Colaberry Inc.</b>"]
    
    style VENDOR fill:#f5f5f5,stroke:#666666,stroke-width:2px,color:#333333
    style PILLAR1 fill:#e0f2f1,stroke:#00897b,stroke-width:2px,color:#004d40
    style PILLAR2 fill:#e3f2fd,stroke:#1976d2,stroke-width:2px,color:#0d47a1
    style PILLAR3 fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#e65100
    style V fill:#eeeeee,stroke:#666666,color:#333333
    style P1 fill:#b2dfdb,stroke:#00897b,color:#004d40
    style P2 fill:#bbdefb,stroke:#1976d2,color:#0d47a1
    style P3 fill:#ffe0b2,stroke:#f57c00,color:#e65100
    style EVAL fill:#c8e6c9,stroke:#388e3c,stroke-width:2px,color:#1b5e20
    style Copyright fill:#ffffff,stroke:none,color:#666666
```

**Pillar 1: INPACT™ Agent Needs (Score Separately)**

The first pillar asks: does this technology help agents meet the six fundamental needs? Each INPACT™ dimension translates into specific vendor evaluation questions:

| INPACT™ Need | Vendor Evaluation Question | What to Look For |
|--------------|---------------------------|------------------|
| **I (Instant)** | Does it support <100ms queries? Real-time data access? | Sub-50ms response times, efficient caching, streaming support |
| **N (Natural)** | Does it support NLU, semantic capabilities? | Vector embeddings, semantic search, terminology mapping |
| **P (Permitted)** | Does it support ABAC, HITL, audit trails? | Role-based + attribute-based access, human escalation, logging |
| **A (Adaptive)** | Does it enable feedback loops, continuous learning? | Model versioning, A/B testing, feedback integration |
| **C (Contextual)** | Does it integrate with multiple sources? | API breadth, connector ecosystem, data federation |
| **T (Transparent)** | Does it provide explainability, citations, compliance? | Audit trails, decision traces, regulatory support |

Score each relevant dimension 1-6. Not every dimension applies to every vendor category—a vector database primarily addresses I (speed) and N (semantic), while a policy engine focuses on P (permitted) and T (transparent). Score only the dimensions relevant to that technology's purpose. *(For complete scoring rubrics, see Appendix DA-5.)*

**INPACT™ Vendor Score**: Sum of relevant dimensions (maximum 36 if all apply)

**Pillar 2: Architecture Fit (Score: 1-6)**

The second pillar ensures the technology integrates cleanly into the 7-Layer Architecture:

- **Layer Alignment**: Which layer does this vendor serve? Is it the right tool for that layer's specific purpose?
- **Adjacent Integration**: Does it connect smoothly with the layers above and below?
- **Gap Prevention**: Does selecting this vendor create gaps in your architecture, or complete a capability you need?
- **Overlap Avoidance**: Does this vendor duplicate functionality you're getting elsewhere?

**Architecture Fit Score**: 1-6 based on layer alignment and integration quality

**Pillar 3: GOALS™ Operations (Score Separately)**

The third pillar measures operational readiness. A technology might score perfectly on INPACT™ but fail if your team can't operate it effectively:

| GOALS™ Dimension | Vendor Evaluation Question | What to Look For |
|------------------|---------------------------|------------------|
| **G (Governance)** | Does it support policy enforcement, compliance? | HIPAA/SOC2 certification, BAA availability, audit features |
| **O (Observability)** | Does it provide monitoring, tracing, dashboards? | Built-in metrics, logging quality, alerting integration |
| **A (Availability)** | What's the uptime SLA? Support quality? | 99.9%+ SLA, responsive support, documentation quality |
| **L (Lexicon)** | Does it support semantic accuracy, terminology? | API quality, SDK maturity, integration breadth |
| **S (Solid)** | Is it reliable, consistent, high-quality? | Production track record, error handling, data integrity |

Score each dimension 1-5 (GOALS™ uses 5-point scale).

**GOALS™ Vendor Score**: Sum of relevant dimensions (maximum 25)

**Why Separate Scores Matter**

INPACT™ measures what infrastructure must *provide* to agents. GOALS™ measures how you *operate* that infrastructure. These are different evaluation dimensions:

- A vendor scoring high on INPACT™ but low on GOALS™ delivers impressive technology your team can't sustain
- A vendor scoring high on GOALS™ but low on INPACT™ is easy to operate but can't meet agent requirements
- Both scores must exceed minimum thresholds independently

**Minimum Thresholds for Healthcare**

| Threshold | Minimum Score | Rationale |
|-----------|---------------|-----------|
| INPACT™ | ≥24/36 (67%) | Agents must meet core needs |
| GOALS™ | ≥18/25 (72%) | Operations must be sustainable |
| P (Permitted) | ≥5/6 | Healthcare requires strong access control |
| G (Governance) | 5/5 | HIPAA compliance non-negotiable |
| BAA | Required | Filter before technical evaluation |

Vendors scoring below these thresholds should be rejected regardless of other strengths.

---

**What This Means for Your Vendor Search**

Your three-pillar scores become your vendor conversation framework. When evaluating any technology:

1. **Filter first**: BAA/compliance requirements eliminate vendors before technical evaluation
2. **Score INPACT™**: Does it meet agent needs for its layer?
3. **Score GOALS™**: Can your team operate it?
4. **Verify architecture fit**: Does it integrate with adjacent layers?

This methodology applies regardless of which specific vendors you evaluate. The vendor landscape changes; the evaluation criteria remain constant.

---

### 1.3 Build vs Buy vs Partner

Not every component requires a vendor purchase. The Architecture of Trust supports a hybrid approach: buy commodity capabilities, build differentiators, partner for expertise.

**Diagram: Build vs Buy vs Partner Decision Flow**

```mermaid

graph LR
    START["Component<br/>Needed"]
    
    subgraph DECISIONS[" "]
        direction TB
        Q1{"Competitive<br/>differentiator?"}
        Q2{"Proven vendor<br/>solutions exist?"}
        Q3{"Team has<br/>expertise?"}
    end
    
    subgraph OUTCOMES[" "]
        direction TB
        BUILD["BUILD<br/>Custom Dev<br/>5-10%"]
        BUY["BUY<br/>SaaS/Cloud<br/>85-90%"]
        PARTNER["PARTNER<br/>Consulting<br/>0-5%"]
    end
    
    Copyright["© 2025 Colaberry Inc."]
    
    START --> Q1
    Q1 -->|"Yes"| BUILD
    Q1 -->|"No"| Q2
    Q2 -->|"Yes"| BUY
    Q2 -->|"No"| Q3
    Q3 -->|"Yes"| BUILD
    Q3 -->|"No"| PARTNER
    
    style DECISIONS fill:none,stroke:none
    style OUTCOMES fill:none,stroke:none
    style START fill:#f5f5f5,stroke:#666666,stroke-width:2px,color:#333333
    style Q1 fill:#fff9c4,stroke:#f9a825,stroke-width:2px,color:#f57f17
    style Q2 fill:#fff9c4,stroke:#f9a825,stroke-width:2px,color:#f57f17
    style Q3 fill:#fff9c4,stroke:#f9a825,stroke-width:2px,color:#f57f17
    style BUILD fill:#e3f2fd,stroke:#1976d2,stroke-width:2px,color:#0d47a1
    style BUY fill:#e0f2f1,stroke:#00897b,stroke-width:2px,color:#004d40
    style PARTNER fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#e65100
    style Copyright fill:#ffffff,stroke:none,color:#666666

```

**Build (Custom Development) — 5-10% of Stack**

Custom development makes sense when:

- The capability is a competitive differentiator unique to your organization
- No vendor solution fits your specific workflow or compliance requirements
- You need deep integration with proprietary systems
- Long-term maintenance costs are acceptable

**Typical Build Candidates**:
- Custom HITL user interfaces matching specific clinical workflows
- Specialized agent prompts incorporating domain-specific concepts
- Integration layers connecting proprietary EHR systems to semantic layers

**Build Trade-offs**:
- ✅ Perfect fit for unique requirements
- ✅ No vendor dependency
- ⚠️ Higher upfront development cost
- ⚠️ Ongoing maintenance burden
- ⚠️ Slower time-to-value

**Buy (SaaS/Cloud Services) — 85-90% of Stack**

Purchasing makes sense when:

- The capability is commodity (many proven solutions exist)
- Time-to-value matters more than perfect fit
- Your team lacks specialized expertise to build and maintain
- Vendor provides compliance certifications you need (HIPAA, SOC2)

**Typical Buy Candidates**:
- Vector databases, data warehouses, graph databases
- CDC platforms, streaming infrastructure
- Observability and monitoring tools
- LLM APIs and embedding services

**Buy Trade-offs**:
- ✅ Fastest time-to-value
- ✅ Vendor handles maintenance, scaling, security
- ✅ Predictable recurring costs
- ⚠️ Vendor dependency and potential lock-in
- ⚠️ Less customization flexibility

**Partner (Managed Services/Consulting) — 0-5% of Stack**

Partnering makes sense when:

- You need expertise your team doesn't have
- Implementation requires specialized knowledge
- One-time setup matters more than ongoing capability
- Knowledge transfer to your team is included

**Typical Partner Candidates**:
- Implementation consulting for transformation projects
- Domain-specific content mapping (clinical terminology, regulatory requirements)
- Compliance validation and audit preparation

**Partner Trade-offs**:
- ✅ Access specialized expertise without hiring
- ✅ Compressed timelines through experienced guidance
- ✅ Knowledge transfer builds internal capability
- ⚠️ Variable costs based on scope
- ⚠️ Dependency on partner availability

**Typical Split for Healthcare Organizations**

| Approach | Percentage | Rationale |
|----------|------------|-----------|
| Buy | 90% | Managed services reduce operational burden, compliance built-in |
| Build | 5% | Competitive differentiators only (workflow-specific interfaces, domain prompts) |
| Partner | 5% | One-time expertise gaps (implementation, compliance validation) |

This split works for organizations needing fast time-to-value with regulatory compliance, lacking internal expertise in agent infrastructure, and with budget for managed services. Your split may differ based on existing capabilities and strategic priorities.

---

### 1.4 Budget Tiers

Technology selection depends heavily on available budget. The three-pillar vendor test identifies capable tools, but budget constraints determine which tier of solutions you can deploy.

**Tier Overview**

| Tier | Total Investment | Monthly Ops | Best For | Stack Philosophy |
|------|------------------|-------------|----------|------------------|
| **Starter** | $150-250K | <$20K | POC, <1,000 users | Open source + minimal SaaS |
| **Growth** | $400-600K | $30-50K | Production healthcare, <50K users | Enterprise SaaS + strategic OSS |
| **Enterprise** | $800K-1.5M | $60-100K | Multi-region, >50K users | Best-in-class everything |

*For detailed budget allocation by layer for each tier, see Appendix D (Budget Methodology).*

**Tier Selection Guide**

| If Your Situation Is... | Choose Tier |
|-------------------------|-------------|
| Proof of concept, internal tools, <1K users | Tier 1: Starter |
| Production system, healthcare compliance, <50K users | Tier 2: Growth |
| Enterprise scale, multi-region, mission-critical | Tier 3: Enterprise |
| Unsure | Start with Tier 2, adjust based on results |

**Budget Allocation by Phase**

Regardless of tier, budget allocation follows the 7-Layer Architecture:

| Phase | Weeks | Layers | Typical Allocation |
|-------|-------|--------|-------------------|
| Foundation | 1-4 | L1-L2 | 35-40% |
| Intelligence | 5-7 | L3-L4 | 30-35% |
| Trust | 8-10 | L5-L6-L7 | 25-30% |

*See Chapter 10 for week-by-week breakdown.*

---

### 1.5 Scoring Quick Reference

**INPACT™ Scoring Scale (1-6)**

| Score | Label | Description |
|-------|-------|-------------|
| **6** | Excellent | Best-in-class; competitive advantage |
| **5** | Strong | Production-ready; meets all requirements |
| **4** | Functional | Adequate with monitoring |
| **3** | Moderate | Basic capability; gaps workable |
| **2** | Significant Gap | Major limitations; workarounds needed |
| **1** | Critical Gap | Blocks deployment |

**GOALS™ Scoring Scale (1-5)**

| Score | Label | Description |
|-------|-------|-------------|
| **5** | Advanced | Full automation with continuous improvement |
| **4** | Proficient | Comprehensive, mostly automated |
| **3** | Developing | Structured but incomplete |
| **2** | Basic | Minimal implementation, reactive |
| **1** | Absent | No formal capability |

**Minimum Thresholds**

| Framework | Minimum | Healthcare Requirement |
|-----------|---------|------------------------|
| INPACT™ | ≥24/36 (67%) | P (Permitted) ≥5/6 |
| GOALS™ | ≥18/25 (72%) | G (Governance) = 5/5 |
| Compliance | BAA Required | Filter before evaluation |

---

## Part 2: Layer-by-Layer Selection Criteria

This section provides selection criteria for each of the seven architecture layers. For each layer, you'll find: the purpose and INPACT™ dimensions to prioritize, minimum requirements and questions to ask vendors, red flags that eliminate vendors, and subcategories to evaluate.

> **📚 For specific vendor comparisons:** See Appendix DA-1 for detailed vendor tables, or visit **trustbeforeintelligence.com/tools** for current evaluations.

**Diagram: The 7-Layer Architecture Technology Stack**

```mermaid

graph TB
    subgraph STACK["7-LAYER ARCHITECTURE"]
        direction TB
        subgraph ROW1[" "]
            direction LR
            subgraph INTEL["INTELLIGENCE"]
                direction TB
                L4["L4: Retrieval"]
                L3["L3: Semantic"]
            end

            subgraph TRUST["TRUST LAYERS"]
                direction TB
                L7["L7: Orchestration"]
                L6["L6: Observability"]
                L5["L5: Governance"]
            end
            
        end
        
        subgraph FOUND["FOUNDATION LAYERS"]
            direction LR
            L2["L2: Data Fabric"]
            L1["L1: Storage"]
        end
    end
    
    Copyright["© 2025 Colaberry Inc."]
    
    ROW1 --> FOUND
    
    style STACK fill:#f5f5f5,stroke:#666666,stroke-width:2px,color:#333333
    style ROW1 fill:none,stroke:none
    style TRUST fill:#e0f2f1,stroke:#00897b,stroke-width:2px,color:#004d40
    style INTEL fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#e65100
    style FOUND fill:#e3f2fd,stroke:#1976d2,stroke-width:2px,color:#0d47a1
    style L7 fill:#b2dfdb,stroke:#00897b,color:#004d40
    style L6 fill:#b2dfdb,stroke:#00897b,color:#004d40
    style L5 fill:#b2dfdb,stroke:#00897b,color:#004d40
    style L4 fill:#ffe0b2,stroke:#f57c00,color:#e65100
    style L3 fill:#ffe0b2,stroke:#f57c00,color:#e65100
    style L2 fill:#bbdefb,stroke:#1976d2,color:#0d47a1
    style L1 fill:#bbdefb,stroke:#1976d2,color:#0d47a1
    style Copyright fill:#ffffff,stroke:none,color:#666666


```

---

### 2.1 Layer 1: Multi-Modal Storage

**Purpose:** Store vectors, structured data, and graph relationships for agent retrieval

**INPACT™ Dimensions to Prioritize:** I (speed), C (integration), N (vectors)

**Implementation Timing:** Weeks 1-4 (Foundation Phase)

Layer 1 establishes the storage foundation everything else depends on. Without performant multi-modal storage, agents can't retrieve context quickly enough for conversational interaction.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| Query Latency | <100ms p95 | What is your p95 latency at 500 concurrent users? |
| Healthcare Compliance | HIPAA BAA available | Do you offer BAA? What's your SOC2 status? |
| Embedding Support | Native vector operations | Which embedding models integrate natively? |
| Scalability | 10x headroom | How do you handle 10x current load? |
| Data Residency | Region-specific storage | Can you guarantee US-only data storage? |

**Red Flags (Eliminate Vendor If Present)**

- No BAA available (eliminates for PHI workloads)
- Latency benchmarks only for small datasets (<1M records)
- Requires self-managed infrastructure without DevOps support
- No native integration with common embedding providers
- Pricing model that scales unpredictably with query volume

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| Vector Databases | Semantic search, RAG | Sub-50ms similarity search |
| Data Warehouses | Structured analytics | SQL compatibility, compliance certifications |
| Graph Databases | Relationship traversal | Multi-hop query performance |
| Document Stores | Flexible schema | JSON native, clinical notes |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.1.*

---

### 2.2 Layer 2: Real-Time Data Fabric

**Purpose:** Keep data fresh (<30 seconds), enable streaming for agents

**INPACT™ Dimensions to Prioritize:** I (freshness), C (CDC), A (streaming)

**Implementation Timing:** Weeks 1-4 (Foundation Phase)

Layer 2 ensures agents work with current information. Without real-time data, agents make decisions on stale context—the difference between catching a medication interaction before administration versus after.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| CDC Latency | <30 seconds end-to-end | What is your typical CDC latency from source to target? |
| Connector Coverage | EHR systems supported | Do you have native connectors for Epic/Cerner? |
| Schema Evolution | Auto-adapt to changes | How do you handle source schema changes? |
| Throughput | >10K events/second | What's your sustained throughput capacity? |
| Exactly-Once Delivery | Guaranteed | How do you ensure no duplicate or lost events? |

**Red Flags (Eliminate Vendor If Present)**

- CDC latency measured in minutes, not seconds
- No native healthcare EHR connectors (requires custom development)
- Manual intervention required for schema changes
- No exactly-once delivery guarantee
- Pricing based on row count without volume discounts

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| CDC Tools | Database change capture | Connector ecosystem breadth |
| Streaming Platforms | Event processing | Throughput and latency |
| Stream Processing | Real-time transformation | Windowing and aggregation |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.2.*

---

### 2.3 Layer 3: Semantic Layer

**Purpose:** Translate business language to data structures

**INPACT™ Dimensions to Prioritize:** N (natural language), C (context), T (transparency)

**Implementation Timing:** Weeks 5-7 (Intelligence Phase)

Layer 3 bridges human language and database schemas. When a clinician asks "Show me patients needing diabetes follow-up," the semantic layer resolves this to precise query logic without requiring SQL knowledge.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| Term Resolution | >95% accuracy | What is your term resolution accuracy on healthcare terminology? |
| Entity Resolution | >90% confidence | How do you handle entity disambiguation across systems? |
| Lineage Tracking | Complete | Can you trace any metric back to source tables? |
| Glossary Scale | >2,000 terms | How many business terms can your glossary support? |
| Ontology Support | Healthcare standards | Do you support SNOMED, ICD-10, LOINC mappings? |

**Red Flags (Eliminate Vendor If Present)**

- No support for healthcare ontologies (SNOMED, ICD-10, LOINC)
- Manual-only term definition (no automation assistance)
- No lineage tracking to source systems
- Entity resolution limited to exact matches only
- No API for programmatic glossary updates

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| Semantic Modeling | Metric definitions | SQL-native transformation |
| Data Catalogs | Discovery and governance | Auto-classification, PII detection |
| Entity Resolution | Identity matching | Probabilistic matching confidence |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.3.*

---

### 2.4 Layer 4: Intelligence Orchestration & Retrieval

**Purpose:** Transform queries into grounded, accurate responses through RAG

**INPACT™ Dimensions to Prioritize:** N (NLU), A (adaptive), T (citations)

**Implementation Timing:** Weeks 5-7 (Intelligence Phase)

Layer 4 is the complete intelligence pipeline: query understanding, embedding generation, hybrid retrieval, reranking, context assembly, LLM generation, and semantic caching. This is not a single technology but an orchestrated workflow.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| RAG Accuracy | >85% on domain queries | What accuracy do you achieve on healthcare RAG tasks? |
| Citation Support | Source attribution | Can responses include source citations? |
| Hybrid Retrieval | Vector + keyword | Do you support hybrid search with RRF? |
| Context Window | >100K tokens | What's your maximum context window? |
| Streaming Response | SSE support | Can you stream responses token-by-token? |

**Red Flags (Eliminate Vendor If Present)**

- No healthcare BAA for LLM providers
- Citation/attribution not supported
- Vector-only retrieval (no keyword fallback)
- No prompt versioning or management
- Cost model opaque or unpredictable

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| LLM Providers | Text generation | Quality, latency, cost |
| Embedding Models | Vectorization | Domain-specific quality |
| RAG Frameworks | Pipeline orchestration | Ecosystem and flexibility |
| Reranking | Result refinement | Accuracy improvement |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.4.*

---

### 2.5 Layer 5: Governance

**Purpose:** Control what agents can do based on context

**INPACT™ Dimensions to Prioritize:** P (permitted), T (transparent)

**Implementation Timing:** Weeks 8-10 (Trust Phase)

Layer 5 provides policy-based authorization and audit infrastructure. Agents make thousands of decisions daily and can't rely on human review for every query. Context-aware authorization evaluates the full situation: who is asking, what they're asking for, when, and why.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| Policy Evaluation | <50ms latency | What is your policy evaluation latency at scale? |
| ABAC Support | Four-factor evaluation | Do you support subject, resource, action, and context attributes? |
| HITL Integration | Workflow support | Can policies trigger human escalation? |
| Audit Completeness | 100% coverage | Are all decisions logged with full context? |
| Policy Versioning | Git-compatible | Can policies be version-controlled? |

**Red Flags (Eliminate Vendor If Present)**

- RBAC only (no attribute-based policies)
- No audit trail or incomplete logging
- Policy changes require code deployments
- No HITL escalation capability
- Latency >100ms (impacts user experience)

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| Policy Engines | ABAC evaluation | Rego/policy language flexibility |
| Data Governance | Compliance management | Healthcare-specific features |
| HITL Platforms | Human escalation | Workflow customization |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.5.*

---

### 2.6 Layer 6: Observability

**Purpose:** See what agents are doing, detect issues, optimize performance

**INPACT™ Dimensions to Prioritize:** T (transparent), A (adaptive)

**Implementation Timing:** Weeks 8-10 (Trust Phase)

Layer 6 delivers complete visibility into agent operations. Without observability, agents are black boxes—you can't debug failures, optimize costs, or detect quality degradation.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| Distributed Tracing | End-to-end | Can you trace requests across all seven layers? |
| LLM Cost Tracking | Per-query attribution | Can you break down cost by query type and model? |
| Latency Percentiles | P50/P95/P99 | What latency metrics do you provide? |
| Alert Integration | PagerDuty/Slack | How do alerts route to on-call teams? |
| Retention | >30 days | How long are traces and logs retained? |

**Red Flags (Eliminate Vendor If Present)**

- No LLM-specific metrics (token usage, cost)
- Sampling-only tracing (misses rare failures)
- No correlation between traces and logs
- Alert fatigue from poor threshold defaults
- Expensive retention pricing

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| APM Platforms | Full-stack monitoring | LLM integration depth |
| LLM Observability | AI-specific tracing | Prompt versioning, quality metrics |
| Log Management | Centralized logging | Search and correlation |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.6.*

---

### 2.7 Layer 7: Orchestration

**Purpose:** Coordinate multiple agents working together on complex queries

**INPACT™ Dimensions to Prioritize:** A (adaptive), C (contextual), all dimensions at integration

**Implementation Timing:** Weeks 8-10 (Trust Phase)

Layer 7 delivers multi-agent coordination. Complex queries often span multiple domains—a care coordination question might require clinical, scheduling, and billing expertise simultaneously.

**Selection Criteria**

| Criterion | Minimum Requirement | Questions to Ask Vendors |
|-----------|---------------------|--------------------------|
| Multi-Agent Support | Supervisor patterns | Can you coordinate multiple specialized agents? |
| State Management | Persistent across steps | How do you maintain state across agent interactions? |
| Routing Logic | Conditional flows | Can routing decisions be based on query content? |
| Integration | Layers 1-6 | How do you integrate with governance and observability? |
| Error Handling | Graceful degradation | What happens when one agent fails? |

**Red Flags (Eliminate Vendor If Present)**

- Single-agent only (no coordination patterns)
- Stateless execution (no memory across steps)
- No integration with observability layer
- Opaque routing decisions (can't explain why agent X was selected)
- No timeout or circuit breaker patterns

**Subcategories to Evaluate**

| Subcategory | Primary Use | Key Differentiator |
|-------------|-------------|-------------------|
| Agent Frameworks | Multi-agent coordination | State management approach |
| Workflow Engines | Process orchestration | Retry and error handling |
| Integration Platforms | Cross-system coordination | Connector ecosystem |

*For detailed vendor comparisons in each subcategory, see Appendix DA-1, Section 2.7.*

---

**Your Layer Choices Now Constrain Each Other**

Technology selections are not independent. Your Layer 1 storage choices constrain which Layer 4 retrieval approaches work efficiently. Your Layer 5 governance choices determine what observability data Layer 6 must capture. Your Layer 3 semantic layer must integrate with both Layer 1 storage below and Layer 4 intelligence above.

Before finalizing any layer, verify integration with adjacent layers. The best individual component that doesn't integrate is worse than a good component that does.

---

## Part 3: Vendor Evaluation Process

Selecting vendors requires more than scoring spreadsheets. This section provides practical tools for evaluation: RFP templates structured around the three pillars, POC validation approaches, and contract negotiation guidance.

---

### 3.1 Three-Pillar RFP Template

Structure your vendor requests around the Architecture of Trust. This ensures responses address what matters for agent infrastructure.

**RFP Structure (100 Points Total)**

**Part 1: INPACT™ Requirements (40 Points)**

| Dimension | Points | Questions to Include |
|-----------|--------|---------------------|
| I (Instant) | 7 | What is your p95 query latency? Describe caching capabilities. |
| N (Natural) | 7 | How do you support semantic search? What embedding models integrate? |
| P (Permitted) | 7 | Describe ABAC capabilities. How do you support HITL workflows? |
| A (Adaptive) | 6 | How do you enable feedback loops? Describe model versioning. |
| C (Contextual) | 6 | How many data sources can you integrate? Describe connector ecosystem. |
| T (Transparent) | 7 | What explainability features exist? Describe compliance certifications. |

**Part 2: Architecture Requirements (30 Points)**

| Criterion | Points | Questions to Include |
|-----------|--------|---------------------|
| Layer Alignment | 10 | Which architecture layer does your product serve? |
| Adjacent Integration | 10 | How do you integrate with Layer N-1 and Layer N+1 technologies? |
| Gap/Overlap Analysis | 10 | What capabilities does your product NOT provide? |

**Part 3: GOALS™ Requirements (30 Points)**

| Dimension | Points | Questions to Include |
|-----------|--------|---------------------|
| G (Governance) | 6 | What compliance certifications do you hold? Is BAA available? |
| O (Observability) | 6 | What monitoring dashboards exist? How do you support tracing? |
| A (Availability) | 6 | What is your uptime SLA? Describe support response times. |
| L (Lexicon) | 6 | Describe API quality and SDK availability. |
| S (Solid) | 6 | What is your production track record? How do you ensure data integrity? |

*Download complete RFP template at trustbeforeintelligence.com/tools*

---

### 3.2 POC Approach

Proof-of-concept validation tests vendors against your specific requirements, not demo environments. Run 2-week POCs for shortlisted vendors using representative data.

**Two-Week POC Structure**

**Week 1: INPACT™ Validation**

| Dimension | Validation Test | Success Criteria |
|-----------|-----------------|------------------|
| I (Instant) | Run 1,000 representative queries | p95 latency < target |
| N (Natural) | Test 100 business-language queries | Accuracy > 85% |
| P (Permitted) | Configure 10 representative policies | Policy evaluation < 50ms |
| A (Adaptive) | Simulate feedback loop | Feedback reflected in < 24 hours |
| C (Contextual) | Connect to 3+ data sources | All sources accessible in single query |
| T (Transparent) | Generate audit logs for all operations | 100% operation coverage |

**Week 2: Layer Integration + GOALS™ Validation**

| Test | Validation Approach | Success Criteria |
|------|---------------------|------------------|
| Layer Integration | Connect to adjacent layers | End-to-end latency < target |
| Monitoring | Configure dashboards and alerts | All key metrics visible |
| Support | Submit support ticket | Response within SLA |
| Documentation | Complete setup using docs only | Achievable without vendor help |
| Failure Recovery | Simulate outage | Recovery within SLA |

**POC Failure Patterns to Watch**

- Latency degradation under realistic load (not demo conditions)
- Data volume limitations not apparent in small-scale tests
- Integration complexity requiring vendor professional services
- Documentation gaps requiring support tickets for basic setup

POC failures save you from costly mistakes. A vendor that fails POC would have failed in production—better to discover this in two weeks than twelve months.

---

### 3.3 Contract Negotiation

Leverage your evaluation process in negotiations. Vendors competing through structured POCs know you're evaluating alternatives seriously.

**Negotiation Leverage Points**

| Lever | Typical Discount | How to Use |
|-------|------------------|------------|
| Annual Commitment | 15-25% | Commit to 12-month minimum for discount |
| Multi-Year | 20-30% | 2-3 year commitment for deeper discount |
| Pilot Success | 10-15% | Reference POC success as proof of value |
| Volume | 10-20% | Commit to higher usage tier upfront |
| Case Study | 5-10% | Offer to be reference customer |

**Must-Have Contract Terms (Healthcare)**

| Term | Requirement | Why It Matters |
|------|-------------|----------------|
| **BAA** | Signed Business Associate Agreement | HIPAA compliance mandatory |
| **Data Residency** | US-only data storage confirmed | PHI cannot leave jurisdiction |
| **SLA** | Uptime guarantee with financial penalties | Accountability for reliability |
| **Exit Clause** | Data portability and transition period | Avoid vendor lock-in |
| **Security Audit** | Right to audit or SOC2/HIPAA certification | Verify security claims |

Negotiate all five terms with every PHI-touching vendor. Walk away from vendors who resist BAA requirements—they'll eventually agree when you demonstrate serious evaluation of alternatives.

---

## Part 4: Applying the Methodology

This section shows how to apply the selection methodology. Echo Health Systems serves as an example of the process, not an endorsement of specific vendors.

---

### 4.1 Echo's Selection Criteria

Echo Health Systems—a mid-size health system with $1.23M budget, 12-week timeline, and 2-person infrastructure team—began with constraints, not vendor lists.

**Echo's Context Shaped Their Criteria**

| Constraint | Implication for Selection |
|------------|---------------------------|
| Healthcare (PHI) | BAA required before technical evaluation |
| 12-week timeline | Managed services over self-hosted |
| $1.23M budget | Growth tier, not Enterprise |
| 2-person infrastructure team | Operational simplicity prioritized |

**Echo's Minimum Thresholds**

Echo applied the healthcare minimum thresholds from Part 1.2: INPACT™ ≥24/36, GOALS™ ≥18/25, P ≥5/6, G=5/5, and BAA required before technical evaluation.

**How Filters Narrowed the Field**

These criteria functioned as progressive filters:

1. **BAA filter** — Vendors without healthcare BAA capability eliminated before technical review
2. **INPACT™ threshold** — Vendors below minimum eliminated after paper evaluation
3. **GOALS™ threshold** — Vendors with impressive technology but unsustainable operations eliminated
4. **POC validation** — Remaining vendors validated against real workloads

The filters did the work. By the time Echo ran POCs, they were choosing between good options, not eliminating bad ones.

**Build vs Buy Decisions**

Echo applied the decision framework from Section 1.3:

| Question | Echo's Answer | Decision |
|----------|---------------|----------|
| Is vector search a competitive differentiator? | No — commodity capability | BUY |
| Does a proven CDC solution exist for Epic EHR? | Yes — multiple vendors | BUY |
| Does our clinical HITL workflow exist off-the-shelf? | No — unique to our process | BUILD |
| Do we have ABAC policy expertise internally? | No | PARTNER (implementation) then BUY |

Result: 90% buy, 5% build, 5% partner.

---

### 4.2 Your Turn: Applying the Methodology

Echo's context—mid-size health system, $1.23M budget, 12-week timeline, 2-person infrastructure team—shaped their criteria. Your context will shape yours differently.

**Different Contexts, Different Criteria**

A financial services firm might prioritize:
- SOC2 Type II over BAA
- Sub-10ms latency over sub-100ms
- On-premises deployment over managed cloud

A manufacturing company might prioritize:
- OT/IT integration capability
- Edge deployment options
- Vendor longevity over startup innovation

**The methodology remains constant. The criteria adapt to context.**

---

### 4.3 Your Selection Toolkit

The following tools help you apply the methodology to your situation.

**Available at trustbeforeintelligence.com/tools:**

**Vendor Evaluation Scorecard**
- INPACT™ scoring template (6 dimensions × 6 points, 36 max)
- GOALS™ scoring template (5 dimensions × 5 points, 25 max)
- Weighted scoring based on your priorities
- Comparison matrix for finalists

**POC Test Plan Template**
- Week 1: INPACT™ validation tests
- Week 2: GOALS™ + integration validation
- Success criteria definition
- Failure documentation guide

**Contract Terms Checklist**
- Non-negotiable terms (BAA/SOC2, data residency, SLA, exit clause)
- Negotiable terms (pricing, commitment length, support tier)
- Red flags that indicate walk-away

**Build vs Buy Decision Matrix**
- Differentiator assessment
- Market availability check
- Internal capability evaluation
- Total cost of ownership comparison

**Budget Planning Worksheet**
- Three-tier templates (Starter, Growth, Enterprise)
- Implementation vs ongoing cost separation
- Hidden cost identification

---

### 4.4 What the Methodology Prevents

Structured methodology prevents common selection failures:

| Failure Mode | How Methodology Prevents It |
|--------------|----------------------------|
| "Shiny object" syndrome | GOALS™ scoring exposes operational gaps behind impressive demos |
| Compliance gaps | BAA/regulatory filter applied before technical evaluation |
| Vendor lock-in | Exit clause required in contract terms checklist |
| Budget overruns | Three-pillar test aligns selection to actual budget tier |
| Integration failures | POC Week 2 validates layer integration before commitment |
| Operational burden | GOALS™ Availability and Solid dimensions expose hidden complexity |

The methodology doesn't guarantee perfect selections. It prevents predictable mistakes.

---

## Part 5: Echo's Complete Stack Summary

This section provides the reference for Echo Health Systems' final technology choices. Every vendor passed the three-pillar test. Every selection has documented rationale.

> **Note:** Echo's choices reflect their specific context (healthcare, $1.23M budget, 12-week timeline). Your selections will differ based on your constraints. For detailed vendor comparisons, see Appendix DA-1.

**Diagram: Echo's Complete Technology Stack**

```mermaid

graph LR
    subgraph TRUST["TRUST"]
        direction LR
        L7["L7: Orchestration"]
        L6["L6: Observability"]
        L5["L5: Governance"]
    end
    
    subgraph INTEL["INTELLIGENCE"]
        direction LR
        L4["L4: Retrieval"]
        L3["L3: Semantic"]
    end
    
    subgraph FOUND["FOUNDATION"]
        direction LR
        L2["L2: Data Fabric"]
        L1["L1: Storage"]
    end
    
    Copyright["© 2025 Colaberry Inc."]
    
    TRUST --> INTEL --> FOUND
    
    style TRUST fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px,color:#4a148c
    style INTEL fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#e65100
    style FOUND fill:#e3f2fd,stroke:#1976d2,stroke-width:2px,color:#0d47a1
    style L7 fill:#e1bee7,stroke:#7b1fa2,color:#4a148c
    style L6 fill:#b2dfdb,stroke:#00897b,color:#004d40
    style L5 fill:#f8bbd9,stroke:#c2185b,color:#880e4f
    style L4 fill:#ffe0b2,stroke:#f57c00,color:#e65100
    style L3 fill:#fff59d,stroke:#f9a825,color:#f57f17
    style L2 fill:#bbdefb,stroke:#1976d2,color:#0d47a1
    style L1 fill:#c8e6c9,stroke:#388e3c,color:#1b5e20
    style Copyright fill:#ffffff,stroke:none,color:#666666

```

**Echo's Selection Principles**

Four principles guided Echo's selections:

**1. Managed Over Self-Hosted** — Healthcare organizations can't staff 24/7 on-call for every component. Trade-off accepted: Some vendor lock-in. Trade-off avoided: Infrastructure operations consuming clinical IT resources.

**2. Healthcare-First** — Every PHI-touching vendor has BAA capability, applied as filter before technical evaluation. Trade-off accepted: Smaller vendor pool. Trade-off avoided: Compliance risk.

**3. Integration-Proven** — Selected vendors that work together, prioritizing ecosystem compatibility over best-in-class isolation. Trade-off accepted: Not always best-in-class for every capability. Trade-off avoided: Integration complexity.

**4. Cost-Optimized** — Growth tier, negotiated annual commits, right-sized to actual scale, open-source where operational burden acceptable. Trade-off accepted: Some manual effort. Trade-off avoided: Over-spending on unused enterprise features.

**Echo's Results**

Echo completed implementation under budget ($992K of $1.23M), achieved INPACT™ 89/100 and GOALS™ 21/25, and went live in 12 weeks. *(For complete investment breakdown, see Appendix D. For canonical metrics, see Appendix E.)*

*For Echo's complete vendor list with costs and rationale, see Appendix DA-1, Section 4.*

---

## Bridge to Chapter 12

You've learned the methodology for selecting your technology stack. Every vendor evaluation uses the three-pillar test. Every layer has clear selection criteria. The Architecture of Trust provides the framework.

Now comes the harder part: keeping it running.

Chapter 12 completes your journey with MLOps practices for versioning and testing, incident response runbooks for when things go wrong, and the continuous improvement cycles that sustain trust over time. You've learned to select the right tools. Now learn to operate them.

---

## Chapter Summary

| Part | Content | Key Deliverable |
|------|---------|-----------------|
| Part 1 | Selection Framework | Three-pillar vendor test, build/buy/partner, budget tiers |
| Part 2 | Layer-by-Layer Criteria | Selection criteria for all 7 layers |
| Part 3 | Evaluation Process | RFP templates, POC approach, negotiation |
| Part 4 | Applying the Methodology | Echo's process as example, your toolkit |
| Part 5 | Echo's Stack Summary | Reference architecture with principles |

**Key Resources:**
- **Appendix DA-1:** Detailed vendor comparisons by layer
- **trustbeforeintelligence.com/tools:** Interactive scorecards, templates, current vendor database

---

## References

**Academic Research (Tier 1)**

[1] Malkov, Y. A., & Yashunin, D. A. (2018). "Efficient and Robust Approximate Nearest Neighbor Search Using Hierarchical Navigable Small World Graphs." *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 42(4), 824-836. https://arxiv.org/abs/1603.09320 (Accessed November 2025)

[2] Gao, Y., Xiong, Y., Gao, X., et al. (2024). "Retrieval-Augmented Generation for Large Language Models: A Survey." *arXiv preprint arXiv:2312.10997*. https://arxiv.org/abs/2312.10997 (Accessed November 2025)

**Government & Standards (Tier 2)**

[3] National Institute of Standards and Technology. (2014). "Guide to Attribute Based Access Control (ABAC) Definition and Considerations." NIST Special Publication 800-162. https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-162.pdf (Accessed November 2025)

[4] National Institute of Standards and Technology. (2023). "AI Risk Management Framework (AI RMF 1.0)." NIST AI 100-1. https://www.nist.gov/itl/ai-risk-management-framework (Accessed November 2025)

---

## Acronym Reference

| Acronym | Definition |
|---------|------------|
| ABAC | Attribute-Based Access Control |
| BAA | Business Associate Agreement |
| CDC | Change Data Capture |
| GOALS™ | Governance, Observability, Availability, Lexicon, Solid |
| HIPAA | Health Insurance Portability and Accountability Act |
| HITL | Human-in-the-Loop |
| INPACT™ | Instant, Natural, Permitted, Adaptive, Contextual, Transparent |
| POC | Proof of Concept |
| RAG | Retrieval-Augmented Generation |
| RFP | Request for Proposal |

---

© 2025 Colaberry Inc. All Rights Reserved.

INPACT™ and GOALS™ are trademarks of Colaberry Inc.
