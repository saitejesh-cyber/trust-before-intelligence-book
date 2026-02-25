# Compliance Navigator  - Knowledge Base

**Book:** Trust Before Intelligence
**Purpose:** Comprehensive compliance framework reference for AI agent deployments
**Date:** January 2026

---

## IMPORTANT DISCLAIMER

**This information is for educational purposes only and does not constitute legal advice.**

Consult with your organization's legal counsel, compliance officer, and relevant regulatory experts before deploying AI agents. Regulations are complex, subject to interpretation, and change over time.

---

## Overview

This knowledge base covers **30 compliance categories** with **200+ frameworks** relevant to AI agent deployments. It is organized to help you:

1. **Identify** which regulations apply to your situation
2. **Understand** the key requirements of each framework
3. **Map** compliance requirements to the 7-layer architecture
4. **Implement** controls to achieve compliance
5. **Prepare** for audits and assessments

---

# THE 30 COMPLIANCE CATEGORIES

## Category 1: DATA PRIVACY
*How personal data is collected, used, stored, and shared.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **GDPR** | EU/EEA | All personal data | Consent, data subject rights, DPO, 72-hr breach notification, privacy by design |
| **CCPA/CPRA** | California | Consumer data | Right to know, delete, opt-out, sensitive data, private right of action |
| **VCDPA** | Virginia | Consumer data | Controller/processor distinction, data protection assessments |
| **CPA** | Colorado | Consumer data | Universal opt-out, data protection assessments |
| **CTDPA** | Connecticut | Consumer data | Similar to CPA |
| **TDPSA** | Texas | Consumer data | Texas-specific requirements |
| **LGPD** | Brazil | Personal data | Similar to GDPR, ANPD enforcement |
| **PIPEDA** | Canada | Commercial data | Consent, access, accuracy, accountability |
| **PIPL** | China | Personal data | Consent, data localization, cross-border restrictions |
| **APPI** | Japan | Personal data | Purpose limitation, third-party transfer rules |
| **PDPA** | Singapore | Personal data | Consent, access, correction, DNC registry |
| **Privacy Act** | Australia | Personal data | APPs, notifiable data breaches scheme |
| **UK GDPR** | United Kingdom | Personal data | Post-Brexit GDPR equivalent, ICO enforcement |
| **DPDP Act** | India | Digital personal data | Consent, data fiduciary obligations, localization |

### AI Agent Requirements
- Obtain valid consent before processing personal data
- Implement data subject rights (access, deletion, portability)
- Minimize data collection to what's necessary
- Document lawful basis for processing
- Enable user opt-out mechanisms
- Implement privacy by design in agent architecture

### Layer Mapping
| Requirement | Layer | Implementation |
|-------------|-------|----------------|
| Consent Management | Layer 7 | Consent capture workflows |
| Data Subject Rights | Layer 7 | Request handling automation |
| Data Minimization | Layer 4, 5 | Query filtering, ABAC |
| Privacy by Design | All Layers | Architecture decisions |

---

## Category 2: HEALTH DATA
*Protected health information and medical data.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **HIPAA** | USA | PHI | Privacy Rule, Security Rule, Breach Notification, BAAs |
| **HITECH** | USA | PHI | Enhanced breach notification, EHR incentives |
| **42 CFR Part 2** | USA | Substance abuse | Extra protections for addiction treatment records |
| **HITRUST CSF** | USA (voluntary) | Healthcare | Comprehensive security framework, certification |
| **FDA 21 CFR Part 11** | USA | Pharma/Devices | Electronic records, electronic signatures |
| **EU MDR** | EU | Medical devices | Software as Medical Device (SaMD) requirements |
| **IVDR** | EU | Diagnostics | In-vitro diagnostic device regulations |
| **PHIPA** | Ontario, Canada | Health info | Health information protection |
| **CMIA** | California | Medical info | Medical information confidentiality |
| **GxP** | Global | Life sciences | Good Manufacturing/Lab/Clinical Practice |

### HIPAA Deep Dive

**Three Rules:**
1. **Privacy Rule**  - How PHI can be used and disclosed
2. **Security Rule**  - Technical, physical, administrative safeguards
3. **Breach Notification Rule**  - Requirements when PHI is compromised

**Technical Safeguards (§164.312):**
- Access Control: Unique IDs, MFA, ABAC, emergency access
- Audit Logging: 100% PHI access logged, 6-year retention, immutable
- Encryption: At rest (AES-256) and in transit (TLS 1.2+)
- Authentication: Strong passwords, MFA required

