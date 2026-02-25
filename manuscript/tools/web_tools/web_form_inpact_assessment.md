# INPACT Assessment  - Web Form Specification

## Overview

**URL:** trustbeforeintelligence.ai/assessment
**Purpose:** Structured 36-question assessment with PDF report generation
**Lead Capture:** Email required before viewing results

---

## User Flow

### Step 1: Landing Page
- Value proposition: "Discover your AI agent readiness score in 15 minutes"
- Brief explanation of INPACT (6 dimensions)
- Echo Health benchmark teaser: "See how you compare to a healthcare org that went from 28% to 89% in 90 days"
- **CTA Button:** "Start Assessment"

### Step 2: Lead Capture (Before Assessment)
Required fields:
- Email (required)
- Name (required)
- Organization (required)
- Role (required)
- Industry (dropdown: Healthcare, Financial Services, Manufacturing, Retail, Technology, Other)

Optional fields:
- Company size (dropdown: 1-50, 51-200, 201-1000, 1000+)
- Planned use cases (checkboxes: Scheduling, Documentation, Customer Service, Data Analysis, Other)

### Step 3: Assessment Interface

**Layout:** One dimension per page (6 pages total)

**For each dimension page:**
- Dimension name and description (e.g., "I  - Instant: Sub-second response times")
- 6 questions displayed as cards
- Each question has:
  - Question text
  - 6-point scale (radio buttons or slider)
  - Score descriptions visible on hover/click
  - "Evidence notes" text field (optional but encouraged)
- Progress bar showing dimension progress (1/6, 2/6, etc.)
- "Next Dimension" button (disabled until all 6 answered)

**Navigation:**
- Progress indicator: "Dimension 2 of 6: Natural"
- Back button to revisit previous dimensions
- Save progress (tied to email)  - users can resume later

### Step 4: Results Page

**Immediate display (before PDF):**
- Overall score: X/36 (XX%)
- Trust Band classification with color coding:
  - Green: High Trust (86-100%)
  - Blue: Good Trust (67-85%)
  - Yellow: Moderate Trust (50-66%)
  - Orange: Low Trust (33-49%)
  - Red: Very Low Trust (<33%)
- Radar chart showing 6 dimensions
- Comparison to Echo Health baseline

**CTA:** "Download Full Report (PDF)"

### Step 5: PDF Report

**Report contents:**
1. Cover page with organization name, date, overall score
2. Executive summary (1 page)
   - Overall score and Trust Band
   - Top 2 strengths
   - Top 2 priority gaps
   - Recommended next steps
3. Dimension breakdown (6 pages, 1 per dimension)
   - Dimension score (X/6)
   - Individual question scores
   - Evidence notes (if provided)
   - Specific recommendations per dimension
4. Echo Health comparison (1 page)
   - Side-by-side radar chart
   - "Echo started at 28% and reached 89% in 90 days"
5. Next steps (1 page)
   - Link to Stack Builder tool
   - Link to book chapters by gap area
   - Consultation CTA

**PDF footer:**
```
From "Trust Before Intelligence" by Ram Katamaraja
```

---

## Scoring Logic

### Per Question
- Score range: 1-6
- No weighting (all questions equal)

### Per Dimension
- Average of 6 questions = 1-6 (dimension score)
- Dimension percentage: (dimension score / 6) × 100
- Example: Questions score [4, 5, 3, 4, 5, 3] → 24/6 = 4.0 → 67%

### Overall Score (Book-Consistent 6-36 System)
- Sum of 6 dimension scores = 6-36 points
- **Overall percentage: (total / 36) × 100**
- Example: Dimension scores [4, 5, 3, 4, 3, 5] = 24 → 24/36 × 100 = **67%**

**Display:** The primary display should be the **percentage** (e.g., "Your INPACT Score: 67%"). The 6-36 point value is secondary/optional.

### Trust Bands
| Band | Percentage | Score Range |
|------|------------|-------------|
| High Trust | 86-100% | 31-36 |
| Good Trust | 67-85% | 24-30 |
| Moderate Trust | 50-66% | 18-23 |
| Low Trust | 33-49% | 12-17 |
| Very Low Trust | <33% | 6-11 |

---

## Technical Requirements

### Frontend
- Responsive design (mobile-friendly)
- Progress auto-save (localStorage + server)
- Accessible (WCAG 2.1 AA)
- Form validation

### Backend
- Store assessment responses
- Generate PDF on demand
- Email delivery of PDF
- Analytics tracking

### Integrations
- Email marketing (for follow-up sequence)
- CRM (lead capture)
- Analytics (conversion tracking)

---

## Follow-up Email Sequence

| Day | Email | Content |
|-----|-------|---------|
| 0 | Results delivered | PDF attachment + key findings summary |
| 3 | How to interpret | Deep dive on their lowest dimension |
| 7 | Chapter excerpt | Relevant chapter based on gaps |
| 14 | Echo case study | Full transformation story |
| 30 | Consultation offer | "Ready to start your 90-day journey?" |

---

## Content Files Needed

The web form uses the same knowledge bases as the GPT:
1. `kb_INPACT_assessment_36_questions.md`  - Question text and scoring criteria
2. `kb_INPACT_scoring_rubrics.md`  - Trust bands and interpretation

---

## Design Notes

### Brand Colors
- Primary: Teal (from book cover)
- Secondary: White, Dark Gray
- Trust Band colors: Green, Blue, Yellow, Orange, Red

### Radar Chart
- 6 axes (I, N, P, A, C, T)
- User score in teal
- Echo baseline in gray (dashed line)
- Echo final in green (for comparison)

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | January 2026 | Initial specification |
| 2.0 | January 2026 | Added Technical Implementation Guide for AI-assisted development |

---

# PART 2: TECHNICAL IMPLEMENTATION GUIDE

> **For AI-Assisted Development (Claude Code, Cursor, Windsurf, etc.)**
>
> This section provides the technical specifications needed to build the INPACT Assessment tool. It includes data models, API endpoints, component architecture, scoring algorithms, and chart generation.

---

## Technology Stack (Recommended)

```
Frontend:
- Framework: Next.js 14+ (App Router) or React 18+
- State Management: Zustand or React Context
- Styling: Tailwind CSS
- Charts: Recharts (radar chart) or Chart.js
- Animation: Framer Motion
- Form Handling: React Hook Form + Zod

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

### 1. Dimension & Question Definitions (Static Data)

```typescript
// types/assessment.ts

type DimensionId = "I" | "N" | "P" | "A" | "C" | "T";

interface Dimension {
  id: DimensionId;
  name: string;
  fullName: string;
  description: string;
  color: string;              // For charts
  questions: Question[];
}

interface Question {
  id: string;                 // e.g., "I-1", "N-3"
  dimensionId: DimensionId;
  questionNumber: number;     // 1-6 within dimension
  title: string;              // Short title
  question: string;           // Full question text
  scoringCriteria: ScoringCriteria[];
  evidenceSources: string[];
  echoBaseline: {
    score: number;
    note: string;
  };
}

interface ScoringCriteria {
  score: number;              // 1-6
  label: string;              // "Excellent", "Strong", etc.
  criteria: string;           // Detailed criteria text
  deploymentReadiness: string;
}

// Scoring labels (shared across all questions)
const SCORE_LABELS: Record<number, string> = {
  6: "Excellent",
  5: "Strong",
  4: "Functional",
  3: "Moderate",
  2: "Significant Gap",
  1: "Critical Gap"
};

