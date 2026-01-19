# SnapCoat CRM - Senior Full-Stack Engineer Project

## Quick Links

- **[Communication Log](Communication%20Log.md)** - All Slack/Upwork conversations
- **[Project Overview](Project%20Overview.md)** - System architecture, metrics, and goals
- **[Development Roadmap](Development%20Roadmap.md)** - Prioritized work breakdown
- **[Job Post](Job%20Post.md)** - Original job requirements
- **[Cover Letter](Cover%20Letter..md)** - Initial proposal and experience

---

## Project Status: 🔄 In Progress

**Start Date:** January 19, 2026  
**Current Phase:** Phase 1 - Security & Stability  
**Progress:** Initial audit in progress

---

## Daily Logs

- 2026-01-19: See `2026-01-19/` for today's TODO and notes
	- Deliverable: [Initial Snapshot and Quick Wins](2026-01-19/Initial%20Snapshot%20and%20Quick%20Wins.md)

---

## Current Access

### Application
- **Dev/Staging:** https://snapcoat-crm-development-preview.onrender.com/
- **Username:** developer@snapcoatcrm.com
- **Password:** Testing#123

### Infrastructure
- ✅ Supabase (Development + Production)
- ✅ Render (SnapCoat CRM project)
- ✅ Email: developer@snapcoatcrm.com

---

## Today's Priorities

1. [ ] Complete 60-minute application audit
2. [ ] Document RLS risks and quick wins
3. [ ] Identify 3-5 high-impact improvements
4. [ ] Share initial findings with client

---

## Technical Stack

- **Frontend:** React on Render
- **Backend:** Supabase (PostgreSQL + RLS)
- **Environments:** Production + Development
- **Users:** ~35 accounts, ~15 companies
- **Status:** Pre-revenue (5 subscriptions)

---

## Key Focus Areas

### Security
- RLS policy audit for tenant isolation
- Cross-tenant data leak prevention
- Auth boundary enforcement

### Performance
- Query optimization (targeting < 500ms)
- N+1 elimination
- Connection pooling tuning

### Integrations
- Payment API hardening
- Quo/OpenPhone stability
- Error retry logic

### Onboarding
- Starter templates
- Default production rates
- Data migration tools

---

## Metrics Reference

### Render Metrics (attached screenshots)
- `image (16).png` - Render dashboard overview
- `image (17).png` - Recent metrics (CPU/Memory)
- `image (18).png` - Application metrics
- `image (19).png` - Instance scaling
- `image (20).png` - Network metrics

### Supabase Issues
- **Development:** 247 issues (5 security, 242 performance)
- **Production:** 49 issues (15 security, 34 performance)

---

## Communication Protocol

- **Primary:** Slack (snapcoat-dev channel)
- **Backup:** Upwork messaging
- **Documentation:** All requirements logged in [Communication Log](Communication%20Log.md)
- **Updates:** Weekly checkpoint reports

---

## File Organization

### Active Documents
- `Communication Log.md` - Consolidated chat history
- `Project Overview.md` - System architecture and goals
- `Development Roadmap.md` - Work breakdown and timeline
- `README.md` - This file

### Reference Documents
- `Job Post.md` - Original requirements
- `Cover Letter..md` - Proposal and experience

### Archived (to be removed)
- ~~`Chat On Slack 01-19-2026 11-29-45.md`~~ → Merged into Communication Log
- ~~`Chat On Upwork 01-18-2026 20-27-16.md`~~ → Merged into Communication Log
- ~~`Chat On Upwork 01-19-2026 11-26-51.md`~~ → Merged into Communication Log

### Assets
- `image (16-21).png` - Render/Supabase metrics screenshots

---

## Next Steps

1. Complete initial audit (see `2026-01-19/TODO.md`)
2. RLS policy quick scan and notes
3. Slow query export + index plan
4. Draft 5 quick wins and Week 1 change plan
5. Report findings to client and push updates
