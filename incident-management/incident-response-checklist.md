# Incident Response & Triage Protocol

**Purpose:** Provide a deterministic framework for handling Sev-1 and Sev-2 incidents to minimize Mean Time to Recovery (MTTR) and customer impact.

## 🚨 Severity Definitions
* **SEV-1 (Critical):** Core system offline. High data loss risk. Widespread customer impact. (e.g., Complete AWS region failure, critical DB dropped).
* **SEV-2 (Major):** Core functionality degraded but system is up. Significant customer friction. (e.g., Checkout failing for 20% of users, onboarding drop-offs spiking) [cite_start][cite: 24].

## 👩‍💻 Incident Roles
1. **Incident Commander (IC):** Drives the resolution. Does NOT code. Manages the room, delegates tasks, and maintains the timeline.
2. **Subject Matter Expert (SME):** The engineer(s) actively debugging the code/infrastructure.
3. **Communications Lead:** Translates technical status into business updates for Product and Customer Success.

## 📋 The Checklist
### Phase 1: Identification & Containment (Minutes 0-15)
- [ ] Open a dedicated Slack channel (`#inc-YYYY-MM-DD-issue-name`) and start a Zoom bridge.
- [ ] Establish roles (IC clearly states: "I am taking IC").
- [ ] Identify blast radius via monitoring tools (Datadog/CloudWatch).
- [ ] **Immediate Action:** Can we mitigate quickly? (Rollback the latest EKS deployment, toggle off the feature flag, restore DB from snapshot) [cite_start][cite: 12, 23].

### Phase 2: Communication (Minutes 15-30)
- [ ] Update internal stakeholders via `#general-engineering` with current impact and ETA for next update.
- [ ] Update external Status Page (if SEV-1).

### Phase 3: Resolution & Wrap-up
- [ ] Confirm mitigation via metric recovery (e.g., error rates return to baseline, queues drain).
- [ ] IC officially declares the incident resolved.
- [ ] Schedule the Blameless RCA meeting within 48 business hours.
