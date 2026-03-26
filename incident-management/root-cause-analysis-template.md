# Blameless Root Cause Analysis (RCA) Document

**Rule #1 of RCA:** We investigate the *system*, not the *person*. Human error is a symptom of poorly designed guardrails.

## 📄 1. Incident Overview
* **Incident Name:** * **Date of Event:** YYYY-MM-DD
* **Severity:** SEV-X
* **Time to Detect (TTD):** [XX minutes]
* **Time to Resolve (TTR):** [XX minutes]
* **Customer Impact:** Quantify it. (e.g., 5,000 background jobs failed, 12% drop in successful API requests).

## ⏱️ 2. Timeline of Events
*(Use UTC or local timezone consistently. Be precise.)*
* `14:00` - PR #1042 containing schema update is merged.
* [cite_start]`14:15` - CI/CD pipeline deploys to production EKS cluster[cite: 12].
* `14:18` - PagerDuty alerts trigger for elevated 5xx errors on the checkout service.
* `14:22` - Incident declared; IC assigned.
* [cite_start]`14:35` - Issue identified; feature flag toggled off to isolate the bad code path[cite: 23].
* `14:40` - Metrics normalize; incident closed.

## 🔍 3. The 5 Whys (Root Cause)
1. **Why did the 5xx errors spike?** The checkout service threw null pointer exceptions.
2. [cite_start]**Why did it throw exceptions?** A new user segment rule required a field that did not exist on older accounts[cite: 22].
3. **Why wasn't this caught in testing?** The automated tests only run against mock data representing newly created users, not legacy schemas.
4. **Why do we lack legacy test data?** Our data seeding script hasn't been updated since the V1 to V2 migration.
5. **Why wasn't the script updated?** It is not owned by any specific pod, resulting in the tragedy of the commons.

## ✅ 4. Action Items & Remediation
*(Every action item MUST have a Jira ticket, an owner, and a strict SLA based on priority).*
| Priority | Action Item | Owner | Jira Ticket | SLA |
| :--- | :--- | :--- | :--- | :--- |
| **P0** | Add null coalescing to the segment rule evaluator | @engineer_name | ENG-401 | 24 Hours |
| **P1** | Update staging DB seeding script with legacy user cohorts | @engineer_name | ENG-405 | 1 Sprint |
| **P2** | Add Datadog monitor for specific segment rule failures | @engineer_name | ENG-410 | 2 Sprints |
