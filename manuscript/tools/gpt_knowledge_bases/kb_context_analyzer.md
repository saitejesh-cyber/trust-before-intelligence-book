# Context Taxonomy for Agentic AI

**Book:** Trust Before Intelligence
**Purpose:** Comprehensive taxonomy of context types required for trustworthy AI agent outputs
**Version:** 2.0
**Date:** January 2026

---

## Overview

This taxonomy defines all context types that AI agents need to access for trustworthy, effective operation. It is organized in three levels:

1. **Core 7 Contexts**  - The foundational contexts from "Trust Before Intelligence" (Chapter 1, Part 3)
2. **10 Context Domains**  - High-level categories for organizing 100+ context types
3. **40+ Context Types**  - Detailed context types within each domain

---

# PART 1: THE CORE 7 CONTEXTS

These are the foundational contexts identified in "Trust Before Intelligence." Echo Health Systems started with only 1 of 7 (Data Context), creating 86% context blindness -the root cause of physician distrust.

## 1. User Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Information about who is using the agent -role, expertise level, preferences, typical patterns |
| **Example Need** | Dr. Chen's documentation style, specialty (endocrinology), preferred terminology |
| **Without It** | Generic outputs that don't match individual styles |
| **Layer Mapping** | Layer 3 (Semantic)  - User profile management, preference storage |

**Key Attributes:**
- Identity (name, ID, authentication)
- Role (job function, authority level)
- Expertise (skill level, domain knowledge)
- Preferences (communication style, defaults)
- Patterns (usage history, behaviors)

---

## 2. Task Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Understanding the specific goal or workflow the user is trying to accomplish |
| **Example Need** | Progress note for diabetes follow-up vs. initial consultation vs. specialist referral |
| **Without It** | Wrong structure, missing required sections for specific task types |
| **Layer Mapping** | Layer 4 (Intelligence)  - Workflow-aware retrieval, task classification |

**Key Attributes:**
- Immediate goal (what to accomplish now)
- Task type/category (classification)
- Success criteria (definition of done)
- Completion state (progress tracking)

---

## 3. Data Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Access to current, relevant data for the immediate task |
| **Example Need** | Today's vitals, labs, chief complaint from current visit |
| **Without It** | Outdated or irrelevant information |
| **Layer Mapping** | Layer 1-2 (Storage, Real-Time Data Fabric) |

**Key Attributes:**
- Immediate task data (current records)
- Freshness (real-time, cached, stale)
- Completeness (all required fields)
- Source systems (where data comes from)

---

## 4. Environmental Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Understanding the physical and operational constraints of the work environment |
| **Example Need** | 15-minute time slots, voice recognition in exam room, workflow pressures |
| **Without It** | Unrealistic expectations, doesn't adapt to pressures |
| **Layer Mapping** | Layer 4 (Intelligence)  - Session metadata integration |

**Key Attributes:**
- Resource constraints (time, compute, budget)
- Workload (current capacity)
- System status (availability, performance)
- Channel (voice, chat, API)

---

## 5. Business Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Domain knowledge, care protocols, regulatory requirements, business rules |
| **Example Need** | Diabetes care protocols, documentation requirements for insurance, escalation paths |
| **Without It** | Missing compliance elements, incomplete documentation |
| **Layer Mapping** | Layer 3 (Semantic)  - Business rule engine, protocol integration |

**Key Attributes:**
- Policies (organizational rules)
- Procedures (standard processes)
- Protocols (domain-specific guidelines)
- Compliance requirements (regulatory mandates)

---

## 6. History Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Longitudinal data across time and systems |
| **Example Need** | 8 years of HbA1c trends, 2 previous medication adjustments, specialist referral history |
| **Without It** | Can't reference "ongoing management" or track progression |
| **Layer Mapping** | Layer 1-2 (Storage, Real-Time Data Fabric)  - Longitudinal data access, CDC pipelines |

**Key Attributes:**
- Longitudinal records (data over time)
- Trends and patterns (analysis across time)
- Previous interactions (past agent conversations)
- Cross-system data (unified view)

---

## 7. Tooling Context

| Attribute | Description |
|-----------|-------------|
| **What It Is** | Ability to take action through integrated systems |
| **Example Need** | Trigger prescription orders, schedule labs, create referrals |
| **Without It** | Generated notes can't trigger necessary actions |
| **Layer Mapping** | Layer 7 (Orchestration)  - Workflow integration APIs, action orchestration |

**Key Attributes:**
- Available tools (what actions are possible)
- Tool capabilities (what each tool can do)
- Tool limitations (constraints, costs)
- Action endpoints (how to trigger actions)

