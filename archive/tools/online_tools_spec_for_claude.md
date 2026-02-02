# Chapter 11 Online Tools Specification
**Version:** 3.0 | **Target:** trustbeforeintelligence.com/tools

---

# PART 1: SHARED DEFINITIONS

## 1.1 Entry Types

```yaml
entry_types:
  - id: vendor_product
    name: "Vendor Product"
    examples: ["Pinecone", "Datadog", "OpenAI"]
    inpact_scoring: full
    goals_scoring: full
    gap_analysis: if_goals_below_70
    contract: true
    rfp: true
    
  - id: managed_opensource
    name: "Managed Open-Source"
    examples: ["Confluent (Kafka)", "Grafana Cloud", "AWS RDS"]
    inpact_scoring: full
    goals_scoring: full
    gap_analysis: if_goals_below_70
    contract: true
    rfp: true
    note: "Send RFP to managed provider, not OSS project"
    
  - id: cloud_hosted
    name: "Cloud Provider Hosted"
    examples: ["Azure OpenAI", "AWS Bedrock", "Google Vertex AI"]
    inpact_scoring: full
    goals_scoring: full
    gap_analysis: if_goals_below_70
    contract: true
    rfp: true
    note: "Contract with cloud provider (Microsoft, AWS, Google)"
    
  - id: self_hosted_opensource
    name: "Self-Hosted Open-Source"
    examples: ["PostgreSQL", "OPA", "Apache Kafka"]
    inpact_scoring: full
    goals_scoring: full
    gap_analysis: always
    contract: false
    rfp: false
    note: "Gap analysis always required; cloud provider contract only"
    
  - id: framework
    name: "Framework/Library"
    examples: ["LangChain", "LlamaIndex", "AutoGen"]
    inpact_scoring: capability_checklist
    goals_scoring: none
    gap_analysis: none
    contract: false
    rfp: false
    note: "Use Tab 9 Framework Capability Checklist"
    
  - id: standard
    name: "Standard/Protocol"
    examples: ["OpenTelemetry", "OIDC", "OAuth"]
    inpact_scoring: none
    goals_scoring: none
    gap_analysis: none
    contract: false
    rfp: false
    note: "Not scoreable; evaluate compliance only"
    
  - id: model
    name: "Model"
    examples: ["LLaMA", "Mistral", "Claude"]
    inpact_scoring: benchmarks
    goals_scoring: none
    gap_analysis: none
    contract: license_only
    rfp: false
    
  - id: model_runtime
    name: "Model Runtime"
    examples: ["Ollama", "vLLM", "TGI"]
    inpact_scoring: partial  # I, A only
    goals_scoring: partial   # O, L, S only
    gap_analysis: if_goals_below_70
    contract: false
    rfp: false
    
  - id: repository
    name: "Repository/Registry"
    examples: ["Hugging Face Hub", "Docker Hub", "MLflow Registry"]
    inpact_scoring: partial  # C only
    goals_scoring: if_paid
    gap_analysis: if_goals_below_70
    contract: if_paid
    rfp: if_paid
```

## 1.2 Layer Configuration

```yaml
layers:
  L1:
    name: "Storage"
    purpose: "Query performance, data access"
    inpact_dimensions: ["I", "C"]
    max_inpact_points: 12
    
  L2:
    name: "Data Fabric"
    purpose: "Real-time data flow"
    inpact_dimensions: ["I", "A", "C"]
    max_inpact_points: 18
    
  L3:
    name: "Semantic"
    purpose: "Business language understanding"
    inpact_dimensions: ["N", "C"]
    max_inpact_points: 12
    
  L4:
    name: "Intelligence"
    purpose: "LLM/RAG capabilities"
    inpact_dimensions: ["I", "N", "A"]
    max_inpact_points: 18
    
  L5:
    name: "Governance"
    purpose: "Access control, policy"
    inpact_dimensions: ["P", "T"]
    max_inpact_points: 12
    
  L6:
    name: "Observability"
    purpose: "Monitoring, tracing"
    inpact_dimensions: ["T", "A"]
    max_inpact_points: 12
    
  L7:
    name: "Orchestration"
    purpose: "Multi-agent coordination"
    inpact_dimensions: ["I", "N", "P", "A", "C", "T"]
    max_inpact_points: 36
    
  Foundational:
    name: "Foundational"
    purpose: "Identity/Auth - enables L5"
    inpact_dimensions: []  # Use standard vendor criteria
    max_inpact_points: 0
    note: "Not part of 7-layer architecture"
```

## 1.3 INPACT Dimensions

```yaml
inpact_dimensions:
  I:
    name: "Instant"
    label: "Instant Response"
    description: "Sub-second query performance"
    score_range: [1, 6]
    scoring_guide:
      1: "Seconds latency, no caching"
      2: "1-2 second latency"
      3: "500ms-1s latency"
      4: "200-500ms latency"
      5: "100-200ms latency"
      6: "<100ms P95 latency with caching"
      
  N:
    name: "Natural"
    label: "Natural Language"
    description: "Semantic understanding quality"
    score_range: [1, 6]
    scoring_guide:
      1: "No NLU capability"
      2: "Basic keyword matching"
      3: "Simple NLU, <70% accuracy"
      4: "Good NLU, 70-80% accuracy"
      5: "Strong NLU, 80-90% accuracy"
      6: ">90% semantic accuracy, domain-aware"
      
  P:
    name: "Permitted"
    label: "Permission Control"
    description: "Access control and policy enforcement"
    score_range: [1, 6]
    scoring_guide:
      1: "No access control"
      2: "Basic authentication only"
      3: "Role-based access (RBAC)"
      4: "RBAC + basic policies"
      5: "ABAC support"
      6: "Full ABAC + audit trail + policy versioning"
      
  A:
    name: "Adaptive"
    label: "Adaptive Learning"
    description: "Feedback loops and continuous improvement"
    score_range: [1, 6]
    scoring_guide:
      1: "No adaptation capability"
      2: "Manual retraining only"
      3: "Scheduled retraining"
      4: "Feedback collection + manual triggers"
      5: "Automated drift detection"
      6: "Full feedback loops + auto-retraining + drift alerts"
      
  C:
    name: "Contextual"
    label: "Context Integration"
    description: "Multi-source data integration"
    score_range: [1, 6]
    scoring_guide:
      1: "Single data source only"
      2: "2-3 connectors, batch only"
      3: "5-10 connectors, some streaming"
      4: "10-20 connectors, real-time capable"
      5: "20+ connectors, multi-modal"
      6: "Extensive catalog, real-time, multi-modal, <30s freshness"
      
  T:
    name: "Transparent"
    label: "Transparency"
    description: "Explainability and audit capabilities"
    score_range: [1, 6]
    scoring_guide:
      1: "Black box, no logging"
      2: "Basic logging only"
      3: "Decision logging, no explanation"
      4: "Explanations available on request"
      5: "Automatic explanations + audit trail"
      6: "Full explainability + compliance reporting + lineage"
```

## 1.4 GOALS Dimensions

