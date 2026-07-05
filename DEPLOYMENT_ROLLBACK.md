# DEPLOYMENT_ROLLBACK.md

# My Gujarat Property — Deployment, Backup, Migration And Rollback Rules

This file defines deployment, backup, migration safety, rollback, production launch, smoke testing and incident handling rules for **My Gujarat Property**.

Claude must update this file whenever deployment, migration, backup, restore, rollback, feature flag, provider mode, environment, production launch or infrastructure behavior changes.

No production update is allowed without backup and rollback plan.

No fake production PASS is allowed.

---

## 1. Purpose

This file exists to make sure every update is safe, reversible and documented.

It covers:

* development deployment rules
* staging deployment rules
* production deployment rules
* backup rules
* database backup rules
* storage backup rules
* code rollback rules
* database rollback rules
* storage rollback rules
* SQL migration safety
* destructive migration approval
* feature flag rollback
* provider fallback
* payment rollback safety
* RLS/security rollback safety
* deployment smoke testing
* production launch checklist
* incident handling
* post-incident review
* two-Claude-account continuation

---

## 2. Absolute Deployment Rules

Claude must follow these rules:

1. Do not deploy without knowing changed files.
2. Do not deploy without checking SQL/migration impact.
3. Do not deploy destructive DB changes without backup and rollback notes.
4. Do not deploy provider-backed features with fake success.
5. Do not deploy payment features without verified webhook or setup-required state.
6. Do not deploy auth/RLS changes without allowed and denied access checks.
7. Do not deploy if service role key can be exposed to client.
8. Do not deploy if hidden contact number leaks.
9. Do not deploy if private documents use public bucket incorrectly.
10. Do not deploy if admin/staff routes are public/indexable.
11. Do not deploy if build fails.
12. Do not deploy if lint/typecheck/build are not run and reason is not documented.
13. Do not deploy if manual verification is missing.
14. Do not deploy if rollback path is missing.
15. Do not deploy if production still uses dev OTP/test payment/mock providers.
16. Do not deploy if demo/test data is public in production.
17. Do not deploy if legal/Terms/Privacy required pages are missing for launch.
18. Do not deploy if critical bugs are open.
19. Do not deploy if Feature Registry is not updated.
20. Do not deploy if Changelog is not updated.
21. Do not deploy if Manual Verification is not updated.
22. Do not deploy if brain.md resume guide is not updated.
23. Do not remove working features for deployment unless user explicitly approves.
24. If deployment is partial, mark `PARTIAL` or `BLOCKED`, not `PASS`.
25. Production deploy requires final Super Admin/user signoff.

---

## 3. Deployment Status Values

Use only these deployment status values:

| Status                 | Meaning                                              |
| ---------------------- | ---------------------------------------------------- |
| `NOT_STARTED`          | Deployment not started                               |
| `PLANNED`              | Deployment planned but not executed                  |
| `READY_FOR_STAGING`    | Ready to deploy to staging                           |
| `STAGING_DEPLOYED`     | Deployed to staging                                  |
| `STAGING_VERIFIED`     | Staging smoke/manual verification passed             |
| `READY_FOR_PRODUCTION` | Ready for production deploy                          |
| `PRODUCTION_DEPLOYED`  | Production deploy completed                          |
| `PRODUCTION_VERIFIED`  | Production smoke/manual verification passed          |
| `PARTIAL`              | Deployment partially completed or partially verified |
| `BLOCKED`              | Deployment blocked                                   |
| `FAILED`               | Deployment failed                                    |
| `ROLLED_BACK`          | Deployment rolled back                               |
| `HOTFIX_DEPLOYED`      | Urgent fix deployed                                  |
| `MONITORING`           | Deployment completed and under monitoring            |

---

## 4. Rollback Status Values

Use only these rollback status values:

| Status                  | Meaning                                     |
| ----------------------- | ------------------------------------------- |
| `NOT_REQUIRED`          | Rollback not needed                         |
| `READY`                 | Rollback plan exists                        |
| `IN_PROGRESS`           | Rollback is currently being done            |
| `COMPLETED`             | Rollback completed                          |
| `PARTIAL`               | Rollback partially completed                |
| `FAILED`                | Rollback failed                             |
| `BLOCKED`               | Rollback cannot proceed                     |
| `NEEDS_BACKUP_RESTORE`  | Database/storage restore required           |
| `FEATURE_FLAG_DISABLED` | Rollback done through feature flag          |
| `CODE_REVERTED`         | Code rollback completed                     |
| `DB_REVERTED`           | Database rollback completed                 |
| `STORAGE_RESTORED`      | Storage rollback/restore completed          |
| `MONITORING`            | Rollback completed and monitoring continues |

---

## 5. Environment Types

Use these environment labels:

| Environment   | Purpose                          |
| ------------- | -------------------------------- |
| `LOCAL`       | Developer local machine          |
| `DEVELOPMENT` | Dev environment                  |
| `STAGING`     | Production-like test environment |
| `PRODUCTION`  | Live public website              |
| `PREVIEW`     | PR/branch preview deploy         |
| `MAINTENANCE` | Maintenance mode                 |
| `ROLLBACK`    | Temporary rollback state         |
| `HOTFIX`      | Urgent fix environment/state     |

---

## 6. Required Deployment Entry Format

Every deployment must be documented using this format:

```md id="deploy-entry"
## DEPLOY-YYYYMMDD-000 — Deployment Title

### Status
NOT_STARTED / PLANNED / READY_FOR_STAGING / STAGING_DEPLOYED / STAGING_VERIFIED / READY_FOR_PRODUCTION / PRODUCTION_DEPLOYED / PRODUCTION_VERIFIED / PARTIAL / BLOCKED / FAILED / ROLLED_BACK / HOTFIX_DEPLOYED / MONITORING

### Environment
LOCAL / DEVELOPMENT / STAGING / PRODUCTION / PREVIEW / MAINTENANCE / ROLLBACK / HOTFIX

### Deployment Date
- Date:
- Time:
- Timezone:
- Deployed by:
- Branch:
- Commit:
- Version/build number:

### Scope
- What changed:
- Why changed:
- User request / phase:
- Related prompt file:
- Related manual verification prompt:
- Related docs:

### Changed Files
- `path/to/file`

### SQL / Migration Files
- `path/to/migration.sql`
- or `None`

### Database Impact
- Tables changed:
- Columns changed:
- Enums changed:
- Indexes changed:
- Triggers/functions changed:
- RLS policies changed:
- Public-safe views changed:
- Seed/demo data changed:
- Destructive changes:
- Data migration required:
- Backup required:

### Storage / Media Impact
- Buckets changed:
- Public files changed:
- Private files changed:
- CDN/cache changed:
- Orphan cleanup impact:
- Backup required:

### Provider / API Impact
- Supabase:
- OTP:
- SMS:
- Email:
- WhatsApp:
- Razorpay:
- Maps:
- Cloudflare R2:
- Cloudflare CDN:
- Turnstile:
- Analytics:
- Error tracking:
- Cron/background jobs:
- Setup-required providers:

### Security / RLS Impact
- Auth impact:
- Role/RBAC impact:
- RLS impact:
- Contact privacy impact:
- Private document impact:
- Admin/staff access impact:
- Payment/webhook security impact:
- Service role exposure risk:
- Rate limit impact:
- Audit log impact:

### Backup
- Code backup:
- DB backup:
- Storage backup:
- Config/env backup:
- Provider config backup:
- Backup location/reference:
- Backup verified: Yes/No

### Pre-Deployment Checks
| Check | Result | Notes |
|---|---|---|
| Docs updated | PASS/PARTIAL/BLOCKED/FAIL |  |
| Feature Registry updated | PASS/PARTIAL/BLOCKED/FAIL |  |
| Changelog updated | PASS/PARTIAL/BLOCKED/FAIL |  |
| Bugs/Fixes updated | PASS/PARTIAL/BLOCKED/FAIL |  |
| Manual Verification updated | PASS/PARTIAL/BLOCKED/FAIL |  |
| Lint | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN |  |
| Typecheck | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN |  |
| Build | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN |  |
| Tests | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN |  |
| SQL migration reviewed | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| RLS checked | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Provider status checked | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Backup completed | PASS/PARTIAL/BLOCKED/FAIL |  |
| Rollback plan ready | PASS/PARTIAL/BLOCKED/FAIL |  |

### Deployment Steps
1.
2.
3.

### Post-Deployment Smoke Test
| Check | Result | Notes |
|---|---|---|
| Homepage opens | PASS/PARTIAL/BLOCKED/FAIL |  |
| Search opens | PASS/PARTIAL/BLOCKED/FAIL |  |
| Auth opens | PASS/PARTIAL/BLOCKED/FAIL |  |
| Dashboard route check | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Admin route check | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| DB connection | PASS/PARTIAL/BLOCKED/FAIL |  |
| RLS/public data check | PASS/PARTIAL/BLOCKED/FAIL |  |
| Provider fallback check | PASS/PARTIAL/BLOCKED/FAIL |  |
| Payment safety check | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Upload/media check | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| No critical console/server error | PASS/PARTIAL/BLOCKED/FAIL |  |
| Mobile quick check | PASS/PARTIAL/BLOCKED/FAIL |  |

### Rollback Plan
- Rollback status:
- Code rollback:
- DB rollback:
- Storage rollback:
- Feature flag rollback:
- Provider rollback:
- Estimated risk:
- Data loss risk:
- User impact:
- Rollback trigger:

### Final Result
PASS / PARTIAL / BLOCKED / FAIL / ROLLED_BACK

### Pending Issues
-

### Next Action
-
```

---

## 7. Required Rollback Entry Format

Every rollback must be documented using this format:

```md id="rollback-entry"
## ROLLBACK-YYYYMMDD-000 — Rollback Title

### Status
NOT_REQUIRED / READY / IN_PROGRESS / COMPLETED / PARTIAL / FAILED / BLOCKED / NEEDS_BACKUP_RESTORE / FEATURE_FLAG_DISABLED / CODE_REVERTED / DB_REVERTED / STORAGE_RESTORED / MONITORING

### Rollback Date
- Date:
- Time:
- Timezone:
- Performed by:
- Environment:
- Related deployment:
- Related incident/bug:

### Reason
- What went wrong:
- User impact:
- Security impact:
- Payment impact:
- Data impact:
- Provider impact:

### Scope
- Code rollback:
- DB rollback:
- Storage rollback:
- Provider/config rollback:
- Feature flag rollback:
- CDN/cache rollback:

### Files Reverted
- `path/to/file`

### SQL / Migration Rollback
- Migration reverted:
- Rollback SQL file:
- Backup restored:
- Data repair needed:
- RLS restored:
- Index restored:
- Function/trigger restored:

### Storage Rollback
- Bucket:
- Files restored:
- Files removed:
- CDN cache purged:
- Private file access checked:

### Provider Rollback
- Provider:
- Previous mode:
- Restored mode:
- Secret rotation needed:
- Webhook reconfigured:
- Test/live mode checked:

### Steps Performed
1.
2.
3.

### Verification After Rollback
| Check | Result | Notes |
|---|---|---|
| Homepage works | PASS/PARTIAL/BLOCKED/FAIL |  |
| Auth works | PASS/PARTIAL/BLOCKED/FAIL |  |
| DB works | PASS/PARTIAL/BLOCKED/FAIL |  |
| RLS works | PASS/PARTIAL/BLOCKED/FAIL |  |
| Payment state safe | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Contact privacy safe | PASS/PARTIAL/BLOCKED/FAIL |  |
| Admin access safe | PASS/PARTIAL/BLOCKED/FAIL |  |
| Provider fallback safe | PASS/PARTIAL/BLOCKED/FAIL |  |
| Critical bug resolved | PASS/PARTIAL/BLOCKED/FAIL |  |

### Docs Updated
- `DEPLOYMENT_ROLLBACK.md`
- `CHANGELOG.md`
- `BUGS_AND_FIXES.md`
- `MANUAL_VERIFICATION.md`
- `FEATURE_REGISTRY.md`
- `brain.md`
- Other:

### Final Result
COMPLETED / PARTIAL / FAILED / BLOCKED / MONITORING

### Follow-Up Required
-
```

