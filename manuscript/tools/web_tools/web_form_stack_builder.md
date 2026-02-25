# Stack Builder  - Web Form Specification

## Overview

**URL:** trustbeforeintelligence.ai/stack
**Purpose:** Interactive 7-layer gap analysis with personalized build recommendations
**Lead Capture:** Email required before viewing full results

---

## User Flow

### Step 1: Landing Page
- Value proposition: "Discover what's missing in your AI agent stack in 5 minutes"
- Brief explanation of the 7-layer architecture
- Preview: Visual stack diagram showing all 7 layers
- Echo Health teaser: "See how Echo Health filled their gaps and went from 28% to 89% readiness"
- **CTA Button:** "Analyze My Stack"

### Step 2: Lead Capture (Before Analysis)
Required fields:
- Email (required)
- Name (required)
- Organization (required)
- Role (required)

Optional fields:
- Industry (dropdown: Healthcare, Financial Services, Manufacturing, Retail, Technology, Government, Other)
- Current INPACT score (if known)

### Step 3: Context Questions (Page 1)

**Question Set A: Industry & Compliance**

| Question | Input Type | Options |
|----------|------------|---------|
| What industry are you in? | Single select | Healthcare, Financial Services, Manufacturing, Retail, Technology, Government, Other |
| What compliance requirements apply? | Multi-select | HIPAA, SOC2, GDPR, FedRAMP, PCI-DSS, None/Unknown |
| Do you handle sensitive data? | Single select | PHI (health), PII (personal), Financial, Public only |

**Question Set B: Scale & Budget**

| Question | Input Type | Options |
|----------|------------|---------|
| Expected agent users? | Single select | <100, 100-1,000, 1,000-10,000, 10,000+ |
| Data volume? | Single select | <1GB, 1-100GB, 100GB-1TB, 1TB+ |
| Budget tier? | Single select | Starter ($30-50K), Growth ($150-250K), Enterprise ($300K+) |

**Question Set C: Platform**

| Question | Input Type | Options |
|----------|------------|---------|
| Primary cloud platform? | Single select | AWS, Azure, GCP, Multi-cloud, On-premises, Hybrid |
| Current data platform? | Single select | Snowflake, Databricks, BigQuery, Redshift, SQL Server, Other, None |

---

### Step 4: Layer-by-Layer Inventory (Pages 2-8)

**One page per layer. For each layer, user selects what they have.**

---

#### Page 2: Layer 1  - Multi-Modal Storage

**Layer Description:** "Where your agent retrieves data from  - vectors for semantic search, graphs for relationships, warehouses for analytics."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| Vector Database | Do you have a vector database? | Pinecone, Weaviate, Chroma, Milvus, Azure AI Search, Qdrant, pgvector, Other, None | CRITICAL  - Agents can't do semantic search |
| Data Warehouse | Do you have a data warehouse? | Snowflake, Databricks, BigQuery, Redshift, Synapse, Other, None, Not Needed | MEDIUM  - May be covered by context question |
| Graph Database | Do you have a graph database? | Neo4j, Amazon Neptune, TigerGraph, Other, None, Not Needed | MEDIUM  - Only if relationship queries needed |
| Data Quality | Do you have data quality tooling? | Great Expectations, dbt tests, Monte Carlo, Soda, Other, None | HIGH  - Garbage in, garbage out |

**Visual:** Show Layer 1 box filling in as user selects

---

#### Page 3: Layer 2  - Real-Time Data Fabric

**Layer Description:** "How your agent data stays fresh  - streaming changes in real-time instead of waiting for batch updates."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| CDC (Change Data Capture) | Do you have CDC? | Debezium, Fivetran CDC, Airbyte CDC, AWS DMS, Azure CDC, Other, None | CRITICAL  - Agents see stale data |
| Stream Processing | Do you have stream processing? | Kafka, Confluent, Amazon Kinesis, Azure Event Hubs, Pulsar, Other, None | HIGH  - No real-time transformation |
| Event Bus | Do you have an event bus? | Kafka, RabbitMQ, Amazon SNS/SQS, Azure Service Bus, Other, None, Not Needed | MEDIUM  - Only if microservices |

**Visual:** Show Layer 2 box filling in

---

#### Page 4: Layer 3  - Universal Semantic Layer

**Layer Description:** "How agents understand business language - translating natural queries (e.g., 'show me high-risk accounts', 'find overdue orders') into actual database queries."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| Semantic Platform | Do you have a semantic layer? | Cube, Looker, dbt Semantic Layer, AtScale, Other, None | CRITICAL  - Agents can't translate NL to queries |
| Data Catalog | Do you have a data catalog? | Atlan, Collibra, Alation, DataHub, Azure Purview, OpenMetadata, Other, None | HIGH  - Agents don't know what data exists |
| Business Glossary | Do you have a business glossary? | Collibra, Atlan, Custom, Integrated in catalog, None | MEDIUM  - Inconsistent terminology |
| Entity Resolution | Do you have entity resolution? | Zingg, Senzing, Tamr, Custom, None, Not Needed | HIGH  - Only if multiple data sources |

**Visual:** Show Layer 3 box filling in

---

#### Page 5: Layer 4  - Intelligence Orchestration

**Layer Description:** "The 'brain' that coordinates retrieval and generation  - RAG frameworks, LLMs, embeddings, caching."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| RAG Framework | Do you have a RAG framework? | LangChain, LlamaIndex, Haystack, Custom, None | CRITICAL  - No retrieval orchestration |
| LLM Access | Do you have LLM access? | OpenAI, Azure OpenAI, Anthropic, Google Vertex AI, AWS Bedrock, Self-hosted, None | CRITICAL  - No generation capability |
| Embedding Models | Do you have embedding models? | OpenAI Ada, Cohere, Sentence Transformers, Custom, Included with LLM | CRITICAL  - No semantic understanding |
| Semantic Cache | Do you have caching for LLM calls? | Redis, GPTCache, Custom, None | MEDIUM  - Cost + latency issues at scale |
| Reranking | Do you have reranking? | Cohere Rerank, Custom, None | MEDIUM  - Retrieval quality |

**Visual:** Show Layer 4 box filling in

---

#### Page 6: Layer 5  - Agent-Aware Governance

**Layer Description:** "How you control what agents can access and track what they do  - the foundation of trust."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| Access Control | What access control do you have? | OPA (Open Policy Agent), Styra DAS, Custom ABAC, RBAC only (IAM), None | CRITICAL  - Agents have unconstrained access |
| Audit Logging | Do you have comprehensive audit logging? | Splunk, Datadog, ELK Stack, CloudWatch/Azure Monitor, Custom, Basic logs only, None | CRITICAL  - No accountability |
| Secrets Management | Do you have secrets management? | HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, GCP Secret Manager, Other, None | HIGH  - Credentials at risk |
| Data Masking | Do you have data masking/tokenization? | Protegrity, Delphix, Privacera, Custom, None, Not Needed | CRITICAL for regulated industries - Sensitive data exposure |

**Visual:** Show Layer 5 box filling in (highlighted for regulated industries: Healthcare/PHI, Financial/CHD, Public Sector/CUI)

---

#### Page 7: Layer 6  - Observability & Feedback

**Layer Description:** "How you monitor agent behavior, capture feedback, and enable continuous improvement."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| LLM Observability | Do you have LLM-specific observability? | LangSmith, Weights & Biases, Arize AI, Helicone, WhyLabs, Other, None | HIGH  - Can't debug agent behavior |
| APM | Do you have application monitoring? | Datadog, New Relic, Dynatrace, Splunk, Grafana, Other, None | MEDIUM  - System blind spots |
| Feedback Collection | Do you collect user feedback? | Custom feedback UI, Integrated in app, Third-party tool, None | MEDIUM  - Can't improve over time |
| A/B Testing | Do you have A/B testing capability? | LaunchDarkly, Split, Custom, None | LOW  - Optimization |

**Visual:** Show Layer 6 box filling in

---

#### Page 8: Layer 7  - Self-Service Data Products

**Layer Description:** "How agents are exposed as products  - orchestration, APIs, and human-in-the-loop interfaces."

| Component | Question | Options | Impact If Missing |
|-----------|----------|---------|-------------------|
| Workflow Orchestration | Do you have workflow orchestration? | Airflow, Temporal, Prefect, Dagster, Step Functions, Azure Logic Apps, Other, None | HIGH  - Can't coordinate complex workflows |
| API Gateway | Do you have an API gateway? | Kong, AWS API Gateway, Azure API Management, Apigee, Other, None | MEDIUM  - No controlled exposure |
| HITL Platform | Do you have human-in-the-loop capability? | Custom approval workflows, Integrated in app, Third-party, None | CRITICAL for high-stakes  - Unsafe autonomy |
| Rate Limiting | Do you have rate limiting? | Built into gateway, Custom, None | MEDIUM  - Usage control |

**Visual:** Show Layer 7 box filling in

---

### Step 5: Interactive Stack Builder (Real-Time Selection)

This is the **core interactive experience**  - users don't just see gaps, they **build their stack in real-time** by selecting products.

---

#### Layout: Split Screen Interface

```
┌─────────────────────────────────────┬─────────────────────────────────────┐
│                                     │                                     │
│     LIVE STACK VISUALIZATION        │       GAP SELECTOR PANEL            │
│     (Updates as user selects)       │       (Recommendations + Selection) │
│                                     │                                     │
└─────────────────────────────────────┴─────────────────────────────────────┘
│                     LIVE METRICS BAR (Budget, Timeline, Readiness)        │
└───────────────────────────────────────────────────────────────────────────┘
```

---

#### Left Panel: Live Stack Visualization

The stack diagram updates **in real-time** as users make selections:

```
YOUR AI AGENT STACK                               Progress: 4/7 Layers ████░░░
────────────────────────────────────────────────────────────────────────────────

┌───────────────────────────────────────────────────────────────────────────┐
│  L7: Self-Service Data Products                                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │Orchestration│  │ API Gateway │  │    HITL     │  │Rate Limiting│      │
│  │  Temporal   │  │    Kong     │  │  ⚠️ SELECT  │  │  Via Kong   │      │
│  │     ✅      │  │     ✅      │  │             │  │     ✅      │      │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │
├───────────────────────────────────────────────────────────────────────────┤
│  L6: Observability & Feedback                                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │LLM Observab.│  │     APM     │  │  Feedback   │  │ A/B Testing │      │
│  │  LangSmith  │  │   Datadog   │  │   Custom    │  │ (Optional)  │      │
│  │     ✅      │  │     ✅      │  │     ✅      │  │     ⬜      │      │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │
├───────────────────────────────────────────────────────────────────────────┤
│  L5: Agent-Aware Governance                                  ⭐ PRIORITY  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │    ABAC     │  │Audit Logging│  │   Secrets   │  │Data Masking │      │
│  │  ❌ SELECT  │  │  ❌ SELECT  │  │Azure KeyVlt │  │  ❌ SELECT  │      │
│  │             │  │             │  │     ✅      │  │  REQUIRED   │      │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │
├───────────────────────────────────────────────────────────────────────────┤
│  L4: Intelligence Orchestration                                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │RAG Framework│  │ LLM Access  │  │ Embeddings  │  │   Cache     │      │
│  │  LangChain  │  │Azure OpenAI │  │Azure OpenAI │  │ (Optional)  │      │
│  │     ✅      │  │     ✅      │  │     ✅      │  │     ⬜      │      │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │
├───────────────────────────────────────────────────────────────────────────┤
│  ... L3, L2, L1 (same pattern) ...                                        │
└───────────────────────────────────────────────────────────────────────────┘
```

