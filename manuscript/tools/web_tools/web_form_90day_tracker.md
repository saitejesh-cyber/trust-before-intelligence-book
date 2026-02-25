# 90-Day Implementation Tracker - Web Tool Specification

## Overview

**URL:** trustbeforeintelligence.ai/tracker
**Purpose:** Complete implementation tracking from Day Zero readiness through 90-day transformation
**Lead Capture:** Email required to access tracker
**Data Storage:** Cloud-based with shareable team access

**Key Insight:** 67% of agent deployments fail in Week 1, not because of bad AI, but because of missing Day Zero preparation. This tool gates Week 1 access until Day Zero readiness is confirmed.

---

## User Flow

### Step 1: Landing Page
- Value proposition: "Track your AI agent transformation from Day Zero to Week 12"
- Key features:
  - "Day Zero readiness checklist (15-35 items based on organization size)"
  - "Week-by-week progress tracking (Weeks 1-12)"
  - "INPACT and GOALS score visualization"
  - "7-Layer build status monitoring"
  - "Team collaboration with shareable dashboards"
- Echo benchmark teaser: "Echo completed Day Zero in 2 weeks, then went from 28% to 89% in 90 days."
- **CTA Button:** "Start Your Journey"

### Step 2: Lead Capture & Project Setup
Required fields:
- Email (required)
- Name (required)
- Organization (required)
- Project name (required)

Optional fields:
- Role (dropdown)
- Industry (dropdown)
- Target completion date
- Team size
- Budget tier (dropdown: Starter, Growth, Enterprise)

### Step 3: Day Zero Readiness (GATE)

**This step must be completed before accessing Weeks 1-12.**

**Step 3a: Organization Tier Selection**

User selects organization tier based on size:

| Tier | Organization Size | Items | Timeline Adjustment |
|------|------------------|-------|---------------------|
| **Essential** | Small (<1,000 employees) | 15 | -2 weeks from baseline |
| **Standard** | Mid-size (1,000-15,000) | 25 | Baseline (12 weeks) |
| **Comprehensive** | Large/Enterprise (15,000+) | 35 | +2 to +4 weeks |

**Step 3b: Day Zero Checklist**

User completes the Day Zero checklist for their selected tier across 6 domains:
1. Assessment & Planning (4 Essential + 2 Standard)
2. Stakeholder Alignment (4 Essential + 3 Standard + 3 Comprehensive)
3. Team & Resources (3 Essential + 1 Comprehensive)
4. Technical Prerequisites (3 Essential + 3 Standard + 3 Comprehensive)
5. Data Readiness (1 Essential)
6. Compliance & Risk (2 Standard + 3 Comprehensive)

**Tier Cumulation:** Each tier includes all items from lower tiers.

**Gate Logic:**
- If readiness ≥ 90% with no critical blockers → Unlock Week 1
- If readiness < 90% or critical blockers exist → Show remediation guidance, keep Week 1 locked

### Step 4: Baseline Setup (After Day Zero Complete)

**Step 4a: Initial INPACT Assessment**
Either:
- Import from INPACT Assessment tool (if completed)
- Quick self-assessment (6 sliders, 1-6 each)

**Step 4b: Initial GOALS Assessment**
- Quick self-assessment (5 sliders, 1-5 each)

**Step 4c: Current Architecture Status**
For each of 7 layers:
- Current tools (optional text)
- Planned tools (optional text)

### Step 5: Dashboard (Main Interface)

**Layout:** Multi-tab dashboard with 8 tabs

---

## Dashboard Tabs

### Tab 0: Day Zero Readiness ⭐ UPDATED

**Purpose:** Tiered pre-transformation checklist (15/25/35 items) ensuring organizational readiness aligned with Chapter 10

**Layout:** Tier selector + domain-based navigation with progress tracking

**Tier Selector (First-time setup):**
- Three cards showing Essential / Standard / Comprehensive
- Organization size guidance for each
- Once selected, can be changed in settings

**Navigation:**
- Left sidebar: 6 domains with progress indicators (items shown based on selected tier)
- Main panel: Checklist items for selected domain
- Right panel: Overall readiness score + verdict

**The 6 Domains (Tiered Items):**

#### Domain 1: Assessment & Planning
| ID | Item | Tier | Critical? |
|----|------|------|-----------|
| E-01 | INPACT Assessment Complete | Essential | ✅ |
| E-02 | Priority Layers Identified | Essential | ✅ |
| E-03 | Phase Strategy Decided | Essential | ✅ |
| E-04 | Week 2 Plan Drafted | Essential | 📋 |
| S-01 | Scaling Adjustments Planned | Standard | 📋 |
| S-02 | Special Considerations Identified | Standard | 📋 |

#### Domain 2: Stakeholder Alignment
| ID | Item | Tier | Critical? |
|----|------|------|-----------|
| E-05 | Executive Sponsor Identified | Essential | ✅ |
| E-06 | Steering Committee Formed | Essential | ✅ |
| E-07 | Budget Approved | Essential | ✅ |
| E-08 | Success Criteria Agreed | Essential | ✅ |
| S-03 | Communication Cadence Established | Standard | 📋 |
| S-04 | Stakeholder Groups Identified | Standard | 📋 |
| S-05 | UAT Users Identified | Standard | 📋 |
| C-01 | Board Awareness | Comprehensive | 📋 |
| C-02 | Legal Review Complete | Comprehensive | 📋 |
| C-03 | Change Management Plan | Comprehensive | 📋 |

#### Domain 3: Team & Resources
| ID | Item | Tier | Critical? |
|----|------|------|-----------|
| E-09 | Core Team Identified | Essential | ✅ |
| E-10 | Resources Allocated | Essential | 📋 |
| E-11 | Technology Track Selected | Essential | ✅ |
| C-04 | Consulting Support Contracted | Comprehensive | 📋 |

#### Domain 4: Technical Prerequisites
| ID | Item | Tier | Critical? |
|----|------|------|-----------|
| E-12 | Current-State Documented | Essential | ✅ |
| E-13 | Cloud Environment Access | Essential | 📋 |
| E-14 | Source System Access | Essential | 📋 |
| S-06 | CDC Complexity Assessed | Standard | 📋 |
| S-07 | LLM Provider Access | Standard | 📋 |
| S-08 | Vector Database Selected | Standard | 📋 |
| C-05 | Multi-Cloud Planned | Comprehensive | 📋 |
| C-06 | Authentication Integration Documented | Comprehensive | 📋 |
| C-07 | Monitoring Infrastructure Available | Comprehensive | 📋 |

#### Domain 5: Data Readiness
| ID | Item | Tier | Critical? |
|----|------|------|-----------|
| E-15 | Data Inventory Complete | Essential | 📋 |

#### Domain 6: Compliance & Risk
| ID | Item | Tier | Critical? |
|----|------|------|-----------|
| S-09 | Regulatory Requirements Known | Standard | 📋 |
| S-10 | Phase Gate Criteria Accepted | Standard | ✅ |
| C-08 | Regulated Industry Adjustment | Comprehensive | 📋 |
| C-09 | Data Classification Complete | Comprehensive | 📋 |
| C-10 | HITL Authority Defined | Comprehensive | 📋 |

**Per Checklist Item:**
- Item ID (e.g., E-01, S-03, C-07)
- Title (e.g., "INPACT Assessment Complete")
- Tier badge (Essential / Standard / Comprehensive)
- Critical indicator (✅ Critical or 📋 Standard)
- Requirement description
- Chapter 10 Reference citation
- Evidence checklist (sub-items)
- Status selector: ✅ Ready | 🟡 In Progress | ❌ Not Ready | N/A
- Evidence notes (text field)
- Data collected fields (specific to each item)
- Owner assignment (optional)
- Target date (optional)

**Scoring & Readiness Logic:**

| Status | Points |
|--------|--------|
| ✅ Ready | 2 |
| 🟡 In Progress | 1 |
| ❌ Not Ready | 0 |
| N/A | Excluded |

**Readiness Thresholds:**
| Percentage | Verdict | Action |
|------------|---------|--------|
| 90-100% | ✅ Ready to Start | Unlock Week 1 |
| 75-89% | 🟡 Almost Ready | Complete In Progress items |
| 50-74% | ⚠️ Significant Gaps | Address blockers first |
| <50% | ❌ Not Ready | Major preparation needed |

**Critical Item Rule:** If ANY critical item is ❌ Not Ready, Week 1 remains locked regardless of overall score.

**Readiness Verdict Display:**
- Large badge showing current verdict
- List of critical blockers (if any)
- Domain-by-domain progress bars
- "Proceed to Week 1" button (enabled only when ready)

---

### Tab 1: Weekly Progress Dashboard

**Layout:** Timeline view with cards for each week

**Per Week Card:**
- Week number (1-12)
- Phase indicator (Foundation / Intelligence / Trust / Operations)
- Primary layer focus (L1-L7)
- INPACT snapshot (score + mini radar)
- GOALS snapshot (score + mini bar)
- Top risk (text + severity color)
- Key deliverable (text + status)
- Status badge (On Track / At Risk / Blocked / Complete)

**Interactive Features:**
- Click week to expand details
- Add/edit notes per week
- Mark week complete
- Add deliverables
- Log risks

**Visual:**
- Progress bar across all 12 weeks
- Current week highlighted
- Echo benchmark overlay (optional toggle)