const DEPLOYMENT_READINESS: Record<number, string> = {
  6: "Production + competitive advantage",
  5: "Deploy with confidence",
  4: "Deploy with monitoring",
  3: "Pilot only",
  2: "Not deployment-ready",
  1: "Immediate remediation"
};
```

### 2. Trust Bands

```typescript
// types/trustBands.ts

interface TrustBand {
  id: string;
  name: string;
  minPercentage: number;
  maxPercentage: number;
  minScore: number;           // INPACT score (6-36)
  maxScore: number;
  color: string;
  bgColor: string;
  description: string;
  recommendations: string[];
}

const TRUST_BANDS: TrustBand[] = [
  {
    id: "high",
    name: "High Trust",
    minPercentage: 86,
    maxPercentage: 100,
    minScore: 31,             // 6-36 scale (86% of 36 ≈ 31)
    maxScore: 36,
    color: "#22c55e",         // green-500
    bgColor: "#dcfce7",       // green-100
    description: "Production-ready with competitive advantage",
    recommendations: [
      "Focus on optimization and innovation",
      "Share learnings with industry peers",
      "Consider advanced use cases"
    ]
  },
  {
    id: "good",
    name: "Good Trust",
    minPercentage: 67,
    maxPercentage: 85,
    minScore: 24,             // 6-36 scale (67% of 36 ≈ 24)
    maxScore: 30,
    color: "#3b82f6",         // blue-500
    bgColor: "#dbeafe",       // blue-100
    description: "Deploy with targeted improvements",
    recommendations: [
      "Address remaining gaps in priority order",
      "Implement comprehensive monitoring",
      "Plan for production scaling"
    ]
  },
  {
    id: "moderate",
    name: "Moderate Trust",
    minPercentage: 50,
    maxPercentage: 66,
    minScore: 18,             // 6-36 scale (50% of 36 = 18)
    maxScore: 23,
    color: "#eab308",         // yellow-500
    bgColor: "#fef9c3",       // yellow-100
    description: "Pilot-ready with significant investment needed",
    recommendations: [
      "Focus on critical gaps first",
      "Build foundation layers before intelligence",
      "Plan 60-90 day improvement sprint"
    ]
  },
  {
    id: "low",
    name: "Low Trust",
    minPercentage: 33,
    maxPercentage: 49,
    minScore: 12,             // 6-36 scale (33% of 36 ≈ 12)
    maxScore: 17,
    color: "#f97316",         // orange-500
    bgColor: "#ffedd5",       // orange-100
    description: "Not deployment-ready, major transformation required",
    recommendations: [
      "Conduct comprehensive infrastructure audit",
      "Secure executive sponsorship for transformation",
      "Plan 90-day foundational sprint"
    ]
  },
  {
    id: "very-low",
    name: "Very Low Trust",
    minPercentage: 0,
    maxPercentage: 32,
    minScore: 6,              // 6-36 scale (minimum possible)
    maxScore: 11,
    color: "#ef4444",         // red-500
    bgColor: "#fee2e2",       // red-100
    description: "Critical gaps requiring immediate attention",
    recommendations: [
      "Pause agent initiatives until foundation is built",
      "Engage with experienced implementation partner",
      "Focus on basic data infrastructure first"
    ]
  }
];
```

### 3. User Session & Response State

```typescript
// types/session.ts

interface AssessmentSession {
  id: string;
  createdAt: Date;
  updatedAt: Date;
  completedAt: Date | null;

  // Lead info
  lead: {
    email: string;
    name: string;
    organization: string;
    role: string;
    industry: Industry;
    companySize?: CompanySize;
    useCases?: string[];
  };

  // Assessment state
  currentDimension: DimensionId;
  currentQuestion: number;      // 1-6

  // Responses
  responses: Record<string, QuestionResponse>;

  // Computed (cached after completion)
  results?: AssessmentResults;
}

interface QuestionResponse {
  questionId: string;           // e.g., "I-1"
  score: number;                // 1-6
  evidenceNotes?: string;
  answeredAt: Date;
}

interface AssessmentResults {
  // Dimension scores
  dimensionScores: Record<DimensionId, DimensionScore>;

  // Overall
  totalScore: number;           // 6-36 (sum of 6 normalized dimension scores, each 1-6)
  percentageScore: number;      // 0-100 ((totalScore/36) × 100)
  trustBand: TrustBand;

  // Analysis
  strengths: DimensionId[];     // Top 2
  gaps: DimensionId[];          // Bottom 2
  criticalGaps: string[];       // Questions with score 1

  // Recommendations
  priorityPhase: string;        // "Phase 1", "Phase 2", etc.
  recommendedChapters: number[];
}

interface DimensionScore {
  dimensionId: DimensionId;
  score: number;                // 1-6 (average of 6 questions, normalized)
  percentageScore: number;      // 0-100 for display ((score/6) × 100)
  questionScores: { questionId: string; score: number }[];
}

type Industry = "healthcare" | "financial" | "manufacturing" | "retail" | "technology" | "government" | "other";
type CompanySize = "1-50" | "51-200" | "201-1000" | "1000+";
```

### 4. Echo Health Benchmark Data

```typescript
// data/echoBenchmark.ts

interface EchoBenchmark {
  week: number;
  totalScore: number;
  percentageScore: number;
  dimensionScores: Record<DimensionId, number>;
  trustBand: string;
  milestone: string;
}

const ECHO_BENCHMARKS: EchoBenchmark[] = [
  {
    week: 0,
    totalScore: 60,
    percentageScore: 28,
    dimensionScores: { I: 8, N: 13, P: 8, A: 9, C: 15, T: 7 },
    trustBand: "very-low",
    milestone: "Initial Assessment"
  },
  {
    week: 4,
    totalScore: 90,
    percentageScore: 42,
    dimensionScores: { I: 18, N: 15, P: 12, A: 12, C: 20, T: 13 },
    trustBand: "low",
    milestone: "Foundation Complete"
  },
  {
    week: 7,
    totalScore: 144,
    percentageScore: 67,
    dimensionScores: { I: 26, N: 24, P: 22, A: 20, C: 28, T: 24 },
    trustBand: "good",
    milestone: "Intelligence Operational"
  },
  {
    week: 10,
    totalScore: 186,
    percentageScore: 86,
    dimensionScores: { I: 32, N: 30, P: 32, A: 28, C: 34, T: 30 },
    trustBand: "high",
    milestone: "Trust Established"
  },
  {
    week: 12,
    totalScore: 192,
    percentageScore: 89,
    dimensionScores: { I: 34, N: 32, P: 33, A: 30, C: 34, T: 29 },
    trustBand: "high",
    milestone: "Production Launch"
  }
];
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
  role VARCHAR(255) NOT NULL,
  industry VARCHAR(50) NOT NULL,
  company_size VARCHAR(20),
  use_cases TEXT[],
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Assessment sessions
CREATE TABLE assessment_sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  lead_id UUID REFERENCES leads(id),

  -- Progress
  current_dimension CHAR(1) DEFAULT 'I',
  current_question INTEGER DEFAULT 1,

  -- Status
  started_at TIMESTAMP DEFAULT NOW(),
  completed_at TIMESTAMP,

  -- Results (computed and cached)
  total_score DECIMAL(3,1),      -- 6-36 (sum of 6 normalized dimension scores)
  percentage_score DECIMAL(5,2), -- 0-100%
  trust_band VARCHAR(20),
  results_json JSONB,

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Individual question responses
CREATE TABLE question_responses (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id UUID REFERENCES assessment_sessions(id) ON DELETE CASCADE,
  question_id VARCHAR(10) NOT NULL,   -- e.g., "I-1", "N-3"
  dimension_id CHAR(1) NOT NULL,
  score INTEGER NOT NULL CHECK (score >= 1 AND score <= 6),
  evidence_notes TEXT,
  answered_at TIMESTAMP DEFAULT NOW(),

  UNIQUE(session_id, question_id)
);

