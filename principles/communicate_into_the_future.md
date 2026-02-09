# Communicate into the future

-   Communication is a key architecture skill
-   Consider the context of who you are communicating too and how it would be best received or understood
-   Simple not simplistic
-   You must consider future teams and architects, years from now decisions will be questioned and problems revisited. Shortcut that future pain by making sure the past can be understood.

## [Architecture Decision Records (ADRs)](https://adr.github.io/)

-   A framework for recording choices that are [architecturally significant](#architecturally-significant-decisions)
-   An ADR is repository/project focussed, and records deviance from the norm
-   Helps with knowledge transfer over the lifetime of a product
-   The process of filling in ADRs helps solidify thinking on a decision

### Standard ADR Structure/Template:

This tamplate is available at [/templates/000-PROPOSED-adr-template.md](/templates/000-PROPOSED-adr-template.md)

- **Title**: Sequential number, titleuse this in the file name `00X-short-title.md`.
  - Order is important, this helps future engineers organise decisions in their heads
- **Status**: Proposed, Accepted, Rejected, Superseded (by [ADR-N]), or Deprecated.
  - Up front, and obvious. 
  - Perhaps put it in the filename partiularly when depreciated or superseeded `00X-DRAFT-short-title.md`
  - Acceptance or Rejection should be performed by a second architect. 
    - The author is the first architect, particularly where the author is a senior engineer (or above)
    - Lead and Principal Engineers 
      - *Could* be the second architect if there is not a technical architect available.
      - *Should* be the second architect where the first architect is a technical architect 
    - include the job title
      - People get promoted and leave. This helps provide context in the future. 
- **Decision**: The chosen solution, articulated in the active voice.
  - Put this up front, if future readers want to know the why they can continue reading.
- **Context**: The technical, business, and social constraints, including why the decision is necessary.
  - Say why
  - State the assumptions
  - also state when the decision should be superseded if relevant
- **Consequences**: Trade-offs, including both positive (pros) and negative (cons) outcomes.
- **Alternatives**: Options considered but not chosen.
  - Include why they were rejected
- **Links**: References to supporting documentation, issues (github), or related ADRs. 

#### Best Practices:

- **Storage**: Keep in the source code repository under `/docs/adr`.
- **Length**: Short and focused, often just one page.
- **Lifecycle**: Never delete; 
  - if a decision changes, create a new ADR that supersedes the old one.
  - if a decision is rejected, keep it as it shows what was considered when, and can be used for later analysis
- **Scope**: Focus on "architecturally significant" decisions (e.g., technology choice, structural patterns, data strategy) that differ from the norms at the time. 


## Architecturally Significant Decisions

In the world of software architecture, we often say that "everything is a trade-off," but an Architecturally Significant Decision (ASD) is where those trade-offs become permanent landmarks. For a mid-level engineer, the distinction between a "design choice" and an "architectural decision" is primarily defined by: 
- impact, 
- cost of reversal
- constraints.

The Core Definition
An ASD is a choice that has a measurable impact on the software’s non-functional requirements (the "ilities"—scalability, maintainability, security) and is disproportionately expensive to change later. While choosing a variable name is a minor detail, choosing between a relational database and a document store is an ASD. If you change your mind about the database six months into production, you aren't just refactoring code; you’re migrating data, rewriting persistence layers, and potentially upending your deployment strategy.

Characteristics of an ASD
To identify an ASD, look for decisions that:

- Define System Boundaries: How services communicate (e.g., synchronous REST vs. asynchronous message queues).

- Dictate the Technical Stack: Selecting a primary language or framework that dictates the hiring pool and ecosystem for years.

- Enforce Trade-offs: Explicitly prioritizing one quality attribute over another, such as choosing Availability over Consistency in a distributed system.


As you progress through an engineering career towards lead and principle engineer, or technical architect. Your role shifts from "how to implement" to "why this way." You are no longer just solving a ticket; you are navigating residual risk. An ASD isn't necessarily about "big" things; it’s about "hard-to-change" things.

A good architect doesn't make these decisions in a vacuum. They document them using [Architecture Decision Records](#architecture-decision-records-adrs), which capture the context, the options considered, and the "why" behind the final choice. This prevents "architectural drift" where the team forgets the original constraints and starts fighting the system’s own design.