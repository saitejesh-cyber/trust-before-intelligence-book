# Compliance Navigator  - Web Tool Specification

## Overview

**URL:** trustbeforeintelligence.ai/compliance
**Purpose:** Interactive compliance assessment for AI agent deployments across 30 regulatory categories
**Lead Capture:** Email required to access navigator
**Knowledge Base:** 200+ frameworks from `kb_compliance_navigator.md`

---

## Key Differentiator

Unlike single-industry compliance tools, this is a **universal compliance navigator** that covers:
- **30 compliance categories** (not just healthcare)
- **200+ regulatory frameworks** globally
- **Industry-specific profiles** (Healthcare, Finance, Education, Government, etc.)
- **Geographic filtering** (USA, EU, UK, APAC, etc.)
- **7-Layer architecture mapping** for remediation

---

## User Flow

### Step 1: Landing Page
- Value proposition: "Navigate AI compliance across 200+ regulatory frameworks"
- Key features:
  - "30 compliance categories from healthcare to AI ethics"
  - "Global coverage: GDPR, HIPAA, PCI-DSS, EU AI Act, and more"
  - "Personalized assessment based on your industry and geography"
  - "7-Layer remediation guidance"
- **CTA Button:** "Start Compliance Check"

### Step 2: Lead Capture
Required fields:
- Email (required)
- Name (required)
- Organization (required)
- Role (required)

Optional fields:
- Industry (dropdown: Healthcare, Financial Services, Education, Government, Manufacturing, Retail, Technology, Other)
- Organization size (dropdown)

### Step 3: Compliance Profile Setup

**Step 3a: Geographic Scope**
Select all regions where you operate or process data:
- [ ] United States (Federal)
- [ ] United States (California)
- [ ] United States (Other States)
- [ ] European Union / EEA
- [ ] United Kingdom
- [ ] Canada
- [ ] Asia-Pacific
- [ ] Latin America
- [ ] Middle East & Africa

**Step 3b: Industry Selection**
Select your primary industry (determines mandatory frameworks):
- Healthcare
- Financial Services
- Insurance
- Education
- Government (Federal)
- Government (State/Local)
- Defense/Aerospace
- Manufacturing
- Retail/eCommerce
- Technology
- Telecommunications
- Energy/Utilities
- Legal/Professional Services
- Other

**Step 3c: Data Types Processed**
Select all data types your AI agents will handle:
- [ ] Personal Identifiable Information (PII)
- [ ] Protected Health Information (PHI)
- [ ] Payment Card Data (PCI)
- [ ] Financial Data
- [ ] Employee Data
- [ ] Student Data
- [ ] Children's Data (under 13)
- [ ] Biometric Data
- [ ] Government Classified Data
- [ ] Intellectual Property

**Step 3d: AI Use Cases**
Select planned AI agent use cases:
- [ ] Customer Service
- [ ] Internal Employees
- [ ] Healthcare/Clinical
- [ ] Financial Advisory
- [ ] HR/Recruiting
- [ ] Legal/Contract Review
- [ ] Content Generation
- [ ] Decision Support
- [ ] Autonomous Actions

### Step 4: Assessment Interface

**Based on profile, generate personalized compliance checklist**

**Layout:** Category-based navigation with compliance status

**Navigation:**
- Left: 30 categories (filtered by relevance)
- Main: Checklist for selected category
- Right: Overall compliance score + export

**Per Category View:**
- Category name + description
- Applicable frameworks (filtered by geography/industry)
- Compliance status per framework
- Requirements checklist
- 7-Layer remediation mapping

**Relevance Filtering:**
- Categories marked as "Mandatory" | "Recommended" | "Optional" based on profile
- Mandatory categories expanded by default
- Irrelevant categories hidden or grayed out

### Step 5: Results Dashboard

**Compliance Score:**
- Overall percentage (X% compliant)
- Risk level (Low / Medium / High / Critical)

**Category Breakdown:**
- Grid of 30 categories with status badges
- Click to drill into specific frameworks

**Critical Gaps:**
- List of non-compliant mandatory frameworks
- Penalty exposure estimates
- Remediation priority

**7-Layer Remediation:**
- Which layers address which compliance gaps
- Recommended products per gap

**Export Options:**
- PDF Compliance Report
- Excel Checklist
- Share with compliance team

---

## The 30 Compliance Categories

### Tier 1: Core Categories (Always Relevant)
| # | Category | Frameworks | Key Regulations |
|---|----------|------------|-----------------|
| 1 | Data Privacy | 14 | GDPR, CCPA, LGPD, PIPEDA |
| 2 | Health Data | 10 | HIPAA, HITECH, HITRUST |
| 3 | Financial Data | 10 | GLBA, PCI-DSS, SOX |
| 4 | AI-Specific | 9 | EU AI Act, NYC LL 144, NIST AI RMF |
| 5 | Information Security | 8 | SOC 2, ISO 27001, NIST CSF |
| 6 | Government & Security | 11 | FedRAMP, FISMA, CMMC |

### Tier 2: Industry-Specific
| # | Category | Frameworks | Key Regulations |
|---|----------|------------|-----------------|
| 7 | Education Data | 4 | FERPA, COPPA, SOPIPA |
| 8 | Industry-Specific | 8 | NERC CIP, FDA, FCC |
| 9 | Consumer Protection | 7 | FTC Act, ADA, TCPA |
| 10 | International & Cross-Border | 7 | SCCs, APEC CBPR, OFAC |
| 11 | Employment & HR | 7 | EEOC, FLSA, WARN Act |
| 12 | Audit & Attestation | 8 | SOC 1/2/3, HITRUST Cert |