-- Indexes
CREATE INDEX idx_sessions_lead ON assessment_sessions(lead_id);
CREATE INDEX idx_sessions_completed ON assessment_sessions(completed_at);
CREATE INDEX idx_responses_session ON question_responses(session_id);
CREATE INDEX idx_responses_dimension ON question_responses(session_id, dimension_id);
```

---

## API Endpoints

```typescript
// Next.js App Router API Routes

// POST /api/assessments - Start new assessment
interface CreateAssessmentRequest {
  lead: {
    email: string;
    name: string;
    organization: string;
    role: string;
    industry: Industry;
    companySize?: CompanySize;
    useCases?: string[];
  };
}

interface CreateAssessmentResponse {
  sessionId: string;
  resumeUrl: string;
}

// GET /api/assessments/:id - Get session state
interface GetAssessmentResponse {
  session: AssessmentSession;
  currentQuestion: Question;
  progress: {
    completedQuestions: number;
    totalQuestions: 36;
    currentDimension: DimensionId;
    completedDimensions: DimensionId[];
  };
}

// POST /api/assessments/:id/responses - Submit response
interface SubmitResponseRequest {
  questionId: string;
  score: number;
  evidenceNotes?: string;
}

interface SubmitResponseResponse {
  saved: boolean;
  nextQuestion: Question | null;
  isComplete: boolean;
  progress: {
    completedQuestions: number;
    currentDimension: DimensionId;
  };
}

// GET /api/assessments/:id/results - Get computed results
interface GetResultsResponse {
  results: AssessmentResults;
  echoBenchmark: EchoBenchmark;  // Week 0 comparison
  radarChartData: RadarChartData;
}

// POST /api/assessments/:id/report - Generate PDF
interface GenerateReportRequest {
  format: "pdf" | "summary";
}

interface GenerateReportResponse {
  downloadUrl: string;
  expiresAt: Date;
}

// Resume session by email
// GET /api/assessments/resume?email=xxx
interface ResumeAssessmentResponse {
  sessions: {
    id: string;
    organization: string;
    progress: number;  // percentage
    lastUpdated: Date;
    isComplete: boolean;
  }[];
}
```

---

## Core Algorithms

### 1. Score Calculation

```typescript
// lib/algorithms/scoring.ts

function calculateResults(
  responses: Record<string, QuestionResponse>
): AssessmentResults {
  const dimensions: DimensionId[] = ["I", "N", "P", "A", "C", "T"];

  // Calculate dimension scores
  const dimensionScores: Record<DimensionId, DimensionScore> = {};

  for (const dim of dimensions) {
    const dimResponses = Object.values(responses).filter(
      r => r.questionId.startsWith(dim)
    );

    const questionSum = dimResponses.reduce((sum, r) => sum + r.score, 0);
    const dimensionScore = questionSum / 6;  // Normalized 1-6

    dimensionScores[dim] = {
      dimensionId: dim,
      score: Math.round(dimensionScore * 10) / 10,  // 1-6 (normalized)
      percentageScore: Math.round((dimensionScore / 6) * 100),  // 0-100%
      questionScores: dimResponses.map(r => ({
        questionId: r.questionId,
        score: r.score
      }))
    };
  }

  // Calculate total INPACT score (sum of 6 dimension scores, each 1-6)
  const totalScore = Object.values(dimensionScores).reduce(
    (sum, d) => sum + d.score,
    0
  );

  // Normalize to 0-100 percentage
  // Formula: (totalScore / 36) × 100
  const percentageScore = Math.round((totalScore / 36) * 100);

  // Determine trust band
  const trustBand = getTrustBand(percentageScore);

  // Identify strengths (top 2) and gaps (bottom 2)
  const sortedDimensions = [...dimensions].sort(
    (a, b) => dimensionScores[b].score - dimensionScores[a].score
  );

  const strengths = sortedDimensions.slice(0, 2);
  const gaps = sortedDimensions.slice(-2).reverse();

  // Find critical gaps (any question with score 1)
  const criticalGaps = Object.values(responses)
    .filter(r => r.score === 1)
    .map(r => r.questionId);

  // Determine priority phase based on lowest dimension
  const lowestDimension = sortedDimensions[sortedDimensions.length - 1];
  const priorityPhase = getPriorityPhase(lowestDimension);

  // Recommend chapters based on gaps
  const recommendedChapters = getRecommendedChapters(gaps, criticalGaps);

  return {
    dimensionScores,
    totalScore,  // 6-36 (sum of 6 normalized dimension scores)
    percentageScore,
    trustBand,
    strengths,
    gaps,
    criticalGaps,
    priorityPhase,
    recommendedChapters
  };
}

function getTrustBand(percentageScore: number): TrustBand {
  return TRUST_BANDS.find(
    band =>
      percentageScore >= band.minPercentage &&
      percentageScore <= band.maxPercentage
  ) || TRUST_BANDS[TRUST_BANDS.length - 1];
}

function getPriorityPhase(lowestDimension: DimensionId): string {
  const phaseMapping: Record<DimensionId, string> = {
    I: "Phase 1: Foundation (Weeks 1-4)",
    C: "Phase 1-2: Foundation & Intelligence (Weeks 1-7)",
    N: "Phase 2: Intelligence (Weeks 5-7)",
    P: "Phase 3: Trust (Weeks 8-10)",
    T: "Phase 3: Trust (Weeks 8-10)",
    A: "Phase 3-4: Trust & Operations (Weeks 8-12)"
  };
  return phaseMapping[lowestDimension];
}

function getRecommendedChapters(
  gaps: DimensionId[],
  criticalGaps: string[]
): number[] {
  const chapterMapping: Record<DimensionId, number[]> = {
    I: [3, 4],     // Storage & Real-Time
    N: [5, 6],     // Semantic & Intelligence
    P: [7],        // Governance
    A: [6, 8],     // Intelligence & Observability
    C: [3, 4, 5],  // Storage, Real-Time, Semantic
    T: [7, 8]      // Governance & Observability
  };

  const chapters = new Set<number>();

  // Add chapters for gap dimensions
  for (const dim of gaps) {
    chapterMapping[dim].forEach(ch => chapters.add(ch));
  }

  // Always include Chapter 10 (Implementation)
  chapters.add(10);

  return [...chapters].sort((a, b) => a - b);
}
```

### 2. Radar Chart Data Generation

```typescript
// lib/algorithms/charts.ts

interface RadarChartData {
  labels: string[];
  datasets: {
    label: string;
    data: number[];
    backgroundColor: string;
    borderColor: string;
    borderWidth: number;
  }[];
}

