# Engineering Pull Request (PR) Standards

**Purpose:** Code reviews are our primary defense against technical debt and production outages. They must be rigorous, empathetic, and efficient.

## ⏱️ SLAs & Expectations
* **Turnaround Time:** PRs should receive their first review within 24 hours. Code waiting for review is blocked inventory.
* **PR Size Limit:** Keep PRs under 400 lines of code (excluding auto-generated lockfiles). Massive PRs lead to "LGTM" rubber-stamping. [cite_start]Break large features down using feature flags[cite: 23].

## 🔍 Reviewer Checklist
Before approving, verify the following:
- [ ] **Architecture:** Does this align with our microservices boundaries? [cite_start]Does it introduce tight coupling? [cite: 13]
- [ ] **Performance:** Are there N+1 queries? [cite_start]Will this scale gracefully in DynamoDB/Postgres under heavy load? [cite: 12]
- [ ] **Observability:** Did the author add necessary logging, metrics, or tracing spans for new critical paths?
- [ ] **Testing:** Is there adequate unit/integration test coverage? [cite_start]Does the CI pipeline pass seamlessly? [cite: 12]
- [ ] **Rollback Plan:** Is this change guarded by a feature flag? [cite_start]If this breaks production, how fast can we revert it? [cite: 23]

## 💬 Feedback Etiquette
* **Ask, don't tell:** "Could we extract this logic into a helper function?" is better than "Move this to a helper function."
* **Label your comments:** * `[Blocker]`: Must be fixed before merging (e.g., security vulnerability, logic error).
  * `[Nit]`: Minor style suggestion, not required for approval.
  * `[Question]`: Seeking to understand the author's approach.
