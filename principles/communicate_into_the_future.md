# Communicate into the future

-   Communication is a key architecture skill
-   Consider the context of who you are communicating too and how it would be best received or understood
-   Simple not simplistic
-   You must consider future teams and architects, years from now decisions will be questioned and problems revisited. Shortcut that future pain by making sure the past can be understood.

## [Architecture Decision Records (ADRs)](https://adr.github.io/)

-   A framework for recording choices that are architecturally significant
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