---

### Tab 2: INPACT Progress Tracker

**Layout:** Radar chart + dimension cards

**Radar Chart:**
- 6 axes (I, N, P, A, C, T)
- Current score in teal
- Baseline in gray (dashed)
- Target in green (if set)
- Echo Week 0 comparison (toggle)
- Echo Week 12 comparison (toggle)

**Dimension Cards (6 cards):**
Each shows:
- Dimension letter + name
- Current score (1-6)
- Trend indicator (↑ ↓ →)
- Week-over-week history (sparkline)
- Quick update button

**Score Entry:**
- Modal for updating dimension scores
- Evidence notes field
- Date picker (defaults to current week)

**Trust Band Indicator:**
- Large visual showing current band (High / Good / Moderate / Low / Very Low)
- Progress to next band

---

### Tab 3: GOALS Health Dashboard

**Layout:** Bar chart + dimension cards

**Bar Chart:**
- 5 horizontal bars (G, O, A, L, S)
- Color-coded by score (green = high, red = low)
- Target markers

**Dimension Cards (5 cards):**
Each shows:
- Dimension letter + name
- Current score (1-5)
- Trend indicator
- Week-over-week sparkline
- Quick update button

**Maturity Level Indicator:**
- Production-Grade (21-25)
- Adoption-Ready (16-20)
- Emerging (11-15)
- Early-Stage (<11)

---

### Tab 4: 7-Layer Build Status

**Layout:** Visual architecture diagram + layer cards

**Architecture Diagram:**
- Stacked 7-layer visual (like book diagrams)
  - 🔴 Red = Not Started
  - 🟡 Yellow = In Progress
  - 🟢 Green = Operational
- Click layer to expand

**Layer Cards (7 cards):**
Each shows:
- Layer number + name
- Status (radio: Not Started / In Progress / Operational)
- Current tools (editable list)
- Planned tools (editable list)
- Target completion week
- Dependencies (links to other layers)

**Build Order Guidance:**
- Recommended sequence visualization
- Highlight if building out of order (warning)

---

### Tab 5: Risk & Blocker Log

**Layout:** Table + risk matrix

**Risk Table:**
| Column | Description |
|--------|-------------|
| ID | Auto-generated |
| Date Added | Date picker |
| Description | Text |
| Category | Dropdown (Technical / Resource / Timeline / Budget / Stakeholder) |
| Severity | 🔴 Critical / 🟡 Medium / 🟢 Low |
| Impact | Text |
| Mitigation | Text |
| Owner | Text |
| Status | Open / Mitigating / Resolved |
| Resolution Date | Date picker |

**Risk Matrix (Optional):**
- 3x3 grid (Likelihood × Impact)
- Dots representing active risks
- Click to filter table

**Features:**
- Add new risk button
- Filter by severity, status, category
- Export risks to CSV

---

### Tab 6: Stakeholder Communication Log

**Layout:** Table + calendar view

**Communication Table:**
| Column | Description |
|--------|-------------|
| Date | Date picker |
| Type | Dropdown (Meeting / Email / Slack / Decision / Escalation) |
| Participants | Text |
| Summary | Text |
| Decisions | Text |
| Action Items | Text (markdown) |
| Follow-up Date | Date picker |

**Calendar View:**
- Monthly calendar
- Dots on days with communications
- Click to see details

**Features:**
- Add communication button
- Filter by type
- Export to CSV

---

### Tab 7: Budget Tracker

**Layout:** Summary cards + line items table + chart

**Summary Cards:**
- Total Planned Budget
- Total Spent to Date
- Remaining Budget
- Variance ($ and %)

**Budget Table:**
| Column | Description |
|--------|-------------|
| Category | Dropdown (Infrastructure / Software / Services / Personnel / Training / Other) |
| Line Item | Text |
| Vendor | Text |
| Planned Amount | Currency |
| Actual Amount | Currency |
| Variance | Auto-calculated |
| Payment Status | Pending / Paid / Overdue |
| Notes | Text |

**Budget Chart:**
- Cumulative spend over time
- Planned vs Actual lines
- Weekly breakdown

**Features:**
- Add line item button
- Edit line items inline
- Export to CSV
- Import from CSV

---

## Interactive Features

### Echo Health Benchmark Overlay
- Toggle to show Echo's progression
- Side-by-side or overlay comparison
- Available on INPACT, GOALS, and Weekly tabs

### Team Collaboration
- Invite team members by email
- Role-based access (Admin / Editor / Viewer)
- Activity log
- Comments on any item

### Export Options
- Export all data as Excel (.xlsx)
- Export individual tabs as CSV
- Export dashboard as PDF report
- Export charts as PNG

### Notifications
- Weekly reminder to update progress
- Risk escalation alerts
- Milestone completion celebrations

---

## Design Notes

### Brand Colors
- Primary: Teal (from book cover)
- Background: Light gray, White cards

### Charts
- Use Recharts or Chart.js
- Consistent styling across all charts
- Responsive on mobile

### Mobile
- Responsive design
- Tab navigation as bottom bar on mobile
- Swipe between weeks

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | January 2026 | Initial specification |
| 2.0 | January 2026 | Added Technical Implementation Guide |
| 3.0 | January 2026 | Integrated Day Zero Checklist as Tab 0 (merged from standalone tool) |
| 4.0 | February 2026 | **Major Update:** Redesigned Day Zero to tiered system (15/25/35 items) aligned with Chapter 10. New domains: Assessment & Planning, Stakeholder Alignment, Team & Resources, Technical Prerequisites, Data Readiness, Compliance & Risk. Organization tier selector (Essential/Standard/Comprehensive). Each item now has Chapter 10 reference. |

---

# PART 2: TECHNICAL IMPLEMENTATION GUIDE

> **For AI-Assisted Development (Claude Code, Cursor, Windsurf, etc.)**
>
> This section provides the technical specifications needed to build the 90-Day Implementation Tracker. It includes data models, database schema, API endpoints, chart components, and real-time collaboration.

---

## Technology Stack (Recommended)

```
Frontend:
- Framework: Next.js 14+ (App Router)
- State Management: Zustand
- Charts: Recharts
- Tables: TanStack Table (React Table v8)
- Forms: React Hook Form + Zod
- Styling: Tailwind CSS
- Animation: Framer Motion
- Date Handling: date-fns

Backend:
- Runtime: Node.js 18+
- Framework: Next.js API Routes
- Database: PostgreSQL with Prisma ORM
- Real-time: Supabase Realtime or Pusher
- File Export: xlsx (SheetJS), pdfkit

Infrastructure:
- Hosting: Vercel or Railway
- Database: Supabase, PlanetScale, or Neon
- Storage: Supabase Storage or S3 (for exports)
```

---

## Data Models

### 1. Project & Team

```typescript
// types/project.ts

interface Project {
  id: string;
  name: string;
  organization: string;
  createdAt: Date;
  updatedAt: Date;

  // Setup
  industry?: Industry;
  budgetTier?: BudgetTier;
  targetCompletionDate?: Date;
  teamSize?: number;
  organizationSize?: OrganizationSize;  // For Day Zero tier selection

  // Day Zero status (GATE for Week 1)
  dayZeroTier: TierId;                // Essential / Standard / Comprehensive
  dayZeroCompletedAt?: Date;
  dayZeroResults?: DayZeroResults;

type OrganizationSize = "small" | "mid-size" | "large" | "enterprise";

  // Baseline (captured after Day Zero)
  baselineInpact: INPACTScores;
  baselineGoals: GOALSScores;
  baselineLayers: LayerStatus[];

  // Current state
  currentWeek: number;  // 0 = Day Zero, 1-12 = implementation weeks
  phase: Phase;

  // Team
  ownerId: string;
  members: ProjectMember[];
}

type DayZeroStatus = "not-started" | "in-progress" | "ready" | "blocked";
type Phase = "day-zero" | "foundation" | "intelligence" | "trust" | "operations";

interface ProjectMember {
  userId: string;
  email: string;
  name: string;
  role: "admin" | "editor" | "viewer";
  invitedAt: Date;
  acceptedAt?: Date;
}

type Industry = "healthcare" | "financial" | "manufacturing" | "retail" | "technology" | "government" | "other";
type BudgetTier = "starter" | "growth" | "enterprise";
```

### 2. Day Zero Checklist Data Models

