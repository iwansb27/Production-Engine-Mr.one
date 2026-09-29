# STAGE 2 TEST PLAN

Stage 2 — Discovery Center

## Acceptance tests
1. Open Discovery Center from navigation.
2. Create a new candidate and verify a unique Candidate ID.
3. Edit title, source URL, evidence, and notes.
4. Save a candidate and verify status SAVED.
5. Archive a candidate and verify status ARCHIVED.
6. Search candidates by title/source/evidence.
7. Filter candidates by status.
8. Select a candidate and inspect its evidence/source URL.
9. Handoff a candidate to Research; verify status READY_FOR_RESEARCH and an audit event.
10. Verify no scraping, downloading, automatic affiliate publishing, or external service is required.

Runtime commands remain the Stage 1 proven path: npm ci, npm run build, then npm run dev -- --host 0.0.0.0 --port 5173.