**Administrative Safeguards (§164.308):**
- Risk assessment completed
- Workforce training (HIPAA + agent-specific)
- Incident response plan
- Contingency/disaster recovery plan

**AI Agent-Specific Requirements:**
- BAAs with ALL vendors (LLM providers, vector DBs, etc.)
- HITL for clinical decisions (mandatory)
- De-identification for training data (18 identifiers)
- Bias testing (<10% disparate impact)
- No PHI in logs (use UUIDs only)

### Penalties
- Civil: $100-$1.5M per violation type/year
- Criminal: Up to $250K and 10 years imprisonment

---

## Category 3: FINANCIAL DATA
*Banking, payments, and financial services data.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **GLBA** | USA | Consumer financial | Privacy notice, safeguards rule, pretexting protection |
| **PCI-DSS** | Global | Cardholder data | 12 requirements, SAQ or QSA assessment |
| **SOX** | USA | Public companies | Financial controls, audit trails, CEO/CFO certification |
| **FFIEC Guidelines** | USA | Banking IT | IT examination handbook, cybersecurity assessment |
| **BSA/AML** | USA | Financial | Anti-money laundering, suspicious activity reports |
| **SEC Regulations** | USA | Securities | Cybersecurity disclosure, Reg S-P, Reg S-ID |
| **FINRA Rules** | USA | Broker-dealers | Record retention, supervision, cybersecurity |
| **MiFID II** | EU | Financial | Transaction reporting, best execution |
| **PSD2** | EU | Payments | Strong customer authentication, open banking |
| **DORA** | EU | Financial | Digital operational resilience |

### PCI-DSS Overview
**12 Requirements:**
1. Install and maintain a firewall
2. No vendor-supplied default passwords
3. Protect stored cardholder data
4. Encrypt transmission of cardholder data
5. Protect against malware
6. Develop secure systems
7. Restrict access on need-to-know
8. Identify and authenticate access
9. Restrict physical access
10. Track and monitor all access
11. Regularly test security systems
12. Maintain information security policy

**AI Agent Note:** Agents should NEVER access raw card numbers. Use tokenization.

---

## Category 4: EDUCATION DATA
*Student and educational records.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **FERPA** | USA | Student records | Parental rights, directory information, consent |
| **COPPA** | USA | Children under 13 | Verifiable parental consent, data minimization |
| **SOPIPA** | California | Student data | EdTech restrictions, no targeted advertising |
| **State Student Privacy Laws** | Various US States | Student data | Additional state-specific requirements |

### AI Agent Requirements
- Parental consent for K-12 student data
- No behavioral targeting or advertising
- Data deletion upon request
- Transparency about data use
- Age verification mechanisms

---

## Category 5: GOVERNMENT & SECURITY
*Federal, defense, and critical infrastructure.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **FedRAMP** | USA Federal | Cloud services | Security authorization, continuous monitoring, 3PAO |
| **FISMA** | USA Federal | Federal IT | Risk management framework, security controls |
| **NIST 800-53** | USA Federal | Security controls | Comprehensive control catalog (1000+ controls) |
| **NIST 800-171** | USA | CUI | Controlled unclassified information (110 controls) |
| **CMMC** | USA DoD | Defense contractors | Cybersecurity maturity levels (1-3) |
| **ITAR** | USA | Defense exports | Export controls for defense articles |
| **DFARS** | USA DoD | Defense contracts | Defense acquisition cybersecurity |
| **CJIS** | USA | Law enforcement | Criminal justice information security |
| **StateRAMP** | USA States | State cloud | State-level FedRAMP equivalent |
| **NIS2** | EU | Critical infrastructure | Network and information security directive |
| **FIPS 140-2/3** | USA | Cryptography | Cryptographic module validation |

### FedRAMP Impact Levels
| Level | Data Sensitivity | Examples |
|-------|------------------|----------|
| Low | Publicly releasable | Public websites |
| Moderate | Controlled unclassified | Most agency data |
| High | Life/safety, economic, national security | Critical systems |

---