**Visual States:**
- ✅ Green checkmark: Component covered (from inventory OR user selection)
- ❌ Red "SELECT": Critical gap  - user must select a product
- ⚠️ Yellow "SELECT": Recommended gap  - user should select
- ⬜ Gray: Optional  - user can skip
- ⭐ PRIORITY badge: Layer should be addressed first (based on industry)

**Click Interaction:**
- Clicking any component box opens the selection panel on the right
- Selected products animate into place with the product name
- Stack "fills up" visually as selections are made
- Budget and timeline update immediately

---

#### Right Panel: Product Selection (Dynamic)

When user clicks a gap, the right panel shows **selectable product recommendations**:

```
┌───────────────────────────────────────────────────────────────────────────┐
│ SELECT: ABAC Policy Engine                                      Layer 5   │
│ ───────────────────────────────────────────────────────────────────────── │
│ Severity: 🔴 CRITICAL                                                     │
│ "Without ABAC, agents have unconstrained access to all data"              │
│                                                                           │
│ YOUR CONTEXT: Healthcare | Growth ($150-250K) | Azure                     │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │ ○ RECOMMENDED                                                       │  │
│  │ ┌─────────────────────────────────────────────────────────────────┐ │  │
│  │ │ Styra DAS                                         $15-25K/year  │ │  │
│  │ │ ✓ Built on OPA   ✓ Healthcare customers   ✓ Azure integration   │ │  │
│  │ │ ✓ Visual policy editor   ✓ Audit trails   ✓ SOC2 compliant     │ │  │
│  │ │                                                                 │ │  │
│  │ │ "Managed OPA with enterprise features. Best for teams          │ │  │
│  │ │  without deep policy expertise."                               │ │  │
│  │ │                                                  [SELECT ✓]     │ │  │
│  │ └─────────────────────────────────────────────────────────────────┘ │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
│                                                                           │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │ ○ BUDGET-FRIENDLY                                                   │  │
│  │ ┌─────────────────────────────────────────────────────────────────┐ │  │
│  │ │ OPA (Open Policy Agent)                           $0 (OSS)      │ │  │
│  │ │ ✓ Free & open-source   ✓ Powerful   ⚠️ Requires expertise      │ │  │
│  │ │ ✓ Large community   ✓ Flexible   ⚠️ Self-managed               │ │  │
│  │ │                                                                 │ │  │
│  │ │ "Industry standard. Requires engineering investment to         │ │  │
│  │ │  build management UI and integrate."                           │ │  │
│  │ │                                                  [SELECT ✓]     │ │  │
│  │ └─────────────────────────────────────────────────────────────────┘ │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
│                                                                           │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │ ○ ENTERPRISE                                                        │  │
│  │ ┌─────────────────────────────────────────────────────────────────┐ │  │
│  │ │ Styra Enterprise + PlainID                        $40-60K/year  │ │  │
│  │ │ ✓ Full ABAC suite   ✓ Identity integration   ✓ On-prem option  │ │  │
│  │ │                                                  [SELECT ✓]     │ │  │
│  │ └─────────────────────────────────────────────────────────────────┘ │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
│                                                                           │
│ ───────────────────────────────────────────────────────────────────────── │
│ [Skip for now]                       [Learn more in Vendor Advisor →]     │
└───────────────────────────────────────────────────────────────────────────┘
```

**Selection Behavior:**
1. User clicks [SELECT ✓] on a product
2. Product animates into the stack visualization on the left
3. Component box turns green with ✅ and shows product name
4. Budget/timeline metrics update immediately in the bottom bar
5. Panel auto-advances to the next priority gap
6. Progress bar updates

---

#### Bottom Bar: Live Metrics (Real-Time Updates)

```
┌───────────────────────────────────────────────────────────────────────────┐
│  STACK COVERAGE         ESTIMATED BUDGET          IMPLEMENTATION TIME     │
│  ████████████░░░        $127,000 - $185,000       10-14 weeks             │
│  5/7 Layers (71%)       ↑ $23K from selections    ↑ 2 weeks from L5       │
│                                                                           │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                                 │
│  │  3 Gaps  │  │  2 Gaps  │  │  1 Gap   │   [Download Report]   [Reset]   │
│  │ CRITICAL │  │   HIGH   │  │ OPTIONAL │                                 │
│  └──────────┘  └──────────┘  └──────────┘                                 │
└───────────────────────────────────────────────────────────────────────────┘
```

**Live Updates on Every Selection:**
- Budget recalculates (shows delta: "↑ $23K from selections")
- Timeline adjusts based on layer dependencies
- Gap counters decrease as selections are made
- Coverage percentage increases
- "Download Report" becomes more prominent as stack completes

---

#### Guided Flow: Priority-Based Navigation

The tool guides users through gaps in **priority order** based on their industry:

**Priority Flow by Industry:**

| Step | Healthcare | Financial Services | Manufacturing | Retail | Public Sector |
|------|------------|-------------------|---------------|--------|---------------|
| 1 | ABAC (HIPAA) | ABAC (PCI-DSS) | ABAC (CMMC) | ABAC (GDPR) | ABAC (FedRAMP) |
| 2 | Audit Logging | Audit (SOX) | Change Mgmt | Consent Mgmt | Audit (FISMA) |
| 3 | Data Masking | Tokenization | Data Class. | Data Masking | Data Class. |
| 4 | LLM Observ. | Fair Lending | Export Ctrl | Privacy | Cont. Monitoring |
| 5 | LLM (BAA) | LLM (SOC2) | LLM (ITAR) | LLM (GDPR) | LLM (FedRAMP) |
| 6 | HITL (Clinical) | HITL (Credit) | HITL (Quality) | HITL (Orders) | HITL (Decisions) |

**Healthcare Example:**
```
Step 1 → L5: ABAC Policy Engine (CRITICAL for HIPAA)
Step 2 → L5: Audit Logging (CRITICAL for HIPAA)
Step 3 → L5: Data Masking (CRITICAL for PHI)
Step 4 → L6: LLM Observability (Required for audit)
Step 5 → L4: LLM Access (Must have BAA - Azure OpenAI only)
Step 6 → L7: HITL Platform (Required for clinical decisions)
... remaining gaps in priority order
```

**Progress Indicator:**
```
┌───────────────────────────────────────────────────────────────────────────┐
│  BUILDING YOUR STACK                                                      │
│  Step 3 of 8: Data Masking                                                │
│  ████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  37%    │
│                                                                           │
│  [← Back to Audit Logging]                        [Skip to Summary →]     │
└───────────────────────────────────────────────────────────────────────────┘
```

---

#### Quick Actions

**"Use Recommended Stack" One-Click Button:**
```
┌───────────────────────────────────────────────────────────────────────────┐
│  Want the fast path?                                                      │
│                                                                           │
│  [🚀 Use Recommended {Industry} Stack]                                    │
│                                                                           │
│  This will select the most common products for {Industry} + {Cloud} +     │
│  {Budget} tier. You can customize any selection after.                    │
│                                                                           │
│  {Industry-specific products listed dynamically}                          │
│  Estimated: ${cost} | {weeks} weeks                                       │
└───────────────────────────────────────────────────────────────────────────┘
```

**Industry-Specific Defaults:**
| Industry | Key Products | Compliance Focus |
|----------|--------------|------------------|
| Healthcare | Azure OpenAI (BAA), Styra DAS, Datadog | HIPAA, BAA required |
| Financial | Azure OpenAI (SOC2), OPA, Splunk | PCI-DSS, SOX audit |
| Manufacturing | Self-hosted LLM, OPA, Grafana | CMMC, ITAR (if defense) |
| Retail | OpenAI, OneTrust, Datadog | GDPR, CCPA consent |
| Public Sector | Azure OpenAI (FedRAMP), AWS Verified Perms | FedRAMP, FISMA |

**"I'll use what I have" Toggle:**
For components where user has partial coverage:
```
┌───────────────────────────────────────────────────────────────────────────┐
│ You selected: AWS IAM (RBAC only)                                         │
│                                                                           │
│ ⚠️ AWS IAM provides RBAC but not full ABAC. For regulated industries:     │
│    - RBAC alone is insufficient for sensitive data access control         │
│    - {Compliance} requires attribute-based decisions (user role + data    │
│      type + purpose + time)                                               │
│                                                                           │
│ ○ Keep AWS IAM AND add ABAC layer (Recommended)                           │
│ ○ Replace with full ABAC solution                                         │
│ ○ Keep AWS IAM only (⚠️ Not recommended for regulated industries)         │
│                                                                           │
│                                                          [Continue →]     │
└───────────────────────────────────────────────────────────────────────────┘
```

**Industry-Specific Warning Text:**
- Healthcare: "HIPAA requires attribute-based decisions for PHI access"
- Financial: "PCI-DSS Req 7 requires need-to-know access control for CHD"
- Manufacturing: "CMMC requires access control based on data classification"
- Public Sector: "FedRAMP requires ABAC for CUI access"

---

### Step 6: Stack Summary & Export

After all selections are complete, show the **complete built stack**:

```
┌───────────────────────────────────────────────────────────────────────────┐
│  ✅ YOUR COMPLETE AI AGENT STACK                                          │
│  ─────────────────────────────────────────────────────────────────────── │
│                                                                           │
│  LAYER 7: Self-Service Data Products                                      │
│  ├── Orchestration: Temporal Cloud ........................... $12K/yr   │
│  ├── API Gateway: Kong Enterprise ............................ $15K/yr   │
│  ├── HITL: Custom (Retool) ................................... $3K/yr    │
│  └── Rate Limiting: Included with Kong ....................... $0        │
│                                                                           │
│  LAYER 6: Observability & Feedback                                        │
│  ├── LLM Observability: LangSmith Pro ........................ $6K/yr    │
│  ├── APM: Datadog (with BAA) ................................. $18K/yr   │
│  └── Feedback: Custom ........................................ $0        │
│                                                                           │
│  LAYER 5: Agent-Aware Governance                                          │
│  ├── ABAC: Styra DAS ......................................... $20K/yr   │
│  ├── Audit Logging: Datadog (shared with APM) ................ incl.     │
│  ├── Secrets: Azure Key Vault ................................ $2K/yr    │
│  └── Data Masking: Privacera ................................. $25K/yr   │
│                                                                           │
│  LAYER 4: Intelligence Orchestration                                      │
│  ├── RAG Framework: LangChain ................................ $0 (OSS)  │
│  ├── LLM Access: Azure OpenAI ................................ $36K/yr   │
│  ├── Embeddings: Azure OpenAI (included) ..................... incl.     │
│  └── Cache: Skipped ..........................................  -         │
│                                                                           │
│  LAYER 3: Universal Semantic Layer                                        │
│  ├── Semantic Platform: Cube Cloud Pro ....................... $15K/yr   │
│  └── Data Catalog: Atlan ..................................... $30K/yr   │
│                                                                           │
│  LAYER 2: Real-Time Data Fabric                                           │
│  ├── CDC: Fivetran ........................................... $18K/yr   │
│  └── Streaming: Confluent Cloud .............................. $24K/yr   │
│                                                                           │
│  LAYER 1: Multi-Modal Storage (Already Had)                               │
│  ├── Vector DB: Pinecone ..................................... existing  │
│  ├── Warehouse: Snowflake .................................... existing  │
│  └── Data Quality: Great Expectations ........................ existing  │
│                                                                           │
│  ─────────────────────────────────────────────────────────────────────── │
│  TOTAL ANNUAL COST (new): $199,000                                        │
│  IMPLEMENTATION TIMELINE: 12-14 weeks                                     │
│  ─────────────────────────────────────────────────────────────────────── │
│                                                                           │
│  [📄 Download PDF Report]  [📊 Export to Excel]  [🔗 Share Link]         │
│                                                                           │
│  ─────────────────────────────────────────────────────────────────────── │
│  NEXT STEPS:                                                              │
│  • Use Vendor Advisor to deep-dive any product before purchasing          │
│  • Take INPACT Assessment to measure your current readiness baseline     │
│  • Use Implementation Guide for week-by-week build plan                   │
│  • Schedule a consultation to review your stack with an expert            │
└───────────────────────────────────────────────────────────────────────────┘
```

