# Skill: Research-to-Product Translation

## Skill Identity

**Name:** Research-to-Product Translation  
**Version:** 1.0  
**Type:** Reasoning + Structured Output Skill  
**Domain:** Innovation, Product Strategy, Translational Research  
**Tone:** Practical, strategic, execution-focused  

---

## Purpose

This skill takes a research idea, concept, paper, prototype, lab capability, or experimental workflow and translates it into a structured product strategy. It bridges the gap between research and real-world deployment by thinking across multiple roles simultaneously: researcher, product strategist, startup founder, systems architect, compliance reviewer, and implementation planner.

---

## Trigger Phrases

Activate this skill when the user says any of the following (or close variations):

- "Turn this research idea into a product"
- "Help me commercialize this concept"
- "Translate this paper into an MVP"
- "What would this look like as a product?"
- "Turn this lab idea into a startup concept"
- "Build a pilot plan from this research"
- "Who would use this and how would we deploy it?"
- "What is the product strategy for this concept?"
- "How do we move this from research to application?"
- "Map this innovation into a real offering"
- "What could this actually become?"
- "What is the go-to-market for this?"
- "How do we productize this?"

Also activate when the user provides any of the following without an explicit trigger phrase:
- A research abstract or paper
- A prototype description
- A lab capability statement
- A technical system description
- A methods section or workflow with a question about its potential
- An invention idea or early startup concept

---

## Accepted Input Types

1. **Short concept description** — A few sentences describing a system, method, or capability
2. **Research abstract** — Academic-style abstract from a paper or grant
3. **Full paper or structured summary** — Pasted content, bullet points, or notes
4. **Existing prototype description** — Description of what has already been built
5. **Lab capability statement** — What data, tools, or methods a lab has access to
6. **Early startup concept** — A rough idea for a product or service

---

## Reasoning Workflow

When this skill is triggered, reason through the following steps in order before generating output.

### STEP 1 — Understand the Research
- What is the actual concept?
- What scientific or technical capability exists?
- What stage is it at: idea, prototype, validated method, pilot-ready, or mature system?
- What domain does it belong to?

### STEP 2 — Identify the Real-World Problem
- What user pain point does this address?
- Is the problem operational, clinical, performance-based, financial, compliance-related, or informational?
- Is the concept a direct product, enabling infrastructure, or internal research tool?

### STEP 3 — Define the User and Buyer
Separate these roles explicitly:
- **End user** — who uses the product day-to-day
- **Economic buyer** — who pays for it
- **Operator/admin** — who configures or manages it
- **Influencer/stakeholder** — who shapes the decision to adopt

### STEP 4 — Create the Value Proposition
Translate technical language into user value. Answer:
- Why would someone care?
- What gets better, faster, safer, cheaper, smarter, or more scalable?

### STEP 5 — Define the MVP
Keep it disciplined. Focus on:
- Smallest valuable version
- Core workflows only
- Must-have features
- What can wait for later phases

### STEP 6 — Define Data Needs
Identify:
- Required data sources
- Possible labels or outcomes
- Collection frequency
- Historical vs. real-time needs
- Data ownership questions
- Data quality issues
- Whether the data is realistic to obtain

### STEP 7 — Review Risk / Privacy / Regulation
Consider as applicable:
- HIPAA, FERPA, GDPR
- Biometric data handling
- Human subjects / IRB concerns
- Clinical claims risk
- AI explainability requirements
- Consent requirements
- Data retention policies
- Cybersecurity requirements
- Model bias and fairness
- Athlete or student privacy

Frame these as likely considerations and probable constraints — not legal certainty. Flag items requiring counsel or compliance review.

### STEP 8 — Create a Pilot Plan
Include:
- Pilot objective
- Pilot site or partner type
- Sample user group
- Duration
- Success metrics
- Implementation dependencies
- What defines pilot success

### STEP 9 — Commercialization Path
Outline possible paths such as:
- Internal lab platform
- B2B SaaS
- Licensing to clinics or athletic departments
- University spinout
- White-label platform
- Data services
- Consulting-enabled software
- Research partnership model
- Grant-funded validation leading to productization

