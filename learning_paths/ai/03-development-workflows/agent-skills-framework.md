# Agent Skills Framework (Anthropic)

**Difficulty**: Intermediate
**Time Investment**: 2-3 hours
**Prerequisites**: Understanding of prompts, agentic workflows, file systems

---

## Learning Resources (Start Here)

### Primary Video
- **[Don't Build Agents, Build Skills Instead – Barry Zhang & Mahesh Murag, Anthropic](https://www.youtube.com/watch?v=CEvIs9y1uog)** (45 min)
  - Explains Anthropic's Skills framework
  - Covers architecture, progressive disclosure, and the MCP stack
  - Includes practical skill creation examples

---

## Why This Matters

**The Problem**: High-quality prompts improve LM performance, but they:
- Are static (loaded into context immediately)
- Are declarative ("Act like a tax lawyer")
- Disappear when the chat session ends
- Can't execute pre-written, validated logic

**Agent Skills solve this** by giving LMs:
- **Procedural execution power** (not just instructions)
- **Progressive context loading** (load only when needed)
- **Portable, reusable toolboxes** (persist across projects)

As a Technical Architect, understanding Skills helps you:
- Build governance guardrails (e.g., ADR enforcement)
- Create reusable expertise packages (e.g., security auditing)
- Design systems where AI "knows how we do things here"

---

## Key Concepts

### Skills vs. High-Quality Prompts

| Feature | High-Quality Prompt | Agent Skill |
|---------|---------------------|-------------|
| **Context Load** | Static. Full text loaded immediately. | Progressive. Tiny metadata first; full manual only if needed. |
| **Logic Type** | Declarative. "Act like a tax lawyer." | Procedural. "Here's a Python script to validate tax codes. Run it if unsure." |
| **Actionability** | LLM describes what it would do. | LLM executes pre-written scripts in secure runtime. |
| **Persistence** | Lost when chat ends (unless in System Prompt). | Portable folders. Reusable across projects. |

**Key takeaway**: If a prompt is an instruction manual, a skill is a **toolbox that includes the manual and the tools**.

---

### Skills vs. Cursor's `.cursorrules` (AI Generated)

Both provide context, but they serve different purposes:

| Aspect | `.cursorrules` | Agent Skills |
|--------|----------------|--------------|
| **Scope** | Conventions (coding style, folder structure) | Capabilities (executable scripts, validation logic) |
| **The "Script" Component** | Can follow rules to write code | Packages **pre-written, validated scripts** that agent calls as tools |
| **Runtime** | Local IDE context | Tight coupling with runtime environment (Claude Code container, VM) |
| **Primary Use** | "Always use TypeScript" | "Here's a script to generate a PDF report" |

**Example**:
- `.cursorrules`: "Use Tailwind for styling"
- Agent Skill: "Here's a script that validates our accessibility standards (WCAG 2.1 AA)"

**Architect's takeaway**: Use `.cursorrules` for **conventions**, Skills for **executable capabilities**.

---

## How It Works: The "Folder" Paradigm

### Skill Structure

```
/my-skill/
├── SKILL.md          # Instructions for when/how to use this skill
└── scripts/          # Executable logic (Python, Bash, etc.)
    ├── validate.py
    └── generate.sh
```

**SKILL.md Example**:
```markdown
# ADR Governor Skill

## When to use
Trigger this skill when:
- User proposes a new technology or architectural change
- A new ADR needs to be created
- An existing ADR needs validation

## How it works
1. Check if ADR exists for this decision domain
2. Run scripts/validate_adr.py to check against enterprise tech radar
3. Draft ADR using templates/adr-template.md
4. Flag deprecated technologies

## Scripts
- validate_adr.py: Checks ADR against enterprise standards
- generate_adr.sh: Creates new ADR from template
```

---

## Technical Advancements

### 1. Progressive Disclosure

**The Problem**: Loading all skills upfront bloats the context window.

**The Solution**: Two-stage loading

**Stage 1: Metadata Only**
```json
{
  "skill_name": "adr-governor",
  "description": "Validates architectural decisions against enterprise standards",
  "triggers": ["new technology", "architecture change", "ADR creation"]
}
```
*(~50 tokens)*

**Stage 2: Full Load (only if triggered)**
```
SKILL.md (full instructions) + scripts/ (executable logic)
```
*(~5000 tokens)*

**Impact**: Agent can have access to 50 skills without context bloat (when triggered reliably). Only loads what it determines it needs.

---

### 2. Code as the Interface

**Philosophy**: Instead of building custom APIs for every task, Anthropic uses **Bash/File System standard**.

**Principle**: If a human can do it in a terminal, the agent *can** do it with a skill.

*if the skill is triggered.

**Example**:
```bash
# Traditional approach: Build custom API
POST /api/skills/threat-model
Body: { "architecture": "..." }

# Skills approach: Standard file operations
£ cat architecture.md | python scripts/threat-model.py > risks.json
```

**Why this matters**: Lower barrier to skill creation. Developers already know Bash/Python.

---

### 3. Transferable Learning (Skill Creation)

**The Innovation**: LMs can **write their own scripts** and save them for future use.

**Example Workflow**:
1. User asks Claude to solve a complex task
2. Claude writes a Python script to solve it
3. Claude saves the script into a skill folder
4. "Future Claude" can now reuse this skill

**Implication**: Skills enable **emergent expertise**—the more an agent works, the more capable it becomes (when skills trigger reliably).

---

## When Skills Fail

Despite their potential, skills don't always activate automatically. Current trigger reliability is ~20% in production environments. Here are practical fallback strategies:

### Fallback Strategy 1: Explicit Prompting

**When to use**: Skills exist but agent doesn't recognise when to trigger them

**How it works**:
```
Instead of: "Review my architecture"
Use: "Use the threat-modeler skill to analyse this architecture"
```

**Trade-off**: Requires you to know which skill to invoke (defeats some automation benefit)

---

### Fallback Strategy 2: Command Shortcuts

**When to use**: Frequent tasks where you want quick invocation

**How it works**:
Create aliases or shell functions:
```bash
alias threat-model="claude --skill threat-modeler"
```

**Trade-off**: Requires setup; still relies on explicit invocation

---

### The Reality

Skills are powerful but **not yet fully autonomous**. Treat them as:
- **High-value tooling** you can invoke when needed
- **Foundation for future autonomy** as triggering improves
- **Reusable expertise** even when manually invoked

For mission-critical tasks (security, compliance), use deterministic approaches such as CI/CD actions that trigger scripts to ensure consistent execution.

---

## The Emerging Stack

Anthropic's vision for the AI infrastructure stack:

```
┌─────────────────────────────────────┐
│  Human / User                       │
└─────────────────────────────────────┘
              ↕
┌─────────────────────────────────────┐
│  Agent (Claude)                     │
├─────────────────────────────────────┤
│  Skills (Expertise)                 │  ← Procedural knowledge
│  - ADR Governance                   │
│  - Threat Modeling                  │
│  - Trade-off Analysis               │
├─────────────────────────────────────┤
│  MCP (Connectivity)                 │  ← Wires to data sources
│  - Slack, GitHub, Databases         │
├─────────────────────────────────────┤
│  Runtime (Execution Environment)    │  ← Where agent "works"
│  - File system, Bash, APIs          │
└─────────────────────────────────────┘
```

**Layers Explained**:
1. **MCP**: Connects agent to your data (Slack messages, GitHub repos, CRM)
2. **Skills**: The "brain" that knows what to do with that data
3. **Runtime**: The "office" where agent sits and works (file access, code execution)

---

## High-Value Architecture Skills

Our recent dive into this area has revealed five potentially useful skills for Technical Architects:

### 1. `threat-modeler` (Security Architect)

**Problem**: Security treated as afterthought; manual STRIDE analysis is tedious

**Skill Contents**:
- **References**: Library of attack vectors (OIDC, Kubernetes, serverless)
- **Scripts**: Python script to parse architecture diagrams (Mermaid/PlantUML) → output Risk Register
- **Workflow**: Proposed architecture → STRIDE analysis → Risk register (High/Medium/Low) → Mitigation suggestions

**Value**: Helps automate security analysis during design phase (shift-left security) when triggered reliably.

---

### 2. `adr-governor` (Technical/Enterprise Architect)

**Problem**: ADRs are forgotten, inconsistent, or misaligned with enterprise standards

**Skill Contents**:
- **Assets**: ADR templates (Nygard format), Enterprise Tech Radar
- **Scripts**: Validator that checks new ADRs against "golden paths"
- **Workflow**: Developer proposes change → Skill drafts ADR → Cross-references enterprise standards → Flags deprecated tech

**Value**: Helps maintain architectural consistency at scale, reducing manual gatekeeping overhead.

---

### 3. `trade-off-analyzer` (Technical Architect)

**Problem**: Technology choices (Kafka vs. RabbitMQ, monolith vs. microservices) are often biased or lack rigor

**Skill Contents**:
- **References**: Framework benchmarks, operational cost datasets
- **Workflow**: Two options provided → Generate trade-off matrix → Identify NFR violations → Recommendation based on constraints (team size, budget, SLAs)

**Value**: Forces structured comparison of "ilities" (scalability, availability, maintainability).

---

### 4. `iac-security-auditor` (Security/Technical Architect)

**Problem**: Security architects can't review every Terraform/CloudFormation file; misconfigurations (open S3 buckets) slip through

**Skill Contents**:
- **Scripts**: Integration with `tfsec`, `checkov` for deterministic scans
- **References**: Company-specific safe defaults (e.g., "All EBS volumes encrypted with KMS Key X")
- **Workflow**: Read `.tf` file → Run scan → Find violations → Rewrite to be compliant → Explain why

**Value**: Real-time enforcement of security policy in IaC layer.

---

### 5. `architecture-context-first` (Solution Architect)

**Problem**: Engineers and AI agents are quick to solutionise a problem before exploring the full context of the problem first, leading to misaligned solutions

**Skill Contents**:
- **References**: Company-specific guides on what's important to capture at context level, red flags, validation questions, principles, etc.
- **Scripts**: None
- **Workflow**: Establish System Context First → Cross-Check Requirements → Facilitate Stakeholder Alignment → Apply MVA Governance → Transition to Contianer level

**Value**: Acts as "Digital Librarian" for enterprise, ensuring contract-first design.

---

## Try It Yourself

### Experiment 1: Create a Simple Skill

**Task** Build a `code-reviewer` skill using Claude's 'skill-creator' Skill, tip: you ask Gemini or ChatGPT to create a prompt for you.

**Test**: Ask Claude Code to "review this file using the code-reviewer skill"

**Observe**: Does it trigger the skill? Does it execute the script?

---

### Experiment 2: Compare Skill vs. Prompt

**Scenario**: Enforce "all functions must have docstrings"

**Approach A: Prompt**
```
Remember to always add docstrings to functions.
```

**Approach B: Skill**
```
/docstring-enforcer/
├── SKILL.md: "Check if functions have docstrings"
└── scripts/check_docstrings.py: AST parser to find missing docstrings
```

**Test**: Generate 5 functions with each approach

**Observe**:
- Which approach is more consistent?
- Which catches violations better?

---

## Common Pitfalls

### Pitfall 1: Skill Bloat
**Problem**: Creating 50 hyper-specific skills
**Solution**: Start with 3-5 high-impact skills; expand only when needed

### Pitfall 2: No Clear Triggers
**Problem**: Skill has vague "when to use" instructions
**Solution**: Define specific triggers (keywords, file patterns, user intents)

### Pitfall 3: Over-Engineering Scripts
**Problem**: Building complex scripts that do too much
**Solution**: Keep scripts focused (one task per script)

### Pitfall 4: Ignoring Maintenance
**Problem**: Skills become outdated (references old standards)
**Solution**: Treat skills like code—version control, regular updates

---

## Advanced Considerations

### Skill Composition

Skills can call other skills:

```
trade-off-analyzer
  ↓ calls
iac-security-auditor  (to check security implications of choice)
  ↓ calls
adr-governor  (to document decision)
```

**Benefit**: Modular, reusable expertise

**Caveat**: Avoid deep nesting (hard to debug)

---

### Skill Reliability

Skills are evolving rapidly. Current limitations:
- **Trigger rate**: ~20% automatic activation in current implementations
- **Workarounds**: Explicit prompting or command shortcuts provide reliable invocation
- **CI/CD**: For critical tasks, integrate skill scripts directly into pipelines

See [When Skills Fail](#when-skills-fail) for detailed fallback strategies.

---

## Related Topics

- [Vibe Engineering](./vibe-engineering.md) - How skills fit into modern development workflows
- [Context Management](./context-management.md) - Providing context through rules and skills
- [Agentic Workflows](../02-core-patterns/agentic-workflows.md) - Skills enable tool use pattern
- [ADR Automation](../04-governance-automation/adr-automation.md) - Deep dive on the adr-governor skill

---

## Key Takeaway

**Skills turn "smart but inexperienced" LMs into domain experts.**

**When to build a skill**:
1. Task requires **procedural knowledge** ("how we do things here")
2. Task needs **deterministic validation** (running actual tools like linters, scanners)
3. Task is **repetitive** (will be done many times across projects)

**Start**:
1. Identify your team's biggest governance bottleneck (ADRs? Security reviews? API contracts?)
2. Build one skill to automate it
3. Measure impact (time saved, errors caught)
4. Iterate and expand

**The opportunity**: A small team of architects can "clone" their expertise via skills and scale governance across hundreds of developers.