```typescript
// types/dayzero.ts

type DomainId = "AP" | "SA" | "TR" | "TP" | "DR" | "CR";
type TierId = "essential" | "standard" | "comprehensive";

interface Domain {
  id: DomainId;
  name: string;
  fullName: string;
  description: string;
  itemCounts: Record<TierId, number>;  // Items per tier
}

const DOMAINS: Domain[] = [
  {
    id: "AP",
    name: "Assessment & Planning",
    fullName: "Domain 1: Assessment & Planning",
    description: "INPACT assessment, layer prioritization, phase strategy",
    itemCounts: { essential: 4, standard: 2, comprehensive: 0 }
  },
  {
    id: "SA",
    name: "Stakeholder Alignment",
    fullName: "Domain 2: Stakeholder Alignment",
    description: "Executive sponsorship, governance, success criteria",
    itemCounts: { essential: 4, standard: 3, comprehensive: 3 }
  },
  {
    id: "TR",
    name: "Team & Resources",
    fullName: "Domain 3: Team & Resources",
    description: "Team allocation, technology track, consulting",
    itemCounts: { essential: 3, standard: 0, comprehensive: 1 }
  },
  {
    id: "TP",
    name: "Technical Prerequisites",
    fullName: "Domain 4: Technical Prerequisites",
    description: "Infrastructure access and technical readiness",
    itemCounts: { essential: 3, standard: 3, comprehensive: 3 }
  },
  {
    id: "DR",
    name: "Data Readiness",
    fullName: "Domain 5: Data Readiness",
    description: "Data inventory and availability",
    itemCounts: { essential: 1, standard: 0, comprehensive: 0 }
  },
  {
    id: "CR",
    name: "Compliance & Risk",
    fullName: "Domain 6: Compliance & Risk",
    description: "Regulatory requirements, phase gate criteria",
    itemCounts: { essential: 0, standard: 2, comprehensive: 3 }
  }
];

// Tier definitions
const TIERS = {
  essential: {
    id: "essential",
    name: "Essential",
    description: "Small organizations (<1,000 employees)",
    itemCount: 15,
    timelineAdjustment: -2,  // weeks
    color: "#22c55e"
  },
  standard: {
    id: "standard",
    name: "Standard",
    description: "Mid-size organizations (1,000-15,000 employees)",
    itemCount: 25,  // 15 + 10
    timelineAdjustment: 0,
    color: "#3b82f6"
  },
  comprehensive: {
    id: "comprehensive",
    name: "Comprehensive",
    description: "Large/Enterprise (15,000+ employees)",
    itemCount: 35,  // 25 + 10
    timelineAdjustment: 2,  // to +4
    color: "#8b5cf6"
  }
};

interface ChecklistItem {
  id: string;                    // e.g., "E-01", "S-03", "C-07"
  domainId: DomainId;
  tier: TierId;                  // Which tier includes this item
  title: string;
  requirement: string;
  chapter10Reference: string;    // Chapter 10 citation
  evidenceItems: string[];       // Sub-checklist
  dataFields?: DataFieldDef[];   // Specific data to collect
  isCritical: boolean;           // ✅ Blocker if not ready
  order: number;                 // Display order within domain
}

interface DataFieldDef {
  key: string;
  label: string;
  type: "text" | "number" | "select" | "multiselect";
  options?: string[];
  required?: boolean;
}

type ItemStatus = "ready" | "in-progress" | "not-ready" | "na";

interface ItemResponse {
  itemId: string;
  evidenceNotes?: string;
  owner?: string;
  targetDate?: Date;
  evidenceChecks: boolean[];     // Which sub-items are checked
  dataValues?: Record<string, any>;  // Collected data field values
  updatedAt: Date;
  updatedBy: string;
}

interface DayZeroResults {
  // Tier context
  selectedTier: TierId;
  tierItemCount: number;  // 15, 25, or 35 based on tier

  // Overall
  totalItems: number;
  applicableItems: number;
  readyCount: number;
  inProgressCount: number;
  notReadyCount: number;
  naCount: number;

  // Scores
  maxScore: number;
  actualScore: number;
  readinessPercentage: number;

  // Verdict
  verdict: DayZeroVerdict;
  criticalBlockers: string[];    // Item IDs (e.g., "E-01", "E-06")

  // Domain breakdown
  domainScores: Record<DomainId, DomainScore>;

  // Timeline impact
  recommendedTimeline: number;  // Adjusted weeks based on tier + special considerations
}

interface DomainScore {
  domainId: DomainId;
  total: number;
  ready: number;
  inProgress: number;
  notReady: number;
  na: number;
  percentage: number;
  hasCriticalBlocker: boolean;
}

type DayZeroVerdict = "ready" | "almost-ready" | "significant-gaps" | "not-ready";

const VERDICT_THRESHOLDS = {
  ready: { min: 90, label: "Ready to Start", color: "#22c55e" },
  "almost-ready": { min: 75, label: "Almost Ready", color: "#3b82f6" },
  "significant-gaps": { min: 50, label: "Significant Gaps", color: "#f97316" },
  "not-ready": { min: 0, label: "Not Ready", color: "#ef4444" }
};
```

### 3. Day Zero Scoring Algorithms

```typescript
// lib/algorithms/dayzero-scoring.ts

import { CHECKLIST_ITEMS, DOMAINS, TIERS } from "@/data/checklistItems";
import { ItemResponse, DayZeroResults, DomainScore, DayZeroVerdict, TierId } from "@/types/dayzero";

const STATUS_POINTS: Record<ItemStatus, number> = {
  ready: 2,
  "in-progress": 1,
  "not-ready": 0,
  na: 0  // Excluded from calculation
};

// Get items applicable to a tier (cumulative)
function getItemsForTier(tier: TierId): ChecklistItem[] {
  const tierOrder: TierId[] = ["essential", "standard", "comprehensive"];
  const tierIndex = tierOrder.indexOf(tier);

  return CHECKLIST_ITEMS.filter(item => {
    const itemTierIndex = tierOrder.indexOf(item.tier);
    return itemTierIndex <= tierIndex;
  });
}

export function calculateDayZeroResults(
  responses: Record<string, ItemResponse>,
  selectedTier: TierId
): DayZeroResults {
  // Get items for selected tier (Essential: 15, Standard: 25, Comprehensive: 35)
  const tierItems = getItemsForTier(selectedTier);
  const totalItems = tierItems.length;
  const tierItemCount = TIERS[selectedTier].itemCount;

  // Count by status
  let readyCount = 0;
  let inProgressCount = 0;
  let notReadyCount = 0;
  let naCount = 0;

  const criticalBlockers: string[] = [];

  // Calculate per item
  for (const item of tierItems) {
    const response = responses[item.id];
    const status = response?.status || "not-ready";

    switch (status) {
      case "ready":
        readyCount++;
        break;
      case "in-progress":
        inProgressCount++;
        break;
      case "not-ready":
        notReadyCount++;
        if (item.isCritical) {
          criticalBlockers.push(item.id);
        }
        break;
      case "na":
        naCount++;
        break;
    }
  }

  // Calculate scores
  const applicableItems = totalItems - naCount;
  const maxScore = applicableItems * 2;
  const actualScore = readyCount * 2 + inProgressCount * 1;
  const readinessPercentage = maxScore > 0
    ? Math.round((actualScore / maxScore) * 100)
    : 0;

  // Determine verdict
  let verdict: DayZeroVerdict;
  if (criticalBlockers.length > 0) {
    verdict = "not-ready";
  } else if (readinessPercentage >= 90) {
    verdict = "ready";
  } else if (readinessPercentage >= 75) {
    verdict = "almost-ready";
  } else if (readinessPercentage >= 50) {
    verdict = "significant-gaps";
  } else {
    verdict = "not-ready";
  }

  // Calculate domain scores (only for tier items)
  const domainScores = calculateDomainScores(responses, selectedTier);

  // Calculate recommended timeline
  const baseTimeline = 12;  // weeks
  const tierAdjustment = TIERS[selectedTier].timelineAdjustment;
  const recommendedTimeline = baseTimeline + tierAdjustment;

  return {
    selectedTier,
    tierItemCount,
    totalItems,
    applicableItems,
    readyCount,
    inProgressCount,
    notReadyCount,
    naCount,
    maxScore,
    actualScore,
    readinessPercentage,
    verdict,
    criticalBlockers,
    domainScores,
    recommendedTimeline
  };
}

function calculateDomainScores(
  responses: Record<string, ItemResponse>,
  selectedTier: TierId
): Record<DomainId, DomainScore> {
  const domainScores: Record<DomainId, DomainScore> = {} as any;
  const tierItems = getItemsForTier(selectedTier);

  for (const domain of DOMAINS) {
    // Only include items that are part of the selected tier
    const domainItems = tierItems.filter(i => i.domainId === domain.id);
    let ready = 0, inProgress = 0, notReady = 0, na = 0;
    let hasCriticalBlocker = false;

    for (const item of domainItems) {
      const response = responses[item.id];
      const status = response?.status || "not-ready";

      switch (status) {
        case "ready": ready++; break;
        case "in-progress": inProgress++; break;
        case "not-ready":
          notReady++;
          if (item.isCritical) hasCriticalBlocker = true;
          break;
        case "na": na++; break;
      }
    }

    const applicable = domainItems.length - na;
    const score = ready * 2 + inProgress * 1;
    const maxScore = applicable * 2;
    const percentage = maxScore > 0 ? Math.round((score / maxScore) * 100) : 0;

    domainScores[domain.id] = {
      domainId: domain.id,
      total: domainItems.length,
      ready,
      inProgress,
      notReady,
      na,
      percentage,
      hasCriticalBlocker
    };
  }

  return domainScores;
}

// Check if Day Zero is complete enough to unlock Week 1
export function canUnlockWeek1(results: DayZeroResults): boolean {
  return results.verdict === "ready" && results.criticalBlockers.length === 0;
}
```

### 4. INPACT & GOALS Tracking