---

## 8. Backup Rules

Backup is mandatory before risky production changes.

### 8.1 Code Backup

Before production deployment:

* ensure latest stable branch/tag exists
* record current production commit
* record new deployment commit
* create release tag if using version tags
* keep rollback branch or previous deployment reference
* record changed files
* record package/lockfile changes
* record environment/config changes without secrets

Required format:

```md id="code-backup"
### Code Backup
- Current production commit:
- New commit:
- Release tag:
- Rollback commit/tag:
- Changed files:
- Package/lockfile changed: Yes/No
- Verified: Yes/No
```

### 8.2 Database Backup

Before DB changes in production:

* take database backup
* verify backup completed
* record backup reference
* do not paste private DB URL/credentials
* include schema backup if needed
* include data backup if destructive change
* backup before destructive migration is mandatory
* backup before RLS rewrite is mandatory
* backup before payment/billing migration is mandatory
* backup before auth/role migration is mandatory
* backup before contact/privacy migration is mandatory
* backup before admin/staff permission migration is mandatory

Required format:

```md id="db-backup"
### Database Backup
- Backup required: Yes/No
- Backup type: schema/data/full
- Backup reference:
- Backup verified: Yes/No
- Tables included:
- Restore tested: Yes/No
- Notes:
```

### 8.3 Storage Backup

Before storage/media changes:

* identify affected buckets
* identify public/private bucket impact
* backup critical files if deleting/moving
* verify private files remain private
* record CDN cache behavior
* do not expose private URLs

Required format:

```md id="storage-backup"
### Storage Backup
- Backup required: Yes/No
- Buckets:
- Public files affected:
- Private files affected:
- Backup reference:
- Restore tested: Yes/No
- CDN purge needed: Yes/No
- Notes:
```

### 8.4 Config / Environment Backup

Before environment/provider changes:

* record variable names changed
* do not record real values
* verify `.env.example` updated
* note previous provider mode
* note new provider mode
* note feature flags changed
* ensure secrets are in secure env only

Required format:

```md id="config-backup"
### Config / Env Backup
- Env variables changed:
- `.env.example` updated: Yes/No
- Real secrets exposed: No
- Previous provider mode:
- New provider mode:
- Feature flags changed:
- Rollback config path:
```

---

## 9. SQL Migration Safety Rules

Every DB change must use migration files.

DB changes include:

* table create/update/delete
* column add/update/delete
* enum add/update/delete
* index add/update/delete
* trigger add/update/delete
* function add/update/delete
* RLS policy add/update/delete
* public-safe view add/update/delete
* storage bucket policy add/update/delete
* seed/setup data add/update/delete
* cron/job function add/update/delete

### 9.1 Migration File Naming

Use phase-wise/timestamp-wise naming:

```txt id="migration-name"
supabase/migrations/YYYYMMDDHHMMSS_phase_XX_short_description.sql
```

Examples:

```txt id="migration-examples"
supabase/migrations/20260629090000_phase_02_auth_roles_rls.sql
supabase/migrations/20260629103000_phase_04_property_project_requirement.sql
supabase/migrations/20260629120000_phase_09_billing_payment_invoice.sql
```

### 9.2 Migration Must Include

Each migration must document:

* purpose
* tables changed
* columns changed
* indexes created
* RLS policies changed
* functions/triggers changed
* data migration impact
* destructive changes
* rollback notes
* seed/demo data status
* idempotency where possible

### 9.3 Migration Header Template

```sql id="migration-header"
-- Migration: YYYYMMDDHHMMSS_phase_XX_short_description.sql
-- Project: My Gujarat Property
-- Purpose:
-- Phase:
-- Related docs:
-- Tables changed:
-- RLS changed: Yes/No
-- Destructive changes: Yes/No
-- Backup required: Yes/No
-- Rollback notes:
-- Created by:
```

### 9.4 Destructive Migration Rules

Destructive changes include:

* dropping table
* dropping column
* deleting data
* changing enum in breaking way
* changing column type with data loss risk
* hard deleting records
* removing RLS policy without replacement
* publicizing private data
* moving private files to public bucket
* changing payment/subscription/invoice tables
* changing contact/private profile fields
* changing verification document storage

Before destructive migration:

1. Ask user approval.
2. Take DB backup.
3. Take storage backup if media affected.
4. Write rollback plan.
5. Write data repair plan.
6. Update `DEPLOYMENT_ROLLBACK.md`.
7. Update `CHANGELOG.md`.
8. Update `FEATURE_REGISTRY.md`.
9. Update `MANUAL_VERIFICATION.md`.
10. Run staging migration first.
11. Verify data and RLS.
12. Only then consider production.

---

## 10. Database Rollback Rules

Database rollback depends on migration type.

### 10.1 Safe Additive Changes

Examples:

* add nullable column
* add table not used yet
* add index
* add non-breaking function
* add feature-flagged table

Rollback:

* disable feature flag
* optionally drop unused objects later
* no immediate data restore needed unless bug

### 10.2 Data-Modifying Changes

Examples:

* backfill
* data normalization
* status migration
* ownership migration
* billing/invoice migration

Rollback:

* restore from backup if needed
* use rollback SQL if reversible
* audit data repair steps
* verify sample records
* verify role/RLS access
* verify affected dashboards

### 10.3 Destructive Changes

Examples:

* drop column
* delete table
* hard delete records
* rewrite payment data
* rewrite user role data

Rollback:

* restore DB backup
* or run explicit rollback SQL if safely possible
* verify restored data
* verify RLS
* verify public/private data
* verify affected flows
* mark deployment `ROLLED_BACK`
* create bug/incident entry

### 10.4 RLS Rollback

RLS rollback must never leave tables unsafe.

If new RLS policy breaks access:

