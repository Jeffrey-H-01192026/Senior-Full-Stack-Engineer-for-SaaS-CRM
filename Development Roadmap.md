# Development Roadmap - SnapCoat CRM

## Phase 1: Security & Stability (Weeks 1-2) - 75 hours

### Week 1: Security Hardening
**Priority: CRITICAL**

#### 1. RLS Audit & Fixes (8h)
- [ ] Audit all 189/190 table RLS policies
- [ ] Identify tenant_id column usage patterns
- [ ] Test cross-tenant access scenarios
- [ ] Fix boundary leaks in joins
- [ ] Validate implicit filtering

**Deliverable:** Security audit report with all tenant isolation gaps closed

#### 2. Database Indexing (4h)
- [ ] Analyze slow query logs (3.6s+ queries)
- [ ] Add indexes on tenant_id columns
- [ ] Index foreign key relationships
- [ ] Optimize RLS policy predicates
- [ ] Verify query plan improvements

**Deliverable:** All critical paths indexed, query times < 500ms

#### 3. Query Performance Profiling (6h)
- [ ] Profile Supabase slow queries
- [ ] Identify N+1 patterns in API calls
- [ ] Analyze pagination efficiency
- [ ] Review connection pooling config
- [ ] Test under simulated load

**Deliverable:** Performance baseline + optimization plan

#### 4. Auth & Tenant Scoping (4h)
- [ ] Verify tenant_id in all API endpoints
- [ ] Audit middleware auth checks
- [ ] Test session management
- [ ] Review JWT token handling
- [ ] Validate logout/revocation

**Deliverable:** Auth boundaries enforced end-to-end

---

### Week 2: Integration Hardening
**Priority: HIGH**

#### 5. Payment API Refactoring (8h)
- [ ] Move processing to background jobs
- [ ] Implement retry logic (exponential backoff)
- [ ] Add idempotency keys
- [ ] Improve error messages
- [ ] Add webhook validation

**Deliverable:** 99%+ payment success rate

#### 6. Quo Integration Stability (6h)
- [ ] Convert to async workflows
- [ ] Add job queue processing
- [ ] Implement error retry
- [ ] Add webhook handling
- [ ] Test failure scenarios

**Deliverable:** Reliable quoting without blocking UI

#### 7. OpenPhone Integration (6h)
- [ ] Async call implementation
- [ ] Error retry logic
- [ ] Request batching
- [ ] Response caching
- [ ] Rate limit handling

**Deliverable:** Stable communication integration

#### 8. Structured Logging (3h)
- [ ] Add logging to payment flows
- [ ] Log external API calls
- [ ] Capture error context
- [ ] Add request tracing
- [ ] Set up log aggregation

**Deliverable:** Full observability into critical flows

#### 9. Database Configuration (3h)
- [ ] Tune connection pool settings
- [ ] Optimize Supabase limits
- [ ] Review timeout configs
- [ ] Test connection lifecycle
- [ ] Monitor pool exhaustion

**Deliverable:** Stable DB connections under load

#### 10. Error Handling Wrappers (4h)
- [ ] Wrap all external API calls
- [ ] Add graceful degradation
- [ ] Implement circuit breakers
- [ ] Handle rate limits
- [ ] Add user-friendly errors

**Deliverable:** Resilient external integrations

---

## Phase 2: Onboarding & UX (Week 3) - 16 hours

### User Experience Improvements
**Priority: HIGH**

#### 11. Starter Templates (6h)
- [ ] Design default project templates
- [ ] Create sample customer records
- [ ] Add demo tasks/workflows
- [ ] Build production rate tables
- [ ] Test new user flow

**Deliverable:** New users see populated data immediately

#### 12. Account Setup Automation (5h)
- [ ] Auto-create default settings
- [ ] Seed production rates
- [ ] Generate starter projects
- [ ] Pre-populate service catalogs
- [ ] Add guided tour

**Deliverable:** < 15 minute onboarding time

#### 13. Data Migration Tools (5h)
- [ ] CSV import for customers
- [ ] Excel import for projects
- [ ] Data validation rules
- [ ] Error handling & previews
- [ ] Import progress tracking

**Deliverable:** Easy migration from existing systems

---

## Phase 3: Infrastructure (Week 4) - 14 hours

### System Reliability
**Priority: MEDIUM**

#### 14. Background Job Processing (4h)
- [ ] Set up job queue (Bull/BullMQ)
- [ ] Move long-running tasks async
- [ ] Add job retry logic
- [ ] Implement job monitoring
- [ ] Test failure recovery