```yaml
goals_dimensions:
  G:
    name: "Governance"
    label: "Governance & Compliance"
    description: "Compliance certifications and audit capabilities"
    score_range: [1, 5]
    scoring_guide:
      1: "No certifications, no audit"
      2: "Basic security, no compliance certs"
      3: "SOC2 Type I or equivalent"
      4: "SOC2 Type II + ISO27001"
      5: "SOC2 Type II + ISO27001 + HIPAA BAA + industry-specific"
    gap_action: "Internal compliance program (audit logging, security reviews)"
    gap_cost: "$20-50K/year"
    
  O:
    name: "Observability"
    label: "Observability & Monitoring"
    description: "Dashboards, alerting, metrics"
    score_range: [1, 5]
    scoring_guide:
      1: "No monitoring"
      2: "Basic health checks"
      3: "Metrics available, no dashboards"
      4: "Dashboards + basic alerting"
      5: "Full dashboards + alerting + export + custom metrics"
    gap_action: "Deploy monitoring stack (Prometheus/Grafana, alerting)"
    gap_cost: "$10-30K/year"
    
  A:
    name: "Availability"
    label: "Availability & Support"
    description: "SLA, support tiers, incident response"
    score_range: [1, 5]
    scoring_guide:
      1: "No SLA, community only"
      2: "Best effort, email support"
      3: "99% SLA, business hours support"
      4: "99.9% SLA, 24/5 support"
      5: "99.95%+ SLA, 24/7 support, dedicated CSM"
    gap_action: "Build HA + on-call rotation (runbooks, incident response)"
    gap_cost: "$30-80K/year"
    
  L:
    name: "Lexicon"
    label: "Lexicon (Documentation)"
    description: "API docs, SDKs, examples"
    score_range: [1, 5]
    scoring_guide:
      1: "No documentation"
      2: "Basic README only"
      3: "API reference, limited examples"
      4: "Good docs + SDK + examples"
      5: "Excellent docs + multiple SDKs + tutorials + community"
    gap_action: "Internal documentation effort (wrapper libraries, training)"
    gap_cost: "$5-15K/year"
    
  S:
    name: "Solid"
    label: "Solid (Reliability)"
    description: "Production maturity and track record"
    score_range: [1, 5]
    scoring_guide:
      1: "Alpha/experimental"
      2: "Beta, <1 year production use"
      3: "1-2 years production, limited scale"
      4: "2-5 years production, proven scale"
      5: "5+ years production, enterprise-proven, case studies"
    gap_action: "Extended validation period (testing, staged rollout)"
    gap_cost: "$10-20K/year"
```

## 1.5 Recommendation Logic (Pseudocode)

```python
def calculate_recommendation(inpact_pct, goals_pct, arch_fit, entry_type):
    """
    Returns: RECOMMEND | CONDITIONAL | NOT_RECOMMENDED | FRAMEWORK
    """
    # Rule 1: Frameworks use capability checklist
    if entry_type == "framework":
        return "FRAMEWORK"
    
    # Rule 2: Standards are informational only
    if entry_type == "standard":
        return "N/A"
    
    # Rule 3: Architecture must pass
    if arch_fit == False:
        return "NOT_RECOMMENDED"
    
    # Rule 4: INPACT must meet threshold
    if inpact_pct < 67:
        return "NOT_RECOMMENDED"
    
    # Rule 5: GOALS determines final recommendation
    if goals_pct >= 70:
        return "RECOMMEND"
    elif goals_pct >= 50:
        return "CONDITIONAL"  # Requires gap budget
    else:
        return "NOT_RECOMMENDED"


def calculate_inpact_percentage(scores, layer):
    """
    scores: dict of dimension -> score (1-6)
    layer: L1-L7
    Returns: percentage (0-100)
    """
    applicable_dims = LAYERS[layer]["inpact_dimensions"]
    total = sum(scores[dim] for dim in applicable_dims if dim in scores)
    max_possible = LAYERS[layer]["max_inpact_points"]
    return (total / max_possible) * 100 if max_possible > 0 else 0


def calculate_goals_percentage(scores):
    """
    scores: dict of G, O, A, L, S -> score (1-5)
    Returns: percentage (0-100)
    """
    total = sum(scores.values())
    return (total / 25) * 100


def calculate_gap_budget(goals_scores):
    """
    Returns: estimated annual gap cost
    """
    gap_costs = {"G": 35000, "O": 20000, "A": 55000, "L": 10000, "S": 15000}
    total = 0
    for dim, score in goals_scores.items():
        gap = 5 - score
        if gap >= 2:
            total += gap_costs[dim]
    return total


def calculate_framework_recommendation(capabilities, maturity_scores):
    """
    capabilities: dict of capability_name -> {required: bool, supported: bool}
    maturity_scores: list of 1-5 scores
    Returns: ADOPT | ADOPT_WITH_CAUTION | DO_NOT_ADOPT
    """
    # Check required capabilities
    required_caps = [c for c, v in capabilities.items() if v["required"]]
    missing_required = [c for c in required_caps if not capabilities[c]["supported"]]
    
    if missing_required:
        return "DO_NOT_ADOPT"
    
    # Check maturity average
    avg_maturity = sum(maturity_scores) / len(maturity_scores) if maturity_scores else 0
    
    if avg_maturity >= 4:
        return "ADOPT"
    elif avg_maturity >= 3:
        return "ADOPT_WITH_CAUTION"
    else:
        return "DO_NOT_ADOPT"
```

## 1.6 Performance Benchmarks

```yaml
benchmarks:
  L1_query_latency:
    target: "<100ms P95"
    metric: "milliseconds"
    
  L2_cdc_freshness:
    target: "<30 seconds"
    metric: "seconds"
    
  L3_semantic_accuracy:
    target: ">85%"
    metric: "percentage"
    
  L4_llm_response:
    target: "<5 seconds P95"
    metric: "seconds"
    
  L5_policy_evaluation:
    target: "<100ms"
    metric: "milliseconds"
    
  end_to_end:
    target: "<5 seconds P95"
    metric: "seconds"
```

---

# PART 2: TOOL SPECIFICATIONS

## Tool 1: Vendor Evaluation Scorecard

