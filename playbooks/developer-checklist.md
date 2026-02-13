# 🏗️ Cheat Sheet - Architecture for developers
 
Scan this list during refinement and before starting a story. Also check this on a pull request.
If a box is checked and don't have a clear path forward, it’s time to get an architects input.

## 🚩 The "Stop & Ask" Triggers

Get an Architect or Lead Engineer involved if this story:

- Introduces a new tool, library, or database we haven't used before.
- Changes the "Source of Truth" for data.
- Bypasses existing Security or Auth patterns.
- Creates a circular dependency between services.


## Gut check

### 💷 Value

- [ ] Efficiency: Are we maximising the work not done?
- [ ] Impact: Are we delivering something that makes a difference.
- [ ] Testable: are the acceptance criteria for the story clear and unambiguous.
- [ ] Achievable: Can the story be delivered in a reasonable timeframe with the resource available.
- [ ] Clear target: Is the definition of done for the story understood.

### 🔐 Data & Security

- [ ] PII & Privacy: Does this touch user data (email, names, IDs)? Are we logging it safely (or not at all)?
- [ ] Auth Check: Are we enforcing the right permissions? (Don't just check if they're logged in; check if they should see this).
- [ ] DB Migrations: Does this change the schema? Is it a "breaking" change that requires a specific deployment order?
- [ ] Sanitization: Are we treating all user input as "guilty until proven innocent" to prevent injections?
- [ ] Secrets: Are we exposing any secrets in the codebase or logs?

### ⚡ Performance & Scale

- [ ] The "N+1" Trap: Are we making multiple DB/API calls when one would do?
- [ ] Latency: Are we adding a synchronous call to a slow external service?
- [ ] Payload Size: Are we fetching the entire universe when we only need a few fields?
- [ ] Throttling: What happens if this feature gets hit 1,000 times a second?
- [ ] State: Is all state managed in the data layer?
- [ ] Flexibility: Have we designed to allow for future changes?

### 🛠️ Reliability & Observability

- [ ] Graceful Failure: If the downstream service is down, is the user experience satisfactory?
- [ ] Logs that Matter: Do our logs contain enough context (Correlation IDs, etc.) to trace an error across services?
- [ ] Alerting: Do we need to know immediately if this specific feature starts failing?
- [ ] Circuit Breakers: Should we "trip the breaker" if a dependency is struggling?

### 🔗 Integrations & Patterns

- [ ] Contract Integrity: Are we changing an API response that other teams or frontend components rely on?
- [ ] Consistency: Does this follow our existing patterns, or are we "freestyling" a new way of doing things?
- [ ] Vendor Lock-in: Are we leaning on a specific cloud tool that will be impossible to swap out later?

### 🛣️ Infrastructure

- [ ] Deployability: Are we adding anything that will significantly increase the time taken to deploy the service?
- [ ] Pipelines: Is the deployment still fully automated?

