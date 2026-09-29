# MR.ONE PRODUCTION ENGINE — MASTER HANDBOOK

Repository: iwansb27/Production-Engine-Mr.one
Source of Truth: GitHub main
Builder / Runtime: Freebuff Cloud
Operating Mode: Continuous controlled build
Status: MASTER HANDBOOK / LOCKED BUILD PLAN
Last updated: 2026-09-29

## 0. PURPOSE
This handbook is the permanent execution reference for the MR.ONE Production Engine. It prevents the build from losing direction, repeating decisions, stopping unnecessarily, or drifting into unrelated projects.

Core rule: Build continuously through the defined stages. Do not ask for permission at every small implementation step.

Within an authorized build run, complete the defined work for the current stage, test it, correct it, document the result, and continue to the next stage unless a destructive or irreversible action, credential/account connection, paid service, external publishing authorization, material architecture change, or hard technical blocker is encountered.

Normal coding, file creation, refactoring, testing, UI work, documentation, and local/mock implementation do not require a new permission request when already covered by this handbook.

## 1. NORTH STAR
MR.ONE Production Engine turns an approved opportunity into a controlled production and distribution workflow.

Master pipeline:
Discovery → Research → Product → Content → Creative → Queue → Scheduler → Distribution → Monitoring → Analytics

Simple in front, structured behind.

## 2. NON-NEGOTIABLE PRINCIPLES
1. Free-first.
2. Proof Before Build.
3. One project.
4. GitHub is the source of truth.
5. Freebuff is the builder/runtime.
6. Native capability before external service.
7. No secrets in Git.
8. Approval Gateway for consequential external actions.
9. Audit important state changes.
10. No silent changes to legacy MR.ONE projects.

## 3. SYSTEM ARCHITECTURE
Workspace / Control Center → Job Engine → Workflow State → Approval Gateway → Registry → Production Modules → Queue/Scheduler → Distribution → Monitoring/Analytics.

External services are provider adapters, never hard dependencies. Storage remains replaceable.

## 4. MASTER DATA MODEL
Job: job_id, title, type, source, current_state, priority, timestamps, owner, approval_state, retry_count, metadata.
Candidate: candidate_id, discovery_source, source_url, title, evidence, status, notes.
Research Brief: research_id, candidate_id, objective, audience, evidence, claims, constraints, recommendation, sources, status.
Product: product_id, research_id, name, description, version, assets, status.
Content Master: content_id, product/research reference, master_text, variants, target_channels, version, status.
Creative Asset: asset_id, job_id, type, prompt, source, location, version, status.
Queue Item: queue_id, job_id, target, scheduled_at, status, retry_count.
Publication: publication_id, queue_id, destination, external_id, published_at, result, error.
Audit Event: event_id, job_id, event_type, actor, timestamp, before_state, after_state, metadata.

## 5. MASTER WORKFLOW STATES
DRAFT → RESEARCHING → READY → PRODUCING → REVIEW → APPROVED → QUEUED → PUBLISHED → MONITORED → ARCHIVED.
Failure/support states: BLOCKED, FAILED, RETRYING.
Every state transition must be intentional and auditable.

## 6. COMPLETE BUILD ROADMAP

### STAGE 0 — BRIDGE / FOUNDATION PROOF
Objective: prove GitHub → Freebuff Cloud → Sandbox → Dependency Install → Dev Server → Preview.
Status: PASSED.
Evidence: minimal test application successfully displayed the MR.ONE Production Engine bridge-test preview.
Do not rebuild this stage.

### STAGE 1 — APPLICATION FOUNDATION
Objective: create the actual application shell without external automation.
Build: React/Vite shell, responsive navigation, Dashboard, Job creation/detail, Workflow State, Approval Gateway, Registry, Audit/History, system health, mock data.
Acceptance: create a test Job ID, view and transition valid states, see approval requirements, see audit events, run in Freebuff Preview.
Completion: Build → Preview → Test → Correction → Retest passes.

### STAGE 2 — DISCOVERY CENTER
Build opportunity discovery, candidate cards, source URL, evidence, status, save/archive, search/filter, and handoff to Research.
Initial source categories: marketplaces, public content sources, approved news sources, user-provided URLs.
Do not implement prohibited scraping, downloading, or automatic affiliate publishing.
Acceptance: candidate can be entered/discovered, saved, inspected, and handed to Research.

### STAGE 3 — RESEARCH ENGINE
Build research jobs, source collection, evidence, audience, opportunity extraction, constraints, claim/evidence mapping, status, versioning, and Research → Product/Content handoff.
Acceptance: candidate produces a complete reviewable research brief.

### STAGE 4 — PRODUCT ENGINE
Build product workspace, concepts, specifications, versioning, assets, status, library, and Research → Product traceability.
Acceptance: approved research produces a traceable product record.