```yaml
tool_id: vendor_scorecard
format: spreadsheet
output: Google Sheets or Excel

tabs:
  - id: instructions
    name: "Instructions"
    content: |
      1. Select Entry Type from dropdown
      2. Select Target Layer
      3. Score applicable INPACT dimensions (1-6)
      4. Score all GOALS dimensions (1-5)
      5. Complete Architecture Fit checklist
      6. Review auto-calculated recommendation
      7. If CONDITIONAL, complete Gap Analysis tab

  - id: inpact_scoring
    name: "INPACT Scoring"
    fields:
      - name: vendor_name
        type: text
        required: true
        label: "Vendor/Product Name"
        
      - name: entry_type
        type: dropdown
        required: true
        label: "Entry Type"
        options: ["Vendor Product", "Managed Open-Source", "Cloud Provider Hosted", "Self-Hosted Open-Source", "Framework/Library", "Standard/Protocol", "Model", "Model Runtime", "Repository/Registry"]
        default: "Vendor Product"
        # See section 1.1 for full Entry Type definitions
        
      - name: target_layer
        type: dropdown
        required: true
        label: "Primary Layer"
        options: ["L1", "L2", "L3", "L4", "L5", "L6", "L7", "Foundational"]
        on_change: "update_applicable_dimensions()"
        
      - name: score_I
        type: number
        label: "I (Instant)"
        range: [1, 6]
        visible_when: "target_layer in ['L1', 'L2', 'L4', 'L7']"
        
      - name: score_N
        type: number
        label: "N (Natural)"
        range: [1, 6]
        visible_when: "target_layer in ['L3', 'L4', 'L7']"
        
      - name: score_P
        type: number
        label: "P (Permitted)"
        range: [1, 6]
        visible_when: "target_layer in ['L5', 'L7']"
        
      - name: score_A
        type: number
        label: "A (Adaptive)"
        range: [1, 6]
        visible_when: "target_layer in ['L2', 'L4', 'L6', 'L7']"
        
      - name: score_C
        type: number
        label: "C (Contextual)"
        range: [1, 6]
        visible_when: "target_layer in ['L1', 'L2', 'L3', 'L7']"
        
      - name: score_T
        type: number
        label: "T (Transparent)"
        range: [1, 6]
        visible_when: "target_layer in ['L5', 'L6', 'L7']"
        
      - name: inpact_total
        type: calculated
        label: "Total Score"
        formula: "SUM(visible score fields)"
        
      - name: inpact_max
        type: calculated
        label: "Max Possible"
        formula: "VLOOKUP(target_layer, layers, max_inpact_points)"
        
      - name: inpact_percentage
        type: calculated
        label: "INPACT %"
        formula: "(inpact_total / inpact_max) * 100"
        format: "percentage"

  - id: goals_scoring
    name: "GOALS Scoring"
    fields:
      - name: vendor_name
        type: reference
        source: "inpact_scoring.vendor_name"
        
      - name: score_G
        type: number
        label: "G (Governance)"
        range: [1, 5]
        required: true
        help: "SOC2? ISO27001? HIPAA BAA?"
        
      - name: score_O
        type: number
        label: "O (Observability)"
        range: [1, 5]
        required: true
        help: "Dashboards? Alerting? Metrics export?"
        
      - name: score_A_goals
        type: number
        label: "A (Availability)"
        range: [1, 5]
        required: true
        help: "SLA? Support tiers? Response time?"
        
      - name: score_L
        type: number
        label: "L (Lexicon)"
        range: [1, 5]
        required: true
        help: "API docs? SDKs? Examples?"
        
      - name: score_S
        type: number
        label: "S (Solid)"
        range: [1, 5]
        required: true
        help: "Years in production? Customer count?"
        
      - name: goals_total
        type: calculated
        label: "Total Score"
        formula: "score_G + score_O + score_A_goals + score_L + score_S"
        
      - name: goals_percentage
        type: calculated
        label: "GOALS %"
        formula: "(goals_total / 25) * 100"
        format: "percentage"

  - id: architecture_fit
    name: "Architecture Fit"
    fields:
      - name: integration_complexity
        type: dropdown
        label: "Integration Complexity"
        options: ["Low", "Medium", "High"]
        required: true
        
      - name: data_residency_ok
        type: boolean
        label: "Data Residency Acceptable?"
        required: true
        
      - name: security_compatible
        type: boolean
        label: "Security Model Compatible?"
        required: true
        
      - name: scalability_adequate
        type: boolean
        label: "Scalability Adequate?"
        required: true
        
      - name: arch_fit_result
        type: calculated
        label: "Architecture Fit"
        formula: "IF(AND(data_residency_ok, security_compatible, scalability_adequate), 'Pass', 'Fail')"

  - id: comparison
    name: "Comparison Matrix"
    fields:
      - name: vendor_name
        type: reference
        source: "inpact_scoring.vendor_name"
        
      - name: entry_type
        type: reference
        source: "inpact_scoring.entry_type"
        
      - name: target_layer
        type: reference
        source: "inpact_scoring.target_layer"
        
      - name: inpact_pct
        type: reference
        source: "inpact_scoring.inpact_percentage"
        
      - name: goals_pct
        type: reference
        source: "goals_scoring.goals_percentage"
        
      - name: arch_fit
        type: reference
        source: "architecture_fit.arch_fit_result"
        
      - name: recommendation
        type: calculated
        label: "Recommendation"
        formula: |
          IF(entry_type="Framework/Library", "FRAMEWORK",
          IF(arch_fit="Fail", "NOT_RECOMMENDED",
          IF(inpact_pct<67, "NOT_RECOMMENDED",
          IF(goals_pct>=70, "RECOMMEND",
          IF(goals_pct>=50, "CONDITIONAL", "NOT_RECOMMENDED")))))
        conditional_formatting:
          RECOMMEND: green
          CONDITIONAL: yellow
          NOT_RECOMMENDED: red
          FRAMEWORK: blue
          
      - name: gap_budget
        type: calculated
        label: "Gap Budget Required"
        formula: "IF(recommendation='CONDITIONAL', calculate_gap_budget(goals_scores), 'N/A')"
        # See section 1.5 for calculate_gap_budget() implementation
        visible_when: "recommendation = 'CONDITIONAL'"

  - id: gap_analysis
    name: "Gap Analysis"
    note: "Complete only if recommendation = CONDITIONAL"
    fields:
      - name: dimension
        type: static
        values: ["G", "O", "A", "L", "S"]
        
      - name: vendor_score
        type: reference
        source: "goals_scoring.score_[dimension]"
        
      - name: gap
        type: calculated
        formula: "5 - vendor_score"
        
      - name: action_required
        type: calculated
        formula: "IF(gap>=2, LOOKUP(dimension, goals_dimensions[dimension].gap_action), 'None')"
        # See section 1.4 for gap_action definitions
        
      - name: estimated_cost
        type: calculated
        formula: "IF(gap>=2, LOOKUP(dimension, goals_dimensions[dimension].gap_cost), 0)"
        # See section 1.4 for gap_cost definitions (use midpoint: G=35000, O=20000, A=55000, L=10000, S=15000)
        
      - name: total_gap_cost
        type: calculated
        formula: "SUM(estimated_cost)"
        label: "Total Annual Gap Budget"

  - id: framework_checklist
    name: "Framework Checklist"
    note: "Use only when entry_type = Framework/Library"
    sections:
      identification:
        - {name: framework_name, type: text, required: true, label: "Framework Name"}
        - {name: target_layer, type: dropdown, options: ["L7", "L4", "L6", "Other"], default: "L7"}
        - {name: license, type: dropdown, options: ["MIT", "Apache 2.0", "GPL", "BSD", "Other"], required: true}
        - {name: maintainer_type, type: dropdown, options: ["Company", "Community", "Research Lab"], required: true}
        - {name: maturity_level, type: dropdown, options: ["Research Project", "Beta", "Production", "Mature"], required: true}
        - {name: github_stars, type: number, label: "GitHub Stars"}
        - {name: last_commit_date, type: date, label: "Last Commit"}
        - {name: first_release_date, type: date, label: "First Release"}
        - {name: breaking_changes, type: dropdown, options: ["None", "Minor", "Major"], label: "Breaking Changes (12 mo)"}
        
      capabilities:
        note: "For each capability: Is it required for your use case? Is it supported? Maturity 1-5."
        items:
          - {id: multi_agent, label: "Multi-agent orchestration"}
          - {id: tool_calling, label: "Tool/function calling"}
          - {id: memory_mgmt, label: "Memory/state management"}
          - {id: streaming, label: "Streaming support"}
          - {id: async_exec, label: "Async execution"}
          - {id: error_handling, label: "Error handling/retry"}
          - {id: observability, label: "Observability hooks"}
          - {id: hitl, label: "HITL integration"}
          - {id: custom_llm, label: "Custom LLM providers"}
          - {id: rag_pipeline, label: "RAG pipeline support"}
        fields_per_item:
          - {name: required, type: boolean, label: "Required?"}
          - {name: supported, type: boolean, label: "Supported?"}
          - {name: maturity, type: number, range: [1, 5], label: "Maturity"}
          
      integration:
        items:
          - {id: l1_storage, label: "Your L1 (Storage)"}
          - {id: l4_llm, label: "Your L4 (LLM provider)"}
          - {id: l5_governance, label: "Your L5 (Governance)"}
          - {id: l6_observability, label: "Your L6 (Observability)"}
          - {id: codebase, label: "Existing codebase"}
        fields_per_item:
          - {name: complexity, type: number, range: [1, 5], label: "Complexity"}
          - {name: effort, type: text, label: "Effort Estimate"}
          
      risks:
        items:
          - {id: abandonment, label: "Maintainer abandonment"}
          - {id: breaking_changes, label: "Breaking API changes"}
          - {id: security, label: "Security vulnerabilities"}
          - {id: scale, label: "Performance at scale"}
          - {id: learning, label: "Team learning curve"}
          - {id: research, label: "Research project risk"}
        fields_per_item:
          - {name: level, type: dropdown, options: ["Low", "Medium", "High"]}
          - {name: mitigation, type: text}
          
      cost_estimation:
        fields:
          - {name: integration_days, type: number, label: "Initial integration (eng-days)"}
          - {name: daily_rate, type: currency, label: "Daily rate ($)"}
          - {name: team_size, type: number, label: "Team members for learning"}
          - {name: learning_days, type: number, label: "Learning days per person"}
          - {name: maintenance_hours, type: number, label: "Monthly maintenance (hours)"}
          - {name: hourly_rate, type: currency, label: "Hourly rate ($)"}
          - {name: upgrade_days, type: number, label: "Annual upgrade (days)"}
        calculated:
          - name: year1_cost
            formula: "(integration_days * daily_rate) + (team_size * learning_days * daily_rate) + (maintenance_hours * 12 * hourly_rate)"
            label: "Year 1 Total"
          - name: ongoing_cost
            formula: "(maintenance_hours * 12 * hourly_rate) + (upgrade_days * daily_rate)"
            label: "Ongoing Annual"
            
      recommendation:
        type: calculated
        formula: |
          required_caps = [c for c in capabilities if c.required]
          missing = [c for c in required_caps if not c.supported]
          avg_maturity = AVG(capabilities.*.maturity)
          
          IF(LEN(missing) > 0, "DO_NOT_ADOPT",
          IF(avg_maturity >= 4, "ADOPT",
          IF(avg_maturity >= 3, "ADOPT_WITH_CAUTION", "DO_NOT_ADOPT")))
```