## Category 6: AI-SPECIFIC REGULATIONS
*Regulations specifically targeting AI systems.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **EU AI Act** | EU | AI systems | Risk categories, human oversight, transparency |
| **Colorado AI Act** | Colorado | High-risk AI | Disclosure, impact assessments, opt-out |
| **NYC Local Law 144** | NYC | Employment AI | Bias audits for automated hiring tools |
| **Illinois BIPA** | Illinois | Biometrics | Biometric data consent |
| **NIST AI RMF** | USA (voluntary) | AI risk | AI risk management framework |
| **UNESCO AI Ethics** | Global (voluntary) | Ethics | Ethical AI principles |
| **OECD AI Principles** | Global (voluntary) | Policy | AI policy guidelines |
| **Canada AIDA** | Canada (proposed) | AI | Artificial Intelligence and Data Act |
| **China AI Regulations** | China | AI | Algorithm recommendations, deepfakes, generative AI |

### EU AI Act Risk Categories

| Category | Examples | Requirements |
|----------|----------|--------------|
| **Unacceptable** | Social scoring, manipulation | PROHIBITED |
| **High Risk** | Healthcare, employment, law enforcement | Strict requirements |
| **Limited Risk** | Chatbots, emotion recognition | Transparency only |
| **Minimal Risk** | Spam filters, games | No requirements |

**High-Risk Requirements (Articles 8-15):**
- Human oversight (Article 14)
- Technical documentation (Article 11)
- Record-keeping (Article 12)
- Transparency (Article 13)
- Accuracy, robustness, security (Article 15)
- Risk management (Article 9)
- Data governance (Article 10)

**Penalties:**
- Prohibited AI: €35M or 7% global revenue
- High-risk non-compliance: €15M or 3% global revenue

---

## Category 7: INFORMATION SECURITY
*General security standards and frameworks.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **SOC 2** | Global | Trust services | Security, Availability, Processing Integrity, Confidentiality, Privacy |
| **ISO 27001** | Global | ISMS | Information security management system certification |
| **ISO 27701** | Global | PIMS | Privacy information management extension |
| **ISO 27017** | Global | Cloud | Cloud security controls |
| **ISO 27018** | Global | Cloud PII | Cloud privacy controls |
| **CSA STAR** | Global | Cloud | Cloud security assessment |
| **CIS Controls** | Global | Security | Critical security controls (18 controls) |
| **NIST CSF** | USA | Cybersecurity | Identify, Protect, Detect, Respond, Recover |

### SOC 2 Trust Service Criteria

| Criteria | Description | AI Agent Relevance |
|----------|-------------|-------------------|
| **Security** | Protection from unauthorized access | ABAC, encryption, MFA |
| **Availability** | System accessible as committed | SLAs, disaster recovery |
| **Processing Integrity** | Processing complete and accurate | Data quality, validation |
| **Confidentiality** | Information protected as committed | Encryption, access control |
| **Privacy** | Personal information handled properly | Consent, data minimization |

**SOC 2 Type I vs Type II:**
- Type I: Point-in-time assessment (snapshot)
- Type II: Period of time (6-12 months)  - more valuable

---

## Category 8: INDUSTRY-SPECIFIC
*Sector-specific regulations.*

### Key Frameworks

| Framework | Industry | Key Requirements |
|-----------|----------|------------------|
| **NERC CIP** | Electric Utilities | Critical infrastructure protection (13 standards) |
| **IATF 16949** | Automotive | Quality management for automotive |
| **AS9100** | Aerospace | Quality management for aerospace |
| **FDA Regulations** | Food, Drugs, Devices | Product safety, manufacturing standards |
| **EPA Regulations** | Environmental | Environmental protection, reporting |
| **FCC Regulations** | Telecommunications | CPNI, communications regulations |
| **ABA Model Rules** | Legal | Attorney ethics, confidentiality |
| **AICPA Standards** | Accounting | Auditor independence, ethics |

---

## Category 9: CONSUMER PROTECTION
*Consumer rights and fair practices.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **FTC Act Section 5** | USA | Unfair practices | Unfair/deceptive acts, data security |
| **CAN-SPAM** | USA | Email | Commercial email rules, opt-out |
| **TCPA** | USA | Telephone | Robocall restrictions, consent |
| **FCRA** | USA | Credit reporting | Accuracy, disputes, adverse action |
| **ECOA** | USA | Credit | Equal credit opportunity, non-discrimination |
| **ADA Title III** | USA | Accessibility | Accessible services for disabled |
| **WCAG** | Global | Web accessibility | Web content accessibility guidelines |

