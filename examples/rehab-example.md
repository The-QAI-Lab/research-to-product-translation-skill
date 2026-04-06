# Example: Rehab Tech — ACL Rehabilitation Decision Support Platform

## Input

> "We have a system that combines force plate data, motion capture, and patient-reported outcome measures to estimate ACL rehabilitation readiness for return-to-sport. A physical therapist inputs session data and the system generates a composite readiness score. We have used it with 40 patients over 18 months in a university sports medicine clinic."

---

# Research-to-Product Translation

## 1. Research Concept Summary

A clinician-facing decision support tool for ACL rehabilitation that fuses objective biomechanical data (force plate, motion capture) with patient-reported outcomes to generate a composite return-to-sport readiness score.

Maturity level: Validated method in a single-site clinical setting. The system has been used with real patients by real clinicians. The gap is multi-site validation, regulatory positioning, and productization.

What makes it novel: Most return-to-sport decisions rely on a single metric (limb symmetry index) or clinician judgment alone. This system integrates multiple data streams into a structured, reproducible readiness assessment — reducing variability in clinical decision-making.

---

## 2. Problem Being Solved

Core problem: Return-to-sport decisions after ACL reconstruction are inconsistent across clinicians and institutions. There is no widely adopted, evidence-based, multi-metric standard. Re-injury rates remain high (15–25% in athletes under 25), partly because athletes are cleared too early or based on incomplete data.

Why it matters: ACL re-injury is career-altering for athletes and costly for healthcare systems. A more reliable readiness assessment could reduce re-injury rates, improve patient outcomes, and reduce liability for clinicians.

Current alternatives: Manual limb symmetry testing, single-metric hop tests, subjective clinician judgment, or expensive motion analysis systems that require a dedicated lab and trained operator. No widely adopted software integrates all of these into a structured workflow.

---

## 3. Target Users and Buyers

- End user: Physical therapist or athletic trainer conducting the rehabilitation session and entering assessment data
- Operator/admin: Clinic director or sports medicine program director who configures the system, manages patient rosters, and reviews aggregate outcomes
- Economic buyer: Clinic owner, hospital system, or university sports medicine program director with budget authority
- Influencers/stakeholders: Orthopedic surgeon (who refers patients and may want outcome data), team physician, insurance payers (interested in outcomes data), patients/athletes (must consent and engage)

---

## 4. Value Proposition

Primary: Give physical therapists a structured, data-driven readiness assessment that reduces guesswork in return-to-sport decisions and creates a defensible clinical record.

Secondary:
- Reduce re-injury risk by catching biomechanical deficits that subjective assessment misses
- Create a longitudinal patient outcome record that supports quality improvement and research
- Differentiate the clinic as a technology-forward, evidence-based practice

Why better than current approaches: Existing tools are either single-metric, require expensive dedicated hardware, or are research-grade systems not designed for clinical workflow. This system is designed for the PT's daily workflow and produces a structured, reproducible output.

---

## 5. Product Concept

What the product is: A clinician-facing ACL rehabilitation decision support platform.

Product type: Web application with hardware integrations (force plate, motion capture system) and a structured assessment workflow.

Core user workflow:
1. PT opens patient profile and selects assessment type (e.g., 6-week, 12-week, return-to-sport)
2. System guides PT through standardized data collection protocol (force plate tests, hop tests, PROM questionnaire)
3. Data is entered or auto-ingested from connected hardware
4. System generates a composite readiness score with component breakdown
5. PT reviews score, adds clinical notes, and generates a structured report
6. Report is saved to patient record and optionally shared with referring surgeon or team physician

---

## 6. MVP Definition

Must-have features:
- Patient profile and session history
- Structured assessment workflow (guided data entry for force plate, hop tests, PROMs)
- Composite readiness score with component breakdown
- Trend visualization per patient across sessions
- Clinician notes field
- PDF report export
- Secure patient data storage (HIPAA-compliant)

Nice-to-have (later phases):
- Direct hardware integration (auto-ingest from force plate or motion capture system)
- Referring surgeon portal for outcome sharing
- Aggregate outcomes dashboard for clinic quality improvement
- Benchmarking against normative data
- Insurance documentation support

Explicitly out of scope for v1:
- Automated clinical recommendations or treatment prescriptions
- Real-time motion capture processing
- Consumer-facing patient app
- Predictive re-injury risk scoring (requires larger validated dataset — do not claim this in v1)

---

## 7. Data Requirements

