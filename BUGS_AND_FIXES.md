# BUGS_AND_FIXES.md

# My Gujarat Property — Bugs, Fixes, Workarounds And Retest Log

This file tracks every known bug, issue, failed verification, workaround, fix, retest and pending defect for **My Gujarat Property**.

Claude must update this file after every bug discovery, every failed test, every failed manual verification, every temporary workaround, every fix and every retest.

No bug should be hidden.

No fix should be marked complete without verification.

No fake PASS is allowed.

---

## 1. Purpose

This file exists to track:

* known bugs
* UI issues
* responsive issues
* text wrapping issues
* dashboard issues
* admin issues
* auth issues
* RLS/security issues
* role/permission issues
* contact privacy issues
* payment issues
* provider/API issues
* media/upload issues
* SEO/CMS/legal issues
* performance issues
* deployment issues
* migration issues
* data issues
* manual verification failures
* production readiness blockers
* temporary workarounds
* fix attempts
* retest results
* removal condition for workarounds
* exact files changed during fixes
* exact SQL/migration files changed during fixes

This file helps two Claude accounts continue the project without losing bug/fix context.

---

## 2. Mandatory Update Rule

Claude must update `BUGS_AND_FIXES.md` whenever:

1. A bug is found.
2. A manual verification fails.
3. A responsive issue is found.
4. Text wrapping breaks.
5. Horizontal scroll appears.
6. UI overlap appears.
7. A dead button is found.
8. A broken link is found.
9. A route crashes.
10. A route shows raw error.
11. Unauthorized direct URL access works.
12. Hidden contact number leaks.
13. Private data leaks.
14. A role can access the wrong module.
15. Admin/staff access is wrong.
16. RLS allows wrong user access.
17. RLS blocks allowed access.
18. A payment state is wrong.
19. A fake payment success appears.
20. A verified badge appears incorrectly.
21. A provider success is faked.
22. Upload validation fails.
23. Private document access is unsafe.
24. SEO metadata is wrong.
25. Thin/fake SEO page appears.
26. Loading/empty/error state is missing.
27. Build, lint, typecheck or test fails.
28. A temporary workaround is added.
29. A workaround is removed.
30. A fix is implemented.
31. A fix is retested.
32. A bug is moved to blocked/setup-required/deferred.
33. A bug affects production readiness.
34. A regression is found.
35. A rollback is required due to a bug.
36. User reports an issue.
37. Staff/admin reports an issue.
38. Monitoring detects an issue.
39. Provider/API failure affects user flow.
40. A conflict between docs/code causes incorrect behavior.

---

## 3. Absolute Bug Handling Rules

Claude must follow these rules:

1. Do not hide bugs.
2. Do not mark a bug fixed unless fix is implemented.
3. Do not mark retest PASS unless retest actually passed.
4. Do not continue next phase if current phase has blocking bugs unless user explicitly approves.
5. Do not write vague entries like “fixed issue”.
6. Every fix must mention exact changed files.
7. Every DB/RLS fix must mention exact SQL/migration files.
8. Every security fix must include allowed and denied access retest.
9. Every responsive fix must include device/screen-size retest.
10. Every payment fix must include failed/pending/success state retest.
11. Every provider/API fix must include real provider test or setup-required reason.
12. Every temporary workaround must have removal condition.
13. Every workaround must be documented in `brain.md`.
14. Every completed fix must update `CHANGELOG.md`.
15. Every affected feature status must update `FEATURE_REGISTRY.md`.
16. Manual verification must be updated in `MANUAL_VERIFICATION.md`.
17. If test cannot be run, mark `PARTIAL` or `BLOCKED` with exact reason.
18. If bug is security-sensitive, do not expose secrets/logs/private data while reporting.
19. Do not paste long logs; only relevant 20–30 lines if needed.
20. Fix errors first, then mark PASS.

---

## 4. Bug Status Values

Use only these values:

| Status                 | Meaning                                                                 |
| ---------------------- | ----------------------------------------------------------------------- |
| `OPEN`                 | Bug is known but not fixed                                              |
| `IN_PROGRESS`          | Fix is currently being worked on                                        |
| `FIXED_PENDING_RETEST` | Fix implemented but retest not completed                                |
| `RETEST_IN_PROGRESS`   | Retest is being performed                                               |
| `RESOLVED`             | Fix retested and passed                                                 |
| `PARTIAL`              | Partly fixed or partly retested                                         |
| `BLOCKED`              | Cannot fix/retest due to dependency, missing info, provider or decision |
| `SETUP_REQUIRED`       | Requires real API/provider/env/config setup                             |
| `DEFERRED_TRACKED`     | Deferred but tracked; not skipped                                       |
| `WONT_FIX_APPROVED`    | User explicitly approved not fixing                                     |
| `DUPLICATE`            | Same as another tracked bug                                             |
| `REGRESSION`           | Bug reappeared after previously passing                                 |
| `ROLLED_BACK`          | Change causing bug was rolled back                                      |
| `NEEDS_REVIEW`         | Needs design/security/legal/human review                                |
| `MONITORING`           | Fix passed but needs continued observation                              |

---

## 5. Severity Values

Use only these severity values:

| Severity      | Meaning                                                           |
| ------------- | ----------------------------------------------------------------- |
| `S0_CRITICAL` | Security/data/payment/privacy/production-down issue               |
| `S1_HIGH`     | Major broken flow, blocked role, payment/auth/listing/admin issue |
| `S2_MEDIUM`   | Important feature partially broken but workaround exists          |
| `S3_LOW`      | Minor UI/content/state issue                                      |
| `S4_POLISH`   | Visual polish or improvement only                                 |

---

## 6. Priority Values

Use only these priority values:

| Priority               | Meaning                           |
| ---------------------- | --------------------------------- |
| `P0_FIX_NOW`           | Must fix before continuing        |
| `P1_FIX_THIS_PHASE`    | Must fix before phase PASS        |
| `P2_FIX_BEFORE_LAUNCH` | Must fix before production launch |
| `P3_FIX_SOON`          | Should fix soon                   |
| `P4_BACKLOG`           | Backlog/deferred                  |

---

## 7. Verification Values

Use only these values:

| Verification             | Meaning                               |
| ------------------------ | ------------------------------------- |
| `PASS`                   | Retest passed completely              |
| `PARTIAL`                | Retest partially passed               |
| `FAIL`                   | Retest failed                         |
| `BLOCKED`                | Retest could not run                  |
| `NOT_RUN`                | Retest not run yet                    |
| `NEEDS_MANUAL_CHECK`     | Human/manual check required           |
| `NEEDS_SECURITY_CHECK`   | RLS/security/privacy retest required  |
| `NEEDS_RESPONSIVE_CHECK` | Mobile/tablet/desktop retest required |
| `NEEDS_PROVIDER_CHECK`   | Real provider/API retest required     |
| `NEEDS_LEGAL_REVIEW`     | Legal/human review required           |

---

