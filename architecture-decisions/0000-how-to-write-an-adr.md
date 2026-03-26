# How to Write an Architecture Decision Record (ADR)

**Purpose:** ADRs provide immutable historical context for critical system design choices. They prevent circular arguments, document trade-offs, and serve as onboarding material.

## 📝 ADR Template Structure

* **Title:** [Short, descriptive noun phrase]
* **Status:** [Proposed | Accepted | Deprecated | Superseded by ADR-XXXX]
* **Date:** YYYY-MM-DD
* **Authors:** [Lead Engineer, Reviewers]

### 1. Context & Problem Statement
* Describe the specific technical or business constraint. Include current metrics if applicable (e.g., "Our current monolithic synchronous API drops 5% of requests during peak load due to thread starvation").

### 2. Decision Drivers
* What are the strict constraints? (e.g., Budget, AWS vendor lock-in, compliance/security, latency SLAs).

### 3. Considered Options
* Detail at least 2-3 alternatives. (e.g., Option A: Scale vertically. Option B: Migrate to SQS/EventBridge. Option C: Implement Redis caching).
* Include brief pros/cons for the rejected options.

### 4. The Decision
* State the chosen solution clearly. 
* Explain *why* it was chosen over the alternatives, referencing the decision drivers.

### 5. Consequences & Mitigation
* **Positive:** (e.g., Increased throughput, decoupled deployments).
* **Negative/Risks:** (e.g., Increased operational complexity, eventual consistency challenges).
* **Mitigation Strategy:** How will we monitor and handle the new risks? (e.g., "We will implement distributed tracing via Datadog to monitor asynchronous workflows").
