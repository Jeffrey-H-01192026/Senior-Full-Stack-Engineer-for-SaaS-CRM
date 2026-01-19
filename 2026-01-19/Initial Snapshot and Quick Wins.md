# Initial 10-Point Snapshot — 2026-01-19

This snapshot summarizes what’s known from current access, docs, and metrics, and outlines immediate actions to de-risk the system. Items are ordered by impact on stability/security.

## Snapshot

1) RLS/Tenant Isolation
- Status: RLS enabled; full policy audit pending.
- Risk: Cross-tenant reads via joins or missing tenant predicates.
- Actions: enumerate tables with `tenant_id`, verify `USING WITH CHECK` alignment, default-deny where unsure, add test queries for cross-tenant access.

2) Auth Boundaries
- Status: Supabase Auth in use; session and JWT handling not yet verified end‑to‑end.
- Actions: confirm JWT claims used in policies, verify logout/revocation, re-check service-role usage and API keys in frontend.

3) Slow Queries & Indexes
- Signal: p90 ~1–1.5s; Supabase shows 3.6–3.7s slow queries.
- Actions: export slow queries; add/verify indexes on `tenant_id`, FK columns, and common filters; compare query plans pre/post.

4) N+1 and Pagination
- Status: Unknown; typical risk in AI-generated codepaths.
- Actions: review high-traffic endpoints; ensure server-side pagination and batched queries.

5) External Integrations (Payments, Quo, OpenPhone)
- Risk: UI blocking calls, lack of retries/idempotency, webhook validation gaps.
- Actions: standardize API client wrappers, enable idempotency, move long tasks to background where applicable.

6) Error Handling & Observability
- Status: Render metrics available; structured, contextual logs not yet confirmed.
- Actions: add request IDs, user/tenant tags, and error context around critical flows; centralize fetch/client logging.

7) Environment Parity
- Status: Dev + Prod on Render; parity not yet validated.
- Actions: diff env vars, API keys, and Supabase anon/service roles across environments; document known differences.

8) Frontend Console/Network Hygiene
- Signal: Not yet reviewed; common 404s and console errors are typical.
- Actions: quick pass to eliminate red errors/404s, normalize error surfaces to users.

9) Onboarding Friction
- Signal: Users struggle to start; need starter templates/production rates.
- Actions: seed default data on tenant creation; add guided steps to first-login flow.

10) Deployment Safety
- Status: GitHub repo established; deployment gate/rules not documented.
- Actions: small, safe diffs; label PRs by risk; maintain weekly checkpoints; ensure quick rollback path.

## Quick Wins (proposed for next push)

1) Index the Hot Paths (30–60 min)
- What: Ensure indexes on `tenant_id` + frequent filters/joins; verify FK indexes.
- Why: Immediate reduction in slow queries; lowers p90.
- Rollback: Index drops are safe; keep DDL in a reversible SQL file.

2) Console/404 Cleanup (1–2 h)
- What: Fix top console errors and missing assets/API 404s; normalize error toasts.
- Why: Reduces noisy failures and user confusion; faster triage.
- Rollback: Revert the small diffs if any regression appears.

3) Fetch/Client Wrapper with Request IDs (1.5–2 h)
- What: Add a single wrapper for external/API calls that injects correlation IDs, tenant/user tags, retry-on-transient, and consistent error shapes.
- Why: Stabilizes integrations and improves observability without large refactors.
- Rollback: Swap back to native `fetch`/client calls; wrapper is additive.

4) RLS Default‑Deny on Uncertain Tables (1–2 h)
- What: Where policies are unclear, add a default-deny policy and explicitly permit tenant-scoped reads/writes.
- Why: Eliminates accidental cross-tenant reads while the audit proceeds.
- Rollback: Relax policies per-table as rules are validated.

5) Starter Templates + Production Rates Seed (2–3 h)
- What: Seed a minimal dataset on new tenant creation (sample customers, rate tables, example project).
- Why: Lowers onboarding friction immediately; gives users something concrete to edit.
- Rollback: Feature flag the seeding; easy to disable if issues arise.

## Next Steps
- Run the 60‑minute audit (UI/network/console) and export slow queries.
- Apply Quick Wins 1–3 first; then 4–5 behind a flag.
- Deliver Week‑1 PR checklist with exact diffs and owners.
