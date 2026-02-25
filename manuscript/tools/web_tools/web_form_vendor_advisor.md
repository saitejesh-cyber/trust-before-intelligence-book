# Vendor Advisor  - Web Tool Specification

## Overview

**URL:** trustbeforeintelligence.ai/vendors
**Purpose:** Conversational AI chatbot for personalized vendor recommendations across the 7-layer architecture
**Lead Capture:** Email required to start conversation
**Knowledge Base:** 90+ products with detailed INPACT/GOALS analysis from `kb_vendor_advisor.md`

---

## User Flow

### Step 1: Landing Page
- Value proposition: "Get personalized technology recommendations for your AI agent stack"
- Key benefits:
  - "90+ products evaluated with INPACT and GOALS scores"
  - "Healthcare, finance, and enterprise expertise"
  - "Budget-tier recommendations ($30K, $150K, $300K+)"
- Echo Health teaser: "See how Echo Health built a 477% ROI stack"
- **CTA Button:** "Start Conversation"

### Step 2: Lead Capture (Before Chat)
Required fields:
- Email (required)
- Name (required)
- Organization (required)

Optional fields:
- Role (dropdown: CTO, VP Engineering, Data Architect, Developer, Other)
- Industry (dropdown: Healthcare, Financial Services, Manufacturing, Retail, Technology, Other)
- Existing cloud platform (dropdown: AWS, Azure, GCP, Multi-cloud, On-prem)

### Step 3: Chat Interface

**Layout:**
- Clean, modern chat interface
- Left: Conversation panel (80% width)
- Right: Context panel (20% width) showing:
  - User profile summary
  - Current layer being discussed
  - Products mentioned in conversation

**Conversation Starter Options:**
After lead capture, present 4 quick-start options:
1. "I need help building a complete stack"
2. "I need a vector database recommendation"
3. "What's the best stack for healthcare?"
4. "Compare [Product A] vs [Product B]"

**Chat Capabilities:**
- Product recommendations by layer
- Head-to-head comparisons
- Budget-tier filtering
- Compliance filtering (HIPAA, SOC2, GDPR)
- Cloud platform filtering

**Suggested Questions (shown as chips):**
- "What's your budget tier?"
- "Which cloud platform?"
- "Need HIPAA compliance?"
- "Compare to alternatives"
- "Show me the Echo stack"

### Step 4: Summary & Export

After conversation, offer:
- **Export Conversation** (PDF)
- **View Stack Recommendation** (link to Stack Builder)
- **Book Consultation** (link to calendar)
- **Continue Chat** (new topic)

---

## Chat Response Format

### Product Recommendation Response
```
**[Product Name]**  - [Vendor]

📊 Scores:
- INPACT: [X]/36 ([Trust Level])
- GOALS: [X]/25 ([Maturity Level])

💰 Pricing: [Tier]  - [Pricing Details]

☁️ Cloud: [AWS | Azure | GCP | Multi-cloud]

✅ Why this product:
- [Reason 1]
- [Reason 2]
- [Reason 3]

⚠️ Trade-offs:
- [Trade-off 1]
- [Trade-off 2]

📚 Book Reference: Chapter [X], Section [Y]
```

### Comparison Response
```
**[Product A] vs [Product B]**

| Criteria | [Product A] | [Product B] |
|----------|-------------|-------------|
| INPACT Score | [X]/36 | [Y]/36 |
| GOALS Score | [X]/25 | [Y]/25 |
| Pricing | [Tier] | [Tier] |
| HIPAA BAA | ✅/❌ | ✅/❌ |
| Best For | [Use Case] | [Use Case] |

**Recommendation:** [Product] because [reason]
```

---

## Knowledge Integration

### Layer-Specific Expertise

| Layer | Products | Key Questions |
|-------|----------|---------------|
| L1: Storage | Vector DBs, Graph DBs, Warehouses | Scale? Query patterns? |
| L2: Real-Time | CDC, Streaming, Ingestion | Latency needs? Volume? |
| L3: Semantic | Semantic layers, Catalogs | Governance needs? |
| L4: Intelligence | RAG, Orchestration, Caching | LLM provider? |
| L5: Governance | ABAC, Audit, Secrets | Compliance? |
| L6: Observability | APM, LLM Monitoring | Debugging needs? |
| L7: Products | Orchestration, Gateways | Multi-agent? |

### Budget Tier Guidance

| Tier | Budget | Monthly | Recommendation Style |
|------|--------|---------|---------------------|
| Lean | $30-50K | $3-5K | Open-source heavy |
| Moderate | $150K | $10-15K | Managed services (recommended) |
| Well-Funded | $300K+ | $25-40K | Enterprise editions |

### Compliance Filtering

For HIPAA users:
- Only recommend products with BAA support
- Highlight "HIPAA BAA Available" badge
- Warn about products without BAA

For SOC 2 users:
- Highlight SOC 2 Type II certified products
- Show certification date

---

## Conversation Memory