```typescript
// types/scores.ts

type DimensionId = "I" | "N" | "P" | "A" | "C" | "T";
type GoalsDimensionId = "G" | "O" | "A" | "L" | "S";

interface INPACTScores {
  I: number;  // 1-6
  N: number;
  P: number;
  A: number;
  C: number;
  T: number;
  total: number;  // 6-36
  percentage: number;  // 0-100
  trustBand: TrustBand;
}

interface GOALSScores {
  G: number;  // 1-5
  O: number;
  A: number;
  L: number;
  S: number;
  total: number;  // 5-25
  maturityLevel: MaturityLevel;
}

interface ScoreEntry {
  id: string;
  projectId: string;
  week: number;
  type: "inpact" | "goals";
  scores: INPACTScores | GOALSScores;
  notes?: string;
  recordedAt: Date;
  recordedBy: string;
}

type TrustBand = "high" | "good" | "moderate" | "low" | "very-low";
type MaturityLevel = "production" | "adoption" | "emerging" | "early";

// Trust band thresholds
const TRUST_BANDS = {
  high: { min: 86, max: 100, label: "High Trust", color: "#22c55e" },
  good: { min: 67, max: 85, label: "Good Trust", color: "#3b82f6" },
  moderate: { min: 50, max: 66, label: "Moderate Trust", color: "#eab308" },
  low: { min: 33, max: 49, label: "Low Trust", color: "#f97316" },
  "very-low": { min: 0, max: 32, label: "Very Low Trust", color: "#ef4444" }
};

// Maturity level thresholds
const MATURITY_LEVELS = {
  production: { min: 21, max: 25, label: "Production-Grade", color: "#22c55e" },
  adoption: { min: 16, max: 20, label: "Adoption-Ready", color: "#3b82f6" },
  emerging: { min: 11, max: 15, label: "Emerging", color: "#eab308" },
  early: { min: 5, max: 10, label: "Early-Stage", color: "#ef4444" }
};
```

### 5. Weekly Progress

```typescript
// types/weekly.ts

interface WeekProgress {
  id: string;
  projectId: string;
  week: number;  // 1-12

  // Status
  phase: Phase;
  primaryLayerFocus: LayerId;

  // Scores (references to ScoreEntry)
  inpactEntryId?: string;
  goalsEntryId?: string;

  // Content
  keyDeliverable?: string;
  deliverableStatus?: DeliverableStatus;
  topRisk?: string;
  riskSeverity?: Severity;
  notes?: string;

  // Completion
  completedAt?: Date;
  completedBy?: string;

  createdAt: Date;
  updatedAt: Date;
}

type WeekStatus = "not-started" | "in-progress" | "on-track" | "at-risk" | "blocked" | "complete";
type DeliverableStatus = "not-started" | "in-progress" | "complete" | "blocked";
type Severity = "critical" | "medium" | "low";
type LayerId = "L1" | "L2" | "L3" | "L4" | "L5" | "L6" | "L7";

// Phase to week mapping
const PHASE_WEEKS = {
  foundation: [1, 2, 3, 4],
  intelligence: [5, 6, 7],
  trust: [8, 9, 10],
  operations: [11, 12]
};
```

### 6. 7-Layer Architecture

```typescript
// types/layers.ts

interface LayerStatus {
  id: string;
  projectId: string;
  layer: LayerId;

  // Status
  targetWeek?: number;

  // Tools
  currentTools: string[];
  plannedTools: string[];

  // Notes
  notes?: string;

  updatedAt: Date;
  updatedBy: string;
}

type BuildStatus = "not-started" | "in-progress" | "operational";

const LAYERS = [
  { id: "L1", name: "Multi-Modal Storage", description: "Vector DBs, Graph DBs, Warehouses" },
  { id: "L2", name: "Real-Time Data Fabric", description: "CDC, Streaming, Ingestion" },
  { id: "L3", name: "Universal Semantic Layer", description: "Semantic Platforms, Catalogs" },
  { id: "L4", name: "Intelligence Orchestration", description: "RAG, Embeddings, Caching" },
  { id: "L5", name: "Agent-Aware Governance", description: "ABAC, Audit, Secrets" },
  { id: "L6", name: "Observability & Feedback", description: "APM, LLM Monitoring" },
  { id: "L7", name: "Self-Service Data Products", description: "Orchestration, Gateways" }
];

// Recommended build order
const RECOMMENDED_ORDER = ["L1", "L2", "L5", "L3", "L4", "L6", "L7"];
```

### 7. Risks & Blockers

```typescript
// types/risks.ts

interface Risk {
  id: string;
  projectId: string;

  // Content
  description: string;
  category: RiskCategory;
  severity: Severity;
  impact: string;
  mitigation?: string;

  // Assignment
  owner?: string;

  // Status
  dateAdded: Date;
  resolutionDate?: Date;

  createdBy: string;
  updatedAt: Date;
}

type RiskCategory = "technical" | "resource" | "timeline" | "budget" | "stakeholder" | "other";
type RiskStatus = "open" | "mitigating" | "resolved" | "accepted";
```

### 8. Communications

```typescript
// types/communications.ts

interface Communication {
  id: string;
  projectId: string;

  // Content
  date: Date;
  type: CommunicationType;
  participants: string;
  summary: string;
  decisions?: string;
  actionItems?: string;
  followUpDate?: Date;

  createdBy: string;
  createdAt: Date;
}

type CommunicationType = "meeting" | "email" | "slack" | "decision" | "escalation" | "review";
```

### 9. Budget

```typescript
// types/budget.ts

interface BudgetLineItem {
  id: string;
  projectId: string;

  // Details
  category: BudgetCategory;
  lineItem: string;
  vendor?: string;

  // Amounts
  plannedAmount: number;
  actualAmount: number;

  // Status
  notes?: string;

  createdAt: Date;
  updatedAt: Date;
}

type BudgetCategory = "infrastructure" | "software" | "services" | "personnel" | "training" | "other";
type PaymentStatus = "pending" | "paid" | "overdue";

interface BudgetSummary {
  totalPlanned: number;
  totalActual: number;
  remaining: number;
  variance: number;
  variancePercent: number;
}
```

---

## Database Schema

```sql
-- PostgreSQL schema

-- Projects (includes Day Zero state)
CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(255) NOT NULL,
  organization VARCHAR(255) NOT NULL,
  owner_id UUID NOT NULL,

  -- Setup
  industry VARCHAR(50),
  budget_tier VARCHAR(20),
  target_completion_date DATE,
  team_size INTEGER,
  organization_size VARCHAR(20),  -- 'small', 'mid-size', 'large', 'enterprise'

  -- Day Zero state (GATE for Week 1)
  day_zero_tier VARCHAR(20) DEFAULT 'standard',  -- 'essential', 'standard', 'comprehensive'
  day_zero_status VARCHAR(20) DEFAULT 'not-started',  -- 'not-started', 'in-progress', 'ready', 'blocked'
  day_zero_completed_at TIMESTAMP,
  day_zero_results JSONB,  -- Cached DayZeroResults (includes tier context)

  -- Baseline (captured after Day Zero)
  baseline_inpact JSONB,
  baseline_goals JSONB,

  -- Current state
  current_week INTEGER DEFAULT 0,  -- 0 = Day Zero, 1-12 = implementation weeks
  phase VARCHAR(20) DEFAULT 'day-zero',  -- 'day-zero', 'foundation', 'intelligence', 'trust', 'operations'

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Day Zero checklist responses
CREATE TABLE dayzero_responses (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  item_id VARCHAR(10) NOT NULL,  -- e.g., "E-01", "S-03", "C-07"

  status VARCHAR(20) NOT NULL,  -- 'ready', 'in-progress', 'not-ready', 'na'
  evidence_notes TEXT,
  owner VARCHAR(255),
  target_date DATE,
  evidence_checks BOOLEAN[] DEFAULT '{}',
  data_values JSONB DEFAULT '{}',  -- Item-specific data collected

  updated_at TIMESTAMP DEFAULT NOW(),
  updated_by UUID,

  UNIQUE(project_id, item_id)
);

-- Project members
CREATE TABLE project_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  user_id UUID NOT NULL,
  email VARCHAR(255) NOT NULL,
  name VARCHAR(255) NOT NULL,
  role VARCHAR(20) NOT NULL,  -- 'admin', 'editor', 'viewer'
  invited_at TIMESTAMP DEFAULT NOW(),
  accepted_at TIMESTAMP,

  UNIQUE(project_id, email)
);

-- Score entries (INPACT and GOALS)
CREATE TABLE score_entries (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  week INTEGER NOT NULL,
  type VARCHAR(10) NOT NULL,  -- 'inpact' or 'goals'
  scores JSONB NOT NULL,
  notes TEXT,
  recorded_at TIMESTAMP DEFAULT NOW(),
  recorded_by UUID NOT NULL,

  UNIQUE(project_id, week, type)
);

-- Weekly progress
CREATE TABLE week_progress (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  week INTEGER NOT NULL,

  phase VARCHAR(20) NOT NULL,
  status VARCHAR(20) DEFAULT 'not-started',
  primary_layer_focus VARCHAR(5),

  inpact_entry_id UUID REFERENCES score_entries(id),
  goals_entry_id UUID REFERENCES score_entries(id),

  key_deliverable TEXT,
  deliverable_status VARCHAR(20),
  top_risk TEXT,
  risk_severity VARCHAR(20),
  notes TEXT,

  completed_at TIMESTAMP,
  completed_by UUID,

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW(),

  UNIQUE(project_id, week)
);

-- Layer status
CREATE TABLE layer_status (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  layer VARCHAR(5) NOT NULL,

  status VARCHAR(20) DEFAULT 'not-started',
  target_week INTEGER,

  current_tools TEXT[] DEFAULT '{}',
  planned_tools TEXT[] DEFAULT '{}',
  notes TEXT,

  updated_at TIMESTAMP DEFAULT NOW(),
  updated_by UUID,

  UNIQUE(project_id, layer)
);

-- Risks
CREATE TABLE risks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,

  description TEXT NOT NULL,
  category VARCHAR(20) NOT NULL,
  severity VARCHAR(20) NOT NULL,
  impact TEXT,
  mitigation TEXT,
  owner VARCHAR(255),

  status VARCHAR(20) DEFAULT 'open',
  date_added DATE DEFAULT CURRENT_DATE,
  resolution_date DATE,

  created_by UUID NOT NULL,
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Communications
CREATE TABLE communications (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,

  date DATE NOT NULL,
  type VARCHAR(20) NOT NULL,
  participants TEXT,
  summary TEXT NOT NULL,
  decisions TEXT,
  action_items TEXT,
  follow_up_date DATE,

  created_by UUID NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Budget line items
CREATE TABLE budget_items (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,

  category VARCHAR(20) NOT NULL,
  line_item VARCHAR(255) NOT NULL,
  vendor VARCHAR(255),

  planned_amount DECIMAL(12, 2) DEFAULT 0,
  actual_amount DECIMAL(12, 2) DEFAULT 0,

  payment_status VARCHAR(20) DEFAULT 'pending',
  notes TEXT,

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Indexes
CREATE INDEX idx_projects_owner ON projects(owner_id);
CREATE INDEX idx_projects_dayzero ON projects(day_zero_status);
CREATE INDEX idx_dayzero_project ON dayzero_responses(project_id);
CREATE INDEX idx_dayzero_status ON dayzero_responses(project_id, status);
CREATE INDEX idx_members_project ON project_members(project_id);
CREATE INDEX idx_scores_project_week ON score_entries(project_id, week);
CREATE INDEX idx_weeks_project ON week_progress(project_id);
CREATE INDEX idx_layers_project ON layer_status(project_id);
CREATE INDEX idx_risks_project ON risks(project_id);
CREATE INDEX idx_comms_project ON communications(project_id);
CREATE INDEX idx_budget_project ON budget_items(project_id);
```