---

### Step 7: PDF Report (With User Selections)

The PDF report now includes the **user's specific product selections**, not just generic recommendations.

**Report Contents:**

1. **Cover Page** (1 page)
   - Organization name and date
   - Industry and compliance context
   - Stack completion: "7/7 Layers Complete"
   - Total investment summary

2. **Executive Summary** (1 page)
   - Visual stack diagram with all selected products
   - Before/after comparison (what you had vs. what you built)
   - Total annual investment breakdown
   - Implementation timeline overview

3. **Your Selected Stack** (2 pages)  - NEW
   Complete list of every selected product with:
   - Product name and vendor
   - Annual cost (and one-time costs if any)
   - Why it was recommended for your context
   - Key features relevant to your industry
   - Integration notes with other products you selected
   - Link to vendor website

4. **Layer-by-Layer Implementation Guide** (7 pages)
   For each layer:
   - What you had before (from inventory)
   - What you selected (from builder)
   - Implementation sequence within the layer
   - Dependencies on other layers
   - Estimated timeline for this layer
   - Key configuration considerations

4. **Prioritized Build Order** (1 page)
   - Industry-specific sequence
   - Dependencies explained
   - Week-by-week timeline
   - Quick wins vs. foundational investments

5. **Budget Summary** (1 page)
   - By layer breakdown
   - By tier (Starter, Growth, Enterprise)
   - Monthly ongoing costs
   - ROI considerations

6. **Next Steps** (1 page)
   - "Use Vendor Advisor to select specific products"
   - "Take the INPACT Assessment to measure readiness"
   - Link to book chapters by gap area
   - Consultation CTA

**PDF footer:**
```
From "Trust Before Intelligence" by Ram Katamaraja
```

---

## Gap Analysis Logic

### Severity Calculation

```
CRITICAL (Red)  - Agents cannot function without this:
- No vector database (L1)
- No RAG framework (L4)
- No LLM access (L4)
- No ABAC (L5) + regulated industry
- No audit logging (L5) + compliance requirements
- No HITL (L7) + high-stakes decisions

HIGH (Orange)  - Significant limitation or risk:
- No CDC (L2)
- No semantic layer (L3)
- No data catalog (L3)
- No secrets management (L5)
- No LLM observability (L6)

MEDIUM (Yellow)  - Reduced capability:
- No graph database + relationship queries needed
- No streaming (L2)
- No caching (L4)
- No APM (L6)
- No orchestration (L7)

LOW (Blue)  - Nice to have:
- No reranking (L4)
- No A/B testing (L6)
- No rate limiting (L7)
```

### Industry Modifiers

| Industry | Layer 5 Priority | Special Requirements |
|----------|------------------|---------------------|
| Healthcare | CRITICAL | Data masking required, BAA for LLMs |
| Financial Services | CRITICAL | SOX audit trails, PCI for payments |
| Government | CRITICAL | FedRAMP, air-gap considerations |
| Retail | MEDIUM | PCI if payments, otherwise standard |
| Technology | MEDIUM | SOC2 for enterprise sales |

### Build Order Logic

```python
def calculate_build_order(industry, gaps, compliance):
    order = []

    # Healthcare always starts with governance
    if industry == "healthcare" or "HIPAA" in compliance:
        order = ["L5", "L6", "L1", "L4", "L3", "L7", "L2"]

    # Financial services: governance + audit
    elif industry == "financial" or "SOX" in compliance:
        order = ["L5", "L6", "L1", "L4", "L3", "L2", "L7"]

    # Government: security first
    elif industry == "government" or "FedRAMP" in compliance:
        order = ["L5", "L1", "L4", "L6", "L3", "L7", "L2"]

    # Default: safety first, then foundation
    else:
        order = ["L5", "L1", "L4", "L3", "L6", "L2", "L7"]

    # Remove layers that are already covered
    return [layer for layer in order if layer in gaps]
```

---

## Gap Recommendations Matrix

When a gap is identified, the tool provides specific product recommendations based on **budget tier**, **cloud platform**, and **compliance requirements**.

---

### Layer 1: Multi-Modal Storage  - Recommendations

#### Vector Database (If Missing)

| Tier | AWS | Azure | GCP | Healthcare (BAA) |
|------|-----|-------|-----|------------------|
| **Starter** | Pinecone (Starter) | Azure AI Search | Pinecone (Starter) | Azure AI Search ✓ |
| **Growth** | Pinecone (Standard), Weaviate Cloud | Azure AI Search, Weaviate Cloud | Pinecone, Vertex AI Vector Search | Pinecone (with BAA) ✓ |
| **Enterprise** | Pinecone (Enterprise), Weaviate Enterprise | Azure AI Search (Enterprise), Weaviate | Vertex AI Vector Search | Azure AI Search ✓, Pinecone Enterprise ✓ |

**Why these recommendations:**
- Pinecone: Fully managed, scales well, offers BAA for healthcare
- Azure AI Search: Native Azure integration, enterprise compliance
- Weaviate: Open-source option, flexible deployment

#### Data Warehouse (If Missing)

| Tier | AWS | Azure | GCP | Healthcare (BAA) |
|------|-----|-------|-----|------------------|
| **Starter** | Redshift Serverless | Azure Synapse Serverless | BigQuery | All have BAA options ✓ |
| **Growth** | Snowflake, Databricks | Snowflake, Databricks, Synapse | Snowflake, BigQuery | Snowflake ✓, Databricks ✓ |
| **Enterprise** | Snowflake Enterprise, Databricks Unity | Snowflake Enterprise, Databricks Unity | Snowflake Enterprise, BigQuery Enterprise | Snowflake Enterprise ✓ |

#### Graph Database (If Missing + Needed)

| Tier | All Platforms | Healthcare |
|------|---------------|------------|
| **Starter** | Neo4j AuraDB Free, Amazon Neptune Serverless | Neo4j AuraDB (with BAA) |
| **Growth** | Neo4j AuraDB Professional, Amazon Neptune | Neo4j AuraDB Professional ✓ |
| **Enterprise** | Neo4j Enterprise, TigerGraph | Neo4j Enterprise ✓ |

#### Data Quality (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | Great Expectations (open-source) + dbt tests | Free, integrates with dbt |
| **Growth** | Monte Carlo, Soda Cloud | Automated monitoring, anomaly detection |
| **Enterprise** | Monte Carlo Enterprise, Collibra DQ | Full lineage, governance integration |

---

### Layer 2: Real-Time Data Fabric  - Recommendations

#### CDC (If Missing)

| Tier | AWS | Azure | GCP | Healthcare |
|------|-----|-------|-----|------------|
| **Starter** | Debezium (self-managed), AWS DMS | Azure CDC, Debezium | Datastream | All options work ✓ |
| **Growth** | Fivetran CDC, Airbyte Cloud | Fivetran CDC, Azure CDC | Fivetran CDC, Datastream | Fivetran (with BAA) ✓ |
| **Enterprise** | Confluent CDC, Fivetran Enterprise | Confluent CDC, Fivetran | Confluent CDC | Fivetran Enterprise ✓ |

#### Stream Processing (If Missing)

| Tier | AWS | Azure | GCP | Healthcare |
|------|-----|-------|-----|------------|
| **Starter** | Amazon Kinesis | Azure Event Hubs | Pub/Sub | All have BAA ✓ |
| **Growth** | Amazon MSK, Confluent Cloud | Confluent Cloud, Event Hubs | Confluent Cloud | Confluent Cloud ✓ |
| **Enterprise** | Confluent Enterprise, Amazon MSK | Confluent Enterprise | Confluent Enterprise | Confluent Enterprise ✓ |

---

### Layer 3: Universal Semantic Layer  - Recommendations

#### Semantic Platform (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | Cube Cloud (free tier), dbt Semantic Layer | Modern, developer-friendly |
| **Growth** | Cube Cloud (Pro), AtScale | Full semantic modeling, caching |
| **Enterprise** | Cube Enterprise, AtScale Enterprise | On-prem options, enterprise support |

#### Data Catalog (If Missing)

| Tier | AWS | Azure | GCP | Healthcare |
|------|-----|-------|-----|------------|
| **Starter** | DataHub (open-source), AWS Glue Catalog | Azure Purview (free tier) | Dataplex | Azure Purview ✓ |
| **Growth** | Atlan, Alation | Atlan, Azure Purview | Atlan, Dataplex | Atlan (with BAA) ✓ |
| **Enterprise** | Collibra, Alation Enterprise | Collibra, Azure Purview Enterprise | Collibra | Collibra ✓ |

---

### Layer 4: Intelligence Orchestration  - Recommendations

#### RAG Framework (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | LangChain + LangServe | Most popular, large community, free |
| **Growth** | LangChain + LangSmith, LlamaIndex | Adds observability, enterprise features |
| **Enterprise** | Custom framework, LlamaIndex Enterprise | Full control, dedicated support |

#### LLM Access (If Missing)

| Tier | General | Healthcare (BAA Required) |
|------|---------|---------------------------|
| **Starter** | OpenAI API | Azure OpenAI ✓ (only BAA option) |
| **Growth** | OpenAI, Anthropic | Azure OpenAI ✓, AWS Bedrock (Anthropic) ✓ |
| **Enterprise** | Azure OpenAI, AWS Bedrock, Google Vertex AI | Azure OpenAI ✓, AWS Bedrock ✓ |

**CRITICAL by Industry:**
- Healthcare: Only Azure OpenAI and AWS Bedrock offer BAAs. OpenAI direct does NOT.
- Financial: Require SOC2 Type II attestation. Azure OpenAI, OpenAI Enterprise, AWS Bedrock qualify.
- Public Sector: FedRAMP authorization required. Azure OpenAI (FedRAMP High) is primary option.

#### Semantic Cache (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | Redis (open-source), GPTCache | Free, simple setup |
| **Growth** | Redis Enterprise, Momento | Managed, scalable |
| **Enterprise** | Redis Enterprise Cloud | Enterprise SLAs, compliance |

---

### Layer 5: Agent-Aware Governance  - Recommendations

#### ABAC Policy Engine (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | OPA (Open Policy Agent) | Free, powerful, widely adopted |
| **Growth** | Styra DAS, OPA + custom UI | Managed policies, audit trails |
| **Enterprise** | Styra Enterprise, PlainID | Full ABAC suite, enterprise features |

**CRITICAL for Regulated Industries:** ABAC is non-negotiable for sensitive data access control.
- Healthcare: RBAC alone insufficient for PHI (HIPAA requires purpose-of-use)
- Financial: PCI-DSS Req 7 requires need-to-know for CHD
- Public Sector: FedRAMP requires attribute-based access for CUI

#### Audit Logging (If Missing)

| Tier | AWS | Azure | GCP | Healthcare |
|------|-----|-------|-----|------------|
| **Starter** | CloudWatch Logs | Azure Monitor | Cloud Logging | All work, ensure 6-year retention ✓ |
| **Growth** | Datadog, Splunk Cloud | Datadog, Azure Sentinel | Datadog | Datadog (with BAA) ✓ |
| **Enterprise** | Splunk Enterprise, Datadog | Splunk, Azure Sentinel | Splunk, Chronicle | Splunk Enterprise ✓ |