**Session Context (maintained during chat):**
- User's industry
- Budget tier
- Cloud platform preference
- Compliance requirements
- Layers already discussed
- Products recommended

**Cross-Reference:**
- After recommending products, suggest: "Want to see how these fit in your stack? Try the Stack Builder tool."
- After INPACT questions, suggest: "Want to assess your current readiness? Try the INPACT Assessment."

---

## Technical Requirements

### Frontend
- Modern chat UI (similar to ChatGPT)
- Streaming responses
- Markdown rendering
- Code block support
- Table rendering
- Mobile responsive

### Backend
- LLM integration (OpenAI GPT-4 or equivalent)
- RAG with vendor knowledge base
- Conversation history storage
- Session management

### Integrations
- Email marketing (lead capture)
- CRM (conversation logging)
- Analytics (conversation metrics)
- Stack Builder (cross-linking)

---

## Design Notes

### Brand Colors
- Primary: Teal (from book cover)
- Secondary: White, Dark Gray
- Accent: Blue for links, Green for positive, Orange for warnings

### Chat Bubbles
- User: Right-aligned, teal background
- Assistant: Left-aligned, gray background
- System: Center-aligned, subtle styling

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | January 2026 | Initial specification |
| 2.0 | January 2026 | Added Technical Implementation Guide |

---

# PART 2: TECHNICAL IMPLEMENTATION GUIDE

> **For AI-Assisted Development (Claude Code, Cursor, Windsurf, etc.)**
>
> This section provides the technical specifications needed to build the Vendor Selection Chatbot. It includes data models, RAG architecture, LLM integration, component structure, and conversation management.

---

## Technology Stack (Recommended)

```
Frontend:
- Framework: Next.js 14+ (App Router)
- Chat UI: Custom or ai/react (Vercel AI SDK)
- Styling: Tailwind CSS
- Markdown: react-markdown + remark-gfm
- Streaming: Server-Sent Events or WebSockets

Backend:
- Runtime: Node.js 18+ or Python 3.11+
- Framework: Next.js API Routes or FastAPI
- LLM: OpenAI GPT-4 / Claude / Azure OpenAI
- Vector Store: Pinecone, Weaviate, or pgvector
- Embeddings: OpenAI text-embedding-3-large
- Database: PostgreSQL with Prisma ORM

Infrastructure:
- Hosting: Vercel, Railway, or AWS
- Vector DB: Pinecone or Supabase pgvector
- Analytics: PostHog or Mixpanel
```

---

## Data Models

### 1. Vendor Product Data

```typescript
// types/vendor.ts

type LayerId = "L1" | "L2" | "L3" | "L4" | "L5" | "L6" | "L7";
type ComponentId = string; // e.g., "vector-db", "cdc", "semantic-layer"

interface VendorProduct {
  id: string;
  name: string;
  vendor: string;
  url: string;

  // Classification
  layer: LayerId;
  component: ComponentId;
  category: string;          // e.g., "Vector Database", "CDC Platform"

  // Scores
  inpactScore: INPACTScore;
  goalsScore: GOALSScore;

  // Pricing
  pricing: PricingInfo;

  // Compliance
  compliance: ComplianceInfo;

  // Cloud
  cloudPlatforms: CloudPlatform[];
  deploymentOptions: DeploymentOption[];

  // Content
  description: string;
  strengths: string[];
  weaknesses: string[];
  bestFor: string[];
  notRecommendedFor: string[];

  // Metadata
  lastUpdated: Date;
  bookReferences: BookReference[];
}

interface INPACTScore {
  I: number;  // Instant (1-6)
  N: number;  // Natural (1-6)
  P: number;  // Permitted (1-6)
  A: number;  // Adaptive (1-6)
  C: number;  // Contextual (1-6)
  T: number;  // Transparent (1-6)
  total: number;  // 6-36
  trustLevel: TrustLevel;
}

interface GOALSScore {
  G: number;  // Governance (1-5)
  O: number;  // Observability (1-5)
  A: number;  // Availability (1-5)
  L: number;  // Lexicon (1-5)
  S: number;  // Solid (1-5)
  total: number;  // 5-25
  maturityLevel: MaturityLevel;
}

type TrustLevel = "high" | "good" | "moderate" | "low";
type MaturityLevel = "production" | "adoption" | "emerging" | "early";

interface PricingInfo {
  model: "subscription" | "usage" | "license" | "free" | "freemium";
  tiers: {
    lean: string;      // $30-50K budget
    moderate: string;  // $150K budget
    enterprise: string; // $300K+ budget
  };
  startingPrice?: string;
  freeTrialDays?: number;
}

interface ComplianceInfo {
  hipaaBAA: boolean;
  soc2Type2: boolean;
  gdprCompliant: boolean;
  iso27001: boolean;
  fedramp: "high" | "moderate" | "low" | "none";
  pciDss: boolean;
  certifications: string[];
}

type CloudPlatform = "aws" | "azure" | "gcp" | "multi-cloud";
type DeploymentOption = "saas" | "self-hosted" | "hybrid" | "on-prem";

interface BookReference {
  chapter: number;
  section?: string;
  context: string;
}
```