---

## API Endpoints

```typescript
// Next.js App Router API Routes

// Projects
// POST /api/projects - Create new project
// GET /api/projects - List user's projects
// GET /api/projects/:id - Get project details
// PATCH /api/projects/:id - Update project
// DELETE /api/projects/:id - Delete project

// Day Zero (Tab 0) - GATE for Week 1
// GET /api/projects/:id/dayzero - Get Day Zero checklist state
// GET /api/projects/:id/dayzero/responses - Get all responses
// POST /api/projects/:id/dayzero/responses - Save single response
// POST /api/projects/:id/dayzero/responses/bulk - Save multiple responses
// GET /api/projects/:id/dayzero/results - Get computed results
// POST /api/projects/:id/dayzero/complete - Mark Day Zero complete (unlocks Week 1)
// GET /api/projects/:id/dayzero/export/pdf - Export as PDF
// GET /api/projects/:id/dayzero/export/xlsx - Export as Excel

// Team
// POST /api/projects/:id/members - Invite member
// DELETE /api/projects/:id/members/:userId - Remove member
// PATCH /api/projects/:id/members/:userId - Update role

// Scores
// POST /api/projects/:id/scores - Add score entry
// GET /api/projects/:id/scores - Get all scores
// GET /api/projects/:id/scores/latest - Get latest scores
// GET /api/projects/:id/scores/history - Get score history for charts

// Weekly Progress
// GET /api/projects/:id/weeks - Get all weeks
// GET /api/projects/:id/weeks/:week - Get specific week
// PATCH /api/projects/:id/weeks/:week - Update week
// POST /api/projects/:id/weeks/:week/complete - Mark week complete

// Layers
// GET /api/projects/:id/layers - Get all layers
// PATCH /api/projects/:id/layers/:layer - Update layer status

// Risks
// GET /api/projects/:id/risks - Get all risks
// POST /api/projects/:id/risks - Add risk
// PATCH /api/projects/:id/risks/:riskId - Update risk
// DELETE /api/projects/:id/risks/:riskId - Delete risk

// Communications
// GET /api/projects/:id/communications - Get all communications
// POST /api/projects/:id/communications - Add communication
// PATCH /api/projects/:id/communications/:commId - Update
// DELETE /api/projects/:id/communications/:commId - Delete

// Budget
// GET /api/projects/:id/budget - Get all budget items + summary
// POST /api/projects/:id/budget - Add budget item
// PATCH /api/projects/:id/budget/:itemId - Update item
// DELETE /api/projects/:id/budget/:itemId - Delete item

// Export
// GET /api/projects/:id/export/xlsx - Export as Excel
// GET /api/projects/:id/export/pdf - Export as PDF report
```

---

## React Components

### 1. Component Structure

```
components/
├── dashboard/
│   ├── DashboardLayout.tsx      # Main layout with tabs
│   ├── TabNavigation.tsx        # Tab bar (8 tabs: 0-7)
│   ├── ProjectHeader.tsx        # Project info + actions
│   └── tabs/
│       ├── DayZeroTab.tsx       # Tab 0: Day Zero Readiness ⭐
│       ├── WeeklyProgress.tsx   # Tab 1
│       ├── InpactTracker.tsx    # Tab 2
│       ├── GoalsTracker.tsx     # Tab 3
│       ├── LayerStatus.tsx      # Tab 4
│       ├── RiskLog.tsx          # Tab 5
│       ├── CommunicationLog.tsx # Tab 6
│       └── BudgetTracker.tsx    # Tab 7
├── dayzero/
│   ├── ChecklistLayout.tsx      # Three-panel Day Zero layout
│   ├── DomainNav.tsx            # Left sidebar: 5 domains
│   ├── DomainPanel.tsx          # Main checklist area
│   ├── ProgressPanel.tsx        # Right sidebar: overall progress
│   ├── ChecklistItem.tsx        # Single item card
│   ├── EvidenceChecklist.tsx    # Sub-item checks
│   ├── StatusSelector.tsx       # Ready/In Progress/Not Ready/N/A
│   ├── VerdictCard.tsx          # Readiness verdict + gate status
│   └── UnlockWeek1Button.tsx    # Gate button to proceed
├── charts/
│   ├── INPACTRadar.tsx          # Radar chart
│   ├── GOALSBar.tsx             # Horizontal bars
│   ├── ScoreSparkline.tsx       # Mini trend line
│   ├── BudgetLine.tsx           # Cumulative spend
│   └── ArchitectureDiagram.tsx  # 7-layer visual
├── forms/
│   ├── ScoreEntryModal.tsx      # Update scores
│   ├── WeekEditModal.tsx        # Edit week details
│   ├── RiskForm.tsx             # Add/edit risk
│   ├── CommunicationForm.tsx    # Add/edit communication
│   └── BudgetItemForm.tsx       # Add/edit budget item
├── tables/
│   ├── RiskTable.tsx            # Risks table
│   ├── CommunicationTable.tsx   # Communications table
│   └── BudgetTable.tsx          # Budget table
├── cards/
│   ├── WeekCard.tsx             # Week summary card
│   ├── DimensionCard.tsx        # Score dimension
│   ├── LayerCard.tsx            # Layer status
│   └── StatCard.tsx             # Summary stat
└── ui/
    ├── StatusBadge.tsx
    ├── SeverityBadge.tsx
    ├── ProgressBar.tsx
    └── TrustBandBadge.tsx
```

### 2. Day Zero Checklist Item Component