## 8. Bug Categories

Use these category labels.

### Documentation And Workflow

* `DOCS`
* `PROMPT`
* `WORKFLOW`
* `MEMORY`
* `REGISTRY`
* `CHANGELOG`
* `MANUAL_VERIFICATION`

### Core App

* `CORE`
* `ROUTING`
* `CONFIG`
* `ENV`
* `FEATURE_FLAG`
* `SERVER_ACTION`
* `API_ROUTE`

### Auth And Roles

* `AUTH`
* `OTP`
* `REGISTER`
* `LOGIN`
* `SESSION`
* `RBAC`
* `PERMISSION`
* `ADMIN_LOGIN`
* `STAFF_ACCESS`
* `ROLE_CHANGE`

### Public Website And UI

* `PUBLIC_UI`
* `HOMEPAGE`
* `HEADER`
* `FOOTER`
* `SEARCH`
* `DETAIL_PAGE`
* `PROFILE_PAGE`
* `MOBILE_UI`
* `RESPONSIVE`
* `TEXT_WRAP`
* `HORIZONTAL_SCROLL`
* `OVERLAP`
* `ACCESSIBILITY`

### Dashboard And Admin

* `OWNER_DASHBOARD`
* `BROKER_DASHBOARD`
* `BUILDER_DASHBOARD`
* `ADMIN`
* `SUPER_ADMIN`
* `STAFF`
* `ADMIN_QUEUE`
* `ADMIN_TABLE`
* `ADMIN_DETAIL`

### Listing Modules

* `PROPERTY`
* `PROJECT`
* `REQUIREMENT`
* `PROPOSAL`
* `POSTING_FORM`
* `APPROVAL`
* `VERIFICATION`
* `RERA`

### CRM And Communication

* `LEADS`
* `INQUIRY`
* `CONTACT_REVEAL`
* `SITE_VISIT`
* `MESSAGING`
* `NOTIFICATION`
* `EMAIL`
* `SMS`
* `WHATSAPP`

### Billing And Payment

* `BILLING`
* `SUBSCRIPTION`
* `PLAN_LIMIT`
* `TRIAL`
* `RAZORPAY`
* `PAYMENT`
* `WEBHOOK`
* `INVOICE`
* `GST`
* `REFUND`
* `CREDIT`
* `BOOST`

### Media And Providers

* `MEDIA`
* `UPLOAD`
* `IMAGE`
* `VIDEO`
* `PDF`
* `PRIVATE_DOCUMENT`
* `CLOUDFLARE_R2`
* `CDN`
* `MAPS`
* `PROVIDER`

### SEO, CMS, Legal And Privacy

* `SEO`
* `CMS`
* `BLOG`
* `LEGAL`
* `PRIVACY`
* `CONSENT`
* `COOKIE`
* `SITEMAP`
* `NOINDEX`
* `SCHEMA`

### Security, Data And Performance

* `SECURITY`
* `RLS`
* `CONTACT_PRIVACY`
* `PRIVATE_DATA`
* `RATE_LIMIT`
* `AUDIT`
* `SOFT_DELETE`
* `MIGRATION`
* `DATABASE`
* `PERFORMANCE`
* `CACHE`
* `BACKGROUND_JOB`
* `DEPLOYMENT`
* `ROLLBACK`

---

## 9. Required Bug Entry Format

Every bug must be added using this exact structure:

```md id="1irpsv"
## BUG-YYYYMMDD-000 — Short Bug Title

### Status
OPEN / IN_PROGRESS / FIXED_PENDING_RETEST / RETEST_IN_PROGRESS / RESOLVED / PARTIAL / BLOCKED / SETUP_REQUIRED / DEFERRED_TRACKED / WONT_FIX_APPROVED / DUPLICATE / REGRESSION / ROLLED_BACK / NEEDS_REVIEW / MONITORING

### Severity
S0_CRITICAL / S1_HIGH / S2_MEDIUM / S3_LOW / S4_POLISH

### Priority
P0_FIX_NOW / P1_FIX_THIS_PHASE / P2_FIX_BEFORE_LAUNCH / P3_FIX_SOON / P4_BACKLOG

### Category
- CATEGORY

### Found In
- Phase:
- Prompt file:
- Verification prompt:
- Environment:
- Route/page:
- Role/login state:
- Device/screen size:
- Browser:
- Provider mode:
- Related feature IDs:

### Summary
- What is wrong:
- Expected behavior:
- Actual behavior:
- User impact:
- Security/privacy impact:
- Payment/provider impact:
- SEO/legal impact:
- Performance impact:

### Reproduction Steps
1.
2.
3.

### Evidence
- Screenshot:
- Video:
- Log excerpt:
- Error message:
- Affected file:
- If no evidence, explain why:

### Root Cause
- Known / Unknown
- Details:

### Fix Plan
- Files to inspect:
- Files likely to change:
- SQL/migration needed: Yes/No
- RLS/security needed: Yes/No
- Provider/API setup needed: Yes/No
- Docs to update:

### Fix Implementation
- Changed files:
- SQL/migration files:
- RLS policies changed:
- Provider/env changes:
- UI changes:
- Notes:

### Retest Steps
1.
2.
3.

### Retest Result
PASS / PARTIAL / FAIL / BLOCKED / NOT_RUN / NEEDS_MANUAL_CHECK / NEEDS_SECURITY_CHECK / NEEDS_RESPONSIVE_CHECK / NEEDS_PROVIDER_CHECK / NEEDS_LEGAL_REVIEW

### Retest Notes
- Date:
- Tested by:
- Result details:
- Remaining issue:

### Docs Updated
- `BUGS_AND_FIXES.md`
- `CHANGELOG.md`
- `FEATURE_REGISTRY.md`
- `MANUAL_VERIFICATION.md`
- `brain.md`
- Other:

### Rollback / Workaround
- Workaround exists: Yes/No
- Workaround details:
- Removal condition:
- Rollback needed: Yes/No
- Rollback path:

### Final Resolution
- Resolved date:
- Final status:
- Final verification:
```

---

## 10. Short Bug Entry Format

For small documentation-only or low-risk issues, this shorter format is allowed:

```md id="gp7lvn"
## BUG-YYYYMMDD-000 — Short Bug Title

### Status
OPEN / RESOLVED / BLOCKED / PARTIAL

### Severity
S3_LOW / S4_POLISH

### Category
- CATEGORY

### Summary
- Issue:
- Expected:
- Actual:

### Fix
- Changed files:
- Notes:

### Retest
- Result:
- Notes:

### Docs Updated
- Files:
```

---

## 11. Workaround Entry Format

Every temporary workaround must be documented here and in `brain.md`.

