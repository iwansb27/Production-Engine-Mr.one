# FINAL ACCEPTANCE TEST PLAN

## A. Build integrity
- npm install succeeds from package.json and resolves the complete dependency tree cleanly.\n- If Freebuff regenerates package-lock during validation, the generated lockfile is retained as the runtime-generated dependency lock.
- npm run build succeeds.
- dev server starts on configured Freebuff preview port.
- no console-breaking import/runtime error.

## B. End-to-end workflow
- Create Job.
- Confirm valid state path: DRAFT → RESEARCHING → READY → PRODUCING → REVIEW → APPROVED → QUEUED → PUBLISHED → MONITORED → ARCHIVED.
- Discovery candidate can be saved, searched, filtered, edited and handed to Research.
- Research, Product, Content and Creative records are editable and traceable by IDs.
- Queue can be scheduled and approved.
- Unapproved publication is blocked.
- Approved mock publication creates a Publication result.
- Monitoring and Analytics reflect the result.
- Optimization presents bounded advisory signals only.

## C. Control plane
- Approval Gateway visible.
- Registry shows adapter states.
- Audit / History records events.
- System Health reports isolation and secret status.

## D. Isolation and security
- No secrets committed.
- No external account is required for mock validation.
- No legacy project is imported or modified.
- No autonomous third-party publishing.

## E. Failure protocol
If Freebuff reports errors, return the complete result to GitHub workflow; fix source files; update checkpoint/docs; then perform one consolidated retest. Do not revert to stage-by-stage user testing unless a genuine blocker requires it.