### AI Agent Requirements
- No deceptive AI practices (FTC)
- Disclose when users are interacting with AI
- Provide opt-out mechanisms
- Ensure accessibility compliance
- Non-discriminatory outcomes

---

## Category 10: INTERNATIONAL & CROSS-BORDER
*Data transfer and international compliance.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **EU-US Data Privacy Framework** | EU-US | Adequacy decision for US transfers |
| **SCCs (Standard Contractual Clauses)** | EU | Cross-border data transfer contracts |
| **BCRs (Binding Corporate Rules)** | EU Multinationals | Intra-group data transfers |
| **APEC CBPR** | Asia-Pacific | Cross-border privacy rules certification |
| **OFAC** | USA | Sanctions compliance |
| **FCPA** | USA | Foreign corrupt practices prohibition |
| **UK Bribery Act** | UK | Anti-bribery |

### AI Agent Requirements
- Identify where data is processed and stored
- Implement appropriate transfer mechanisms
- Screen against sanctions lists
- Data localization compliance (China, Russia, etc.)

---

## Category 11: EMPLOYMENT & HR
*Workplace and employee data.*

### Key Frameworks

| Framework | Geography | Scope | Key Requirements |
|-----------|-----------|-------|------------------|
| **EEOC Guidelines** | USA | Employment | AI in hiring non-discrimination |
| **ADA (Employment)** | USA | Disability | Reasonable accommodation |
| **FLSA** | USA | Wages | Wage and hour records |
| **OSHA** | USA | Safety | Workplace safety records |
| **WARN Act** | USA | Layoffs | 60-day layoff notification |
| **State Employment Laws** | Various | Employment | Background checks, salary history bans |
| **GDPR (Employee Data)** | EU | Employee data | Consent, monitoring limits |

### AI in Hiring
- NYC Local Law 144: Bias audits required
- EEOC: AI must not discriminate
- Document AI decision rationale
- Human review of AI recommendations

---

## Category 12: AUDIT & ATTESTATION
*Third-party assessments and certifications.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **SOC 1 (SSAE 18)** | Financial controls | Controls over financial reporting |
| **SOC 2 Type I** | Security | Point-in-time assessment |
| **SOC 2 Type II** | Security | 6-12 month observation period |
| **SOC 3** | Security | Public-facing SOC 2 summary |
| **ISO 27001 Certification** | ISMS | Third-party certification audit |
| **PCI QSA Assessment** | Payments | Qualified security assessor |
| **FedRAMP 3PAO** | Government | Third-party assessment organization |
| **HITRUST Certification** | Healthcare | HITRUST CSF certification |

---

## Category 13: ETHICAL AI & RESPONSIBLE AI
*Fairness, bias, transparency, explainability.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **IEEE Ethically Aligned Design** | Global | Ethical AI principles |
| **AI Fairness 360 (IBM)** | Open Source | Bias detection/mitigation tools |
| **Model Cards (Google)** | Open Source | Model documentation standards |
| **Datasheets for Datasets** | Open Source | Dataset documentation |
| **Microsoft Responsible AI** | Voluntary | Fairness, reliability, privacy, inclusiveness |
| **EU Ethics Guidelines for AI** | EU | Trustworthy AI requirements |
| **Algorithmic Accountability** | Various | Audit requirements for algorithms |
| **AI Bill of Rights (OSTP)** | USA (voluntary) | Safe, effective, non-discriminatory AI |

### Key Principles
1. **Fairness**  - No discriminatory outcomes
2. **Transparency**  - Explainable decisions
3. **Accountability**  - Clear responsibility
4. **Privacy**  - Data protection
5. **Safety**  - No harm to users
6. **Human Oversight**  - Meaningful human control

### AI Agent Requirements
- Bias testing across demographics
- Explainability for high-stakes decisions
- Regular algorithmic audits
- Documentation of model behavior
- Feedback mechanisms for users

---

## Category 14: INTELLECTUAL PROPERTY
*Copyright, patents, trade secrets, licensing.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **Copyright Law** | Global | Training data rights, output ownership |
| **Patent Law** | Global | AI-generated inventions |
| **Trade Secret Law** | Global | Model protection, proprietary algorithms |
| **Open Source Licenses** | Global | GPL, MIT, Apache compliance |
| **Creative Commons** | Global | Content licensing for training data |
| **DMCA** | USA | Safe harbor, takedown procedures |
| **EU Copyright Directive** | EU | Text and data mining exceptions |