```md id="5r850m"
## WORKAROUND-YYYYMMDD-000 — Short Workaround Title

### Status
ACTIVE / REMOVED / REPLACED / BLOCKED

### Related Bug
- BUG ID:

### Reason
- Why workaround was needed:

### Temporary Behavior
- What the workaround does:

### Risk
- Security risk:
- Privacy risk:
- Payment risk:
- UX risk:
- Performance risk:
- Data risk:

### Removal Condition
- Exact condition when this workaround must be removed:

### Files Changed
- `path/to/file`

### SQL / Migration Files
- `path/to/migration.sql`
- or None

### Docs Updated
- `brain.md`
- `BUGS_AND_FIXES.md`
- `CHANGELOG.md`
- `FEATURE_REGISTRY.md`
- `MANUAL_VERIFICATION.md`

### Retest
- Result:
- Notes:
```

Allowed workaround statuses:

| Status         | Meaning                             |
| -------------- | ----------------------------------- |
| `ACTIVE`       | Workaround currently in use         |
| `REMOVED`      | Workaround removed after proper fix |
| `REPLACED`     | Replaced by better workaround/fix   |
| `BLOCKED`      | Workaround cannot be applied        |
| `NEEDS_REVIEW` | Needs human/security/design review  |

---

## 12. Regression Entry Format

If a previously fixed issue reappears, add a regression entry.

```md id="tj3dnq"
## REGRESSION-YYYYMMDD-000 — Short Regression Title

### Related Original Bug
- BUG ID:

### Status
REGRESSION / IN_PROGRESS / FIXED_PENDING_RETEST / RESOLVED / BLOCKED

### Severity
S0_CRITICAL / S1_HIGH / S2_MEDIUM / S3_LOW / S4_POLISH

### What Regressed
- Expected old fixed behavior:
- Current broken behavior:

### Suspected Cause
- Recent phase/change:
- Changed files:
- Migration/provider/config impact:

### Fix Plan
- Steps:

### Retest
- Result:
- Notes:
```

Regression bugs must also update:

* `CHANGELOG.md`
* `FEATURE_REGISTRY.md`
* `MANUAL_VERIFICATION.md`
* `brain.md`

---

## 13. Security Bug Rules

Security bugs are always serious.

Mark as `S0_CRITICAL` or `S1_HIGH` if any of these happen:

* hidden contact number leaks
* private verification document leaks
* service role key exposed
* admin/staff page public accessible
* wrong user sees another user’s data
* wrong owner can edit/delete another listing
* guest can access protected dashboard
* staff can access module without permission
* RLS policy allows wrong access
* payment can be marked success without verification
* verified badge can be faked
* provider secrets exposed
* logs contain OTP/token/password/private data
* direct URL bypass works
* destructive action lacks permission/audit
* private storage bucket is public
* webhook signature missing/incorrect
* raw SQL/database error visible publicly

Security bug fix cannot be marked `RESOLVED` until:

* allowed access test passes
* denied guest test passes
* denied wrong-owner test passes
* denied wrong-role test passes
* admin/staff scoped test passes where relevant
* service role client exposure check passes
* logs checked for secrets/private data
* `SECURITY_RLS_CHECKLIST.md` updated
* `MANUAL_VERIFICATION.md` updated
* `CHANGELOG.md` updated
* `FEATURE_REGISTRY.md` updated

---

## 14. Contact Privacy Bug Rules

Contact privacy is critical.

Create a bug immediately if:

* guest sees hidden phone number
* hidden phone appears in API response
* hidden phone appears in page source
* hidden phone appears in metadata/schema
* hidden phone appears in SEO page
* hidden phone appears in search result card
* hidden phone appears in share preview
* contact reveal works without login
* contact reveal works without consent
* contact reveal does not log access
* contact reveal allows unlimited scraping
* project contact rule is implemented incorrectly
* property hidden contact setting is ignored

Contact privacy bug must include:

* route/page
* role/login state
* API response check
* HTML/page source check
* metadata/schema check
* RLS/public-view check
* contact reveal log check

---

## 15. Payment Bug Rules

Payment bugs are critical.

Create a bug immediately if:

* plan activates without verified payment
* fake payment success appears
* failed payment activates subscription
* pending payment activates subscription
* webhook signature is skipped
* duplicate payment creates duplicate subscription
* invoice generated for failed payment
* invoice number wasted on failed payment
* refund state incorrect
* manual activation lacks audit reason
* test mode appears in production
* Razorpay key exposed client-side incorrectly
* payment raw error visible to user
* payment provider failure has no safe fallback
* coupon/discount allows abuse
* GST invoice calculation is wrong
* billing history shows wrong amount
* checkout amount differs from invoice amount

Payment bug fix cannot be marked `RESOLVED` until failed/pending/success/duplicate cases are retested or marked `SETUP_REQUIRED` with reason.

---

## 16. Provider Bug Rules

Provider/API bugs must never be hidden.

Create a bug or setup-required entry if:

* OTP provider missing
* OTP delivery fails
* WhatsApp API fails
* WhatsApp template missing/unapproved
* SMS provider fails
* Email provider fails
* Google Maps quota fails
* Razorpay webhook fails
* Cloudflare R2 upload fails
* Cloudflare CDN URL fails
* Analytics provider fails
* Error tracking leaks private data
* provider dashboard says active without real test
* provider fallback missing
* provider secret exposed
* provider test button gives fake success
* `.env.example` missing required variable
* production uses dev/mock/test provider

If provider is not configured, status must be `SETUP_REQUIRED`, not `RESOLVED`.

---

## 17. Media / Upload Bug Rules

Create a bug immediately if:

* unsupported file type uploads
* unsafe SVG uploads
* file size limit ignored
* corrupt image breaks page
* image stretches/distorts
* image causes layout shift
* image drag causes accidental interaction
* cover image missing and no fallback
* upload failure has no retry
* upload leaves orphan file
* private document uses public bucket
* PDF preview leaks private file
* signed URL never expires
* EXIF metadata leaks private location/device data
* video upload breaks layout
* HEIC/HEIF unsupported without fallback
* CDN cache shows old deleted media
* malicious upload not blocked where scan is required

Media fix cannot be marked `RESOLVED` until upload, display, error, privacy and mobile checks pass for affected file type.

---

## 18. UI / Responsive Bug Rules

Create a bug immediately if:

* horizontal scroll appears
* element overlaps
* button/card text wraps badly
* brand name “My Gujarat Property” wraps or breaks
* mobile header overflows
* sticky CTA covers content
* table does not convert to cards on mobile
* modal overflows mobile screen
* bottom sheet cannot close
* overlay inside click closes modal
* background scroll remains unlocked
* card opens while scrolling
* nested button triggers parent click
* text click auto-copies without copy button
* images drag accidentally
* gallery swipe conflicts with page scroll
* dead button exists
* broken link exists
* loading state missing
* empty state missing
* error state missing
* unauthorized state missing
* setup-required state missing
* disabled state unclear
* keyboard navigation broken
* focus state missing
* contrast too low
* form error not readable

Responsive bug must mention tested width:

* 320px
* 360px
* 390px
* 430px
* 768px
* 1024px
* 1366px
* ultra-wide if relevant