```tsx
// components/dayzero/ChecklistItem.tsx

import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { ChecklistItem as ChecklistItemType, ItemResponse } from "@/types/dayzero";
import { StatusSelector } from "./StatusSelector";
import { EvidenceChecklist } from "./EvidenceChecklist";

interface Props {
  item: ChecklistItemType;
  response?: ItemResponse;
  onUpdate: (response: Partial<ItemResponse>) => void;
}

export function ChecklistItem({ item, response, onUpdate }: Props) {
  const [expanded, setExpanded] = useState(false);
  const status = response?.status || undefined;

  return (
    <div
      className={`
        rounded-xl border-2 overflow-hidden transition-all
        ${item.isCritical ? "border-l-4 border-l-red-500" : ""}
        ${status === "ready" ? "border-green-200 bg-green-50" : ""}
        ${status === "in-progress" ? "border-yellow-200 bg-yellow-50" : ""}
        ${status === "not-ready" ? "border-red-200 bg-red-50" : ""}
        ${status === "na" ? "border-gray-200 bg-gray-50 opacity-60" : ""}
        ${!status ? "border-gray-200 bg-white" : ""}
      `}
    >
      {/* Header */}
      <div className="p-4">
        <div className="flex items-start justify-between gap-4">
          <div className="flex-1">
            <div className="flex items-center gap-2 mb-1">
              <span className="font-mono text-sm text-gray-500 bg-gray-100 px-2 py-0.5 rounded">
                {item.id}
              </span>
              {item.isCritical && (
                <span className="text-xs bg-red-100 text-red-700 px-2 py-0.5 rounded-full font-medium">
                  Critical
                </span>
              )}
            </div>
            <h3 className="font-semibold text-gray-900">{item.title}</h3>
            <p className="text-sm text-gray-600 mt-1">{item.requirement}</p>
          </div>

          <StatusSelector
            value={status}
          />
        </div>

        {/* Expand button */}
        <button
          onClick={() => setExpanded(!expanded)}
          className="mt-3 text-sm text-teal-600 hover:text-teal-700 flex items-center gap-1"
        >
          {expanded ? "Hide details" : "Show details"}
          <svg
            className={`w-4 h-4 transition-transform ${expanded ? "rotate-180" : ""}`}
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M19 9l-7 7-7-7" />
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
              {/* Evidence checklist */}
              <div>
                <h4 className="text-sm font-medium text-gray-700 mb-2">
                  Evidence Required:
                </h4>
                <EvidenceChecklist
                  items={item.evidenceItems}
                  checks={response?.evidenceChecks || []}
                  onChange={(checks) => onUpdate({ evidenceChecks: checks })}
                />
              </div>

              {/* Echo example */}
              <div className="bg-blue-50 border border-blue-100 rounded-lg p-3">
                <h4 className="text-sm font-medium text-blue-800 mb-1">
                  Echo Health Example:
                </h4>
                <p className="text-sm text-blue-700">{item.echoExample}</p>
              </div>

              {/* Additional fields */}
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
                    Target Date
                  </label>
                  <input
                    type="date"
                    value={response?.targetDate?.toISOString().split("T")[0] || ""}
                    onChange={(e) => onUpdate({ targetDate: new Date(e.target.value) })}
                    className="w-full px-3 py-2 border rounded-lg text-sm"
                  />
                </div>
              </div>

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
                  placeholder="Document evidence or notes..."
                />
              </div>
            </div>
          </motion.div>
        )}
      </AnimatePresence>
    </div>
  );
}
```

### 3. Day Zero Verdict Card Component

```tsx
// components/dayzero/VerdictCard.tsx

import { motion } from "framer-motion";
import { DayZeroVerdict, VERDICT_THRESHOLDS } from "@/types/dayzero";
import { CHECKLIST_ITEMS } from "@/data/checklistItems";

interface Props {
  verdict: DayZeroVerdict;
  percentage: number;
  criticalBlockers: string[];
  onProceed?: () => void;
}

export function VerdictCard({ verdict, percentage, criticalBlockers, onProceed }: Props) {
  const verdictInfo = VERDICT_THRESHOLDS[verdict];
  const canProceed = verdict === "ready" && criticalBlockers.length === 0;

  return (
    <motion.div
      className="rounded-2xl overflow-hidden shadow-xl"
      initial={{ opacity: 0, scale: 0.9 }}
      animate={{ opacity: 1, scale: 1 }}
    >
      {/* Header with verdict */}
      <div
        className="p-8 text-center text-white"
        style={{ backgroundColor: verdictInfo.color }}
      >
        <div className="text-6xl font-bold mb-2">{percentage}%</div>
        <div className="text-2xl font-semibold">{verdictInfo.label}</div>
        <div className="text-sm opacity-80 mt-2">Day Zero Readiness Score</div>
      </div>

      {/* Body */}
      <div className="bg-white p-6">
        {/* Critical blockers */}
        {criticalBlockers.length > 0 && (
          <div className="mb-6 p-4 bg-red-50 border border-red-200 rounded-lg">
            <h3 className="font-semibold text-red-800 mb-2 flex items-center gap-2">
              <span>⚠️</span> Critical Blockers
            </h3>
            <p className="text-sm text-red-700 mb-3">
              These must be resolved before starting Week 1:
            </p>
            <ul className="space-y-1">
              {criticalBlockers.map((itemId) => {
                const item = CHECKLIST_ITEMS.find(i => i.id === itemId);
                return (
                  <li key={itemId} className="flex items-center gap-2 text-sm">
                    <span className="font-mono bg-red-100 text-red-800 px-1.5 py-0.5 rounded text-xs">
                      {itemId}
                    </span>
                    <span className="text-red-800">{item?.title}</span>
                  </li>
                );
              })}
            </ul>
          </div>
        )}

        {/* Proceed button or blocker message */}
        {canProceed ? (
          <button
            onClick={onProceed}
            className="w-full py-4 bg-teal-600 text-white rounded-xl font-semibold text-lg hover:bg-teal-700 transition-colors flex items-center justify-center gap-2"
          >
            <span>🚀</span> Proceed to Week 1
          </button>
        ) : (
          <div className="text-center p-4 bg-gray-100 rounded-xl">
            <div className="text-gray-500 font-medium">Week 1 Locked</div>
            <div className="text-sm text-gray-400 mt-1">
              {criticalBlockers.length > 0
                ? "Resolve critical blockers to unlock"
                : "Achieve 90%+ readiness to unlock"
              }
            </div>
          </div>
        )}
      </div>
    </motion.div>
  );
}
```

### 4. INPACT Radar Chart Component

```tsx
// components/charts/INPACTRadar.tsx

import {
  Radar,
  RadarChart,
  PolarGrid,
  PolarAngleAxis,
  PolarRadiusAxis,
  Legend,
  ResponsiveContainer,
  Tooltip
} from "recharts";

interface Props {
  current: INPACTScores;
  baseline?: INPACTScores;
  target?: INPACTScores;
  showEchoBaseline?: boolean;
  showEchoFinal?: boolean;
}

const DIMENSIONS = [
  { key: "I", label: "Instant" },
  { key: "N", label: "Natural" },
  { key: "P", label: "Permitted" },
  { key: "A", label: "Adaptive" },
  { key: "C", label: "Contextual" },
  { key: "T", label: "Transparent" }
];

const ECHO_BASELINE = { I: 1.3, N: 2.2, P: 1.3, A: 1.5, C: 2.5, T: 1.2 };
const ECHO_FINAL = { I: 5.7, N: 5.3, P: 5.5, A: 5.0, C: 5.7, T: 4.8 };

export function INPACTRadar({
  current,
  baseline,
  target,
  showEchoBaseline,
  showEchoFinal
}: Props) {
  const data = DIMENSIONS.map(dim => ({
    dimension: dim.label,
    current: current[dim.key as keyof INPACTScores] as number,
    baseline: baseline?.[dim.key as keyof INPACTScores] as number,
    target: target?.[dim.key as keyof INPACTScores] as number,
    echoBaseline: showEchoBaseline ? ECHO_BASELINE[dim.key as keyof typeof ECHO_BASELINE] : undefined,
    echoFinal: showEchoFinal ? ECHO_FINAL[dim.key as keyof typeof ECHO_FINAL] : undefined
  }));

  return (
    <ResponsiveContainer width="100%" height={400}>
      <RadarChart data={data}>
        <PolarGrid stroke="#e5e7eb" />
        <PolarAngleAxis
          dataKey="dimension"
          tick={{ fill: "#374151", fontSize: 12 }}
        />
        <PolarRadiusAxis
          angle={30}
          domain={[0, 6]}
          tickCount={7}
          tick={{ fill: "#9ca3af", fontSize: 10 }}
        />

        {/* Current score */}
        <Radar
          name="Current"
          dataKey="current"
          stroke="#14b8a6"
          fill="#14b8a6"
          fillOpacity={0.3}
          strokeWidth={2}
        />

        {/* Baseline (if provided) */}
        {baseline && (
          <Radar
            name="Baseline"
            dataKey="baseline"
            stroke="#9ca3af"
            fill="none"
            strokeWidth={1}
            strokeDasharray="5 5"
          />
        )}

        {/* Target (if provided) */}
        {target && (
          <Radar
            name="Target"
            dataKey="target"
            stroke="#22c55e"
            fill="none"
            strokeWidth={1}
            strokeDasharray="3 3"
          />
        )}

        {/* Echo benchmarks */}
        {showEchoBaseline && (
          <Radar
            name="Echo (Week 0)"
            dataKey="echoBaseline"
            stroke="#f97316"
            fill="none"
            strokeWidth={1}
            strokeDasharray="2 2"
          />
        )}

        {showEchoFinal && (
          <Radar
            name="Echo (Week 12)"
            dataKey="echoFinal"
            stroke="#22c55e"
            fill="none"
            strokeWidth={1}
          />
        )}

        <Legend />
        <Tooltip />
      </RadarChart>
    </ResponsiveContainer>
  );
}
```

### 5. 7-Layer Architecture Diagram

