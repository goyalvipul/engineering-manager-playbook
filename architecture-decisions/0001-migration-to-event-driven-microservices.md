# ADR 0001: Migration to Event-Driven Microservices on AWS

* **Status:** Accepted
* **Date:** 2022-08-15
* **Authors:** Vipul Goyal (Sr. Engineering Manager), [Tech Lead Name]

## 1. Context & Problem Statement
[cite_start]Our platform's growth requires processing 3-5 parallel A/B tests per sprint[cite: 33]. The current synchronous architecture tightly couples experiment evaluation with the main monolith, causing high latency during peak traffic and limiting our ability to deploy experiment updates independently. 

## 2. Decision Drivers
* Reduce evaluation latency to < 50ms at P99.
* Enable decoupled deployments for the experimentation team.
* Reduce overall AWS infrastructure costs.

## 3. Considered Options
* **Option A:** Optimize monolithic codebase and scale horizontally (Rejected: Does not solve deployment coupling).
* **Option B:** Migrate to synchronous RESTful microservices (Rejected: Cascading failures and network latency overhead).
* [cite_start]**Option C:** Migrate to an event-driven architecture utilizing AWS EventBridge and SQS/SNS[cite: 12].

## 4. The Decision
We will proceed with **Option C**. [cite_start]We will extract the experiment evaluation and feature flag engines into independent microservices deployed via Docker on AWS EKS[cite: 12]. Communication will happen asynchronously. State changes (e.g., user cohort updates) will emit events to EventBridge, which downstream services will consume.

## 5. Consequences & Mitigation
* **Positive:**
  * [cite_start]Enabled low-latency experiment evaluation[cite: 27].
  * [cite_start]Reduced infrastructure costs by 20% by right-sizing specific node groups in EKS[cite: 27].
* **Negative:**
  * Introduces eventual consistency into the user activation funnel.
  * Harder to debug cross-service request lifecycles.
* **Mitigation:**
  * Implement strict schema registries for all event payloads.
  * Enforce distributed tracing headers across all services before pushing to production.
