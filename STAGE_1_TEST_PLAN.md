# STAGE 1 — APPLICATION FOUNDATION TEST PLAN

1. Application shell renders without external services.
2. Dashboard shows job counters and active jobs.
3. New Job creates a unique Job ID in DRAFT.
4. Workflow advances only through the handbook state chain.
5. State transitions create audit events.
6. Approval Gateway becomes PENDING at consequential states.
7. Registry reports only local/mock adapters and no false integrations.
8. System Health reports repository-safe status.
9. Layout remains usable on mobile widths.
10. npm run build completes successfully.

Runtime note: Freebuff preview/build verification is still required for formal Stage 1 acceptance because Freebuff is the designated runtime and has no direct connector available in this session.