### 2. Chat & Session State

```typescript
// types/chat.ts

interface ChatSession {
  id: string;
  leadId: string;
  createdAt: Date;
  updatedAt: Date;

  // User context (gathered during conversation)
  context: UserContext;

  // Conversation
  messages: ChatMessage[];

  // Products discussed
  productsDiscussed: string[];  // Product IDs
  comparisons: ComparisonLog[];
  recommendations: RecommendationLog[];
}

interface UserContext {
  industry?: Industry;
  budgetTier?: BudgetTier;
  cloudPlatform?: CloudPlatform;
  complianceNeeds: string[];
  layersDiscussed: LayerId[];
  currentFocus?: LayerId;
}

interface ChatMessage {
  id: string;
  role: "user" | "assistant" | "system";
  content: string;
  timestamp: Date;

  // Metadata
  productsReferenced?: string[];
  suggestedQuestions?: string[];
  toolCalls?: ToolCall[];
}

interface ComparisonLog {
  products: string[];
  winner?: string;
  reason?: string;
  timestamp: Date;
}

interface RecommendationLog {
  productId: string;
  layer: LayerId;
  score: number;
  reason: string;
  timestamp: Date;
}

type Industry = "healthcare" | "financial" | "manufacturing" | "retail" | "technology" | "other";
type BudgetTier = "lean" | "moderate" | "well-funded";
```

### 3. RAG Context

```typescript
// types/rag.ts

interface VendorChunk {
  id: string;
  productId: string;
  productName: string;
  layer: LayerId;

  // Chunk content
  content: string;
  chunkType: "overview" | "pricing" | "compliance" | "comparison" | "use-case";

  // Embedding
  embedding: number[];  // 1536 or 3072 dimensions

  // Metadata for filtering
  metadata: {
    inpactTotal: number;
    goalsTotal: number;
    hipaaBAA: boolean;
    cloudPlatforms: string[];
    budgetTier: string[];
  };
}

interface RetrievalResult {
  chunks: VendorChunk[];
  relevanceScores: number[];
  productsFound: string[];
}
```

---

## Database Schema

```sql
-- PostgreSQL schema

-- Leads
CREATE TABLE leads (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) NOT NULL UNIQUE,
  name VARCHAR(255) NOT NULL,
  organization VARCHAR(255) NOT NULL,
  role VARCHAR(100),
  industry VARCHAR(50),
  cloud_platform VARCHAR(50),
  created_at TIMESTAMP DEFAULT NOW()
);

-- Chat sessions
CREATE TABLE chat_sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  lead_id UUID REFERENCES leads(id),

  -- Context (JSON)
  context JSONB DEFAULT '{}',

  -- Stats
  message_count INTEGER DEFAULT 0,
  products_discussed TEXT[] DEFAULT '{}',

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Chat messages
CREATE TABLE chat_messages (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id UUID REFERENCES chat_sessions(id) ON DELETE CASCADE,

  role VARCHAR(20) NOT NULL,  -- 'user', 'assistant', 'system'
  content TEXT NOT NULL,

  -- Metadata
  products_referenced TEXT[] DEFAULT '{}',
  suggested_questions TEXT[] DEFAULT '{}',
  tool_calls JSONB,

  created_at TIMESTAMP DEFAULT NOW()
);

-- Product recommendations log
CREATE TABLE recommendation_logs (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id UUID REFERENCES chat_sessions(id),
  product_id VARCHAR(100) NOT NULL,
  layer VARCHAR(10) NOT NULL,
  reason TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Indexes
CREATE INDEX idx_sessions_lead ON chat_sessions(lead_id);
CREATE INDEX idx_messages_session ON chat_messages(session_id);
CREATE INDEX idx_messages_created ON chat_messages(created_at);
```

---

## RAG Architecture

### 1. Knowledge Base Preparation

```typescript
// lib/rag/prepare.ts

import { VendorProduct, VendorChunk } from "@/types/vendor";

function chunkProduct(product: VendorProduct): VendorChunk[] {
  const chunks: VendorChunk[] = [];

  // Overview chunk
  chunks.push({
    id: `${product.id}-overview`,
    productId: product.id,
    productName: product.name,
    layer: product.layer,
    content: formatOverview(product),
    chunkType: "overview",
    embedding: [],  // Will be computed
    metadata: extractMetadata(product)
  });

  // Pricing chunk
  chunks.push({
    id: `${product.id}-pricing`,
    productId: product.id,
    productName: product.name,
    layer: product.layer,
    content: formatPricing(product),
    chunkType: "pricing",
    embedding: [],
    metadata: extractMetadata(product)
  });

  // Compliance chunk
  if (hasComplianceInfo(product)) {
    chunks.push({
      id: `${product.id}-compliance`,
      productId: product.id,
      productName: product.name,
      layer: product.layer,
      content: formatCompliance(product),
      chunkType: "compliance",
      embedding: [],
      metadata: extractMetadata(product)
    });
  }

  return chunks;
}

function formatOverview(product: VendorProduct): string {
  return `
