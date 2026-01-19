# Glossary

Key terms and concepts used throughout the AI for Technical Architects learning path.

---

## A

**ADI (Architectural Drift Index)**
A quantitative metric that measures how much a code change deviates from the planned architecture ("Golden Path"). Formula: ADI = (Σ Vi × Si) / T, where Vi = violation, Si = severity weight, T = total architectural touchpoints. Used to enforce governance thresholds.

**ADR (Architecture Decision Record)**
A document that captures an important architectural decision along with its context and consequences. Typically follows the Nygard format with sections: Status, Context, Decision, Consequences.

**AST (Abstract Syntax Tree)**
A tree representation of source code structure, used for code analysis and transformations. Critical for drift detection and policy enforcement tools.

**Agent**
An AI system that can autonomously perform tasks by combining reasoning, tool use, and iteration. Unlike simple prompts, agents can plan, execute, and adapt.

**Agent Skill**
A portable package (folder) containing instructions (SKILL.md) and executable scripts that give an LLM procedural capabilities. Different from prompts, which are declarative.

**Accidental Complexity**
(Fred Brooks, "No Silver Bullet") Everything added to a system beyond the essential problem: workarounds, defensive code, frameworks, abstractions that made sense years ago. In real codebases, this is tangled with Essential Complexity. AI preserves both equally, unable to distinguish between them.

**Agentic Workflow**
A pattern where LLMs autonomously perform multi-step tasks through planning, reflexion, tool use, or multi-agent collaboration.

**Anthropic**
AI safety company that created Claude (LLM family). Known for constitutional AI and safety research.

**API Contract**
A formal agreement between API provider and consumer defining request/response formats, error codes, and versioning strategy.

**Avro**
A schema-based data serialization format commonly used in event-driven systems (e.g., Kafka).

---

## B

**Blast Radius**
The scope of potential damage if a system component fails. In AI safety, it refers to what an agent could harm if it acts maliciously or incorrectly.

**Bolt-On Security**
Adding security measures after design/implementation, as opposed to "secure-by-design."

**Breaking Change**
A modification to an API or schema that breaks backward compatibility (e.g., removing a required field, changing data types).

---

## C

**Capacity Gap**
The problem where a more capable "untrusted" AI model (U) is monitored by a less capable "trusted" model (T), making it easy for U to hide malicious behavior.

**Chain of Thought (CoT)**
A prompting technique where the LLM is asked to "think step-by-step," externalizing its reasoning process to improve accuracy on complex tasks.

**Checkov**
An open-source security scanner for Infrastructure-as-Code (supports Terraform, CloudFormation, Kubernetes).

**Chroma**
An in-memory, local vector database optimised for prototyping and small-scale RAG applications.

**Chunking**
The process of breaking large documents into smaller, semantically meaningful pieces for RAG systems. Trade-off between context preservation and retrieval precision.

**CKR (Context-to-Code Ratio)**
A metric measuring what percentage of code in a PR can be traced back to the original architectural intent (from MVA or ADRs). Target: >90%. Low CKR indicates AI-generated "extras" (unnecessary code).

**Claude**
Anthropic's family of LLMs (Opus, Sonnet, Haiku). Known for long context windows (200k tokens) and safety features.

**Comprehension Gap**
The growing delta between AI code generation velocity (exponentially increasing) and human comprehension capacity (relatively constant). Leads to engineers merging code they don't fully understand.

**Comprehension Verification**
A code review pattern that requires engineers to prove they understand the logic (not just the syntax) before merge approval. Blocks merge if engineer is "guessing" rather than "knowing."

**Conftest**
A tool that uses OPA policies to test configuration files (IaC, K8s manifests). Commonly integrated into CI/CD pipelines.

**Context Compression**
A three-phase approach (Research → Planning → Implementation) for maintaining understanding at AI generation speed. Compresses hours of exploration into minutes of reading. Also called spec-driven development.

**Claude Code**
Anthropic's CLI tool for AI-assisted development, featuring agent skills and MCP integration.

**Context Window**
The maximum amount of text (measured in tokens) an LLM can process at once. Larger context windows allow for more information but increase cost.

**Cosine Similarity**
A metric for measuring similarity between vectors, commonly used in RAG to find semantically related chunks.