**Deliverable:** API stays responsive under load

#### 15. Caching Layer (4h)
- [ ] Evaluate Redis setup
- [ ] Cache service catalogs
- [ ] Cache production rates
- [ ] Cache frequently-read data
- [ ] Set cache invalidation

**Deliverable:** Reduced database load

#### 16. Testing Coverage (6h)
- [ ] Unit tests for auth flows
- [ ] Integration tests for payments
- [ ] E2E tests for critical paths
- [ ] RLS policy tests
- [ ] Load testing scripts

**Deliverable:** Automated regression protection

---

## Quick Wins (First 48 Hours)

### Immediate Impact Items
**Can be implemented during initial audit**

1. **Missing Indexes** (30 min)
   - Add tenant_id indexes where missing
   - Index frequently-queried columns

2. **Console Errors** (1h)
   - Fix JavaScript errors
   - Remove broken API calls
   - Clean up 404s

3. **UI Blocking** (1h)
   - Move slow operations to background
   - Add loading states
   - Improve error messages

4. **RLS Low-Hanging Fruit** (2h)
   - Fix obvious policy gaps
   - Add missing tenant checks
   - Simplify complex policies

5. **Performance Wins** (1h)
   - Enable query caching
   - Reduce API payload sizes
   - Optimize frequent queries

**Total:** ~5-6 hours for measurable improvements

---

## Success Metrics

### Security (Phase 1)
- ✅ 0 RLS policy failures in audit
- ✅ 100% tenant isolation coverage
- ✅ 0 auth bypass vulnerabilities

### Performance (Phase 1)
- ✅ P90 response time < 1s (currently 1-1.5s)
- ✅ P99 response time < 2s
- ✅ Database query time < 500ms average

### Reliability (Phase 1-2)
- ✅ Payment success rate > 99%
- ✅ Integration uptime > 99.5%
- ✅ 0 production incidents

### Onboarding (Phase 2)
- ✅ Setup time < 15 minutes
- ✅ 80% of users complete onboarding
- ✅ Data import success rate > 95%

### Infrastructure (Phase 3)
- ✅ Background jobs processing reliably
- ✅ Cache hit rate > 70%
- ✅ Test coverage > 60% critical paths

---

## Risk Mitigation

### High-Risk Changes
1. **RLS Policies:** Test thoroughly in dev, validate with real data
2. **Payment Flows:** Never deploy on Friday, have rollback ready
3. **Database Indexes:** Monitor query plans, watch for lock contention

### Rollback Strategy
- All changes deployed as feature flags
- Database migrations reversible
- Small batch deployments
- Monitor metrics 24h post-deploy

### Communication Protocol
- Daily updates on progress
- Immediate escalation for blockers
- Weekly checkpoint calls
- Document all decisions in Slack

---

## Future Roadmap (Post-Stabilization)

### Phase 4: AI Agent (4-6 weeks)
- Lead nurturing workflows
- Automated follow-ups
- Customer engagement scoring
- Email/SMS automation
- Integration with CRM data

### Phase 5: Mobile Apps (8-12 weeks)
- iOS app for field crews
- Android app for field crews
- Offline support
- Photo capture/upload
- GPS tracking

### Phase 6: Advanced Features
- Advanced reporting & analytics
- Multi-location support
- Team collaboration tools
- Document management
- Inventory tracking

---

## Estimated Timeline

| Phase | Duration | Hours | Status |
|-------|----------|-------|--------|
| Phase 1: Security & Stability | 2 weeks | 75h | 🔄 In Progress |
| Phase 2: Onboarding & UX | 1 week | 16h | ⏳ Planned |
| Phase 3: Infrastructure | 1 week | 14h | ⏳ Planned |
| **Total Core Stabilization** | **4 weeks** | **105h** | - |

**Additional buffer:** 15-20 hours for unexpected issues, testing, documentation

**Grand Total:** ~120-125 hours for complete stabilization

---

## Next Actions

### Immediate (Today)
- [x] Access granted
- [x] Credentials received
- [ ] Initial app audit (60 min report)
- [ ] Identify quick wins
- [ ] Prioritize Week 1 tasks

### This Week
- [ ] Complete security audit
- [ ] Fix critical RLS issues
- [ ] Add missing indexes
- [ ] Profile slow queries
- [ ] Weekly checkpoint report

### Next Week
- [ ] Payment API refactoring
- [ ] Integration hardening
- [ ] Logging implementation
- [ ] Error handling improvements
- [ ] Week 2 checkpoint report