# ${product.name} by ${product.vendor}

## Layer ${product.layer}: ${product.category}

**INPACT Score: ${product.inpactScore.total}/36 (${product.inpactScore.trustLevel})**
- Instant: ${product.inpactScore.I}/6
- Natural: ${product.inpactScore.N}/6
- Permitted: ${product.inpactScore.P}/6
- Adaptive: ${product.inpactScore.A}/6
- Contextual: ${product.inpactScore.C}/6
- Transparent: ${product.inpactScore.T}/6

**GOALS Score: ${product.goalsScore.total}/25 (${product.goalsScore.maturityLevel})**

## Description
${product.description}

## Strengths
${product.strengths.map(s => `- ${s}`).join("\n")}

## Best For
${product.bestFor.map(b => `- ${b}`).join("\n")}

## Trade-offs
${product.weaknesses.map(w => `- ${w}`).join("\n")}
`.trim();
}

function formatPricing(product: VendorProduct): string {
  return `
# ${product.name} Pricing

**Pricing Model:** ${product.pricing.model}

## Budget Tier Recommendations

| Budget Tier | Recommendation |
|-------------|----------------|
| Lean ($30-50K) | ${product.pricing.tiers.lean} |
| Moderate ($150K) | ${product.pricing.tiers.moderate} |
| Enterprise ($300K+) | ${product.pricing.tiers.enterprise} |

${product.pricing.startingPrice ? `**Starting Price:** ${product.pricing.startingPrice}` : ""}
${product.pricing.freeTrialDays ? `**Free Trial:** ${product.pricing.freeTrialDays} days` : ""}
`.trim();
}

function formatCompliance(product: VendorProduct): string {
  return `
# ${product.name} Compliance

**HIPAA BAA:** ${product.compliance.hipaaBAA ? "✅ Available" : "❌ Not Available"}
**SOC 2 Type II:** ${product.compliance.soc2Type2 ? "✅ Certified" : "❌ Not Certified"}
**GDPR:** ${product.compliance.gdprCompliant ? "✅ Compliant" : "❌ Not Verified"}
**ISO 27001:** ${product.compliance.iso27001 ? "✅ Certified" : "❌ Not Certified"}
**FedRAMP:** ${product.compliance.fedramp !== "none" ? product.compliance.fedramp.toUpperCase() : "Not Applicable"}
**PCI-DSS:** ${product.compliance.pciDss ? "✅ Compliant" : "❌ Not Applicable"}

**Additional Certifications:**
${product.compliance.certifications.map(c => `- ${c}`).join("\n") || "None listed"}
`.trim();
}
```

### 2. Vector Store Integration

```typescript
// lib/rag/vectorStore.ts

import { Pinecone } from "@pinecone-database/pinecone";
import { OpenAI } from "openai";
import { VendorChunk, RetrievalResult } from "@/types/rag";

const pinecone = new Pinecone();
const openai = new OpenAI();

const INDEX_NAME = "vendor-advisor";

// Embed and upsert chunks
async function indexChunks(chunks: VendorChunk[]): Promise<void> {
  const index = pinecone.Index(INDEX_NAME);

  // Get embeddings
  const embeddings = await openai.embeddings.create({
    model: "text-embedding-3-large",
    input: chunks.map(c => c.content),
    dimensions: 1536
  });

  // Prepare vectors
  const vectors = chunks.map((chunk, i) => ({
    id: chunk.id,
    values: embeddings.data[i].embedding,
    metadata: {
      productId: chunk.productId,
      productName: chunk.productName,
      layer: chunk.layer,
      chunkType: chunk.chunkType,
      ...chunk.metadata
    }
  }));

  // Upsert in batches
  const batchSize = 100;
  for (let i = 0; i < vectors.length; i += batchSize) {
    await index.upsert(vectors.slice(i, i + batchSize));
  }
}

// Retrieve relevant chunks
async function retrieveChunks(
  query: string,
  filters: RetrievalFilters,
  topK: number = 10
): Promise<RetrievalResult> {
  const index = pinecone.Index(INDEX_NAME);

  // Get query embedding
  const embedding = await openai.embeddings.create({
    model: "text-embedding-3-large",
    input: query,
    dimensions: 1536
  });

  // Build filter
  const filter: Record<string, any> = {};
  if (filters.layer) filter.layer = filters.layer;
  if (filters.hipaaRequired) filter.hipaaBAA = true;
  if (filters.cloudPlatform) filter.cloudPlatforms = { $in: [filters.cloudPlatform] };
  if (filters.budgetTier) filter.budgetTier = { $in: [filters.budgetTier] };

  // Query
  const results = await index.query({
    vector: embedding.data[0].embedding,
    topK,
    filter: Object.keys(filter).length > 0 ? filter : undefined,
    includeMetadata: true
  });

  // Map to chunks
  const chunks = results.matches.map(match => ({
    id: match.id,
    productId: match.metadata?.productId as string,
    productName: match.metadata?.productName as string,
    layer: match.metadata?.layer as LayerId,
    content: "", // Fetch from DB if needed
    chunkType: match.metadata?.chunkType as string,
    embedding: [],
    metadata: match.metadata as any
  }));

  return {
    chunks,
    relevanceScores: results.matches.map(m => m.score || 0),
    productsFound: [...new Set(chunks.map(c => c.productId))]
  };
}

interface RetrievalFilters {
  layer?: LayerId;
  hipaaRequired?: boolean;
  cloudPlatform?: CloudPlatform;
  budgetTier?: BudgetTier;
}
```

