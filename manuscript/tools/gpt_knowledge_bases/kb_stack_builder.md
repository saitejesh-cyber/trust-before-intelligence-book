# Stack Builder Knowledge Base
## 7-Layer Architecture Gap Analysis

**Purpose:** Help users identify gaps in their current technology stack and prioritize what to build next.
**Date:** January 2026

---

## How Stack Builder Works

1. **User inputs what they have**  - For each layer, user selects existing technologies
2. **System identifies gaps**  - Missing layers or inadequate coverage flagged
3. **Prioritized recommendations**  - Build order based on dependencies and impact
4. **Budget estimation**  - Investment range by tier
5. **Handoff to Vendor Advisor**  - For specific product selection

---

## The 7-Layer Architecture

| Layer | Name | Purpose | Critical For |
|-------|------|---------|--------------|
| **L1** | Multi-Modal Storage | Store vectors, graphs, documents | All agent memory |
| **L2** | Real-Time Data Fabric | Stream changes, keep data fresh | Context currency |
| **L3** | Universal Semantic Layer | Define business meaning | Natural language queries |
| **L4** | Intelligence Orchestration | RAG, embeddings, retrieval | Agent reasoning |
| **L5** | Agent-Aware Governance | ABAC, audit, secrets | Trust & compliance |
| **L6** | Observability & Feedback | Monitor, learn, improve | Continuous improvement |
| **L7** | Self-Service Data Products | Orchestration, APIs, HITL | Production deployment |

---

## Layer 1: Multi-Modal Storage

### What This Layer Does
Stores the data agents need to access  - vectors for semantic search, graphs for relationships, warehouses for structured data.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| Vector Database | Semantic similarity search | ✅ Required |
| Graph Database | Relationship traversal | ⚠️ Recommended |
| Data Warehouse | Structured analytics | ⚠️ If analytics needed |
| Data Quality | Validate, clean, monitor | ✅ Required |

### Common User Inputs
- "We use Snowflake" → Warehouse covered, need vector + graph
- "We use Pinecone" → Vector covered, need warehouse + graph
- "We use Neo4j" → Graph covered, need vector + warehouse
- "We use Databricks" → Warehouse + some vector covered
- "None" → Full layer gap

### Gap Analysis Logic
```
IF no vector database → CRITICAL GAP (agents can't do semantic search)
IF no data quality tool → HIGH GAP (garbage in, garbage out)
IF no warehouse AND analytics needed → MEDIUM GAP
IF no graph AND relationship queries needed → MEDIUM GAP
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $5-10K/year | Pinecone + existing warehouse |
| Growth ($150K) | $20-40K/year | Weaviate + Snowflake + Great Expectations |
| Enterprise ($300K+) | $50-100K/year | Full multi-modal with Neo4j |

---

## Layer 2: Real-Time Data Fabric

### What This Layer Does
Keeps agent data fresh by streaming changes in real-time. Without this, agents work with stale information.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| CDC (Change Data Capture) | Capture database changes | ✅ Required |
| Stream Processing | Transform in flight | ⚠️ Recommended |
| Event Bus | Distribute events | ⚠️ If microservices |

### Common User Inputs
- "We use Kafka" → Event bus covered, may need CDC
- "We use Debezium" → CDC covered, need event bus
- "We use Fivetran" → Batch ETL only, need real-time
- "We use Airbyte" → Batch + some CDC
- "None" → Full layer gap

### Gap Analysis Logic
```
IF no CDC → CRITICAL GAP (agents see stale data)
IF CDC but no streaming → MEDIUM GAP (delayed freshness)
IF batch ETL only → HIGH GAP (not real-time)
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $3-8K/year | Debezium + managed Kafka |
| Growth ($150K) | $15-30K/year | Confluent Cloud + custom CDC |
| Enterprise ($300K+) | $40-80K/year | Full Confluent + Flink |

---

## Layer 3: Universal Semantic Layer

