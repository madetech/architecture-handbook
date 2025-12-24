# Strategic Guide: Leveraging Agent Skills in Software Architecture

## Executive Summary

Software Architecture in large estates is a high-context, high-nuance discipline. This framework ensures that Agent Skills (automated capabilities) are developed only to solve proven SDLC constraints and are structured to align with the technical requirements of the agentic environment.

---

## 1. The ROI Filter: The Bottleneck Test

Before any "Agent Skill" is developed, it must pass the **Bottleneck Test**.

* **The Rule:** No skill is developed unless it alleviates a measured delay in the SDLC (e.g., PR Review Latency, Documentation Upkeep, or Incident Triage).
* **The Logic:** "An hour saved on something that isn't the bottleneck is worthless." We prioritize automation where the human flow is currently stalled.

---

## 2. Implementation Strategy: Skill Components

An Agent Skill is a directory-based package. Based on the task archetype, we provide different assets within the `.claude/skills/` folder structure.

### Level 1: The Discovery Layer (Metadata)

* **File:** `SKILL.md` (Frontmatter)
* **Content:** Unique `name` and specific `description`.
* **Behavior:** Always loaded; used by the agent to decide if the skill is relevant to the user's request.

### Level 2: The Guidance Layer (Instructions)

* **File:** `SKILL.md` (Body)
* **Content:** Natural language instructions, Socratic nudges, or pattern-matching rules.
* **Behavior:** Loaded only when the skill is triggered.

### Level 3: The Resource Layer (Supporting Files)

* **Folders:** `/references`, `/scripts`, `/assets`
* **Content:** Python/Bash scripts for validation, Markdown ADRs, YAML schemas, or checklists.
* **Behavior:** Accessed by the agent only when explicitly needed.

---

## 3. The Four Archetypes of Architectural AI

Understanding these archetypes dictates which "Level" of assets you need to prioritize during development.

| Archetype | Logic Goal | Primary Assets | Primary Bottleneck |
| --- | --- | --- | --- |
| **The Enforcer** | **Precision** | `/scripts` & YAML Schemas | Governance/Compliance Lag |
| **The Librarian** | **Discovery** | `/references` (Markdown/Logs) | Discovery & Research Time |
| **The Mentor** | **Behavior** | `SKILL.md` Instructions | Review Latency / Skill Gaps |
| **The Assistant** | **Execution** | `/assets` & Templates | Administrative / Toil tasks |

---

## 4. Operational Guardrails

1. **Citations are Mandatory:** No response from a `/references` asset is valid without a link to the source document.
2. **Explicit Uncertainty:** If confidence in a search is low, the agent must defer to a human architect.
3. **Human-in-the-loop (HITL):** AI output for synthesis tasks remains a "Draft" until signed off by a human.
4. **Experience Sampling:** Consider capturing a "Helpful/Not Helpful" score for every invocation to track the **Developer Experience Index (DXI)**.

---

## 5. Decision Flow: From Bottleneck to Folder Structure

```mermaid
graph TD

    Start([Opportunity for AI Skill]) --> B1{Is this a known SDLC Bottleneck?}
    B1 -- No --> Stop([STOP: Re-evaluate Priorities])
    B1 -- Yes --> Q1{Nature of Task?}

    Q1 -- Deterministic Policy --> Q2{Is the Rule/Schema Structured?}
    Q1 -- Judgment / Synthesis --> Q3{Is Context High-Volatility?}

    %% Deterministic Path
    Q2 -- Yes (YAML/JSON) --> Q4[SKILL TYPE: 'Enforcer']
    Q4 --> A4[FOLDER: /scripts <br/>Add validation scripts & schemas]

    Q2 -- No (Unstructured) --> Q5[SKILL TYPE: 'Librarian']
    Q5 --> A5[FOLDER: /references <br/>Add Markdown docs & text logs]

    %% Synthesis Path
    Q3 -- Yes (Rapidly Changing) --> Q6{Is Social Nuance Required?}
    Q3 -- No (Historical/Fixed) --> Q7[SKILL TYPE: 'Librarian']
    Q7 --> A7[FOLDER: /references <br/>Add historical ADRs/Wikis]

    %% Coaching Path
    Q6 -- Yes (Mentorship) --> Q8[SKILL TYPE: 'Mentor']
    Q8 --> A8[FILE: SKILL.md body <br/>Add Socratic instructions]

    Q6 -- No --> Q9{Risk of Hallucination?}

    %% Risk Assessment
    Q9 -- High Impact --> Q10[STOP: Keep as Human-Only Task]
    Q9 -- Low Impact --> Q11[SKILL TYPE: 'Assistant']
    Q11 --> A11[FOLDER: /assets <br/>Add templates & checklists]

    %% Styles
    style Q4 fill:#2ECC71,stroke:#27AE60,color:#fff
    style Q5 fill:#E67E22,stroke:#D35400,color:#fff
    style Q7 fill:#9B59B6,stroke:#8E44AD,color:#fff
    style Q8 fill:#3498DB,stroke:#2980B9,color:#fff
    style Q10 fill:#E74C3C,stroke:#C0392B,color:#fff
    style Q11 fill:#F1C40F,stroke:#F39C12,color:#000
    style Stop fill:#E74C3C,stroke:#C0392B,color:#fff

```

## Conclusion

This framework ensures that Agent Skills are applied strategically, enhancing architectural decision-making without compromising the nuanced judgment that human architects provide. By categorizing skills into clear archetypes and following operational guardrails, organizations can leverage AI capabilities while engineering trust in the process.