UI bug fix cannot be marked `RESOLVED` until responsive retest passes for affected sizes.

---

## 19. Auth And Role Bug Rules

Create a bug immediately if:

* registered user still sees Login/Register button
* guest sees dashboard
* owner can post project
* builder can post normal property when not allowed
* broker/builder/owner redirected to wrong dashboard
* login/register does not preserve action intent
* unregistered mobile does not show register message
* public user can register as admin/staff
* admin/staff can login through mobile public login
* admin/staff login route indexed
* admin/staff create account visible publicly
* staff can access unassigned module
* Super Admin cannot access a staff module
* role change bypasses approval
* role change does not warn about listing/subscription impact
* session not revoked after ban/role change where required
* direct URL bypass works

Auth/role bug fix requires guest, owner, broker, builder, admin/staff and wrong-role tests where relevant.

---

## 20. Property / Project / Requirement Bug Rules

Create a bug immediately if:

* wrong fields show for selected property type
* required fields missing
* irrelevant fields show
* owner can post project
* builder can post property
* project allows PG/hostel/room type
* property/project publishes without approval
* edit/update does not require reapproval
* rejected listing appears publicly
* hidden contact leaks
* project contact not visible to logged-in users
* fake RERA/verified badge appears
* project unit inventory inconsistent
* requirement feed shows wrong role data
* proposal duplicates allowed
* proposal status wrong
* requirement expiry/renewal broken
* listing delete hard-deletes without rule
* soft delete not respected
* public detail page shows draft/private data
* similar listings show fake or unrelated data

Fix requires role, status, public/private, dashboard and admin moderation retest.

---

## 21. Admin / Staff Bug Rules

Create a bug immediately if:

* admin route is public
* staff role sees wrong menu
* staff can perform unauthorized action
* Super Admin cannot see all modules
* admin row is not clickable where required
* admin detail missing required related data
* sensitive data visible without permission
* private document accessible without permission
* reject/need-changes lacks reason
* audit log missing for high-risk action
* bulk action lacks preview/confirmation
* staff can approve own high-risk action where maker-checker is required
* export lacks permission/audit
* delete lacks confirmation/audit
* admin mobile layout breaks
* admin table not usable on mobile

Admin bugs must be retested with at least:

* Super Admin
* Admin
* relevant staff role
* wrong staff role
* unauthenticated guest

where applicable.

---

## 22. SEO / CMS / Legal Bug Rules

Create a bug immediately if:

* fake city page appears
* fake listing count appears
* empty/thin page indexed
* canonical wrong
* noindex missing where required
* sitemap includes private/admin/thin pages
* robots allows admin route indexing
* hidden phone/private data appears in schema/meta
* false “No.1”, “100% verified”, “guaranteed” claim appears
* legal page missing
* Terms/Privacy checkbox missing during registration
* cookie banner missing where required
* refund/payment policy missing from checkout
* listing legal warning missing
* RERA disclaimer missing on project page
* verification disclaimer missing
* lead/contact sharing notice missing
* legal content marked final without lawyer review

Legal bugs may require `NEEDS_LEGAL_REVIEW`.

---

## 23. Performance Bug Rules

Create a bug if:

* unbounded DB read exists
* N+1 query exists
* search loads too much data
* dashboard loads too slowly
* image not optimized
* large images used on cards
* list/table lacks pagination
* no index on expensive query
* cache invalidation too broad
* whole site revalidated unnecessarily
* page freezes on mobile
* long task blocks interaction
* build bundle too large
* provider call blocks user request unnecessarily
* background job not used for heavy work
* Core Web Vitals targets fail
* 1 lakh live user target is not considered for major feature

Performance bug fix must not weaken security, RLS, privacy or verification.

---

## 24. Deployment / Rollback Bug Rules

Create a bug if:

* migration lacks rollback notes
* destructive migration lacks backup plan
* production update lacks backup
* deployment lacks changelog
* deployment lacks smoke test
* production shows blank/crash page
* raw DB error appears
* feature flag kill switch missing for risky feature
* rollback plan missing
* demo/dev/test data appears in production
* dev OTP remains enabled in production
* test payment remains enabled in production
* mock provider remains enabled in production
* production secrets hardcoded
* `.env.example` outdated

Deployment bugs must update `DEPLOYMENT_ROLLBACK.md`.

---

## 25. Manual Verification Failure Rules

Whenever manual verification fails, create a bug.

Manual verification failures include:

* route failed
* login failed
* role access failed
* RLS failed
* UI layout failed
* responsive failed
* text wrap failed
* no horizontal scroll failed
* provider setup-required missing
* payment state failed
* notification failed
* upload failed
* SEO/legal check failed
* build/lint/typecheck failed
* test not run due to blocker

Manual verification bug must mention:

* verification prompt file
* exact checklist item
* screen size/device
* role/login state
* route
* expected result
* actual result
* fix required
* retest required

---

## 26. Current Known Bugs

No actual website implementation has started yet.

Therefore, there are currently no app-code bugs discovered.

Current status:

| Area                | Known Bugs |
| ------------------- | ---------- |
| Code setup          | None yet   |
| Database            | None yet   |
| RLS                 | None yet   |
| Auth                | None yet   |
| Public UI           | None yet   |
| Dashboards          | None yet   |
| Admin               | None yet   |
| Property            | None yet   |
| Project             | None yet   |
| Requirement         | None yet   |
| Leads CRM           | None yet   |
| Messaging           | None yet   |
| Billing/payment     | None yet   |
| Media/upload        | None yet   |
| Providers           | None yet   |
| SEO/CMS/legal       | None yet   |
| Performance         | None yet   |
| Deployment          | None yet   |
| Manual verification | None yet   |

Important:

* `None yet` does not mean bug-free.
* It means implementation/testing has not started.
* Bugs must be added as soon as development or verification finds them.

---

## 27. Current Documentation Issues / Pending Risks

These are not app-code bugs, but they are documentation-generation tracking risks.

## BUG-20260629-001 — Documentation Pack Not Fully Generated Yet

### Status

OPEN

### Severity

S2_MEDIUM

### Priority

P1_FIX_THIS_PHASE

### Category

* DOCS
* WORKFLOW

### Found In

* Phase: Documentation generation
* Prompt file: Not applicable yet
* Verification prompt: Not applicable yet
* Environment: Chat/document generation
* Route/page: None
* Role/login state: None
* Device/screen size: None
* Browser: None
* Provider mode: None
* Related feature IDs:

  * DOC-004
  * DOC-005
  * DOC-006
  * DOC-007
  * DOC-008
  * DOC-009
  * DOC-010
  * DOC-011 to DOC-029

### Summary

* What is wrong: Full documentation pack is still in progress.
* Expected behavior: All 26 detailed documentation files and all prompt files must be generated without skipping any requirement.
* Actual behavior: First files are generated, remaining files are pending.
* User impact: Claude Code cannot yet use the complete final documentation pack.
* Security/privacy impact: Security/RLS docs are pending.
* Payment/provider impact: API provider status docs are pending.
* SEO/legal impact: Detailed SEO/legal docs are pending.
* Performance impact: Performance checklist and detailed performance docs are pending.