**CRITICAL for Regulated Industries:** Immutable logs required.
- Healthcare: 6-year retention, 100% PHI access tracking
- Financial: 1-year minimum (PCI-DSS), 7-year for SOX
- Public Sector: Per NIST 800-53 AU controls, continuous monitoring

#### Secrets Management (If Missing)

| Tier | AWS | Azure | GCP |
|------|-----|-------|-----|
| **Starter** | AWS Secrets Manager | Azure Key Vault | Secret Manager |
| **Growth** | HashiCorp Vault Cloud | HashiCorp Vault, Azure Key Vault | HashiCorp Vault |
| **Enterprise** | HashiCorp Vault Enterprise | HashiCorp Vault Enterprise | HashiCorp Vault Enterprise |

#### Data Masking / Tokenization (If Missing + Regulated)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | Custom masking functions, Presidio (open-source) | Free, basic PII detection |
| **Growth** | Privacera, Immuta | Dynamic masking, policy-based |
| **Enterprise** | Protegrity, Delphix | Enterprise-grade tokenization |

**CRITICAL for Regulated Industries:** Data masking/tokenization required for sensitive data.
- Healthcare: PHI masking mandatory (HIPAA)
- Financial: CHD tokenization mandatory (PCI-DSS Req 3)
- Retail: Customer PII masking for GDPR compliance

---

### Layer 6: Observability & Feedback  - Recommendations

#### LLM Observability (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | LangSmith (free tier), Helicone | Free tiers available, LLM-specific |
| **Growth** | LangSmith Pro, Weights & Biases, Arize AI | Full tracing, evaluation |
| **Enterprise** | LangSmith Enterprise, Arize Enterprise | On-prem options, enterprise support |

#### APM (If Missing)

| Tier | AWS | Azure | GCP |
|------|-----|-------|-----|
| **Starter** | CloudWatch, X-Ray | Azure Monitor, Application Insights | Cloud Monitoring |
| **Growth** | Datadog, New Relic | Datadog, Dynatrace | Datadog |
| **Enterprise** | Datadog Enterprise, Dynatrace | Dynatrace, Splunk | Datadog Enterprise |

---

### Layer 7: Self-Service Data Products  - Recommendations

#### Workflow Orchestration (If Missing)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | Airflow (managed), Prefect Cloud (free) | Free tiers, widely adopted |
| **Growth** | Temporal Cloud, Dagster Cloud | Better for long-running workflows |
| **Enterprise** | Temporal Enterprise, Airflow (self-managed) | Full control, enterprise features |

#### API Gateway (If Missing)

| Tier | AWS | Azure | GCP |
|------|-----|-------|-----|
| **Starter** | AWS API Gateway | Azure API Management (Consumption) | Apigee X (pay-as-you-go) |
| **Growth** | AWS API Gateway, Kong | Azure API Management, Kong | Apigee, Kong |
| **Enterprise** | Kong Enterprise | Kong Enterprise, Azure APIM Premium | Apigee Enterprise |

#### HITL Platform (If Missing + High-Stakes)

| Tier | Recommendation | Why |
|------|----------------|-----|
| **Starter** | Custom approval UI, Retool | Low-code, quick to build |
| **Growth** | Custom + workflow integration | Integrated with Temporal/Airflow |
| **Enterprise** | Custom enterprise platform | Full audit, compliance features |

**CRITICAL for High-Stakes Decisions:** HITL is mandatory. No exceptions.
- Healthcare: Clinical decisions require clinician approval
- Financial: Credit decisions require human reviewer (Fair Lending)
- Manufacturing: Quality holds require QA manager approval
- Public Sector: Benefit determinations require human adjudication

---

### Quick Reference: Industry-Specific Stacks

**Select your industry for the recommended stack by tier.**

#### Healthcare Stack (HIPAA-Compliant)

For healthcare organizations:

| Layer | Component | Starter | Growth | Enterprise |
|-------|-----------|---------|--------|------------|
| L1 | Vector DB | Azure AI Search | Pinecone (BAA) | Pinecone Enterprise |
| L1 | Warehouse | Snowflake | Snowflake | Snowflake Enterprise |
| L2 | CDC | Fivetran | Fivetran (BAA) | Fivetran Enterprise |
| L2 | Streaming | Azure Event Hubs | Confluent Cloud | Confluent Enterprise |
| L3 | Semantic | Cube Cloud | Cube Pro | Cube Enterprise |
| L3 | Catalog | Azure Purview | Atlan (BAA) | Collibra |
| L4 | RAG | LangChain | LangChain + LangSmith | Custom |
| L4 | LLM | Azure OpenAI ✓ | Azure OpenAI ✓ | Azure OpenAI ✓ |
| L5 | ABAC | OPA | Styra DAS | Styra Enterprise |
| L5 | Audit | Azure Monitor | Datadog (BAA) | Splunk Enterprise |
| L5 | Secrets | Azure Key Vault | HashiCorp Vault | Vault Enterprise |
| L5 | Masking | Presidio | Privacera | Protegrity |
| L6 | LLM Obs | LangSmith | LangSmith Pro | LangSmith Enterprise |
| L6 | APM | Azure Monitor | Datadog | Datadog Enterprise |
| L7 | Orchestration | Airflow | Temporal Cloud | Temporal Enterprise |
| L7 | HITL | Custom | Custom + Temporal | Enterprise Platform |

#### Financial Services Stack (PCI-DSS/SOX Compliant)

For financial services organizations:

| Layer | Component | Starter | Growth | Enterprise |
|-------|-----------|---------|--------|------------|
| L1 | Vector DB | Azure AI Search | Pinecone (SOC2) | Pinecone Enterprise |
| L1 | Warehouse | Snowflake | Snowflake (PCI) | Snowflake Enterprise |
| L2 | CDC | Fivetran | Fivetran (SOC2) | Fivetran Enterprise |
| L3 | Semantic | Cube Cloud | Cube Pro | Cube Enterprise |
| L4 | LLM | Azure OpenAI ✓ | Azure OpenAI ✓ | Azure OpenAI ✓ |
| L5 | ABAC | OPA | OPA + Styra | Styra Enterprise |
| L5 | Audit | Splunk Cloud | Splunk Enterprise | Splunk + SIEM |
| L5 | Tokenization | Custom | Protegrity | Protegrity Enterprise |
| L6 | APM | Datadog | Datadog | Datadog Enterprise |
| L7 | HITL | Custom | Custom + Workflow | Enterprise Platform |

#### Public Sector Stack (FedRAMP Compliant)

For public sector organizations:

| Layer | Component | Starter | Growth | Enterprise |
|-------|-----------|---------|--------|------------|
| L1 | Vector DB | Azure AI Search (FedRAMP) | Azure AI Search | Azure AI Search |
| L1 | Warehouse | Snowflake Gov | Snowflake Gov | Snowflake Gov |
| L2 | CDC | AWS DMS (GovCloud) | AWS DMS | AWS DMS |
| L3 | Semantic | dbt Cloud | dbt Cloud | dbt Enterprise |
| L4 | LLM | Azure OpenAI (FedRAMP) ✓ | Azure OpenAI ✓ | Azure OpenAI ✓ |
| L5 | ABAC | AWS Verified Permissions | OPA + Styra | Styra Enterprise |
| L5 | Audit | AWS CloudWatch | Splunk GovCloud | Splunk GovCloud |
| L6 | APM | AWS X-Ray | Datadog Gov | Datadog Gov |
| L7 | HITL | Custom | Custom + Workflow | Enterprise Platform |

---

## Budget Calculation

### Per-Layer Budget Ranges

| Layer | Starter | Growth | Enterprise |
|-------|---------|--------|------------|
| L1 | $5-10K | $20-40K | $50-100K |
| L2 | $3-8K | $15-30K | $40-80K |
| L3 | $5-12K | $25-50K | $60-120K |
| L4 | $5-15K | $30-60K | $80-200K |
| L5 | $3-8K | $15-35K | $40-100K |
| L6 | $2-6K | $10-25K | $30-70K |
| L7 | $2-5K | $10-25K | $30-60K |
| **Total** | **$25-64K** | **$125-265K** | **$330-730K** |

### Calculation Logic

```python
def calculate_budget(gaps, tier, industry):
    budget_ranges = {
        "Starter": {...},
        "Growth": {...},
        "Enterprise": {...}
    }

    total_min = 0
    total_max = 0

    for layer in gaps:
        range = budget_ranges[tier][layer]
        total_min += range["min"]
        total_max += range["max"]

    # Industry compliance modifier
    compliance_modifiers = {
        "healthcare": 1.15,     # HIPAA overhead
        "financial": 1.20,     # PCI-DSS + SOX overhead
        "public_sector": 1.25, # FedRAMP overhead
        "manufacturing": 1.10, # CMMC overhead (if defense)
        "retail": 1.05,        # GDPR overhead
        "technology": 1.00     # No compliance overhead
    }

    modifier = compliance_modifiers.get(industry, 1.0)
    total_min *= modifier
    total_max *= modifier

    return (total_min, total_max)
```

---

## Technical Requirements

### Frontend
- Responsive design (mobile-friendly)
- Progress auto-save (localStorage + server)
- Accessible (WCAG 2.1 AA)
- Interactive stack visualization
- Real-time gap highlighting

### Backend
- Store assessment responses
- Gap analysis calculation
- Build order algorithm
- Budget calculation
- PDF generation
- Email delivery

### Integrations
- Email marketing (follow-up sequence)
- CRM (lead capture)
- Analytics (conversion tracking)
- Link to Vendor Advisor chatbot

---

## Follow-up Email Sequence

| Day | Email | Content |
|-----|-------|---------|
| 0 | Results delivered | PDF attachment + top 3 gaps summary |
| 3 | Deep dive on #1 gap | Detailed explanation of most critical gap |
| 7 | Build order rationale | Why this sequence matters for their industry |
| 14 | Echo case study | How Echo filled similar gaps |
| 21 | Vendor comparison | Top vendors for their gaps (teaser for Vendor Advisor) |
| 30 | Consultation offer | "Ready to start building?" |

---

## Synergy with Other Tools

### Integration Points

| Tool | Relationship |
|------|--------------|
| **INPACT Assessment** | "Not sure about readiness? Take the INPACT Assessment first" |
| **Vendor Advisor** | "Now select specific products for each gap" → Deep link with context |
| **Compliance Navigator** | "Need compliance details?" → Link based on detected requirements |
| **Implementation Guide** | "Ready to build?" → Week-by-week guidance |

### Data Sharing

Stack Builder results can pre-populate:
- Vendor Advisor context (industry, budget, gaps)
- Implementation Guide starting point
- Compliance Navigator requirements

---

## Design Notes

### Brand Colors
- Primary: Teal (from book cover)
- Secondary: White, Dark Gray
- Status colors: Green (covered), Yellow (partial), Red (missing)

### Stack Visualization
- 7 horizontal layers stacked vertically
- Each layer shows status indicator
- Click to expand layer details
- Animated fill as user completes

### Mobile Considerations
- Layers stack vertically
- Single question per screen
- Swipe navigation between layers

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | January 2026 | Initial specification |
| 2.0 | January 2026 | Added interactive stack builder, technical implementation guide |

---

# PART 2: TECHNICAL IMPLEMENTATION GUIDE

> **For AI-Assisted Development (Claude Code, Cursor, Windsurf, etc.)**
>
> This section provides the technical specifications needed to build the Stack Builder tool. It includes data models, API endpoints, component architecture, and implementation algorithms.