---

## Tool 2: RFP Template

```yaml
tool_id: rfp_template
format: document_template
output: Google Docs, Word, or Markdown

applicability:
  include: ["vendor_product", "managed_opensource", "cloud_hosted"]
  exclude: ["self_hosted_opensource", "framework", "standard", "model", "model_runtime", "repository"]

template:
  title: "Request for Proposal: [PROJECT_NAME]"
  
  sections:
    - id: cover
      title: "Cover Page"
      content: |
        # Request for Proposal
        
        **Project:** [PROJECT_NAME]
        **Issuing Organization:** [ORG_NAME]
        **Issue Date:** [DATE]
        **Response Deadline:** [DEADLINE]
        **Contact:** [CONTACT_NAME] ([CONTACT_EMAIL])
        
    - id: intro
      title: "1. Introduction"
      length: "1 page"
      content: |
        ## 1. Introduction
        
        ### 1.1 Project Overview
        [BRIEF_DESCRIPTION]
        
        ### 1.2 Timeline
        - RFP Issue: [DATE]
        - Questions Due: [DATE]
        - Responses Due: [DATE]
        - Evaluation: [DATE_RANGE]
        - Selection: [DATE]
        - POC Start: [DATE]
        
        ### 1.3 Evaluation Criteria
        Responses will be evaluated on:
        - INPACT™ Framework (technical capabilities)
        - GOALS™ Framework (operational readiness)
        - Commercial terms
        
        ### 1.4 Submission Instructions
        [SUBMISSION_DETAILS]

    - id: company
      title: "2. Company Information"
      length: "1 page"
      fields:
        - "Company background and history"
        - "Relevant experience in [INDUSTRY]"
        - "Customer references (minimum 3)"
        - "Financial stability indicators"
        - "Key personnel for this engagement"

    - id: inpact
      title: "3. INPACT™ Technical Requirements"
      length: "3-4 pages"
      conditional: true
      condition: "Show questions only for dimensions applicable to target_layer"
      subsections:
        - id: instant
          title: "3.1 Instant Response (I)"
          visible_when: "layer in [L1, L2, L4, L7]"
          questions:
            - "What is your P95 query latency at 10K, 100K, 1M queries/day?"
            - "Describe your caching strategy and cache hit rates."
            - "How does performance degrade under 2x, 5x, 10x load?"
            
        - id: natural
          title: "3.2 Natural Language (N)"
          visible_when: "layer in [L3, L4, L7]"
          questions:
            - "What semantic accuracy metrics do you report?"
            - "Which embedding models do you support?"
            - "How do you handle domain-specific terminology?"
            
        - id: permitted
          title: "3.3 Permission Control (P)"
          visible_when: "layer in [L5, L7]"
          questions:
            - "Do you support ABAC (attribute-based access control)?"
            - "What is your policy evaluation latency?"
            - "Describe your audit trail capabilities."
            
        - id: adaptive
          title: "3.4 Adaptive Learning (A)"
          visible_when: "layer in [L2, L4, L6, L7]"
          questions:
            - "Describe your feedback loop architecture."
            - "What is your approach to model retraining?"
            - "How do you detect and alert on drift?"
            
        - id: contextual
          title: "3.5 Context Integration (C)"
          visible_when: "layer in [L1, L2, L3, L7]"
          questions:
            - "List your connector catalog (data sources)."
            - "Do you support multi-source queries?"
            - "What is your real-time sync latency?"
            
        - id: transparent
          title: "3.6 Transparency (T)"
          visible_when: "layer in [L5, L6, L7]"
          questions:
            - "What explainability features do you provide?"
            - "Describe your decision logging capabilities."
            - "What compliance reports can you generate?"

    - id: goals
      title: "4. GOALS™ Operational Requirements"
      length: "2-3 pages"
      subsections:
        - id: governance
          title: "4.1 Governance (G)"
          questions:
            - "List your compliance certifications (SOC2, ISO27001, etc.)."
            - "Do you offer a HIPAA BAA?"
            - "Describe your audit logging capabilities."
            - "What data residency options do you provide?"
            
        - id: observability
          title: "4.2 Observability (O)"
          questions:
            - "What monitoring dashboards do you provide?"
            - "How does alerting integrate with common tools (PagerDuty, etc.)?"
            - "Can metrics be exported to external systems?"
            
        - id: availability
          title: "4.3 Availability (A)"
          questions:
            - "What is your SLA commitment?"
            - "Describe your support tiers and response times."
            - "What is your incident response process?"
            
        - id: lexicon
          title: "4.4 Lexicon (L)"
          questions:
            - "Provide links to your API documentation."
            - "Which SDKs do you offer?"
            - "What training resources are available?"
            
        - id: solid
          title: "4.5 Solid (S)"
          questions:
            - "How long has your product been in production?"
            - "How many production customers do you have?"
            - "Provide 2-3 case studies in our industry."

    - id: commercial
      title: "5. Commercial Terms"
      length: "1-2 pages"
      fields:
        - "Pricing model (per-seat, per-query, flat, usage-based)"
        - "Pricing tiers and volume discounts"
        - "Contract terms and minimum commitment"
        - "SLA and financial penalties"
        - "Data portability and exit provisions"

    - id: poc
      title: "6. POC Requirements"
      length: "1 page"
      fields:
        - "Proposed POC scope and objectives"
        - "Success criteria"
        - "Timeline (target: 2 weeks)"
        - "Resources required from vendor"
        - "Resources required from customer"

    - id: appendix
      title: "Appendix"
      content:
        - "A. Scoring rubric reference"
        - "B. Required compliance certifications"
        - "C. Technical environment details"
        - "D. Evaluation timeline"
```