---

## LLM Integration

### 1. System Prompt

```typescript
// lib/chat/prompts.ts

export const SYSTEM_PROMPT = `You are the Vendor Selection Advisor from "Trust Before Intelligence" by Ram Katamaraja. You help organizations select the right technology products for their AI agent infrastructure.

## Your Role
- Recommend products from the 7-layer architecture based on user needs
- Compare products objectively using INPACT and GOALS scores
- Filter recommendations by budget tier, cloud platform, and compliance
- Reference the book's frameworks when explaining recommendations

## Knowledge
You have access to 90+ products with detailed analysis across 7 layers:
- Layer 1: Multi-Modal Storage (Vector DBs, Graph DBs, Warehouses)
- Layer 2: Real-Time Data Fabric (CDC, Streaming, Ingestion)
- Layer 3: Universal Semantic Layer (Semantic Platforms, Catalogs)
- Layer 4: Intelligence Orchestration (RAG, Embeddings, Caching)
- Layer 5: Agent-Aware Governance (ABAC, Audit, Secrets)
- Layer 6: Observability & Feedback (APM, LLM Monitoring)
- Layer 7: Self-Service Data Products (Orchestration, Gateways)

## Scoring Frameworks

**INPACT (Agent Trust Needs)  - 6-36 points:**
- I = Instant (1-6): Sub-second response times
- N = Natural (1-6): Business language understanding
- P = Permitted (1-6): Dynamic authorization
- A = Adaptive (1-6): Continuous learning
- C = Contextual (1-6): Multi-system integration
- T = Transparent (1-6): Audit and explainability

Trust Levels:
- 30-36: High Trust (production-ready for healthcare)
- 24-29: Good Trust (most enterprise use)
- 18-23: Moderate Trust (internal tools)
- <18: Low Trust (not recommended)

**GOALS (Operational Readiness)  - 5-25 points:**
- G = Governance (1-5)
- O = Observability (1-5)
- A = Availability (1-5)
- L = Lexicon (1-5)
- S = Solid (1-5)

Maturity Levels:
- 21-25: Production-Grade
- 16-20: Adoption-Ready
- 11-15: Emerging
- <11: Early-Stage

## Guidelines
1. Always ask about budget tier, cloud platform, and compliance needs if not known
2. For healthcare users, ONLY recommend products with HIPAA BAA
3. Format recommendations using the structured template
4. When comparing products, use tables for clarity
5. Reference book chapters when relevant
6. Suggest the Stack Builder tool after providing recommendations

## Response Format
Use markdown formatting with:
- Bold for product names and scores
- Tables for comparisons
- Bullet points for lists
- Code blocks for technical details

## Important
- Be honest about trade-offs
- Never recommend products without verified data
- Acknowledge when a product may not be the best fit
- Suggest alternatives when the primary choice has limitations`;
```

### 2. Chat Completion

```typescript
// lib/chat/completion.ts

import OpenAI from "openai";
import { ChatMessage, UserContext } from "@/types/chat";
import { retrieveChunks } from "@/lib/rag/vectorStore";
import { SYSTEM_PROMPT } from "./prompts";

const openai = new OpenAI();

interface ChatCompletionInput {
  messages: ChatMessage[];
  context: UserContext;
  userMessage: string;
}

export async function getChatCompletion(
  input: ChatCompletionInput
): Promise<ReadableStream<Uint8Array>> {
  const { messages, context, userMessage } = input;

  // Build filters from context
  const filters = {
    layer: context.currentFocus,
    hipaaRequired: context.complianceNeeds.includes("hipaa"),
    cloudPlatform: context.cloudPlatform,
    budgetTier: context.budgetTier
  };

  // Retrieve relevant context
  const retrieved = await retrieveChunks(userMessage, filters, 8);

  // Build context string
  const retrievedContext = retrieved.chunks
    .map(c => `---\n${c.content}\n---`)
    .join("\n\n");

  // Build messages array
  const llmMessages: OpenAI.ChatCompletionMessageParam[] = [
    { role: "system", content: SYSTEM_PROMPT },
    {
      role: "system",
      content: `## User Context