---

## Core 7 Assessment

**Scoring:**
- **Full (1 point):** Comprehensive coverage, production-ready
- **Partial (0.5 points):** Some capability, but gaps or limitations
- **None (0 points):** Not available

**Context Coverage:** (Total Points / 7) × 100
**Context Blindness:** 100 - Context Coverage

**Benchmarks:**
- 1/7 (14% coverage): Echo Health's starting point  - severe trust issues
- 4/7 (57% coverage): Common enterprise starting point
- 6/7 (86% coverage): Echo Health's endpoint  - production-ready
- 7/7 (100% coverage): Ideal state

---

# PART 2: THE 10 CONTEXT DOMAINS

Beyond the Core 7, the complete context taxonomy includes 10 domains with 40+ context types.

```
┌─────────────────────────────────────────────────────────────────┐
│                    CONTEXT TAXONOMY                              │
├─────────────────────────────────────────────────────────────────┤
│  CORE 7 (from the book)           │  EXTENDED DOMAINS           │
│  ─────────────────────────        │  ─────────────────────      │
│  1. User Context                  │  Actor Contexts             │
│  2. Task Context                  │  Intent Contexts            │
│  3. Data Context                  │  Data Contexts              │
│  4. Environmental Context         │  Environment Contexts       │
│  5. Business Context              │  Governance Contexts        │
│  6. History Context               │  Memory Contexts            │
│  7. Tooling Context               │  Capability Contexts        │
│                                   │  + Organizational Contexts  │
│                                   │  + Communication Contexts   │
│                                   │  + Quality Contexts         │
└─────────────────────────────────────────────────────────────────┘
```

---

## Domain 1: ACTOR CONTEXTS (Who)

*Core 7 Mapping: Extends User Context*

### 1.1 User Context ⭐ (Core 7)
Who is directly using the agent.
- Identity, Role, Expertise, Preferences, Patterns, Accessibility needs

### 1.2 Audience Context
Who will receive or see the agent's output.
- Primary audience (direct recipient)
- Secondary audience (others who may see output)
- Expertise level (technical vs non-technical)
- Expectations (what they need)

### 1.3 Stakeholder Context
Who else is affected by the agent's actions.
- Affected parties
- Decision makers
- Approvers in workflow
- Interests and concerns

### 1.4 Agent Context
Other agents in the ecosystem.
- Self-awareness (own capabilities, limitations, version)
- Peer agents (available, specializations)
- Supervisor agents (escalation paths)
- Subordinate agents (delegation options)

---

## Domain 2: INTENT CONTEXTS (What & Why)

*Core 7 Mapping: Extends Task Context*

### 2.1 Task Context ⭐ (Core 7)
The specific goal or workflow being accomplished.
- Immediate goal, Task type, Success criteria, Completion state

### 2.2 Goal Context
Higher-level objectives beyond the immediate task.
- Strategic objective (business outcome)
- User's underlying need (why they're really asking)
- Long-term vs short-term goals
- Goal hierarchy (how tasks connect to goals)

### 2.3 Intent Context
Inferred meaning behind user requests.
- Explicit intent (what they stated)
- Implicit intent (what they likely mean)
- Confidence level (how sure are we)
- Clarification needs (when to ask)

### 2.4 Constraint Context
Boundaries and limitations on actions.
- Must do (hard requirements)
- Must not do (prohibitions)
- Should do (soft preferences)
- Trade-off rules (when constraints conflict)

---

## Domain 3: DATA CONTEXTS (Information)

*Core 7 Mapping: Extends Data Context and History Context*

### 3.1 Current Data Context ⭐ (Core 7 - Data)
Data for the immediate task.
- Immediate task data, Freshness, Completeness, Source systems

### 3.2 Historical Data Context ⭐ (Core 7 - History)
Longitudinal data across time.
- Longitudinal records, Trends, Previous interactions, Audit trail

### 3.3 Knowledge Context
Domain knowledge and relationships.
- Domain knowledge (industry-specific)
- Ontology/taxonomy (classification systems)
- Entity relationships (knowledge graph)
- Business rules (encoded logic)

### 3.4 Quality Context
Data quality signals.
- Data quality scores
- Source reliability ratings
- Validation status
- Known gaps and limitations

### 3.5 External Data Context
Data from outside the organization.
- Market data (prices, rates, indices)
- News and events (current affairs)
- Competitor information
- Regulatory updates

---

## Domain 4: MEMORY CONTEXTS (Persistence)

