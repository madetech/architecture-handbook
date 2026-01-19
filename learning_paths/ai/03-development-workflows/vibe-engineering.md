# Vibe Engineering

**Difficulty**: Intermediate
**Time Investment**: 1-2 hours
**Prerequisites**: Experience with modern development workflows

---

## Learning Resources (Start Here)

### Primary Video
- **[From Vibe Coding To Vibe Engineering – Kitze, Sizzy](https://www.youtube.com/watch?v=JV-wY5pxXLo)** (60 min)
  - Practical perspective on AI-assisted development
  - Covers tools (Cursor), workflows (voice-to-code), and cultural shifts
  - Honest take on what works and what's hype

---

## Why This Matters

The workflow for engineers is being extended:
- **Traditional**: Write every line of code, review every detail
- **Vibe Engineering**: Define outcomes, let AI handle implementation, audit high-level structure

 Understanding this new way of working provides insight into:
- How senior engineers are 10x-ing their outputs with this shift
- What new skills teams need (context clarity, architectural judgment, comprehension) vs. what becomes less critical (line-by-line implementation and review)
- The trade-offs between speed and control

---

## Key Concepts

### Vibe Coding vs. Vibe Engineering

**Vibe Coding** (coined by Andrej Karpathy):
- Developer focuses on the "vibe" (desired outcome)
- LLM handles implementation
- Developer often doesn't read every line of generated code

**Vibe Engineering** (the speaker's distinction):
- **Architect-level approach**: Maintain high-level structural standards
- **Remain suspicious**: Don't blindly trust AI output
- **Leverage for complex systems**: Build production-grade software faster

**The difference**: Vibe Coding is casual experimentation. Vibe Engineering is a professional discipline.

---

## The Paradigm Shift

With vibe engineering, the **development bottleneck*** fundamentally changes:

**Old bottleneck**: Writing implementation code (80% of time)
**New bottleneck**: Providing clear context and maintaining architectural judgment (60% of time)

This shift has profound implications for team structure, skill requirements, and how we measure productivity.

* if development isn't the bottleneck vibe engineering wont increase velocity.
---

## The Comprehension Gap

### The Hidden Risk

As AI code generation velocity increases, a critical gap emerges:

```
┌─────────────────────────────────────┐
│  AI Code Generation Velocity        │  ← Exponentially increasing
│  (300-1000+ lines/hour)             │
├─────────────────────────────────────┤
│                                     │
│    ← COMPREHENSION GAP →            │  ← Growing over time
│                                     │
├─────────────────────────────────────┤
│  Human Comprehension Capacity       │  ← Relatively constant
│  (~50-200 lines/hour)                │
└─────────────────────────────────────┘
```

**The problem**: Engineers can generate 300-1000+ lines of AI code in an hour, but can only deeply comprehend 50-200 lines in that same time. Velocity exceeds understanding capacity.

### The "Easy Button" Trap

**Definition**: Accepting AI-generated code without critical analysis because it "looks right" and passes tests.

**Symptoms**:
- PRs approved in <5 minutes despite complex logic
- Engineers can't explain edge cases ("The AI handled it")
- Bugs discovered months later (no one understood the code)
- Technical debt accumulates invisibly

**Real-world example**:
```
Engineer: "Add rate limiting to the API"
AI: [generates 200 lines with redis, sliding window, token bucket]
Engineer: "Looks good!" → Merge

3 months later: Memory leak discovered
Root cause: No one understood the token bucket implementation
```

### Knowledge Atrophy

**The danger**: As AI handles the "how," engineers lose the "why."

**Impact**:
- Can't debug when AI-generated code fails
- Can't pivot when requirements change
- Can't mentor junior developers (no one understands the code)
- Organisational knowledge becomes locked in AI-generated code

**Ensure vibe engineering doesn't become "vibe guessing."**

---

## Critical Success Factors

### 1. Context is King

**The Problem**: LMs are "not mind readers." Without context, they generate generic slop.

**The Solution**: Provide rich context through:
- **Rules files** (e.g., `.cursorrules`): Project conventions, architecture decisions
- **Documentation**: ADRs, design docs, API schemas
- **Examples**: Quality implementations within existing code

**Example `.cursorrules`**:
```
# Project Conventions
- Always use TypeScript (no JS)
- Follow feature-based folder structure: /features/[feature-name]
- Use Tailwind for styling, no CSS modules
- API calls go through /lib/api wrapper
- All forms use React Hook Form + Zod validation

# Architecture Decisions
- Authentication: NextAuth.js with JWT
- State management: Zustand (no Redux)
- Database: Prisma + PostgreSQL
```

**Impact**: With good context, AI is more likely to generate code that **fits your project** instead of generic examples.

---

### 2. The "Good Enough" Skill

**Definition**: The ability to judge when code is "clean enough" for the agent to continue, rather than striving for perfection.
**The trade-off**:
- ✅ Ship faster (iterate quickly)
- ❌ Accumulate technical debt if you're not careful

**When "good enough" fails**: When you let the AI continue building on fundamentally flawed architecture.

**Architect's role**: Define **minimum acceptable quality** standards.

---

### 3. Abstracting Early (The LLM Advantage)

**Traditional wisdom**: "Don't abstract until you have 3 examples" (avoid premature abstraction)

**With LLMs**: You can delay abstraction indefinitely because LLMs don't care about repetitive code.

**Example**:
```typescript
// Traditionally, you'd abstract this after 3 similar components
<UserCard name="Alice" email="alice@example.com" />
<UserCard name="Bob" email="bob@example.com" />
<UserCard name="Charlie" email="charlie@example.com" />

// With AI, you can have 20 similar components
// Then ask AI: "Abstract these 20 components into a reusable pattern"
```

**Benefit**: You see the actual usage pattern before creating abstraction (better API design).

**Caveat**: You still need to abstract eventually (for maintainability).

---

## Tools and Workflows

### Cursor: Composer Mode

**What it does**: AI-powered code editor with "Composer" feature for multi-file edits

**Why it matters**: Developer stays in the "driver's seat"
- Start, stop, redirect AI mid-task
- Iterative feedback loop
- Real-time correction

**Comparison to other tools**:
| Tool | Control Level | Use Case |
|------|---------------|----------|
| **GitHub Copilot** | Autocomplete | Line-by-line suggestions |
| **Cursor Composer** | Architect-driven | Multi-file refactors, features |
| **Devin, GPT Engineer** | Fully autonomous | Entire projects (less control) |

**Architect's takeaway**: Cursor-style tools give you control while keeping velocity high.

---

### Voice-to-Code (Your Milage May Vary)

**What it does**: Speak requirements out loud; AI translates to code

**Why it's powerful**:
- **Brain dump** complex context quickly (faster than typing)
- **Captures intent better** than written specs

**Example Workflow**:
```
[Voice]: "Hey, I'm seeing a bug where the modal doesn't close when you click outside of it.
I think it's because we're not handling the onClickOutside event in the Dialog component.
Can you fix that and also make sure it still closes when you hit Escape?"

[AI]: Generates fix across 2 files (Dialog.tsx, useOnClickOutside hook)
```

**When to use**:
- Debugging (explain the issue)
- Feature requests (describe the flow)
- Complex UI behavior (visual interactions can be a pain to write)

---

## The "PITA Developer" Problem

**PITA**: "Pain in the Ass" (speaker's humorous term)

**Profile**:
- Nitpicks PRs (tabs vs. spaces, minor formatting)
- Resists new tools ("AI will never replace me")
- Prioritises process over outcomes

**The irony**: If a PITA developer adopts Vibe Engineering, they become **10x more productive**.

**Why**: Their attention to detail becomes **auditing AI output** instead of writing boilerplate.

**Takeaway**: Resistance to AI tools might lead to missed opportunities to amplify our strengths."

---

## The Future Implications

### 1. Thinning from the Bottom (Speakers Prediction)

**Observation**: AI will replace junior/intern tasks first.

**Why**: Juniors can't yet distinguish "good enough" code from "wrong" code.

**Implication**: Juniors need **more mentorship**, not less, when using AI tools.

---

### 2. The "Legacy AI Code" Market (Speakers Prediction)

**Prediction**: A new market for "Vibe Code Fixers"—senior engineers hired to finish the "last 20%" of AI-generated projects.

**Analogy**: Like "Cobol Cowboys" maintaining old systems, future engineers will maintain AI-generated codebases.

**Our role**: As ever; design systems today that won't become "legacy spaghetti" tomorrow.

---

### 3. Stay Chronically Online (Speakers Advice)

**Problem**: Model capabilities change often when you look across all vendors (Claude → Gemini → GPT updates).

**Solution**: Follow developer communities (Twitter/X, Discord, Reddit) to know which model is "currently smartest."

**Example**: "GPT-4 was best for coding last month, but Gemini 2.0 is better this month."

**Implication**: Tool selection is now a **continuous evaluation process**, not a one-time decision.

---

## Try It Yourself (AI Generated)

### Experiment 1: Voice-to-Code Debugging
**Setup**: Use Cursor or Claude Code with voice input enabled

**Task**: Explain a UI bug out loud instead of writing a ticket

**Observe**:
- How much faster is voice vs. typing?
- Does the AI capture your intent?
- Do you explain differently when speaking vs. writing?

---

### Experiment 2: The "Good Enough" Test
**Setup**: Ask AI to generate a React component

**Workflow**:
1. Generate initial version
2. Identify 3 improvements
3. Ask yourself: "Is it good enough to build on top of, or should I fix these first?"
4. Try both approaches:
   - **A**: Fix all 3, then continue
   - **B**: Build 2 more components on top, then refactor all 3 together

**Observe**: Which approach ships faster? Which produces better architecture?

---

### Experiment 3: Context Files Impact
**Setup**: Same task, two scenarios

**Scenario A**: No `.cursorrules` file
```
Prompt: "Build a login form"
```

**Scenario B**: With `.cursorrules`
```
Rules:
- Use React Hook Form + Zod
- Tailwind styling
- Error messages below inputs (not toast)
- Submit button disabled while validating
```

**Observe**: How different are the outputs? How much manual fixing is needed?

---

## Common Pitfalls (AI Generated)

### Pitfall 1: No Primitives / Component Libraries
**Problem**: AI generates inconsistent UI components
**Solution**: Start with a design system (Shadcn, Radix) so AI has "good primitives" to work with

### Pitfall 2: Blindly Trusting AI
**Problem**: Merge AI code without review → bugs in production
**Solution**: Treat AI code like junior developer code (review structure, test edge cases)

### Pitfall 3: Giving AI Tools to Juniors Without Guardrails
**Problem**: Juniors can't tell "good enough" from "wrong"
**Solution**: Pair programming (junior + AI + senior oversight)

### Pitfall 4: Over-Relying on Latest Model
**Problem**: Constant model switching → inconsistent coding style
**Solution**: Pick a model, use it for a project, switch only when clearly beneficial

---

## Related Topics

- [Spec-Driven Development](./spec-driven-development.md) - Maintaining understanding at AI generation speed
- [Context Management](./context-management.md) - How to give LMs the right context
- [Agent Skills Framework](./agent-skills-framework.md) - Anthropic's approach to structured AI workflows
- [Agentic Workflows](../02-core-patterns/agentic-workflows.md) - The patterns powering vibe engineering tools
- [Architectural Drift Prevention](../04-governance-automation/architectural-drift-prevention.md) - Preventing the comprehension gap and "easy button" trap

---

## Key Takeaway

**Vibe Engineering is real.** Senior engineers are already 10x-ing productivity with AI tools.

**What you can do to get better outcomes**:
1. **Enable the team**: Set up context files, design systems, conventions
2. **Define "good enough"**: What's the minimum acceptable quality?
3. **Prevent AI slop**: Code review standards, architectural guardrails
4. **Stay current**: Model capabilities change monthly—keep evaluating

**The shift**: From "writing **all the code**" to "writing the critical paths, providing context, and auditing code."

**Start**: Pick one tool (Cursor or Claude Code), set up a `.cursorrules` file, try voice-to-code for a few days. Measure: How much faster did you ship?