---

## Technology Stack (Recommended)

```
Frontend:
- Framework: Next.js 14+ (App Router) or React 18+
- State Management: Zustand or React Context
- Styling: Tailwind CSS
- Animation: Framer Motion
- Charts: Recharts or Chart.js

Backend:
- Runtime: Node.js 18+ or Python 3.11+
- Framework: Next.js API Routes, FastAPI, or Express
- Database: PostgreSQL with Prisma ORM
- PDF Generation: @react-pdf/renderer or Puppeteer
- Email: Resend or SendGrid

Infrastructure:
- Hosting: Vercel, Railway, or AWS
- Database: Supabase, PlanetScale, or RDS
- Analytics: PostHog or Mixpanel
```

---

## Data Models

### 1. Product Catalog (Static Data)

```typescript
// types/product.ts

interface Product {
  id: string;                    // e.g., "pinecone-standard"
  name: string;                  // e.g., "Pinecone"
  vendor: string;                // e.g., "Pinecone Systems"
  layer: LayerId;                // e.g., "L1"
  component: ComponentId;        // e.g., "vector_db"

  // Pricing
  pricing: {
    model: "subscription" | "usage" | "one_time" | "free";
    tiers: {
      starter: PriceRange;
      growth: PriceRange;
      enterprise: PriceRange;
    };
  };

  // Compatibility
  cloudPlatforms: ("aws" | "azure" | "gcp" | "any")[];
  hasBAA: boolean;               // HIPAA Business Associate Agreement
  compliance: string[];          // ["SOC2", "HIPAA", "GDPR"]

  // Recommendations
  recommendedFor: {
    industries: string[];        // ["healthcare", "financial"]
    budgetTiers: BudgetTier[];
    useCases: string[];
  };

  // Display
  description: string;
  shortDescription: string;
  features: string[];
  caveats: string[];             // Warnings like "Requires expertise"
  websiteUrl: string;
  docsUrl: string;

  // Sorting
  popularity: number;            // For default sorting
  isRecommended: boolean;        // Show "Recommended" badge
}

interface PriceRange {
  min: number;
  max: number;
  unit: "year" | "month" | "one_time";
  notes?: string;
}

type LayerId = "L1" | "L2" | "L3" | "L4" | "L5" | "L6" | "L7";
type BudgetTier = "starter" | "growth" | "enterprise";
type ComponentId =
  // L1
  | "vector_db" | "data_warehouse" | "graph_db" | "data_quality"
  // L2
  | "cdc" | "stream_processing" | "event_bus"
  // L3
  | "semantic_platform" | "data_catalog" | "business_glossary" | "entity_resolution"
  // L4
  | "rag_framework" | "llm_access" | "embeddings" | "semantic_cache" | "reranking"
  // L5
  | "abac" | "audit_logging" | "secrets_management" | "data_masking"
  // L6
  | "llm_observability" | "apm" | "feedback_collection" | "ab_testing"
  // L7
  | "workflow_orchestration" | "api_gateway" | "hitl_platform" | "rate_limiting";
```

### 2. Layer & Component Definitions

```typescript
// types/layer.ts

interface Layer {
  id: LayerId;
  name: string;
  shortName: string;
  description: string;
  components: Component[];
  priorityOrder: Record<Industry, number>;  // Lower = higher priority
}

interface Component {
  id: ComponentId;
  name: string;
  description: string;
  required: boolean | RequirementCondition;
  impactIfMissing: Severity;
  impactDescription: string;
}

interface RequirementCondition {
  type: "industry" | "compliance" | "useCase";
  values: string[];
}

type Severity = "critical" | "high" | "medium" | "low" | "optional";
type Industry = "healthcare" | "financial" | "government" | "retail" | "technology" | "other";

// Example data
const LAYERS: Layer[] = [
  {
    id: "L1",
    name: "Multi-Modal Storage",
    shortName: "Storage",
    description: "Where your agent retrieves data from",
    priorityOrder: {
      healthcare: 3,
      financial: 2,
      government: 2,
      retail: 1,
      technology: 1,
      other: 1
    },
    components: [
      {
        id: "vector_db",
        name: "Vector Database",
        description: "Semantic similarity search",
        required: true,
        impactIfMissing: "critical",
        impactDescription: "Agents can't do semantic search"
      },
      // ... more components
    ]
  },
  // ... more layers
];
```

### 3. User Session State

```typescript
// types/session.ts

interface UserSession {
  id: string;
  createdAt: Date;
  updatedAt: Date;

  // Lead info (from Step 2)
  lead: {
    email: string;
    name: string;
    organization: string;
    role: string;
  };

  // Context (from Step 3)
  context: {
    industry: Industry;
    compliance: string[];           // ["HIPAA", "SOC2"]
    sensitiveData: "phi" | "pii" | "financial" | "public";
    expectedUsers: "<100" | "100-1000" | "1000-10000" | "10000+";
    dataVolume: "<1GB" | "1-100GB" | "100GB-1TB" | "1TB+";
    budgetTier: BudgetTier;
    cloudPlatform: "aws" | "azure" | "gcp" | "multi" | "onprem" | "hybrid";
    currentDataPlatform: string;
  };

  // Inventory (from Steps 4-10)
  inventory: Record<ComponentId, InventoryItem>;

  // Selections (from Step 11 - Interactive Builder)
  selections: Record<ComponentId, Selection>;

  // Computed
  gaps: Gap[];
  totalBudget: PriceRange;
  implementationWeeks: { min: number; max: number };
  completionPercentage: number;
}

interface InventoryItem {
  componentId: ComponentId;
  hasExisting: boolean;
  existingProduct: string | null;  // e.g., "Snowflake"
  existingProductId: string | null;
}

interface Selection {
  componentId: ComponentId;
  productId: string;
  product: Product;
  selectedAt: Date;
  isFromInventory: boolean;       // true if user already had it
}

interface Gap {
  componentId: ComponentId;
  layerId: LayerId;
  severity: Severity;
  priorityRank: number;           // Based on industry
  recommendations: Product[];     // Filtered and sorted
}
```

### 4. API Request/Response Types

```typescript
// types/api.ts

// POST /api/sessions - Create new session
interface CreateSessionRequest {
  lead: UserSession["lead"];
}
interface CreateSessionResponse {
  sessionId: string;
}

// PUT /api/sessions/:id/context - Save context
interface SaveContextRequest {
  context: UserSession["context"];
}

// PUT /api/sessions/:id/inventory - Save inventory for a layer
interface SaveInventoryRequest {
  layerId: LayerId;
  items: InventoryItem[];
}

// GET /api/sessions/:id/gaps - Get computed gaps
interface GetGapsResponse {
  gaps: Gap[];
  priorityOrder: ComponentId[];
  totalGapsCount: {
    critical: number;
    high: number;
    medium: number;
    optional: number;
  };
}

// PUT /api/sessions/:id/selections/:componentId - Select a product
interface SelectProductRequest {
  productId: string;
}
interface SelectProductResponse {
  selection: Selection;
  updatedBudget: PriceRange;
  updatedTimeline: { min: number; max: number };
  remainingGaps: number;
  nextGap: Gap | null;
}

// GET /api/sessions/:id/summary - Get final summary
interface GetSummaryResponse {
  session: UserSession;
  stackByLayer: LayerSummary[];
  totalNewCost: PriceRange;
  existingCost: number;
  timeline: { min: number; max: number };
}

// POST /api/sessions/:id/report - Generate PDF
interface GenerateReportRequest {
  format: "pdf" | "excel";
}
interface GenerateReportResponse {
  downloadUrl: string;
}
```

---

## Database Schema

```sql
-- PostgreSQL schema

-- Users/Leads
CREATE TABLE leads (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) NOT NULL UNIQUE,
  name VARCHAR(255) NOT NULL,
  organization VARCHAR(255) NOT NULL,
  role VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Sessions
CREATE TABLE sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  lead_id UUID REFERENCES leads(id),

  -- Context JSON
  context JSONB NOT NULL DEFAULT '{}',

  -- State
  current_step VARCHAR(50) DEFAULT 'context',
  completed_at TIMESTAMP,

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Inventory items (what user already has)
CREATE TABLE inventory_items (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id UUID REFERENCES sessions(id) ON DELETE CASCADE,
  component_id VARCHAR(50) NOT NULL,
  has_existing BOOLEAN DEFAULT FALSE,
  existing_product VARCHAR(255),
  existing_product_id VARCHAR(100),
  created_at TIMESTAMP DEFAULT NOW(),

  UNIQUE(session_id, component_id)
);

-- Product selections (what user chose)
CREATE TABLE selections (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id UUID REFERENCES sessions(id) ON DELETE CASCADE,
  component_id VARCHAR(50) NOT NULL,
  product_id VARCHAR(100) NOT NULL,
  is_from_inventory BOOLEAN DEFAULT FALSE,
  selected_at TIMESTAMP DEFAULT NOW(),

  UNIQUE(session_id, component_id)
);

-- Products catalog (can be in DB or static JSON)
CREATE TABLE products (
  id VARCHAR(100) PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  vendor VARCHAR(255) NOT NULL,
  layer_id VARCHAR(10) NOT NULL,
  component_id VARCHAR(50) NOT NULL,
  pricing JSONB NOT NULL,
  cloud_platforms TEXT[] NOT NULL,
  has_baa BOOLEAN DEFAULT FALSE,
  compliance TEXT[] DEFAULT '{}',
  description TEXT,
  features TEXT[] DEFAULT '{}',
  caveats TEXT[] DEFAULT '{}',
  website_url VARCHAR(500),
  popularity INTEGER DEFAULT 0,
  is_active BOOLEAN DEFAULT TRUE,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Indexes
CREATE INDEX idx_sessions_lead ON sessions(lead_id);
CREATE INDEX idx_inventory_session ON inventory_items(session_id);
CREATE INDEX idx_selections_session ON selections(session_id);
CREATE INDEX idx_products_layer ON products(layer_id);
CREATE INDEX idx_products_component ON products(component_id);
```

---

## API Endpoints

```typescript
// Next.js App Router example: app/api/sessions/route.ts

// POST /api/sessions - Create session
export async function POST(request: Request) {
  const { lead } = await request.json();

  // Upsert lead
  const leadRecord = await prisma.lead.upsert({
    where: { email: lead.email },
    update: { name: lead.name, organization: lead.organization, role: lead.role },
    create: lead
  });

  // Create session
  const session = await prisma.session.create({
    data: { leadId: leadRecord.id }
  });

  return Response.json({ sessionId: session.id });
}

// GET /api/sessions/:id/gaps
export async function GET(
  request: Request,
  { params }: { params: { id: string } }
) {
  const session = await getSessionWithInventory(params.id);
  const gaps = computeGaps(session);
  const priorityOrder = sortGapsByPriority(gaps, session.context.industry);

  return Response.json({
    gaps,
    priorityOrder: priorityOrder.map(g => g.componentId),
    totalGapsCount: countGapsBySeverity(gaps)
  });
}

// PUT /api/sessions/:id/selections/:componentId
export async function PUT(
  request: Request,
  { params }: { params: { id: string; componentId: string } }
) {
  const { productId } = await request.json();
  const product = await getProduct(productId);

  // Save selection
  const selection = await prisma.selection.upsert({
    where: {
      sessionId_componentId: {
        sessionId: params.id,
        componentId: params.componentId
      }
    },
    update: { productId },
    create: {
      sessionId: params.id,
      componentId: params.componentId,
      productId
    }
  });

  // Recompute budget and timeline
  const allSelections = await getSessionSelections(params.id);
  const budget = computeTotalBudget(allSelections);
  const timeline = computeTimeline(allSelections);
  const remainingGaps = await computeRemainingGaps(params.id);

  return Response.json({
    selection: { ...selection, product },
    updatedBudget: budget,
    updatedTimeline: timeline,
    remainingGaps: remainingGaps.length,
    nextGap: remainingGaps[0] || null
  });
}
```