### Reproduction Steps

1. Check final agreed file list.
2. Compare generated files count.
3. Observe pending files remain.

### Evidence

* Generated:

  * `CLAUDE.md`
  * `brain.md`
  * `FEATURE_REGISTRY.md`
  * `CHANGELOG.md`
  * `BUGS_AND_FIXES.md`
* Pending:

  * `MANUAL_VERIFICATION.md`
  * `API_PROVIDER_STATUS.md`
  * `DEPLOYMENT_ROLLBACK.md`
  * `SECURITY_RLS_CHECKLIST.md`
  * `PERFORMANCE_CHECKLIST.md`
  * detailed docs
  * prompt files

### Root Cause

* Documentation generation is being done file-by-file as requested.

### Fix Plan

* Continue generating files in agreed order.
* Do not skip any requirement.
* Keep each file complete.
* Mention next file after each generation.

### Fix Implementation

* Changed files:

  * `BUGS_AND_FIXES.md`
* SQL/migration files:

  * None
* RLS policies changed:

  * None
* Provider/env changes:

  * None
* UI changes:

  * None

### Retest Steps

1. Complete all documentation files.
2. Complete all prompt files.
3. Compare against final agreed list.
4. Confirm no file missing.

### Retest Result

NOT_RUN

### Retest Notes

* Date: 2026-06-29
* Tested by: Not run yet
* Result details: Pending full documentation generation
* Remaining issue: Many files still need generation.

### Docs Updated

* `BUGS_AND_FIXES.md`
* `CHANGELOG.md` should be updated after this file is accepted.
* `FEATURE_REGISTRY.md` should mark DOC-005 as DONE after acceptance.
* `brain.md` should update generated file progress after acceptance.

### Rollback / Workaround

* Workaround exists: No
* Workaround details: Continue file-by-file generation.
* Removal condition: All agreed docs and prompts generated.
* Rollback needed: No
* Rollback path: Revert documentation file if wrong.

### Final Resolution

* Resolved date: Pending
* Final status: OPEN
* Final verification: NOT_RUN

---

## BUG-20260629-002 — Website Implementation Not Started Yet

### Status

OPEN

### Severity

S2_MEDIUM

### Priority

P2_FIX_BEFORE_LAUNCH

### Category

* CORE
* WORKFLOW

### Found In

* Phase: Documentation generation
* Prompt file: Not applicable yet
* Verification prompt: Not applicable yet
* Environment: Project planning
* Route/page: None
* Role/login state: None
* Device/screen size: None
* Browser: None
* Provider mode: None
* Related feature IDs:

  * CORE-001 onward
  * AUTH-001 onward
  * PROP-001 onward
  * PROJ-001 onward
  * REQ-001 onward
  * ADMIN-001 onward
  * BILL-001 onward
  * QA-001 onward

### Summary

* What is wrong: Actual website implementation has not started.
* Expected behavior: After docs and prompts are generated, Claude Code must implement the website phase-by-phase.
* Actual behavior: Only documentation is being generated currently.
* User impact: Website is not yet built.
* Security/privacy impact: RLS/security not implemented yet.
* Payment/provider impact: Razorpay/providers not configured yet.
* SEO/legal impact: SEO/legal pages not implemented yet.
* Performance impact: Performance architecture not implemented yet.

### Reproduction Steps

1. Check current project implementation status in `brain.md`.
2. Observe all implementation areas are `NOT_STARTED` or `SETUP_REQUIRED`.

### Evidence

* No app code generated in this documentation phase.
* No SQL migration created.
* No provider configured.
* No manual verification run.

### Root Cause

* User requested documentation generation first before prompt files and before Claude Code implementation.

### Fix Plan

* Finish documentation pack.
* Generate prompt pack.
* Run phase prompts in Claude Code.
* Implement website phase-by-phase.
* Verify every phase before moving next.

### Fix Implementation

* Changed files:

  * `BUGS_AND_FIXES.md`
* SQL/migration files:

  * None
* RLS policies changed:

  * None
* Provider/env changes:

  * None
* UI changes:

  * None

### Retest Steps

1. After prompt pack is created, run `prompts/01_PROJECT_SETUP_BASELINE.md`.
2. Verify project setup.
3. Update implementation status.

### Retest Result

NOT_RUN

### Retest Notes

* Date: 2026-06-29
* Tested by: Not run yet
* Result details: Implementation has not started.
* Remaining issue: Website still needs implementation.

### Docs Updated

* `BUGS_AND_FIXES.md`
* `brain.md` should continue showing implementation not started until code phase begins.
* `FEATURE_REGISTRY.md` should keep implementation features `NOT_STARTED`.

### Rollback / Workaround

* Workaround exists: No
* Workaround details: Not applicable.
* Removal condition: Initial project setup phase starts and passes verification.
* Rollback needed: No
* Rollback path: Not applicable.

### Final Resolution

* Resolved date: Pending
* Final status: OPEN
* Final verification: NOT_RUN

---

## BUG-20260629-003 — Real API Providers Not Configured Yet

### Status

SETUP_REQUIRED

### Severity

S2_MEDIUM

### Priority

P2_FIX_BEFORE_LAUNCH

### Category

* PROVIDER
* OTP
* WHATSAPP
* EMAIL
* SMS
* MAPS
* RAZORPAY
* CLOUDFLARE_R2
* CDN
* ANALYTICS

### Found In

* Phase: Documentation generation
* Prompt file: Not applicable yet
* Verification prompt: Not applicable yet
* Environment: Project planning
* Route/page: Provider-backed features
* Role/login state: All roles affected depending on feature
* Device/screen size: None
* Browser: None
* Provider mode: `SETUP_REQUIRED`
* Related feature IDs:

  * API-005 onward
  * BILL-022 onward
  * MEDIA-001 onward
  * NOTIF-019 onward
  * SEARCH-025 onward

### Summary

* What is wrong: Real API providers are not configured yet.
* Expected behavior: Missing providers must show `SETUP_REQUIRED` and never fake success.
* Actual behavior: Documentation tracks providers as setup-required; no provider configured.
* User impact: OTP, WhatsApp, Razorpay, email, SMS, maps, Cloudflare R2/CDN, analytics and error tracking cannot be considered production-active yet.
* Security/privacy impact: Provider secrets and server-only configuration must be handled later.
* Payment/provider impact: Payment cannot be marked working until Razorpay is real and verified.
* SEO/legal impact: Maps/analytics/cookie consent provider-dependent features pending.
* Performance impact: CDN/storage optimization pending.

### Reproduction Steps

1. Check `brain.md` provider memory.
2. Check `FEATURE_REGISTRY.md` provider rows.
3. Observe providers marked `SETUP_REQUIRED`.

### Evidence

