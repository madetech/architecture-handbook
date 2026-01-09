# Prompt Engineering

**Difficulty**: Introductory
**Time Investment**: 1-2 hours
**Prerequisites**: Basic familiarity with LLMs

---

## Learning Resources (Start Here)

### Primary Video
- **[Stanford Webinar - Agentic AI: A Progression of Language Model Usage](https://www.youtube.com/watch?v=kJLiOGle3Lw)** (90 min)
  - Section on "Strategies for Effective Prompts" (first 30 minutes)
  - Covers systematic prompt optimization and testing approaches

---

## Why This Matters

Prompt engineering is the foundation of getting reliable, consistent outputs from LLMs. This requires understanding:
- Why some prompts work and others fail
- How to systematically improve prompt performance
- The trade-offs between simple prompts and complex, chained workflows

**The key insight**: Small changes in how you phrase a prompt can dramatically change output quality. Without systematic testing, you're guessing.

---

## Key Concepts

### The Prompt Quality Spectrum

```
Low Quality                                    High Quality
├──────────────┼──────────────┼──────────────┤
Vague          Specific       Specific +      Specific +
                             Examples        Examples +
                                             Context +
                                             Reasoning
```

**Example Evolution**:

1. **Vague**: "Summarise the meeting notes"
2. **Specific**: "Summarise the meeting notes in a single paragraph"
3. **Specific + Examples**: "Summarise the meeting notes in a single paragraph. Then write a markdown list of the speakers and their key points."
4. **Specific + Examples + Context**: "Summarise the meeting notes in a single paragraph. Then write a markdown list of the speakers and their key points. Finally, list next steps or action items suggested by the speakers, if any."

**Result**: Prompt #4 produces consistent, actionable outputs. Prompt #1 is unpredictable.

---

## Core Strategies

### Strategy 1: Clear, Descriptive Instructions

**Principle**: Be specific about format, length, and structure.

**Bad Example**:
```
Write a function to validate emails
```

**Good Example**:
```
Write a Python function called validate_email that:
- Takes a string as input
- Returns True if valid, False otherwise
- Uses regex to check for: local part, @, domain, and TLD
- Includes docstring with example usage
```

**Why it works**: The LM knows exactly what success looks like.

---

### Strategy 2: Few-Shot Examples

**Principle**: Show the LM the style or format you want by providing examples.

**Use case**: When output format is hard to describe explicitly.

**Example - Extracting structured data**:
```
Extract the name, email, and role from the following text.

Example:
Input: "John Smith (john@example.com) is our Lead Developer"
Output: {"name": "John Smith", "email": "john@example.com", "role": "Lead Developer"}

Example:
Input: "Contact Sarah Lee at sarah.lee@company.org for DevOps questions"
Output: {"name": "Sarah Lee", "email": "sarah.lee@company.org", "role": "DevOps"}

Now process this:
Input: "Our new architect is Mike Chen (m.chen@tech.io)"
```

**Result**: The LM learns the pattern and applies it consistently.

---

### Strategy 3: Provide References & Context

**Principle**: Reduce hallucinations by giving the LM relevant context and explicit instructions to say "I don't know."

**Bad Example**:
```
What's our refund policy?
```
*(LM will hallucinate a generic policy)*

**Good Example**:
```
Use the provided company policy document to answer questions about refunds.
If the answer cannot be found in the document, write "I could not find an answer."

Policy Document:
[paste policy here]

Question: What's our refund policy for digital products?
```

**Why it works**: The LM is grounded in real data and has an "escape hatch" for missing info.

---

### Strategy 4: Enable Chain of Thought (CoT) Reasoning

**Principle**: Give the LM time to "think" by asking it to break down the problem.

**Basic Prompt**:
```
What is 15% of 240, then add 30?
```
*(Higher error rate on multi-step math)*

**CoT Prompt**:
```
What is 15% of 240, then add 30?
Think step-by-step:
1. First calculate 15% of 240
2. Then add 30 to that result
```

**Why it works**: The LM externalises intermediate steps, reducing errors in complex reasoning.

**Modern LMs**: Many can do this automatically if you add "Let's think step-by-step" or "Explain your reasoning."

---

### Strategy 5: Break Down Complex Tasks

**Principle**: Chain multiple prompts instead of asking for everything at once.

**Bad Example (single complex prompt)**:
```
Analyze this codebase and suggest improvements to performance, security, and maintainability.
```
*(Overwhelming; high error rate)*

**Good Example (chained prompts)**:
```
Prompt 1: "Analyze this codebase for performance bottlenecks. List the top 3."
Prompt 2: "Now analyze the same codebase for security vulnerabilities. List the top 3."
Prompt 3: "Finally, suggest maintainability improvements based on SOLID principles."
```

**Why it works**: Each prompt has a narrow focus, improving accuracy.

**Advanced**: Many LMs can now chain prompts internally (agentic workflows), but explicit chaining gives you more control.

---

### Strategy 6: Systematic Testing & Evaluation

**Principle**: Without testing, you can't improve. Treat prompts like code—version them and measure performance.

**How to test prompts**:

1. **Create a test set**: 10-20 example inputs with known "good" outputs
2. **Run the prompt against the test set**
3. **Measure success rate**: How often is the output acceptable?
4. **Iterate**: Change the prompt, re-test, compare results

**Example Test Set (Email Validation)**:
| Input | Expected Output |
|-------|----------------|
| `user@example.com` | `True` |
| `invalid.email` | `False` |
| `user+tag@domain.co.uk` | `True` |
| `@example.com` | `False` |

**Metrics to track**:
- **Accuracy**: % of correct outputs
- **Consistency**: Does the same input always produce the same output?
- **Latency**: How long does the prompt take?
- **Cost**: Token usage (longer prompts = higher cost)

**Pro tip**: LLMs can help evaluate outputs. Use a second LM to score the quality of the first LM's response.

---

## Common Approaches

### Approach 1: Simple, Single-Shot Prompts
**When to use**: Well-defined, straightforward tasks
**Trade-offs**:
- ✅ Fast, low latency
- ✅ Easy to debug
- ❌ High error rate on complex tasks

### Approach 2: Few-Shot Prompts
**When to use**: When output format is important
**Trade-offs**:
- ✅ Consistent formatting
- ✅ Works for niche domains
- ❌ Higher token cost (examples take up context)

### Approach 3: Chain-of-Thought
**When to use**: Multi-step reasoning, math, logic
**Trade-offs**:
- ✅ Higher accuracy on complex problems
- ✅ Easier to debug (you see the reasoning)
- ❌ Slower (more tokens generated)

### Approach 4: Chained Prompts (Sequential Tasks)
**When to use**: Complex workflows (e.g., research → summarise → format)
**Trade-offs**:
- ✅ Highest accuracy (each step is focused)
- ✅ Easier to optimise individual steps
- ❌ Higher latency (multiple LM calls)
- ❌ Higher cost

---

## Try It Yourself

### Experiment 1: Test Prompt Specificity
**Task**: Ask an LM to "write a function to reverse a string"

**Test 3 levels of specificity**:
1. Vague: "Write a function to reverse a string"
2. Specific: "Write a Python function called reverse_string that takes a string and returns it reversed"
3. Specific + Examples: Add a few-shot example showing input/output

**Observe**: Does the LM include docstrings? Type hints? Error handling? Which prompt gives you production-ready code?

---

### Experiment 2: Compare Single vs. Chained Prompts
**Task**: "Analyze this code for bugs and suggest fixes"

**Approach A (single prompt)**:
```
Analyze this code for bugs and suggest fixes:
[paste code]
```

**Approach B (chained)**:
```
Prompt 1: "Review this code and list potential bugs"
Prompt 2: "For each bug you found, suggest a specific fix"
```

**Observe**: Which approach gives more thorough analysis? Which is easier to validate?

---

### Experiment 3: Systematic Prompt Testing
**Setup**: Create a test set of 5 code snippets with known bugs

**Task**:
1. Write a prompt: "Find bugs in this code"
2. Run it on all 5 snippets
3. Measure: How many bugs did it catch?
4. Improve the prompt (add examples, CoT, etc.)
5. Re-test and compare

**Goal**: Learn to iterate on prompts based on data, not intuition.

---

## Common Pitfalls

### Pitfall 1: Assuming the LM "Knows" Your Context
**Problem**: "Fix the authentication bug" (which bug? which system?)
**Solution**: Provide full context in every prompt

### Pitfall 2: Not Testing for Edge Cases
**Problem**: Prompt works on happy path but fails on edge cases
**Solution**: Build a test set that includes edge cases (empty inputs, special characters, etc.)

### Pitfall 3: Overloading a Single Prompt
**Problem**: Asking for 10 things in one prompt
**Solution**: Break into smaller, focused prompts

### Pitfall 4: Ignoring Cost
**Problem**: Using 5 few-shot examples when 2 would work
**Solution**: Test with fewer examples; only add more if accuracy improves significantly

---

## Advanced Techniques

### Technique 1: Self-Consistency
Run the same prompt multiple times and take the majority answer.

**Example**: For math problems, run the prompt 5 times. If 4 out of 5 give the same answer, that's likely correct.

**Trade-off**: 5x cost, but higher accuracy.

### Technique 2: Prompt Chaining with Validation
```
Prompt 1: Generate SQL query
Prompt 2: Review the query for syntax errors
Prompt 3: If errors found, regenerate
```

**Why it works**: Self-correction improves accuracy.

### Technique 3: Role-Based Prompting
```
You are a senior security architect. Review this code for vulnerabilities.
```

**Why it works**: LMs adjust their "persona" and prioritise relevant knowledge.

---

## Related Topics

- [Agentic Workflows](./agentic-workflows.md) - Chaining prompts automatically with agents
- [Context Management](../03-development-workflows/context-management.md) - Providing the right context to LMs
- [RAG Architecture](./rag-architecture.md) - Augmenting prompts with retrieved data

---

## Key Takeaway

**Prompts are code.** Treat them with the same rigor:
- Version control
- Systematic testing
- Performance metrics
- Code review (for critical prompts)

**When evaluating LM-powered tools, ask**:
1. Are prompts tested systematically?
2. Is there a feedback loop to improve prompts over time?
3. Are edge cases handled?

Start simple, measure, iterate. Don't over-engineer prompts until you have data showing it's needed.