### AI Agent Considerations
- Training data licensing rights
- Who owns AI-generated content?
- Open source model compliance (LLaMA, etc.)
- Trade secret protection for fine-tuned models
- Patent eligibility for AI inventions

---

## Category 15: CONTENT MODERATION & SAFETY
*Harmful content, misinformation, illegal content.*

### Key Frameworks

| Framework | Geography | Key Requirements |
|-----------|-----------|------------------|
| **Digital Services Act (DSA)** | EU | Content moderation, transparency, illegal content |
| **Section 230** | USA | Platform liability protections |
| **Online Safety Act** | UK | Duty of care, harmful content removal |
| **NetzDG** | Germany | 24-hour hate speech removal |
| **CSAM Laws** | Global | Mandatory reporting of child abuse material |
| **Terrorist Content Regulation** | EU | 1-hour removal requirement |
| **Deepfake Laws** | Various | Synthetic media disclosure |

### AI Agent Requirements
- Content filtering for harmful outputs
- CSAM detection and reporting
- Misinformation guardrails
- Deepfake disclosure
- User reporting mechanisms

---

## Category 16: ACCESSIBILITY
*Ensuring AI is usable by people with disabilities.*

### Key Frameworks

| Framework | Geography | Key Requirements |
|-----------|-----------|------------------|
| **ADA Title III** | USA | Accessible digital services |
| **Section 508** | USA Federal | Federal IT accessibility |
| **WCAG 2.1/2.2** | Global | Web content accessibility guidelines |
| **EN 301 549** | EU | ICT accessibility standard |
| **AODA** | Ontario | Accessibility for Ontarians |
| **EAA** | EU | European Accessibility Act |

### WCAG Levels
- Level A: Minimum accessibility
- Level AA: Standard (most common requirement)
- Level AAA: Enhanced accessibility

### AI Agent Requirements
- Screen reader compatibility
- Keyboard navigation
- Alternative text for images
- Captions for audio
- Cognitive accessibility considerations

---

## Category 17: ENVIRONMENTAL & SUSTAINABILITY
*AI's environmental impact, ESG reporting.*

### Key Frameworks

| Framework | Geography | Key Requirements |
|-----------|-----------|------------------|
| **EU CSRD** | EU | Corporate sustainability reporting |
| **SEC Climate Disclosure** | USA | Climate-related financial disclosures |
| **GHG Protocol** | Global | Carbon emissions measurement |
| **SBTi** | Global | Science-based emissions targets |
| **EU Taxonomy** | EU | Sustainable activities classification |
| **ISO 14001** | Global | Environmental management |

### AI Agent Considerations
- Model training carbon footprint
- Inference energy consumption
- Data center sustainability
- ESG reporting on AI operations

---

## Category 18: RECORDS MANAGEMENT & RETENTION
*How long to keep data, legal holds, destruction.*

### Key Frameworks

| Framework | Scope | Retention Period |
|-----------|-------|------------------|
| **FRCP** | USA Litigation | Legal hold during litigation |
| **SEC Rule 17a-4** | Broker-dealers | 6 years |
| **HIPAA** | Healthcare | 6 years minimum |
| **SOX** | Public companies | 7 years |
| **GDPR** | EU | "No longer than necessary" |
| **State Laws** | Various | State-specific |
| **ISO 15489** | Global | Records management standard |

### AI Agent Requirements
- Audit log retention (regulatory minimum)
- Model version history
- Training data lineage
- Legal hold capabilities
- Secure deletion procedures

---

## Category 19: INCIDENT RESPONSE & BREACH NOTIFICATION
*What to do when things go wrong.*

### Key Frameworks

| Framework | Notification Timeline |
|-----------|----------------------|
| **GDPR** | 72 hours to DPA |
| **HIPAA** | 60 days to individuals |
| **State Breach Laws** | Varies (24 hours to 90 days) |
| **SEC** | 4 days (material incidents) |
| **CIRCIA** | 72 hours to CISA (critical infrastructure) |
| **NIS2** | 24-hour early warning |
| **PCI-DSS** | Immediate to card brands |

### AI Agent Requirements
- Incident detection capabilities
- Breach assessment procedures
- Notification templates ready
- Communication plans
- Post-incident review process

---