---

## Tool 3: POC Test Plan

```yaml
tool_id: poc_template
format: document_template
output: Google Docs, Word, or Markdown

poc_types:
  vendor:
    applies_to: ["vendor_product", "managed_opensource", "cloud_hosted"]
    duration: "2 weeks"
  self_managed:
    applies_to: ["self_hosted_opensource"]
    duration: "2-3 weeks"
  framework:
    applies_to: ["framework"]
    duration: "1-2 weeks"
  benchmark:
    applies_to: ["model"]
    duration: "1 week"
  infrastructure:
    applies_to: ["model_runtime"]
    duration: "1-2 weeks"

template:
  title: "POC Test Plan: [VENDOR_NAME]"
  
  sections:
    - id: overview
      title: "1. POC Overview"
      fields:
        - {name: vendor_name, type: text, label: "Vendor/Product"}
        - {name: entry_type, type: dropdown, label: "Entry Type"}
        - {name: target_layer, type: dropdown, label: "Target Layer"}
        - {name: start_date, type: date, label: "Start Date"}
        - {name: end_date, type: date, label: "End Date"}
        - {name: success_criteria_summary, type: textarea, label: "Success Criteria Summary"}
        - {name: team_members, type: textarea, label: "Team Members & Roles"}

    - id: week1
      title: "2. Week 1: INPACT™ Validation"
      applies_to: ["vendor", "self_managed", "infrastructure"]
      tests:
        - day: "Monday AM"
          test: "Environment Setup"
          criteria: "Vendor environment accessible, credentials working"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked"]}
          notes: {type: textarea}
          
        - day: "Monday PM"
          test: "Baseline Metrics"
          criteria: "Current state performance documented"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked"]}
          notes: {type: textarea}
          
        - day: "Tuesday AM"
          test: "Latency Testing"
          criteria: "<100ms P95 (L1) or <5s P95 (end-to-end)"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked"]}
          actual_value: {type: text, label: "Actual P95"}
          notes: {type: textarea}
          
        - day: "Tuesday PM"
          test: "Throughput Testing"
          criteria: "Meets volume requirements"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked"]}
          actual_value: {type: text, label: "Actual QPS"}
          notes: {type: textarea}
          
        - day: "Wednesday AM"
          test: "Semantic Accuracy"
          criteria: ">85% on domain queries"
          visible_when: "layer in [L3, L4, L7]"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked", "N/A"]}
          actual_value: {type: text, label: "Actual %"}
          notes: {type: textarea}
          
        - day: "Wednesday PM"
          test: "Policy Enforcement"
          criteria: "100% policy application"
          visible_when: "layer in [L5, L7]"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked", "N/A"]}
          notes: {type: textarea}
          
        - day: "Thursday AM"
          test: "Stress Testing"
          criteria: "Graceful degradation at 2x load"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked"]}
          notes: {type: textarea}
          
        - day: "Thursday PM"
          test: "Recovery Testing"
          criteria: "Recovery <15 minutes"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked"]}
          actual_value: {type: text, label: "Actual recovery time"}
          notes: {type: textarea}
          
        - day: "Friday AM"
          test: "Explainability"
          criteria: "Decision rationale available"
          visible_when: "layer in [L4, L5, L6, L7]"
          result: {type: dropdown, options: ["Pass", "Fail", "Blocked", "N/A"]}
          notes: {type: textarea}
          
        - day: "Friday PM"
          test: "Week 1 Review"
          criteria: "Findings documented, Week 2 plan confirmed"
          notes: {type: textarea}

    - id: week2_vendor
      title: "3. Week 2: GOALS™ + Integration (Vendor)"
      applies_to: ["vendor"]
      tests:
        - {day: "Monday AM", test: "Layer Integration", criteria: "Adjacent layer latency <500ms"}
        - {day: "Monday PM", test: "Data Flow Validation", criteria: "End-to-end consistency verified"}
        - {day: "Tuesday AM", test: "Monitoring Setup", criteria: "Vendor dashboards operational"}
        - {day: "Tuesday PM", test: "Alert Validation", criteria: "Alerts fire correctly"}
        - {day: "Wednesday AM", test: "Support Test", criteria: "Response within SLA"}
        - {day: "Wednesday PM", test: "Documentation Review", criteria: "Adequate for team self-service"}
        - {day: "Thursday AM", test: "Failure Injection", criteria: "Recovery within 15 minutes"}
        - {day: "Thursday PM", test: "Failover Test", criteria: "Automatic failover successful"}
        - {day: "Friday", test: "Go/No-Go Decision", criteria: "Recommendation documented"}

    - id: week2_self_managed
      title: "3. Week 2: Self-Managed Validation"
      applies_to: ["self_managed"]
      note: "Replace vendor tests with internal capability tests"
      tests:
        - {day: "Monday AM", test: "Layer Integration", criteria: "Adjacent layer latency <500ms"}
        - {day: "Monday PM", test: "Data Flow Validation", criteria: "End-to-end consistency verified"}
        - {day: "Tuesday AM", test: "Internal Monitoring", criteria: "YOUR Prometheus/Grafana operational"}
        - {day: "Tuesday PM", test: "Internal Alerting", criteria: "YOUR alerting pipeline works"}
        - {day: "Wednesday AM", test: "Community Support Test", criteria: "Question posted, response within 48h"}
        - {day: "Wednesday PM", test: "Documentation Review", criteria: "Official + community docs adequate"}
        - {day: "Thursday AM", test: "Failure Injection", criteria: "Recovery with YOUR runbooks within 30 min"}
        - {day: "Thursday PM", test: "HA Validation", criteria: "YOUR HA architecture failover works"}
        - {day: "Friday", test: "Ops Readiness", criteria: "Team confident to support"}

    - id: framework_poc
      title: "3. Framework Integration POC"
      applies_to: ["framework"]
      tests:
        - {day: "1-2", test: "Basic Setup", criteria: "Hello world example running"}
        - {day: "2-3", test: "LLM Integration", criteria: "Connected to your L4 provider"}
        - {day: "3-4", test: "Storage Integration", criteria: "Connected to your L1 storage"}
        - {day: "4-5", test: "Simple Agent", criteria: "Basic agent workflow functional"}
        - {day: "5-6", test: "Complex Agent", criteria: "Multi-step workflow functional"}
        - {day: "6-7", test: "Error Handling", criteria: "Graceful failure and recovery"}
        - {day: "7-8", test: "Observability", criteria: "Traces visible in your L6 tools"}
        - {day: "8-9", test: "Performance", criteria: "Meets latency requirements"}
        - {day: "9-10", test: "Team Review", criteria: "Team comfortable with framework"}

    - id: failures
      title: "4. Failure Documentation"
      fields:
        - {name: failure_description, type: textarea, label: "What failed?"}
        - {name: root_cause, type: textarea, label: "Root cause (if known)"}
        - {name: vendor_response, type: textarea, label: "Vendor/community response"}
        - {name: impact, type: dropdown, options: ["Blocker", "Major", "Minor", "None"], label: "Impact on recommendation"}

    - id: summary
      title: "5. POC Summary"
      fields:
        - {name: overall_result, type: dropdown, options: ["Pass", "Fail", "Conditional"]}
        - {name: key_strengths, type: textarea, label: "Key strengths observed"}
        - {name: key_concerns, type: textarea, label: "Key concerns identified"}
        - {name: recommendation, type: dropdown, options: ["Proceed", "Do Not Proceed", "Proceed with Conditions"]}
        - {name: conditions, type: textarea, label: "Conditions for proceeding (if applicable)", visible_when: "recommendation = 'Proceed with Conditions'"}
```