- Industry: ${context.industry || "Not specified"}
- Budget Tier: ${context.budgetTier || "Not specified"}
- Cloud Platform: ${context.cloudPlatform || "Not specified"}
- Compliance Needs: ${context.complianceNeeds.join(", ") || "None specified"}
- Layers Discussed: ${context.layersDiscussed.join(", ") || "None yet"}`
    },
    {
      role: "system",
      content: `## Relevant Products\n\n${retrievedContext}`
    },
    // Previous conversation
    ...messages.map(m => ({
      role: m.role as "user" | "assistant",
      content: m.content
    })),
    // Current user message
    { role: "user", content: userMessage }
  ];

  // Get streaming completion
  const response = await openai.chat.completions.create({
    model: "gpt-4-turbo-preview",
    messages: llmMessages,
    stream: true,
    temperature: 0.7,
    max_tokens: 2000
  });

  // Return as ReadableStream for SSE
  return response.toReadableStream();
}
```

---

## API Endpoints

```typescript
// Next.js App Router API Routes

// POST /api/chat/sessions - Start new chat session
interface CreateSessionRequest {
  lead: {
    email: string;
    name: string;
    organization: string;
    role?: string;
    industry?: Industry;
    cloudPlatform?: CloudPlatform;
  };
}

interface CreateSessionResponse {
  sessionId: string;
  starterOptions: string[];
}

// GET /api/chat/sessions/:id - Get session with messages
interface GetSessionResponse {
  session: ChatSession;
  messages: ChatMessage[];
}

// POST /api/chat/sessions/:id/messages - Send message (streaming)
interface SendMessageRequest {
  content: string;
}
// Response: Server-Sent Events stream

// PATCH /api/chat/sessions/:id/context - Update session context
interface UpdateContextRequest {
  context: Partial<UserContext>;
}

// GET /api/chat/sessions/:id/export - Export conversation as PDF
interface ExportResponse {
  pdfUrl: string;
  expiresAt: Date;
}

// GET /api/products - Get all products (for filtering UI)
interface GetProductsResponse {
  products: VendorProduct[];
  layers: LayerInfo[];
  filters: FilterOptions;
}

// GET /api/products/:id - Get single product details
interface GetProductResponse {
  product: VendorProduct;
  relatedProducts: VendorProduct[];
}

// POST /api/products/compare - Compare multiple products
interface CompareRequest {
  productIds: string[];
}

interface CompareResponse {
  products: VendorProduct[];
  comparisonTable: ComparisonRow[];
  recommendation: string;
}
```

---

## React Components

### 1. Component Structure

```
components/
├── chat/
│   ├── ChatInterface.tsx      # Main chat container
│   ├── MessageList.tsx        # Scrollable message list
│   ├── MessageBubble.tsx      # Single message
│   ├── InputArea.tsx          # Text input + send button
│   ├── StarterOptions.tsx     # Quick-start chips
│   ├── SuggestedQuestions.tsx # Follow-up suggestions
│   ├── TypingIndicator.tsx    # Loading animation
│   └── ContextPanel.tsx       # Right sidebar
├── products/
│   ├── ProductCard.tsx        # Product summary card
│   ├── ProductComparison.tsx  # Side-by-side table
│   ├── ScoreBadge.tsx         # INPACT/GOALS badge
│   └── ComplianceBadges.tsx   # HIPAA, SOC2, etc.
├── lead/
│   └── LeadCaptureForm.tsx    # Email collection
└── ui/
    ├── Button.tsx
    ├── Input.tsx
    ├── Card.tsx
    └── Badge.tsx
```

### 2. Chat Interface Component

```tsx
// components/chat/ChatInterface.tsx

"use client";

import { useState, useRef, useEffect } from "react";
import { useChat } from "ai/react";  // Vercel AI SDK
import { MessageList } from "./MessageList";
import { InputArea } from "./InputArea";
import { ContextPanel } from "./ContextPanel";
import { StarterOptions } from "./StarterOptions";

interface Props {
  sessionId: string;
  initialContext: UserContext;
}