1. Identify affected table/policy.
2. Restore previous safe RLS policy.
3. Do not disable RLS unless user explicitly approves emergency action.
4. If disabling RLS is unavoidable, block public access first.
5. Test allowed and denied cases.
6. Update `SECURITY_RLS_CHECKLIST.md`.
7. Update `MANUAL_VERIFICATION.md`.
8. Update `BUGS_AND_FIXES.md`.

---

## 11. Storage / Cloudflare R2 Rollback Rules

Storage rollback is required if:

* public media breaks
* private documents leak
* wrong bucket policy applied
* deleted media needs restore
* CDN caches unsafe/stale media
* signed URL behavior breaks
* media variants point to wrong files
* PDF files inaccessible
* banner ads show wrong images
* user profile images corrupt
* original backups missing

### 11.1 Public Media Rollback

Steps:

1. Identify affected media asset IDs.
2. Restore previous public file if backup exists.
3. Repoint DB URL to previous file if needed.
4. Purge CDN cache.
5. Verify public detail/search cards.
6. Verify mobile image layout.
7. Verify no broken image placeholder on critical pages.

### 11.2 Private Media Rollback

Steps:

1. Immediately block public access if leak suspected.
2. Rotate signed URL secret/key if needed.
3. Restore private bucket policy.
4. Revoke leaked signed URLs where possible.
5. Audit access logs.
6. Notify/admin-review if real privacy incident.
7. Verify staff permission access.
8. Verify public denied access.
9. Create security bug.

### 11.3 CDN Rollback

Steps:

1. Purge affected URLs.
2. Purge affected directories/tags if available.
3. Lower cache TTL temporarily if needed.
4. Verify old private content not cached.
5. Verify changed/deleted media not stale.
6. Verify performance impact.

---

## 12. Feature Flag Rollback Rules

Feature flags are preferred for risky/incomplete features.

Use feature flags for:

* new auth flow
* new role dashboard
* new admin module
* new billing/payment feature
* new provider integration
* new media processing
* new notification channel
* new ads/promotion module
* new SEO automation
* new performance/caching change
* new search/filter behavior
* new RLS-sensitive feature
* Turnstile
* maps API
* WhatsApp API
* analytics/error tracking
* cron jobs

### 12.1 Feature Flag Rollback Steps

1. Disable feature flag.
2. Verify public UI no longer exposes broken feature.
3. Verify backend blocks feature if flag disabled.
4. Verify database data remains safe.
5. Verify no broken links/dead buttons.
6. Verify setup-required/disabled state shown.
7. Update Feature Registry.
8. Update Changelog.
9. Update Manual Verification.
10. Update Bugs/Fixes if due to bug.

### 12.2 Feature Flag Entry Format

```md id="feature-flag"
## FEATURE-FLAG-YYYYMMDD-000 — Flag Name

### Flag
- Name:
- Purpose:
- Default:
- Environment:
- Owner:

### Enabled Scope
- Roles:
- Routes:
- Modules:
- Providers:

### Rollback
- Disable action:
- Expected behavior after disable:
- Data impact:
- User impact:

### Verification
- Enabled check:
- Disabled check:
- Backend enforcement check:
```

---

## 13. Provider Rollback Rules

Provider rollback is required when:

* OTP fails
* SMS/email/WhatsApp deliver incorrectly
* Razorpay payment/webhook fails
* Google Maps quota/key fails
* R2 upload fails
* CDN exposes wrong/stale data
* Turnstile blocks valid users
* analytics sends private data
* error tracking leaks private data
* cron job misfires
* media processing corrupts files

### 13.1 General Provider Rollback Steps

1. Switch provider status to `DISABLED_BY_FLAG`, `FALLBACK_ACTIVE`, `SETUP_REQUIRED` or previous provider mode.
2. Disable fake success.
3. Show safe user message.
4. Log safe admin error.
5. Stop retry storm.
6. Preserve user data.
7. Update `API_PROVIDER_STATUS.md`.
8. Update `BUGS_AND_FIXES.md`.
9. Update `CHANGELOG.md`.
10. Update `MANUAL_VERIFICATION.md`.

### 13.2 Payment Provider Rollback

If Razorpay/webhook has issue:

1. Stop new checkouts if payment safety affected.
2. Keep pending payments pending.
3. Do not activate plan from unverified payment.
4. Do not generate invoice from failed/pending payment.
5. Verify webhook signature handling.
6. Reconcile events manually if needed.
7. Audit manual activation if used.
8. Notify affected users safely if needed.
9. Update billing/payment docs.

### 13.3 OTP Provider Rollback

If OTP provider fails:

1. Disable OTP send or switch fallback provider if configured.
2. Do not fake OTP sent.
3. Show safe auth unavailable/setup-required message.
4. Preserve login security.
5. Apply rate limits.
6. Log provider failure safely.
7. Keep admin/staff login separate.

### 13.4 Storage Provider Rollback

If R2/CDN fails:

1. Disable upload if unsafe.
2. Do not fake upload success.
3. Preserve existing media.
4. Use safe placeholder if media unavailable.
5. Keep private documents private.
6. Purge CDN if stale/leaked.
7. Verify upload/download permissions.

---

## 14. Caching And Revalidation Rollback Rules

Caching bugs can expose stale or private data.

Rollback caching changes if:

* hidden contact appears due to cached response
* private dashboard data appears publicly
* old listing status remains public after reject/delete
* old price/contact remains after update
* city SEO page shows fake/stale count
* ad remains after expiry/pause
* payment/subscription status stale
* admin moderation status stale
* RLS/user-specific data cached globally

### 14.1 Revalidation Rules

Use targeted revalidation:

* property update → property detail page, relevant search/listing tags, city/locality SEO pages
* project update → project detail page, project search/listing tags, city/locality SEO pages
* requirement update → requirement dashboard/feed tags
* lead update → related dashboard/notification tags
* payment success → billing/subscription dashboard tags
* ad approval/pause → homepage ad tags, city ad tags
* CMS/legal update → exact page path/tag
* SEO metadata update → exact SEO page path/tag

Do not revalidate whole site unnecessarily.

### 14.2 Cache Rollback Steps

