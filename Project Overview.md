# SnapCoat CRM - Project Overview

## Project Summary

**Client:** Braiden Smith, SnapCoat LLC  
**Project Type:** SaaS CRM for Painting Contractors  
**Status:** Live production with paying clients (pre-revenue stage)  
**Start Date:** January 19, 2026

---

## Technical Stack

### Frontend
- **Hosting:** Render
- **Environments:** Production + Development/Staging
- **Features:** Comprehensive logging available

### Backend
- **Platform:** Supabase (PostgreSQL + Auth + Storage)
- **Security:** Row-Level Security (RLS) implemented
- **Databases:** 
  - Production: 190 tables, 0 functions, 0 replicas
  - Development: 189 tables, 0 functions, 0 replicas

### Infrastructure
- **Origin:** Migrated from Replit → Render + Supabase
- **Monitoring:** Render metrics (CPU, Memory, Network)
- **Performance:** 
  - Response times: 1-1.5s average (p90)
  - Memory: 25-40% utilization (2GB limit)
  - CPU: 1 vCPU with burst capacity

---

## Current Metrics

### Users & Scale
- **User Accounts:** ~35 active users
- **Companies:** ~15 companies registered
- **Subscriptions:** 5 active subscriptions
- **Production Usage:** 1 painting company fully operational

### System Health (Last 48 Hours)
- **REST Requests:** 6 (Development), 6 (Production)
- **Auth Requests:** 6 (Development), 6 (Production)
- **Storage Requests:** 0 (both environments)
- **Bandwidth:** 11.58 GB monthly usage
- **Total Requests:** ~20-50k daily (variable peaks)

### Known Issues
- **Development:** 247 issues need attention (5 security, 242 performance)
- **Production:** 49 issues need attention (15 security, 34 performance)
- Slow queries detected (3.63-3.74s average)
- RLS policy warnings on multiple tables

---

## Core Business Problem

### Target Market
Painting contractors across the United States who need:
- Customer relationship management
- Project estimation and quoting
- Job tracking and management
- Payment processing
- Communication integration (Quo, OpenPhone)

### Current Pain Points
1. **Onboarding Friction:** Users struggle to get started
2. **Data Migration:** Difficult to import from existing CRM/estimation systems
3. **Missing Templates:** Need better starter templates and production rates
4. **Integration Stability:** Payment, Quo, OpenPhone APIs need hardening

---

## Project Goals

### Phase 1: Stabilization (Current)
1. **Security Hardening**
   - Audit RLS policies for tenant isolation
   - Fix cross-tenant data leak risks
   - Implement proper auth boundaries

2. **Performance Optimization**
   - Eliminate N+1 query patterns
   - Add missing indexes on foreign keys
   - Optimize slow RLS evaluations
   - Tune connection pooling

3. **Bug Fixes**
   - Production bug triage and resolution
   - Error handling improvements
   - Edge case defensive checks

### Phase 2: Onboarding Improvements
1. **User Experience**
   - Starter templates for new users
   - Default production rates
   - Sample data scaffolding
   - Guided setup workflow

2. **Data Migration**
   - Import tools for common CRM systems
   - CSV/Excel import workflows
   - Data validation and cleanup

### Phase 3: Integration Hardening
1. **Payment Processing**
   - Async workflows with retry logic
   - Idempotency guarantees
   - Better error messaging

2. **Communication APIs**
   - Quo integration stability
   - OpenPhone webhook reliability
   - Rate limiting and caching

### Future: AI Agent
- Lead nurturing automation
- Automated follow-ups
- Customer engagement workflows

---

## Technical Priorities

### Immediate (Week 1-2)
1. RLS audit and security fixes (8h)
2. Index optimization (4h)
3. Slow query profiling (6h)
4. Payment API hardening (8h)
5. Quo/OpenPhone stabilization (12h)

### Short-term (Week 3-4)
6. Onboarding templates (6h)
7. Default data seeding (5h)
8. Tenant scoping verification (4h)
9. Auth middleware tightening (4h)
10. Logging and observability (3h)

### Medium-term (Week 5-6)
11. Background job processing (4h)
12. Caching layer (Redis) (4h)
13. Database config tuning (3h)
14. Error handling wrappers (4h)
15. Testing coverage (12h)

**Total Estimated:** ~95-110 hours

---

## Success Criteria

### Security
- ✅ Zero cross-tenant data leaks
- ✅ All RLS policies validated
- ✅ Auth boundaries enforced at DB level

### Performance
- ✅ P90 response time < 1s
- ✅ All queries indexed properly
- ✅ No N+1 patterns in critical paths

### Stability
- ✅ Payment success rate > 99%
- ✅ Zero production downtime
- ✅ Integration retry logic in place

### Onboarding
- ✅ New user setup < 15 minutes
- ✅ Data import tools functional
- ✅ Sample data pre-populated

---

## Risk Areas

### High Priority
1. **Tenant Isolation:** RLS policy gaps could expose data
2. **Payment Processing:** No retry/idempotency = lost revenue
3. **Query Performance:** Slow queries under load will break UX

### Medium Priority
4. **Third-party APIs:** Quo/OpenPhone downtime impacts users
5. **Onboarding UX:** Poor experience = high churn
6. **Data Migration:** Complex imports = support burden

### Low Priority
7. **Caching:** Not critical at current scale
8. **Offline Mode:** Nice-to-have, not blocking
9. **Testing Coverage:** Needed but not urgent

---

## Development Approach

### Workflow
1. **Discovery:** Logs, metrics, RLS policies, slow queries
2. **Prioritization:** Security → Stability → Performance → UX
3. **Implementation:** Small, safe diffs with rollback capability
4. **Validation:** Test in staging, ship to production incrementally
5. **Monitoring:** Track metrics before/after each change

### Communication
- All requirements documented in Slack/Upwork chat
- Weekly checkpoint updates
- Immediate escalation for blockers
- ROI visibility at each milestone

### Deliverables
- Prioritized issue list (RLS, queries, integrations)
- 3-5 quick wins (high-impact, low-effort fixes)
- Security audit report
- Performance optimization recommendations
- Onboarding improvement plan

---

## Next Steps

1. ✅ Access granted (Supabase + Render)
2. ✅ Application credentials received
3. 🔄 Initial application audit (in progress)
4. ⏳ RLS policy review
5. ⏳ Slow query analysis
6. ⏳ 60-minute findings report