---

## Core Algorithms

### 1. Gap Detection Algorithm

```typescript
// lib/algorithms/gaps.ts

function computeGaps(session: UserSession): Gap[] {
  const gaps: Gap[] = [];

  for (const layer of LAYERS) {
    for (const component of layer.components) {
      const inventoryItem = session.inventory[component.id];
      const selection = session.selections[component.id];

      // Skip if user has it or selected it
      if (inventoryItem?.hasExisting || selection) {
        continue;
      }

      // Check if component is required for this context
      const isRequired = evaluateRequirement(
        component.required,
        session.context
      );

      if (!isRequired && component.impactIfMissing === "optional") {
        continue; // Skip truly optional components
      }

      // Get recommendations for this gap
      const recommendations = getRecommendations(
        component.id,
        session.context
      );

      gaps.push({
        componentId: component.id,
        layerId: layer.id,
        severity: adjustSeverityForContext(
          component.impactIfMissing,
          session.context
        ),
        priorityRank: layer.priorityOrder[session.context.industry],
        recommendations
      });
    }
  }

  return gaps;
}

function evaluateRequirement(
  requirement: boolean | RequirementCondition,
  context: UserSession["context"]
): boolean {
  if (typeof requirement === "boolean") {
    return requirement;
  }

  switch (requirement.type) {
    case "industry":
      return requirement.values.includes(context.industry);
    case "compliance":
      return requirement.values.some(v => context.compliance.includes(v));
    case "useCase":
      return requirement.values.includes(context.sensitiveData);
    default:
      return false;
  }
}

function adjustSeverityForContext(
  baseSeverity: Severity,
  context: UserSession["context"]
): Severity {
  // Healthcare elevates certain gaps to critical
  if (context.industry === "healthcare") {
    if (["data_masking", "abac", "audit_logging", "hitl_platform"].includes(componentId)) {
      return "critical";
    }
  }

  return baseSeverity;
}
```

### 2. Recommendation Filtering & Sorting

```typescript
// lib/algorithms/recommendations.ts

function getRecommendations(
  componentId: ComponentId,
  context: UserSession["context"]
): Product[] {
  // Get all products for this component
  let products = PRODUCTS.filter(p => p.component === componentId);

  // Filter by cloud platform
  products = products.filter(p =>
    p.cloudPlatforms.includes("any") ||
    p.cloudPlatforms.includes(context.cloudPlatform)
  );

  // Filter by BAA requirement for healthcare
  if (context.industry === "healthcare" || context.compliance.includes("HIPAA")) {
    // For critical components, require BAA
    if (["llm_access", "vector_db", "audit_logging"].includes(componentId)) {
      products = products.filter(p => p.hasBAA);
    }
  }

  // Filter by budget tier (show products at or below tier)
  const tierOrder = { starter: 1, growth: 2, enterprise: 3 };
  const userTierLevel = tierOrder[context.budgetTier];

  // Sort by relevance
  products.sort((a, b) => {
    // 1. Recommended for this industry first
    const aIndustryMatch = a.recommendedFor.industries.includes(context.industry) ? 1 : 0;
    const bIndustryMatch = b.recommendedFor.industries.includes(context.industry) ? 1 : 0;
    if (aIndustryMatch !== bIndustryMatch) return bIndustryMatch - aIndustryMatch;

    // 2. Recommended for this budget tier
    const aTierMatch = a.recommendedFor.budgetTiers.includes(context.budgetTier) ? 1 : 0;
    const bTierMatch = b.recommendedFor.budgetTiers.includes(context.budgetTier) ? 1 : 0;
    if (aTierMatch !== bTierMatch) return bTierMatch - aTierMatch;

    // 3. By popularity
    return b.popularity - a.popularity;
  });

  // Group into recommendation tiers
  return groupByRecommendationTier(products, context.budgetTier);
}

function groupByRecommendationTier(
  products: Product[],
  userTier: BudgetTier
): Product[] {
  // Return top 3-4 products with tier labels
  const result: Product[] = [];

  // Find best match for user's tier (recommended)
  const recommended = products.find(p =>
    p.recommendedFor.budgetTiers.includes(userTier)
  );
  if (recommended) {
    result.push({ ...recommended, _tier: "recommended" });
  }

  // Find budget-friendly option
  const budgetFriendly = products.find(p =>
    p.pricing.tiers.starter.min === 0 ||
    p.pricing.model === "free"
  );
  if (budgetFriendly && budgetFriendly.id !== recommended?.id) {
    result.push({ ...budgetFriendly, _tier: "budget" });
  }

  // Find enterprise option
  const enterprise = products.find(p =>
    p.recommendedFor.budgetTiers.includes("enterprise")
  );
  if (enterprise && enterprise.id !== recommended?.id) {
    result.push({ ...enterprise, _tier: "enterprise" });
  }

  return result;
}
```

### 3. Priority Ordering Algorithm

```typescript
// lib/algorithms/priority.ts

function sortGapsByPriority(
  gaps: Gap[],
  industry: Industry
): Gap[] {
  // Get industry-specific layer order
  const layerOrder = getLayerOrderForIndustry(industry);

  return gaps.sort((a, b) => {
    // 1. Sort by severity (critical first)
    const severityOrder = { critical: 0, high: 1, medium: 2, low: 3, optional: 4 };
    const severityDiff = severityOrder[a.severity] - severityOrder[b.severity];
    if (severityDiff !== 0) return severityDiff;

    // 2. Sort by layer priority for this industry
    const aLayerPriority = layerOrder.indexOf(a.layerId);
    const bLayerPriority = layerOrder.indexOf(b.layerId);
    if (aLayerPriority !== bLayerPriority) return aLayerPriority - bLayerPriority;

    // 3. Sort by component order within layer
    return COMPONENT_ORDER[a.componentId] - COMPONENT_ORDER[b.componentId];
  });
}

function getLayerOrderForIndustry(industry: Industry): LayerId[] {
  switch (industry) {
    case "healthcare":
      return ["L5", "L6", "L1", "L4", "L3", "L7", "L2"];
    case "financial":
      return ["L5", "L6", "L1", "L4", "L3", "L2", "L7"];
    case "government":
      return ["L5", "L1", "L4", "L6", "L3", "L7", "L2"];
    default:
      return ["L5", "L1", "L4", "L3", "L6", "L2", "L7"];
  }
}
```

### 4. Budget Calculation Algorithm

```typescript
// lib/algorithms/budget.ts

function computeTotalBudget(
  selections: Selection[],
  context: UserSession["context"]
): PriceRange {
  let totalMin = 0;
  let totalMax = 0;

  for (const selection of selections) {
    if (selection.isFromInventory) continue; // Don't count existing products

    const product = selection.product;
    const tierPricing = product.pricing.tiers[context.budgetTier];

    // Normalize to annual
    const multiplier = tierPricing.unit === "month" ? 12 : 1;
    totalMin += tierPricing.min * multiplier;
    totalMax += tierPricing.max * multiplier;
  }

  // Industry modifiers
  if (context.industry === "healthcare") {
    // Add 15% for compliance overhead
    totalMin *= 1.15;
    totalMax *= 1.15;
  }

  return {
    min: Math.round(totalMin),
    max: Math.round(totalMax),
    unit: "year"
  };
}

function computeTimeline(
  selections: Selection[],
  context: UserSession["context"]
): { min: number; max: number } {
  // Base timeline by layer
  const layerTimelines: Record<LayerId, { min: number; max: number }> = {
    L1: { min: 1, max: 2 },
    L2: { min: 1, max: 2 },
    L3: { min: 2, max: 3 },
    L4: { min: 2, max: 4 },
    L5: { min: 2, max: 3 },
    L6: { min: 1, max: 2 },
    L7: { min: 2, max: 3 }
  };

  // Get unique layers that need implementation
  const layersToImplement = new Set(
    selections
      .filter(s => !s.isFromInventory)
      .map(s => getLayerForComponent(s.componentId))
  );

  // Calculate with parallel implementation
  // Assume layers can be done in parallel with some overlap
  let totalMin = 0;
  let totalMax = 0;

  for (const layerId of layersToImplement) {
    totalMin += layerTimelines[layerId].min * 0.6; // 60% parallel
    totalMax += layerTimelines[layerId].max * 0.8; // 80% sequential
  }

  // Minimum 4 weeks, round up
  return {
    min: Math.max(4, Math.ceil(totalMin)),
    max: Math.max(6, Math.ceil(totalMax))
  };
}
```

---

## React Components

### 1. Component Structure

```
components/
├── stack-builder/
│   ├── StackBuilder.tsx           # Main container
│   ├── LeadCapture.tsx            # Step 2
│   ├── ContextQuestions.tsx       # Step 3
│   ├── LayerInventory.tsx         # Steps 4-10
│   ├── InteractiveBuilder.tsx     # Step 11 (main experience)
│   │   ├── StackVisualization.tsx # Left panel
│   │   ├── LayerRow.tsx           # Single layer in visualization
│   │   ├── ComponentBox.tsx       # Single component box
│   │   ├── GapSelector.tsx        # Right panel
│   │   ├── ProductCard.tsx        # Product recommendation card
│   │   ├── MetricsBar.tsx         # Bottom bar
│   │   └── ProgressIndicator.tsx  # Step progress
│   ├── StackSummary.tsx           # Step 12
│   └── hooks/
│       ├── useSession.ts          # Session state management
│       ├── useGaps.ts             # Gap computation
│       ├── useSelections.ts       # Selection management
│       └── useBudget.ts           # Budget calculation
├── ui/
│   ├── Button.tsx
│   ├── Card.tsx
│   ├── ProgressBar.tsx
│   ├── RadioGroup.tsx
│   └── Badge.tsx
└── pdf/
    └── StackReport.tsx            # PDF template
```

### 2. Main Interactive Builder Component

