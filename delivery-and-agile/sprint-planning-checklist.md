# Agile Sprint Planning & Execution 

[cite_start]**Purpose:** Shift from output-driven (shipping story points) to outcome-driven (moving business metrics) planning[cite: 38]. 

## 📊 Pre-Planning: The Data Review
Before looking at the backlog, engineering and product leadership must review:
* **Current OKR Progress:** Are our onboarding experiments actually moving the activation funnel metrics? [cite: 24]
* **Velocity & Capacity:** Calculate actual capacity. Subtract public holidays, planned PTO, and on-call rotation overhead.
* **Tech Debt Budget:** Allocate a strict 20% of sprint capacity to technical debt, refactoring, and infrastructure improvements.

## 🎯 During Planning
* **Define the Sprint Goal:** What is the single most important objective to achieve this sprint? (If the sprint goal is met, the sprint is a success, even if lower-priority tickets roll over).
* **Ticket Readiness:** Reject tickets that do not have clearly defined Acceptance Criteria or have unresolved cross-functional dependencies.
* **Experimentation Planning:** If deploying new growth features, ensure the A/B test instrumentation and cohort analysis parameters are fully defined with the Data team before coding begins[cite: 20].

## 🚢 Release & Deployment
* All significant features must be deployed behind feature flags to enable progressive rollouts (e.g., 10% -> 50% -> 100% of user base)[cite: 23].
* Deployments should be fully automated via CI/CD pipelines[cite: 12]. If a deployment requires manual SSH or database hacking, the release is blocked until the pipeline is fixed.