1. Disable risky cache/tag if needed.
2. Revalidate affected paths/tags.
3. Purge CDN if public stale data.
4. Verify public/private separation.
5. Verify updated listing status.
6. Verify search result correctness.
7. Verify performance still acceptable.
8. Update `PERFORMANCE_CHECKLIST.md`.

---

## 15. Deployment Gates

Every implementation phase must pass gates before deployment.

### 15.1 Development Gate

Required before moving from local/dev to staging:

* relevant docs read
* plan made
* changed files known
* SQL/migration files created where needed
* lint run or reason documented
* typecheck run or reason documented
* build run or reason documented
* relevant tests run or reason documented
* manual verification updated
* bugs tracked
* Feature Registry updated
* Changelog updated
* brain.md updated

### 15.2 Staging Gate

Required before production:

* staging deployment succeeds
* migrations apply on staging
* RLS allowed/denied tests pass
* role routes tested
* public/private data tested
* provider setup-required/fallback tested
* payment test/sandbox behavior tested if in scope
* media upload tested if in scope
* responsive quick check done
* smoke test done
* rollback path reviewed
* no S0/S1 open bugs

### 15.3 Production Gate

Required before production:

* user/Super Admin approval
* backup completed and verified
* rollback plan ready
* production env variables configured safely
* `.env.example` updated
* dev/mock/test providers disabled
* real providers tested or explicitly setup-required/disabled
* Razorpay live/sandbox status intentional
* RLS final pass
* contact privacy final pass
* admin/staff noindex/access final pass
* payment safety final pass if billing launched
* legal pages and consent checked
* production build passed
* smoke test plan ready

---

## 16. Smoke Test Checklist

Smoke test must run after deployment and rollback.

### 16.1 Public Smoke Test

| Check                                   | Required |
| --------------------------------------- | -------- |
| Homepage loads                          | Yes      |
| Header loads correctly                  | Yes      |
| Brand does not wrap                     | Yes      |
| City selector visible                   | Yes      |
| Search button works                     | Yes      |
| Search page loads                       | Yes      |
| Public detail page loads if data exists | Yes      |
| Public footer legal links visible       | Yes      |
| Login/register opens                    | Yes      |
| Guest protected action shows auth popup | Yes      |
| No horizontal scroll mobile quick check | Yes      |
| No critical console/server error        | Yes      |

### 16.2 Auth Smoke Test

| Check                                               | Required |
| --------------------------------------------------- | -------- |
| Public login/register route/popup opens             | Yes      |
| Admin/staff login route separate                    | Yes      |
| Public admin create account absent                  | Yes      |
| Logged-out dashboard blocked                        | Yes      |
| Logged-in dashboard route check if test user exists | Yes      |
| Logout works if logged in                           | Yes      |

### 16.3 Role Smoke Test

| Role        | Required Check                          |
| ----------- | --------------------------------------- |
| Guest       | public-only access                      |
| Owner       | owner dashboard access if implemented   |
| Broker      | broker dashboard access if implemented  |
| Builder     | builder dashboard access if implemented |
| Super Admin | admin access if implemented             |
| Staff       | scoped access if implemented            |
| Wrong role  | denied access where relevant            |

### 16.4 Security Smoke Test

| Check                             | Required           |
| --------------------------------- | ------------------ |
| Service role not in client bundle | Yes                |
| Hidden contact not shown to guest | Yes                |
| Private documents not public      | Yes if docs exist  |
| Admin routes noindex/protected    | Yes                |
| Wrong-owner access denied         | Yes where relevant |
| RLS public-safe view check        | Yes where relevant |
| User-facing errors safe           | Yes                |

### 16.5 Payment Smoke Test

If billing/payment in scope:

| Check                                                | Required |
| ---------------------------------------------------- | -------- |
| Checkout disabled/setup-required if Razorpay missing | Yes      |
| Fake payment success blocked                         | Yes      |
| Failed payment does not activate plan                | Yes      |
| Pending payment does not activate plan               | Yes      |
| Invoice only after verified success                  | Yes      |
| Test/live mode label correct                         | Yes      |

### 16.6 Provider Smoke Test

| Provider       | Check                                 |
| -------------- | ------------------------------------- |
| OTP            | real send or setup-required           |
| Email          | real send or setup-required           |
| SMS            | real send or setup-required           |
| WhatsApp       | free/API real or setup-required       |
| Maps           | real map or text fallback             |
| R2/CDN         | real upload/media or setup-required   |
| Analytics      | active only with consent/safe config  |
| Error tracking | redacted/safe or setup-required       |
| Cron           | protected/scheduled or setup-required |

---

## 17. Production Launch Freeze Rules

Before launch:

1. Stop new feature additions unless approved.
2. Only allow bug fixes, security fixes, content/legal fixes, provider setup and launch blockers.
3. Freeze database schema except critical fixes.
4. Freeze UI redesign except critical responsive/accessibility fixes.
5. Freeze plan/payment pricing changes unless approved.
6. Freeze provider changes unless needed for launch.
7. Run final verification.
8. Run backup.
9. Confirm rollback.
10. Get Super Admin/user signoff.

During freeze, any new requirement goes to:

* `DEFERRED_TRACKED`
* `POST_LAUNCH`
* or user-approved emergency scope

No silent skip.

---

## 18. Production Launch Checklist

Production launch cannot pass unless this checklist is completed.

### 18.1 Documentation

* [ ] `CLAUDE.md` updated
* [ ] `brain.md` updated with final resume guide
* [ ] `FEATURE_REGISTRY.md` updated
* [ ] `CHANGELOG.md` updated
* [ ] `BUGS_AND_FIXES.md` has no launch-blocking unresolved bugs
* [ ] `MANUAL_VERIFICATION.md` final PASS/PARTIAL/BLOCKED documented
* [ ] `API_PROVIDER_STATUS.md` updated
* [ ] `DEPLOYMENT_ROLLBACK.md` updated
* [ ] `SECURITY_RLS_CHECKLIST.md` updated
* [ ] `PERFORMANCE_CHECKLIST.md` updated
* [ ] relevant detailed docs updated

