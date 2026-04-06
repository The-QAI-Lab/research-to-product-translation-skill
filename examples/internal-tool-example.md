# Example: Internal Lab Tooling — Research Protocol Management and Data Pipeline Tool

## Input

> "We built an internal tool for our sports science lab that manages research study protocols, tracks participant enrollment and session completion, automates data quality checks on incoming sensor data, and generates standardized reports for each study. It took us 18 months to build. Other labs keep asking us how we built it and whether they can use it. We want to understand if this could become a product."

---

# Research-to-Product Translation

## 1. Research Concept Summary

An internal research operations platform built for a sports science lab that handles study protocol management, participant tracking, automated data quality checking, and standardized report generation. Built over 18 months for internal use, with growing external interest from peer labs.

Maturity level: Mature internal tool. The system works in production for its original use case. The gap is the transition from a custom-built internal tool to a generalizable, supportable product for external users.

What makes it novel: Research labs in sports science, health tech, and applied science universally struggle with the same operational problems — participant tracking, data quality, and report generation — but almost all solve them with spreadsheets, custom scripts, or expensive general-purpose tools not designed for their domain. A purpose-built research operations platform for this space does not exist as a commercial product.

Note: This is a strong candidate for productization, but the transition from internal tool to external product is non-trivial. The tool was built for one lab's specific workflow. Generalizing it requires understanding what is universal vs. what is specific to the original lab.

---

## 2. Problem Being Solved

Core problem: Sports science and applied research labs spend a disproportionate amount of time on research operations — tracking who has completed which sessions, chasing down missing data, manually checking data quality, and assembling reports. This administrative burden reduces time available for actual science.

Why it matters: Research productivity is directly limited by operational overhead. Labs that run cleaner operations produce more data, publish faster, and attract more funding. A tool that reduces operational friction has clear value.

Current alternatives: Spreadsheets (fragile, not scalable, no automation), REDCap (powerful but complex, not designed for sensor data), general project management tools (Notion, Airtable — not domain-specific), or custom scripts (require ongoing maintenance and technical staff).

---

## 3. Target Users and Buyers

- End user: Research coordinator or lab manager who tracks participant enrollment, session completion, and data quality day-to-day
- Operator/admin: Principal investigator or lab director who configures study protocols, manages team access, and reviews study progress
- Economic buyer: Lab director with discretionary budget, or university research office that funds lab infrastructure
- Influencers/stakeholders: Graduate students and postdocs (who use the tool daily), IRB office (interested in protocol compliance and data governance), funding agencies (interested in data quality and reproducibility), IT department (data security and infrastructure)

---

## 4. Value Proposition

Primary: Give research labs a purpose-built operations platform that replaces spreadsheets and custom scripts — so coordinators spend less time on administrative overhead and more time on science.

Secondary:
- Automated data quality checks catch problems early, before they become analysis errors or publication issues
- Standardized reports reduce the time spent assembling study summaries for PIs, funders, and IRBs
- A structured participant tracking system reduces the risk of protocol deviations and missed sessions

Why better than current approaches: REDCap is powerful but complex and not designed for sensor data workflows. General project management tools lack domain-specific features. Custom scripts require ongoing maintenance. This platform is purpose-built for the sports science and applied research lab workflow.

---

## 5. Product Concept

What the product is: A research operations platform for sports science and applied research labs.

Product type: Web application with study protocol management, participant tracking, automated data quality checking, and report generation.

Core user workflow:
1. PI or lab director creates a new study in the platform, defines the protocol (sessions, data collection points, inclusion/exclusion criteria)
2. Research coordinator enrolls participants and schedules sessions
3. After each session, data files are uploaded or synced to the platform
4. Platform runs automated data quality checks and flags issues (missing files, out-of-range values, incomplete sessions)
5. Coordinator reviews flags and resolves issues
6. PI or coordinator generates a standardized study progress report (enrollment status, completion rates, data quality summary)
7. At study close, platform generates a final data package and summary report

---

## 6. MVP Definition

Must-have features:
- Study protocol builder (define sessions, data collection points, required files)
- Participant enrollment and session tracking
- Data file upload and basic automated quality checks (file presence, format validation, basic range checks)
- Study progress dashboard (enrollment status, session completion rates, data quality summary)
- Standardized report generation (PDF or CSV export)
- Role-based access (PI, coordinator, student researcher)
- Secure data storage