## Category 20: THIRD-PARTY & SUPPLY CHAIN
*Vendor management, supply chain security.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **Vendor Risk Management** | Global | Due diligence, ongoing monitoring |
| **SOC 2 for Vendors** | Global | Vendor attestation requirement |
| **NIST 800-161** | USA | Supply chain risk management |
| **EU DORA** | EU Financial | ICT third-party risk |
| **OCC Guidance** | USA Banking | Bank vendor management |
| **ISO 27036** | Global | Supplier security |
| **SBOM** | USA/Global | Software bill of materials |

### AI Agent Requirements
- LLM provider due diligence
- Vector database vendor assessment
- Cloud provider security review
- BAAs/DPAs with all vendors
- SBOM for AI components

---

## Category 21: CONTRACTS & LEGAL
*Agreements, terms of service, liability.*

### Key Frameworks

| Agreement Type | When Required |
|----------------|---------------|
| **DPA (Data Processing Agreement)** | GDPR controller-processor |
| **BAA (Business Associate Agreement)** | HIPAA covered entity-BA |
| **SLA (Service Level Agreement)** | All vendors |
| **Terms of Service** | User-facing applications |
| **Acceptable Use Policy** | AI usage restrictions |
| **AI-Specific Indemnification** | AI output liability |

### AI-Specific Contract Considerations
- Liability for AI outputs
- Accuracy warranties (or disclaimers)
- Data usage rights for training
- Model ownership
- Indemnification for AI decisions

---

## Category 22: INSURANCE & LIABILITY
*Risk transfer and coverage.*

### Key Frameworks

| Insurance Type | Coverage |
|----------------|----------|
| **Cyber Insurance** | Breach costs, business interruption |
| **E&O Insurance** | Professional liability |
| **AI-Specific Insurance** | AI output liability (emerging) |
| **Product Liability** | AI as "product" |
| **D&O Insurance** | Director/officer AI governance |

### AI Agent Considerations
- Does cyber insurance cover AI incidents?
- AI-specific exclusions in policies
- Product vs. service liability
- Director liability for AI governance

---

## Category 23: SECTOR REGULATORS
*Industry-specific oversight bodies.*

### Key Regulators for AI

| Regulator | Scope | AI Focus |
|-----------|-------|----------|
| **FTC** | Consumer protection | AI deception, unfairness |
| **CFPB** | Consumer finance | Fair lending AI |
| **EEOC** | Employment | Hiring AI discrimination |
| **FDA** | Medical | Software as Medical Device |
| **NHTSA** | Automotive | Autonomous vehicles |
| **FAA** | Aviation | Autonomous aircraft |
| **SEC** | Securities | AI disclosure, trading |
| **OCC/FDIC** | Banking | AI risk management |

---

## Category 24: EMERGING REGULATIONS
*Regulations in development or recently enacted.*

### Pending/Recent Frameworks

| Framework | Status | Expected Impact |
|-----------|--------|-----------------|
| **Federal AI Legislation (USA)** | Various bills | Potential federal AI law |
| **State AI Laws** | Expanding | Colorado, Connecticut, etc. |
| **Canada AIDA** | Proposed | AI and Data Act |
| **UK AI Regulation** | Developing | Pro-innovation approach |
| **India AI Rules** | In development | Sector-specific |
| **Global AI Treaty** | Council of Europe | International standards |
| **Foundation Model Regulations** | Discussed | Large model requirements |

---

## Category 25: ANTI-TRUST & COMPETITION
*AI market dominance, bundling, fair competition.*

### Key Frameworks

| Framework | Geography | Key Requirements |
|-----------|-----------|------------------|
| **Sherman Act** | USA | Monopolization prohibition |
| **Clayton Act** | USA | Anti-competitive mergers |
| **FTC Act Section 5** | USA | Unfair methods of competition |
| **EU Competition Law** | EU | Abuse of dominance, mergers |
| **Digital Markets Act (DMA)** | EU | Gatekeeper obligations |

### AI Considerations
- AI model market concentration
- Bundling AI with other services
- Data advantages as competitive moat
- Interoperability requirements

---

## Category 26: NATIONAL SECURITY & EXPORT CONTROLS
*AI export restrictions, dual-use technology.*

### Key Frameworks

| Framework | Geography | Key Requirements |
|-----------|-----------|------------------|
| **EAR (Export Administration Regulations)** | USA | Export controls for dual-use tech |
| **ITAR** | USA | Defense article export controls |
| **CFIUS** | USA | Foreign investment review |
| **EU Dual-Use Regulation** | EU | Export controls |
| **Wassenaar Arrangement** | Multilateral | Conventional arms/dual-use |
| **Entity List** | USA | Prohibited parties |

