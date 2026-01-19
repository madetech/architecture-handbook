# Context Management for LLMs

**Difficulty**: Introductory
**Time Investment**: 1 hour
**Prerequisites**: Basic understanding of how LLMs work

---

## Learning Resources (Start Here)

### Primary Videos
- **[From Vibe Coding To Vibe Engineering – Kitze](https://www.youtube.com/watch?v=JV-wY5pxXLo)** (60 min)
  - Section on "Context is King" (around 35 min mark)
  - Practical examples of context files and memories

- **[Stanford Webinar - Agentic AI](https://www.youtube.com/watch?v=kJLiOGle3Lw)** (90 min)
  - "Provide References & Context" section (around 20 min mark)

---

## Why This Matters

**The fundamental truth**: LLMs are not mind readers.

Without proper context, an LM will:
- Generate generic, boilerplate code
- Violate your team's conventions
- Make incorrect assumptions about your architecture
- Hallucinate when it doesn't know the answer

**With proper context**, the same LM:
- Generates code that fits seamlessly into your project
- Follows your team's patterns
- Admits when it doesn't have information
- Produces production-ready outputs

Managing context is how you ensure AI tools **amplify** your team's productivity instead of creating cleanup work.

---

## Key Concepts

### The Context Hierarchy

```
┌─────────────────────────────────────┐
│  System Prompt                      │  ← Base behavior (set by tool vendor)
├─────────────────────────────────────┤
│  Project Context                    │  ← Your conventions, standards
│  - .cursorrules, .clinerules        │
│  - ADRs, design docs                │
├─────────────────────────────────────┤
│  Session Memory                     │  ← What happened earlier in this chat
│  - Previous messages                │
├─────────────────────────────────────┤
│  Immediate Prompt                   │  ← The current user request
└─────────────────────────────────────┘
```

**Priority**: Lower levels override higher levels.
- Immediate prompt > Session memory > Project context > System prompt

**Architect's role**: Design the **Project Context** layer to encode team knowledge.

---

## Context Delivery Mechanisms

### 1. Rules Files (`.cursorrules`, `.clinerules`)

**What they are**: Plain text files that define project conventions

**When loaded**: Automatically at project start (IDE-level)

**Best for**: Coding standards, architecture decisions, tooling choices

**Example `.cursorrules`**:
```markdown
# Tech Stack
- Framework: Next.js 14 (App Router)
- Language: TypeScript (strict mode)
- Styling: Tailwind CSS
- State: Zustand
- Database: Prisma + PostgreSQL
- Auth: NextAuth.js

# Code Conventions
- Use named exports (no default exports)
- Place components in /features/[feature-name]
- API routes in /app/api/[resource]
- Use React Server Components by default
- Client components only when needed (mark with 'use client')

# Architecture Decisions
- See /docs/adr/ for all ADRs
- ADR-001: Use server actions instead of API routes where possible
- ADR-003: All database queries go through /lib/db wrapper

# Quality Standards
- All functions must have TSDoc comments
- No `any` types (use `unknown` if needed)
- Test coverage minimum: 80% for business logic
```

**Impact**: The LM now knows "how we do things here" and generates code that fits your patterns.

---

### 2. Documentation Files

**What they are**: Markdown files explaining architecture, patterns, decisions

**When loaded**: Referenced explicitly or via RAG

**Best for**: Complex architecture explanations, integration patterns, runbooks

**Key files to maintain**:
```
/docs/
├── architecture/
│   ├── system-overview.md    # C4 context diagram
│   ├── data-flow.md          # How data moves through the system
│   └── security-model.md     # Auth, authz, data protection
├── adr/
│   ├── 001-use-nextjs.md
│   ├── 002-database-choice.md
│   └── template.md
└── patterns/
    ├── error-handling.md     # Standard error patterns
    ├── api-integration.md    # How to call external APIs
    └── testing.md            # Testing strategies
```

**How to use**:
- **Option A**: Link in `.cursorrules`: "See /docs/patterns/ for standard patterns"
- **Option B**: RAG-based search: LM retrieves relevant docs when needed

---

### 3. Memories (Persistent Session State)

**What they are**: Facts the LM should remember across sessions

**When loaded**: At session start (tool-dependent)

**Best for**: Project-specific context that doesn't fit in rules files

**Example memories**:
```
- The "admin dashboard" refers to /app/admin, not /features/dashboard
- When user says "API", they mean the internal GraphQL API, not REST
- The team prefers optimistic UI updates (don't wait for server response)
- "The database" is always PostgreSQL prod instance, not local
```

**Tools that support memories**:
- Claude Projects (Anthropic)
- ChatGPT Custom Instructions (OpenAI)
- Cursor's workspace memory

---

### 4. Inline Context (In the Prompt)

**What it is**: Providing context directly in the user's request

**When to use**: When context is specific to this task, not project-wide

**Example**:
```
Bad prompt:
"Fix the authentication bug"

Good prompt:
"Fix the authentication bug in /lib/auth.ts where users aren't redirected
after login. Context: We use NextAuth.js with JWT tokens. The redirect
should go to /dashboard for normal users, /admin for admins. See ADR-005
for our auth flow."
```

**Why it works**: The LM doesn't have to guess; you've provided all relevant info.

---

## Common Approaches

### Approach 1: Minimal Context (Generic AI)
**What**: No rules files, no documentation, no memories
**Use case**: Quick prototypes, throwaway code
**Trade-offs**:
- ✅ Fast to set up
- ❌ Generic, boilerplate code
- ❌ High cleanup effort

---

### Approach 2: Rules Files Only
**What**: `.cursorrules` with conventions
**Use case**: Small teams, consistent stack
**Trade-offs**:
- ✅ Low maintenance (one file)
- ✅ Good for coding standards
- ❌ Limited for complex architecture decisions

---

### Approach 3: Documentation + RAG
**What**: Comprehensive docs in `/docs`, LM retrieves as needed
**Use case**: Large projects, complex architecture
**Trade-offs**:
- ✅ Scales to complex systems
- ✅ Self-documenting (humans can read too)
- ❌ Requires RAG setup (vector DB, embeddings)
- ❌ Higher maintenance (keep docs updated)

---

### Approach 4: Full Context Stack (Rules + Docs + Memories + RAG)
**What**: All mechanisms combined
**Use case**: Enterprise systems, long-lived projects
**Trade-offs**:
- ✅ Highest quality AI output
- ✅ Codifies institutional knowledge
- ❌ High upfront investment
- ❌ Requires dedicated ownership

**Architect's decision**: Start with Approach 2 (rules files), upgrade to 3 or 4 as project complexity grows.

---

## Try It Yourself

### Experiment 1: No Context vs. Context File

**Setup**: Same task, two scenarios

**Scenario A: No context**
```
Prompt: "Create a login form"
```

**Scenario B: With `.cursorrules`**
```
.cursorrules:
- Use React Hook Form + Zod validation
- Tailwind for styling
- Error messages inline (not toast)
- Submit button shows loading spinner
- On success, redirect to /dashboard

Prompt: "Create a login form"
```

**Observe**:
- **Scenario A**: Generic HTML form, basic validation, no error handling
- **Scenario B**: Matches your stack, follows conventions, production-ready

**Lesson**: Context files save you from rewriting generic code to fit your patterns.

---

### Experiment 2: Test the "Hallucination Escape Hatch"

**Bad prompt**:
```
What's our company's vacation policy?
```
*(LM will hallucinate a generic policy)*

**Good prompt**:
```
Use the provided HR policy document to answer questions.
If the answer cannot be found in the document, write "I could not find an answer."

[Paste policy document]

Question: What's our company's vacation policy?
```

**Observe**: With the escape hatch, the LM won't make up facts.

---

### Experiment 3: Context Overload

**Setup**: Create a massive `.cursorrules` file (5000+ lines)

**Task**: Ask LM to create a simple component

**Observe**:
- Does the LM use the relevant rules?
- Does it get confused by too much context?
- What's the latency impact?

**Lesson**: There's a limit to useful context. Keep rules files **focused** on high-impact conventions.

---

## Common Pitfalls

### Pitfall 1: Context Drift
**Problem**: Rules file says "use Redux" but team switched to Zustand 6 months ago
**Solution**: Treat context files like code—review and update regularly

### Pitfall 2: Vague Context
**Problem**: "Follow best practices" (what practices?)
**Solution**: Be specific. "Use React Server Components by default; client components only for interactivity"

### Pitfall 3: Buried Context
**Problem**: Critical info hidden in a 10-page doc
**Solution**: Put most important context at the top of rules files

### Pitfall 4: No Context Ownership
**Problem**: No one maintains rules files; they become outdated
**Solution**: Assign ownership (e.g., tech lead reviews quarterly)

---

## Best Practices

### 1. Layer Context by Scope

```
Global (all projects):
- Company-wide tech radar (approved vs. deprecated tech)

Project (this codebase):
- .cursorrules with this project's stack and patterns

Feature (this task):
- Inline prompt context for task-specific details
```

**Why**: Avoid repeating global context in every project.

---

### 2. Start Broad, Then Narrow

**Structure for rules files**:
```markdown
# 1. Tech Stack (broad)
- Next.js, TypeScript, Tailwind

# 2. Architecture Decisions (medium)
- Use server actions instead of API routes
- Prisma for database access

# 3. Code Conventions (narrow)
- Named exports only
- TSDoc for all functions
```

**Why**: LM reads top-to-bottom; prioritise high-impact context.

---

### 3. Link to Deeper Docs

**In `.cursorrules`**:
```markdown
# Architecture
See /docs/architecture/ for system design details
See /docs/adr/ for all architectural decision records
```

**Why**: Keep rules files concise; use RAG or explicit file reads for deep dives.

---

### 4. Version Control Context Files

Treat `.cursorrules` and `/docs` like code:
- Commit to git
- Review in PRs
- Track changes over time

**Why**: As your architecture evolves, context needs to evolve too.

---

## Advanced Techniques

### Technique 1: Conditional Context

**Problem**: Different rules for frontend vs. backend code

**Solution**: Use path-based rules (if your tool supports it)
```markdown
# Frontend (app/)
- Use React Server Components
- Tailwind for styling

# Backend (lib/)
- Use Prisma for database
- Zod for validation
```

---

### Technique 2: Examples in Context

**Instead of**:
```markdown
Use semantic commit messages
```

**Use**:
```markdown
Use semantic commit messages:
- feat: Add user login form
- fix: Resolve redirect bug in auth flow
- refactor: Extract validation logic to hook
```

**Why**: Examples are clearer than abstract rules.

---

### Technique 3: Negative Context (What NOT to Do)

```markdown
# Anti-Patterns (DO NOT USE)
- ❌ Direct Prisma calls in components (use /lib/db wrapper)
- ❌ Client-side env vars (use server actions for secrets)
- ❌ Inline styles (use Tailwind classes)
```

**Why**: Helps LM avoid common mistakes.

---

## Related Topics

- [Vibe Engineering](./vibe-engineering.md) - Context is the foundation of effective vibe engineering
- [Agent Skills Framework](./agent-skills-framework.md) - Skills as a form of procedural context
- [Prompt Engineering](../02-core-patterns/prompt-engineering.md) - Inline context strategies
- [RAG Architecture](../02-core-patterns/rag-architecture.md) - Retrieval-based context delivery

---

## Key Takeaway

**Context is your leverage point.** Good context turns generic AI into a team member who "gets" your architecture.

**Steps to implement**:
1. **Start small**: Create a `.cursorrules` file with your top 10 conventions
2. **Test impact**: Generate code before/after adding rules; measure quality improvement
3. **Expand**: Add `/docs` for complex architecture patterns
4. **Maintain**: Review and update quarterly (assign ownership)

**The ROI**: 1 hour to write a good `.cursorrules` file saves 10+ hours of fixing generic AI code.

**Remember**: LMs are not mind readers. If you want them to follow your patterns, **give them the context they need**.