Nice-to-have (later phases):
- Sensor-specific data quality checks (e.g., GPS dropout detection, HRV artifact flagging)
- Integration with common data collection tools (REDCap, Qualtrics, Catapult)
- Automated participant communication (session reminders, completion confirmations)
- Multi-study portfolio view for lab directors
- IRB documentation support
- API for external analysis tools

Explicitly out of scope for v1:
- Data analysis or statistical tools
- Publication or manuscript management
- Grant management
- Consumer or participant-facing features
- Real-time data streaming

---

## 7. Data Requirements

Required inputs (the platform manages these, does not generate them):
- Study protocol definitions (sessions, data types, schedules)
- Participant enrollment records
- Session completion records
- Data files from each session (format varies by study)

Optional/enrichment data:
- Participant demographic and eligibility data
- IRB protocol documents
- Adverse event logs

Labels/outcomes needed (for the platform's own quality checks):
- Expected data file formats and value ranges per study protocol
- Session completion criteria

Data collection feasibility: High — the platform manages data that labs already collect. The challenge is generalizing the data quality check logic across different study types and sensor systems.

Data risks/gaps:
- Data quality check logic must be configurable per study — a one-size-fits-all approach will not work across different sensor types and protocols
- Participant data is sensitive — IRB compliance and data governance must be built in from the start
- If the platform stores raw research data, it becomes responsible for data integrity and long-term archiving

---

## 8. Technical / System Considerations

Likely architecture:
- Web application (React frontend, Python/FastAPI or Django backend)
- PostgreSQL for structured records (participants, sessions, protocols)
- Object storage (S3 or equivalent) for data files
- Background job queue (Celery or similar) for automated quality checks
- PDF generation service for reports
- Cloud deployment with per-lab data isolation

Integration requirements:
- File upload from common formats (CSV, JSON, proprietary sensor formats)
- Optional: REDCap API, Qualtrics API for survey data ingestion
- Optional: Catapult, Polar APIs for sensor data ingestion

Hardware/software dependencies:
- No hardware dependencies for the core platform
- Sensor integrations are optional and additive

Deployment environment: Cloud-hosted SaaS with per-institution data tenancy. University IT departments may require on-premise or university-hosted deployment for research data.

Scalability concerns: Data file storage scales with study volume and file sizes. Quality check processing scales with data volume. Both are manageable with standard cloud infrastructure.

---

## 9. Regulatory / Privacy / Ethical Considerations

Privacy concerns:
- Participant data in research studies is protected by IRB protocols and applicable privacy law
- HIPAA may apply if any health data is collected
- FERPA may apply if participants are students
- GDPR applies for EU-based participants or institutions

Security concerns:
- Research data must be encrypted at rest and in transit
- Role-based access control must enforce that researchers only access data for their own studies
- Data retention and deletion policies must align with IRB requirements and institutional policy

Regulatory/compliance considerations:
- The platform must support IRB-compliant data handling — audit logs, access controls, and data retention policies are essential
- If the platform stores identifiable participant data, it must comply with applicable privacy law
- University IT security review will likely be required before institutional adoption

Ethical issues:
- Participant consent records must be managed carefully — the platform should support consent tracking
- Data sharing across institutions requires data use agreements
- The platform must not make it easier to misuse participant data — access controls and audit logs are ethical requirements, not just technical ones

Claims to avoid:
- "IRB approved" (the platform supports IRB compliance, but each study requires its own IRB approval)
- "HIPAA compliant" without a formal compliance audit and BAA

---

## 10. Pilot Plan

Recommended pilot environment: Two or three peer sports science labs at different universities that have already expressed interest

Pilot user group: 1–2 research coordinators and 1 PI per lab, across 2–3 active studies per lab

Duration: One full study cycle per lab (typically 3–6 months)

Metrics:
- Time saved on study administration vs. current process (self-reported)
- Data quality flag detection rate (% of real data issues caught by automated checks)
- Report generation time vs. manual process
- User satisfaction score (end-of-pilot survey)
- System reliability (uptime, error rate)

Success criteria:
- Coordinators report meaningful time savings on administrative tasks
- Automated quality checks catch at least 80% of data issues that would have been caught manually
- PIs report that study progress reports are useful and accurate
- No data security incidents

Operational dependencies:
- University IT approval for cloud data storage
- IRB review of the platform's data handling practices (may be required by some institutions)
- Staff training completed (target: <3 hours per coordinator)

---

## 11. Validation Strategy

What must be validated first: Whether the platform's protocol and workflow model is general enough to support different labs' study designs — or whether it is too tightly coupled to the original lab's specific workflow.

Technical validation:
- Data quality check accuracy across different sensor types and study designs
- Report generation correctness
- System reliability and data integrity

User validation:
- Do coordinators at other labs find the platform intuitive without extensive training?
- Does the protocol builder support the range of study designs used by pilot labs?
- Is the report output useful for PIs and funders?

Outcome validation:
- Does use of the platform reduce administrative overhead measurably?
- Does it reduce data quality issues compared to the lab's previous process?

Business validation:
- Are labs willing to pay for this as a standalone SaaS tool?
- What is the willingness-to-pay range (per lab, per year)?
- Is the buying decision made by the PI, the lab director, or the university research office?

---

## 12. Commercialization Path

Likely business model(s):
- B2B SaaS: Annual subscription per lab, tiered by number of active studies or users
- University site license: Institution-wide license covering multiple labs
- Freemium research tier: Free for labs with one active study; paid for multiple studies or advanced features (lowers adoption barrier, builds user base)

Go-to-market entry point: Sports science and applied research labs at universities — they are the original target user, they have already expressed interest, and they are a credible reference market for expansion into adjacent research domains.

Early adopter profile: Labs with 2–5 active studies, a research coordinator who is frustrated with spreadsheet-based tracking, and a PI who values data quality and reproducibility.

Partnership opportunities:
- University research offices and technology transfer offices — for institutional licensing and spinout support
- Research funding agencies (NIH, NSF, DARPA) — grant-funded labs are a natural customer base
- Sports science professional organizations (NSCA, ACSM) — visibility and credibility with the target market

Expansion path:
1. Sports science and applied research labs (entry market)
2. Clinical research labs and rehabilitation research centers (adjacent market with similar operational needs)
3. Human performance research programs in military and government settings
4. Broader academic research lab management (larger market, more competition)

---

## 13. Risks and Constraints

Main execution risks:
- The platform was built for one lab's specific workflow — generalizing it may require significant rearchitecting
- University IT approval processes are slow and complex — institutional adoption takes time
- The tool competes with REDCap (free, widely adopted) for mindshare, even though it is not a direct substitute

Data risks:
- The platform stores sensitive research data — a data breach or integrity failure would damage trust with the research community
- Data quality check logic must be maintained as sensor formats and study designs evolve

Adoption risks:
- Research coordinators and PIs are often resistant to changing established workflows, even if the new tool is better
- University procurement processes can be slow and require IT security review, legal review, and budget approval
- Without a strong user community, the platform may struggle to gain traction beyond early adopters

Regulatory risks:
- IRB compliance requirements vary by institution — the platform must be flexible enough to support different institutional requirements
- HIPAA and FERPA compliance may be required for some research populations

Technical risks:
- Generalizing the data quality check logic across different sensor types and study designs is technically complex
- University IT environments are heterogeneous — the platform must work across different institutional IT configurations
- Long-term data archiving and retention is a responsibility that comes with storing research data

---

## 14. Recommended Next Steps

Immediate (next 30 days):
- Interview 3–5 labs that have expressed interest to understand their specific workflow needs and pain points
- Identify which features of the current internal tool are universal vs. specific to the original lab
- Define the v1 feature set based on the most common needs across interested labs
- Assess the legal and compliance requirements for external deployment (data governance, IRB, HIPAA)

Short-term build plan (next 90 days):
- Refactor the protocol builder and participant tracking module to support configurable study designs
- Build the web-based interface for external users (the internal tool may have a different UX)
- Deploy to 2–3 pilot labs and begin collecting feedback
- Establish a support and feedback process for pilot users

Strategic next milestone (6–12 months):
- Complete pilot with documented time savings and user satisfaction data
- Define pricing model and begin outreach to additional labs
- Explore university site license conversations with 2–3 research-intensive institutions
- Assess whether a university spinout, open-source model, or commercial SaaS is the right long-term path
