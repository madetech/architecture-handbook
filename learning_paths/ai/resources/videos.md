# Video Library (AI Generated)

A curated collection of video resources organised by topic. All videos are referenced throughout the learning path.

---

## Foundations

### Agentic AI Evolution

**[Stanford Webinar - Agentic AI: A Progression of Language Model Usage](https://www.youtube.com/watch?v=kJLiOGle3Lw)** (90 min)
- **Speaker**: Stanford AI Lab
- **Topics**: Prompt engineering, RAG, ReAct patterns, agentic design patterns
- **Key Sections**:
  - 0:00 - Effective prompting strategies
  - 20:00 - RAG architecture and implementation
  - 40:00 - Agentic workflows (planning, reflexion, tool use, multi-agent)
- **Best for**: Comprehensive overview of LM evolution
- **Referenced in**:
  - [Agentic AI Evolution](../01-foundations/agentic-ai-evolution.md)
  - [Prompt Engineering](../02-core-patterns/prompt-engineering.md)
  - [RAG Architecture](../02-core-patterns/rag-architecture.md)
  - [Agentic Workflows](../02-core-patterns/agentic-workflows.md)

---

### AI Safety & Control

**[The Hard Problem of Controlling Powerful AI Systems - Computerphile](https://www.youtube.com/watch?v=JAcwtV_bFp4)** (30 min)
- **Speaker**: Computerphile
- **Topics**: Adversarial AI, scheming detection, trusted monitoring, capacity gap
- **Key Concepts**:
  - Utility trap (users grant too much autonomy)
  - Adversarial shift (AI as the adversary)
  - Mitigation strategies (defer to resample, resample incrimination)
- **Best for**: Understanding security implications of agentic systems
- **Referenced in**:
  - [AI Safety & Control](../01-foundations/ai-safety-control.md)

---

### MLOps Principles

**[Principles of Good Machine Learning Systems Design - Chip Huyen, Stanford MLSys Seminar](https://www.youtube.com/watch?v=c_AUuTuPA5k)** (90 min)
- **Speaker**: Chip Huyen (ML infrastructure expert)
- **Topics**: ML system design, research vs. production infrastructure, the 10/90 rule
- **Key Principles**:
  - ML is 10% ML, 90% engineering
  - Start simple (simple models → optimised simple → complex)
  - Production infrastructure ≠ research infrastructure
- **Best for**: Architects evaluating ML platform investments
- **Referenced in**:
  - [MLOps Principles](../01-foundations/mlops-principles.md)

---

## Development Workflows

### Vibe Engineering

**[From Vibe Coding To Vibe Engineering – Kitze, Sizzy](https://www.youtube.com/watch?v=JV-wY5pxXLo)** (60 min)
- **Speaker**: Kitze (Sizzy founder, developer productivity expert)
- **Topics**: Vibe engineering, Cursor Composer, voice-to-code, context management
- **Key Sections**:
  - 10:00 - Vibe coding vs. vibe engineering
  - 25:00 - Tools and workflows (Cursor Composer)
  - 35:00 - Context is king (rules files, memories)
  - 45:00 - The "PITA developer" and resistance to AI
  - 55:00 - Future implications (legacy AI code market)
- **Best for**: Understanding how AI changes developer workflows
- **Referenced in**:
  - [Vibe Engineering](../03-development-workflows/vibe-engineering.md)
  - [Context Management](../03-development-workflows/context-management.md)

---

### Spec-Driven Development (Context Compression)

**[Shipping Code You Don't Understand - Netflix Engineer at AI Engineer Summit](https://www.youtube.com/watch?v=eIoohUmYpGI)** (20 min)
- **Speaker**: Netflix Engineer (AI adoption lead)
- **Topics**: The knowledge gap, simple vs. easy, context compression, three-phase approach
- **Key Sections**:
  - 0:00 - The confession: shipping code without understanding
  - 5:00 - Simple vs. Easy (Rich Hickey's definition)
  - 8:00 - Essential vs. Accidental Complexity (Fred Brooks)
  - 10:00 - The conversational complexity trap
  - 12:00 - Three-phase approach: Research → Planning → Implementation
  - 16:00 - Real example: Netflix OAuth migration
  - 18:00 - Pattern recognition atrophy
- **Best for**: Understanding how to maintain comprehension at AI generation speed
- **Referenced in**:
  - [Spec-Driven Development](../03-development-workflows/spec-driven-development.md)
  - [Vibe Engineering](../03-development-workflows/vibe-engineering.md)
  - [Architectural Drift Prevention](../04-governance-automation/architectural-drift-prevention.md)

---

### Agent Skills Framework

**[Don't Build Agents, Build Skills Instead – Barry Zhang & Mahesh Murag, Anthropic](https://www.youtube.com/watch?v=CEvIs9y1uog)** (45 min)
- **Speakers**: Barry Zhang & Mahesh Murag (Anthropic team)
- **Topics**: Anthropic Skills framework, progressive disclosure, MCP stack
- **Key Concepts**:
  - Skills vs. high-quality prompts (procedural vs. declarative)
  - Skills vs. .cursorrules (capabilities vs. conventions)
  - The folder paradigm (SKILL.md + scripts/)
  - MCP + Skills + Runtime stack
- **Best for**: Understanding how to build reusable AI expertise
- **Referenced in**:
  - [Agent Skills Framework](../03-development-workflows/agent-skills-framework.md)
  - [ADR Automation](../04-governance-automation/adr-automation.md)
  - [Security Automation](../04-governance-automation/security-automation.md)
  - [Integration Contracts](../04-governance-automation/integration-contracts.md)

---

## By Topic Area

### Prompt Engineering
- ✅ [Stanford Webinar - Agentic AI](https://www.youtube.com/watch?v=kJLiOGle3Lw) (0:00 - 30:00)
  - Clear instructions, few-shot examples, CoT reasoning

### RAG Architecture
- ✅ [Stanford Webinar - Agentic AI](https://www.youtube.com/watch?v=kJLiOGle3Lw) (20:00 - 50:00)
  - Chunking, embedding, vector databases, retrieval strategies

### Security & Safety
- ✅ [Computerphile - Controlling AI Systems](https://www.youtube.com/watch?v=JAcwtV_bFp4)
  - Trusted monitoring, capacity gap, adversarial AI

### ML System Design
- ✅ [Chip Huyen - ML Systems Design](https://www.youtube.com/watch?v=c_AUuTuPA5k)
  - Research vs. production, the 10/90 rule, principles of good ML systems

### Modern Development Workflows
- ✅ [Kitze - Vibe Engineering](https://www.youtube.com/watch?v=JV-wY5pxXLo)
  - Context management, voice-to-code, Cursor workflows

### Architecture Governance
- ✅ [Anthropic - Agent Skills](https://www.youtube.com/watch?v=CEvIs9y1uog)
  - Building governance skills (ADR, security, contracts)

---

## By Duration

### Short (< 45 min)
- [Computerphile - Controlling AI Systems](https://www.youtube.com/watch?v=JAcwtV_bFp4) (30 min)
- [Anthropic - Agent Skills](https://www.youtube.com/watch?v=CEvIs9y1uog) (45 min)

### Medium (45-90 min)
- [Kitze - Vibe Engineering](https://www.youtube.com/watch?v=JV-wY5pxXLo) (60 min)
- [Stanford - Agentic AI](https://www.youtube.com/watch?v=kJLiOGle3Lw) (90 min)
- [Chip Huyen - ML Systems](https://www.youtube.com/watch?v=c_AUuTuPA5k) (90 min)

### Long (> 90 min)
- None in current collection

**Recommended viewing order**:
1. Stanford - Agentic AI (foundations)
2. Kitze - Vibe Engineering (practical workflows)
3. Anthropic - Agent Skills (governance automation)
4. Chip Huyen - ML Systems (if ML-focused)
5. Computerphile - Controlling AI (safety considerations)

---

## Supplementary Resources

### Deep Dive Learning Paths
- **[Made With ML](https://madewithml.com/)** - Comprehensive hands-on MLOps course
  - Model training, evaluation, deployment
  - Production monitoring and debugging
  - Free, project-based learning

### Documentation & Guides
- **[Anthropic's Claude Agent Guide](https://docs.anthropic.com/claude/docs/agents)** - Building agents with Claude API
- **[OpenAI Cookbook - RAG Examples](https://cookbook.openai.com/examples/question_answering_using_embeddings)** - Code examples for RAG
- **[Pinecone - What is RAG?](https://www.pinecone.io/learn/retrieval-augmented-generation/)** - Practical RAG implementation guide

### Tools & Standards
- **[Thoughtworks Tech Radar](https://www.thoughtworks.com/radar)** - Example of technology governance at scale
- **[Michael Nygard ADR Templates](https://github.com/joelparkerhenderson/architecture-decision-record)** - Standard ADR formats
- **[OWASP Top 10](https://owasp.org/www-project-top-ten/)** - Common security vulnerabilities
- **[STRIDE Threat Modeling](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats)** - Microsoft's threat modeling framework

---

## Community & Updates

### Staying Current
As noted in the Vibe Engineering video, AI model capabilities change rapidly. Stay updated via:

- **Twitter/X**: Follow AI researchers, tool builders, early adopters
- **Discord/Slack**: Join communities for specific tools (Cursor, Claude Code, etc.)
- **Reddit**: r/LocalLLaMA, r/MachineLearning, r/ClaudeAI
- **YouTube**: Subscribe to channels covering AI developments

### Key Accounts to Follow (as of 2026)
- Andrej Karpathy (coined "vibe coding")
- Anthropic (Claude updates)
- OpenAI (GPT updates)
- Chip Huyen (MLOps insights)
- Tool-specific accounts (Cursor, Replit, etc.)

---

## How to Use This Library

### For Teams New to AI
**Start with**: Stanford Webinar (foundations) → Kitze Vibe Engineering (practical)

### For Experienced Developers
**Start with**: Anthropic Agent Skills → Stanford Webinar (workflows section)

### For Security Architects
**Start with**: Computerphile (safety) → Stanford Webinar (agentic patterns) → Anthropic Skills (governance)

### For Enterprise Architects
**Start with**: Chip Huyen (ML systems) → Anthropic Skills (governance) → Stanford Webinar (patterns)

---

## Contributing

Found a valuable video resource? Suggest additions by:
1. Ensuring it's relevant to Technical Architects
2. Providing a brief description and key topics
3. Identifying which learning path topics it supports

**Quality over quantity**: Only include videos that provide unique insights or practical value for architects.