---

## Tool 4: Contract Checklist

```yaml
tool_id: contract_checklist
format: checklist
output: PDF or interactive web

applicability:
  full: ["vendor_product", "managed_opensource", "cloud_hosted"]
  cloud_only: ["self_hosted_opensource"]
  license_only: ["framework", "model"]
  none: ["standard", "model_runtime", "repository"]

sections:
  - id: non_negotiable
    title: "Non-Negotiable Terms"
    rule: "ALL must be Yes to proceed"
    items:
      - id: compliance_cert
        label: "Compliance Certification"
        requirement: "Industry-required (SOC2, ISO27001, etc.)"
        response: {type: dropdown, options: ["Yes", "No", "Partial"]}
        notes: {type: text}
        
      - id: data_residency
        label: "Data Residency"
        requirement: "Data stored in required jurisdiction"
        response: {type: dropdown, options: ["Yes", "No", "Partial"]}
        notes: {type: text}
        
      - id: uptime_sla
        label: "Uptime SLA"
        requirement: "≥99.9% with financial penalties"
        response: {type: dropdown, options: ["Yes", "No", "Partial"]}
        actual_sla: {type: text, label: "Actual SLA offered"}
        notes: {type: text}
        
      - id: exit_clause
        label: "Exit Clause"
        requirement: "Data portability + transition period"
        response: {type: dropdown, options: ["Yes", "No", "Partial"]}
        notes: {type: text}
        
      - id: security_audit
        label: "Security Audit"
        requirement: "Right to audit or certification proof"
        response: {type: dropdown, options: ["Yes", "No", "Partial"]}
        notes: {type: text}

  - id: negotiable
    title: "Negotiable Terms"
    items:
      - id: pricing
        label: "Pricing"
        target: "[Your target]"
        vendor_initial: {type: currency}
        negotiated: {type: currency}
        savings: {type: calculated, formula: "vendor_initial - negotiated"}
        
      - id: payment_terms
        label: "Payment Terms"
        target: "Net 60"
        vendor_initial: {type: text}
        negotiated: {type: text}
        
      - id: commitment
        label: "Commitment Length"
        target: "12 months"
        vendor_initial: {type: text}
        negotiated: {type: text}
        
      - id: support_tier
        label: "Support Tier"
        target: "[Your target tier]"
        vendor_initial: {type: text}
        negotiated: {type: text}
        
    discounts:
      - {type: "Annual Commitment", range: "15-25%", achieved: {type: text}}
      - {type: "Multi-Year (2-3 years)", range: "20-30%", achieved: {type: text}}
      - {type: "Volume", range: "10-20%", achieved: {type: text}}
      - {type: "Pilot Success", range: "10-15%", achieved: {type: text}}
      - {type: "Case Study/Reference", range: "5-10%", achieved: {type: text}}

  - id: red_flags
    title: "Red Flags"
    rule: "ANY Yes = Walk Away"
    items:
      - {label: "Refuses to sign compliance agreement", response: {type: boolean}}
      - {label: "No written SLA", response: {type: boolean}}
      - {label: "No exit clause or >12 month lock-in", response: {type: boolean}}
      - {label: "Cannot confirm data residency", response: {type: boolean}}
      - {label: "Requires unlimited liability from customer", response: {type: boolean}}
      - {label: "No production references available", response: {type: boolean}}

  - id: self_hosted
    title: "Self-Hosted Open-Source Checklist"
    applies_to: ["self_hosted_opensource"]
    note: "No vendor contract, but verify these"
    items:
      - {label: "Open-source license reviewed (commercial use OK)", response: {type: boolean}}
      - {label: "Cloud provider SLA adequate (for infrastructure)", response: {type: boolean}, sla: {type: text}}
      - {label: "Internal SLA defined (since no vendor SLA)", response: {type: boolean}}
      - {label: "Support plan documented (community vs paid)", response: {type: boolean}}
      - {label: "Security responsibility acknowledged (you own it)", response: {type: boolean}}

  - id: framework_license
    title: "Framework/Library License Review"
    applies_to: ["framework"]
    items:
      - {label: "License type", value: {type: dropdown, options: ["MIT", "Apache 2.0", "GPL", "BSD", "Other"]}}
      - {label: "Commercial use permitted", response: {type: boolean}}
      - {label: "Attribution requirements understood", response: {type: boolean}}
      - {label: "Patent grant (if Apache 2.0)", response: {type: boolean}}
      - {label: "Copyleft implications (if GPL)", response: {type: boolean}}
```

---

## Tool 5: Build/Buy/Adopt Matrix