export function ChatInterface({ sessionId, initialContext }: Props) {
  const [context, setContext] = useState<UserContext>(initialContext);
  const [showStarters, setShowStarters] = useState(true);
  const messagesEndRef = useRef<HTMLDivElement>(null);

  const {
    messages,
    input,
    handleInputChange,
    handleSubmit,
    isLoading,
    append
  } = useChat({
    api: `/api/chat/sessions/${sessionId}/messages`,
    body: { context },
    onFinish: (message) => {
      // Update context based on conversation
      updateContextFromMessage(message.content);
    }
  });

  const handleStarterClick = (starter: string) => {
    setShowStarters(false);
    append({ role: "user", content: starter });
  };

  useEffect(() => {
    messagesEndRef.current?.scrollIntoView({ behavior: "smooth" });
  }, [messages]);

  return (
    <div className="flex h-screen bg-gray-50">
      {/* Main chat area */}
      <div className="flex-1 flex flex-col">
        {/* Header */}
        <header className="bg-white border-b px-6 py-4">
          <h1 className="text-xl font-semibold text-gray-900">
            Vendor Selection Advisor
          </h1>
          <p className="text-sm text-gray-500">
            Get personalized technology recommendations
          </p>
        </header>

        {/* Messages */}
        <div className="flex-1 overflow-y-auto p-6">
          {messages.length === 0 && showStarters ? (
            <div className="max-w-2xl mx-auto">
              <div className="text-center mb-8">
                <h2 className="text-2xl font-semibold text-gray-900 mb-2">
                  How can I help you today?
                </h2>
                <p className="text-gray-600">
                  I can recommend products, compare options, and help you build your stack.
                </p>
              </div>
              <StarterOptions onSelect={handleStarterClick} />
            </div>
          ) : (
            <MessageList
              messages={messages}
              isLoading={isLoading}
            />
          )}
          <div ref={messagesEndRef} />
        </div>

        {/* Input */}
        <InputArea
          value={input}
          onChange={handleInputChange}
          onSubmit={handleSubmit}
          isLoading={isLoading}
          placeholder="Ask about products, compare options, or get recommendations..."
        />
      </div>

      {/* Context panel */}
      <ContextPanel
        context={context}
        productsDiscussed={extractProductsFromMessages(messages)}
      />
    </div>
  );
}
```

### 3. Message Bubble Component

```tsx
// components/chat/MessageBubble.tsx

import { memo } from "react";
import ReactMarkdown from "react-markdown";
import remarkGfm from "remark-gfm";
import { Message } from "ai";

interface Props {
  message: Message;
}

export const MessageBubble = memo(function MessageBubble({ message }: Props) {
  const isUser = message.role === "user";

  return (
    <div
      className={`flex ${isUser ? "justify-end" : "justify-start"} mb-4`}
    >
      <div
        className={`max-w-[80%] rounded-2xl px-4 py-3 ${
          isUser
            ? "bg-teal-600 text-white"
            : "bg-white border border-gray-200 text-gray-900"
        }`}
      >
        {isUser ? (
          <p className="whitespace-pre-wrap">{message.content}</p>
        ) : (
          <ReactMarkdown
            remarkPlugins={[remarkGfm]}
            components={{
              // Custom rendering for markdown elements
              table: ({ children }) => (
                <div className="overflow-x-auto my-4">
                  <table className="min-w-full divide-y divide-gray-200 text-sm">
                    {children}
                  </table>
                </div>
              ),
              th: ({ children }) => (
                <th className="px-3 py-2 bg-gray-50 text-left font-semibold">
                  {children}
                </th>
              ),
              td: ({ children }) => (
                <td className="px-3 py-2 border-t">{children}</td>
              ),
              code: ({ inline, children }) =>
                inline ? (
                  <code className="bg-gray-100 px-1 py-0.5 rounded text-sm">
                    {children}
                  </code>
                ) : (
                  <pre className="bg-gray-900 text-gray-100 p-4 rounded-lg overflow-x-auto my-4">
                    <code>{children}</code>
                  </pre>
                ),
              a: ({ href, children }) => (
                <a
                  href={href}
                  target="_blank"
                  rel="noopener noreferrer"
                  className="text-teal-600 hover:underline"
                >
                  {children}
                </a>
              )
            }}
          >
            {message.content}
          </ReactMarkdown>
        )}
      </div>
    </div>
  );
});
```

### 4. Context Panel Component

```tsx
// components/chat/ContextPanel.tsx

import { UserContext } from "@/types/chat";
import { ScoreBadge } from "@/components/products/ScoreBadge";

interface Props {
  context: UserContext;
  productsDiscussed: ProductSummary[];
}