Required inputs:
- Limb symmetry index (force plate or hop test)
- Quadriceps and hamstring strength metrics
- Functional hop test results (single-leg hop, triple hop, crossover hop)
- Patient-reported outcome measures (IKDC, ACL-RSI, or equivalent)
- Session date and weeks post-surgery

Optional/enrichment data:
- Motion capture kinematics (knee valgus, hip drop during landing)
- Pain and swelling ratings
- Surgeon operative notes (graft type, concomitant injuries)
- Return-to-sport outcome (did the patient return? did they re-injure?)

Labels/outcomes needed:
- Actual return-to-sport date
- Re-injury occurrence (for long-term model validation)
- Clinician's final clearance decision

Data collection feasibility: High for the core metrics — these are already collected in standard ACL rehab protocols. The challenge is structured digital capture rather than paper or spreadsheet recording.

Data risks/gaps:
- Re-injury outcome data requires long-term follow-up (6–24 months post-clearance) — this is a gap for model validation
- Normative benchmarks vary by sport, age, and sex — the system should not apply a single threshold universally without disclosure
- Patient data is protected health information — HIPAA compliance is non-negotiable

---

## 8. Technical / System Considerations

Likely architecture:
- Web application (React frontend, Python/FastAPI or Django backend)
- PostgreSQL database with patient data encryption at rest
- PDF generation service for report export
- Optional: hardware SDK integrations for force plate vendors (AMTI, Bertec, Kistler)
- Cloud deployment with HIPAA-compliant hosting (AWS GovCloud, Azure Healthcare, or equivalent BAA-covered environment)

Integration requirements:
- Force plate vendor APIs or SDK (if auto-ingestion is pursued in later phases)
- EHR integration (Epic, Athenahealth) — complex, likely post-MVP
- PROM survey tools (REDCap, or built-in)

Hardware/software dependencies:
- Force plate hardware must be present in the clinic (existing equipment)
- Motion capture integration requires compatible system (Vicon, Qualisys, or markerless alternative)
- Reliable internet connection for cloud-hosted version; offline mode may be needed for some clinic environments

Deployment environment: Cloud-hosted SaaS with HIPAA BAA. On-premise option may be required for hospital system buyers.

Scalability concerns: Patient data volume is manageable. The main scalability challenge is multi-site deployment with consistent data standards across clinicians and hardware configurations.

---

## 9. Regulatory / Privacy / Ethical Considerations

Privacy concerns:
- All patient data is protected health information (PHI) under HIPAA
- Business Associate Agreement (BAA) required with any cloud hosting provider
- Minimum necessary data principle should guide what is collected and retained
- Data retention and deletion policies must be defined

Security concerns:
- Encryption at rest and in transit is required
- Role-based access control — clinicians should only see their own patients
- Audit logging for PHI access
- Penetration testing before launch

Regulatory/compliance considerations:
- This system is likely a clinical decision support (CDS) tool — FDA has guidance on when CDS software requires 510(k) clearance
- If the system makes autonomous treatment recommendations, it may be classified as a Software as a Medical Device (SaMD) — legal and regulatory counsel review is required before launch
- If it is positioned as a documentation and workflow tool that supports (not replaces) clinician judgment, it may fall under FDA's CDS enforcement discretion — but this must be confirmed
- IRB approval required if patient data is used for research or publication

Ethical issues:
- The system must not be used to override clinician judgment — it is a support tool, not a decision-maker
- Patients must consent to data collection and understand how their data is used
- Normative benchmarks must be disclosed — a score that is "normal" for a 25-year-old male soccer player may not be appropriate for a 16-year-old female basketball player

Claims to avoid without validation:
- "Prevents ACL re-injury"
- "Clinically proven to reduce re-injury rates"
- "FDA cleared" (unless cleared)
- "Replaces clinical judgment"
- Any specific re-injury risk percentage without a validated, peer-reviewed study

---

## 10. Pilot Plan

Recommended pilot environment: One university sports medicine clinic or one orthopedic rehabilitation practice with an existing ACL patient population and force plate access

Pilot user group: 3–5 physical therapists, 20–40 ACL rehabilitation patients over the pilot period

Duration: 12–16 weeks (one full rehabilitation cycle for several patients)

Metrics:
- System adoption rate (% of eligible patients assessed using the platform vs. paper/spreadsheet)
- Assessment completion time vs. baseline (is it faster or slower than current workflow?)
- Clinician satisfaction score (end-of-pilot survey)
- Data completeness rate (% of required fields completed per session)
- Number of reports generated and shared with referring providers

Success criteria:
- PTs report the system fits their workflow and produces useful output
- Assessment completion time is not significantly longer than current process
- No data security incidents
- At least 20 complete patient assessment records captured