**Cursor**
An AI-native code editor (VSCode fork) with features like Composer mode for multi-file edits and voice-to-code.

---

## D

**Declarative**
Describing **what** should happen (e.g., "Act like a tax lawyer") vs. **how** to do it. Contrast with procedural.

**Defer to Resample**
An AI safety technique where moderately suspicious actions are discarded and the agent is asked to try again, reducing risk without human intervention.

**Deterministic**
Producing the same output given the same input every time. Contrast with probabilistic (LLM behavior).

**Drift**
In ML, the degradation of model performance over time as data patterns change. Requires continuous monitoring and retraining.

---

## E

**Easy**
(Rich Hickey's definition) What's adjacent, within reach, accessible without effort. About proximity, not structure. Examples: copy-paste, install a package, generate with AI. Contrast with Simple. AI is the "ultimate easy button."

**"Easy Button" Trap**
The pattern of accepting AI-generated code without critical analysis because it "looks right" and passes tests. Leads to accumulation of technical debt and the comprehension gap.

**Embedding**
Converting text into a numerical vector representation (e.g., 1536-dimensional array) for similarity search. Semantically similar text has numerically similar vectors.

**Essential Complexity**
(Fred Brooks, "No Silver Bullet") The fundamental difficulty of the problem you're solving. Why your software exists (users need to pay, orders must be fulfilled). Contrast with Accidental Complexity. AI cannot distinguish between them.

**Enterprise Tech Radar**
A governance tool listing approved, experimental, and deprecated technologies for an organisation (inspired by Thoughtworks Tech Radar).

---

## F

**False Positive**
When a security scanner or monitoring system flags a benign action as malicious, overwhelming reviewers with noise.

**Few-Shot Prompting**
Providing 2-5 examples in a prompt to show the LLM the desired output format or style.

**Fine-Tuning**
Training an existing LLM on domain-specific data to specialise it for particular tasks. More expensive than prompting or RAG.

---

## G

**GDPR (General Data Protection Regulation)**
EU privacy law regulating how personal data is collected, processed, and stored. Violations can result in fines up to 4% of revenue.

**Gemini**
Google's family of multimodal LLMs (successor to Bard/PaLM).

**Golden Path**
An enterprise-blessed, standardised approach to solving a common problem (e.g., "use PostgreSQL for relational data," "all S3 access through S3Wrapper"). AI agents often violate the Golden Path because they're trained on generic internet code, not organisation-specific patterns. Enforced via OPA policies and drift detection.

**GPT (Generative Pre-trained Transformer)**
OpenAI's family of LLMs (GPT-3.5, GPT-4, GPT-4o).

---

## H

**Hallucination**
When an LLM generates plausible-sounding but factually incorrect information. Reduced via RAG, grounding, and explicit "I don't know" instructions.

**HyDE (Hypothetical Document Embeddings)**
A RAG technique where the LLM generates a hypothetical answer, embeds it, then searches for real documents similar to the hypothetical answer.

---

## I

**IaC (Infrastructure as Code)**
Managing infrastructure through code (e.g., Terraform, CloudFormation) rather than manual configuration.

**Integration Contract**
See API Contract.

---

## J

**JSON Schema**
A vocabulary for annotating and validating JSON documents, commonly used for API contracts.

**JWT (JSON Web Token)**
A compact, URL-safe token format for securely transmitting information between parties, commonly used for authentication.

---

## K

**K8s (Kubernetes)**
An open-source container orchestration platform for deploying, scaling, and managing containerised applications.

**KMS (Key Management Service)**
A cloud service for managing encryption keys (e.g., AWS KMS, Azure Key Vault).

**Knowledge Atrophy**
The loss of engineering expertise as AI handles implementation details ("the how"), leaving engineers unable to debug, pivot, or mentor when AI-generated code fails. A key risk of the comprehension gap.

---

## L

**Latency**
The time delay between a request and response. Critical in production AI systems (users expect <2 second responses).

**LLM (Large Language Model)**
A neural network trained on massive text datasets to generate human-like text (e.g., GPT-4, Claude, Gemini).

**LM (Language Model)**
Broader term for models that process/generate language (includes LLMs and smaller models).

---

## M

**MCP (Model Context Protocol)**
Anthropic's protocol for connecting LLMs to external data sources (Slack, GitHub, databases).

**Mermaid**
A markdown-based diagramming language (useful for architecture diagrams in documentation).

**MLOps (Machine Learning Operations)**
The practice of deploying and maintaining ML models in production (analogous to DevOps for ML).

**Multi-Agent Collaboration**
An agentic design pattern where specialised agents work together (e.g., one searches, one summarises, one validates).

**MVA (Minimum Viable Architecture)**
A lightweight, context-first scoping process that captures architectural intent before code is written. Ensures the "System of Record" for design decisions is human-authored, not AI-inferred. Produces an "Intent Snapshot" document that agent skills reference.

---

## N

**Non-Breaking Change**
A modification to an API/schema that maintains backward compatibility (e.g., adding optional fields).

**Nygard Format**
A popular ADR template structure (Status, Context, Decision, Consequences) created by Michael Nygard.

---

## O

**OIDC (OpenID Connect)**
An identity layer on top of OAuth 2.0 for authentication.

**OpenAPI**
A specification for defining REST API contracts (formerly Swagger).

**OPA (Open Policy Agent)**
A policy engine for enforcing architectural rules in code using the Rego language. Used for policy-as-code enforcement (e.g., "All S3 access must use S3Wrapper"). Integrates with CI/CD to block non-compliant code before merge.

**OWASP (Open Web Application Security Project)**
A nonprofit organisation focused on improving software security. Known for the OWASP Top 10 vulnerabilities list.

---

## P

**Pact**
A tool for consumer-driven contract testing, ensuring API providers meet consumer expectations.

**pgvector**
A PostgreSQL extension for vector similarity search, useful for RAG on existing Postgres databases.

**PII (Personally Identifiable Information)**
Data that can identify an individual (e.g., SSN, email, phone). Must be protected per GDPR, CCPA, etc.

**Pinecone**
A managed, cloud-native vector database optimised for RAG at scale.

**Pattern Recognition Atrophy**
The loss of ability to recognise architectural problems when you don't understand your own system. Occurs when engineers skip thinking to keep up with AI generation speed. That instinct that says "this is getting complex" atrophies when you don't maintain comprehension.

**Planning (Agent Pattern)**
An agentic design pattern where the LLM breaks complex goals into multi-step plans before execution.

**Procedural**
Describing **how** to do something (e.g., "Here's a Python script to run"). Contrast with declarative.

**Progressive Disclosure**
Loading information incrementally (e.g., loading full skill instructions only when triggered, not upfront).

**Prompt Engineering**
The practice of designing effective prompts to get reliable, consistent outputs from LLMs.

---

## Q

**Qdrant**
An open-source, Rust-based vector database optimised for performance.

---

## R

**RAG (Retrieval Augmented Generation)**
A pattern where LLMs retrieve relevant external data before generating responses, reducing hallucinations and adding domain knowledge.

**ReAct (Reason + Act)**
An agentic pattern where the LLM alternates between reasoning (thinking) and acting (using tools) to solve complex tasks.

**Reflexion**
An agentic design pattern where the LLM examines its own output, critiques it, then regenerates (iterative self-improvement).

**Reranking**
A two-stage retrieval strategy: fast search retrieves top 50 candidates, then a powerful model re-ranks to select the best 5.

**Resample Incrimination**
An AI safety technique where the agent is forced to provide multiple alternative actions. A malicious agent is likely to repeat its attack, revealing a scheming pattern.

---

## S

**Sandboxing**
Running code or agents in an isolated environment to limit the "blast radius" if something goes wrong.

**Schema Registry**
A centralised repository for API/event schemas (e.g., Confluent Schema Registry for Kafka).

**Scheming**
When an AI purposefully waits for the right moment to perform malicious actions (e.g., data exfiltration).

**Semantic Versioning (SemVer)**
A versioning scheme (MAJOR.MINOR.PATCH) where MAJOR = breaking changes, MINOR = new features (non-breaking), PATCH = bug fixes.

**Similarity Search**
Finding items (documents, images, etc.) that are numerically "close" in vector space, used in RAG.

**Simple**
(Rich Hickey's definition) One fold, one braid, no entanglement. About structure, not proximity. Each piece does one thing and doesn't intertwine with others. Contrast with Easy. Simplicity requires thought, design, and untangling—you can't make something simple by wishing it.

**SKILL.md**
The instruction file in an Anthropic Agent Skill folder, describing when and how to use the skill.

**STRIDE**
Microsoft's threat modeling framework: Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege.

**System Prompt**
The base instructions given to an LLM at the start of a conversation, setting its behavior and persona.

---

## T

**Tech Radar**
A visualization of technology choices categorised by maturity (Adopt, Trial, Assess, Hold). See Thoughtworks Tech Radar.

**tfsec**
A security scanner specifically for Terraform code.

**Threat Modeling**
The process of identifying security threats in a system design (e.g., using STRIDE framework).

**Token**
The basic unit of text for LLMs (roughly 0.75 words). LLMs have token limits (context window) and pricing is per token.

**Tool Use (Agent Pattern)**
An agentic design pattern where the LLM can call external functions/APIs to gather data or perform actions.

**Trusted Monitoring**
An AI safety pattern where a trusted model (T) monitors the actions of an untrusted model (U) and flags suspicious behavior.

---

## U

**Utility Trap**
The tendency for users to grant agents high autonomy to reduce tedious oversight, inadvertently creating safety risks.

---

## V

**Vector Database**
A database optimised for storing and searching high-dimensional vectors (embeddings), used in RAG systems.

**Vector Embedding**
See Embedding.

**Vibe Coding**
(Coined by Andrej Karpathy) A workflow where the developer focuses on the desired outcome ("vibe") and lets the LLM handle implementation details.

**Vibe Engineering**
An architect-level approach to vibe coding, maintaining high-level structural standards while using AI for implementation.

---

## W

**Weaviate**
An open-source vector database supporting hybrid search (vector + keyword).

---

## Z

**Zero-Shot Prompting**
Asking an LLM to perform a task without providing examples (contrast with few-shot prompting).

**Zod**
A TypeScript schema validation library commonly used for API request/response validation.

**Zustand**
A lightweight state management library for React (alternative to Redux).

---

## Acronyms Quick Reference

| Acronym | Full Term | Category |
|---------|-----------|----------|
| ADI | Architectural Drift Index | Governance |
| ADR | Architecture Decision Record | Governance |
| API | Application Programming Interface | Integration |
| AST | Abstract Syntax Tree | Code Analysis |
| CKR | Context-to-Code Ratio | Governance |
| CoT | Chain of Thought | Prompting |
| GDPR | General Data Protection Regulation | Compliance |
| GPT | Generative Pre-trained Transformer | LLM |
| IaC | Infrastructure as Code | DevOps |
| JWT | JSON Web Token | Security |
| K8s | Kubernetes | Infrastructure |
| KMS | Key Management Service | Security |
| LLM | Large Language Model | AI |
| LM | Language Model | AI |
| MCP | Model Context Protocol | Integration |
| ML | Machine Learning | AI |
| MLOps | Machine Learning Operations | DevOps |
| MVA | Minimum Viable Architecture | Governance |
| NFR | Non-Functional Requirement | Architecture |
| OIDC | OpenID Connect | Security |
| OPA | Open Policy Agent | Governance |
| OWASP | Open Web Application Security Project | Security |
| PII | Personally Identifiable Information | Privacy |
| RAG | Retrieval Augmented Generation | Pattern |
| ROI | Return on Investment | Business |
| SemVer | Semantic Versioning | Standards |
| STRIDE | Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege | Security |
| TCO | Total Cost of Ownership | Business |

---

## Related Topics

- [Agentic AI Evolution](../01-foundations/agentic-ai-evolution.md) - Core concepts in depth
- [Prompt Engineering](../02-core-patterns/prompt-engineering.md) - Prompting techniques
- [Agent Skills Framework](../03-development-workflows/agent-skills-framework.md) - Skills terminology

---

## Contributing

If you encounter a term in the learning path that's not defined here, please suggest an addition.

**Format**:
```
**Term**
Clear, concise definition (1-3 sentences). Include practical context for Technical Architects.
```

**Quality standards**:
- Define for a technical audience (not beginners)
- Focus on practical understanding over academic precision
- Include trade-offs or "why it matters" where relevant
