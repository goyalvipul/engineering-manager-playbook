# Engineering Interview Evaluation Rubric

**Purpose:** Standardize the assessment of candidates against objective technical and behavioral criteria to ensure high-quality, unbiased hiring.

## 💻 1. Technical Execution & Coding
* [cite_start]**Strong Hire:** Produces production-ready, modular code (e.g., TypeScript/Python)[cite: 12]. Immediately writes unit tests. Proactively identifies edge cases, time/space complexity, and handles errors gracefully.
* **Hire:** Reaches an optimal solution but requires minor prompting. Code is clean but lacks comprehensive error handling.
* **No Hire:** Cannot optimize brute-force solutions. Messy code structure; ignores edge cases.

## 🏗️ 2. System Design & Cloud Architecture
* **Strong Hire:** Drives the design. [cite_start]Clearly defines API boundaries, database choices (e.g., SQL vs. NoSQL/DynamoDB), and caching layers (Redis)[cite: 12]. Discusses trade-offs in distributed systems (CAP theorem, idempotency).
* [cite_start]**Hire:** Can design a functional, scalable system using cloud primitives (AWS/Azure) but struggles with deep dive questions on data replication or resolving bottleneck scenarios[cite: 13].
* **No Hire:** Designs single points of failure. Cannot justify technology choices beyond "it is what I used before."

## 🚀 3. CI/CD & Operational Excellence
* [cite_start]**Strong Hire:** Understands containerization (Docker/Kubernetes) deeply[cite: 13]. [cite_start]Can explain how to structure a robust CI/CD pipeline (GitHub Actions/GitLab CI) with automated software testing[cite: 12].
* **Hire:** Familiar with Docker and deployment concepts but relies heavily on DevOps teams in practice.

## 🤝 4. Behavioral & Culture Add
* [cite_start]**Strong Hire:** Exhibits high ownership and autonomy[cite: 26]. Gives credit to teams ("we"). Articulates clear learnings from past failures.
* **Hire:** Collaborative and communicative. Good cultural fit.
* **No Hire:** Defensive when challenged. Lacks empathy for cross-functional partners (Product/Design).