```tsx
// components/charts/ArchitectureDiagram.tsx

import { motion } from "framer-motion";
import { LayerStatus } from "@/types/layers";

interface Props {
  layers: LayerStatus[];
  onLayerClick: (layerId: string) => void;
}

const LAYER_DEFINITIONS = [
  { id: "L7", name: "Self-Service Data Products", height: 60 },
  { id: "L6", name: "Observability & Feedback", height: 50 },
  { id: "L5", name: "Agent-Aware Governance", height: 50 },
  { id: "L4", name: "Intelligence Orchestration", height: 60 },
  { id: "L3", name: "Universal Semantic Layer", height: 50 },
  { id: "L2", name: "Real-Time Data Fabric", height: 50 },
  { id: "L1", name: "Multi-Modal Storage", height: 60 }
];

const STATUS_COLORS = {
  "not-started": { bg: "#fecaca", border: "#ef4444", text: "#991b1b" },
  "in-progress": { bg: "#fef3c7", border: "#f59e0b", text: "#92400e" },
  "operational": { bg: "#bbf7d0", border: "#22c55e", text: "#166534" }
};

export function ArchitectureDiagram({ layers, onLayerClick }: Props) {
  const getLayerStatus = (layerId: string) =>
    layers.find(l => l.layer === layerId)?.status || "not-started";

  return (
    <div className="flex flex-col gap-2 p-4">
      {LAYER_DEFINITIONS.map((layer, index) => {
        const status = getLayerStatus(layer.id);
        const colors = STATUS_COLORS[status];

        return (
          <motion.button
            key={layer.id}
            onClick={() => onLayerClick(layer.id)}
            className="relative rounded-lg border-2 transition-all hover:shadow-md"
            style={{
              height: layer.height,
              backgroundColor: colors.bg,
              borderColor: colors.border
            }}
            whileHover={{ scale: 1.02 }}
            whileTap={{ scale: 0.98 }}
            initial={{ opacity: 0, x: -20 }}
            animate={{ opacity: 1, x: 0 }}
            transition={{ delay: index * 0.1 }}
          >
            <div className="absolute inset-0 flex items-center justify-between px-4">
              <div className="flex items-center gap-3">
                <span
                  className="font-mono font-bold text-lg"
                  style={{ color: colors.text }}
                >
                  {layer.id}
                </span>
                <span className="font-medium" style={{ color: colors.text }}>
                  {layer.name}
                </span>
              </div>

              <div className="flex items-center gap-2">
                <span
                  className="text-xs uppercase font-semibold px-2 py-1 rounded"
                  style={{
                    backgroundColor: colors.border,
                    color: "white"
                  }}
                >
                  {status.replace("-", " ")}
                </span>
              </div>
            </div>
          </motion.button>
        );
      })}

      {/* Legend */}
      <div className="flex justify-center gap-6 mt-4 text-sm">
        {Object.entries(STATUS_COLORS).map(([status, colors]) => (
          <div key={status} className="flex items-center gap-2">
            <div
              className="w-4 h-4 rounded border-2"
              style={{
                backgroundColor: colors.bg,
                borderColor: colors.border
              }}
            />
            <span className="capitalize">{status.replace("-", " ")}</span>
          </div>
        ))}
      </div>
    </div>
  );
}
```

### 6. Week Card Component

```tsx
// components/cards/WeekCard.tsx

import { motion } from "framer-motion";
import { WeekProgress } from "@/types/weekly";
import { StatusBadge } from "@/components/ui/StatusBadge";
import { SeverityBadge } from "@/components/ui/SeverityBadge";

interface Props {
  week: WeekProgress;
  isCurrentWeek: boolean;
  scores?: { inpact: number; goals: number };
  onClick: () => void;
}

const PHASE_COLORS = {
  foundation: "#3b82f6",    // blue
  intelligence: "#8b5cf6",  // purple
  trust: "#22c55e",         // green
  operations: "#f97316"     // orange
};

export function WeekCard({ week, isCurrentWeek, scores, onClick }: Props) {
  return (
    <motion.button
      onClick={onClick}
      className={`
        w-full text-left rounded-xl border-2 p-4 transition-all
        ${isCurrentWeek
          ? "border-teal-500 bg-teal-50 shadow-md"
          : "border-gray-200 bg-white hover:border-gray-300 hover:shadow"
        }
      `}
      whileHover={{ scale: 1.01 }}
      whileTap={{ scale: 0.99 }}
    >
      {/* Header */}
      <div className="flex items-center justify-between mb-3">
        <div className="flex items-center gap-2">
          <span className="text-lg font-bold text-gray-900">
            Week {week.week}
          </span>
          <span
            className="text-xs px-2 py-0.5 rounded-full font-medium capitalize"
            style={{
              backgroundColor: `${PHASE_COLORS[week.phase]}20`,
              color: PHASE_COLORS[week.phase]
            }}
          >
            {week.phase}
          </span>
        </div>

        <StatusBadge status={week.status} />
      </div>

      {/* Layer focus */}
      {week.primaryLayerFocus && (
        <div className="text-sm text-gray-600 mb-2">
          <span className="font-medium">Focus:</span> {week.primaryLayerFocus}
        </div>
      )}

      {/* Scores (if available) */}
      {scores && (
        <div className="flex gap-4 mb-3">
          <div className="text-sm">
            <span className="text-gray-500">INPACT:</span>{" "}
            <span className="font-semibold text-teal-600">
              {scores.inpact}%
            </span>
          </div>
          <div className="text-sm">
            <span className="text-gray-500">GOALS:</span>{" "}
            <span className="font-semibold text-blue-600">
              {scores.goals}/25
            </span>
          </div>
        </div>
      )}

      {/* Deliverable */}
      {week.keyDeliverable && (
        <div className="text-sm mb-2">
          <span className="text-gray-500">Deliverable:</span>{" "}
          <span className="text-gray-900">{week.keyDeliverable}</span>
        </div>
      )}

      {/* Risk */}
      {week.topRisk && (
        <div className="flex items-center gap-2 text-sm">
          <span className="text-gray-500">Top Risk:</span>
          <SeverityBadge severity={week.riskSeverity || "medium"} />
          <span className="text-gray-900 truncate">{week.topRisk}</span>
        </div>
      )}

      {/* Current week indicator */}
      {isCurrentWeek && (
        <div className="mt-3 pt-3 border-t border-teal-200">
          <span className="text-xs font-medium text-teal-600 uppercase">
            Current Week
          </span>
        </div>
      )}
    </motion.button>
  );
}
```

---

## State Management