### Tier 3: Specialized Categories
| # | Category | Frameworks | Key Regulations |
|---|----------|------------|-----------------|
| 13 | Ethical AI | 8 | IEEE Ethics, AI Bill of Rights |
| 14 | Intellectual Property | 7 | Copyright, DMCA, Trade Secrets |
| 15 | Content Moderation | 7 | DSA, Section 230, NetzDG |
| 16 | Accessibility | 6 | ADA, Section 508, WCAG |
| 17 | Environmental & ESG | 5 | CSRD, SEC Climate, GRI |
| 18 | Insurance | 4 | State Insurance Laws, NAIC |
| 19 | Telecommunications | 4 | FCC, CPNI, Wiretap Laws |
| 20 | Real Estate | 4 | RESPA, Fair Housing, BSA |

### Tier 4: Emerging & Regional
| # | Category | Frameworks | Key Regulations |
|---|----------|------------|-----------------|
| 21 | Children's Privacy | 4 | COPPA, UK Age Appropriate Design |
| 22 | Biometric Data | 4 | BIPA, GDPR Biometrics |
| 23 | Marketing & Advertising | 4 | CAN-SPAM, TCPA, ePrivacy |
| 24 | Records Retention | 4 | Industry-specific retention rules |
| 25 | Crisis & Incident | 4 | Breach notification laws |
| 26 | Third-Party Risk | 4 | Vendor management requirements |
| 27 | Model Governance | 4 | Model risk management (SR 11-7) |
| 28 | Supply Chain | 4 | USMCA, conflict minerals |
| 29 | Emerging Regulations | 5 | State AI laws, EU developments |
| 30 | Industry Standards | 5 | Voluntary best practices |

---

## Compliance Item Structure

### Per Framework Checklist Item
```
┌────────────────────────────────────────────────────────────────┐
│ ☐ HIPAA Security Rule  - Technical Safeguards (§164.312)       │
│                                                                │
│ Category: Health Data                                          │
│ Geography: United States                                       │
│ Mandatory For: Healthcare providers, health plans, clearinghouses
│                                                                │
│ Requirements:                                                  │
│ ☐ Access Control (unique IDs, MFA, ABAC)                      │
│ ☐ Audit Logging (100% PHI access, 6-year retention)           │
│ ☐ Encryption at Rest (AES-256)                                │
│ ☐ Encryption in Transit (TLS 1.2+)                            │
│ ☐ Emergency Access Procedures                                  │
│                                                                │
│ Status: ○ Compliant  ○ Partial  ○ Non-Compliant  ○ N/A        │
│                                                                │
│ Evidence Notes: [________________________]                     │
│                                                                │
│ 7-Layer Mapping:                                               │
│ • Layer 1: Encryption at rest (Snowflake, Azure SQL)          │
│ • Layer 5: Access control (Azure AD, OPA)                     │
│ • Layer 6: Audit logging (Datadog, Splunk)                    │
│                                                                │
│ Penalty: $100-$1.5M per violation type/year                   │
└────────────────────────────────────────────────────────────────┘
```

---

## Scoring & Risk Logic

### Compliance Scoring
| Status | Points | Weight |
|--------|--------|--------|
| Compliant | 2 | 1.0x |
| Partial | 1 | 1.0x |
| Non-Compliant | 0 | 1.0x |
| N/A | Excluded | - |

**Mandatory frameworks:** 2x weight
**High-penalty frameworks:** 1.5x weight

### Risk Level Calculation
| Compliance % | Mandatory Gaps | Risk Level |
|--------------|----------------|------------|
| 90%+ | 0 | Low |
| 75-89% | 0 | Medium |
| 75%+ | 1+ | High |
| <75% | Any | Critical |

### Penalty Exposure Estimate
- Sum of maximum penalties for non-compliant mandatory frameworks
- Show range (minimum to maximum)
- Industry-specific guidance

---

## 7-Layer Remediation Mapping

For each compliance gap, show which infrastructure layers provide remediation:

| Requirement | Layer | Products |
|-------------|-------|----------|
| Access Control | L5 | Azure AD, OPA, Cerbos |
| Encryption | L1 | Snowflake, Azure SQL TDE |
| Audit Logging | L6 | Splunk, Datadog, ELK |
| Data Masking | L3 | Privacera, Immuta |
| Consent Management | L7 | OneTrust, TrustArc |
| Bias Testing | L4 | AI Fairness 360, Fiddler |
| Human Oversight | L7 | LangGraph HITL, Temporal |
| Data Retention | L1 | Lifecycle policies |

---

## Technical Requirements

### Frontend
- Category-based navigation with filtering
- Collapsible framework sections
- Real-time compliance percentage
- Mobile responsive
- Export functionality

### Backend
- Compliance rules engine
- Profile-based framework filtering
- Scoring algorithm
- PDF/Excel generation

### Knowledge Base
- All 30 categories from kb_compliance_navigator.md
- 200+ frameworks with requirements
- Penalty data
- Layer mappings

---

## Design Notes

### Visual Elements
- Traffic light status (Green/Yellow/Red/Gray)
- Category cards with compliance percentage
- Radar chart for category overview
- Penalty exposure callouts