### STAGE 5 — CONTENT ENGINE
Build Content Master, hooks, captions, scripts, CTA, topic metadata, platform variants, versioning, review status, and Product → Content traceability.
Acceptance: one approved brief produces a reusable master and controlled channel variants.

### STAGE 6 — CREATIVE ENGINE
Build storyboard, scene structure, image/video prompts, asset registry, render status, preview, revisions, and creative review.
Use mock/local production first. External AI providers are adapters, not hard dependencies.
Acceptance: content job produces a complete creative brief/storyboard and tracks assets/revisions.

### STAGE 7 — QUEUE & SCHEDULER
Build queue, priority, target channel, scheduled time, status, retry count, validation, approval state, and manual release control.
Acceptance: only approved jobs enter the release queue.

### STAGE 8 — DISTRIBUTION ADAPTERS
Build provider-neutral adapters for authenticate, validate, prepare, publish, retrieve result, and error handling.
Potential destinations: Instagram, Facebook, TikTok, YouTube, and marketplace destinations.
Audit each provider independently for read/write capability, authentication, limits, free tier, terms, supported media, and failure handling.
Do not claim an integration works until tested.
Acceptance: one approved test publication executes through a verified provider.

### STAGE 9 — MONITORING
Track job execution, publication result, provider response, errors, retries, publication timestamp, and external ID.
Acceptance: published test job is traceable from Job ID through provider result.

### STAGE 10 — ANALYTICS
Build production and distribution metrics, failure/retry rates, cycle time, channel metrics where available, job performance, and historical trends.
Acceptance: analytics display real or mock data with clear source attribution.

### STAGE 11 — OPTIMIZATION / AUTONOMOUS ASSISTANCE
Only after the complete controlled pipeline works.
Possible capabilities: recommendations, queue optimization, content reuse, opportunity scoring, provider fallback, error recovery, workload routing.
Automation must be bounded, auditable, and reversible. Do not autonomously control third-party platforms in violation of their terms.

## 7. STAGE EXECUTION PROTOCOL
1. BUILD — implement the complete scope of the current stage.
2. PREVIEW — run the current application in Freebuff.
3. TEST — execute acceptance tests.
4. CORRECT — fix discovered failures.
5. RETEST — run acceptance tests again.
6. CHECKPOINT — record scope, result, corrections, limitations, next stage, and commit.
7. CONTINUE — if passed and no approval/blocker condition exists, continue to the next stage without asking for another permission.

## 8. WHEN TO STOP AND ASK
Stop for human review only when the next action requires money, credentials, account authorization, external publishing, destructive deletion, irreversible migration, legal/terms-sensitive automation, or a material architecture change not covered by this handbook.

Everything else covered by the current stage should continue.

## 9. CHECKPOINT FORMAT
Stage:
Status: PASSED / BLOCKED / FAILED
Commit:
Built:
Tested:
Corrections:
Known limitations:
Next stage:
Human approval required: YES / NO

## 10. EXTERNAL SERVICE POLICY
Default: no external dependency until proven necessary.
Supabase: avoid by default.
Cloudinary: only if native storage is insufficient.
Make: only if native orchestration is insufficient.
Buffer: only if direct distribution is insufficient.
Paid AI APIs: only after free/native options are exhausted and revenue justification exists.

## 11. SECURITY
Never commit API keys, OAuth tokens, passwords, cookies, private keys, session credentials, or personal access tokens.
Use environment variables or platform-managed secrets.

## 12. PROJECT ISOLATION
This repository is isolated. Never import or modify Home MR.ONE, AppDeploy projects, old Discovery Center, Replit fallback, unrelated GitHub projects, BASB ERP, or other personal projects unless explicitly requested.

## 13. CURRENT CHECKPOINT
Bridge: PASSED.
Master Specification: INSTALLED.
Master Handbook: INSTALLED.
Current build stage: STAGE 2 — DISCOVERY CENTER.
Current status: BUILT — GitHub implementation complete; Freebuff runtime verification pending.
Previous stage: STAGE 1 — PASSED based on the Freebuff runtime report supplied by the user.
Current objective: opportunity discovery, candidate cards, source URL, evidence, status, save/archive, search/filter, and handoff to Research.
Checkpoint: STAGE_2_CHECKPOINT.md

## 14. FINAL OPERATING COMMAND
When the user says LANJUTKAN, KERJAKAN, or Lanjut, interpret it as authorization to continue the already-defined build sequence.
Do not repeatedly ask for permission for ordinary implementation steps covered by this handbook.
Continue until the current authorized stage is complete and tested, a genuine blocker occurs, or a human-approval condition is reached. Then record the checkpoint in GitHub.

## 15. MASTER RULE
Do not let the project drift.
Always return to this handbook before a material implementation decision.
Handbook = plan. GitHub = source of truth. Freebuff = build/runtime. Application = controlled continuous build.
Execution pattern: Build → Test → Correct → Checkpoint → Continue.