function generateRadarChartData(
  userScores: Record<DimensionId, DimensionScore>,
  includeEchoBenchmark: boolean = true
): RadarChartData {
  const dimensions: DimensionId[] = ["I", "N", "P", "A", "C", "T"];
  const dimensionNames = {
    I: "Instant",
    N: "Natural",
    P: "Permitted",
    A: "Adaptive",
    C: "Contextual",
    T: "Transparent"
  };

  const labels = dimensions.map(d => dimensionNames[d]);

  // User scores (normalized to 0-100)
  const userData = dimensions.map(d => userScores[d].percentageScore);

  const datasets: RadarChartData["datasets"] = [
    {
      label: "Your Score",
      data: userData,
      backgroundColor: "rgba(20, 184, 166, 0.2)",  // teal
      borderColor: "rgb(20, 184, 166)",
      borderWidth: 2
    }
  ];

  if (includeEchoBenchmark) {
    // Echo Week 0 (baseline) - dimension scores are 1-6, convert to percentage
    const echoWeek0 = ECHO_BENCHMARKS[0];
    const echoBaselineData = dimensions.map(
      d => Math.round((echoWeek0.dimensionScores[d] / 6) * 100)
    );

    datasets.push({
      label: "Echo Health (Week 0)",
      data: echoBaselineData,
      backgroundColor: "rgba(156, 163, 175, 0.1)",  // gray
      borderColor: "rgb(156, 163, 175)",
      borderWidth: 1
    });

    // Echo Week 12 (final) - dimension scores are 1-6, convert to percentage
    const echoWeek12 = ECHO_BENCHMARKS[ECHO_BENCHMARKS.length - 1];
    const echoFinalData = dimensions.map(
      d => Math.round((echoWeek12.dimensionScores[d] / 6) * 100)
    );

    datasets.push({
      label: "Echo Health (Week 12)",
      data: echoFinalData,
      backgroundColor: "rgba(34, 197, 94, 0.1)",  // green
      borderColor: "rgb(34, 197, 94)",
      borderWidth: 1
    });
  }

  return { labels, datasets };
}
```

### 3. Progress Tracking

```typescript
// lib/algorithms/progress.ts

interface ProgressState {
  completedQuestions: number;
  totalQuestions: 36;
  percentComplete: number;
  currentDimension: DimensionId;
  currentQuestionNumber: number;
  completedDimensions: DimensionId[];
  remainingDimensions: DimensionId[];
}

function calculateProgress(
  responses: Record<string, QuestionResponse>,
  currentDimension: DimensionId,
  currentQuestion: number
): ProgressState {
  const dimensions: DimensionId[] = ["I", "N", "P", "A", "C", "T"];

  const completedQuestions = Object.keys(responses).length;
  const percentComplete = Math.round((completedQuestions / 36) * 100);

  const completedDimensions: DimensionId[] = [];
  const remainingDimensions: DimensionId[] = [];

  for (const dim of dimensions) {
    const dimResponses = Object.keys(responses).filter(id =>
      id.startsWith(dim)
    );
    if (dimResponses.length === 6) {
      completedDimensions.push(dim);
    } else {
      remainingDimensions.push(dim);
    }
  }

  return {
    completedQuestions,
    totalQuestions: 36,
    percentComplete,
    currentDimension,
    currentQuestionNumber: currentQuestion,
    completedDimensions,
    remainingDimensions
  };
}

function getNextQuestion(
  responses: Record<string, QuestionResponse>,
  currentDimension: DimensionId,
  currentQuestion: number
): { dimension: DimensionId; question: number } | null {
  const dimensions: DimensionId[] = ["I", "N", "P", "A", "C", "T"];

  // Find next unanswered question
  for (let dimIndex = dimensions.indexOf(currentDimension); dimIndex < 6; dimIndex++) {
    const dim = dimensions[dimIndex];
    const startQ = dim === currentDimension ? currentQuestion : 1;

    for (let q = startQ; q <= 6; q++) {
      const questionId = `${dim}-${q}`;
      if (!responses[questionId]) {
        return { dimension: dim, question: q };
      }
    }
  }

  return null; // Assessment complete
}
```

---

## React Components

### 1. Component Structure

```
components/
├── assessment/
│   ├── AssessmentFlow.tsx        # Main container
│   ├── LandingPage.tsx           # Step 1
│   ├── LeadCapture.tsx           # Step 2
│   ├── DimensionAssessment.tsx   # Step 3 (main)
│   │   ├── DimensionHeader.tsx   # Dimension title + description
│   │   ├── QuestionCard.tsx      # Single question
│   │   ├── ScoreSelector.tsx     # 1-6 scale selection
│   │   ├── EvidenceNotes.tsx     # Optional notes field
│   │   └── NavigationButtons.tsx
│   ├── ProgressBar.tsx           # Overall + dimension progress
│   ├── ResultsPage.tsx           # Step 4
│   │   ├── ScoreSummary.tsx      # Overall score + trust band
│   │   ├── RadarChart.tsx        # 6-dimension chart
│   │   ├── DimensionBreakdown.tsx
│   │   ├── EchoComparison.tsx
│   │   └── RecommendationsPanel.tsx
│   └── hooks/
│       ├── useAssessment.ts      # Assessment state
│       ├── useProgress.ts        # Progress tracking
│       └── useResults.ts         # Results computation
├── charts/
│   └── RadarChart.tsx            # Recharts radar
├── pdf/
│   └── AssessmentReport.tsx      # PDF template
└── ui/
    ├── Button.tsx
    ├── Card.tsx
    ├── ProgressBar.tsx
    ├── Badge.tsx
    └── RadioGroup.tsx
```

### 2. Main Assessment Flow Component

```tsx
// components/assessment/AssessmentFlow.tsx

"use client";

import { useState, useEffect } from "react";
import { useRouter } from "next/navigation";
import { useAssessmentStore } from "@/lib/store/assessmentStore";
import { LandingPage } from "./LandingPage";
import { LeadCapture } from "./LeadCapture";
import { DimensionAssessment } from "./DimensionAssessment";
import { ResultsPage } from "./ResultsPage";
import { ProgressBar } from "./ProgressBar";

type Step = "landing" | "lead" | "assessment" | "results";

interface Props {
  sessionId?: string;  // For resuming
}

export function AssessmentFlow({ sessionId }: Props) {
  const router = useRouter();
  const {
    session,
    currentStep,
    setStep,
    loadSession,
    isComplete
  } = useAssessmentStore();

  useEffect(() => {
    if (sessionId) {
      loadSession(sessionId);
    }
  }, [sessionId]);

  const handleLeadSubmit = async (lead: Lead) => {
    const newSessionId = await createSession(lead);
    router.push(`/assessment/${newSessionId}`);
    setStep("assessment");
  };

  const handleAssessmentComplete = () => {
    setStep("results");
  };

  return (
    <div className="min-h-screen bg-gray-50">
      {/* Progress bar (shown during assessment) */}
      {currentStep === "assessment" && session && (
        <ProgressBar session={session} />
      )}

      {/* Step content */}
      <main className="max-w-4xl mx-auto px-4 py-8">
        {currentStep === "landing" && (
          <LandingPage onStart={() => setStep("lead")} />
        )}

        {currentStep === "lead" && (
          <LeadCapture onSubmit={handleLeadSubmit} />
        )}

        {currentStep === "assessment" && session && (
          <DimensionAssessment
            session={session}
            onComplete={handleAssessmentComplete}
          />
        )}

        {currentStep === "results" && session && (
          <ResultsPage session={session} />
        )}
      </main>
    </div>
  );
}
```

### 3. Question Card Component

```tsx
// components/assessment/QuestionCard.tsx

import { useState } from "react";
import { motion } from "framer-motion";
import { ScoreSelector } from "./ScoreSelector";
import { EvidenceNotes } from "./EvidenceNotes";
import { Question } from "@/types/assessment";

interface Props {
  question: Question;
  currentScore?: number;
  currentNotes?: string;
  onSubmit: (score: number, notes?: string) => void;
  isLast: boolean;
}

