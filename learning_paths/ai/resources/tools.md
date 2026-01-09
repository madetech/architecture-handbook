# Tool Comparison Matrix (AI Generated)

A practical guide to AI/ML tools for Technical Architects. Organised by category with trade-off analysis.

---

## AI-Assisted Development Tools

### Code Editors & IDEs

| Tool | Type | Key Features | Best For | Trade-offs |
|------|------|--------------|----------|-----------|
| **Cursor** | AI-native IDE (VSCode fork) | Composer mode (multi-file edits), voice-to-code, context-aware | Architects who want control + velocity | ✅ High control, iterative feedback<br>❌ Paid product, vendor lock-in |
| **Claude Code** | CLI agent | Agent skills, MCP integration, terminal-based | Architects building governance automation | ✅ Extensible (skills), runs locally<br>❌ Command-line only, learning curve |
| **GitHub Copilot** | Autocomplete plugin | Inline suggestions, works in any IDE | Quick productivity boost, low friction | ✅ IDE-agnostic, low learning curve<br>❌ Line-level only (no multi-file) |
| **Replit Agent** | Cloud IDE | Full-stack app generation, hosting included | Rapid prototyping, demos | ✅ Zero setup, instant deploy<br>❌ Cloud-only, less control |
| **Devin** | Autonomous agent | Fully autonomous (plans, codes, tests, deploys) | Experimental, high-risk projects | ✅ Minimal human input<br>❌ Low control, unpredictable |

**Architect's Decision Framework**:
- Need **control** + **multi-file edits**? → Cursor
- Need **governance automation**? → Claude Code
- Need **quick autocomplete**? → GitHub Copilot
- Need **rapid prototyping**? → Replit Agent
- Experimental / research? → Devin

---

## LLM Providers

### Model Comparison (As of January 2026)

| Provider | Models | Strengths | Weaknesses | Pricing |
|----------|--------|-----------|------------|---------|
| **Anthropic** | Claude Opus 4.5, Sonnet 4.5, Haiku | Long context (200k), tool use, safety | Not best at math/code (vs GPT-4) | ££££ (Opus), £££ (Sonnet), £ (Haiku) |
| **OpenAI** | GPT-4o, GPT-4 Turbo, GPT-3.5 | Code generation, reasoning, broad training | Shorter context (128k), less safe | ££££ (GPT-4), ££ (GPT-3.5) |
| **Google** | Gemini 2.0, Gemini Pro | Multimodal (video, audio), fast inference | Newer, less battle-tested | £££ (2.0), ££ (Pro) |
| **Open Source** | Llama 3.1, Mixtral, Qwen | Free, runs locally, no data sent to cloud | Lower quality, need infrastructure | Free (compute cost only) |

**Key Insight**: Model "best for coding" changes monthly. Follow community (Twitter, Reddit) to track current leader.

**Architect's Decision**:
- **Production systems**: Claude (safety, reliability)
- **Code generation**: GPT-4o or Gemini 2.0 (check current benchmarks)
- **Cost-sensitive**: Haiku or GPT-3.5
- **Privacy-critical**: Open source (Llama, Mixtral) self-hosted

---

## RAG & Vector Databases

| Database | Type | Best For | Trade-offs |
|----------|------|----------|-----------|
| **Pinecone** | Managed, cloud-native | Production, scale quickly | ✅ Easy setup, auto-scaling<br>❌ Vendor lock-in, cost at scale |
| **Weaviate** | Open-source, self-hosted | Need control, hybrid search (vector + keyword) | ✅ Flexible, open-source<br>❌ Operational overhead, slower setup |
| **pgvector** | Postgres extension | Already using Postgres, simple stack | ✅ No new infrastructure<br>❌ Less optimised for scale |
| **Chroma** | In-memory, local | Prototyping, small datasets | ✅ Fast setup, free<br>❌ Not production-ready, no persistence |
| **Qdrant** | Open-source, Rust-based | High performance, self-hosted | ✅ Fast, efficient<br>❌ Smaller community, newer tool |

**Architect's Decision**:
- **Prototype**: Chroma (free, fast setup)
- **Production (small scale)**: pgvector (leverage existing Postgres)
- **Production (large scale, managed)**: Pinecone (ease of use)
- **Production (large scale, self-hosted)**: Weaviate or Qdrant (control + cost)

---

## MLOps Platforms