### 18.2 Code

* [ ] build passes
* [ ] lint passes
* [ ] typecheck passes
* [ ] critical tests pass
* [ ] E2E critical flows pass or blocked reason documented
* [ ] no dead primary buttons
* [ ] no broken critical routes
* [ ] no fake UI/data/payment/verification
* [ ] no secrets in code
* [ ] no service role in client
* [ ] no raw errors

### 18.3 Database

* [ ] migrations applied
* [ ] rollback notes exist
* [ ] backup complete
* [ ] RLS enabled
* [ ] RLS allowed/denied tests passed
* [ ] public-safe views safe
* [ ] indexes exist for expensive queries
* [ ] no unbounded critical reads
* [ ] audit logs working
* [ ] soft delete rules implemented where needed
* [ ] seed/demo data hidden/removed from production public views

### 18.4 Auth / Roles

* [ ] public login/register works or provider setup-required documented
* [ ] unregistered mobile register prompt works
* [ ] role selector works
* [ ] logged-in user no login/register buttons
* [ ] owner dashboard access works
* [ ] broker dashboard access works
* [ ] builder dashboard access works
* [ ] admin/staff login separate
* [ ] no public admin/staff create account
* [ ] direct URL bypass blocked
* [ ] staff permissions enforced

### 18.5 Security / Privacy

* [ ] hidden contact not leaked
* [ ] private documents protected
* [ ] service role safe
* [ ] input validation exists
* [ ] rate limits exist where needed
* [ ] provider secrets safe
* [ ] payment webhook signatures verified if payment live
* [ ] logs redacted
* [ ] legal consent exists
* [ ] report/fraud system safe where launched
* [ ] admin routes noindex
* [ ] sitemap excludes admin/private/thin pages

### 18.6 Providers

* [ ] Supabase live configured
* [ ] OTP live or setup-required
* [ ] Email live or setup-required
* [ ] SMS live or setup-required
* [ ] WhatsApp free/API live or setup-required
* [ ] Razorpay live/sandbox status intentional
* [ ] Razorpay webhook verified if live payment
* [ ] Google Maps live or fallback
* [ ] Cloudflare R2 live or setup-required
* [ ] Cloudflare CDN live or fallback
* [ ] Turnstile disabled/enabled intentionally
* [ ] Analytics consent-safe or disabled
* [ ] Error tracking redacted or disabled
* [ ] Cron jobs protected or setup-required
* [ ] no provider fake success

### 18.7 UI / Responsive

* [ ] 320px check
* [ ] 360px check
* [ ] 390px check
* [ ] 430px check
* [ ] 768px check
* [ ] 1024px check
* [ ] 1366px check
* [ ] no horizontal scroll
* [ ] no overlap
* [ ] brand no-wrap
* [ ] mobile CTA not covering content
* [ ] modals/drawers/bottom sheets work
* [ ] tables become cards
* [ ] loading/empty/error states exist

### 18.8 SEO / Legal

* [ ] title/meta/canonical safe
* [ ] sitemap safe
* [ ] robots safe
* [ ] no fake city/listing counts
* [ ] empty/thin pages noindex/hidden
* [ ] legal pages exist
* [ ] Terms/Privacy checkbox exists
* [ ] payment/refund policy visible
* [ ] RERA disclaimers where needed
* [ ] platform marketplace disclaimer visible
* [ ] legal text reviewed or marked `NEEDS_REVIEW`

### 18.9 Backup / Rollback

* [ ] code rollback ready
* [ ] DB backup ready
* [ ] storage backup ready if needed
* [ ] feature flags ready
* [ ] provider fallback ready
* [ ] rollback owner known
* [ ] incident contact known
* [ ] monitoring enabled/setup-required
* [ ] smoke test plan ready

---

## 19. Hotfix Rules

Hotfix means urgent fix for production issue.

Hotfix allowed for:

* security leak
* contact privacy leak
* payment failure
* production crash
* RLS failure
* admin/staff access bug
* provider outage fallback bug
* broken login
* broken checkout
* broken listing detail/search
* legal/privacy emergency fix
* critical mobile layout issue blocking users

Hotfix still requires:

* exact bug ID
* minimal scope
* changed files list
* SQL/migration list or None
* backup if DB/storage/config affected
* rollback plan
* smoke test
* docs update after fix
* no fake PASS

### Hotfix Entry Format

```md id="hotfix-entry"
## HOTFIX-YYYYMMDD-000 — Hotfix Title

### Related Bug / Incident
- ID:

### Severity
S0_CRITICAL / S1_HIGH

### Scope
- What is fixed:
- What is not changed:

### Changed Files
-

### SQL / Migration Files
-

### Backup
-

### Tests / Verification
-

### Rollback
-

### Final Status
PASS / PARTIAL / BLOCKED / FAIL
```

---

## 20. Incident Handling Rules

Incident means production problem affecting users, data, payment, privacy, security, providers or availability.

### 20.1 Incident Severity

| Severity      | Meaning                                            |
| ------------- | -------------------------------------------------- |
| `INCIDENT-S0` | Security/privacy/payment/data leak/production down |
| `INCIDENT-S1` | Major user flow broken                             |
| `INCIDENT-S2` | Important degraded feature                         |
| `INCIDENT-S3` | Minor issue                                        |
| `INCIDENT-S4` | Cosmetic/low-risk issue                            |

### 20.2 Incident Entry Format

```md id="incident-entry"
## INCIDENT-YYYYMMDD-000 — Incident Title

### Severity
INCIDENT-S0 / INCIDENT-S1 / INCIDENT-S2 / INCIDENT-S3 / INCIDENT-S4

### Status
OPEN / INVESTIGATING / MITIGATED / RESOLVED / ROLLED_BACK / MONITORING

### Timeline
- Detected:
- Acknowledged:
- Mitigated:
- Resolved:

### Impact
- Users affected:
- Roles affected:
- Routes affected:
- Data affected:
- Payment affected:
- Provider affected:
- Security/privacy affected:

### Root Cause
- Known/Unknown:
- Details:

### Immediate Action
-

### Rollback / Mitigation
-

### Verification
-

### Follow-Up
-

### Docs Updated
-
```