export function QuestionCard({
  question,
  currentScore,
  currentNotes,
  onSubmit,
  isLast
}: Props) {
  const [score, setScore] = useState<number | null>(currentScore || null);
  const [notes, setNotes] = useState(currentNotes || "");
  const [showCriteria, setShowCriteria] = useState(false);

  const handleSubmit = () => {
    if (score !== null) {
      onSubmit(score, notes || undefined);
    }
  };

  return (
    <motion.div
      className="bg-white rounded-xl shadow-lg p-6"
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      exit={{ opacity: 0, y: -20 }}
    >
      {/* Question header */}
      <div className="mb-6">
        <div className="flex items-center gap-2 text-sm text-gray-500 mb-2">
          <span className="font-mono bg-gray-100 px-2 py-0.5 rounded">
            {question.id}
          </span>
          <span>{question.title}</span>
        </div>
        <h2 className="text-xl font-semibold text-gray-900">
          {question.question}
        </h2>
      </div>

      {/* Score selector */}
      <div className="mb-6">
        <ScoreSelector
          value={score}
          onChange={setScore}
          criteria={question.scoringCriteria}
        />
      </div>

      {/* Scoring criteria (expandable) */}
      <div className="mb-6">
        <button
          className="text-sm text-teal-600 hover:text-teal-700 flex items-center gap-1"
          onClick={() => setShowCriteria(!showCriteria)}
        >
          {showCriteria ? "Hide" : "Show"} scoring criteria
          <svg
            className={`w-4 h-4 transition-transform ${
              showCriteria ? "rotate-180" : ""
            }`}
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

        {showCriteria && (
          <motion.div
            className="mt-3 bg-gray-50 rounded-lg p-4"
            initial={{ opacity: 0, height: 0 }}
            animate={{ opacity: 1, height: "auto" }}
          >
            <table className="w-full text-sm">
              <thead>
                <tr className="text-left text-gray-500">
                  <th className="pb-2 w-16">Score</th>
                  <th className="pb-2">Criteria</th>
                </tr>
              </thead>
              <tbody>
                {question.scoringCriteria.map((c) => (
                  <tr
                    key={c.score}
                    className={`border-t ${
                      score === c.score ? "bg-teal-50" : ""
                    }`}
                  >
                    <td className="py-2 font-mono font-bold">{c.score}</td>
                    <td className="py-2">{c.criteria}</td>
                  </tr>
                ))}
              </tbody>
            </table>
          </motion.div>
        )}
      </div>

      {/* Evidence notes */}
      <EvidenceNotes
        value={notes}
        onChange={setNotes}
        placeholder="Optional: Add evidence or notes to support your score..."
        suggestedSources={question.evidenceSources}
      />

      {/* Echo baseline hint */}
      <div className="mt-4 text-sm text-gray-500 bg-gray-50 p-3 rounded-lg">
        <span className="font-medium">Echo Health baseline:</span>{" "}
        Score {question.echoBaseline.score}  - {question.echoBaseline.note}
      </div>

      {/* Submit button */}
      <div className="mt-6 flex justify-end">
        <button
          className={`px-6 py-2 rounded-lg font-medium ${
            score !== null
              ? "bg-teal-600 text-white hover:bg-teal-700"
              : "bg-gray-200 text-gray-400 cursor-not-allowed"
          }`}
          onClick={handleSubmit}
          disabled={score === null}
        >
          {isLast ? "Complete Assessment" : "Next Question →"}
        </button>
      </div>
    </motion.div>
  );
}
```

### 4. Score Selector Component

```tsx
// components/assessment/ScoreSelector.tsx

import { motion } from "framer-motion";
import { ScoringCriteria } from "@/types/assessment";

interface Props {
  value: number | null;
  onChange: (score: number) => void;
  criteria: ScoringCriteria[];
}

const SCORE_COLORS: Record<number, { bg: string; border: string; text: string }> = {
  6: { bg: "bg-green-100", border: "border-green-500", text: "text-green-700" },
  5: { bg: "bg-blue-100", border: "border-blue-500", text: "text-blue-700" },
  4: { bg: "bg-teal-100", border: "border-teal-500", text: "text-teal-700" },
  3: { bg: "bg-yellow-100", border: "border-yellow-500", text: "text-yellow-700" },
  2: { bg: "bg-orange-100", border: "border-orange-500", text: "text-orange-700" },
  1: { bg: "bg-red-100", border: "border-red-500", text: "text-red-700" }
};

export function ScoreSelector({ value, onChange, criteria }: Props) {
  return (
    <div className="space-y-2">
      <label className="block text-sm font-medium text-gray-700 mb-3">
        Select your score:
      </label>

      <div className="grid grid-cols-6 gap-2">
        {[6, 5, 4, 3, 2, 1].map((score) => {
          const colors = SCORE_COLORS[score];
          const isSelected = value === score;
          const criterion = criteria.find((c) => c.score === score);

          return (
            <motion.button
              key={score}
              className={`
                relative p-3 rounded-lg border-2 transition-all
                ${isSelected
                  ? `${colors.bg} ${colors.border}`
                  : "bg-white border-gray-200 hover:border-gray-300"
                }
              `}
              onClick={() => onChange(score)}
              whileHover={{ scale: 1.02 }}
              whileTap={{ scale: 0.98 }}
            >
              <div className={`text-2xl font-bold ${isSelected ? colors.text : "text-gray-600"}`}>
                {score}
              </div>
              <div className={`text-xs mt-1 ${isSelected ? colors.text : "text-gray-500"}`}>
                {criterion?.label}
              </div>

              {/* Selection indicator */}
              {isSelected && (
                <motion.div
                  className={`absolute -top-1 -right-1 w-5 h-5 rounded-full ${colors.border.replace("border", "bg")} flex items-center justify-center`}
                  initial={{ scale: 0 }}
                  animate={{ scale: 1 }}
                >
                  <svg className="w-3 h-3 text-white" fill="currentColor" viewBox="0 0 20 20">
                    <path
                      fillRule="evenodd"
                      d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                      clipRule="evenodd"
                    />
                  </svg>
                </motion.div>
              )}
            </motion.button>
          );
        })}
      </div>

      {/* Selected score details */}
      {value !== null && (
        <motion.div
          className={`mt-4 p-3 rounded-lg ${SCORE_COLORS[value].bg}`}
          initial={{ opacity: 0, y: -10 }}
          animate={{ opacity: 1, y: 0 }}
        >
          <div className={`text-sm ${SCORE_COLORS[value].text}`}>
            <span className="font-semibold">
              {criteria.find((c) => c.score === value)?.label}:
            </span>{" "}
            {criteria.find((c) => c.score === value)?.criteria}
          </div>
        </motion.div>
      )}
    </div>
  );
}
```

### 5. Radar Chart Component

```tsx
// components/charts/RadarChart.tsx

import {
  Radar,
  RadarChart as RechartsRadar,
  PolarGrid,
  PolarAngleAxis,
  PolarRadiusAxis,
  Legend,
  ResponsiveContainer,
  Tooltip
} from "recharts";

interface Props {
  data: {
    dimension: string;
    userScore: number;
    echoBaseline?: number;
    echoFinal?: number;
  }[];
  showEchoBenchmark?: boolean;
}