| Platform | Type | Best For | Trade-offs |
|----------|------|----------|-----------|
| **AWS SageMaker** | Managed, cloud | AWS-native, integrated with AWS services | ✅ Built-in features, auto-scaling<br>❌ Vendor lock-in, higher cost |
| **Azure ML** | Managed, cloud | Azure-native, enterprise integration | ✅ Enterprise features, security<br>❌ Vendor lock-in, complex UI |
| **GCP Vertex AI** | Managed, cloud | GCP-native, good for BigQuery integration | ✅ Integrated ML tools<br>❌ Vendor lock-in, newer platform |
| **MLflow** | Open-source | Experiment tracking, model registry | ✅ Vendor-neutral, free<br>❌ No compute (need to integrate) |
| **Kubeflow** | Open-source, Kubernetes | Full ML pipelines on K8s | ✅ Cloud-agnostic, powerful<br>❌ High complexity, steep learning curve |

**Architect's Decision**:
- **Already on AWS**: SageMaker (easiest path)
- **Already on Azure**: Azure ML
- **Multi-cloud / avoid lock-in**: MLflow + Kubernetes
- **Need full control**: Kubeflow (if team has K8s expertise)

---

## Context Management Tools

| Tool | Purpose | Best For | Trade-offs |
|------|---------|----------|-----------|
| **.cursorrules** | Project conventions (Cursor-specific) | Coding standards, architecture decisions | ✅ Simple (one file), built-in to Cursor<br>❌ Cursor-only, limited to text rules |
| **.clinerules** | Project conventions (Claude Code) | Similar to .cursorrules but for Claude Code | ✅ Works with CLI agent<br>❌ Claude Code-only |
| **Claude Projects** | Persistent context (Anthropic) | Project-specific context across sessions | ✅ Cross-session memory<br>❌ Anthropic-only, cloud-based |
| **ChatGPT Custom Instructions** | User-level context (OpenAI) | Personal preferences, global rules | ✅ Works across all chats<br>❌ User-level (not project-level) |
| **MCP Servers** | Data connectivity | Connect LM to Slack, GitHub, databases | ✅ Real-time data access<br>❌ Requires setup, security config |

**Architect's Decision**:
- **Single tool (Cursor)**: Use .cursorrules
- **Claude Code workflows**: Use .clinerules + Agent Skills
- **Multi-session projects**: Claude Projects
- **Need data integration**: MCP Servers

---

## Security & Compliance Tools

### IaC Security Scanners

| Tool | Coverage | Best For | Trade-offs |
|------|----------|----------|-----------|
| **tfsec** | Terraform | Terraform-specific, fast | ✅ Fast, detailed reports<br>❌ Terraform-only |
| **Checkov** | Terraform, CloudFormation, K8s, ARM | Multi-platform IaC | ✅ Broad coverage, active development<br>❌ Slower than tfsec |
| **Terrascan** | Terraform, K8s, Docker | Policy-as-code | ✅ Custom policies<br>❌ Smaller community |
| **Snyk IaC** | Multi-platform | Enterprise, integrated with Snyk ecosystem | ✅ Enterprise features, good UI<br>❌ Paid product |

**Architect's Decision**:
- **Terraform-only**: tfsec (speed)
- **Multi-platform IaC**: Checkov (coverage)
- **Need custom policies**: Terrascan
- **Enterprise with budget**: Snyk IaC

### Threat Modeling Tools

| Tool | Type | Best For | Trade-offs |
|------|------|----------|-----------|
| **Microsoft Threat Modeling Tool** | GUI-based | Windows users, STRIDE methodology | ✅ Free, structured STRIDE<br>❌ Windows-only, manual process |
| **OWASP Threat Dragon** | Web/desktop | Cross-platform, open-source | ✅ Open-source, multi-platform<br>❌ Less mature than MS tool |
| **IriusRisk** | Enterprise platform | Large orgs, compliance tracking | ✅ Automated, enterprise features<br>❌ Expensive, complex setup |
| **Agent Skills** | AI-powered | Automated STRIDE during design phase | ✅ Fast, integrated into workflow<br>❌ Requires building the skill |

**Architect's Decision**:
- **Manual threat modeling**: MS Threat Modeling Tool (structured)
- **Automated (small team)**: Build agent skill (see [Security Automation](../04-governance-automation/security-automation.md))
- **Enterprise compliance**: IriusRisk (if budget allows)

