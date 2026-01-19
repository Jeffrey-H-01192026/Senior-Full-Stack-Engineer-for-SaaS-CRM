# Daily TODO - 2026-01-19

Project: SnapCoat CRM (Render + Supabase)
Owner: Jeffrey Helseth

Total Timebox: ~7h

1) Access & Environment Verification — 15m
- What: Confirm login to Supabase (dev/prod), Render, and staging app
- How: Validate permissions, org/project scopes, and environment variables visibility
- Deliverable: Note access confirmation + any gaps

2) 60-Min App Audit (UI/Network/Console) — 60m
- What: End-to-end pass of staging app
- How: Open DevTools → Network/Console; capture errors, 404s, long requests (>1s)
- Deliverable: Audit notes with 3–5 example requests and trace links

3) Supabase RLS Quick Scan — 90m
- What: Identify obvious tenant isolation risks
- How: Review policies for core tables (users, companies, jobs, invoices, messages)
- Deliverable: List of policy issues + immediate fixes (low-hanging fruit)

4) Slow Query Export + Index Plan — 60m
- What: Capture slow queries (p90 > 1s) and propose indexes
- How: Supabase → Database → Observability/Performance; map predicates to indexes
- Deliverable: Index plan (table, columns, reason)

5) Render Logs + Error Taxonomy — 45m
- What: Classify recurring errors (by endpoint/integration)
- How: Render logs filter last 24–48h; group by route/stack trace
- Deliverable: Top 5 recurring issues + suggested fixes

6) Onboarding UX Walkthrough — 45m
- What: Document friction points for new tenant
- How: Fresh signup path; note missing templates/rates/data priming
- Deliverable: 5 changes to reduce time-to-value (<15 min target)

7) Quick Wins Draft (5 items) — 45m
- What: High-impact, low-effort fixes from steps 2–6
- How: For each—owner, estimate, rollback plan
- Deliverable: Ready-to-execute checklist

8) Week 1 Change Plan + PR Checklist — 30m
- What: Scope Security & Stability week
- How: Break down into small deployable PRs; include rollout/rollback steps
- Deliverable: Plan aligned to Roadmap Phase 1

9) Stakeholder Update — 15m
- What: Send summary to Braiden
- How: 10-point snapshot + 3–5 quick wins + asks
- Deliverable: Draft message content

10) Repo Hygiene & Docs Sync — 15m
- What: Ensure dated logs, update README links, commit+push
- How: Git commit & push to `main`
- Deliverable: PR-less push to project repo