export function RadarChart({ data, showEchoBenchmark = true }: Props) {
  return (
    <ResponsiveContainer width="100%" height={400}>
      <RechartsRadar data={data}>
        <PolarGrid stroke="#e5e7eb" />
        <PolarAngleAxis
          dataKey="dimension"
          tick={{ fill: "#374151", fontSize: 14, fontWeight: 500 }}
        />
        <PolarRadiusAxis
          angle={30}
          domain={[0, 100]}
          tick={{ fill: "#9ca3af", fontSize: 12 }}
        />

        {/* User score */}
        <Radar
          name="Your Score"
          dataKey="userScore"
          stroke="#14b8a6"
          fill="#14b8a6"
          fillOpacity={0.3}
          strokeWidth={2}
        />

        {/* Echo benchmarks */}
        {showEchoBenchmark && (
          <>
            <Radar
              name="Echo (Week 0)"
              dataKey="echoBaseline"
              stroke="#9ca3af"
              fill="none"
              strokeWidth={1}
              strokeDasharray="5 5"
            />
            <Radar
              name="Echo (Week 12)"
              dataKey="echoFinal"
              stroke="#22c55e"
              fill="none"
              strokeWidth={1}
              strokeDasharray="3 3"
            />
          </>
        )}

        <Legend />
        <Tooltip
          formatter={(value: number) => [`${value}%`, ""]}
          labelFormatter={(label) => `Dimension: ${label}`}
        />
      </RechartsRadar>
    </ResponsiveContainer>
  );
}
```

### 6. Results Page Component

```tsx
// components/assessment/ResultsPage.tsx

import { motion } from "framer-motion";
import { RadarChart } from "@/components/charts/RadarChart";
import { TrustBandBadge } from "./TrustBandBadge";
import { DimensionBreakdown } from "./DimensionBreakdown";
import { RecommendationsPanel } from "./RecommendationsPanel";
import { generatePDF } from "@/lib/pdf/generateReport";

interface Props {
  session: AssessmentSession;
}

export function ResultsPage({ session }: Props) {
  const { results } = session;

  if (!results) return null;

  const radarData = Object.entries(results.dimensionScores).map(
    ([dim, score]) => ({
      dimension: DIMENSION_NAMES[dim as DimensionId],
      userScore: score.percentageScore,
      echoBaseline: getEchoScore(dim as DimensionId, 0),
      echoFinal: getEchoScore(dim as DimensionId, 12)
    })
  );

  const handleDownloadPDF = async () => {
    const pdfUrl = await generatePDF(session);
    window.open(pdfUrl, "_blank");
  };

  return (
    <div className="space-y-8">
      {/* Header with overall score */}
      <motion.div
        className="text-center"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
      >
        <h1 className="text-3xl font-bold text-gray-900 mb-2">
          Your INPACT Assessment Results
        </h1>
        <p className="text-gray-600">
          {session.lead.organization} • Completed {formatDate(session.completedAt)}
        </p>
      </motion.div>

      {/* Score card */}
      <motion.div
        className="bg-white rounded-2xl shadow-xl p-8 text-center"
        initial={{ opacity: 0, scale: 0.95 }}
        animate={{ opacity: 1, scale: 1 }}
        transition={{ delay: 0.1 }}
      >
        <div className="text-6xl font-bold text-gray-900 mb-2">
          {results.percentageScore}
          <span className="text-2xl text-gray-400">/100</span>
        </div>

        <TrustBandBadge band={results.trustBand} size="large" />

        <p className="mt-4 text-gray-600 max-w-md mx-auto">
          {results.trustBand.description}
        </p>

        {/* INPACT score (6-36 scale) */}
        <div className="mt-4 text-sm text-gray-500">
          INPACT Score: {results.totalScore.toFixed(1)}/36
        </div>
      </motion.div>

      {/* Radar chart */}
      <motion.div
        className="bg-white rounded-2xl shadow-xl p-8"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ delay: 0.2 }}
      >
        <h2 className="text-xl font-semibold text-gray-900 mb-6 text-center">
          Dimension Breakdown
        </h2>
        <RadarChart data={radarData} showEchoBenchmark={true} />

        <div className="mt-6 flex justify-center gap-6 text-sm">
          <div className="flex items-center gap-2">
            <div className="w-4 h-4 rounded bg-teal-500" />
            <span>Your Score</span>
          </div>
          <div className="flex items-center gap-2">
            <div className="w-4 h-1 border-t-2 border-dashed border-gray-400" />
            <span>Echo (Week 0): 28%</span>
          </div>
          <div className="flex items-center gap-2">
            <div className="w-4 h-1 border-t-2 border-dashed border-green-500" />
            <span>Echo (Week 12): 89%</span>
          </div>
        </div>
      </motion.div>

      {/* Strengths & Gaps */}
      <div className="grid md:grid-cols-2 gap-6">
        <motion.div
          className="bg-green-50 rounded-xl p-6"
          initial={{ opacity: 0, x: -20 }}
          animate={{ opacity: 1, x: 0 }}
          transition={{ delay: 0.3 }}
        >
          <h3 className="text-lg font-semibold text-green-800 mb-4">
            💪 Your Strengths
          </h3>
          <ul className="space-y-2">
            {results.strengths.map((dim) => (
              <li key={dim} className="flex items-center gap-2">
                <span className="text-green-600 font-bold">
                  {results.dimensionScores[dim].averageScore.toFixed(1)}
                </span>
                <span className="text-green-700">
                  {DIMENSION_NAMES[dim]}
                </span>
              </li>
            ))}
          </ul>
        </motion.div>

        <motion.div
          className="bg-orange-50 rounded-xl p-6"
          initial={{ opacity: 0, x: 20 }}
          animate={{ opacity: 1, x: 0 }}
          transition={{ delay: 0.3 }}
        >
          <h3 className="text-lg font-semibold text-orange-800 mb-4">
            🎯 Priority Gaps
          </h3>
          <ul className="space-y-2">
            {results.gaps.map((dim) => (
              <li key={dim} className="flex items-center gap-2">
                <span className="text-orange-600 font-bold">
                  {results.dimensionScores[dim].averageScore.toFixed(1)}
                </span>
                <span className="text-orange-700">
                  {DIMENSION_NAMES[dim]}
                </span>
              </li>
            ))}
          </ul>
        </motion.div>
      </div>

      {/* Critical gaps warning */}
      {results.criticalGaps.length > 0 && (
        <motion.div
          className="bg-red-50 border border-red-200 rounded-xl p-6"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 0.4 }}
        >
          <h3 className="text-lg font-semibold text-red-800 mb-2">
            ⚠️ Critical Gaps (Score 1)
          </h3>
          <p className="text-red-700 mb-3">
            These areas require immediate attention before agent deployment:
          </p>
          <div className="flex flex-wrap gap-2">
            {results.criticalGaps.map((qId) => (
              <span
                key={qId}
                className="bg-red-100 text-red-800 px-3 py-1 rounded-full text-sm font-medium"
              >
                {qId}
              </span>
            ))}
          </div>
        </motion.div>
      )}

      {/* Dimension breakdown */}
      <DimensionBreakdown dimensionScores={results.dimensionScores} />

      {/* Recommendations */}
      <RecommendationsPanel
        priorityPhase={results.priorityPhase}
        recommendedChapters={results.recommendedChapters}
        trustBand={results.trustBand}
      />

      {/* Download & next steps */}
      <motion.div
        className="bg-teal-50 rounded-xl p-8 text-center"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ delay: 0.5 }}
      >
        <h2 className="text-xl font-semibold text-teal-900 mb-4">
          Download Your Full Report
        </h2>
        <p className="text-teal-700 mb-6 max-w-md mx-auto">
          Get a detailed PDF report with all 36 question scores, evidence notes,
          and personalized recommendations.
        </p>
        <button
          onClick={handleDownloadPDF}
          className="bg-teal-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-teal-700 transition-colors"
        >
          📄 Download PDF Report
        </button>

        <div className="mt-8 pt-6 border-t border-teal-200">
          <h3 className="text-lg font-semibold text-teal-900 mb-3">
            Next Steps
          </h3>
          <div className="flex flex-col sm:flex-row justify-center gap-4">
            <a
              href="/stack"
              className="bg-white text-teal-700 border border-teal-300 px-6 py-2 rounded-lg hover:bg-teal-50"
            >
              🔧 Build Your Stack
            </a>
            <a
              href="/book"
              className="bg-white text-teal-700 border border-teal-300 px-6 py-2 rounded-lg hover:bg-teal-50"
            >
              📚 Get the Book
            </a>
            <a
              href="/consult"
              className="bg-white text-teal-700 border border-teal-300 px-6 py-2 rounded-lg hover:bg-teal-50"
            >
              💬 Schedule Consultation
            </a>
          </div>
        </div>
      </motion.div>
    </div>
  );
}
```

---

## State Management (Zustand)

```typescript
// lib/store/assessmentStore.ts