### 20.3 Incident Response Steps

1. Confirm issue.
2. Protect user data first.
3. Disable risky feature if needed.
4. Stop payment/provider damage if needed.
5. Rollback if faster/safer than fix.
6. Create bug/incident entry.
7. Communicate safe status if public impact.
8. Verify mitigation.
9. Fix root cause.
10. Retest.
11. Update docs.
12. Post-incident review.

---

## 21. Seed / Demo / Test Data Deployment Rules

Development seed/demo/test data is allowed only for testing.

Rules:

1. Do not delete development seed data accidentally.
2. Flag seed/demo data clearly.
3. Production must not show fake/demo public data.
4. Production must not show fake listing count.
5. Production must not show fake leads/views/analytics.
6. Production must not show fake verified users.
7. Production must not show fake payments.
8. Production must not show fake banner ads.
9. Demo accounts must be hidden/disabled in production.
10. If seed data is used in staging, mark environment clearly.
11. Before production launch, run demo data cleanup/hide checklist.
12. Feature Registry must track seed/demo data status.

### Seed Data Entry Format

```md id="seed-entry"
## SEED-DATA-YYYYMMDD-000 — Seed Data Batch

### Environment
LOCAL / DEVELOPMENT / STAGING / PRODUCTION

### Purpose
-

### Data Types
- users:
- properties:
- projects:
- requirements:
- leads:
- payments:
- ads:
- CMS pages:

### Production Visibility
- Public visible: Yes/No
- Cleanup required: Yes/No
- Cleanup plan:

### Rollback
-
```

---

## 22. Maintenance Mode Rules

Maintenance mode should be available for high-risk production work.

Maintenance mode may be used for:

* destructive DB migration
* major RLS rewrite
* payment provider migration
* storage bucket policy migration
* auth provider change
* emergency security fix
* data repair
* incident mitigation

Maintenance mode requirements:

* public-friendly message
* estimated status without false promise
* admin access if safe
* payment/checkout disabled if affected
* no raw error
* SEO-safe status where possible
* monitoring active
* rollback ready

Maintenance mode must not expose internal details.

---

## 23. Versioning Rules

Every production deployment should have version/build tracking.

Recommended format:

```txt id="version-format"
MGP-YYYY.MM.DD.N
```

Example:

```txt id="version-example"
MGP-2026.06.29.1
```

Track:

* version
* environment
* commit
* migration batch
* provider mode
* feature flags
* deployment date
* rollback version

Version entry:

```md id="version-entry"
## VERSION — MGP-YYYY.MM.DD.N

### Environment
-

### Commit
-

### Migration Batch
-

### Feature Flags
-

### Provider Modes
-

### Deployment Status
-

### Rollback Version
-
```

---

## 24. Deployment Documentation Update Rules

Every deployment must update:

* `DEPLOYMENT_ROLLBACK.md`
* `CHANGELOG.md`
* `MANUAL_VERIFICATION.md`
* `FEATURE_REGISTRY.md`
* `brain.md`

Also update when relevant:

* `BUGS_AND_FIXES.md`
* `API_PROVIDER_STATUS.md`
* `SECURITY_RLS_CHECKLIST.md`
* `PERFORMANCE_CHECKLIST.md`
* detailed docs
* prompt verification file result

If DB changed:

* migration files
* rollback notes
* `SECURITY_RLS_CHECKLIST.md` if RLS/security affected
* `PERFORMANCE_CHECKLIST.md` if indexes/query affected

If provider changed:

* `API_PROVIDER_STATUS.md`
* `.env.example`
* provider health/status entries

If UI changed:

* responsive verification notes

If payment changed:

* payment webhook/invoice verification notes

---

## 25. Deployment Final Response Rule

After deployment-related work, Claude final response must include:

```md id="deployment-final-response"
## Deployment / Rollback Result
PASS / PARTIAL / BLOCKED / FAIL / ROLLED_BACK

## Environment
- LOCAL / DEVELOPMENT / STAGING / PRODUCTION

## Changed Files
- path/to/file

## SQL / Migration Files
- path/to/migration.sql
- None

## Backup
- Code:
- Database:
- Storage:
- Config:

## Tests Run
- lint:
- typecheck:
- build:
- tests:
- smoke test:

## Verification
- Manual verification result:
- RLS/security:
- Provider status:
- Payment safety:
- Responsive:

## Rollback
- Rollback ready: Yes/No
- Rollback path:

## Docs Updated
- DEPLOYMENT_ROLLBACK.md
- CHANGELOG.md
- MANUAL_VERIFICATION.md
- FEATURE_REGISTRY.md
- brain.md
- others:

## Pending Issues
- issue or None

## Next Phase
-
```

If any required check was not run, state exact reason and do not mark `PASS`.

---

## 26. Current Deployment Status

No actual website implementation or deployment has started yet.

| Area                   | Status                |
| ---------------------- | --------------------- |
| Code deployment        | `NOT_STARTED`         |
| Staging environment    | `NOT_STARTED`         |
| Production environment | `NOT_STARTED`         |
| Database migrations    | `NOT_STARTED`         |
| Database backup        | `NOT_STARTED`         |
| Storage backup         | `NOT_STARTED`         |
| Provider config        | `SETUP_REQUIRED`      |
| Feature flags          | `NOT_STARTED`         |
| RLS verification       | `NOT_STARTED`         |
| Manual verification    | `NOT_STARTED`         |
| Production launch      | `NOT_STARTED`         |
| Rollback plan          | `DOCUMENTED_BASELINE` |
| Incident handling      | `DOCUMENTED_BASELINE` |

---

## 27. Current Open Deployment Risks

## DEPLOY-RISK-20260629-001 — Website Implementation Not Started

### Status

`NOT_STARTED`

### Risk

* No code deployment can happen yet.
* Deployment rules are documentation-only baseline.

### Required Action

* Finish documentation pack.
* Generate prompt pack.
* Run implementation phases.
* Deploy only after verification.

### Related Docs