```tsx
// components/stack-builder/InteractiveBuilder.tsx

"use client";

import { useState, useEffect } from "react";
import { useSession } from "./hooks/useSession";
import { useGaps } from "./hooks/useGaps";
import { useSelections } from "./hooks/useSelections";
import { StackVisualization } from "./StackVisualization";
import { GapSelector } from "./GapSelector";
import { MetricsBar } from "./MetricsBar";
import { ProgressIndicator } from "./ProgressIndicator";

interface Props {
  sessionId: string;
}

export function InteractiveBuilder({ sessionId }: Props) {
  const { session, context } = useSession(sessionId);
  const { gaps, priorityOrder, currentGapIndex, goToNextGap, goToPrevGap } = useGaps(sessionId);
  const { selections, selectProduct, totalBudget, timeline } = useSelections(sessionId);

  const [selectedComponentId, setSelectedComponentId] = useState<string | null>(
    priorityOrder[0] || null
  );

  const currentGap = gaps.find(g => g.componentId === selectedComponentId);
  const completionPercentage = calculateCompletion(gaps, selections);

  // Handle product selection
  const handleSelectProduct = async (productId: string) => {
    if (!selectedComponentId) return;

    await selectProduct(selectedComponentId, productId);

    // Auto-advance to next gap
    const nextGap = goToNextGap();
    if (nextGap) {
      setSelectedComponentId(nextGap.componentId);
    }
  };

  // Handle clicking a component in the visualization
  const handleComponentClick = (componentId: string) => {
    setSelectedComponentId(componentId);
  };

  return (
    <div className="flex flex-col h-screen">
      {/* Progress */}
      <ProgressIndicator
        currentStep={currentGapIndex + 1}
        totalSteps={gaps.length}
        currentLabel={currentGap?.componentId}
        onBack={goToPrevGap}
        onSkip={goToNextGap}
      />

      {/* Main content - split view */}
      <div className="flex flex-1 overflow-hidden">
        {/* Left: Stack Visualization */}
        <div className="w-1/2 p-6 overflow-auto border-r">
          <StackVisualization
            session={session}
            selections={selections}
            gaps={gaps}
            selectedComponentId={selectedComponentId}
            onComponentClick={handleComponentClick}
          />
        </div>

        {/* Right: Gap Selector */}
        <div className="w-1/2 p-6 overflow-auto">
          {currentGap ? (
            <GapSelector
              gap={currentGap}
              context={context}
              onSelect={handleSelectProduct}
              onSkip={goToNextGap}
            />
          ) : (
            <div className="text-center py-12">
              <h2 className="text-2xl font-bold text-green-600">
                ✅ Stack Complete!
              </h2>
              <p className="mt-2 text-gray-600">
                You've addressed all gaps. Review your stack below.
              </p>
            </div>
          )}
        </div>
      </div>

      {/* Bottom: Metrics Bar */}
      <MetricsBar
        budget={totalBudget}
        timeline={timeline}
        completionPercentage={completionPercentage}
        gapCounts={{
          critical: gaps.filter(g => g.severity === "critical").length,
          high: gaps.filter(g => g.severity === "high").length,
          optional: gaps.filter(g => g.severity === "optional").length,
        }}
        onDownloadReport={() => {/* trigger PDF generation */}}
        onReset={() => {/* reset selections */}}
      />
    </div>
  );
}
```

### 3. Stack Visualization Component

```tsx
// components/stack-builder/StackVisualization.tsx

import { motion, AnimatePresence } from "framer-motion";
import { LayerRow } from "./LayerRow";
import { LAYERS } from "@/lib/data/layers";

interface Props {
  session: UserSession;
  selections: Record<string, Selection>;
  gaps: Gap[];
  selectedComponentId: string | null;
  onComponentClick: (componentId: string) => void;
}

export function StackVisualization({
  session,
  selections,
  gaps,
  selectedComponentId,
  onComponentClick
}: Props) {
  // Calculate layer status
  const getLayerStatus = (layerId: string) => {
    const layer = LAYERS.find(l => l.id === layerId)!;
    const requiredComponents = layer.components.filter(c => c.required);

    const coveredCount = requiredComponents.filter(c =>
      session.inventory[c.id]?.hasExisting || selections[c.id]
    ).length;

    if (coveredCount === requiredComponents.length) return "complete";
    if (coveredCount > 0) return "partial";
    return "missing";
  };

  return (
    <div className="space-y-2">
      <div className="flex justify-between items-center mb-4">
        <h2 className="text-xl font-bold">Your AI Agent Stack</h2>
        <div className="text-sm text-gray-500">
          Progress: {calculateLayerProgress(selections, gaps)}/7 Layers
        </div>
      </div>

      {/* Render layers from L7 to L1 (top to bottom) */}
      {[...LAYERS].reverse().map((layer) => (
        <motion.div
          key={layer.id}
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ delay: (7 - parseInt(layer.id[1])) * 0.1 }}
        >
          <LayerRow
            layer={layer}
            status={getLayerStatus(layer.id)}
            inventory={session.inventory}
            selections={selections}
            gaps={gaps}
            selectedComponentId={selectedComponentId}
            industryPriority={layer.priorityOrder[session.context.industry]}
            onComponentClick={onComponentClick}
          />
        </motion.div>
      ))}
    </div>
  );
}
```

### 4. Product Card Component

```tsx
// components/stack-builder/ProductCard.tsx

import { motion } from "framer-motion";
import { Check, AlertTriangle } from "lucide-react";
import { Badge } from "@/components/ui/Badge";
import { Button } from "@/components/ui/Button";

interface Props {
  product: Product;
  tier: "recommended" | "budget" | "enterprise";
  context: UserSession["context"];
  onSelect: () => void;
}

export function ProductCard({ product, tier, context, onSelect }: Props) {
  const pricing = product.pricing.tiers[context.budgetTier];

  const tierLabels = {
    recommended: "Recommended",
    budget: "Budget-Friendly",
    enterprise: "Enterprise"
  };

  const tierColors = {
    recommended: "bg-green-100 text-green-800",
    budget: "bg-blue-100 text-blue-800",
    enterprise: "bg-purple-100 text-purple-800"
  };

  return (
    <motion.div
      className={`border rounded-lg p-4 ${
        tier === "recommended" ? "border-green-500 border-2" : "border-gray-200"
      }`}
      whileHover={{ scale: 1.01 }}
      transition={{ type: "spring", stiffness: 300 }}
    >
      <div className="flex justify-between items-start mb-3">
        <div>
          <Badge className={tierColors[tier]}>
            {tierLabels[tier]}
          </Badge>
          <h3 className="text-lg font-semibold mt-2">{product.name}</h3>
          <p className="text-sm text-gray-500">{product.vendor}</p>
        </div>
        <div className="text-right">
          <div className="text-lg font-bold">
            {pricing.min === 0 ? "Free" : `$${pricing.min.toLocaleString()}`}
            {pricing.max !== pricing.min && ` - $${pricing.max.toLocaleString()}`}
          </div>
          <div className="text-sm text-gray-500">/{pricing.unit}</div>
        </div>
      </div>

      {/* Features */}
      <div className="flex flex-wrap gap-2 mb-3">
        {product.features.slice(0, 4).map((feature, i) => (
          <span key={i} className="inline-flex items-center text-sm text-gray-600">
            <Check className="w-4 h-4 text-green-500 mr-1" />
            {feature}
          </span>
        ))}
      </div>

      {/* Caveats */}
      {product.caveats.length > 0 && (
        <div className="flex flex-wrap gap-2 mb-3">
          {product.caveats.map((caveat, i) => (
            <span key={i} className="inline-flex items-center text-sm text-amber-600">
              <AlertTriangle className="w-4 h-4 mr-1" />
              {caveat}
            </span>
          ))}
        </div>
      )}

      {/* Description */}
      <p className="text-sm text-gray-600 mb-4">
        "{product.shortDescription}"
      </p>

      {/* BAA badge for healthcare */}
      {context.industry === "healthcare" && product.hasBAA && (
        <Badge className="bg-green-500 text-white mb-3">
          ✓ BAA Available
        </Badge>
      )}

      <Button
        onClick={onSelect}
        className="w-full"
        variant={tier === "recommended" ? "primary" : "secondary"}
      >
        Select {product.name}
      </Button>
    </motion.div>
  );
}
```

### 5. Metrics Bar Component

```tsx
// components/stack-builder/MetricsBar.tsx

import { motion } from "framer-motion";
import { Download, RotateCcw } from "lucide-react";
import { Button } from "@/components/ui/Button";

interface Props {
  budget: PriceRange;
  timeline: { min: number; max: number };
  completionPercentage: number;
  gapCounts: { critical: number; high: number; optional: number };
  onDownloadReport: () => void;
  onReset: () => void;
}

export function MetricsBar({
  budget,
  timeline,
  completionPercentage,
  gapCounts,
  onDownloadReport,
  onReset
}: Props) {
  return (
    <motion.div
      className="border-t bg-white p-4 flex items-center justify-between"
      initial={{ y: 100 }}
      animate={{ y: 0 }}
    >
      {/* Stack Coverage */}
      <div className="flex-1">
        <div className="text-sm text-gray-500">Stack Coverage</div>
        <div className="flex items-center gap-2">
          <div className="w-32 h-2 bg-gray-200 rounded-full overflow-hidden">
            <motion.div
              className="h-full bg-green-500"
              initial={{ width: 0 }}
              animate={{ width: `${completionPercentage}%` }}
              transition={{ type: "spring", stiffness: 50 }}
            />
          </div>
          <span className="font-semibold">{completionPercentage}%</span>
        </div>
      </div>

      {/* Budget */}
      <div className="flex-1 text-center">
        <div className="text-sm text-gray-500">Estimated Budget</div>
        <div className="font-semibold text-lg">
          ${budget.min.toLocaleString()} - ${budget.max.toLocaleString()}
        </div>
        <div className="text-xs text-gray-400">per year</div>
      </div>

      {/* Timeline */}
      <div className="flex-1 text-center">
        <div className="text-sm text-gray-500">Implementation Time</div>
        <div className="font-semibold text-lg">
          {timeline.min}-{timeline.max} weeks
        </div>
      </div>

      {/* Gap counters */}
      <div className="flex gap-2">
        {gapCounts.critical > 0 && (
          <div className="px-3 py-1 bg-red-100 text-red-800 rounded-full text-sm font-medium">
            {gapCounts.critical} Critical
          </div>
        )}
        {gapCounts.high > 0 && (
          <div className="px-3 py-1 bg-amber-100 text-amber-800 rounded-full text-sm font-medium">
            {gapCounts.high} High
          </div>
        )}
        {gapCounts.optional > 0 && (
          <div className="px-3 py-1 bg-gray-100 text-gray-600 rounded-full text-sm font-medium">
            {gapCounts.optional} Optional
          </div>
        )}
      </div>

      {/* Actions */}
      <div className="flex gap-2 ml-4">
        <Button variant="outline" size="sm" onClick={onReset}>
          <RotateCcw className="w-4 h-4 mr-1" />
          Reset
        </Button>
        <Button variant="primary" size="sm" onClick={onDownloadReport}>
          <Download className="w-4 h-4 mr-1" />
          Download Report
        </Button>
      </div>
    </motion.div>
  );
}
```

---

## State Management (Zustand)

