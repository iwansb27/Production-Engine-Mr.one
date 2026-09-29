# MR.ONE Production Engine — Master Specification

Status: FOUNDATION / CONTROLLED BUILD
Repository: iwansb27/Production-Engine-Mr.one
Source of truth: GitHub
Builder/runtime: Freebuff Cloud
Principle: Free-first, no unnecessary external services

## 1. Mission
Build one modular production engine that turns an approved opportunity/idea into research, product/content assets, creative outputs, a controlled queue, distribution jobs, monitoring, and analytics.

## 2. Core pipeline
Discovery → Research → Product → Content → Creative → Queue → Scheduler → Distribution → Monitoring → Analytics

## 3. Architecture
- Workspace: central control surface for jobs, status, approvals, history, and configuration.
- Job: immutable identity for each production request.
- Workflow State: Draft → Researching → Ready → Producing → Review → Approved → Queued → Published → Monitored → Archived.
- Approval Gateway: no external publishing action without explicit approval unless a later policy explicitly enables it.
- Registry: providers, channels, templates, prompts, storage targets, and capabilities.
- Audit/History: every state transition and production action recorded.
- Provider Adapter layer: external AI/API providers are optional adapters, not hard dependencies.
- Storage abstraction: keep storage replaceable; do not introduce Supabase by default.

## 4. Operating principles
1. Proof Before Build.
2. Free/zero-rupiah first.
3. Native capability before external service.
4. One project, modular architecture; no duplicate apps.
5. Human approval at consequential publishing steps.
6. Never silently modify locked legacy MR.ONE projects.
7. Every major stage must be testable independently.
8. Keep credentials/secrets out of Git.
9. Prefer mobile-friendly, simple UI over technical complexity.
10. Build only after the current stage passes its test.

## 5. Initial modules
### A. Control Center
Job creation, workflow state, approvals, activity log, health indicators.

### B. Discovery
Capture opportunities from approved sources. Store candidate, source, URL, evidence, status, and notes. Discovery does not publish.

### C. Research
Turn a candidate into a structured research brief with source references, claims, constraints, audience, and production recommendation.

### D. Product
Generate product concepts/assets from approved research. Keep reusable product records and versioning.

### E. Content
Generate platform-neutral content masters and channel-specific variants.

### F. Creative
Manage storyboard, image/video prompts, assets, render status, and review.

### G. Queue & Scheduler
Queue approved jobs with target channel, planned time, status, retry count, and audit trail.

### H. Distribution
Provider adapters for supported destinations. Start as manual/assisted; automate only after connector capability is verified.

### I. Monitoring & Analytics
Track publication result, errors, engagement metrics when available, and job-level history.

## 6. First implementation stage
Build only the Foundation:
- application shell
- navigation
- Control Center
- Job model
- Workflow State
- Approval Gateway
- Registry
- Audit/History
- mock data
- bridge-test status indicator

Do NOT implement real marketplace scraping, social publishing, paid APIs, or autonomous external automation in Stage 1.

## 7. Acceptance test for Stage 1
A user can:
1. Create a test job.
2. See its Job ID.
3. Move it through controlled workflow states.
4. See approval required before a consequential action.
5. See the complete audit trail.
6. Refresh the app without losing the mock job during the active session.
7. Open the app through Freebuff Preview.

## 8. Out of scope until separately approved
- Supabase
- paid API dependencies
- automatic social publishing
- marketplace account automation
- scraping that violates source terms
- autonomous control of third-party builder platforms

## 9. Build sequence
Stage 1 Foundation → Stage 2 Discovery/Research → Stage 3 Product/Content → Stage 4 Creative → Stage 5 Queue/Scheduler → Stage 6 Distribution adapters → Stage 7 Monitoring/Analytics.

Each stage requires: Build → Preview → Test → Correction → Checkpoint before the next stage.