export function ContextPanel({ context, productsDiscussed }: Props) {
  return (
    <aside className="w-80 bg-white border-l p-6 overflow-y-auto">
      {/* User context */}
      <section className="mb-8">
        <h3 className="text-sm font-semibold text-gray-500 uppercase tracking-wide mb-4">
          Your Context
        </h3>

        <dl className="space-y-3">
          {context.industry && (
            <div>
              <dt className="text-xs text-gray-500">Industry</dt>
              <dd className="font-medium capitalize">{context.industry}</dd>
            </div>
          )}
          {context.budgetTier && (
            <div>
              <dt className="text-xs text-gray-500">Budget Tier</dt>
              <dd className="font-medium capitalize">{context.budgetTier}</dd>
            </div>
          )}
          {context.cloudPlatform && (
            <div>
              <dt className="text-xs text-gray-500">Cloud Platform</dt>
              <dd className="font-medium uppercase">{context.cloudPlatform}</dd>
            </div>
          )}
          {context.complianceNeeds.length > 0 && (
            <div>
              <dt className="text-xs text-gray-500">Compliance</dt>
              <dd className="flex flex-wrap gap-1 mt-1">
                {context.complianceNeeds.map((c) => (
                  <span
                    key={c}
                    className="bg-blue-100 text-blue-800 text-xs px-2 py-0.5 rounded"
                  >
                    {c.toUpperCase()}
                  </span>
                ))}
              </dd>
            </div>
          )}
        </dl>
      </section>

      {/* Products discussed */}
      {productsDiscussed.length > 0 && (
        <section>
          <h3 className="text-sm font-semibold text-gray-500 uppercase tracking-wide mb-4">
            Products Discussed
          </h3>

          <ul className="space-y-3">
            {productsDiscussed.map((product) => (
              <li
                key={product.id}
                className="bg-gray-50 rounded-lg p-3"
              >
                <div className="font-medium text-sm">{product.name}</div>
                <div className="text-xs text-gray-500">
                  Layer {product.layer}
                </div>
                <div className="flex gap-2 mt-2">
                  <ScoreBadge
                    type="inpact"
                    score={product.inpactScore}
                    size="sm"
                  />
                  <ScoreBadge
                    type="goals"
                    score={product.goalsScore}
                    size="sm"
                  />
                </div>
              </li>
            ))}
          </ul>
        </section>
      )}

      {/* Cross-links */}
      <section className="mt-8 pt-6 border-t">
        <h3 className="text-sm font-semibold text-gray-500 uppercase tracking-wide mb-4">
          Related Tools
        </h3>

        <div className="space-y-2">
          <a
            href="/stack"
            className="block text-sm text-teal-600 hover:text-teal-700"
          >
            🔧 Build Your Stack →
          </a>
          <a
            href="/assessment"
            className="block text-sm text-teal-600 hover:text-teal-700"
          >
            📊 INPACT Assessment →
          </a>
          <a
            href="/book"
            className="block text-sm text-teal-600 hover:text-teal-700"
          >
            📚 Get the Book →
          </a>
        </div>
      </section>
    </aside>
  );
}
```

---

## File Structure Summary

```
vendor-chatbot/
├── app/
│   ├── page.tsx                      # Landing page
│   ├── vendors/
│   │   ├── page.tsx                  # Lead capture → chat
│   │   └── [sessionId]/
│   │       └── page.tsx              # Chat interface
│   ├── api/
│   │   ├── chat/
│   │   │   └── sessions/
│   │   │       ├── route.ts          # POST: create session
│   │   │       └── [id]/
│   │   │           ├── route.ts      # GET session
│   │   │           ├── messages/route.ts # POST: send message (streaming)
│   │   │           ├── context/route.ts  # PATCH: update context
│   │   │           └── export/route.ts   # GET: export PDF
│   │   └── products/
│   │       ├── route.ts              # GET all products
│   │       ├── [id]/route.ts         # GET single product
│   │       └── compare/route.ts      # POST: compare products
├── components/
│   ├── chat/                         # Chat UI components
│   ├── products/                     # Product display components
│   ├── lead/                         # Lead capture
│   └── ui/                           # Shared UI components
├── lib/
│   ├── chat/
│   │   ├── prompts.ts                # System prompts
│   │   └── completion.ts             # LLM integration
│   ├── rag/
│   │   ├── prepare.ts                # Chunk products
│   │   └── vectorStore.ts            # Vector operations
│   ├── db/
│   │   └── prisma.ts                 # Database client
│   └── products/
│       └── data.ts                   # Product definitions
├── types/
│   ├── vendor.ts
│   ├── chat.ts
│   └── rag.ts
└── prisma/
    └── schema.prisma
```

---

## Quick Start for AI Coding Tools

```markdown
## Instructions for Claude Code / Cursor / Windsurf

1. **Create Next.js app:**
   ```bash
   npx create-next-app@latest vendor-chatbot --typescript --tailwind --app
   cd vendor-chatbot
   npm install ai openai @pinecone-database/pinecone react-markdown remark-gfm
   npm install zustand @prisma/client
   npm install -D prisma
   ```

2. **Set up environment:**
   ```env
   OPENAI_API_KEY=sk-...
   PINECONE_API_KEY=...
   PINECONE_INDEX=vendor-advisor
   DATABASE_URL=postgresql://...
   ```

3. **Create types:**
   - Copy all interfaces from "Data Models" section to `types/`

4. **Prepare product data:**
   - Parse `kb_vendor_advisor.md` into JSON product objects
   - Chunk products using the chunking functions
   - Embed and index in Pinecone

5. **Implement RAG:**
   - Copy vector store functions to `lib/rag/`
   - Test retrieval with sample queries

6. **Build chat backend:**
   - Copy LLM integration to `lib/chat/`
   - Create API routes for sessions and messages
   - Implement streaming responses

7. **Build chat UI:**
   - Use Vercel AI SDK's `useChat` hook
   - Build MessageList, MessageBubble, InputArea components
   - Add ContextPanel for session info

8. **Test the flow:**
   - Lead capture → Start chat → Ask questions → Get recommendations
   - Verify streaming, markdown rendering, product references
```