---

## Schema & API Tools

| Tool | Purpose | Best For | Trade-offs |
|------|---------|----------|-----------|
| **OpenAPI** | REST API schemas | REST APIs, code generation | ✅ Industry standard, tooling ecosystem<br>❌ Verbose for simple APIs |
| **GraphQL** | API query language + schema | Flexible queries, strong typing | ✅ Client-driven queries<br>❌ More complex backend |
| **Avro** | Schema for events | Kafka, event-driven systems | ✅ Schema evolution support<br>❌ Requires schema registry |
| **Protobuf** | Binary serialization + schema | gRPC, high-performance systems | ✅ Compact, fast<br>❌ Not human-readable |
| **OpenAPI Diff** | Breaking change detection | CI/CD validation | ✅ Automated detection<br>❌ CLI-only, basic reports |
| **Pact** | Consumer-driven contracts | Microservices integration testing | ✅ Consumer-driven, good for testing<br>❌ Setup overhead |

**Architect's Decision**:
- **REST APIs**: OpenAPI (standard)
- **Event-driven**: Avro (with schema registry like Confluent)
- **High-performance RPC**: Protobuf + gRPC
- **Breaking change detection**: OpenAPI Diff (or build agent skill)
- **Consumer-driven**: Pact (integration testing)

---

## Governance & Architectural Drift Prevention

### Policy Enforcement Tools

| Tool | Type | Best For | Trade-offs |
|------|------|----------|-----------|
| **OPA (Open Policy Agent)** | Policy engine | Enforcing architectural rules in code | ✅ Flexible, declarative policies<br>❌ Learning curve (Rego language) |
| **Conftest** | OPA for configs | Testing IaC, K8s manifests | ✅ Easy integration with CI/CD<br>❌ Limited to static analysis |
| **Kyverno** | Kubernetes-native | K8s policy enforcement | ✅ Simpler than OPA for K8s<br>❌ K8s-only |

**Architect's Decision**:
- **General policy-as-code**: OPA (most flexible)
- **IaC validation**: Conftest (OPA + CI/CD integration)
- **Kubernetes-specific**: Kyverno (easier learning curve)

### Drift Detection & Code Review Tools