```typescript
// lib/store/trackerStore.ts

import { create } from "zustand";
import { persist } from "zustand/middleware";

interface TrackerState {
  // Project
  projectId: string | null;
  project: Project | null;

  // Day Zero (Tab 0)
  dayZeroTier: TierId;             // Selected tier (essential/standard/comprehensive)
  dayZeroResponses: Record<string, ItemResponse>;
  dayZeroResults: DayZeroResults | null;
  dayZeroCurrentDomain: DomainId;

  // Scores
  inpactHistory: ScoreEntry[];
  goalsHistory: ScoreEntry[];
  latestInpact: INPACTScores | null;
  latestGoals: GOALSScores | null;

  // Weeks
  weeks: WeekProgress[];
  currentWeek: number;  // 0 = Day Zero, 1-12 = weeks

  // Layers
  layers: LayerStatus[];

  // Risks & Budget
  risks: Risk[];
  budgetItems: BudgetLineItem[];

  // UI State
  activeTab: number;  // 0 = Day Zero, 1-7 = other tabs
  showEchoBenchmark: boolean;

  // Actions
  loadProject: (projectId: string) => Promise<void>;

  // Day Zero actions
  setDayZeroTier: (tier: TierId) => Promise<void>;  // Select org size tier
  updateDayZeroResponse: (itemId: string, response: Partial<ItemResponse>) => Promise<void>;
  setDayZeroCurrentDomain: (domain: DomainId) => void;
  completeDayZero: () => Promise<boolean>;  // Returns true if Week 1 unlocked

  // Scores actions
  updateScores: (type: "inpact" | "goals", scores: any) => Promise<void>;
  updateWeek: (week: number, data: Partial<WeekProgress>) => Promise<void>;
  updateLayer: (layer: LayerId, data: Partial<LayerStatus>) => Promise<void>;
  addRisk: (risk: Omit<Risk, "id">) => Promise<void>;
  updateRisk: (id: string, data: Partial<Risk>) => Promise<void>;
  addBudgetItem: (item: Omit<BudgetLineItem, "id">) => Promise<void>;
  setActiveTab: (tab: number) => void;
  toggleEchoBenchmark: () => void;
}

export const useTrackerStore = create<TrackerState>()(
  persist(
    (set, get) => ({
      projectId: null,
      project: null,
      dayZeroTier: "standard",  // Default to mid-size
      dayZeroResponses: {},
      dayZeroResults: null,
      dayZeroCurrentDomain: "AP",  // Start at Assessment & Planning
      inpactHistory: [],
      goalsHistory: [],
      latestInpact: null,
      latestGoals: null,
      weeks: [],
      currentWeek: 0,  // Start at Day Zero
      layers: [],
      risks: [],
      budgetItems: [],
      activeTab: 0,  // Start at Day Zero tab
      showEchoBenchmark: false,

      loadProject: async (projectId) => {
        const response = await fetch(`/api/projects/${projectId}`);
        const data = await response.json();

        set({
          projectId,
          project: data.project,
          dayZeroResponses: data.dayZeroResponses || {},
          dayZeroResults: data.dayZeroResults,
          inpactHistory: data.inpactHistory,
          goalsHistory: data.goalsHistory,
          latestInpact: data.latestInpact,
          latestGoals: data.latestGoals,
          weeks: data.weeks,
          currentWeek: data.project.currentWeek,
          layers: data.layers,
          risks: data.risks,
          budgetItems: data.budgetItems
        });
      },

      // Day Zero actions
      setDayZeroTier: async (tier) => {
        const { projectId, dayZeroResponses } = get();
        set({ dayZeroTier: tier });

        // Recalculate results with new tier
        const results = calculateDayZeroResults(dayZeroResponses, tier);
        set({ dayZeroResults: results });

        // Persist to server
        await fetch(`/api/projects/${projectId}`, {
          method: "PATCH",
          body: JSON.stringify({ dayZeroTier: tier })
        });
      },

      updateDayZeroResponse: async (itemId, response) => {
        const { projectId, dayZeroResponses, dayZeroTier } = get();

        // Optimistic update
        const updatedResponses = {
          ...dayZeroResponses,
          [itemId]: {
            ...dayZeroResponses[itemId],
            ...response,
            itemId,
            updatedAt: new Date()
          }
        };
        set({ dayZeroResponses: updatedResponses });

        // Recalculate results with current tier
        const results = calculateDayZeroResults(updatedResponses, dayZeroTier);
        set({ dayZeroResults: results });

        // Persist to server
        await fetch(`/api/projects/${projectId}/dayzero/responses`, {
          method: "POST",
          body: JSON.stringify({ itemId, ...response })
        });
      },

      setDayZeroCurrentDomain: (domain) => {
        set({ dayZeroCurrentDomain: domain });
      },

      completeDayZero: async () => {
        const { projectId, dayZeroResults } = get();

        if (!dayZeroResults || !canUnlockWeek1(dayZeroResults)) {
          return false;
        }

        await fetch(`/api/projects/${projectId}/dayzero/complete`, {
          method: "POST"
        });

        // Refresh to get updated project state
        await get().loadProject(projectId!);
        return true;
      },

      updateScores: async (type, scores) => {
        const { projectId, currentWeek } = get();
        await fetch(`/api/projects/${projectId}/scores`, {
          method: "POST",
          body: JSON.stringify({ type, week: currentWeek, scores })
        });
        // Refresh data
        await get().loadProject(projectId!);
      },

      updateWeek: async (week, data) => {
        const { projectId } = get();
        await fetch(`/api/projects/${projectId}/weeks/${week}`, {
          method: "PATCH",
          body: JSON.stringify(data)
        });
        // Refresh
        await get().loadProject(projectId!);
      },

      updateLayer: async (layer, data) => {
        const { projectId } = get();
        await fetch(`/api/projects/${projectId}/layers/${layer}`, {
          method: "PATCH",
          body: JSON.stringify(data)
        });
        await get().loadProject(projectId!);
      },

      addRisk: async (risk) => {
        const { projectId } = get();
        await fetch(`/api/projects/${projectId}/risks`, {
          method: "POST",
          body: JSON.stringify(risk)
        });
        await get().loadProject(projectId!);
      },

      updateRisk: async (id, data) => {
        const { projectId } = get();
        await fetch(`/api/projects/${projectId}/risks/${id}`, {
          method: "PATCH",
          body: JSON.stringify(data)
        });
        await get().loadProject(projectId!);
      },

      addBudgetItem: async (item) => {
        const { projectId } = get();
        await fetch(`/api/projects/${projectId}/budget`, {
          method: "POST",
          body: JSON.stringify(item)
        });
        await get().loadProject(projectId!);
      },

      setActiveTab: (tab) => set({ activeTab: tab }),

      toggleEchoBenchmark: () =>
        set((state) => ({ showEchoBenchmark: !state.showEchoBenchmark }))
    }),
    {
      name: "tracker-state",
      partialize: (state) => ({
        projectId: state.projectId,
        activeTab: state.activeTab,
        showEchoBenchmark: state.showEchoBenchmark
      })
    }
  )
);
```

---

## File Structure Summary

```
90day-tracker/
├── app/
│   ├── page.tsx                     # Landing page
│   ├── tracker/
│   │   ├── page.tsx                 # Lead capture + setup
│   │   └── [projectId]/
│   │       └── page.tsx             # Dashboard (8 tabs: Day Zero + 7 others)
│   ├── api/
│   │   └── projects/
│   │       ├── route.ts             # Create/list projects
│   │       └── [id]/
│   │           ├── route.ts         # Get/update/delete project
│   │           ├── dayzero/         # Day Zero endpoints ⭐
│   │           │   ├── route.ts     # Get Day Zero state
│   │           │   ├── responses/route.ts
│   │           │   ├── results/route.ts
│   │           │   ├── complete/route.ts
│   │           │   └── export/
│   │           │       ├── pdf/route.ts
│   │           │       └── xlsx/route.ts
│   │           ├── scores/route.ts  # Score entries
│   │           ├── weeks/[week]/route.ts
│   │           ├── layers/[layer]/route.ts
│   │           ├── risks/route.ts
│   │           ├── communications/route.ts
│   │           ├── budget/route.ts
│   │           └── export/
│   │               ├── xlsx/route.ts
│   │               └── pdf/route.ts
├── components/
│   ├── dashboard/                   # Layout + tabs (8 tabs)
│   ├── dayzero/                     # Day Zero components ⭐
│   │   ├── ChecklistLayout.tsx
│   │   ├── DomainNav.tsx
│   │   ├── DomainPanel.tsx
│   │   ├── ProgressPanel.tsx
│   │   ├── ChecklistItem.tsx
│   │   ├── EvidenceChecklist.tsx
│   │   ├── StatusSelector.tsx
│   │   ├── VerdictCard.tsx
│   │   └── UnlockWeek1Button.tsx
│   ├── charts/                      # Visualizations
│   ├── forms/                       # Input modals
│   ├── tables/                      # Data tables
│   ├── cards/                       # Summary cards
│   └── ui/                          # Shared UI
├── lib/
│   ├── store/
│   │   └── trackerStore.ts          # Includes Day Zero state
│   ├── algorithms/
│   │   ├── dayzero-scoring.ts       # Day Zero scoring ⭐
│   │   └── inpact-scoring.ts
│   ├── db/
│   │   └── prisma.ts
│   └── export/
│       ├── xlsx.ts
│       └── pdf.ts
├── data/
│   └── checklistItems.ts            # All 50 Day Zero items ⭐
├── types/
│   ├── project.ts
│   ├── dayzero.ts                   # Day Zero types ⭐
│   ├── scores.ts
│   ├── weekly.ts
│   ├── layers.ts
│   ├── risks.ts
│   ├── communications.ts
│   └── budget.ts
└── prisma/
    └── schema.prisma
```

---

## Quick Start for AI Coding Tools

```markdown
## Instructions for Claude Code / Cursor / Windsurf

1. **Create Next.js app:**
   ```bash
   npx create-next-app@latest 90day-tracker --typescript --tailwind --app
   cd 90day-tracker
   npm install zustand recharts @tanstack/react-table react-hook-form zod
   npm install framer-motion date-fns xlsx @react-pdf/renderer
   npm install @prisma/client
   npm install -D prisma
   ```

2. **Set up database:**
   - Copy schema to `prisma/schema.prisma`
   - Run `npx prisma migrate dev`

3. **Create types:**
   - Copy all interfaces from "Data Models" to `types/`
   - Include Day Zero types (DayZeroResults, ItemResponse, etc.)

4. **Create Day Zero checklist data:**
   - Copy all 35 items from Tab 0 specification (15 Essential + 10 Standard + 10 Comprehensive)
   - Structure into CHECKLIST_ITEMS array with domains and tiers
   - Mark critical items (isCritical: true)
   - Include Chapter 10 references and data field definitions

5. **Implement Day Zero scoring:**
   - Copy calculateDayZeroResults function (tier-aware)
   - Implement getItemsForTier function for cumulative tier logic
   - Implement verdict logic with critical blocker check
   - Add canUnlockWeek1 gate check
   - Calculate recommendedTimeline based on tier

6. **Build Day Zero UI (Tab 0):**
   - TierSelector with three organization size options
   - ChecklistLayout with three-panel layout
   - DomainNav with 6 domains + progress indicators (items filtered by tier)
   - ChecklistItem with tier badge, collapsible evidence sections, data fields
   - StatusSelector with 4 options (Ready/In Progress/Not Ready/N/A)
   - VerdictCard with gate status, timeline recommendation, and "Proceed to Week 1" button

7. **Create Echo benchmark data:**
   - Add ECHO_BASELINE and ECHO_FINAL constants
   - Include week-by-week progression data

8. **Build charts:**
   - INPACTRadar with Recharts
   - GOALSBar with horizontal bars
   - ArchitectureDiagram with Framer Motion

9. **Build dashboard tabs (Tabs 1-7):**
   - WeeklyProgress with WeekCard grid (locked until Day Zero complete)
   - InpactTracker with radar + dimension cards
   - GoalsTracker with bars + dimension cards
   - LayerStatus with architecture diagram
   - RiskLog with TanStack Table
   - CommunicationLog with table + calendar
   - BudgetTracker with summary cards + table

10. **Implement state:**
    - Copy Zustand store to `lib/store/`
    - Include Day Zero state and actions
    - Connect to API endpoints

11. **Add export:**
    - Excel export with SheetJS
    - PDF report with @react-pdf/renderer

12. **Test the complete flow:**
    - Create project → Select Day Zero tier (Essential/Standard/Comprehensive) →
      Complete Day Zero (15/25/35 items) → Unlock Week 1 →
      Setup INPACT/GOALS baseline → Update weekly → View charts → Export
```