### What This Layer Does
Translates business language into data queries. This is how agents understand "show me high-risk patients" means specific database filters.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| Semantic Platform | Business definitions → queries | ✅ Required |
| Data Catalog | Discover available data | ✅ Required |
| Business Glossary | Standard terminology | ⚠️ Recommended |
| Entity Resolution | Match records across systems | ⚠️ If multiple sources |

### Common User Inputs
- "We use dbt" → Transformations only, need semantic layer
- "We use Cube" → Semantic covered
- "We use Atlan" → Catalog covered, need semantic
- "We use Collibra" → Catalog + glossary covered
- "None" → Full layer gap

### Gap Analysis Logic
```
IF no semantic platform → CRITICAL GAP (agents can't translate NL to queries)
IF no data catalog → HIGH GAP (agents don't know what data exists)
IF multiple data sources AND no entity resolution → HIGH GAP (duplicate entities)
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $5-12K/year | Cube + open-source catalog |
| Growth ($150K) | $25-50K/year | Cube + Atlan |
| Enterprise ($300K+) | $60-120K/year | Cube + Collibra + entity resolution |

---

## Layer 4: Intelligence Orchestration

### What This Layer Does
Coordinates retrieval, embeddings, and LLM calls. This is the "brain" that assembles context and generates responses.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| RAG Framework | Retrieve → Augment → Generate | ✅ Required |
| Embedding Models | Convert text to vectors | ✅ Required |
| LLM Access | Generate responses | ✅ Required |
| Semantic Cache | Reduce redundant calls | ⚠️ Recommended |
| Reranking | Improve retrieval quality | ⚠️ Recommended |

### Common User Inputs
- "We use LangChain" → Framework covered, need models
- "We use OpenAI" → LLM + embeddings covered
- "We use Azure OpenAI" → LLM + embeddings + compliance
- "We use LlamaIndex" → Framework + some orchestration
- "None" → Full layer gap

### Gap Analysis Logic
```
IF no RAG framework → CRITICAL GAP (no retrieval orchestration)
IF no LLM access → CRITICAL GAP (no generation capability)
IF no embeddings → CRITICAL GAP (no semantic understanding)
IF high volume AND no cache → MEDIUM GAP (cost + latency issues)
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $5-15K/year | LangChain + OpenAI |
| Growth ($150K) | $30-60K/year | LangChain + Azure OpenAI + cache |
| Enterprise ($300K+) | $80-200K/year | Custom orchestration + multiple LLMs |

---

## Layer 5: Agent-Aware Governance

### What This Layer Does
Controls what agents can access and tracks what they do. Critical for compliance and trust.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| ABAC Policy Engine | Attribute-based access control | ✅ Required |
| Audit Logging | Track all agent actions | ✅ Required |
| Secrets Management | Secure credentials | ✅ Required |
| Data Masking | Protect sensitive fields | ⚠️ If PII/PHI |

### Common User Inputs
- "We use OPA" → Policy engine covered
- "We use HashiCorp Vault" → Secrets covered
- "We use AWS IAM" → Basic RBAC only, need ABAC
- "We have audit logs" → Logging covered, need policy
- "None" → Full layer gap (CRITICAL for healthcare)