* Provider setup not done in documentation phase.
* No env variables configured.
* No `.env.example` provider variables generated yet.
* No real provider tests run.

### Root Cause

* User instructed development should first connect core Supabase and later real APIs one by one after website feature-complete.
* Provider integrations require real credentials/configuration.

### Fix Plan

* Keep provider-backed features in `SETUP_REQUIRED` until configured.
* Generate `API_PROVIDER_STATUS.md`.
* During provider phases, add env variables to `.env.example`.
* Test real providers.
* Block fake success states.
* Update provider status.

### Fix Implementation

* Changed files:

  * `BUGS_AND_FIXES.md`
* SQL/migration files:

  * None
* RLS policies changed:

  * None
* Provider/env changes:

  * None
* UI changes:

  * None

### Retest Steps

1. Configure real provider.
2. Test provider credentials.
3. Verify success/failure/setup-required states.
4. Update `API_PROVIDER_STATUS.md`.
5. Retest affected feature.

### Retest Result

NEEDS_PROVIDER_CHECK

### Retest Notes

* Date: 2026-06-29
* Tested by: Not run yet
* Result details: No real provider configured.
* Remaining issue: All provider integrations require later setup.

### Docs Updated

* `BUGS_AND_FIXES.md`
* `API_PROVIDER_STATUS.md` pending generation
* `brain.md` should continue showing setup-required provider status
* `FEATURE_REGISTRY.md` tracks provider dependencies

### Rollback / Workaround

* Workaround exists: Yes
* Workaround details: Show `SETUP_REQUIRED` state and disable/hide provider-backed action where needed.
* Removal condition: Real provider configured, tested and documented.
* Rollback needed: No
* Rollback path: Keep setup-required mode.

### Final Resolution

* Resolved date: Pending
* Final status: SETUP_REQUIRED
* Final verification: NEEDS_PROVIDER_CHECK

---

## BUG-20260629-004 — Manual Verification Has Not Started Yet

### Status

OPEN

### Severity

S2_MEDIUM

### Priority

P1_FIX_THIS_PHASE

### Category

* MANUAL_VERIFICATION
* QA

### Found In

* Phase: Documentation generation
* Prompt file: Not applicable yet
* Verification prompt: Not generated yet
* Environment: Project planning
* Route/page: All future routes
* Role/login state: All future roles
* Device/screen size: All required sizes
* Browser: Future QA
* Provider mode: Mixed
* Related feature IDs:

  * QA-001 onward
  * DOC-006

### Summary

* What is wrong: Manual verification structure is not generated and verification has not started.
* Expected behavior: Every phase must have manual verification prompt and detailed verification result.
* Actual behavior: Manual verification docs and prompts are pending.
* User impact: No phase can be considered PASS yet.
* Security/privacy impact: No RLS/security tests have run.
* Payment/provider impact: No provider/payment tests have run.
* SEO/legal impact: No SEO/legal checks have run.
* Performance impact: No responsive/performance checks have run.

### Reproduction Steps

1. Check generated files list.
2. Observe `MANUAL_VERIFICATION.md` is pending.
3. Observe no manual verification prompts generated yet.

### Evidence

* Current generated files:

  * `CLAUDE.md`
  * `brain.md`
  * `FEATURE_REGISTRY.md`
  * `CHANGELOG.md`
  * `BUGS_AND_FIXES.md`
* Pending:

  * `MANUAL_VERIFICATION.md`
  * all manual verification prompt files

### Root Cause

* Documentation generation is still in progress.

### Fix Plan

* Generate `MANUAL_VERIFICATION.md` next.
* Include detailed verification format.
* Later generate phase-wise manual verification prompts.
* Every implementation phase must fill manual verification results.

### Fix Implementation

* Changed files:

  * `BUGS_AND_FIXES.md`
* SQL/migration files:

  * None
* RLS policies changed:

  * None
* Provider/env changes:

  * None
* UI changes:

  * None

### Retest Steps

1. Generate `MANUAL_VERIFICATION.md`.
2. Confirm it includes PASS/PARTIAL/BLOCKED/FAIL rules.
3. Generate phase verification prompts later.
4. Use them during development.

### Retest Result

NOT_RUN

### Retest Notes

* Date: 2026-06-29
* Tested by: Not run yet
* Result details: Verification docs pending.
* Remaining issue: Manual verification system pending.

### Docs Updated

* `BUGS_AND_FIXES.md`

### Rollback / Workaround

* Workaround exists: No
* Workaround details: Not applicable.
* Removal condition: `MANUAL_VERIFICATION.md` generated and later used.
* Rollback needed: No
* Rollback path: Not applicable.

### Final Resolution

* Resolved date: Pending
* Final status: OPEN
* Final verification: NOT_RUN

---

## 28. Current Active Workarounds

## WORKAROUND-20260629-001 — Provider-Backed Features Must Use SETUP_REQUIRED Until Real API Setup

### Status

ACTIVE

### Related Bug

* BUG-20260629-003

### Reason

* Real providers are not configured during documentation generation.
* OTP, WhatsApp, Email, SMS, Razorpay, Maps, Cloudflare R2/CDN, Analytics and Error Tracking require real credentials and testing later.

### Temporary Behavior

* Provider-backed features must not pretend to work.
* UI must show `SETUP_REQUIRED` where relevant.
* Actions may be hidden/disabled with clear explanation.
* No fake sent, paid, uploaded, mapped, verified or active provider status is allowed.

### Risk

* Security risk: Low if disabled/setup-required state is enforced.
* Privacy risk: Low if provider calls are not made and private data stays local/server-side.
* Payment risk: Medium until Razorpay is configured; payments cannot be production-active.
* UX risk: Medium because some features will be unavailable.
* Performance risk: Low.
* Data risk: Low if no provider data is sent.

### Removal Condition

Remove this workaround only when:

1. Real provider credentials are configured.
2. `.env.example` is updated.
3. Provider test passes.
4. Failure state is tested.
5. Setup-required fallback still works if provider becomes disabled.
6. `API_PROVIDER_STATUS.md` is updated.
7. `CHANGELOG.md` is updated.
8. Affected features in `FEATURE_REGISTRY.md` are updated.

### Files Changed

* `BUGS_AND_FIXES.md`

### SQL / Migration Files

* None

### Docs Updated

* `BUGS_AND_FIXES.md`
* `brain.md` should keep provider setup-required memory.
* `API_PROVIDER_STATUS.md` pending generation.
* `FEATURE_REGISTRY.md` tracks provider dependencies.

### Retest

* Result: NEEDS_PROVIDER_CHECK
* Notes: Real provider setup and testing pending.

---

## WORKAROUND-20260629-002 — Documentation Generation File-by-File Until Complete

### Status

ACTIVE

### Related Bug

* BUG-20260629-001

### Reason

* Full documentation pack is large.
* User requested file-by-file generation and asked to continue without skipping/missing anything.

### Temporary Behavior