import { create } from "zustand";
import { persist } from "zustand/middleware";

interface AssessmentState {
  // Session
  sessionId: string | null;
  session: AssessmentSession | null;
  currentStep: "landing" | "lead" | "assessment" | "results";

  // Assessment state
  currentDimension: DimensionId;
  currentQuestion: number;
  responses: Record<string, QuestionResponse>;

  // Results (computed)
  results: AssessmentResults | null;

  // Actions
  setStep: (step: AssessmentState["currentStep"]) => void;
  loadSession: (sessionId: string) => Promise<void>;
  submitResponse: (questionId: string, score: number, notes?: string) => Promise<void>;
  goToQuestion: (dimension: DimensionId, question: number) => void;
  goToNextQuestion: () => void;
  goToPrevQuestion: () => void;
  calculateResults: () => AssessmentResults;
  reset: () => void;
}

export const useAssessmentStore = create<AssessmentState>()(
  persist(
    (set, get) => ({
      sessionId: null,
      session: null,
      currentStep: "landing",
      currentDimension: "I",
      currentQuestion: 1,
      responses: {},
      results: null,

      setStep: (step) => set({ currentStep: step }),

      loadSession: async (sessionId) => {
        const response = await fetch(`/api/assessments/${sessionId}`);
        const { session, progress } = await response.json();

        set({
          sessionId,
          session,
          responses: session.responses || {},
          currentDimension: progress.currentDimension,
          currentQuestion: progress.currentQuestionNumber,
          currentStep: session.completedAt ? "results" : "assessment"
        });

        if (session.completedAt) {
          set({ results: session.results });
        }
      },

      submitResponse: async (questionId, score, notes) => {
        const { sessionId, responses } = get();

        // Save to server
        await fetch(`/api/assessments/${sessionId}/responses`, {
          method: "POST",
          body: JSON.stringify({ questionId, score, evidenceNotes: notes })
        });

        // Update local state
        const newResponses = {
          ...responses,
          [questionId]: {
            questionId,
            score,
            evidenceNotes: notes,
            answeredAt: new Date()
          }
        };

        set({ responses: newResponses });

        // Check if complete
        if (Object.keys(newResponses).length === 36) {
          const results = get().calculateResults();
          set({ results, currentStep: "results" });
        } else {
          get().goToNextQuestion();
        }
      },

      goToNextQuestion: () => {
        const { currentDimension, currentQuestion, responses } = get();
        const next = getNextQuestion(responses, currentDimension, currentQuestion);

        if (next) {
          set({
            currentDimension: next.dimension,
            currentQuestion: next.question
          });
        }
      },

      goToPrevQuestion: () => {
        const { currentDimension, currentQuestion } = get();

        if (currentQuestion > 1) {
          set({ currentQuestion: currentQuestion - 1 });
        } else {
          // Go to previous dimension
          const dimensions: DimensionId[] = ["I", "N", "P", "A", "C", "T"];
          const dimIndex = dimensions.indexOf(currentDimension);
          if (dimIndex > 0) {
            set({
              currentDimension: dimensions[dimIndex - 1],
              currentQuestion: 6
            });
          }
        }
      },

      calculateResults: () => {
        const { responses } = get();
        return calculateResults(responses);
      },

      reset: () => {
        set({
          sessionId: null,
          session: null,
          currentStep: "landing",
          currentDimension: "I",
          currentQuestion: 1,
          responses: {},
          results: null
        });
      }
    }),
    {
      name: "inpact-assessment",
      partialize: (state) => ({
        sessionId: state.sessionId,
        responses: state.responses,
        currentDimension: state.currentDimension,
        currentQuestion: state.currentQuestion
      })
    }
  )
);
```

---

## Question Data File

```typescript
// data/questions.ts

import { Dimension, DimensionId } from "@/types/assessment";

export const DIMENSIONS: Dimension[] = [
  {
    id: "I",
    name: "Instant",
    fullName: "I  - INSTANT",
    description: "Measures infrastructure's ability to deliver sub-second responses that match conversational expectations.",
    color: "#14b8a6",  // teal
    questions: [
      {
        id: "I-1",
        dimensionId: "I",
        questionNumber: 1,
        title: "Query Response Time",
        question: "What is your P95 query response time for agent-relevant data?",
        scoringCriteria: [
          { score: 6, label: "Excellent", criteria: "<500ms P95, <100ms P50, consistent across query types", deploymentReadiness: "Production + competitive advantage" },
          { score: 5, label: "Strong", criteria: "<1s P95, <300ms P50, occasional spikes under load", deploymentReadiness: "Deploy with confidence" },
          { score: 4, label: "Functional", criteria: "<3s P95, <1s P50, predictable performance", deploymentReadiness: "Deploy with monitoring" },
          { score: 3, label: "Moderate", criteria: "<5s P95, variable performance, load-dependent", deploymentReadiness: "Pilot only" },
          { score: 2, label: "Significant Gap", criteria: "5-15s P95, frequent timeouts, unpredictable", deploymentReadiness: "Not deployment-ready" },
          { score: 1, label: "Critical Gap", criteria: ">15s or frequent timeouts, unusable for conversation", deploymentReadiness: "Immediate remediation" }
        ],
        evidenceSources: ["APM dashboards", "database query logs", "load test results"],
        echoBaseline: { score: 1, note: "47-second average query time, 2-minute P95" }
      },
      {
        id: "I-2",
        dimensionId: "I",
        questionNumber: 2,
        title: "Data Freshness",
        question: "How current is the data agents access?",
        scoringCriteria: [
          { score: 6, label: "Excellent", criteria: "Real-time (<1 minute), streaming architecture", deploymentReadiness: "Production + competitive advantage" },
          { score: 5, label: "Strong", criteria: "Near real-time (<5 minutes), CDC operational", deploymentReadiness: "Deploy with confidence" },
          { score: 4, label: "Functional", criteria: "<1 hour freshness, reliable refresh cycles", deploymentReadiness: "Deploy with monitoring" },
          { score: 3, label: "Moderate", criteria: "<4 hours freshness, scheduled batch with monitoring", deploymentReadiness: "Pilot only" },
          { score: 2, label: "Significant Gap", criteria: "4-24 hours freshness, overnight batch only", deploymentReadiness: "Not deployment-ready" },
          { score: 1, label: "Critical Gap", criteria: ">24 hours or unknown freshness, no freshness SLA", deploymentReadiness: "Immediate remediation" }
        ],
        evidenceSources: ["CDC lag dashboards", "ETL schedules", "data timestamp analysis"],
        echoBaseline: { score: 1, note: "72-hour batch refresh cycle" }
      },
      // ... Continue with I-3 through I-6
      // ... Then N-1 through N-6
      // ... Then P-1 through P-6
      // ... Then A-1 through A-6
      // ... Then C-1 through C-6
      // ... Then T-1 through T-6
    ]
  },
  // ... Continue with N, P, A, C, T dimensions
];