| Tool | Focus | Strengths | Gaps |
|------|-------|-----------|------|
| **vFunction** | Architectural drift detection | Visualises true architecture vs. intended, monitors drift in real-time | Observability-focused (tells you drift happened, doesn't prevent it) |
| **CodeRabbit** | AI peer review | Deep, context-aware reviews beyond syntax | Recommender, not enforcer (no comprehension verification gate) |
| **Qodo (Codium)** | AI test generation + review | Good at generating tests, coverage analysis | Focuses on test coverage, not architectural comprehension |
| **Traycer** | Intent-based review | Detects when code "veers off intent," monitors modularity | Still prioritises velocity over understanding |
| **SonarQube** | Code quality + security | Established platform, wide language support | Focuses on bugs/vulnerabilities, not architectural patterns |

**Architect's Decision**:
- **Architectural drift monitoring**: vFunction (if budget allows) or build custom agent skill
- **AI-assisted PR review**: CodeRabbit or Qodo (for velocity)
- **Comprehension verification**: Build custom workflow (see [Architectural Drift Prevention](../04-governance-automation/architectural-drift-prevention.md))
- **Code quality baseline**: SonarQube (complementary to drift tools)

### AST Analysis & Dependency Tools

| Tool | Purpose | Best For | Trade-offs |
|------|---------|----------|-----------|
| **madge** | Dependency graph (JS/TS) | Visualizing module dependencies, circular detection | ✅ Fast, simple<br>❌ JavaScript-only |
| **dependency-cruiser** | Advanced dependency rules | Enforcing architectural boundaries (layers, modules) | ✅ Powerful rule engine<br>❌ Complex configuration |
| **jscodeshift** | AST transformations (JS/TS) | Automated refactoring, codemod creation | ✅ Powerful for migrations<br>❌ JavaScript-only, steep learning curve |
| **semgrep** | Multi-language AST analysis | Finding anti-patterns, enforcing custom rules | ✅ Works across many languages<br>❌ Less architectural focus (more security) |

**Architect's Decision**:
- **Visualise dependencies**: madge (JS/TS) or language-specific tool
- **Enforce boundaries**: dependency-cruiser (JS/TS) or custom AST parser
- **Custom pattern detection**: semgrep (multi-language)

---

## Cost Comparison (Rough Estimates)

### LLM API Costs (per 1M tokens)

| Provider | Model | Input | Output | Use Case |
|----------|-------|-------|--------|----------|
| Anthropic | Claude Opus 4.5 | £15 | £75 | Complex reasoning, long context |
| Anthropic | Claude Sonnet 4.5 | £3 | £15 | Balanced (most use cases) |
| Anthropic | Claude Haiku | £0.25 | £1.25 | High-volume, simple tasks |
| OpenAI | GPT-4o | £5 | £15 | Code generation, general |
| OpenAI | GPT-3.5 Turbo | £0.50 | £1.50 | Cost-sensitive, simple tasks |
| Google | Gemini 2.0 | £4 | £12 | Multimodal, fast inference |

**Cost Optimization Tips**:
- Use cheaper models (Haiku, GPT-3.5) for simple tasks (search, validation)
- Use expensive models (Opus, GPT-4) for complex reasoning
- Cache prompts (reduce input tokens)
- Set max token limits (avoid runaway costs)

---

## Integration Patterns

### Tool Stacks for Common Scenarios

#### Scenario 1: Small Team, Rapid Development
```
Development: Cursor (AI IDE)
Context: .cursorrules (conventions)
LLM: Claude Sonnet (balanced cost/quality)
RAG: pgvector (simple, no new infrastructure)
```

#### Scenario 2: Enterprise, Governance Focus
```
Development: Claude Code (CLI agent)
Context: Agent Skills (ADR, security, contracts)
LLM: Claude Opus (safety, long context)
RAG: Weaviate (self-hosted, control)
IaC Security: Checkov (multi-platform)
Schema: OpenAPI + Pact (contract-driven)
```

#### Scenario 3: ML-Heavy, Cloud-Native
```
MLOps: AWS SageMaker (managed)
LLM: OpenAI GPT-4o (code generation)
Vector DB: Pinecone (managed, scalable)
Monitoring: MLflow (experiment tracking)
```

#### Scenario 4: Cost-Conscious, Open-Source
```
Development: VSCode + GitHub Copilot
LLM: Llama 3.1 (self-hosted)
RAG: Chroma → Qdrant (free, self-hosted)
MLOps: MLflow (free) + Kubernetes
IaC Security: tfsec (free)
```

---

## Evaluation Framework

When evaluating a new AI/ML tool, ask:

### 1. Control vs. Autonomy
- Do you need full control (Cursor, Claude Code)?
- Or prefer high autonomy (Devin, Replit)?

### 2. Cost vs. Quality
- What's your token budget?
- Can you use cheaper models for some tasks?

### 3. Lock-in vs. Convenience
- Is vendor lock-in acceptable (SageMaker, Pinecone)?
- Or do you need portability (MLflow, Weaviate)?

### 4. Setup Time vs. Features
- Need quick start (Chroma, managed services)?
- Or willing to invest in setup (Kubeflow, self-hosted)?

### 5. Team Expertise
- Do you have ML/DevOps expertise?
- Or need managed solutions?

---

## Staying Current

**Model capabilities change monthly.** This comparison is a snapshot (January 2026).

**How to stay updated**:
1. Follow tool-specific Discord/Slack channels
2. Monitor Twitter/X for benchmark updates
3. Check tool release notes monthly
4. Test new models quarterly (benchmark on your workloads)

**Red flags** (tool might be declining):
- No updates in 6+ months
- Community shrinking (Discord going quiet)
- Competitors significantly outperforming

---

## Related Topics

- [Vibe Engineering](../03-development-workflows/vibe-engineering.md) - Tools in practice
- [Agent Skills Framework](../03-development-workflows/agent-skills-framework.md) - Claude Code skills
- [RAG Architecture](../02-core-patterns/rag-architecture.md) - Vector database selection

---

## Key Takeaway

**No "one size fits all" tool.** Your stack should match:
- Team size and expertise
- Control vs. speed requirements
- Budget constraints
- Governance needs

**Start simple**:
1. Pick one AI IDE (Cursor or GitHub Copilot)
2. Pick one LLM (Claude Sonnet or GPT-4o)
3. Use built-in context tools (.cursorrules)
4. Add complexity (RAG, MLOps, Skills) only when needed

**Iterate**: Re-evaluate tools quarterly. The landscape changes fast.