```yaml
tool_id: build_buy_matrix
format: spreadsheet
output: Google Sheets or Excel

sections:
  - id: decision_questions
    title: "Decision Questions"
    fields:
      - name: differentiator
        label: "Is this capability a competitive differentiator?"
        type: dropdown
        options: ["Yes", "No"]
        weight: High
        
      - name: vendor_exists
        label: "Does a proven commercial vendor solution exist?"
        type: dropdown
        options: ["Yes", "No"]
        weight: High
        
      - name: opensource_fits
        label: "Does an open-source solution meet requirements?"
        type: dropdown
        options: ["Yes", "No", "Partially"]
        weight: Medium
        
      - name: internal_expertise
        label: "Do we have internal expertise to build/maintain?"
        type: dropdown
        options: ["Yes", "No"]
        weight: Medium
        
      - name: ops_capability
        label: "Do we have ops capability for open-source?"
        type: dropdown
        options: ["Yes", "No"]
        weight: High
        
      - name: time_critical
        label: "Is time-to-value critical (<3 months)?"
        type: dropdown
        options: ["Yes", "No"]
        weight: High
        
      - name: tech_evolving
        label: "Is the technology rapidly evolving?"
        type: dropdown
        options: ["Yes", "No"]
        weight: Medium

  - id: recommendation
    title: "Recommendation"
    type: calculated
    formula: |
      IF(differentiator="Yes" AND internal_expertise="Yes", "BUILD",
      IF(differentiator="Yes" AND internal_expertise="No", "PARTNER",
      IF(vendor_exists="Yes" AND time_critical="Yes", "BUY",
      IF(opensource_fits IN ["Yes", "Partially"] AND ops_capability="Yes", "ADOPT",
      IF(opensource_fits IN ["Yes", "Partially"] AND ops_capability="No", "BUY (Managed)",
      IF(internal_expertise="Yes", "BUILD", "PARTNER"))))))
    
    options:
      BUILD:
        description: "Build internally"
        when: "Competitive differentiator + internal capability"
        cost_model: "Development + ongoing maintenance"
        
      BUY:
        description: "Purchase commercial solution"
        when: "Commodity need + vendor exists + time-critical"
        cost_model: "License + minimal ops"
        
      ADOPT:
        description: "Adopt open-source"
        when: "OSS fits + internal ops capability"
        cost_model: "$0 license + significant ops"
        
      PARTNER:
        description: "Engage implementation partner"
        when: "Need expertise we don't have"
        cost_model: "Consulting + knowledge transfer"

  - id: tco_comparison
    title: "TCO Comparison"
    columns: ["BUILD", "BUY", "ADOPT", "PARTNER"]
    rows:
      - {name: "Initial Implementation", type: currency}
      - {name: "Year 1 Operations", type: currency}
      - {name: "Year 2 Operations", type: currency}
      - {name: "Year 3 Operations", type: currency}
      - {name: "3-Year TCO", type: calculated, formula: "SUM(above)"}
      - {name: "GOALS Gap Coverage", type: currency, note: "ADOPT typically $80-150K/year"}
      - {name: "Adjusted TCO", type: calculated, formula: "3-Year TCO + (GOALS Gap * 3)"}

  - id: layer_guidance
    title: "Layer-by-Layer Guidance"
    data:
      L1: {typical: "BUY/ADOPT", commercial: "Pinecone, MongoDB Atlas", opensource: "PostgreSQL, Milvus"}
      L2: {typical: "BUY/ADOPT", commercial: "Confluent, Fivetran", opensource: "Kafka, Debezium"}
      L3: {typical: "BUY/ADOPT", commercial: "AtScale, Cube", opensource: "dbt, Metabase"}
      L4: {typical: "BUY + BUILD prompts", commercial: "OpenAI, Anthropic", opensource: "Ollama + OSS models"}
      L5: {typical: "BUY", commercial: "Immuta, Privacera", opensource: "OPA, Ranger"}
      L6: {typical: "BUY/ADOPT", commercial: "Datadog, Splunk", opensource: "Prometheus/Grafana"}
      L7: {typical: "ADOPT + BUILD", commercial: "(few exist)", opensource: "LangChain, LlamaIndex"}
```

---

## Tool 6: Budget Worksheet

```yaml
tool_id: budget_worksheet
format: spreadsheet
output: Google Sheets or Excel

sections:
  - id: track_selection
    title: "Track Selection"
    options:
      open_source:
        name: "Open-Source Track"
        budget_range: "$190K-$400K"
        timeline: "16 weeks"
        engineering: "High (required)"
        ops_burden: "High"
        goals_gap: "$80-150K/year"
        
      hybrid:
        name: "Hybrid Track"
        budget_range: "$460K-$910K"
        timeline: "14 weeks"
        engineering: "Medium"
        ops_burden: "Medium"
        goals_gap: "$30-60K/year"
        
      commercial:
        name: "Commercial Track"
        budget_range: "$890K-$1.5M"
        timeline: "12 weeks"
        engineering: "Low-Medium"
        ops_burden: "Low"
        goals_gap: "$0-20K/year"
        
    selection: {type: dropdown, options: ["Open-Source", "Hybrid", "Commercial"]}

  - id: phase_budget
    title: "Budget by Phase"
    phases:
      - {phase: "Foundation", weeks: "1-4", layers: "L1-L2", pct_range: "35-40%", amount: {type: currency}}
      - {phase: "Intelligence", weeks: "5-7", layers: "L3-L4", pct_range: "30-35%", amount: {type: currency}}
      - {phase: "Trust", weeks: "8-10", layers: "L5-L7", pct_range: "25-30%", amount: {type: currency}}
    total: {type: calculated, formula: "SUM(amounts)"}

  - id: layer_budget
    title: "By-Layer Breakdown"
    rows:
      - {layer: "L1: Storage", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}
      - {layer: "L2: Data Fabric", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}
      - {layer: "L3: Semantic", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}
      - {layer: "L4: Intelligence", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}
      - {layer: "L5: Governance", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}
      - {layer: "L6: Observability", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}
      - {layer: "L7: Orchestration", vendor: {type: text}, implementation: {type: currency}, monthly: {type: currency}, annual: {type: calculated}}

  - id: l4_special
    title: "L4 Intelligence: Special Cost Models"
    note: "L4 has different cost structures"
    options:
      api:
        name: "Commercial LLM API (BUY)"
        fields:
          - {name: "API usage (tokens)", monthly: {type: currency}}
          - {name: "Fine-tuning (one-time)", amount: {type: currency}}
          - {name: "Embedding API", monthly: {type: currency}}
        total_monthly: {type: calculated}
        total_annual: {type: calculated}
        
      self_hosted:
        name: "Self-Hosted Models (ADOPT)"
        fields:
          - {name: "GPU infrastructure", monthly: {type: currency}}
          - {name: "Model serving ops", monthly: {type: currency}}
          - {name: "Fine-tuning compute", amount: {type: currency}}
          - {name: "MLOps/monitoring", monthly: {type: currency}}
        total_monthly: {type: calculated}
        total_annual: {type: calculated}
        
    guidance: |
      Use API (BUY) when: Variable workloads, need vendor SLA, limited ML ops
      Use Self-Host (ADOPT) when: Data privacy required, predictable high volume, have ML ops

  - id: l7_special
    title: "L7 Orchestration: Framework Costs"
    note: "Frameworks have $0 license but significant engineering cost"
    fields:
      - {name: "Initial integration", days: {type: number}, rate: {type: currency}, total: {type: calculated}}
      - {name: "Team learning", people: {type: number}, days: {type: number}, rate: {type: currency}, total: {type: calculated}}
      - {name: "Custom development", days: {type: number}, rate: {type: currency}, total: {type: calculated}}
      - {name: "Testing/validation", days: {type: number}, rate: {type: currency}, total: {type: calculated}}
    year1_total: {type: calculated}
    ongoing_annual:
      - {name: "Maintenance", hours_per_month: {type: number}, rate: {type: currency}, total: {type: calculated}}
      - {name: "Upgrades", days_per_year: {type: number}, rate: {type: currency}, total: {type: calculated}}
    reality_check: "Budget $50-150K in engineering time, not software cost"

  - id: goals_gap
    title: "GOALS Gap Budget"
    note: "Add if using ADOPT (open-source) or CONDITIONAL vendors"
    by_dimension:
      - {dimension: "G (Governance)", cost_range: "$20-50K", your_cost: {type: currency}}
      - {dimension: "O (Observability)", cost_range: "$10-30K", your_cost: {type: currency}}
      - {dimension: "A (Availability)", cost_range: "$30-80K", your_cost: {type: currency}}
      - {dimension: "L (Lexicon)", cost_range: "$5-15K", your_cost: {type: currency}}
      - {dimension: "S (Solid)", cost_range: "$10-20K", your_cost: {type: currency}}
    total: {type: calculated, formula: "SUM(your_cost)"}
```