### STEP 10 — Next Steps
Give a realistic phased path:
- Next 30 days
- Next 90 days
- Next 6–12 months

---

## Output Format

Produce the following structured output every time this skill is triggered.

---

# Research-to-Product Translation

## 1. Research Concept Summary
- Plain-language summary of the concept
- Current maturity level (idea / prototype / validated method / pilot-ready / mature system)
- What makes it novel or useful

## 2. Problem Being Solved
- Core problem
- Why it matters
- Current alternatives or status quo

## 3. Target Users and Buyers
- End user
- Operator/admin user
- Economic buyer
- Influencers/stakeholders

## 4. Value Proposition
- Primary value proposition
- Secondary value propositions
- Why this is better than current approaches

## 5. Product Concept
- What the product is
- Product type (app, dashboard, platform, API, device-enabled service, analytics layer, etc.)
- Core user workflow

## 6. MVP Definition
- Must-have features
- Nice-to-have (later phases)
- What should explicitly NOT be in v1

## 7. Data Requirements
- Required data inputs
- Optional/enrichment data
- Labels/outcomes needed
- Data collection feasibility
- Data risks or gaps

## 8. Technical / System Considerations
- Likely architecture
- Integration requirements
- Hardware/software dependencies
- Deployment environment
- Scalability concerns

## 9. Regulatory / Privacy / Ethical Considerations
- Privacy concerns
- Security concerns
- Regulatory/compliance considerations
- Ethical issues
- Claims that should be avoided without validation

## 10. Pilot Plan
- Recommended pilot environment
- Pilot user group
- Duration
- Metrics
- Success criteria
- Operational dependencies

## 11. Validation Strategy
- What must be validated first
- Technical validation
- User validation
- Outcome validation
- Business validation

## 12. Commercialization Path
- Likely business model(s)
- Go-to-market entry point
- Early adopter profile
- Partnership opportunities
- Expansion path

## 13. Risks and Constraints
- Main execution risks
- Data risks
- Adoption risks
- Regulatory risks
- Technical risks

## 14. Recommended Next Steps
- Immediate next actions (next 30 days)
- Short-term build plan (next 90 days)
- Strategic next milestone (6–12 months)

---

## Output Quality Rules

1. Do not stay too academic. Translate research into product language.
2. Do not become too shallow. Maintain technical credibility.
3. Always distinguish between end user, buyer, and stakeholder — they are often different people.
4. Do not recommend bloated MVPs. Be disciplined and realistic.
5. Clearly identify assumptions. If something is unknown, say it is an assumption.
6. Avoid pretending to give final legal advice. Flag regulatory/privacy/compliance issues appropriately.
7. Be honest about feasibility. If data access, validation, or adoption looks difficult, say so.
8. When the concept is too early-stage, say: "This is better framed as a pilot or research platform before full productization."
9. When useful, offer multiple commercialization options instead of forcing one path.
10. Make the response actionable enough that a founder, lab director, product lead, or engineer could use it as a starting blueprint.

---

## Optional Enhancements

If enough information exists, the skill may also include:

- User persona snapshot
- Buyer persona snapshot
- Competitive substitute overview
- Build-vs-buy considerations
- Research questions that still need answering
- Grant opportunities or translational funding paths
- Partnership types to pursue
- Recommended KPIs
- Sample positioning statement
- Sample one-sentence pitch
- Implementation timeline by phase

---

## Domains This Skill Handles Well

- AI/ML systems
- Sports science and performance technology
- Health tech and digital health
- Biomechanics and movement science
- Rehabilitation technology
- Computer vision systems
- Sensor platforms and wearables
- Data platforms and analytics infrastructure
- Simulation tools and digital twins
- Neurotechnology
- Applied research labs
- SaaS and platform products
- Internal research tooling with external product potential

---

## Authorship

**Author / Lead Scientist:** William McDonald
**Affiliation:** University of North Carolina Chapel Hill
**Organization:** Founder, QAI Lab

This skill was developed as part of the QAI Lab's mission to build reusable, agent-agnostic AI tools that accelerate the translation of research and technical innovation into real-world products and deployments.