// Helper to get a specific question
export function getQuestion(questionId: string): Question | undefined {
  for (const dim of DIMENSIONS) {
    const q = dim.questions.find(q => q.id === questionId);
    if (q) return q;
  }
  return undefined;
}

// Helper to get all questions for a dimension
export function getDimensionQuestions(dimensionId: DimensionId): Question[] {
  const dim = DIMENSIONS.find(d => d.id === dimensionId);
  return dim?.questions || [];
}
```

---

## File Structure Summary

```
inpact-assessment/
├── app/
│   ├── page.tsx                      # Landing redirect
│   ├── assess/
│   │   ├── page.tsx                  # Start new assessment
│   │   └── [sessionId]/
│   │       └── page.tsx              # Resume/view assessment
│   ├── api/
│   │   ├── assessments/
│   │   │   ├── route.ts              # POST: create session
│   │   │   ├── resume/route.ts       # GET: find by email
│   │   │   └── [id]/
│   │   │       ├── route.ts          # GET session
│   │   │       ├── responses/route.ts # POST response
│   │   │       ├── results/route.ts   # GET computed results
│   │   │       └── report/route.ts    # POST generate PDF
├── components/
│   ├── assessment/                    # All components listed above
│   ├── charts/
│   │   └── RadarChart.tsx
│   ├── pdf/
│   │   └── AssessmentReport.tsx
│   └── ui/
├── lib/
│   ├── data/
│   │   ├── questions.ts              # All 36 questions
│   │   ├── dimensions.ts             # Dimension definitions
│   │   ├── trustBands.ts             # Trust band definitions
│   │   └── echoBenchmark.ts          # Echo Health data
│   ├── algorithms/
│   │   ├── scoring.ts                # Score calculation
│   │   ├── progress.ts               # Progress tracking
│   │   └── charts.ts                 # Chart data generation
│   ├── store/
│   │   └── assessmentStore.ts        # Zustand store
│   └── db/
│       └── prisma.ts
├── types/
│   ├── assessment.ts
│   ├── session.ts
│   └── trustBands.ts
└── prisma/
    └── schema.prisma
```

---

## Quick Start for AI Coding Tools

```markdown
## Instructions for Claude Code / Cursor / Windsurf

1. **Create Next.js app:**
   ```bash
   npx create-next-app@latest inpact-assessment --typescript --tailwind --app
   cd inpact-assessment
   npm install zustand framer-motion recharts react-hook-form zod @prisma/client
   npm install -D prisma
   ```

2. **Set up database:**
   - Copy the schema from "Database Schema" section to `prisma/schema.prisma`
   - Run `npx prisma migrate dev`

3. **Create types:**
   - Copy all interfaces from "Data Models" section to `types/` folder

4. **Create question data:**
   - Copy the DIMENSIONS array pattern to `lib/data/questions.ts`
   - Add all 36 questions following the pattern shown
   - Reference `kb_INPACT_assessment_36_questions.md` for full question text

5. **Implement algorithms:**
   - Copy scoring functions to `lib/algorithms/scoring.ts`
   - Copy progress functions to `lib/algorithms/progress.ts`
   - Copy chart generation to `lib/algorithms/charts.ts`

6. **Create Zustand store:**
   - Copy store to `lib/store/assessmentStore.ts`

7. **Build components:**
   - Start with `AssessmentFlow.tsx` as the main container
   - Build `QuestionCard.tsx` and `ScoreSelector.tsx` for question UX
   - Build `ResultsPage.tsx` with `RadarChart.tsx` for results display
   - Use Tailwind for styling, Framer Motion for animations

8. **Create API routes:**
   - Follow the endpoint patterns in "API Endpoints" section
   - Use Prisma for database operations

9. **Add PDF generation:**
   - Use @react-pdf/renderer for PDF report
   - Include radar chart, dimension breakdown, recommendations

10. **Test the flow:**
    - Landing → Lead capture → 36 questions (6 per dimension) → Results + PDF
```

---

## PDF Report Template (React-PDF)

```tsx
// lib/pdf/AssessmentReport.tsx

import {
  Document,
  Page,
  Text,
  View,
  StyleSheet,
  Image
} from "@react-pdf/renderer";

const styles = StyleSheet.create({
  page: { padding: 40, fontFamily: "Helvetica" },
  header: { marginBottom: 30 },
  title: { fontSize: 24, fontWeight: "bold", marginBottom: 10 },
  subtitle: { fontSize: 12, color: "#666" },
  scoreCard: {
    backgroundColor: "#f0fdfa",
    padding: 20,
    borderRadius: 8,
    marginBottom: 20,
    textAlign: "center"
  },
  bigScore: { fontSize: 48, fontWeight: "bold", color: "#0d9488" },
  trustBand: { fontSize: 16, marginTop: 10 },
  section: { marginBottom: 20 },
  sectionTitle: { fontSize: 16, fontWeight: "bold", marginBottom: 10 },
  table: { width: "100%" },
  tableRow: { flexDirection: "row", borderBottomWidth: 1, borderColor: "#e5e7eb" },
  tableCell: { flex: 1, padding: 8, fontSize: 10 },
  footer: { position: "absolute", bottom: 30, left: 40, right: 40, textAlign: "center", fontSize: 8, color: "#999" }
});

interface Props {
  session: AssessmentSession;
  radarChartImage: string;  // Base64 encoded
}

export function AssessmentReport({ session, radarChartImage }: Props) {
  const { results, lead } = session;

  return (
    <Document>
      {/* Cover Page */}
      <Page size="A4" style={styles.page}>
        <View style={styles.header}>
          <Text style={styles.title}>INPACT Assessment Report</Text>
          <Text style={styles.subtitle}>
            {lead.organization} • {formatDate(session.completedAt)}
          </Text>
        </View>

        <View style={styles.scoreCard}>
          <Text style={styles.bigScore}>{results.percentageScore}/100</Text>
          <Text style={styles.trustBand}>{results.trustBand.name}</Text>
        </View>

        {/* Radar chart */}
        <Image src={radarChartImage} style={{ width: 300, height: 300, alignSelf: "center" }} />

        <View style={styles.footer}>
        </View>
      </Page>

      {/* Executive Summary */}
      <Page size="A4" style={styles.page}>
        <Text style={styles.sectionTitle}>Executive Summary</Text>
        {/* ... summary content */}
      </Page>

      {/* Dimension Pages (6 pages) */}
      {Object.entries(results.dimensionScores).map(([dim, score]) => (
        <Page key={dim} size="A4" style={styles.page}>
          <Text style={styles.sectionTitle}>
            {DIMENSION_NAMES[dim as DimensionId]}  - Score: {score.averageScore.toFixed(1)}/6
          </Text>
          {/* ... dimension breakdown */}
        </Page>
      ))}

      {/* Recommendations */}
      <Page size="A4" style={styles.page}>
        <Text style={styles.sectionTitle}>Recommendations & Next Steps</Text>
        {/* ... recommendations */}
      </Page>
    </Document>
  );
}
```