### Brand Colors
- Primary: Teal
- Compliant: Green (#22c55e)
- Partial: Yellow (#eab308)
- Non-Compliant: Red (#ef4444)
- N/A: Gray (#9ca3af)

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | January 2026 | Initial specification (Healthcare-only) |
| 2.0 | January 2026 | Expanded to 30 categories, 200+ frameworks |
| 3.0 | January 2026 | Added Technical Implementation Guide |

---

# PART 2: TECHNICAL IMPLEMENTATION GUIDE

> **For AI-Assisted Development (Claude Code, Cursor, Windsurf, etc.)**
>
> This section provides the technical specifications needed to build the Compliance Navigator. It includes data models, rules engine, scoring algorithms, and profile-based filtering.

---

## Technology Stack (Recommended)

```
Frontend:
- Framework: Next.js 14+ (App Router)
- State Management: Zustand
- Forms: React Hook Form + Zod
- Charts: Recharts (radar, bar charts)
- Tables: TanStack Table
- Styling: Tailwind CSS

Backend:
- Runtime: Node.js 18+
- Framework: Next.js API Routes
- Database: PostgreSQL with Prisma ORM
- PDF Generation: @react-pdf/renderer
- Excel Export: xlsx (SheetJS)

Infrastructure:
- Hosting: Vercel or Railway
- Database: Supabase or PlanetScale
```

---

## Data Models

### 1. Compliance Categories & Frameworks (Static)

```typescript
// types/compliance.ts

type CategoryId =
  | "data-privacy" | "health-data" | "financial-data" | "education-data"
  | "government-security" | "ai-specific" | "information-security"
  | "industry-specific" | "consumer-protection" | "international"
  | "employment-hr" | "audit-attestation" | "ethical-ai" | "intellectual-property"
  | "content-moderation" | "accessibility" | "environmental-esg" | "insurance"
  | "telecommunications" | "real-estate" | "childrens-privacy" | "biometric-data"
  | "marketing-advertising" | "records-retention" | "crisis-incident"
  | "third-party-risk" | "model-governance" | "supply-chain"
  | "emerging-regulations" | "industry-standards";

type GeographyId =
  | "usa-federal" | "usa-california" | "usa-other-states"
  | "eu-eea" | "uk" | "canada" | "apac" | "latam" | "mea";

type IndustryId =
  | "healthcare" | "financial" | "insurance" | "education"
  | "government-federal" | "government-state" | "defense"
  | "manufacturing" | "retail" | "technology" | "telecom"
  | "energy" | "legal" | "other";

type DataTypeId =
  | "pii" | "phi" | "pci" | "financial" | "employee"
  | "student" | "childrens" | "biometric" | "classified" | "ip";

interface Category {
  id: CategoryId;
  name: string;
  description: string;
  tier: 1 | 2 | 3 | 4;  // Priority tier
  frameworkCount: number;
  applicableIndustries: IndustryId[] | "all";
  applicableGeographies: GeographyId[] | "all";
  requiredDataTypes: DataTypeId[];
}

interface Framework {
  id: string;
  categoryId: CategoryId;
  name: string;
  fullName: string;
  description: string;

  // Applicability
  geography: GeographyId[];
  industries: IndustryId[] | "all";
  mandatory: boolean;
  dataTypes: DataTypeId[];

  // Requirements
  requirements: Requirement[];

  // Enforcement
  enforcementBody: string;
  penaltyMin?: number;
  penaltyMax?: number;
  penaltyDescription: string;

  // References
  url: string;
  bookChapter?: number;

  // Layer mapping
  layerMappings: LayerMapping[];
}

interface Requirement {
  id: string;
  description: string;
  details?: string;
  isCritical: boolean;
}

interface LayerMapping {
  layerId: LayerId;
  description: string;
  recommendedProducts: string[];
}

type LayerId = "L1" | "L2" | "L3" | "L4" | "L5" | "L6" | "L7";
```

### 2. User Profile & Assessment

```typescript
// types/assessment.ts

interface ComplianceProfile {
  // Geography
  geographies: GeographyId[];

  // Industry
  primaryIndustry: IndustryId;
  secondaryIndustries?: IndustryId[];

  // Data Types
  dataTypes: DataTypeId[];

  // Use Cases
  useCases: UseCaseId[];

  // Organization size
  orgSize?: OrgSize;
}

type UseCaseId =
  | "customer-service" | "internal-employee" | "healthcare-clinical"
  | "financial-advisory" | "hr-recruiting" | "legal-contract"
  | "content-generation" | "decision-support" | "autonomous-actions";

type OrgSize = "small" | "medium" | "large" | "enterprise";

interface ComplianceSession {
  id: string;
  createdAt: Date;
  updatedAt: Date;
  completedAt?: Date;

  // Lead info
  lead: {
    email: string;
    name: string;
    organization: string;
    role: string;
  };

  // Profile
  profile: ComplianceProfile;

  // Applicable frameworks (computed from profile)
  applicableFrameworks: ApplicableFramework[];

  // Responses
  responses: Record<string, FrameworkResponse>;

  // Results
  results?: ComplianceResults;
}

interface ApplicableFramework {
  frameworkId: string;
  relevance: "mandatory" | "recommended" | "optional";
  reason: string;  // Why it applies
}

interface FrameworkResponse {
  frameworkId: string;
  status: ComplianceStatus;
  requirementChecks: Record<string, boolean>;
  evidenceNotes?: string;
  owner?: string;
  dueDate?: Date;
  updatedAt: Date;
}

type ComplianceStatus = "compliant" | "partial" | "non-compliant" | "na";
```

### 3. Results & Scoring

```typescript
// types/results.ts

interface ComplianceResults {
  // Overall
  totalFrameworks: number;
  applicableFrameworks: number;

  // Status counts
  compliantCount: number;
  partialCount: number;
  nonCompliantCount: number;
  naCount: number;

  // Scores
  compliancePercentage: number;
  weightedScore: number;
  maxWeightedScore: number;

  // Risk
  riskLevel: RiskLevel;
  mandatoryGaps: string[];  // Framework IDs

  // Penalties
  penaltyExposure: PenaltyEstimate;

  // Category breakdown
  categoryScores: Record<CategoryId, CategoryScore>;

  // Remediation
  remediationPriorities: RemediationPriority[];
}

type RiskLevel = "low" | "medium" | "high" | "critical";

interface CategoryScore {
  categoryId: CategoryId;
  applicable: number;
  compliant: number;
  partial: number;
  nonCompliant: number;
  percentage: number;
  hasMandatoryGap: boolean;
}

interface PenaltyEstimate {
  minExposure: number;
  maxExposure: number;
  topRisks: {
    frameworkId: string;
    frameworkName: string;
    maxPenalty: number;
    description: string;
  }[];
}

interface RemediationPriority {
  frameworkId: string;
  frameworkName: string;
  priority: number;  // 1 = highest
  layers: LayerId[];
  products: string[];
  effort: "low" | "medium" | "high";
}
```

---

## Compliance Rules Engine

### 1. Framework Applicability

```typescript
// lib/engine/applicability.ts

import { FRAMEWORKS, CATEGORIES } from "@/data/complianceData";
import { ComplianceProfile, ApplicableFramework } from "@/types/assessment";

export function determineApplicableFrameworks(
  profile: ComplianceProfile
): ApplicableFramework[] {
  const applicable: ApplicableFramework[] = [];

  for (const framework of FRAMEWORKS) {
    const result = checkFrameworkApplicability(framework, profile);

    if (result.applies) {
      applicable.push({
        frameworkId: framework.id,
        relevance: result.relevance,
        reason: result.reason
      });
    }
  }

  // Sort by relevance (mandatory first)
  return applicable.sort((a, b) => {
    const order = { mandatory: 0, recommended: 1, optional: 2 };
    return order[a.relevance] - order[b.relevance];
  });
}

function checkFrameworkApplicability(
  framework: Framework,
  profile: ComplianceProfile
): { applies: boolean; relevance: Relevance; reason: string } {
  // Check geography
  const geoMatch = framework.geography.some(g =>
    profile.geographies.includes(g)
  );
  if (!geoMatch) {
    return { applies: false, relevance: "optional", reason: "" };
  }

  // Check industry
  const industryMatch =
    framework.industries === "all" ||
    framework.industries.includes(profile.primaryIndustry) ||
    framework.industries.some(i => profile.secondaryIndustries?.includes(i));

  if (!industryMatch && framework.mandatory) {
    return { applies: false, relevance: "optional", reason: "" };
  }

  // Check data types
  const dataTypeMatch = framework.dataTypes.some(dt =>
    profile.dataTypes.includes(dt)
  );

  // Determine relevance
  let relevance: Relevance = "optional";
  let reason = "";

  if (framework.mandatory && industryMatch && dataTypeMatch) {
    relevance = "mandatory";
    reason = `Required for ${profile.primaryIndustry} handling ${framework.dataTypes.join(", ")}`;
  } else if (industryMatch || dataTypeMatch) {
    relevance = "recommended";
    reason = `Recommended based on your industry/data profile`;
  } else if (geoMatch) {
    relevance = "optional";
    reason = `Optional but applicable in your geography`;
  }

  return {
    applies: relevance !== "optional" || geoMatch,
    relevance,
    reason
  };
}

type Relevance = "mandatory" | "recommended" | "optional";
```

### 2. Scoring Algorithm

```typescript
// lib/engine/scoring.ts

import { ComplianceSession, ComplianceResults, CategoryScore } from "@/types/results";
import { FRAMEWORKS, CATEGORIES } from "@/data/complianceData";

const STATUS_POINTS = {
  compliant: 2,
  partial: 1,
  "non-compliant": 0,
  na: 0
};

const RELEVANCE_WEIGHTS = {
  mandatory: 2.0,
  recommended: 1.0,
  optional: 0.5
};

const HIGH_PENALTY_THRESHOLD = 1000000;  // $1M
const HIGH_PENALTY_WEIGHT = 1.5;

export function calculateComplianceResults(
  session: ComplianceSession
): ComplianceResults {
  const { applicableFrameworks, responses } = session;

  // Count by status
  let compliantCount = 0;
  let partialCount = 0;
  let nonCompliantCount = 0;
  let naCount = 0;
  let weightedScore = 0;
  let maxWeightedScore = 0;

  const mandatoryGaps: string[] = [];
  const categoryScores: Record<CategoryId, CategoryScore> = {} as any;

  // Initialize category scores
  for (const category of CATEGORIES) {
    categoryScores[category.id] = {
      categoryId: category.id,
      applicable: 0,
      compliant: 0,
      partial: 0,
      nonCompliant: 0,
      percentage: 0,
      hasMandatoryGap: false
    };
  }

  // Process each applicable framework
  for (const af of applicableFrameworks) {
    const response = responses[af.frameworkId];
    const framework = FRAMEWORKS.find(f => f.id === af.frameworkId)!;
    const status = response?.status || "non-compliant";

    // Count by status
    switch (status) {
      case "compliant": compliantCount++; break;
      case "partial": partialCount++; break;
      case "non-compliant": nonCompliantCount++; break;
      case "na": naCount++; break;
    }

    // Skip N/A for scoring
    if (status === "na") continue;

    // Calculate weight
    let weight = RELEVANCE_WEIGHTS[af.relevance];
    if (framework.penaltyMax && framework.penaltyMax >= HIGH_PENALTY_THRESHOLD) {
      weight *= HIGH_PENALTY_WEIGHT;
    }

    // Add to weighted score
    weightedScore += STATUS_POINTS[status] * weight;
    maxWeightedScore += 2 * weight;

    // Track mandatory gaps
    if (af.relevance === "mandatory" && status === "non-compliant") {
      mandatoryGaps.push(af.frameworkId);
    }

    // Update category scores
    const catScore = categoryScores[framework.categoryId];
    catScore.applicable++;
    if (status === "compliant") catScore.compliant++;
    if (status === "partial") catScore.partial++;
    if (status === "non-compliant") catScore.nonCompliant++;
    if (af.relevance === "mandatory" && status === "non-compliant") {
      catScore.hasMandatoryGap = true;
    }
  }

  // Calculate percentages
  const compliancePercentage = maxWeightedScore > 0
    ? Math.round((weightedScore / maxWeightedScore) * 100)
    : 0;

  // Calculate category percentages
  for (const cat of Object.values(categoryScores)) {
    if (cat.applicable > 0) {
      const catScore = cat.compliant * 2 + cat.partial;
      const catMax = cat.applicable * 2;
      cat.percentage = Math.round((catScore / catMax) * 100);
    }
  }

  // Determine risk level
  const riskLevel = calculateRiskLevel(compliancePercentage, mandatoryGaps.length);

  // Calculate penalty exposure
  const penaltyExposure = calculatePenaltyExposure(mandatoryGaps, responses);

  // Generate remediation priorities
  const remediationPriorities = generateRemediationPriorities(
    mandatoryGaps,
    responses,
    applicableFrameworks
  );

  return {
    totalFrameworks: FRAMEWORKS.length,
    applicableFrameworks: applicableFrameworks.length,
    compliantCount,
    partialCount,
    nonCompliantCount,
    naCount,
    compliancePercentage,
    weightedScore,
    maxWeightedScore,
    riskLevel,
    mandatoryGaps,
    penaltyExposure,
    categoryScores,
    remediationPriorities
  };
}

function calculateRiskLevel(
  percentage: number,
  mandatoryGaps: number
): RiskLevel {
  if (mandatoryGaps > 0) {
    return percentage < 75 ? "critical" : "high";
  }
  if (percentage >= 90) return "low";
  if (percentage >= 75) return "medium";
  return "high";
}

function calculatePenaltyExposure(
  mandatoryGaps: string[],
  responses: Record<string, FrameworkResponse>
): PenaltyEstimate {
  let minExposure = 0;
  let maxExposure = 0;
  const topRisks: PenaltyEstimate["topRisks"] = [];

  for (const frameworkId of mandatoryGaps) {
    const framework = FRAMEWORKS.find(f => f.id === frameworkId);
    if (!framework) continue;

    if (framework.penaltyMin) minExposure += framework.penaltyMin;
    if (framework.penaltyMax) {
      maxExposure += framework.penaltyMax;
      topRisks.push({
        frameworkId: framework.id,
        frameworkName: framework.name,
        maxPenalty: framework.penaltyMax,
        description: framework.penaltyDescription
      });
    }
  }

  // Sort by penalty amount
  topRisks.sort((a, b) => b.maxPenalty - a.maxPenalty);

  return {
    minExposure,
    maxExposure,
    topRisks: topRisks.slice(0, 5)  // Top 5
  };
}

function generateRemediationPriorities(
  gaps: string[],
  responses: Record<string, FrameworkResponse>,
  applicableFrameworks: ApplicableFramework[]
): RemediationPriority[] {
  const priorities: RemediationPriority[] = [];

  for (const frameworkId of gaps) {
    const framework = FRAMEWORKS.find(f => f.id === frameworkId);
    const af = applicableFrameworks.find(a => a.frameworkId === frameworkId);
    if (!framework || !af) continue;

    const layers = framework.layerMappings.map(lm => lm.layerId);
    const products = framework.layerMappings.flatMap(lm => lm.recommendedProducts);

    priorities.push({
      frameworkId: framework.id,
      frameworkName: framework.name,
      priority: af.relevance === "mandatory" ? 1 : 2,
      layers: [...new Set(layers)],
      products: [...new Set(products)].slice(0, 5),
      effort: estimateEffort(framework)
    });
  }

  return priorities.sort((a, b) => a.priority - b.priority);
}

function estimateEffort(framework: Framework): "low" | "medium" | "high" {
  const reqCount = framework.requirements.length;
  const criticalCount = framework.requirements.filter(r => r.isCritical).length;

  if (criticalCount > 5 || reqCount > 10) return "high";
  if (criticalCount > 2 || reqCount > 5) return "medium";
  return "low";
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
  role VARCHAR(100) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Compliance sessions
CREATE TABLE compliance_sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  lead_id UUID REFERENCES leads(id),

  -- Profile (JSON)
  profile JSONB NOT NULL,

  -- Applicable frameworks (computed)
  applicable_frameworks JSONB,

  -- Results (cached)
  results JSONB,

  completed_at TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Framework responses
CREATE TABLE framework_responses (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id UUID REFERENCES compliance_sessions(id) ON DELETE CASCADE,
  framework_id VARCHAR(50) NOT NULL,

  status VARCHAR(20) NOT NULL,
  requirement_checks JSONB DEFAULT '{}',
  evidence_notes TEXT,
  owner VARCHAR(255),
  due_date DATE,

  updated_at TIMESTAMP DEFAULT NOW(),

  UNIQUE(session_id, framework_id)
);

-- Indexes
CREATE INDEX idx_sessions_lead ON compliance_sessions(lead_id);
CREATE INDEX idx_responses_session ON framework_responses(session_id);
CREATE INDEX idx_responses_status ON framework_responses(session_id, status);
```

---

## API Endpoints

```typescript
// Next.js App Router API Routes

// POST /api/compliance - Start new session
interface CreateSessionRequest {
  lead: {
    email: string;
    name: string;
    organization: string;
    role: string;
  };
  profile: ComplianceProfile;
}

interface CreateSessionResponse {
  sessionId: string;
  applicableFrameworks: ApplicableFramework[];
  categoryBreakdown: {
    categoryId: string;
    name: string;
    frameworkCount: number;
    relevance: "mandatory" | "recommended" | "optional";
  }[];
}

// GET /api/compliance/:id - Get session
interface GetSessionResponse {
  session: ComplianceSession;
  categories: CategoryWithFrameworks[];
  progress: ProgressState;
}

// POST /api/compliance/:id/responses - Save response
interface SaveResponseRequest {
  frameworkId: string;
  status: ComplianceStatus;
  requirementChecks?: Record<string, boolean>;
  evidenceNotes?: string;
  owner?: string;
  dueDate?: string;
}

// POST /api/compliance/:id/responses/bulk - Bulk save
interface BulkSaveRequest {
  responses: SaveResponseRequest[];
}

// GET /api/compliance/:id/results - Get computed results
interface GetResultsResponse {
  results: ComplianceResults;
  recommendations: string[];
}

// GET /api/compliance/:id/export/pdf - Export PDF
// GET /api/compliance/:id/export/xlsx - Export Excel

// GET /api/compliance/frameworks - Get all frameworks
// GET /api/compliance/categories - Get all categories
```

---

## React Components

### 1. Component Structure

```
components/
├── compliance/
│   ├── ComplianceLayout.tsx       # Main layout
│   ├── ProfileSetup.tsx           # Steps 3a-3d
│   ├── CategoryNav.tsx            # Left sidebar (30 categories)
│   ├── FrameworkList.tsx          # Framework checklist
│   ├── FrameworkCard.tsx          # Single framework
│   ├── RequirementChecklist.tsx   # Sub-requirements
│   ├── LayerMapping.tsx           # 7-layer remediation
│   ├── ResultsDashboard.tsx       # Final results
│   ├── RiskCard.tsx               # Risk level display
│   ├── PenaltyExposure.tsx        # Penalty estimates
│   └── RemediationPanel.tsx       # Priority fixes
├── charts/
│   ├── CategoryRadar.tsx          # 30-category radar
│   ├── ComplianceBars.tsx         # Category bars
│   ├── RiskGauge.tsx              # Risk level gauge
│   └── PenaltyChart.tsx           # Exposure chart
├── forms/
│   ├── ProfileForm.tsx            # Multi-step profile
│   ├── StatusSelector.tsx         # Compliance status
│   └── FilterPanel.tsx            # Category/geography filters
└── ui/
    ├── RelevanceBadge.tsx         # Mandatory/Recommended/Optional
    ├── PenaltyBadge.tsx           # Penalty display
    └── LayerBadge.tsx             # L1-L7 badges
```

### 2. Framework Card Component

```tsx
// components/compliance/FrameworkCard.tsx

import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { Framework, FrameworkResponse, ApplicableFramework } from "@/types/compliance";
import { StatusSelector } from "./StatusSelector";
import { RequirementChecklist } from "./RequirementChecklist";
import { LayerMapping } from "./LayerMapping";
import { RelevanceBadge } from "@/components/ui/RelevanceBadge";
import { PenaltyBadge } from "@/components/ui/PenaltyBadge";

interface Props {
  framework: Framework;
  applicability: ApplicableFramework;
  response?: FrameworkResponse;
  onUpdate: (response: Partial<FrameworkResponse>) => void;
}

export function FrameworkCard({
  framework,
  applicability,
  response,
  onUpdate
}: Props) {
  const [expanded, setExpanded] = useState(false);
  const status = response?.status;

  return (
    <div
      className={`
        rounded-xl border-2 overflow-hidden transition-all
        ${applicability.relevance === "mandatory" ? "border-l-4 border-l-red-500" : ""}
        ${status === "compliant" ? "border-green-200 bg-green-50" : ""}
        ${status === "partial" ? "border-yellow-200 bg-yellow-50" : ""}
        ${status === "non-compliant" ? "border-red-200 bg-red-50" : ""}
        ${status === "na" ? "border-gray-200 bg-gray-50 opacity-60" : ""}
        ${!status ? "border-gray-200 bg-white" : ""}
      `}
    >
      {/* Header */}
      <div className="p-4">
        <div className="flex items-start justify-between gap-4">
          <div className="flex-1">
            <div className="flex items-center gap-2 mb-1 flex-wrap">
              <RelevanceBadge relevance={applicability.relevance} />
              {framework.penaltyMax && (
                <PenaltyBadge amount={framework.penaltyMax} />
              )}
              <span className="text-xs text-gray-500">
                {framework.geography.join(", ")}
              </span>
            </div>
            <h3 className="font-semibold text-gray-900">{framework.name}</h3>
            <p className="text-sm text-gray-600 mt-1">{framework.description}</p>
          </div>

          <StatusSelector
            value={status}
            onChange={(newStatus) => onUpdate({ status: newStatus })}
          />
        </div>

        {/* Applicability reason */}
        <p className="text-xs text-teal-600 mt-2">{applicability.reason}</p>

        {/* Expand button */}
        <button
          onClick={() => setExpanded(!expanded)}
          className="mt-3 text-sm text-teal-600 hover:text-teal-700 flex items-center gap-1"
        >
          {expanded ? "Hide details" : "Show requirements"}
          <svg
            className={`w-4 h-4 transition-transform ${expanded ? "rotate-180" : ""}`}
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              strokeLinecap="round"
              strokeLinejoin="round"
              strokeWidth={2}
              d="M19 9l-7 7-7-7"
            />
          </svg>
        </button>
      </div>

      {/* Expanded content */}
      <AnimatePresence>
        {expanded && (
          <motion.div
            initial={{ height: 0, opacity: 0 }}
            animate={{ height: "auto", opacity: 1 }}
            exit={{ height: 0, opacity: 0 }}
            className="border-t border-gray-200"
          >
            <div className="p-4 space-y-4">
              {/* Requirements */}
              <div>
                <h4 className="text-sm font-medium text-gray-700 mb-2">
                  Requirements ({framework.requirements.length}):
                </h4>
                <RequirementChecklist
                  requirements={framework.requirements}
                  checks={response?.requirementChecks || {}}
                  onChange={(checks) => onUpdate({ requirementChecks: checks })}
                />
              </div>

              {/* Layer mapping */}
              <div>
                <h4 className="text-sm font-medium text-gray-700 mb-2">
                  7-Layer Remediation:
                </h4>
                <LayerMapping mappings={framework.layerMappings} />
              </div>

              {/* Penalty info */}
              {framework.penaltyMax && (
                <div className="bg-red-50 border border-red-100 rounded-lg p-3">
                  <h4 className="text-sm font-medium text-red-800 mb-1">
                    Penalty Exposure:
                  </h4>
                  <p className="text-sm text-red-700">
                    {framework.penaltyDescription}
                  </p>
                </div>
              )}

              {/* Evidence notes */}
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">
                  Evidence Notes
                </label>
                <textarea
                  value={response?.evidenceNotes || ""}
                  onChange={(e) => onUpdate({ evidenceNotes: e.target.value })}
                  className="w-full px-3 py-2 border rounded-lg text-sm"
                  rows={3}
                  placeholder="Document compliance evidence..."
                />
              </div>

              {/* Owner and due date */}
              <div className="grid grid-cols-2 gap-4">
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-1">
                    Owner
                  </label>
                  <input
                    type="text"
                    value={response?.owner || ""}
                    onChange={(e) => onUpdate({ owner: e.target.value })}
                    className="w-full px-3 py-2 border rounded-lg text-sm"
                    placeholder="Assign owner..."
                  />
                </div>
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-1">
                    Due Date
                  </label>
                  <input
                    type="date"
                    value={response?.dueDate?.toISOString().split("T")[0] || ""}
                    onChange={(e) => onUpdate({ dueDate: new Date(e.target.value) })}
                    className="w-full px-3 py-2 border rounded-lg text-sm"
                  />
                </div>
              </div>

              {/* External link */}
              <a
                href={framework.url}
                target="_blank"
                rel="noopener noreferrer"
                className="text-sm text-teal-600 hover:text-teal-700 flex items-center gap-1"
              >
                View official documentation →
              </a>
            </div>
          </motion.div>
        )}
      </AnimatePresence>
    </div>
  );
}
```

### 3. Results Dashboard

```tsx
// components/compliance/ResultsDashboard.tsx

import { motion } from "framer-motion";
import { ComplianceResults } from "@/types/results";
import { RiskCard } from "./RiskCard";
import { PenaltyExposure } from "./PenaltyExposure";
import { RemediationPanel } from "./RemediationPanel";
import { CategoryRadar } from "@/components/charts/CategoryRadar";
import { ComplianceBars } from "@/components/charts/ComplianceBars";

interface Props {
  results: ComplianceResults;
  onExportPDF: () => void;
  onExportExcel: () => void;
}

export function ResultsDashboard({ results, onExportPDF, onExportExcel }: Props) {
  return (
    <div className="space-y-8">
      {/* Header */}
      <div className="text-center">
        <h1 className="text-3xl font-bold text-gray-900 mb-2">
          Compliance Assessment Results
        </h1>
        <p className="text-gray-600">
          Assessment across {results.applicableFrameworks} frameworks in {
            Object.values(results.categoryScores).filter(c => c.applicable > 0).length
          } categories
        </p>
      </div>

      {/* Risk & Score summary */}
      <div className="grid md:grid-cols-2 gap-6">
        <RiskCard
          riskLevel={results.riskLevel}
          percentage={results.compliancePercentage}
          mandatoryGaps={results.mandatoryGaps.length}
        />

        <motion.div
          className="bg-white rounded-xl shadow-lg p-6"
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
        >
          <h2 className="text-lg font-semibold text-gray-900 mb-4">
            Compliance Status
          </h2>
          <div className="grid grid-cols-4 gap-4 text-center">
            <div>
              <div className="text-3xl font-bold text-green-600">
                {results.compliantCount}
              </div>
              <div className="text-xs text-gray-500">Compliant</div>
            </div>
            <div>
              <div className="text-3xl font-bold text-yellow-600">
                {results.partialCount}
              </div>
              <div className="text-xs text-gray-500">Partial</div>
            </div>
            <div>
              <div className="text-3xl font-bold text-red-600">
                {results.nonCompliantCount}
              </div>
              <div className="text-xs text-gray-500">Non-Compliant</div>
            </div>
            <div>
              <div className="text-3xl font-bold text-gray-400">
                {results.naCount}
              </div>
              <div className="text-xs text-gray-500">N/A</div>
            </div>
          </div>
        </motion.div>
      </div>

      {/* Penalty exposure */}
      {results.mandatoryGaps.length > 0 && (
        <PenaltyExposure exposure={results.penaltyExposure} />
      )}

      {/* Category breakdown */}
      <div className="grid md:grid-cols-2 gap-6">
        <motion.div
          className="bg-white rounded-xl shadow-lg p-6"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
        >
          <h2 className="text-lg font-semibold text-gray-900 mb-4">
            Category Overview
          </h2>
          <CategoryRadar categoryScores={results.categoryScores} />
        </motion.div>

        <motion.div
          className="bg-white rounded-xl shadow-lg p-6"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
        >
          <h2 className="text-lg font-semibold text-gray-900 mb-4">
            Category Breakdown
          </h2>
          <ComplianceBars categoryScores={results.categoryScores} />
        </motion.div>
      </div>

      {/* Remediation priorities */}
      <RemediationPanel priorities={results.remediationPriorities} />

      {/* Export actions */}
      <div className="flex justify-center gap-4">
        <button
          onClick={onExportPDF}
          className="flex items-center gap-2 px-6 py-3 bg-teal-600 text-white rounded-lg font-medium hover:bg-teal-700"
        >
          📄 Export Compliance Report
        </button>
        <button
          onClick={onExportExcel}
          className="flex items-center gap-2 px-6 py-3 bg-white border border-gray-300 text-gray-700 rounded-lg font-medium hover:bg-gray-50"
        >
          📊 Export Checklist
        </button>
      </div>

      {/* Cross-links */}
      <div className="text-center pt-6 border-t">
        <p className="text-gray-600 mb-4">Next steps for remediation:</p>
        <div className="flex justify-center gap-4">
          <a
            href="/stack"
            className="text-teal-600 hover:text-teal-700 font-medium"
          >
            🔧 Build Compliant Stack →
          </a>
          <a
            href="/vendors"
            className="text-teal-600 hover:text-teal-700 font-medium"
          >
            💬 Get Vendor Recommendations →
          </a>
        </div>
      </div>
    </div>
  );
}
```

---

## Compliance Data File Structure

```typescript
// data/complianceData.ts

export const CATEGORIES: Category[] = [
  {
    id: "data-privacy",
    name: "Data Privacy",
    description: "How personal data is collected, used, stored, and shared",
    tier: 1,
    frameworkCount: 14,
    applicableIndustries: "all",
    applicableGeographies: "all",
    requiredDataTypes: ["pii"]
  },
  {
    id: "health-data",
    name: "Health Data",
    description: "Protected health information and medical data",
    tier: 1,
    frameworkCount: 10,
    applicableIndustries: ["healthcare", "insurance"],
    applicableGeographies: "all",
    requiredDataTypes: ["phi"]
  },
  // ... 28 more categories
];

export const FRAMEWORKS: Framework[] = [
  {
    id: "gdpr",
    categoryId: "data-privacy",
    name: "GDPR",
    fullName: "General Data Protection Regulation",
    description: "EU regulation on data protection and privacy",
    geography: ["eu-eea"],
    industries: "all",
    mandatory: true,
    dataTypes: ["pii"],
    requirements: [
      { id: "gdpr-consent", description: "Valid consent for processing", isCritical: true },
      { id: "gdpr-dsr", description: "Data subject rights implementation", isCritical: true },
      { id: "gdpr-dpo", description: "Data Protection Officer (if required)", isCritical: false },
      { id: "gdpr-breach", description: "72-hour breach notification", isCritical: true },
      { id: "gdpr-pbd", description: "Privacy by design and default", isCritical: false },
      { id: "gdpr-dpia", description: "Data Protection Impact Assessment", isCritical: false }
    ],
    enforcementBody: "EU Data Protection Authorities",
    penaltyMin: 10000000,
    penaltyMax: 20000000,
    penaltyDescription: "Up to €20M or 4% of global annual revenue",
    url: "https://gdpr.eu",
    bookChapter: 7,
    layerMappings: [
      { layerId: "L5", description: "Access control, consent management", recommendedProducts: ["Azure AD", "OneTrust"] },
      { layerId: "L6", description: "Audit logging for DSR compliance", recommendedProducts: ["Datadog", "Splunk"] },
      { layerId: "L7", description: "Consent capture workflows", recommendedProducts: ["OneTrust", "TrustArc"] }
    ]
  },
  {
    id: "hipaa-security",
    categoryId: "health-data",
    name: "HIPAA Security Rule",
    fullName: "HIPAA Security Rule (§164.312)",
    description: "Technical safeguards for protecting ePHI",
    geography: ["usa-federal"],
    industries: ["healthcare"],
    mandatory: true,
    dataTypes: ["phi"],
    requirements: [
      { id: "hipaa-access", description: "Access control (unique IDs, MFA, ABAC)", isCritical: true },
      { id: "hipaa-audit", description: "Audit logging (100% PHI access, 6-year retention)", isCritical: true },
      { id: "hipaa-encrypt-rest", description: "Encryption at rest (AES-256)", isCritical: true },
      { id: "hipaa-encrypt-transit", description: "Encryption in transit (TLS 1.2+)", isCritical: true },
      { id: "hipaa-emergency", description: "Emergency access procedures", isCritical: false }
    ],
    enforcementBody: "HHS Office for Civil Rights",
    penaltyMin: 100,
    penaltyMax: 1500000,
    penaltyDescription: "$100-$1.5M per violation type/year",
    url: "https://www.hhs.gov/hipaa",
    bookChapter: 7,
    layerMappings: [
      { layerId: "L1", description: "Encryption at rest", recommendedProducts: ["Snowflake", "Azure SQL TDE"] },
      { layerId: "L5", description: "Access control (ABAC)", recommendedProducts: ["Azure AD", "OPA", "Cerbos"] },
      { layerId: "L6", description: "Audit logging", recommendedProducts: ["Datadog", "Splunk", "Azure Monitor"] }
    ]
  },
  // ... 198+ more frameworks
];
```

---

## File Structure Summary

```
compliance-checker/
├── app/
│   ├── page.tsx                     # Landing page
│   ├── compliance/
│   │   ├── page.tsx                 # Lead capture + profile
│   │   └── [sessionId]/
│   │       ├── page.tsx             # Assessment interface
│   │       └── results/page.tsx     # Results dashboard
│   ├── api/
│   │   └── compliance/
│   │       ├── route.ts             # Create session
│   │       ├── frameworks/route.ts  # Get frameworks
│   │       ├── categories/route.ts  # Get categories
│   │       └── [id]/
│   │           ├── route.ts         # Get session
│   │           ├── responses/route.ts
│   │           ├── results/route.ts
│   │           └── export/
│   │               ├── pdf/route.ts
│   │               └── xlsx/route.ts
├── components/
│   ├── compliance/                  # Main components
│   ├── charts/                      # Visualizations
│   ├── forms/                       # Input forms
│   └── ui/                          # Shared UI
├── lib/
│   ├── engine/
│   │   ├── applicability.ts         # Framework filtering
│   │   └── scoring.ts               # Compliance scoring
│   └── db/
│       └── prisma.ts
├── data/
│   └── complianceData.ts            # 30 categories, 200+ frameworks
├── types/
│   ├── compliance.ts
│   ├── assessment.ts
│   └── results.ts
└── prisma/
    └── schema.prisma
```

---

## Quick Start for AI Coding Tools

```markdown
## Instructions for Claude Code / Cursor / Windsurf

1. **Create Next.js app:**
   ```bash
   npx create-next-app@latest compliance-checker --typescript --tailwind --app
   cd compliance-checker
   npm install zustand framer-motion recharts react-hook-form zod
   npm install xlsx @react-pdf/renderer @tanstack/react-table
   npm install @prisma/client
   npm install -D prisma
   ```

2. **Set up database:**
   - Copy schema to `prisma/schema.prisma`
   - Run `npx prisma migrate dev`

3. **Create compliance data:**
   - Copy all 30 categories from kb_compliance_navigator.md
   - Create FRAMEWORKS array with 200+ frameworks
   - Include requirements, penalties, layer mappings

4. **Implement rules engine:**
   - Copy applicability logic for profile-based filtering
   - Implement weighted scoring algorithm
   - Add penalty exposure calculation

5. **Build UI components:**
   - ProfileSetup with multi-step form
   - CategoryNav with relevance filtering
   - FrameworkCard with requirements and layer mapping
   - ResultsDashboard with risk and remediation

6. **Add visualizations:**
   - CategoryRadar for 30-category overview
   - ComplianceBars for category comparison
   - RiskGauge for overall risk level

7. **Implement export:**
   - PDF compliance report with gap analysis
   - Excel checklist for offline work

8. **Test the flow:**
   - Lead capture → Profile setup → Assess frameworks → View results → Export
```

---

**© 2026 Colaberry Inc. All rights reserved.**
**INPACT™ and GOALS™ are trademarks of Colaberry Inc.**
**From "Trust Before Intelligence" by Ram Katamaraja**