*Core 7 Mapping: Extends History Context*

### 4.1 Conversation Context
Current dialogue state.
- Current turn (immediate exchange)
- Session history (this conversation)
- Thread/topic tracking (conversation branches)
- Pending clarifications (open questions)

### 4.2 Session Context
Current session metadata.
- Session ID
- Start time, duration
- Device and channel
- Session state (active, idle, ending)

### 4.3 Working Memory Context
Temporary processing state.
- Scratchpad (intermediate notes)
- Intermediate results (partial answers)
- Reasoning chain (thought process)
- Hypotheses being tested

### 4.4 Long-term Memory Context
Persistent knowledge across sessions.
- Learned preferences (accumulated understanding)
- Past corrections (what user has fixed)
- Relationship history (interaction patterns)
- Accumulated insights (things learned over time)

---

## Domain 5: ENVIRONMENT CONTEXTS (Where & When)

*Core 7 Mapping: Extends Environmental Context*

### 5.1 Operational Context ⭐ (Core 7 - Environmental)
Physical and operational constraints.
- Resource constraints, Workload, System status, Capacity

### 5.2 Temporal Context
Time-related factors.
- Current time (absolute, with timezone)
- Business hours (working time vs off-hours)
- Deadlines (time constraints)
- Schedules (planned events)

### 5.3 Urgency Context
Priority and time sensitivity.
- Priority level (critical, high, normal, low)
- SLA requirements (response time commitments)
- Time sensitivity (how urgent)
- Escalation thresholds (when to escalate)

### 5.4 Geographic Context
Location-related factors.
- Physical location
- Jurisdiction (legal boundaries)
- Regional variations (local rules)
- Time zone

### 5.5 Channel Context
Communication medium.
- Medium type (chat, voice, email, API)
- Device type (mobile, desktop, kiosk)
- Bandwidth/latency constraints
- Channel capabilities (rich text, images, etc.)

---

## Domain 6: ORGANIZATIONAL CONTEXTS (Structure)

*Core 7 Mapping: New domain (partially related to User and Business)*

### 6.1 Organization Context
Company-level information.
- Company/entity identity
- Industry classification
- Size and scale
- Organizational culture

### 6.2 Team Context
Team-level information.
- Team membership
- Team goals and OKRs
- Collaboration patterns
- Team norms and practices

### 6.3 Hierarchy Context
Reporting and authority structure.
- Reporting structure
- Authority levels
- Approval chains
- Escalation paths

### 6.4 Process Context
Workflow and procedure state.
- Current workflow state
- Standard procedures
- Exception handling rules
- Handoff protocols

---

## Domain 7: GOVERNANCE CONTEXTS (Rules & Controls)

*Core 7 Mapping: Extends Business Context*

### 7.1 Business Rules Context ⭐ (Core 7 - Business)
Organizational policies and procedures.
- Policies, Procedures, Protocols, Best practices

### 7.2 Regulatory Context
Applicable laws and regulations.
- Applicable regulations (HIPAA, GDPR, SOC2, etc.)
- Compliance requirements
- Reporting obligations
- Penalties and risks

### 7.3 Security Context
Security state and controls.
- Authentication state (who they proved they are)
- Authorization level (what they can access)
- Trust score (confidence in identity)
- Security clearance (classification level)

### 7.4 Privacy Context
Data privacy rules.
- Data classification (sensitivity levels)
- Consent status (what user agreed to)
- Minimization rules (least necessary data)
- Retention requirements (how long to keep)

### 7.5 Audit Context
Logging and compliance tracking.
- What to log (required audit events)
- Retention period (how long to keep logs)
- Access tracking (who accessed what)
- Compliance evidence (proof of compliance)

### 7.6 Ethical Context
Ethical considerations.
- Bias considerations (fairness requirements)
- Transparency obligations (explainability)
- Human oversight rules (HITL requirements)
- Harm prevention (safety guardrails)

---

## Domain 8: CAPABILITY CONTEXTS (How)

*Core 7 Mapping: Extends Tooling Context*

### 8.1 Tool Context ⭐ (Core 7 - Tooling)
Available tools and actions.
- Available tools, Tool capabilities, Tool limitations, Tool costs