* Generate one file at a time.
* Each response must contain the complete requested file.
* If a file cannot fit in one response, clearly state continuation point.
* After each file, mention the next file.

### Risk

* Security risk: Low.
* Privacy risk: Low.
* Payment risk: Low.
* UX risk: Low.
* Performance risk: None.
* Data risk: Low.
* Workflow risk: Medium if a file is skipped; must follow agreed order.

### Removal Condition

Remove this workaround when all 26 docs and 31 prompt files are generated and reviewed.

### Files Changed

* `BUGS_AND_FIXES.md`

### SQL / Migration Files

* None

### Docs Updated

* `BUGS_AND_FIXES.md`
* `brain.md` should track progress.
* `CHANGELOG.md` should track generated files.

### Retest

* Result: NOT_RUN
* Notes: Full pack generation not complete yet.

---

## 29. Current Resolved Bugs

No resolved bugs yet.

Implementation and verification have not started.

Resolved bugs will be added here after actual fix + retest PASS.

Template:

```md id="0pmkhc"
## Resolved Bug Summary

| Bug ID | Title | Severity | Fixed In Phase | Retest Result | Files Changed | Date |
|---|---|---|---|---|---|---|
| BUG-YYYYMMDD-000 | Title | S2_MEDIUM | Phase name | PASS | file paths | YYYY-MM-DD |
```

---

## 30. Current Blocked Bugs

Current blocked/setup-required items:

| Bug ID           | Title                                   | Status         | Reason                                           | Required Action                             |
| ---------------- | --------------------------------------- | -------------- | ------------------------------------------------ | ------------------------------------------- |
| BUG-20260629-003 | Real API Providers Not Configured Yet   | SETUP_REQUIRED | Requires real provider credentials/configuration | Configure/test providers in provider phases |
| BUG-20260629-004 | Manual Verification Has Not Started Yet | OPEN           | Verification docs/prompts pending                | Generate `MANUAL_VERIFICATION.md` next      |

---

## 31. Retest Queue

Current retest queue:

| Bug ID           | Title                                      | Retest Needed                                   | Status               |
| ---------------- | ------------------------------------------ | ----------------------------------------------- | -------------------- |
| BUG-20260629-001 | Documentation Pack Not Fully Generated Yet | Full docs/prompt pack completeness check        | NOT_RUN              |
| BUG-20260629-002 | Website Implementation Not Started Yet     | Project setup phase verification                | NOT_RUN              |
| BUG-20260629-003 | Real API Providers Not Configured Yet      | Provider configuration and real API tests       | NEEDS_PROVIDER_CHECK |
| BUG-20260629-004 | Manual Verification Has Not Started Yet    | Manual verification doc/prompt generation check | NOT_RUN              |

---

## 32. Fix Checklist

Before marking any bug `RESOLVED`, Claude must confirm:

* [ ] Bug is clearly described.
* [ ] Expected behavior is written.
* [ ] Actual behavior is written.
* [ ] Impact is written.
* [ ] Root cause is known or marked unknown.
* [ ] Fix plan is written.
* [ ] Exact files changed are listed.
* [ ] SQL/migration files are listed or `None`.
* [ ] RLS/security impact is listed.
* [ ] Provider/API impact is listed.
* [ ] UI/responsive impact is listed.
* [ ] Tests are run or exact reason is documented.
* [ ] Manual verification is run or exact reason is documented.
* [ ] Retest result is not fake.
* [ ] `CHANGELOG.md` updated.
* [ ] `FEATURE_REGISTRY.md` updated.
* [ ] `MANUAL_VERIFICATION.md` updated.
* [ ] `brain.md` updated if status/workaround/decision changed.
* [ ] `SECURITY_RLS_CHECKLIST.md` updated for security/RLS bugs.
* [ ] `API_PROVIDER_STATUS.md` updated for provider bugs.
* [ ] `DEPLOYMENT_ROLLBACK.md` updated for deployment/rollback bugs.
* [ ] `PERFORMANCE_CHECKLIST.md` updated for performance bugs.
* [ ] Workaround removed or removal condition written.
* [ ] Pending issues honestly listed.
* [ ] No secrets/log-private-data exposed.

If any item is missing, do not mark `RESOLVED`.

---

## 33. Phase PASS Blocking Rules

A phase cannot be marked `PASS` if any of these exist in that phase:

* `S0_CRITICAL` open bug
* `S1_HIGH` open bug
* security/RLS bug not fixed
* contact privacy bug not fixed
* payment verification bug not fixed
* admin/staff permission bug not fixed
* public/private data leak not fixed
* build failure
* typecheck failure
* lint failure that affects release quality
* route crash
* broken login/register
* dead primary CTA
* broken posting flow in that phase
* broken admin approval flow in that phase
* broken mobile layout in that phase
* horizontal scroll in primary views
* provider fake success
* test mode active in production phase
* dev OTP active in production phase
* missing required migration for DB change
* missing rollback notes for destructive DB change
* manual verification not run and no acceptable reason
* documentation not updated

Allowed exception:

* User explicitly approves moving ahead with `PARTIAL` or `BLOCKED`.
* The issue must stay tracked in this file and `FEATURE_REGISTRY.md`.

---

## 34. Production Launch Blocking Bugs

Production launch is blocked if any of these remain open:

### Security / Privacy

* contact number leak
* private document leak
* service role key leak
* RLS failure
* admin/staff public access
* role bypass
* raw secret/log exposure
* provider secret exposure
* unsafe upload
* webhook signature missing
* missing rate limits for OTP/contact reveal/payment-sensitive APIs

### Payment / Billing

* fake payment success
* failed/pending payment activates plan
* invoice generated without verified payment
* test payment mode active
* Razorpay webhook unverified
* GST/invoice sequence broken
* manual activation lacks audit

### Auth / Roles

* public admin registration possible
* admin mobile login possible
* logged-in user still sees login/register
* wrong dashboard redirect
* direct URL unauthorized access works
* role change bypasses approval

### UI / UX

* homepage broken
* search broken
* login/register popup broken
* public detail page broken
* dashboard broken for any active role
* admin panel broken
* mobile layout broken on required sizes
* horizontal scroll on primary pages
* text wrap breaks key UI
* dead primary buttons

### Providers / Deployment

* dev OTP active
* mock provider active
* test payment active
* production env misconfigured
* no backup
* no rollback plan
* build fails
* no production smoke test
* demo data visible publicly
* legal pages missing
* privacy/terms consent missing

---

## 35. Bug ID Rules

Bug IDs must use:

```md id="4fb3um"
BUG-YYYYMMDD-001
```

Example:

```md id="pczfoq"
BUG-20260629-001
```

Workaround IDs must use:

```md id="8tl0c1"
WORKAROUND-YYYYMMDD-001
```

Regression IDs must use:

```md id="h9b7vk"
REGRESSION-YYYYMMDD-001
```

Rules:

