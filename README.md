# Research-to-Product Translation Skill

**Author / Lead Scientist:** William McDonald
**Affiliation:** University of North Carolina Chapel Hill
**Organization:** Founder, QAI Lab

---

## Why This Skill Matters

The gap between research and real-world deployment is one of the most persistent and costly problems in science, technology, and innovation. Brilliant ideas get stuck in labs. Validated methods never reach the people who need them. Prototypes sit on shelves because no one translated the science into a product strategy.

This skill exists to close that gap.

Whether you are a researcher who has spent years developing a method and wants to know what it could become, a technical founder trying to turn a prototype into a company, a lab director exploring commercialization, or a product manager working with an R&D team — this skill gives you a structured, practical framework for translating what you have built into what the world can actually use.

It does not just summarize your idea. It forces the right questions: Who is the real user? Who actually pays for this? What is the smallest version that delivers real value? What data do you actually need? What regulatory landmines exist? What does a realistic pilot look like? What does the path from concept to commercialization actually look like?

These are the questions that separate research that ships from research that sits.

This skill is especially valuable because it thinks across roles simultaneously — researcher, product strategist, startup founder, systems architect, compliance reviewer, and implementation planner — in a single structured output. Most people have access to one or two of those perspectives. This skill gives you all of them at once.

It is designed to be used across any AI agent or interface, making it a portable, reusable asset for any team, lab, or organization that wants to move faster from discovery to deployment.

---

## What This Skill Does

This skill takes a research idea, concept, paper, prototype, lab capability, or experimental workflow and translates it into a structured product strategy. It bridges the gap between research and real-world deployment.

The skill thinks across multiple roles simultaneously:
- Researcher
- Product strategist
- Startup founder
- Systems architect
- Compliance and risk reviewer
- Implementation planner

The output is a structured, actionable product translation document covering everything from user definition and MVP scoping to pilot planning, regulatory considerations, and commercialization paths.

---

## Who This Is For

- Applied researchers and lab directors exploring commercialization
- Technical founders moving from prototype to product
- Innovation teams inside universities, hospitals, or enterprises
- Product managers working with R&D teams
- Startup advisors helping translate science into strategy
- Engineers who need to communicate research value to non-technical stakeholders

---

## When to Use It

Use this skill when you have any of the following and want to understand what it could become as a real product:

- A research concept or idea
- A scientific abstract or paper
- A prototype or proof-of-concept
- A lab capability or dataset
- A technical system description
- An early startup concept
- A methods section or workflow

---

## Supported Input Types

| Input Type | Example |
|---|---|
| Short concept description | "We built a CV model that tracks player fatigue from video." |
| Research abstract | Paste an academic abstract |
| Full paper or notes | Paste structured content or bullet points |
| Prototype description | "We have a FastAPI backend and an iPad dashboard." |
| Lab capability statement | "Our lab collects VR, eye tracking, GPS, and survey data." |
| Early startup concept | "We want to help coaches monitor athlete cognitive readiness." |

---

## Example Prompts

```
Turn this research idea into a product: [paste concept]
```

```
What would this look like as a product? [paste abstract]
```

```
Help me commercialize this concept: [paste description]
```

```
Translate this paper into an MVP: [paste paper or summary]
```

```
Build a pilot plan from this research: [paste concept]
```

```
Who would use this and how would we deploy it? [paste prototype description]
```

```
What is the product strategy for this concept? [paste lab capability]
```

---

## Expected Output Structure

Every response from this skill follows this structure:

1. Research Concept Summary
2. Problem Being Solved
3. Target Users and Buyers
4. Value Proposition
5. Product Concept
6. MVP Definition
7. Data Requirements
8. Technical / System Considerations
9. Regulatory / Privacy / Ethical Considerations
10. Pilot Plan
11. Validation Strategy
12. Commercialization Path
13. Risks and Constraints
14. Recommended Next Steps

---

## How to Use With Each Agent

### Kiro-cli

Drop the skill file into your `.kiro/skills/` directory or reference it directly in your session context.

```
/context add skill/research-to-product-translation.md
```

Then prompt:
```
Using the Research-to-Product Translation skill, translate this concept: [your input]
```

---

### Claude (claude.ai or API)

Paste the contents of `wrappers/claude.md` as your system prompt or at the top of your conversation. Then provide your research input as the user message.

Alternatively, paste the full skill file as context before your prompt.

---

### Codex (OpenAI API / Codex CLI)

Use `wrappers/codex.md` as your system prompt when calling the API. Provide the research concept as the user message.

For CLI use:
```
codex --system-prompt wrappers/codex.md "Translate this concept: [your input]"
```

---

### Gemini (Google AI Studio or API)

Paste `wrappers/gemini.md` as the system instruction in Google AI Studio, or include it as the first turn in your API call. Then provide your research input.

---

### GitHub Copilot (Chat)

Open Copilot Chat and paste the contents of `wrappers/copilot.md` followed by your research concept. Copilot Chat works best with direct inline prompting rather than system prompts.

---

### Cursor Agent

In Cursor, open the AI panel and paste `wrappers/cursor-agent.md` as your instruction context. Then describe your research concept in the chat.

For `.cursorrules` integration, append the skill trigger instructions from `wrappers/cursor-agent.md` to your project's `.cursorrules` file.

---

### OpenClaw

Load `wrappers/openclaw.md` as a skill definition in your OpenClaw agent configuration. The wrapper is formatted to match OpenClaw's skill/tool definition pattern.

---

## File Structure

```
research-to-product-translation-skill/
  README.md
  LICENSE
  /skill
    research-to-product-translation.md     ← main portable skill file
  /wrappers
    claude.md
    codex.md
    gemini.md
    copilot.md
    cursor-agent.md
    openclaw.md
  /examples
    sports-science-example.md
    rehab-example.md
    computer-vision-example.md
    sensor-platform-example.md
    internal-tool-example.md
```

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

## Notes

- This skill does not provide legal, medical, or financial advice. Regulatory and compliance sections flag considerations for review — not final determinations.
- The skill is designed to be honest about feasibility. If something is difficult, it will say so.
- MVP recommendations are intentionally disciplined. The skill will push back on scope creep.
- When a concept is too early-stage for productization, the skill will say so and recommend a research or pilot framing instead.