### 8.2 Integration Context
Connected systems and APIs.
- Connected systems (what's integrated)
- APIs available (callable endpoints)
- Data sources (where to get data)
- Action endpoints (where to send actions)

### 8.3 Model Context
LLM and AI model information.
- Model name and version
- Capabilities (what it can do)
- Limitations (what it can't do)
- Context window (token limits)
- Cost per token/call

### 8.4 Infrastructure Context
Technical infrastructure.
- Compute available (processing power)
- Latency constraints (speed requirements)
- Throughput limits (volume capacity)
- Availability status (uptime)

### 8.5 Cost Context
Budget and resource constraints.
- Budget constraints (spending limits)
- Cost per action (price of each tool use)
- ROI considerations (value vs cost)
- Resource allocation (how to prioritize spend)

---

## Domain 9: COMMUNICATION CONTEXTS (Expression)

*Core 7 Mapping: New domain (partially related to User)*

### 9.1 Language Context
Language and terminology.
- Language (English, Spanish, etc.)
- Dialect/variant (US English vs UK English)
- Translation needs
- Domain terminology (jargon, acronyms)

### 9.2 Cultural Context
Cultural norms and expectations.
- Cultural norms (appropriate behavior)
- Communication style (direct vs indirect)
- Formality level (casual vs formal)
- Taboos and sensitivities

### 9.3 Tone Context
Appropriate tone and voice.
- Appropriate tone (professional, friendly, urgent)
- Emotional state (user's mood)
- Relationship dynamic (new vs established)
- Brand voice (organizational style)

### 9.4 Format Context
Output format requirements.
- Output format (text, JSON, table, etc.)
- Structure requirements (sections, headings)
- Length constraints (brief vs comprehensive)
- Accessibility needs (screen reader, etc.)

---

## Domain 10: QUALITY CONTEXTS (Confidence & Feedback)

*Core 7 Mapping: New domain*

### 10.1 Confidence Context
Certainty and reliability.
- Certainty level (how confident)
- Evidence strength (supporting data)
- Hedging requirements (when to qualify)
- Escalation thresholds (when confidence too low)

### 10.2 Feedback Context
User feedback signals.
- Explicit feedback (ratings, corrections, comments)
- Implicit feedback (behavior patterns, abandonment)
- Historical accuracy (past performance)
- Improvement signals (what to learn)

### 10.3 Validation Context
Verification requirements.
- Verification requirements (what needs checking)
- Fact-checking needs (claims to verify)
- Source citation (attribution requirements)
- Human review triggers (when to escalate)

---

# PART 3: QUICK REFERENCE

## Core 7 → Extended Domain Mapping

| Core 7 Context | Primary Domain | Extended Types |
|----------------|----------------|----------------|
| User Context | Actor | + Audience, Stakeholder, Agent |
| Task Context | Intent | + Goal, Intent, Constraint |
| Data Context | Data | + Knowledge, Quality, External |
| Environmental Context | Environment | + Temporal, Urgency, Geographic, Channel |
| Business Context | Governance | + Regulatory, Security, Privacy, Audit, Ethical |
| History Context | Memory | + Conversation, Session, Working Memory, Long-term Memory |
| Tooling Context | Capability | + Integration, Model, Infrastructure, Cost |
|  - | Organizational | Organization, Team, Hierarchy, Process |
|  - | Communication | Language, Cultural, Tone, Format |
|  - | Quality | Confidence, Feedback, Validation |

---

## Industry-Specific Critical Contexts

### Healthcare
| Priority | Contexts |
|----------|----------|
| Critical | User (physician), Business (protocols), History (patient records), Regulatory (HIPAA), Security, Audit |
| High | Task (visit type), Data (vitals/labs), Ethical (bias), Privacy (PHI) |
| Medium | Tooling (orders), Temporal (appointments), Confidence (clinical decisions) |

### Financial Services
| Priority | Contexts |
|----------|----------|
| Critical | User (advisor), Security (authentication), Regulatory (SEC/FINRA), Audit |
| High | Data (positions), Business (suitability), History (transactions), Privacy |
| Medium | Temporal (market hours), External (market data), Cost (trading fees) |

### Customer Service
| Priority | Contexts |
|----------|----------|
| Critical | User (customer), Task (ticket), Conversation (session history) |
| High | History (interaction history), Tone (sentiment), Urgency (SLA) |
| Medium | Channel (medium), Tooling (CRM), Feedback (CSAT) |

---

## Assessment Levels

| Level | Scope | Use Case |
|-------|-------|----------|
| **Quick (Core 7)** | 7 contexts | Executive summary, initial assessment |
| **Standard (Domains)** | 10 domains | Planning, architecture review |
| **Comprehensive (Types)** | 40+ types | Deep dive, implementation planning |

---

© 2026 Colaberry Inc. All Rights Reserved.
INPACT™ and GOALS™ are trademarks of Colaberry Inc.