```typescript
// lib/store/stackBuilderStore.ts

import { create } from "zustand";
import { persist } from "zustand/middleware";

interface StackBuilderState {
  // Session
  sessionId: string | null;
  currentStep: "lead" | "context" | "inventory" | "builder" | "summary";

  // Data
  lead: Lead | null;
  context: Context | null;
  inventory: Record<ComponentId, InventoryItem>;
  selections: Record<ComponentId, Selection>;

  // Computed (cached)
  gaps: Gap[];
  priorityOrder: ComponentId[];
  totalBudget: PriceRange;
  timeline: { min: number; max: number };

  // UI State
  selectedComponentId: ComponentId | null;
  currentGapIndex: number;

  // Actions
  setLead: (lead: Lead) => void;
  setContext: (context: Context) => void;
  setInventoryItem: (componentId: ComponentId, item: InventoryItem) => void;
  selectProduct: (componentId: ComponentId, product: Product) => void;
  skipComponent: (componentId: ComponentId) => void;
  setSelectedComponent: (componentId: ComponentId | null) => void;
  goToNextGap: () => Gap | null;
  goToPrevGap: () => Gap | null;
  applyRecommendedStack: () => void;
  reset: () => void;

  // Computed actions
  recomputeGaps: () => void;
  recomputeBudget: () => void;
}

export const useStackBuilderStore = create<StackBuilderState>()(
  persist(
    (set, get) => ({
      // Initial state
      sessionId: null,
      currentStep: "lead",
      lead: null,
      context: null,
      inventory: {},
      selections: {},
      gaps: [],
      priorityOrder: [],
      totalBudget: { min: 0, max: 0, unit: "year" },
      timeline: { min: 0, max: 0 },
      selectedComponentId: null,
      currentGapIndex: 0,

      // Actions
      selectProduct: (componentId, product) => {
        set((state) => ({
          selections: {
            ...state.selections,
            [componentId]: {
              componentId,
              productId: product.id,
              product,
              selectedAt: new Date(),
              isFromInventory: false
            }
          }
        }));

        // Recompute
        get().recomputeGaps();
        get().recomputeBudget();
      },

      goToNextGap: () => {
        const { gaps, currentGapIndex, priorityOrder } = get();
        const nextIndex = currentGapIndex + 1;

        if (nextIndex < gaps.length) {
          const nextGap = gaps[nextIndex];
          set({
            currentGapIndex: nextIndex,
            selectedComponentId: nextGap.componentId
          });
          return nextGap;
        }

        return null;
      },

      applyRecommendedStack: () => {
        const { gaps, context } = get();
        const selections: Record<ComponentId, Selection> = {};

        for (const gap of gaps) {
          // Get top recommendation for each gap
          const recommendations = getRecommendations(gap.componentId, context!);
          if (recommendations.length > 0) {
            const product = recommendations[0];
            selections[gap.componentId] = {
              componentId: gap.componentId,
              productId: product.id,
              product,
              selectedAt: new Date(),
              isFromInventory: false
            };
          }
        }

        set({ selections, gaps: [] });
        get().recomputeBudget();
      },

      recomputeGaps: () => {
        const { context, inventory, selections } = get();
        if (!context) return;

        const gaps = computeGaps({ context, inventory, selections });
        const priorityOrder = sortGapsByPriority(gaps, context.industry)
          .map(g => g.componentId);

        set({ gaps, priorityOrder });
      },

      recomputeBudget: () => {
        const { selections, context } = get();
        if (!context) return;

        const selectionsArray = Object.values(selections);
        const totalBudget = computeTotalBudget(selectionsArray, context);
        const timeline = computeTimeline(selectionsArray, context);

        set({ totalBudget, timeline });
      },

      reset: () => {
        set({
          selections: {},
          gaps: [],
          priorityOrder: [],
          totalBudget: { min: 0, max: 0, unit: "year" },
          timeline: { min: 0, max: 0 },
          selectedComponentId: null,
          currentGapIndex: 0
        });
        get().recomputeGaps();
      }
    }),
    {
      name: "stack-builder-storage",
      partialize: (state) => ({
        sessionId: state.sessionId,
        lead: state.lead,
        context: state.context,
        inventory: state.inventory,
        selections: state.selections
      })
    }
  )
);
```

---

## Product Catalog Data File

```typescript
// lib/data/products.ts

export const PRODUCTS: Product[] = [
  // Layer 1: Vector Databases
  {
    id: "pinecone-starter",
    name: "Pinecone",
    vendor: "Pinecone Systems",
    layer: "L1",
    component: "vector_db",
    pricing: {
      model: "subscription",
      tiers: {
        starter: { min: 0, max: 70, unit: "month" },
        growth: { min: 70, max: 300, unit: "month" },
        enterprise: { min: 500, max: 2000, unit: "month" }
      }
    },
    cloudPlatforms: ["aws", "azure", "gcp"],
    hasBAA: true,
    compliance: ["SOC2", "HIPAA", "GDPR"],
    description: "Fully managed vector database for production AI applications.",
    shortDescription: "Leading managed vector database with enterprise compliance.",
    features: [
      "Fully managed",
      "Auto-scaling",
      "Real-time updates",
      "Metadata filtering"
    ],
    caveats: [],
    websiteUrl: "https://pinecone.io",
    docsUrl: "https://docs.pinecone.io",
    recommendedFor: {
      industries: ["healthcare", "financial", "technology"],
      budgetTiers: ["growth", "enterprise"],
      useCases: ["semantic_search", "rag"]
    },
    popularity: 95,
    isRecommended: true
  },

  {
    id: "azure-ai-search",
    name: "Azure AI Search",
    vendor: "Microsoft",
    layer: "L1",
    component: "vector_db",
    pricing: {
      model: "usage",
      tiers: {
        starter: { min: 100, max: 250, unit: "month" },
        growth: { min: 250, max: 800, unit: "month" },
        enterprise: { min: 1000, max: 5000, unit: "month" }
      }
    },
    cloudPlatforms: ["azure"],
    hasBAA: true,
    compliance: ["SOC2", "HIPAA", "GDPR", "FedRAMP"],
    description: "Enterprise search with vector capabilities, native Azure integration.",
    shortDescription: "Native Azure vector search with full enterprise compliance.",
    features: [
      "Native Azure",
      "Hybrid search",
      "Semantic ranking",
      "Built-in security"
    ],
    caveats: ["Azure only"],
    websiteUrl: "https://azure.microsoft.com/products/ai-services/ai-search",
    docsUrl: "https://learn.microsoft.com/azure/search",
    recommendedFor: {
      industries: ["healthcare", "government", "financial"],
      budgetTiers: ["starter", "growth", "enterprise"],
      useCases: ["semantic_search", "enterprise_search"]
    },
    popularity: 85,
    isRecommended: true
  },

  // Layer 4: LLM Access
  {
    id: "azure-openai",
    name: "Azure OpenAI",
    vendor: "Microsoft",
    layer: "L4",
    component: "llm_access",
    pricing: {
      model: "usage",
      tiers: {
        starter: { min: 500, max: 2000, unit: "month" },
        growth: { min: 2000, max: 5000, unit: "month" },
        enterprise: { min: 5000, max: 20000, unit: "month" }
      }
    },
    cloudPlatforms: ["azure"],
    hasBAA: true,
    compliance: ["SOC2", "HIPAA", "GDPR", "FedRAMP"],
    description: "OpenAI models with enterprise security and compliance via Azure.",
    shortDescription: "ONLY LLM option with HIPAA BAA. Required for healthcare.",
    features: [
      "GPT-4, GPT-4o",
      "BAA available",
      "Enterprise security",
      "Data privacy"
    ],
    caveats: ["Azure only", "Requires Azure subscription"],
    websiteUrl: "https://azure.microsoft.com/products/ai-services/openai-service",
    docsUrl: "https://learn.microsoft.com/azure/ai-services/openai",
    recommendedFor: {
      industries: ["healthcare", "government", "financial"],
      budgetTiers: ["starter", "growth", "enterprise"],
      useCases: ["rag", "agents", "generation"]
    },
    popularity: 98,
    isRecommended: true
  },

  // Layer 5: ABAC
  {
    id: "styra-das",
    name: "Styra DAS",
    vendor: "Styra",
    layer: "L5",
    component: "abac",
    pricing: {
      model: "subscription",
      tiers: {
        starter: { min: 0, max: 0, unit: "year" }, // Free tier
        growth: { min: 15000, max: 25000, unit: "year" },
        enterprise: { min: 40000, max: 80000, unit: "year" }
      }
    },
    cloudPlatforms: ["aws", "azure", "gcp", "any"],
    hasBAA: false,
    compliance: ["SOC2"],
    description: "Managed Open Policy Agent (OPA) with visual policy editor.",
    shortDescription: "Managed OPA with enterprise features for teams without policy expertise.",
    features: [
      "Built on OPA",
      "Visual editor",
      "Audit trails",
      "Decision logging"
    ],
    caveats: [],
    websiteUrl: "https://styra.com",
    docsUrl: "https://docs.styra.com",
    recommendedFor: {
      industries: ["healthcare", "financial", "technology"],
      budgetTiers: ["growth", "enterprise"],
      useCases: ["abac", "authorization"]
    },
    popularity: 80,
    isRecommended: true
  },

  {
    id: "opa",
    name: "Open Policy Agent (OPA)",
    vendor: "CNCF",
    layer: "L5",
    component: "abac",
    pricing: {
      model: "free",
      tiers: {
        starter: { min: 0, max: 0, unit: "year" },
        growth: { min: 0, max: 0, unit: "year" },
        enterprise: { min: 0, max: 0, unit: "year" }
      }
    },
    cloudPlatforms: ["any"],
    hasBAA: false,
    compliance: [],
    description: "Open-source policy engine. Industry standard for policy-as-code.",
    shortDescription: "Free, powerful, widely adopted. Requires engineering investment.",
    features: [
      "Free & open-source",
      "Policy as code",
      "Large community",
      "Flexible"
    ],
    caveats: ["Requires expertise", "Self-managed", "Build your own UI"],
    websiteUrl: "https://www.openpolicyagent.org",
    docsUrl: "https://www.openpolicyagent.org/docs",
    recommendedFor: {
      industries: ["technology"],
      budgetTiers: ["starter"],
      useCases: ["abac", "authorization"]
    },
    popularity: 90,
    isRecommended: false
  },

  // ... Add remaining ~50 products following this pattern
];
```

---

## File Structure Summary

```
stack-builder/
├── app/
│   ├── page.tsx                      # Landing page
│   ├── assess/
│   │   └── page.tsx                  # Main assessment flow
│   ├── api/
│   │   ├── sessions/
│   │   │   ├── route.ts              # POST: create session
│   │   │   └── [id]/
│   │   │       ├── route.ts          # GET/PUT session
│   │   │       ├── context/route.ts
│   │   │       ├── inventory/route.ts
│   │   │       ├── gaps/route.ts
│   │   │       ├── selections/
│   │   │       │   └── [componentId]/route.ts
│   │   │       ├── summary/route.ts
│   │   │       └── report/route.ts   # PDF generation
│   │   └── products/
│   │       └── route.ts              # GET all products
├── components/
│   └── stack-builder/                # All components listed above
├── lib/
│   ├── data/
│   │   ├── products.ts               # Product catalog
│   │   ├── layers.ts                 # Layer definitions
│   │   └── components.ts             # Component definitions
│   ├── algorithms/
│   │   ├── gaps.ts                   # Gap detection
│   │   ├── recommendations.ts        # Filtering/sorting
│   │   ├── priority.ts               # Priority ordering
│   │   └── budget.ts                 # Budget calculation
│   ├── store/
│   │   └── stackBuilderStore.ts      # Zustand store
│   └── db/
│       ├── prisma.ts                 # Prisma client
│       └── schema.prisma             # Database schema
├── types/
│   ├── product.ts
│   ├── layer.ts
│   ├── session.ts
│   └── api.ts
└── public/
    └── images/
        └── vendor-logos/             # Product logos
```

---

## Quick Start for AI Coding Tools

```markdown
## Instructions for Claude Code / Cursor / Windsurf

1. **Create Next.js app:**
   ```bash
   npx create-next-app@latest stack-builder --typescript --tailwind --app
   cd stack-builder
   npm install zustand framer-motion @prisma/client lucide-react
   npm install -D prisma
   ```

2. **Set up database:**
   - Copy the schema from "Database Schema" section to `prisma/schema.prisma`
   - Run `npx prisma migrate dev`

3. **Create types:**
   - Copy all interfaces from "Data Models" section to `types/` folder

4. **Create product catalog:**
   - Copy PRODUCTS array to `lib/data/products.ts`
   - Expand with all ~50 products using the pattern shown

5. **Implement algorithms:**
   - Copy all algorithm functions to `lib/algorithms/`

6. **Create Zustand store:**
   - Copy store to `lib/store/stackBuilderStore.ts`

7. **Build components:**
   - Start with `InteractiveBuilder.tsx` as the main component
   - Build child components: StackVisualization, GapSelector, MetricsBar
   - Use Tailwind for styling, Framer Motion for animations

8. **Create API routes:**
   - Follow the endpoint patterns in "API Endpoints" section
   - Use Prisma for database operations

9. **Test the flow:**
   - Lead capture → Context → Inventory (7 layers) → Interactive Builder → Summary
```