Operational dependencies:
- HIPAA BAA in place before any patient data is collected
- IT approval from clinic or hospital system
- Patient consent process established
- Staff training completed (target: <2 hours per clinician)

---

## 11. Validation Strategy

What must be validated first: Clinical workflow fit — does the system actually work in a real PT's daily schedule, or does it add burden without perceived value?

Technical validation:
- Data pipeline reliability and accuracy of score calculation
- Report generation correctness
- Security and HIPAA compliance audit

User validation:
- Do PTs find the readiness score interpretable and clinically meaningful?
- Does the structured workflow improve consistency across clinicians?
- Is the report useful for communication with surgeons and referring providers?

Outcome validation:
- Does the composite readiness score correlate with clinician clearance decisions?
- (Long-term) Does use of the system correlate with lower re-injury rates? (Assumption: requires multi-year follow-up data — not a v1 claim)

Business validation:
- Are clinics willing to pay for this as a standalone SaaS tool?
- What is the willingness-to-pay range per clinic or per provider?
- Is the buying decision made by the clinic director, the PT, or the hospital system?

---

## 12. Commercialization Path

Likely business model(s):
- B2B SaaS: Monthly or annual subscription per clinic, tiered by number of providers or patient volume
- Per-assessment pricing: Charge per completed assessment report (aligns cost with usage)
- Enterprise license: Multi-site hospital system or rehabilitation group license

Go-to-market entry point: University sports medicine programs and orthopedic rehabilitation clinics with existing research relationships — they are more likely to adopt early-stage tools and provide outcome data for validation.

Early adopter profile: Evidence-based PT practices with sports medicine focus, existing force plate infrastructure, and a clinician champion who is interested in outcomes research.

Partnership opportunities:
- Force plate vendors (AMTI, Bertec, Kistler) — integration partnership and co-marketing to their existing clinic customers
- Orthopedic surgery groups — outcome data sharing in exchange for patient referral pipeline
- Physical therapy continuing education organizations — training and certification programs that feature the platform

Expansion path:
1. ACL rehabilitation (entry market — well-defined protocol, clear outcome metric)
2. Other knee and lower extremity rehabilitation protocols
3. Broader musculoskeletal rehabilitation decision support
4. Integration with EHR systems for hospital system sales

---

## 13. Risks and Constraints

Main execution risks:
- Regulatory classification uncertainty — if FDA determines this is a SaMD requiring clearance, the timeline and cost increase significantly
- Clinical workflow resistance — PTs may resist adding a new digital tool to an already busy workflow
- Hardware dependency — clinics without force plates cannot use the core functionality

Data risks:
- Re-injury outcome data requires long-term follow-up that is difficult to collect in a SaaS model
- Normative data gaps — the system needs population-specific benchmarks to be clinically meaningful
- PHI handling errors would be a serious legal and reputational risk

Adoption risks:
- Hospital system IT approval processes are slow and complex
- Clinicians may not trust a score that differs from their clinical judgment
- Reimbursement: there is currently no CPT code for AI-assisted rehabilitation assessment — the cost must be justified by efficiency or outcomes, not billing

Regulatory risks:
- FDA SaMD classification risk is real and must be assessed before launch
- State-level PT practice act variations may affect how the tool can be marketed
- HIPAA compliance is non-negotiable — a breach would be catastrophic for a small company

Technical risks:
- Force plate hardware fragmentation — different vendors have different data formats and APIs
- EHR integration is complex and expensive — should be deferred until there is clear demand
- Model drift if the scoring algorithm is not maintained as clinical evidence evolves

---

## 14. Recommended Next Steps

Immediate (next 30 days):
- Engage healthcare regulatory counsel to assess FDA CDS/SaMD classification risk
- Establish HIPAA-compliant data infrastructure before any patient data is collected
- Identify one pilot clinic partner and define the pilot scope
- Define the v1 feature set — cut everything that is not essential to the core assessment workflow

Short-term build plan (next 90 days):
- Build the structured assessment workflow and readiness score calculation
- Implement HIPAA-compliant patient data storage and access controls
- Deploy to pilot clinic and begin collecting patient assessment data
- Conduct weekly feedback sessions with pilot PTs

Strategic next milestone (6–12 months):
- Complete pilot with documented clinician feedback and outcome data
- Publish or present pilot results (conference abstract or case study) to build credibility
- Use pilot results to define pricing model and begin outreach to 3–5 additional clinics
- Assess regulatory pathway and determine whether 510(k) clearance is needed before scaling