### Gap Analysis Logic
```
IF no ABAC → CRITICAL GAP (agents have unconstrained access)
IF no audit logging → CRITICAL GAP (no accountability)
IF no secrets management → HIGH GAP (credentials at risk)
IF healthcare AND no data masking → CRITICAL GAP (PHI exposure)
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $3-8K/year | OPA + Vault + basic logging |
| Growth ($150K) | $15-35K/year | Styra DAS + Vault Enterprise |
| Enterprise ($300K+) | $40-100K/year | Full governance suite |

---

## Layer 6: Observability & Feedback

### What This Layer Does
Monitors agent performance, captures feedback, enables continuous improvement.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| LLM Observability | Track prompts, tokens, latency | ✅ Required |
| APM (Application Monitoring) | System health | ✅ Required |
| Feedback Collection | User ratings, corrections | ⚠️ Recommended |
| A/B Testing | Compare approaches | ⚠️ For optimization |

### Common User Inputs
- "We use Datadog" → APM covered, need LLM-specific
- "We use LangSmith" → LLM observability covered
- "We use Weights & Biases" → ML tracking covered
- "We have basic logging" → Insufficient for agents
- "None" → Full layer gap

### Gap Analysis Logic
```
IF no LLM observability → HIGH GAP (can't debug agent behavior)
IF no APM → MEDIUM GAP (system blind spots)
IF no feedback loop → MEDIUM GAP (can't improve over time)
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $2-6K/year | LangSmith + existing APM |
| Growth ($150K) | $10-25K/year | LangSmith + Datadog |
| Enterprise ($300K+) | $30-70K/year | Full observability suite |

---

## Layer 7: Self-Service Data Products

### What This Layer Does
Exposes agents as products  - APIs, workflows, human-in-the-loop interfaces.

### Components Needed
| Component | Purpose | Required? |
|-----------|---------|-----------|
| Workflow Orchestration | Coordinate multi-step processes | ✅ Required |
| API Gateway | Expose agent capabilities | ✅ Required |
| HITL Platform | Human review/approval | ⚠️ If high-stakes |
| Rate Limiting | Control usage | ⚠️ Recommended |

### Common User Inputs
- "We use Airflow" → Orchestration covered
- "We use Temporal" → Orchestration covered
- "We use Kong" → API gateway covered
- "We use AWS API Gateway" → Gateway covered
- "None" → Full layer gap

### Gap Analysis Logic
```
IF no orchestration → HIGH GAP (can't coordinate complex workflows)
IF no API gateway → MEDIUM GAP (no controlled exposure)
IF high-stakes decisions AND no HITL → CRITICAL GAP (unsafe autonomy)
```

### Budget Estimates
| Tier | Investment | Typical Stack |
|------|------------|---------------|
| Starter ($30K) | $2-5K/year | Airflow + basic gateway |
| Growth ($150K) | $10-25K/year | Temporal + Kong |
| Enterprise ($300K+) | $30-60K/year | Full orchestration + HITL |

---

## Build Order Priority

### Recommended Sequence (Default)
1. **Layer 5 (Governance)**  - Safety first
2. **Layer 1 (Storage)**  - Foundation for data
3. **Layer 4 (Intelligence)**  - Core agent capability
4. **Layer 3 (Semantic)**  - Business understanding
5. **Layer 6 (Observability)**  - Monitor and improve
6. **Layer 2 (Real-Time)**  - Data freshness
7. **Layer 7 (Products)**  - Production deployment

### Healthcare Sequence
1. **Layer 5 (Governance)**  - HIPAA compliance first
2. **Layer 6 (Observability)**  - Audit requirements
3. **Layer 1 (Storage)**  - PHI-safe storage
4. **Layer 4 (Intelligence)**  - BAA-covered LLMs
5. **Layer 3 (Semantic)**  - Clinical terminology
6. **Layer 7 (Products)**  - HITL for clinical decisions
7. **Layer 2 (Real-Time)**  - Patient data freshness

### Fast MVP Sequence
1. **Layer 4 (Intelligence)**  - Get agents working
2. **Layer 1 (Storage)**  - Basic vector search
3. **Layer 5 (Governance)**  - Minimum viable security
4. (Expand from there)

---

## Total Budget Summary

| Tier | Total Investment | Typical Timeline |
|------|------------------|------------------|
| **Starter** | $25-60K/year | 30-60 days |
| **Growth** | $125-265K/year | 60-90 days |
| **Enterprise** | $330-730K/year | 90-180 days |

---

## Integration with Other Tools

- **After Stack Builder** → Use **Vendor Advisor** to select specific products for each gap
- **Before Stack Builder** → Use **INPACT Assessor** to understand current readiness score
- **During Build** → Use **Trust Coach** for week-by-week guidance
- **For Issues** → Use **Pattern Finder** to troubleshoot problems