* Do not reuse IDs.
* Do not renumber old bugs.
* Mark duplicates as `DUPLICATE` and link original bug.
* Keep old bug history even after resolved.
* Do not delete bug history.
* Do not hide production bugs.

---

## 36. Bug Source Rules

Every bug must mention where it came from:

* manual verification
* automated test
* lint/typecheck/build
* user report
* admin/staff report
* monitoring alert
* security review
* RLS test
* provider test
* payment webhook test
* responsive QA
* SEO QA
* legal review
* performance/load test
* deployment smoke test
* production incident
* code review
* migration review
* docs/code conflict

---

## 37. Exact Evidence Rules

Do not paste long logs.

Allowed evidence:

* relevant 20–30 log lines
* exact route path
* exact file path
* screenshot filename/path
* browser/device size
* error code
* provider error ID if safe
* payment order ID if safe and redacted
* database migration filename
* SQL error summary without secrets/private data

Never include:

* OTP
* password
* API key
* access token
* refresh token
* service role key
* Razorpay secret
* provider secret
* private document URL
* full private user payload
* full hidden contact list
* raw database credentials

---

## 38. Bug Fix Final Response Rule

When Claude fixes a bug, final response must include:

```md id="cjvby5"
## Fixed
- Bug ID:
- Summary:

## Changed Files
- path/to/file

## SQL / Migration Files
- path/to/file.sql
- None

## Tests Run
- command
- result

## Retest Result
PASS / PARTIAL / BLOCKED / FAIL

## Docs Updated
- BUGS_AND_FIXES.md
- CHANGELOG.md
- FEATURE_REGISTRY.md
- MANUAL_VERIFICATION.md
- brain.md

## Pending Issues
- issue or None
```

If no test was run, say exact reason and do not mark `PASS`.

---

## 39. Bug Relationship To Other Docs

When updating this file, also update:

### Always for bug/fix

* `CHANGELOG.md`
* `FEATURE_REGISTRY.md`
* `MANUAL_VERIFICATION.md`

### If project memory/status changes

* `brain.md`

### If provider/API bug

* `API_PROVIDER_STATUS.md`

### If security/RLS/privacy/contact/admin bug

* `SECURITY_RLS_CHECKLIST.md`

### If performance/query/cache/load bug

* `PERFORMANCE_CHECKLIST.md`

### If deployment/migration/rollback bug

* `DEPLOYMENT_ROLLBACK.md`

### If code behavior contradicts docs

* relevant detailed docs
* `brain.md` conflict note

---

## 40. Current Documentation Generation Progress

| File No. | File                                                      | Bug/Fix Tracking Status          |
| -------: | --------------------------------------------------------- | -------------------------------- |
|        1 | `CLAUDE.md`                                               | Created, needs manual review     |
|        2 | `brain.md`                                                | Created, needs continued updates |
|        3 | `FEATURE_REGISTRY.md`                                     | Created, needs continued updates |
|        4 | `CHANGELOG.md`                                            | Created, needs continued updates |
|        5 | `BUGS_AND_FIXES.md`                                       | Created                          |
|        6 | `MANUAL_VERIFICATION.md`                                  | Pending                          |
|        7 | `API_PROVIDER_STATUS.md`                                  | Pending                          |
|        8 | `DEPLOYMENT_ROLLBACK.md`                                  | Pending                          |
|        9 | `SECURITY_RLS_CHECKLIST.md`                               | Pending                          |
|       10 | `PERFORMANCE_CHECKLIST.md`                                | Pending                          |
|       11 | `docs/01_PROJECT_MASTER_AND_SCOPE.md`                     | Pending                          |
|       12 | `docs/02_CLAUDE_WORKFLOW_AND_TOKEN_LIGHT_RULES.md`        | Pending                          |
|       13 | `docs/03_ARCHITECTURE_TECH_STACK_DATABASE_RLS.md`         | Pending                          |
|       14 | `docs/04_AUTH_LOGIN_REGISTER_ROLES_PERMISSIONS.md`        | Pending                          |
|       15 | `docs/05_PUBLIC_ROLES_HOME_PROFILE_DASHBOARD.md`          | Pending                          |
|       16 | `docs/06_PROPERTY_PROJECT_REQUIREMENT_FULL_MATRIX.md`     | Pending                          |
|       17 | `docs/07_LEADS_CRM_PROPOSALS_SITE_VISITS_MESSAGES.md`     | Pending                          |
|       18 | `docs/08_ADMIN_SUPER_ADMIN_STAFF_MODULES.md`              | Pending                          |
|       19 | `docs/09_BILLING_SUBSCRIPTION_PAYMENT_GST_TRIAL.md`       | Pending                          |
|       20 | `docs/10_ADS_PROMOTION_NOTIFICATION_PROVIDER_MODES.md`    | Pending                          |
|       21 | `docs/11_LOCATION_SEARCH_SEO_CMS_BLOG_LEGAL.md`           | Pending                          |
|       22 | `docs/12_MEDIA_UPLOAD_STORAGE_IMAGE_VIDEO_PDF.md`         | Pending                          |
|       23 | `docs/13_UI_UX_DESIGN_SYSTEM_RESPONSIVE_RULES.md`         | Pending                          |
|       24 | `docs/14_SECURITY_PRIVACY_CONSENT_FRAUD_LEGAL.md`         | Pending                          |
|       25 | `docs/15_PERFORMANCE_DEPLOYMENT_ROLLBACK_QA.md`           | Pending                          |
|       26 | `docs/16_ADVANCED_FEATURES_PWA_LOCALIZATION_ANALYTICS.md` | Pending                          |

---

## 41. Current Open Bug Summary

| Bug ID           | Title                                      | Status         | Severity  | Priority             | Category               | Retest               |
| ---------------- | ------------------------------------------ | -------------- | --------- | -------------------- | ---------------------- | -------------------- |
| BUG-20260629-001 | Documentation Pack Not Fully Generated Yet | OPEN           | S2_MEDIUM | P1_FIX_THIS_PHASE    | DOCS/WORKFLOW          | NOT_RUN              |
| BUG-20260629-002 | Website Implementation Not Started Yet     | OPEN           | S2_MEDIUM | P2_FIX_BEFORE_LAUNCH | CORE/WORKFLOW          | NOT_RUN              |
| BUG-20260629-003 | Real API Providers Not Configured Yet      | SETUP_REQUIRED | S2_MEDIUM | P2_FIX_BEFORE_LAUNCH | PROVIDER               | NEEDS_PROVIDER_CHECK |
| BUG-20260629-004 | Manual Verification Has Not Started Yet    | OPEN           | S2_MEDIUM | P1_FIX_THIS_PHASE    | MANUAL_VERIFICATION/QA | NOT_RUN              |

---

## 42. Final Rule

A bug is not fixed until it is fixed and retested.

A phase is not PASS until blocking bugs are fixed or user explicitly accepts moving forward with tracked `PARTIAL` / `BLOCKED`.

A production launch is not allowed while critical bugs remain open.

Never skip, hide, delete or fake bug status.