* `brain.md`
* `FEATURE_REGISTRY.md`
* `CHANGELOG.md`
* `MANUAL_VERIFICATION.md`

---

## DEPLOY-RISK-20260629-002 — Providers Not Configured

### Status

`SETUP_REQUIRED`

### Risk

* OTP/payment/email/SMS/WhatsApp/maps/storage/CDN cannot be production-active.
* Provider-backed features must show setup-required/fallback.

### Required Action

* Configure providers in relevant phases.
* Update `.env.example`.
* Verify provider success/failure.
* Update `API_PROVIDER_STATUS.md`.

---

## DEPLOY-RISK-20260629-003 — SQL/Migration System Not Created Yet

### Status

`NOT_STARTED`

### Risk

* Future DB changes must create migration files.
* RLS/security changes must be migration-controlled.

### Required Action

* Create migration folder/files in implementation phases.
* Add rollback notes to each migration.
* Test migration in staging before production.

---

## DEPLOY-RISK-20260629-004 — Production Backup Not Tested Yet

### Status

`NOT_STARTED`

### Risk

* Production launch cannot happen without backup/restore confidence.

### Required Action

* Define backup method during deployment phase.
* Test restore process where possible.
* Record backup reference safely.

---

## DEPLOY-RISK-20260629-005 — RLS Final Pass Not Done

### Status

`NOT_STARTED`

### Risk

* Production cannot launch without RLS final pass.

### Required Action

* Implement RLS.
* Run allowed/denied access tests.
* Update `SECURITY_RLS_CHECKLIST.md`.

---

## DEPLOY-RISK-20260629-006 — Manual Verification Not Fully Run

### Status

`NOT_STARTED`

### Risk

* No phase can be considered production-ready.

### Required Action

* Use phase manual verification prompts.
* Update `MANUAL_VERIFICATION.md`.
* Fix errors first, then mark PASS.

---

## 28. Current Documentation Generation Progress

| File No. | File                                                      | Status  |
| -------: | --------------------------------------------------------- | ------- |
|        1 | `CLAUDE.md`                                               | Created |
|        2 | `brain.md`                                                | Created |
|        3 | `FEATURE_REGISTRY.md`                                     | Created |
|        4 | `CHANGELOG.md`                                            | Created |
|        5 | `BUGS_AND_FIXES.md`                                       | Created |
|        6 | `MANUAL_VERIFICATION.md`                                  | Created |
|        7 | `API_PROVIDER_STATUS.md`                                  | Created |
|        8 | `DEPLOYMENT_ROLLBACK.md`                                  | Created |
|        9 | `SECURITY_RLS_CHECKLIST.md`                               | Pending |
|       10 | `PERFORMANCE_CHECKLIST.md`                                | Pending |
|       11 | `docs/01_PROJECT_MASTER_AND_SCOPE.md`                     | Pending |
|       12 | `docs/02_CLAUDE_WORKFLOW_AND_TOKEN_LIGHT_RULES.md`        | Pending |
|       13 | `docs/03_ARCHITECTURE_TECH_STACK_DATABASE_RLS.md`         | Pending |
|       14 | `docs/04_AUTH_LOGIN_REGISTER_ROLES_PERMISSIONS.md`        | Pending |
|       15 | `docs/05_PUBLIC_ROLES_HOME_PROFILE_DASHBOARD.md`          | Pending |
|       16 | `docs/06_PROPERTY_PROJECT_REQUIREMENT_FULL_MATRIX.md`     | Pending |
|       17 | `docs/07_LEADS_CRM_PROPOSALS_SITE_VISITS_MESSAGES.md`     | Pending |
|       18 | `docs/08_ADMIN_SUPER_ADMIN_STAFF_MODULES.md`              | Pending |
|       19 | `docs/09_BILLING_SUBSCRIPTION_PAYMENT_GST_TRIAL.md`       | Pending |
|       20 | `docs/10_ADS_PROMOTION_NOTIFICATION_PROVIDER_MODES.md`    | Pending |
|       21 | `docs/11_LOCATION_SEARCH_SEO_CMS_BLOG_LEGAL.md`           | Pending |
|       22 | `docs/12_MEDIA_UPLOAD_STORAGE_IMAGE_VIDEO_PDF.md`         | Pending |
|       23 | `docs/13_UI_UX_DESIGN_SYSTEM_RESPONSIVE_RULES.md`         | Pending |
|       24 | `docs/14_SECURITY_PRIVACY_CONSENT_FRAUD_LEGAL.md`         | Pending |
|       25 | `docs/15_PERFORMANCE_DEPLOYMENT_ROLLBACK_QA.md`           | Pending |
|       26 | `docs/16_ADVANCED_FEATURES_PWA_LOCALIZATION_ANALYTICS.md` | Pending |

---

## 29. Resume Guide For Future Claude

Before doing deployment/rollback work, Claude must read:

1. `CLAUDE.md`
2. `brain.md`
3. `FEATURE_REGISTRY.md`
4. `CHANGELOG.md`
5. `BUGS_AND_FIXES.md`
6. `MANUAL_VERIFICATION.md`
7. `API_PROVIDER_STATUS.md`
8. `DEPLOYMENT_ROLLBACK.md`
9. `SECURITY_RLS_CHECKLIST.md`
10. `PERFORMANCE_CHECKLIST.md`
11. relevant detailed docs
12. latest SQL/migration files

Claude must not depend on chat memory.

Claude must inspect current code, routes, DB schema, RLS policies and provider config before making deployment changes.

---

## 30. Final Rule

Deployment is not complete until:

* code changes are known
* SQL/migration impact is known
* backup is done where required
* rollback is ready
* tests are run or honestly blocked
* manual verification is updated
* RLS/security is checked where relevant
* provider states are real or setup-required
* payment safety is verified where relevant
* docs are updated
* pending issues are honestly listed

Rollback is not complete until:

* system is safe again
* data/privacy/payment state is safe
* smoke test passes
* docs are updated
* incident/bug is tracked
* monitoring continues where needed

Never deploy blindly.

Never rollback blindly.

Never fake production PASS.
