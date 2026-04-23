# AI Learning Path for Technical Architects

A structured learning guide for technical architects looking to understand modern AI/ML capabilities, agentic workflows, and architecture automation patterns.

Disclaimer:
This learning path been created from a learning path based on human intiution. Learning notes were fed into Claude Code, it was tasked with producing this learning path based on those notes. The path has been reviewed by a human, any fully AI generated content that has not been validated has been marked with **(AI Generated)**. Additionally this guide contains hypotheses about how AI Agents could be used to aid Architects, these have been marked with **(Hypothesis)**.

## Who This Is For

This learning path is designed for technical leaders who need to:
- Understand how AI can augment development workflows
- Evaluate AI tooling and patterns for their teams
- Design systems that integrate with AI/ML capabilities
- Make informed build vs. buy decisions for AI-powered solutions

## How to Use This Guide

Each topic includes:
- **Video resources** (primary learning material)
- **Key concepts** (80/20 insights)
- **How it works** (technical explanations with diagrams)
- **Common approaches** (trade-offs, no prescriptive "winners")
- **Try it yourself** (hands-on experiments where applicable)

---

## Capability Matrix

| Topic | Difficulty | Key Architectural Takeaway | Section |
|-------|-----------|---------------------------|---------|
| **Large Language Models** | Introductory | What is a Large Language Model | [01-foundations](./01-foundations/ai-large-language-models.md) |
| **Agentic AI Evolution** | Introductory | How LMs evolved from simple prompts → RAG → autonomous agents | [01-foundations](./01-foundations/agentic-ai-evolution.md) |
| **AI Safety & Control** | Intermediate | Understanding adversarial AI, monitoring, and the capacity gap | [01-foundations](./01-foundations/ai-safety-control.md) |
| **MLOps Principles** | Introductory | ML systems are 10% ML, 90% good engineering | [01-foundations](./01-foundations/mlops-principles.md) |
| **Prompt Engineering** | Introductory | CoT, few-shot examples, systematic evaluation | [02-core-patterns](./02-core-patterns/prompt-engineering.md) |
| **RAG Architecture** | Intermediate | Vector stores, chunking, retrieval for domain-specific knowledge | [02-core-patterns](./02-core-patterns/rag-architecture.md) |
| **Agentic Workflows** | Intermediate | ReAct, reflexion, tool use, multi-agent collaboration | [02-core-patterns](./02-core-patterns/agentic-workflows.md) |
| **Vibe Engineering** | Intermediate | The paradigm shift in AI-assisted development | [03-development-workflows](./03-development-workflows/vibe-engineering.md) |
| **Model Context Protocol** | Intermediate | Using AI to deliver practical tooling  | [03-development-workflows](./03-development-workflows/model-context-protocol.md) |
| **Spec-Driven Development** | Intermediate | Context compression: maintaining understanding at AI generation speed | [03-development-workflows](./03-development-workflows/spec-driven-development.md) |
| **Agent Skills Framework** | Intermediate | Anthropic Skills: procedural vs. declarative AI capabilities | [03-development-workflows](./03-development-workflows/agent-skills-framework.md) |
| **Context Management** | Introductory | Giving LMs the right context to reduce hallucinations | [03-development-workflows](./03-development-workflows/context-management.md) |
| **ADR Automation** | Advanced | Using agent skills for architecture governance | [04-governance-automation](./04-governance-automation/adr-automation.md) |
| **Security Automation** | Advanced | Threat modeling and IaC security auditing with agents | [04-governance-automation](./04-governance-automation/security-automation.md) |
| **Integration Contracts** | Advanced | API contract validation and schema governance | [04-governance-automation](./04-governance-automation/integration-contracts.md) |
| **Architectural Drift Prevention** | Advanced | Preventing the comprehension gap and measuring drift with ADI | [04-governance-automation](./04-governance-automation/architectural-drift-prevention.md) |

---

## Suggested Learning Paths

### Path 1: Foundations First (Recommended for teams new to AI)
```
01-foundations/
  → ai-large-language-models.md
  → agentic-ai-evolution.md
  → mlops-principles.md

02-core-patterns/
  → prompt-engineering.md
  → rag-architecture.md

03-development-workflows/
 
  → vibe-engineering.md
  → context-management.md
```

### Path 2: Hands-On Development (For teams already using AI tools)
```
03-development-workflows/
  → model-context-protocol.md
  → vibe-engineering.md
  → agent-skills-framework.md
  → context-management.md

02-core-patterns/
  → prompt-engineering.md
  → agentic-workflows.md
```

### Path 3: Architecture Governance (For teams experienced in leveraging AI tools)
```
01-foundations/
  → ai-safety-control.md

02-core-patterns/
  → agentic-workflows.md
  → model-context-protocol.md


04-governance-automation/
  → adr-automation.md
  → security-automation.md
  → integration-contracts.md
```

---

## Quick Navigation

### By Role
- **Enterprise Architects**: Focus on 04-governance-automation
- **Solution Architects**: Start with 02-core-patterns + 03-development-workflows
- **Security Architects**: Prioritise ai-safety-control.md + security-automation.md
- **Team Leads**: Begin with vibe-engineering.md + context-management.md

### By Use Case
- **Evaluating AI tools**: Start with agent-skills-framework.md + vibe-engineering.md
- **Building AI-powered systems**: Focus on 02-core-patterns section
- **Governance & safety**: Navigate to 01-foundations/ai-safety-control.md + 04-governance-automation
- **Team enablement**: Begin with 03-development-workflows section

---

## Resources

- [Video Library](./resources/videos.md) - All curated video content organised by topic
- [Tool Comparison](./resources/tools.md) - Claude Code, Cursor, MCP servers, and more
- [Glossary](./resources/glossary.md) - Key terms and concepts

---

## Contributing

This is a living learning guide. If you've discovered valuable resources or have insights to add, contributions are welcome.