---

## Tool 7: Vendor Database

```yaml
tool_id: vendor_database
format: web_app
output: Airtable, Notion, or custom web app
update_schedule: "Quarterly"

schema:
  tables:
    - name: vendors
      fields:
        - {name: id, type: auto_increment, primary_key: true}
        - {name: entry_name, type: text, required: true, label: "Name"}
        - {name: product_name, type: text, required: true, label: "Product"}
        - {name: entry_type, type: enum, options: ["Vendor Product", "Managed Open-Source", "Cloud Provider Hosted", "Self-Hosted Open-Source", "Framework", "Standard", "Model", "Model Runtime", "Repository/Registry"], required: true}
        - {name: deployment_model, type: enum, options: ["SaaS", "Managed Cloud", "Self-Hosted", "Local"]}
        - {name: primary_layer, type: enum, options: ["L1", "L2", "L3", "L4", "L5", "L6", "L7", "Foundational"], required: true}
        - {name: secondary_layers, type: multi_enum, options: ["L1", "L2", "L3", "L4", "L5", "L6", "L7"]}
        - {name: dependencies, type: multi_relation, relation: vendors, label: "Requires"}
        - {name: maturity_level, type: enum, options: ["Research Project", "Beta", "Production", "Mature"]}
        - {name: inpact_scores, type: json, schema: {I: int, N: int, P: int, A: int, C: int, T: int}}
        - {name: inpact_total, type: computed, formula: "SUM(applicable scores based on layer)"}
        - {name: inpact_max, type: computed, formula: "LOOKUP(primary_layer, layers.max_inpact_points)"}
        - {name: inpact_pct, type: computed, formula: "(inpact_total / inpact_max) * 100", format: "percent"}
        - {name: goals_scores, type: json, schema: {G: int, O: int, A: int, L: int, S: int}}
        - {name: goals_total, type: computed, formula: "SUM(goals_scores)"}
        - {name: goals_pct, type: computed, formula: "(goals_total / 25) * 100", format: "percent"}
        - {name: recommendation, type: computed, formula: "calculate_recommendation(...)"}
        - {name: architecture_fit, type: boolean}
        - {name: compliance_certs, type: multi_enum, options: ["SOC2", "ISO27001", "HIPAA BAA", "GDPR", "FedRAMP", "None", "N/A"]}
        - {name: pricing_model, type: enum, options: ["Per-seat", "Per-query", "Flat", "Usage-based", "Open-Source", "Free"]}
        - {name: track_fit, type: multi_enum, options: ["Open-Source", "Hybrid", "Commercial"]}
        - {name: gap_budget, type: computed, formula: "calculate_gap_budget(goals_scores)", format: "currency"}
        - {name: last_evaluated, type: date, required: true}
        - {name: notes, type: long_text}
        - {name: product_url, type: url}
        - {name: github_url, type: url}
        - {name: license, type: text}

views:
  - name: "All Vendors"
    type: table
    default_sort: "entry_name ASC"
    
  - name: "By Layer"
    type: table
    group_by: "primary_layer"
    
  - name: "By Entry Type"
    type: table
    group_by: "entry_type"
    
  - name: "Recommended"
    type: table
    filter: "recommendation = 'RECOMMEND'"
    
  - name: "Conditional (Review Gap)"
    type: table
    filter: "recommendation = 'CONDITIONAL'"
    columns: ["entry_name", "primary_layer", "inpact_pct", "goals_pct", "gap_budget"]
    
  - name: "Frameworks"
    type: table
    filter: "entry_type = 'Framework'"
    columns: ["entry_name", "maturity_level", "github_url", "license"]
    
  - name: "By Compliance"
    type: table
    filter_input: "compliance_certs"
    
  - name: "Recently Updated"
    type: table
    sort: "last_evaluated DESC"
    limit: 20
```

---

# PART 3: SPECIAL CASES

```yaml
special_cases:
  dependencies:
    description: "Technologies that require other technologies"
    examples:
      - {tech: "Debezium", requires: "Apache Kafka", note: "Evaluate Kafka separately"}
      - {tech: "LangChain", requires: "LLM provider", note: "Must have L4 selected"}
      - {tech: "dbt", requires: "Data warehouse", note: "Must have L1 selected"}
    handling: |
      1. Score the technology on its own dimensions
      2. Document dependencies in the database
      3. Evaluate each dependency separately
      4. Calculate combined TCO

  bundles:
    description: "Technologies commonly deployed together"
    examples:
      - {bundle: "Prometheus + Grafana", layer: "L6"}
      - {bundle: "ELK Stack", layer: "L6"}
    handling: |
      Options:
      1. Score separately (flexibility)
      2. Score as combined entry (simplicity)
      3. Use managed bundle if available

  multi_purpose_platforms:
    description: "Providers offering multiple products"
    examples:
      - provider: "Hugging Face"
        products: ["Hub", "Inference Endpoints", "Transformers"]
      - provider: "Databricks"
        products: ["Lakehouse", "Streaming", "MLflow"]
    handling: "Create separate entries per product"

  identity_auth:
    description: "Foundational infrastructure outside 7 layers"
    examples: ["Keycloak", "Auth0", "Okta"]
    handling: |
      - Use primary_layer = "Foundational"
      - Evaluate with standard vendor criteria
      - Note relationship to L5

  straddling:
    description: "Technologies that span multiple layers"
    examples:
      - {tech: "dbt", layers: ["L2", "L3"], guidance: "Choose based on primary use"}
      - {tech: "Snowflake", layers: ["L1", "L2", "L4"], guidance: "Evaluate each use separately"}
    handling: "Score by primary use, document secondary uses"
```

---

# PART 4: IMPLEMENTATION NOTES

```yaml
implementation:
  tech_stack:
    spreadsheets: 
      tools: ["Tool 1", "Tool 5", "Tool 6"]
      platform: "Google Sheets with Apps Script"
      
    documents:
      tools: ["Tool 2", "Tool 3"]
      platform: "Google Docs with template variables"
      
    checklists:
      tools: ["Tool 4"]
      platform: "PDF or interactive web form"
      
    database:
      tools: ["Tool 7"]
      platform: "Airtable, Notion, or React + Supabase"

  data_flow:
    - {from: "Tool 1 (Scorecard)", to: ["Tool 5", "Tool 6", "Tool 7"]}
    - {from: "Tool 2 (RFP)", to: ["Tool 3"]}
    - {from: "Tool 3 (POC)", to: ["Tool 1", "Tool 4"]}
    - {from: "Tool 7 (Database)", to: ["All (reference)"]}

  user_workflow:
    1: "Identify Entry Type and Layer"
    2: "If vendor → Tool 2 (RFP)"
    3: "Tool 3 (POC) for validation"
    4: "Tool 1 (Scorecard) to record results"
    5: "If CONDITIONAL → Tab 8 (Gap Analysis)"
    6: "Tool 5 (Build/Buy) for decision"
    7: "Tool 6 (Budget) for planning"
    8: "If proceeding → Tool 4 (Contract)"
    9: "Tool 7 (Database) to record decision"
```