### AI Export Considerations
- Advanced AI chips export restrictions
- AI model export to certain countries
- Foreign investment in AI companies
- Deemed exports (foreign nationals)

---

## Category 27: HUMAN RIGHTS
*UN principles, surveillance, labor practices.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **UN Guiding Principles** | Global | Business and human rights |
| **UN Global Compact** | Global | 10 principles including human rights |
| **Modern Slavery Acts** | UK, Australia | Supply chain transparency |
| **Uyghur Forced Labor Prevention Act** | USA | Import restrictions |
| **EU AI Act (Prohibited Uses)** | EU | Social scoring, mass surveillance |

### AI Considerations
- AI in surveillance systems
- Facial recognition restrictions
- Labor rights in AI supply chain
- AI and freedom of expression

---

## Category 28: QUALITY MANAGEMENT
*Quality standards for AI systems.*

### Key Frameworks

| Framework | Scope | Key Requirements |
|-----------|-------|------------------|
| **ISO 9001** | Global | Quality management systems |
| **ISO/IEC 42001** | Global | AI management systems (new) |
| **ISO/IEC 25010** | Global | Software quality |
| **Six Sigma** | Global | Process improvement |
| **CMMI** | Global | Capability maturity |

### AI Quality Considerations
- Model quality metrics
- Testing and validation
- Continuous improvement
- Defect tracking for AI outputs

---

## Category 29: PROFESSIONAL LICENSING
*AI practicing regulated professions.*

### Key Frameworks

| Profession | Licensing Body | AI Considerations |
|------------|----------------|-------------------|
| **Medicine** | State medical boards | AI medical advice restrictions |
| **Law** | State bar associations | Unauthorized practice of law |
| **Accounting** | State CPA boards | Financial advice restrictions |
| **Engineering** | State PE boards | Engineering decisions |
| **Financial Advice** | SEC, FINRA | Investment advice restrictions |

### AI Agent Requirements
- Clear disclaimers for regulated domains
- Human professional oversight
- No unauthorized practice claims
- Appropriate licensing for human supervisors

---

## Category 30: WHISTLEBLOWER PROTECTION
*Reporting AI harms and compliance violations.*

### Key Frameworks

| Framework | Geography | Key Requirements |
|-----------|-----------|------------------|
| **SOX Whistleblower** | USA | Protection for reporting fraud |
| **Dodd-Frank** | USA | Financial whistleblower rewards |
| **EU Whistleblower Directive** | EU | Protection for reporting breaches |
| **SEC Whistleblower Program** | USA | Monetary awards |
| **OSHA Whistleblower** | USA | Retaliation protection |

### AI Considerations
- Channels for reporting AI harms
- Protection for AI ethics concerns
- Internal escalation procedures
- External reporting mechanisms

---

# QUICK REFERENCE

## By Industry

| Industry | Primary Categories |
|----------|-------------------|
| **Healthcare** | 2, 1, 6, 7, 13, 19 |
| **Financial Services** | 3, 1, 7, 12, 6, 19 |
| **Government** | 5, 7, 26, 18, 12 |
| **Technology/SaaS** | 7, 1, 6, 12, 14, 20 |
| **Retail/E-commerce** | 1, 3, 9, 16, 15 |
| **Education** | 4, 1, 16, 6 |
| **Manufacturing** | 8, 17, 28, 20 |
| **Legal/Professional** | 29, 21, 18, 13 |

## By AI Agent Type

| Agent Type | Critical Categories |
|------------|---------------------|
| **Healthcare Agents** | 2, 6, 13, 19, 29 |
| **Customer Service Bots** | 1, 9, 15, 16 |
| **HR/Recruiting Agents** | 11, 6, 13, 1 |
| **Financial Advisors** | 3, 29, 6, 9 |
| **Content Generation** | 14, 15, 13, 6 |
| **Multi-Agent Systems** | 7, 19, 18, 20 |

## Layer Mapping Summary

| Category | Primary Layers |
|----------|----------------|
| Data Privacy | L4, L5, L7 |
| Health Data | L5, L6 |
| Financial Data | L5, L6 |
| AI-Specific | L4, L5, L6, L7 |
| Information Security | All |
| Ethical AI | L4, L6 |
| Incident Response | L6, L7 |
| Audit | L5, L6 |