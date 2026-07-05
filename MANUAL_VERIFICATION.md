# MANUAL_VERIFICATION.md

# My Gujarat Property — Manual Verification, QA And Phase PASS Checklist

This file defines the manual verification system for **My Gujarat Property**.

Claude must update this file after every phase, every verification run, every failed check, every fix and every retest.

A phase must not move forward until it is verified as `PASS`, or the user explicitly approves continuing with `PARTIAL` or `BLOCKED`.

No fake PASS is allowed.

Manual verification must include exact notes, not only “done”.

---

## 1. Purpose

This file exists to make sure every development phase is manually checked before moving to the next phase.

Manual verification must confirm:

* requirements are implemented
* no feature is skipped
* no fake UI/data/payment/verified/provider status exists
* role-based access is correct
* RLS and backend security are correct
* public/private data stays protected
* responsive layout works on required devices
* no horizontal scroll appears
* no overlap appears
* important text does not wrap badly
* forms validate correctly
* loading/empty/error/success/disabled states exist
* provider missing states show `SETUP_REQUIRED`
* payment and billing states are safe
* media uploads are safe
* SEO/legal rules are respected
* docs are updated
* SQL/migrations are updated where needed
* bugs are tracked and fixed before PASS

This file is the source of truth for verification results.

---

## 2. Mandatory Verification Rule

Claude must manually verify every phase before marking it complete.

Every phase must include:

1. automated checks where available
2. manual UI checks
3. role access checks
4. RLS/security checks where relevant
5. responsive checks
6. provider/setup-required checks where relevant
7. payment checks where relevant
8. database/migration checks where relevant
9. documentation update checks
10. bug/fix tracking checks
11. final status

Allowed final verification results:

* `PASS`
* `PARTIAL`
* `BLOCKED`
* `FAIL`

No other result is allowed for final phase verification.

---

## 3. Verification Result Definitions

| Result    | Meaning                                                                                                                        | Can Move Next Phase?  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------ | --------------------- |
| `PASS`    | All required checks passed, no blocking bugs remain, docs updated                                                              | Yes                   |
| `PARTIAL` | Some checks passed but non-critical issues remain or some checks could not run                                                 | Only if user approves |
| `BLOCKED` | Verification cannot complete due to missing provider, missing decision, build failure, environment issue or unresolved blocker | Only if user approves |
| `FAIL`    | Verification failed and blocking issue exists                                                                                  | No                    |

---

## 4. No Fake PASS Rule

Do not mark `PASS` if any of these are true:

* tests were not run and no valid reason is documented
* manual verification was not run
* role access was not checked where relevant
* RLS/security was not checked where relevant
* hidden contact privacy was not checked where relevant
* responsive layout was not checked where relevant
* provider-backed feature fakes success
* payment activates plan without verified payment
* build/lint/typecheck failed
* a primary route crashes
* a primary CTA is dead
* dashboard access is wrong
* admin/staff access is wrong
* UI has horizontal scroll
* UI has overlap
* important text wraps/breaks badly
* loading/empty/error states are missing
* SQL/migration file is missing for DB change
* docs were not updated
* Feature Registry was not updated
* Changelog was not updated
* bugs were found but not tracked
* blocking bug remains unresolved

If anything is incomplete, mark:

* `PARTIAL`
* `BLOCKED`
* or `FAIL`

---

## 5. Manual Verification Update Rule

Claude must update this file after:

1. every phase implementation
2. every phase verification
3. every verification prompt run
4. every bug found during verification
5. every bug fix
6. every retest
7. every deployment smoke test
8. every rollback verification
9. every production readiness check
10. every user-approved PARTIAL/BLOCKED continuation

This file must never say only “done”.

Every verification entry must include exact notes.

---

## 6. Relationship To Other Docs

Whenever this file is updated, Claude must also update:

### Always

* `brain.md`
* `FEATURE_REGISTRY.md`
* `CHANGELOG.md`

### If bugs or failed checks exist

* `BUGS_AND_FIXES.md`

### If provider/API status changed

* `API_PROVIDER_STATUS.md`

### If deployment/rollback/migration/backup changed

* `DEPLOYMENT_ROLLBACK.md`

### If RLS/security/privacy/contact/admin access changed

* `SECURITY_RLS_CHECKLIST.md`

### If performance/caching/query/image/load changed

* `PERFORMANCE_CHECKLIST.md`

### If detailed requirement changed

* relevant detailed doc in `docs/`

---

## 7. Required Verification Entry Format

Every phase verification must use this exact format:

```md id="v5z7ph"
## PHASE-XX — Phase Name Verification

### Verification Date
- Date:
- Time:
- Environment:
- Branch:
- Commit:
- Build/version:
- Verified by:

### Related Files
- Prompt file:
- Manual verification prompt:
- Detailed docs used:
- Changed files:
- SQL/migration files:

### Phase Scope
- What this phase was supposed to implement:
- What was excluded:
- What is setup-required:
- What is deferred but tracked:

### Automated Checks
| Check | Command | Result | Notes |
|---|---|---|---|
| Install/dependency check | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| Lint | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| Typecheck | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| Build | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| Unit tests | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| E2E tests | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| SQL/migration validation | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |
| RLS tests | `command` | PASS/PARTIAL/BLOCKED/FAIL/NOT_RUN | notes |

### Manual Role Checks
| Role | Routes/Actions Checked | Result | Notes |
|---|---|---|---|
| Guest |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Owner |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Broker/Agent |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Builder/Developer |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Super Admin |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Admin |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Staff role(s) |  | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |

### Security / RLS Checks
| Check | Result | Notes |
|---|---|---|
| Guest denied protected access | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Wrong role denied | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Wrong owner denied | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Allowed owner access works | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Admin/staff scoped access works | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Super Admin full access works | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Service role not exposed to client | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Hidden contact number not leaked | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Private document not leaked | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Safe user-facing errors | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Rate limits checked | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Audit logs checked | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |

### UI / UX / Responsive Checks
| Width/Device | Result | Notes |
|---|---|---|
| 320px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| 360px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| 390px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| 430px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| 768px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| 1024px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| 1366px | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Ultra-wide if relevant | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |

### UI State Checks
| State | Result | Notes |
|---|---|---|
| Loading | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Empty | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Error | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Success | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Disabled | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Unauthorized | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Setup-required | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |

### Provider Checks
| Provider | Result | Notes |
|---|---|---|
| Supabase Auth | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Supabase DB | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Supabase RLS | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| OTP Provider | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| WhatsApp | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Email | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| SMS | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Razorpay | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Google Maps | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Cloudflare R2 | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Cloudflare CDN | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Analytics | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |
| Error tracking | PASS/PARTIAL/BLOCKED/FAIL/SETUP_REQUIRED/NOT_APPLICABLE |  |

### Data / Database Checks
| Check | Result | Notes |
|---|---|---|
| Migration file exists if DB changed | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Migration is safe/idempotent where possible | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Rollback notes exist | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| RLS policies exist | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Indexes added where needed | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| No unbounded reads | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| No N+1 query risk | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Soft delete respected | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Audit log created for sensitive action | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |

### SEO / Legal Checks
| Check | Result | Notes |
|---|---|---|
| Title/meta/canonical correct | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| No fake city/listing count | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Empty/thin pages noindex/hidden | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Legal notices present | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| Terms/Privacy consent present | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| RERA disclaimer present where needed | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |
| No false guarantee claims | PASS/PARTIAL/BLOCKED/FAIL/NOT_APPLICABLE |  |

### Bugs Found
| Bug ID | Title | Severity | Status | Notes |
|---|---|---|---|---|
|  |  |  |  |  |

### Fixes Done During Verification
| Bug ID | Fix Summary | Changed Files | Retest Result |
|---|---|---|---|
|  |  |  |  |

### Docs Updated
| File | Updated | Notes |
|---|---|---|
| `brain.md` | Yes/No |  |
| `FEATURE_REGISTRY.md` | Yes/No |  |
| `CHANGELOG.md` | Yes/No |  |
| `BUGS_AND_FIXES.md` | Yes/No |  |
| `MANUAL_VERIFICATION.md` | Yes/No |  |
| `API_PROVIDER_STATUS.md` | Yes/No/Not Applicable |  |
| `DEPLOYMENT_ROLLBACK.md` | Yes/No/Not Applicable |  |
| `SECURITY_RLS_CHECKLIST.md` | Yes/No/Not Applicable |  |
| `PERFORMANCE_CHECKLIST.md` | Yes/No/Not Applicable |  |

### Final Verification Result
PASS / PARTIAL / BLOCKED / FAIL

### Final Notes
- What passed:
- What failed:
- What is blocked:
- What is setup-required:
- What is pending:
- User approval required before next phase: Yes/No

### Next Phase
- Next prompt:
- Next verification prompt:
```

---

## 8. Short Verification Entry Format

For documentation-only files, this short format is allowed:

```md id="l0fnbq"
## DOC-XX — File Name Verification

### File
- `path/to/file.md`

### Verification Date
- Date:
- Verified by:

### Checks
| Check | Result | Notes |
|---|---|---|
| File created | PASS/PARTIAL/BLOCKED/FAIL |  |
| Scope covered | PASS/PARTIAL/BLOCKED/FAIL |  |
| No contradiction found | PASS/PARTIAL/BLOCKED/FAIL |  |
| Next file mentioned | PASS/PARTIAL/BLOCKED/FAIL |  |
| Changelog update required | PASS/PARTIAL/BLOCKED/FAIL |  |
| Feature Registry update required | PASS/PARTIAL/BLOCKED/FAIL |  |
| Brain update required | PASS/PARTIAL/BLOCKED/FAIL |  |

### Final Result
PASS / PARTIAL / BLOCKED / FAIL

### Notes
- 
```

---

## 9. Required Automated Checks

Claude must run these commands before marking an implementation phase `PASS`, unless not applicable or impossible.

Exact commands may vary by project package manager.

### 9.1 Dependency / Install Check

Examples:

```bash
npm install
npm ci
pnpm install
pnpm install --frozen-lockfile
```

Verification:

* dependencies install successfully
* no missing package
* no incompatible package
* lockfile updated only when intended
* no unexpected package added

### 9.2 Lint

Examples:

```bash
npm run lint
pnpm lint
```

Verification:

* lint passes
* no ignored real errors
* no new unsafe patterns
* no broken imports
* no unused critical code
* no accessibility lint issues where configured

### 9.3 Typecheck

Examples:

```bash
npm run typecheck
pnpm typecheck
tsc --noEmit
```

Verification:

* TypeScript passes
* no `any` abuse for critical data models
* server action return types are typed
* role/permission types are strict
* payment/provider status types are strict

### 9.4 Build

Examples:

```bash
npm run build
pnpm build
```

Verification:

* production build passes
* no route build crash
* no server/client boundary error
* no environment variable crash
* no exposed server-only import in client
* no static generation private data leak

### 9.5 Unit Tests

Examples:

```bash
npm run test
pnpm test
```

Verification:

* relevant tests pass
* failing tests are not ignored
* new critical logic has tests where feasible

### 9.6 E2E Tests

Examples:

```bash
npm run test:e2e
pnpm test:e2e
```

Verification:

* critical flows pass
* role navigation works
* protected routes blocked
* forms submit/validate
* dashboards load

### 9.7 SQL / Migration Validation

Examples:

```bash
supabase db diff
supabase db push --dry-run
supabase migration up --dry-run
```

Verification:

* migration file exists
* migration can apply
* migration has rollback notes
* RLS policies are included
* destructive operations are approved/documented
* seed/demo data is flagged

### 9.8 RLS Tests

Verification must include:

* guest denied sensitive data
* wrong owner denied
* wrong role denied
* correct owner allowed
* correct role allowed
* Super Admin allowed where intended
* staff scoped permissions enforced
* public-safe views do not leak private fields

---

## 10. If Automated Tests Cannot Run

If a command cannot run, Claude must document:

* command
* exact reason
* environment limitation
* risk
* manual fallback
* result status

Use this format:

```md id="7e0ziv"
### Test Not Run
- Command:
- Reason:
- Risk:
- Manual fallback:
- Result: PARTIAL / BLOCKED
```

A phase with missing automated tests cannot be `PASS` unless:

* the test is truly not applicable, and
* manual verification covers the risk, and
* reason is documented.

---

## 11. Required Responsive Verification

Manual responsive checks must include:

|      Width | Device Type          | Required                                        |
| ---------: | -------------------- | ----------------------------------------------- |
|      320px | Small mobile         | Always for public/auth/dashboard UI             |
|      360px | Common Android       | Always for public/auth/dashboard UI             |
|      390px | iPhone-like          | Always for public/auth/dashboard UI             |
|      430px | Large mobile         | Always for public/auth/dashboard UI             |
|      768px | Tablet               | Always for public/auth/dashboard/admin UI       |
|     1024px | Tablet/small desktop | Always for dashboard/admin/public UI            |
|     1366px | Desktop              | Always for dashboard/admin/public UI            |
| Ultra-wide | Large desktop        | Required for major dashboard/admin/search pages |

At every width, check:

* no horizontal scroll
* no overlap
* no unwanted gap
* no cramped cards
* no broken header
* brand name “My Gujarat Property” does not wrap
* buttons readable
* tap targets large enough
* form labels readable
* dropdowns usable
* modal/drawer/bottom sheet opens/closes correctly
* sticky CTA does not cover content
* table becomes cards on mobile
* text does not break important UI
* images do not stretch or distort
* loading/empty/error states fit layout
* footer hidden on dashboards/features
* public footer visible only where intended

---

## 12. Required Browser Verification

For production-ready phases, check:

* Chrome
* Safari
* Firefox
* Edge

Mobile-specific checks:

* Android Chrome
* iOS Safari if available

If browser testing cannot be done, mark:

* `PARTIAL`
* or `BLOCKED`

and document exact reason.

---

## 13. Required Accessibility Verification

For every new UI feature, check:

* keyboard navigation works
* focus state visible
* buttons have accessible names
* icons have labels if interactive
* form errors are readable
* labels connected to inputs
* modal focus does not trap incorrectly
* drawer/bottom sheet can be closed
* color contrast acceptable
* alt text for images
* no essential action is mouse-only
* no tiny tap targets on mobile

Target: WCAG 2.2 AA where practical.

Accessibility failures must be logged in `BUGS_AND_FIXES.md`.

---

## 14. Required UI State Verification

Every page/component must verify these states where applicable:

### Loading State

Check:

* skeleton or spinner appears
* layout does not jump badly
* no blank screen
* no raw loading placeholder
* no infinite spinner without timeout/fallback

### Empty State

Check:

* clear message
* helpful next action
* no fake data
* no fake count
* role-specific message where needed

### Error State

Check:

* safe user-facing error
* no raw SQL error
* no stack trace
* retry option where suitable
* provider failure maps to setup-required/failed state

### Success State

Check:

* clear confirmation
* correct redirect or next step
* no duplicate submit
* notification/toast if needed
* dashboard data updated/revalidated

### Disabled State

Check:

* disabled reason visible
* no dead button
* no `href="#"`
* plan/verification/provider lock clearly explained

### Unauthorized State

Check:

* guest redirected/prompted safely
* wrong role sees forbidden/upgrade/role message
* protected data not fetched publicly
* direct URL bypass blocked

### Setup-Required State

Check:

* missing provider not faked
* feature disabled safely
* clear setup message for allowed admin/internal
* public user gets graceful unavailable state where appropriate

---

## 15. Required Interaction Verification

Check these for any interactive UI:

* image drag disabled where needed
* card click does not fire while scrolling
* nested button does not trigger parent card click
* text does not auto-copy on click
* copy only through explicit copy button
* modal content click does not close overlay
* overlay outside click closes popup
* bottom sheet locks background scroll
* mobile back closes popup first where implemented
* double-submit blocked
* submit button shows loading/disabled state
* payment submit cannot duplicate
* inquiry submit cannot duplicate
* lead submit cannot duplicate
* upload cannot accidentally reorder while scrolling
* carousel swipe does not conflict with page scroll
* sticky CTA does not block content
* dropdown closes safely
* focus returns to trigger where practical

Failures must be logged as bugs.

---

## 16. Role-Based Manual Verification Matrix

Every role-sensitive phase must test these roles.

### 16.1 Guest

Guest must be able to:

* open homepage
* search approved public listings/projects
* view public detail pages
* view public SEO/CMS/legal pages
* open login/register popup
* use filters/search UI
* use city selector
* see public-safe profile pages where allowed

Guest must not be able to:

* see hidden contact numbers
* submit inquiry without login/register
* reveal contact without login/register
* save/shortlist without login
* post property
* post project
* post requirement
* access any dashboard
* access admin/staff routes
* access private API data
* access private documents

Guest verification checks:

| Check                                      | Required |
| ------------------------------------------ | -------- |
| Homepage opens                             | Yes      |
| Search works with real approved data only  | Yes      |
| Hidden contact not visible                 | Yes      |
| Inquiry triggers login/register            | Yes      |
| Direct dashboard URL blocked               | Yes      |
| Direct admin URL blocked                   | Yes      |
| No private data in page source/API         | Yes      |
| Legal/footer links visible on public pages | Yes      |

### 16.2 Owner

Owner must be able to:

* login/register as Owner
* see owner-specific header/home/dashboard
* post property
* post requirement
* manage own properties
* manage own requirements
* receive own leads
* view own analytics
* manage billing/subscription
* manage profile
* use help/support

Owner must not be able to:

* post project
* access broker-only modules
* access builder-only modules
* access admin/staff modules
* edit another user’s property/requirement
* see another user’s private leads/documents

Owner verification checks:

| Check                              | Required |
| ---------------------------------- | -------- |
| Owner dashboard redirect works     | Yes      |
| Owner can post property            | Yes      |
| Owner can post requirement         | Yes      |
| Owner cannot post project          | Yes      |
| Owner sees only own listings/leads | Yes      |
| Wrong-owner access denied          | Yes      |
| Plan/verification gates work       | Yes      |
| Dashboard mobile layout works      | Yes      |

### 16.3 Broker / Agent

Broker must be able to:

* login/register as Broker/Agent
* see broker-specific header/home/dashboard
* post property
* post requirement
* manage own property listings
* manage own requirements
* view relevant requirement feed
* send proposals where allowed
* receive/manage leads
* view analytics
* manage billing/subscription
* submit broker verification
* use help/support

Broker must not be able to:

* post builder project
* access builder team module unless assigned
* access admin/staff modules
* edit another broker/owner listing
* bypass plan/verification gates

Broker verification checks:

| Check                                                 | Required |
| ----------------------------------------------------- | -------- |
| Broker dashboard redirect works                       | Yes      |
| Broker can post property                              | Yes      |
| Broker can post requirement                           | Yes      |
| Broker cannot post project                            | Yes      |
| Broker requirement feed rules work                    | Yes      |
| Proposal duplicate prevention works where implemented | Yes      |
| Broker verification state shown correctly             | Yes      |
| Mobile dashboard usable                               | Yes      |

### 16.4 Builder / Developer

Builder must be able to:

* login/register as Builder/Developer
* see builder-specific header/home/dashboard
* post project
* manage own projects
* receive project leads
* receive matching buying requirements where allowed
* manage project analytics
* add agents
* assign agent permissions
* submit builder verification
* request banner ads/promotions
* manage billing/subscription
* use help/support

Builder must not be able to:

* post normal property unless explicitly approved by future rule
* post PG/hostel/room as project
* access owner/broker-only modules unless assigned by approved permission
* access admin/staff modules
* edit another builder’s project

Builder verification checks:

| Check                                                          | Required |
| -------------------------------------------------------------- | -------- |
| Builder dashboard redirect works                               | Yes      |
| Builder can post project                                       | Yes      |
| Builder cannot post normal property                            | Yes      |
| Project RERA fields/rules work                                 | Yes      |
| Project contact visible to logged-in users                     | Yes      |
| Agent permission scope works                                   | Yes      |
| Banner ads require approved project/plan/RERA where applicable | Yes      |
| Mobile dashboard usable                                        | Yes      |

### 16.5 Super Admin

Super Admin must be able to:

* login through separate admin/staff login
* access all admin modules
* see every staff module
* manage users
* manage staff
* manage roles
* manage permissions
* manage properties/projects/requirements
* manage moderation queues
* manage verification
* manage billing/plans/payments
* manage providers/settings
* manage ads
* manage SEO/CMS/legal
* manage locations
* view audit logs
* view system/provider health
* use feature flags
* use maintenance mode
* perform allowed high-risk actions with audit/confirmation

Super Admin must not:

* use public mobile OTP admin login
* create staff account publicly
* perform high-risk actions without audit where required
* expose secrets

Super Admin verification checks:

| Check                        | Required |
| ---------------------------- | -------- |
| Separate admin login works   | Yes      |
| Admin URL noindex            | Yes      |
| All modules visible          | Yes      |
| Staff module access included | Yes      |
| Sensitive actions audited    | Yes      |
| Provider secrets not exposed | Yes      |
| Admin mobile layout works    | Yes      |

### 16.6 Admin

Admin must be able to:

* login through separate admin/staff login
* access assigned daily operation modules
* manage moderation/support/users based on permissions
* view details where allowed
* take audited actions where allowed

Admin must not automatically be able to:

* manage provider secrets
* manage feature flags
* manage Super Admin settings
* manage staff permissions unless granted
* bypass sensitive permissions
* access private documents without permission

Admin verification checks:

| Check                                 | Required |
| ------------------------------------- | -------- |
| Admin route blocked from public login | Yes      |
| Assigned module access works          | Yes      |
| Unassigned module access denied       | Yes      |
| Sensitive data permission enforced    | Yes      |
| Admin actions audited                 | Yes      |

### 16.7 Staff Roles

Staff roles to verify where implemented:

* Verification Manager
* Support Manager
* Content Manager
* SEO Manager
* Ads Manager
* Billing Manager
* Payment Manager
* City Manager
* User Manager
* Notification Manager
* System Manager
* Security Manager
* Reports Manager
* Audit Manager

Staff verification checks:

| Check                                             | Required |
| ------------------------------------------------- | -------- |
| Staff sees only assigned menu                     | Yes      |
| Staff cannot access wrong module by URL           | Yes      |
| Staff action permissions enforced server-side     | Yes      |
| Staff sensitive action audited                    | Yes      |
| Staff private document access permission enforced | Yes      |
| Staff export permission enforced                  | Yes      |
| Staff mobile admin layout usable                  | Yes      |
| Staff session/security rules work                 | Yes      |

---

## 17. Direct URL Bypass Verification

Every protected route must be manually tested by pasting URL directly into browser.

Check direct URL access for:

* guest
* wrong role
* wrong owner
* owner
* broker
* builder
* admin
* wrong staff role
* Super Admin

Required result:

* allowed role can access
* denied role cannot access
* denied user does not receive protected data
* API/server action also denies
* RLS also denies
* forbidden/redirect message is safe
* no raw error
* no private info in response

Direct URL bypass failure is a blocking security bug.

---

## 18. RLS Manual Verification

RLS must be checked whenever DB/RLS/sensitive data changes.

### 18.1 Required RLS Cases

| Case                                                 | Expected |
| ---------------------------------------------------- | -------- |
| Guest reads public approved property/project only    | Allowed  |
| Guest reads draft/pending/rejected listing           | Denied   |
| Guest reads hidden contact/private fields            | Denied   |
| Guest reads private documents                        | Denied   |
| Owner reads own property/requirement                 | Allowed  |
| Owner reads another user’s private data              | Denied   |
| Broker reads own listings/leads                      | Allowed  |
| Broker reads unauthorized listings/leads             | Denied   |
| Builder reads own projects/leads/agents              | Allowed  |
| Builder reads another builder’s private project data | Denied   |
| Agent reads assigned builder leads only              | Allowed  |
| Agent reads unassigned leads                         | Denied   |
| Admin/staff reads assigned scope                     | Allowed  |
| Staff reads unassigned scope                         | Denied   |
| Super Admin reads all allowed admin data             | Allowed  |
| Public-safe views exclude private fields             | Required |
| Service role only used server-side                   | Required |

### 18.2 RLS Verification Evidence

Verification must include:

* role tested
* table/view tested
* action tested
* expected result
* actual result
* SQL/API/server action path used
* result PASS/PARTIAL/BLOCKED/FAIL

If RLS cannot be tested, mark `BLOCKED` or `PARTIAL`.

---

## 19. Contact Privacy Verification

Contact privacy must be checked for every public detail/search/profile/contact-related phase.

### 19.1 Hidden Contact Checks

Check hidden contact number is not present in:

* search result cards
* detail pages
* dashboard views where unauthorized
* public profile pages
* page source
* API response
* server component props exposed to client
* metadata
* Open Graph metadata
* schema markup
* sitemap
* share preview
* logs
* notifications where unauthorized
* export files

### 19.2 Contact Reveal Checks

Check:

* guest cannot reveal contact
* guest gets login/register popup
* login/register preserves original intent
* logged-in user sees allowed contact/reveal flow
* consent notice shown
* contact reveal logged
* reveal limit/rate limit works where implemented
* duplicate reveal handling works
* abuse protection works
* owner/broker/builder receives lead/notification where expected
* hidden property contact setting respected
* project contact visible to logged-in users as required

Any contact leak is `S0_CRITICAL` and phase cannot pass.

---

## 20. Auth Manual Verification

Auth phases must check:

### Public Login/Register

| Check                                             | Required |
| ------------------------------------------------- | -------- |
| Mobile number input works                         | Yes      |
| Existing number proceeds to login OTP             | Yes      |
| Unregistered number shows register prompt         | Yes      |
| Register role selector shows Owner/Broker/Builder | Yes      |
| Role details are clear                            | Yes      |
| Full name field required                          | Yes      |
| Email field shown                                 | Yes      |
| Mobile field shown                                | Yes      |
| Terms + Privacy checkbox mandatory                | Yes      |
| OTP confirmation works or setup-required shown    | Yes      |
| OTP resend cooldown works                         | Yes      |
| Wrong OTP error safe                              | Yes      |
| Rate limit exists or tracked                      | Yes      |
| Logged-in user no longer sees Login/Register      | Yes      |
| Login action returns to original intent           | Yes      |
| Login direct button redirects correctly           | Yes      |

### Admin/Staff Login

| Check                                                   | Required |
| ------------------------------------------------------- | -------- |
| Separate admin/staff login URL                          | Yes      |
| Admin/staff URL noindex                                 | Yes      |
| No public create account                                | Yes      |
| No mobile login for staff/admin                         | Yes      |
| Email/Google login only                                 | Yes      |
| Invite-only staff account                               | Yes      |
| Staff permissions enforced                              | Yes      |
| Login attempts limited                                  | Yes      |
| Session timeout where implemented                       | Yes      |
| Suspicious login alert where implemented/setup-required | Yes      |

---

## 21. Property Manual Verification

Property phases must check:

* owner can post property
* broker can post property
* builder cannot post property unless approved future rule
* property type selector works
* purpose selector works
* subtype fields work
* irrelevant fields hidden
* required fields block next step/submit
* helper text shown where needed
* full location hierarchy works
* missing location request works where implemented
* image upload works or setup-required shown
* cover image selection works
* image reorder/crop works where implemented
* brochure PDF only where allowed
* contact visibility rules work
* preview before submit works
* draft save/resume works
* submit for approval works
* public display blocked until approved
* edit/update requires reapproval
* pause/resume works
* delete is soft delete
* detail page shows all public details
* inquiry button works
* report option works
* uploader profile clickable
* similar properties real or hidden
* SEO/meta safe
* legal warning present
* no hidden contact leak

---

## 22. Project Manual Verification

Project phases must check:

* builder can post project
* owner cannot post project
* broker cannot post project unless future approved rule
* project type selector works
* purpose sell/rent only
* no PG/hostel/room project type
* project subtype fields work
* RERA fields/rules work
* RERA number required where applicable before promotion/ad
* RERA disclaimer shown on detail page
* wings/towers/floors/units structure works
* unit inventory statuses work
* amenities work
* construction/possession timeline works
* project images upload or setup-required shown
* one video rule works
* brochure PDF works
* floor plan section works
* 360°/virtual tour URL/embed safe where implemented
* project contact visible to logged-in users
* inquiry button works
* approval workflow works
* edit/update reapproval works
* pause/resume works
* soft delete works
* detail page shows public-safe data
* builder/uploader profile clickable
* similar projects real or hidden
* SEO/meta/schema safe
* no fake RERA/verified badge

---

## 23. Requirement And Proposal Manual Verification

Requirement phases must check:

* owner can post requirement
* broker can post requirement
* builder requirement visibility rules work
* required fields work
* location/budget/preference fields work
* privacy/contact rules work
* legal notice shown
* approval workflow works
* edit/update requires reapproval
* requirement feed role visibility works
* duplicate/spam prevention works where implemented
* matching algorithm does not fake results
* match score only if implemented and explainable
* notifications for matching work or setup-required shown
* broker/builder can send proposal where allowed
* irrelevant proposal blocked where implemented
* duplicate proposal blocked
* proposal status lifecycle works
* proposal viewed/shortlist/accepted/rejected/withdrawn/expired works where implemented
* contact privacy respected
* no unauthorized feed data leak

---

## 24. Leads CRM Manual Verification

Leads/CRM phases must check:

* inquiry creates lead
* duplicate inquiry protection works
* contact reveal creates/reuses lead as intended
* lead source tracked
* lead receiver sees only their leads
* lead sender privacy respected
* lead statuses work:

  * New
  * Contacted
  * Interested
  * Follow-up
  * Site Visit
  * Converted
  * Lost
  * Closed
* lead notes private
* tags work
* follow-up date/reminder works
* duplicate merge works where implemented
* builder lead assignment works
* builder round-robin works where implemented
* agent sees only assigned leads
* lead transfer/reassignment audited
* consent log exists
* DND/do-not-contact respected where implemented
* lead abuse/spam protection works
* lead analytics real only
* no fake lead count

---

## 25. Site Visit Manual Verification

Site visit phases must check:

* request flow works
* receiver approval works
* reschedule works
* cancellation reason required
* calendar view works
* reminder works or setup-required shown
* no-show status works where implemented
* completed status works
* feedback form works where implemented
* safety notice shown
* site visit does not imply deal confirmation
* notifications/deep links work
* CRM integration works
* privacy respected
* role access respected

---

## 26. Messaging Manual Verification

Messaging phases must check:

* inbox loads
* lead-based thread works
* proposal-based thread works
* requirement-based thread works
* unread count real
* notifications real
* participants only can read thread
* wrong user denied
* wrong role denied
* report/block works where implemented
* attachments safe where implemented
* attachment upload scans/validates where implemented
* archive works
* retry/failure state works
* no fake sent status for external providers
* messaging legal warning shown
* mobile thread UI usable

---

## 27. Profile And Agent Manual Verification

Profile phases must check:

* profile page loads role-wise
* profile image upload/crop/remove works or setup-required shown
* owner privacy safe
* broker profile fields work
* builder profile fields work
* office address fields work
* public broker profile safe
* public builder profile safe
* public microsite safe
* profile completion score real
* public profile SEO safe
* claim/report profile works where implemented
* role change request works
* role change warning shown
* role change requires approval
* builder can invite agents
* agent invite expiry works
* agent permissions work
* agent cannot access unassigned data
* agent removal impact handled
* agent seat limit plan gate works

---

## 28. Verification And Trust Manual Verification

Verification phases must check:

* owner verification where enabled
* broker verification
* builder verification
* business profile verification
* role change verification
* property/project/requirement verification where enabled
* document upload private
* document access permission enforced
* document access logged
* verification status lifecycle works:

  * not submitted
  * draft
  * submitted
  * under review
  * need changes
  * rejected
  * approved
  * revoked
  * expired where applicable
* need changes reason visible
* rejection reason visible
* approval audit exists
* verified badge appears only after real approval
* fake badge blocked
* verification legal disclaimer shown
* false document warning shown
* sensitive document masking/restriction works
* RERA status/recheck rules tracked

---

## 29. Admin / Staff Manual Verification

Admin/staff phases must check:

* admin login separate
* admin URL noindex
* no public staff create account
* staff invite-only
* Super Admin sees all modules
* Admin sees assigned modules
* staff sees only permitted modules
* wrong staff role denied direct URL
* every admin row clickable
* detail preview/drawer/page works
* related data visible where allowed:

  * user
  * property
  * project
  * requirement
  * leads
  * payments
  * billing
  * verification
  * reports
  * actions
  * logs
  * timeline
* admin notes internal only
* public preview link works safely
* moderation queue ownership/locking works where implemented
* reason mandatory on reject/need changes
* audit logs created
* sensitive data permission enforced
* private document permission enforced
* export permission enforced
* bulk action preview/confirmation works
* Super Admin override audited
* admin mobile layout works
* admin tables become cards on mobile
* no fake admin metrics

---

## 30. Billing / Payment / GST / Trial Manual Verification

Billing/payment phases must check:

### Plan And Subscription

* pricing page real
* role-based plans
* plan limits correct
* active plan required before posting where required
* subscription popup clear
* upgrade/downgrade rules work
* downgrade impact warning shown
* usage meters real
* plan expiry state works
* grace period rules work where implemented
* no fake active plan

### Razorpay Payment

* order creation works
* checkout opens
* callback handles safe state
* webhook signature verification implemented/tested or setup-required documented
* failed payment state safe
* pending payment state safe
* success only after verified payment/webhook
* duplicate payment handled
* no fake payment success
* no test payment in production
* no payment secret exposed

### Invoice / GST

* invoice generated only after verified success
* sequential invoice number correct
* failed payment does not waste invoice number
* invoice download permission works
* invoice email setup-required or works
* billing address works
* GSTIN optional
* GSTIN validation works
* B2B/B2C logic works
* CGST/SGST/IGST split works where configured
* credit/debit note rules tracked
* custom billing edits audited

### Free Trial

* Super Admin controls trial
* role/user/city targeting works
* trial activation real
* trial expiry works
* trial abuse detection tracked
* trial legal notice shown
* no auto-charge unless clearly disclosed
* no fake trial active state

Payment failure is phase-blocking if payment is in scope.

---

## 31. Ads / Promotion Manual Verification

Ads phases must check:

* builder ads module accessible only to builder/allowed admin
* builder selects own approved/published project
* desktop/tablet/mobile banner upload works or setup-required shown
* image ratio/pixel hints shown
* city targeting required
* all Gujarat option works
* selected multiple city targeting works
* ad policy accepted
* RERA ad compliance checked where applicable
* submit for approval works
* admin approve/reject/need changes works
* reason required on reject/need changes
* builder/admin pause/edit/update/delete works
* unapproved/unpaid/expired ad not shown
* sponsored/ad label visible
* city/IP targeting works or setup-required shown
* nearby city fallback works where implemented
* impressions/clicks real only
* no fake ad analytics
* ad fraud click protection tracked
* ad expiry notification works or setup-required shown

---

## 32. Notifications Manual Verification

Notification phases must check:

* bell/icon visible for logged-in users
* unread badge count real
* no fake badge
* dropdown/popup opens desktop
* bottom sheet/full-screen drawer works mobile
* latest list shows real notifications
* notification item clickable
* redirect/deep link works
* notification marks read on click
* unread count decreases
* mark all as read works
* empty state works
* fallback route works if deep link missing
* owner notifications correct
* broker notifications correct
* builder notifications correct
* admin notifications correct
* templates safe
* preferences work
* delivery logs real
* failed delivery retry setup-required/provider checked
* no fake sent status for Email/SMS/WhatsApp
* digest/quiet hours tracked where implemented

---

## 33. Search / Location Manual Verification

Search/location phases must check:

* homepage search routes to `/search`
* search query params persist
* URL state works
* filters work:

  * purpose
  * type
  * budget
  * BHK/unit
  * area
  * locality
  * sort
* filter chips work
* clear filters work
* mobile filter bottom sheet works
* mobile sort bottom sheet works
* infinite scroll/page query works
* pagination/load more works
* empty state works
* no fake result count
* map toggle works only if maps configured
* map fallback works if not configured
* sponsored/organic separated
* saved search works
* saved search alerts work or setup-required shown
* recently viewed works
* guest local history sync works on login where implemented
* search scraping/rate limit tracked
* Gujarat location hierarchy works
* cascading dropdowns work
* missing location request works
* admin missing location approval works
* city selector works
* manual city override works
* pin code/city/taluka mismatch validation works
* transliteration/Gujarati/Hindi search works where implemented
* no private data leaks in search response

---

## 34. SEO / CMS / Blog / Legal Manual Verification

SEO/CMS/legal phases must check:

* public pages have title/meta/canonical
* H1 exists
* intro content exists where relevant
* sitemap includes useful pages only
* empty/thin pages noindex/hidden
* admin/staff pages noindex
* robots.txt blocks appropriate paths
* schema valid and safe
* no hidden phone/private data in schema/meta
* no fake city/listing count
* no false “No.1”, “100% verified”, “guaranteed” claims
* city pages real-data based
* locality pages real-data based
* property type pages real-data based
* detail page SEO safe
* blog category/tag/slug/meta/featured image/publish status works
* CMS draft/publish/preview works
* legal pages exist:

  * Terms & Conditions
  * Privacy Policy
  * Cookie Policy
  * Refund Policy
  * Cancellation Policy
  * Listing Policy
  * Advertising Policy
  * Verification Policy
  * Payment Policy
  * Disclaimer
  * Grievance/Support Policy
* footer legal links visible
* register Terms/Privacy checkbox present
* important paid action terms notice present
* listing/project/requirement legal warnings present
* RERA disclaimer present
* lead/contact sharing consent present
* final legal text marked `NEEDS_LEGAL_REVIEW` until lawyer/human approved

---

## 35. Media / Upload / Storage Manual Verification

Media phases must check:

* allowed image formats validate
* unsafe file formats blocked
* file size validation works
* corrupt file handled safely
* upload progress shown
* retry on failure works
* failed upload cleanup tracked
* public image bucket only for public files
* private documents in private/signed access
* no private file public URL leak
* image converts to WebP/AVIF where supported or setup-required tracked
* original stored where defined
* multiple image sizes generated where implemented
* lazy loading works
* dimensions reserved to avoid CLS
* image safe crop/no stretch
* cover image selection works
* image reorder safe
* image drag disabled where needed
* PDF brochure stored as PDF
* PDF preview/download permission works
* floor plan section works
* video one-upload rule works
* video thumbnail/compression works or setup-required shown
* 360° embed URL safe
* EXIF removal works or setup-required tracked
* SVG security works
* HEIC/HEIF fallback works
* orphan cleanup job tracked
* CDN cache purge works or setup-required tracked

---

## 36. Security / Privacy / Fraud Manual Verification

Security phases must check:

* RLS enabled on sensitive tables
* public-safe views do not leak private fields
* server-side authorization exists
* frontend-only protection is not used alone
* service role not exposed
* secrets not in client/docs/logs
* inputs validated
* safe errors
* logs redacted
* rate limits work
* OTP cost protection works
* contact reveal abuse protection works
* search scraping protection works
* payment webhook signature verification works
* CSRF protection where required
* XSS protection
* SSRF protection for external URLs/embeds
* CORS safe
* bot protection/Turnstile feature flag works where implemented
* staff high-risk action confirmation works
* sensitive data permission works
* consent logs work
* Terms/Privacy/cookie preferences work
* marketing opt-out works where implemented
* data export/delete request works where implemented
* legal hold works where implemented
* report flows work:

  * property
  * project
  * profile
  * requirement
  * proposal
  * banner ad
* fake report prevention tracked
* appeal system tracked where implemented
* account suspension/ban rules work
* session revoke on ban works
* UGC moderation works where implemented

---

## 37. Audit / Soft Delete Manual Verification

Audit/soft delete phases must check:

* audit log created for admin actions
* audit log created for staff actions
* audit log created for manual billing/payment actions
* audit log created for verification actions
* audit log created for provider setting changes
* audit log created for role/permission changes
* audit log created for delete/restore/hard delete actions
* reason required for high-risk actions
* audit logs not editable/deletable by normal staff
* soft delete default for listings/leads/important data
* restore works where implemented
* hard delete Super Admin only after retention/approval
* retention policy tracked
* recycle bin/trash works where implemented
* cron cleanup tracked
* private media/orphan cleanup tracked

---

## 38. Performance Manual Verification

Performance phases must check:

* no unbounded DB reads
* no N+1 queries
* lists/tables paginated
* search paginated/infinite load
* admin large tables paginated
* indexes created where needed
* slow queries reviewed
* public pages cached safely
* revalidateTag/revalidatePath targeted
* no full-site unnecessary revalidation
* images optimized/lazy/responsive
* bundle size acceptable
* third-party scripts limited
* font loading avoids CLS
* heavy jobs in background
* provider failures graceful
* mobile loading smooth
* no layout freeze
* Core Web Vitals target tracked:

  * LCP <= 2.5s
  * INP <= 200ms
  * CLS <= 0.1
* load/stress test before launch
* 1 lakh live user target considered

Performance fixes must not break:

* security
* RLS
* role permissions
* contact privacy
* manual verification
* docs
* rollback safety

---

## 39. Deployment / Rollback Manual Verification

Deployment phases must check:

* code backup done
* DB backup done
* storage backup needed/done
* migration reviewed
* rollback notes present
* feature flags reviewed
* build/type/lint/tests pass
* auth/RLS/security checked
* provider impact checked
* payment/contact privacy checked
* responsive checked
* changelog updated
* feature registry updated
* deployment version recorded
* smoke test passed
* production env safe
* dev OTP disabled
* test payment disabled
* mock providers disabled
* demo data removed/hidden after approval
* secrets server-only
* rollback path tested or documented
* maintenance mode ready
* incident/monitoring ready
* final signoffs captured

Rollback verification must check:

* code rollback successful
* DB rollback/restore safe
* feature flag kill switch used where needed
* user data preserved
* payment/subscription data safe
* post-rollback smoke test passed
* rollback logged in `CHANGELOG.md`
* rollback logged in `DEPLOYMENT_ROLLBACK.md`

---

## 40. Production Launch Verification

Production launch cannot pass until all launch blockers are resolved.

### 40.1 Production Security Checks

| Check                             | Required Result |
| --------------------------------- | --------------- |
| Service role key not in client    | PASS            |
| RLS final pass                    | PASS            |
| Hidden contact not leaked         | PASS            |
| Private documents private         | PASS            |
| Admin/staff public access blocked | PASS            |
| Direct URL bypass blocked         | PASS            |
| Webhook signatures verified       | PASS            |
| Rate limits active                | PASS            |
| Safe errors only                  | PASS            |
| Logs redacted                     | PASS            |
| Security headers configured       | PASS            |
| Test/mock providers disabled      | PASS            |

### 40.2 Production Payment Checks

| Check                                  | Required Result                            |
| -------------------------------------- | ------------------------------------------ |
| Razorpay live mode configured          | PASS or SETUP_REQUIRED if payment not live |
| Test payment disabled                  | PASS                                       |
| Webhook verified                       | PASS                                       |
| Failed payment does not activate plan  | PASS                                       |
| Pending payment does not activate plan | PASS                                       |
| Invoice only after verified payment    | PASS                                       |
| Invoice sequence correct               | PASS                                       |
| Manual activation audited              | PASS                                       |
| Refund rules documented                | PASS/PARTIAL with approval                 |

### 40.3 Production Provider Checks

| Provider          | Required Result                                   |
| ----------------- | ------------------------------------------------- |
| Supabase Auth     | PASS                                              |
| Supabase DB       | PASS                                              |
| Supabase RLS      | PASS                                              |
| OTP provider      | PASS or explicitly SETUP_REQUIRED if not launched |
| Razorpay          | PASS or explicitly SETUP_REQUIRED if not launched |
| Email             | PASS or SETUP_REQUIRED                            |
| SMS               | PASS or SETUP_REQUIRED                            |
| WhatsApp          | PASS or SETUP_REQUIRED                            |
| Google Maps       | PASS or SETUP_REQUIRED                            |
| Cloudflare R2/CDN | PASS or SETUP_REQUIRED                            |
| Analytics         | PASS or SETUP_REQUIRED                            |
| Error tracking    | PASS or SETUP_REQUIRED                            |

Provider-backed feature cannot fake success.

### 40.4 Production UI Checks

| Check                           | Required Result |
| ------------------------------- | --------------- |
| Homepage works                  | PASS            |
| Search works                    | PASS            |
| Detail pages work               | PASS            |
| Login/register works            | PASS            |
| Dashboards work                 | PASS            |
| Admin panel works               | PASS            |
| Required responsive widths pass | PASS            |
| No horizontal scroll            | PASS            |
| No overlap                      | PASS            |
| Brand no-wrap                   | PASS            |
| No dead primary CTAs            | PASS            |
| Loading/empty/error states      | PASS            |
| Footer rules correct            | PASS            |

### 40.5 Production SEO/Legal Checks

| Check                                         | Required Result                          |
| --------------------------------------------- | ---------------------------------------- |
| Legal pages exist                             | PASS                                     |
| Terms/Privacy consent exists                  | PASS                                     |
| Cookie policy/preference exists where needed  | PASS                                     |
| Sitemap safe                                  | PASS                                     |
| Admin routes noindex                          | PASS                                     |
| Empty/thin pages noindex/hidden               | PASS                                     |
| No fake counts/claims                         | PASS                                     |
| Schema safe                                   | PASS                                     |
| Legal content reviewed or marked NEEDS_REVIEW | PASS/NEEDS_REVIEW with explicit approval |

### 40.6 Production Data Checks

| Check                                        | Required Result |
| -------------------------------------------- | --------------- |
| Demo/test data removed/hidden after approval | PASS            |
| Seed data flagged                            | PASS            |
| No fake public listings/counts               | PASS            |
| Soft delete works                            | PASS            |
| Backup done                                  | PASS            |
| Rollback ready                               | PASS            |
| Audit logs working                           | PASS            |

---

## 41. Phase-Specific Verification Index

Future phase manual verification prompts must map to this file.

### Phase 01 — Project Setup Baseline

Must verify:

* project installs
* lint/type/build runs
* docs exist
* root routes load
* environment structure safe
* no secrets exposed
* no unrelated files changed
* `brain.md`, `FEATURE_REGISTRY.md`, `CHANGELOG.md`, `MANUAL_VERIFICATION.md` updated

### Phase 02 — Auth Roles RLS Foundation

Must verify:

* public auth
* admin/staff auth separation
* role selection
* protected routes
* RLS base
* direct URL bypass blocked
* no service role client leak
* session/logout
* wrong role denied

### Phase 03 — Public UI Home Header Footer Hero

Must verify:

* homepage
* old hero migration if requested
* header role-wise
* brand no-wrap
* city selector
* footer public-only
* no horizontal scroll
* responsive sizes
* search routes to `/search`
* no dead buttons

### Phase 04 — Property Project Requirement System

Must verify:

* property post owner/broker
* project post builder
* requirement post owner/broker
* conditional fields
* media/setup-required
* approval workflows
* edit reapproval
* contact privacy
* legal warnings

### Phase 05 — Public Search Detail Profile SEO

Must verify:

* search filters
* URL query state
* result cards
* detail pages
* profiles
* contact privacy
* SEO metadata
* no fake counts
* responsive

### Phase 06 — Owner Broker Builder Dashboards

Must verify:

* owner dashboard
* broker dashboard
* builder dashboard
* dashboard modules
* role gates
* analytics real/empty/setup-required
* notifications
* mobile dashboard

### Phase 07 — Admin Staff Super Admin System

Must verify:

* admin login
* Super Admin all modules
* staff permissions
* queues
* detail drawers
* audit logs
* sensitive permission
* mobile admin
* direct URL deny

### Phase 08 — Leads CRM Requirements Proposals Messages

Must verify:

* leads
* inquiries
* contact reveal
* proposals
* messages
* site visits
* follow-ups
* duplicate/spam protection
* notifications
* role access

### Phase 09 — Billing Payment Subscription Trial GST

Must verify:

* plans
* plan gates
* checkout
* Razorpay setup-required/real test
* webhook
* failed/pending/success states
* invoices
* GST
* trials
* billing dashboard

### Phase 10 — Media Storage Uploads R2 CDN

Must verify:

* image upload
* PDF upload
* video/floor plans
* private documents
* Cloudflare R2/CDN
* variants
* signed URLs
* upload failure/retry
* orphan cleanup tracked

### Phase 11 — Location Search SEO CMS Legal

Must verify:

* Gujarat location data
* city/locality search
* SEO pages
* CMS pages
* legal pages
* sitemap/noindex/robots
* blog
* consent notices

### Phase 12 — Ads Promotion Notifications Providers

Must verify:

* builder ads
* city targeting
* approval
* sponsored label
* notifications
* provider status
* setup-required states
* no fake sent/active/provider status

### Phase 13 — Security Privacy Fraud Rate Limits

Must verify:

* RLS final pass
* privacy/consent
* reports/fraud
* rate limits
* Turnstile feature flag
* audit logs
* data export/delete
* security headers/errors/log redaction

### Phase 14 — Performance Caching Deployment Launch

Must verify:

* pagination
* indexes
* caching
* image optimization
* background jobs
* Core Web Vitals tracking
* load/stress readiness
* deployment/backup/rollback

### Phase 15 — Final Production API Testing And Signoff

Must verify:

* production provider modes
* real OTP/payment/email/media/maps where launched
* test/dev/mock disabled
* final RLS
* final responsive
* final SEO/legal
* final backup/rollback
* final Super Admin signoff

---

## 42. Current Manual Verification Status

No actual website implementation has started yet.

Current status:

| Area                     | Manual Verification Status |
| ------------------------ | -------------------------- |
| Documentation generation | IN_PROGRESS                |
| Project setup            | NOT_STARTED                |
| Auth/RBAC/RLS            | NOT_STARTED                |
| Public UI                | NOT_STARTED                |
| Dashboards               | NOT_STARTED                |
| Admin/staff              | NOT_STARTED                |
| Property module          | NOT_STARTED                |
| Project module           | NOT_STARTED                |
| Requirement/proposals    | NOT_STARTED                |
| Leads CRM                | NOT_STARTED                |
| Messaging                | NOT_STARTED                |
| Billing/payment          | SETUP_REQUIRED             |
| Media/storage            | SETUP_REQUIRED             |
| Search/location          | NOT_STARTED                |
| SEO/CMS/legal            | NOT_STARTED                |
| Ads/promotions           | NOT_STARTED                |
| Notifications            | NOT_STARTED                |
| Security/privacy/fraud   | NOT_STARTED                |
| Performance/deployment   | NOT_STARTED                |
| Production readiness     | NOT_STARTED                |

---

## 43. Current Documentation File Verification

## DOC-01 — `CLAUDE.md` Verification

### File

* `CLAUDE.md`

### Verification Date

* Date: 2026-06-29
* Verified by: Pending human/manual review

### Checks

| Check                            | Result             | Notes                                                          |
| -------------------------------- | ------------------ | -------------------------------------------------------------- |
| File created                     | PASS               | File content generated                                         |
| Scope covered                    | PARTIAL            | Global short rules covered; full detail spread into later docs |
| No contradiction found           | NEEDS_MANUAL_CHECK | Human review required                                          |
| Next file mentioned              | PASS               | Next file was `brain.md`                                       |
| Changelog update required        | PASS               | Entry included in `CHANGELOG.md`                               |
| Feature Registry update required | PASS               | `DOC-001` tracked                                              |
| Brain update required            | PASS               | `brain.md` generated after this                                |

### Final Result

PARTIAL

### Notes

* Documentation-only verification.
* Mark final PASS after full docs pack is reviewed.

---

## DOC-02 — `brain.md` Verification

### File

* `brain.md`

### Verification Date

* Date: 2026-06-29
* Verified by: Pending human/manual review

### Checks

| Check                            | Result             | Notes                                                |
| -------------------------------- | ------------------ | ---------------------------------------------------- |
| File created                     | PASS               | File content generated                               |
| Scope covered                    | PARTIAL            | Project memory structure created; must keep updating |
| No contradiction found           | NEEDS_MANUAL_CHECK | Human review required                                |
| Next file mentioned              | PASS               | Next file was `FEATURE_REGISTRY.md`                  |
| Changelog update required        | PASS               | Entry included in `CHANGELOG.md`                     |
| Feature Registry update required | PASS               | `DOC-002` tracked                                    |
| Brain update required            | PASS               | This file itself is memory baseline                  |

### Final Result

PARTIAL

### Notes

* Must be updated after every future phase.

---

## DOC-03 — `FEATURE_REGISTRY.md` Verification

### File

* `FEATURE_REGISTRY.md`

### Verification Date

* Date: 2026-06-29
* Verified by: Pending human/manual review

### Checks

| Check                            | Result             | Notes                                                   |
| -------------------------------- | ------------------ | ------------------------------------------------------- |
| File created                     | PASS               | File content generated                                  |
| Scope covered                    | PARTIAL            | Large registry created; must be maintained and reviewed |
| No contradiction found           | NEEDS_MANUAL_CHECK | Human review required                                   |
| Next file mentioned              | PASS               | Next file was `CHANGELOG.md`                            |
| Changelog update required        | PASS               | Entry included in `CHANGELOG.md`                        |
| Feature Registry update required | PASS               | Registry file itself tracks docs/features               |
| Brain update required            | PARTIAL            | Brain should update progress after acceptance           |

### Final Result

PARTIAL

### Notes

* Must be updated after every future phase.
* Features remain baseline statuses until implementation begins.

---

## DOC-04 — `CHANGELOG.md` Verification

### File

* `CHANGELOG.md`

### Verification Date

* Date: 2026-06-29
* Verified by: Pending human/manual review

### Checks

| Check                            | Result             | Notes                                                     |
| -------------------------------- | ------------------ | --------------------------------------------------------- |
| File created                     | PASS               | File content generated                                    |
| Scope covered                    | PASS               | Changelog rules and initial entries included              |
| No contradiction found           | NEEDS_MANUAL_CHECK | Human review required                                     |
| Next file mentioned              | PASS               | Next file was `BUGS_AND_FIXES.md`                         |
| Changelog update required        | PASS               | This file itself includes current entries                 |
| Feature Registry update required | PASS               | `DOC-004` should be marked done after acceptance          |
| Brain update required            | PARTIAL            | Brain should update generated file count after acceptance |

### Final Result

PARTIAL

### Notes

* Documentation-only verification.
* Full project verification pending.

---

## DOC-05 — `BUGS_AND_FIXES.md` Verification

### File

* `BUGS_AND_FIXES.md`

### Verification Date

* Date: 2026-06-29
* Verified by: Pending human/manual review

### Checks

| Check                            | Result             | Notes                                                      |
| -------------------------------- | ------------------ | ---------------------------------------------------------- |
| File created                     | PASS               | File content generated                                     |
| Scope covered                    | PASS               | Bug/fix/retest/workaround rules included                   |
| No contradiction found           | NEEDS_MANUAL_CHECK | Human review required                                      |
| Next file mentioned              | PASS               | Next file was `MANUAL_VERIFICATION.md`                     |
| Changelog update required        | PARTIAL            | `CHANGELOG.md` should be updated after this file is copied |
| Feature Registry update required | PASS               | `DOC-005` should be marked done after acceptance           |
| Brain update required            | PARTIAL            | Brain should update generated file count after acceptance  |

### Final Result

PARTIAL

### Notes

* Documentation-only verification.
* Current open docs-generation risks are tracked.

---

## DOC-06 — `MANUAL_VERIFICATION.md` Verification

### File

* `MANUAL_VERIFICATION.md`

### Verification Date

* Date: 2026-06-29
* Verified by: Pending human/manual review

### Checks

| Check                            | Result             | Notes                                                                                                                                 |
| -------------------------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| File created                     | PASS               | File content generated                                                                                                                |
| Scope covered                    | PASS               | Manual verification system, role checks, RLS, responsive, provider, payment, admin, SEO, media, deployment and production QA included |
| No contradiction found           | NEEDS_MANUAL_CHECK | Human review required                                                                                                                 |
| Next file mentioned              | PASS               | Next file is `API_PROVIDER_STATUS.md`                                                                                                 |
| Changelog update required        | PARTIAL            | `CHANGELOG.md` must be updated after acceptance                                                                                       |
| Feature Registry update required | PASS               | `DOC-006` should be marked done after acceptance                                                                                      |
| Brain update required            | PARTIAL            | Brain should update generated file count after acceptance                                                                             |

### Final Result

PARTIAL

### Notes

* This is documentation-only verification.
* Final PASS requires full documentation pack review and later real implementation verification.

---

## 44. Current Open Verification Blockers

| Blocker ID   | Area                         | Status         | Required Action                                 |
| ------------ | ---------------------------- | -------------- | ----------------------------------------------- |
| MV-BLOCK-001 | Full documentation pack      | PARTIAL        | Continue generating remaining docs              |
| MV-BLOCK-002 | Prompt pack                  | NOT_STARTED    | Generate prompt files after detailed docs       |
| MV-BLOCK-003 | Website implementation       | NOT_STARTED    | Start Phase 01 after docs/prompts               |
| MV-BLOCK-004 | Real providers               | SETUP_REQUIRED | Configure and test providers in provider phases |
| MV-BLOCK-005 | RLS/security implementation  | NOT_STARTED    | Implement and test in architecture/auth phases  |
| MV-BLOCK-006 | Responsive UI implementation | NOT_STARTED    | Implement and test in UI phases                 |
| MV-BLOCK-007 | Production readiness         | NOT_STARTED    | Run final production verification later         |

---

## 45. Bug Creation Rule During Verification

If any check fails, Claude must:

1. create bug entry in `BUGS_AND_FIXES.md`
2. assign severity and priority
3. document reproduction steps
4. fix the bug if in current scope
5. update changed files
6. rerun relevant verification
7. update `MANUAL_VERIFICATION.md`
8. update `CHANGELOG.md`
9. update `FEATURE_REGISTRY.md`
10. update `brain.md`
11. only mark PASS after retest passes

If bug remains:

* mark phase `PARTIAL`, `BLOCKED` or `FAIL`
* do not hide the issue

---

## 46. Verification Final Response Format

After every verification run, Claude final response must include:

```md id="vp986x"
## Verification Result
PASS / PARTIAL / BLOCKED / FAIL

## Scope Checked
- phase/module checked

## Checks Run
- lint:
- typecheck:
- build:
- tests:
- manual checks:

## Role Checks
- Guest:
- Owner:
- Broker:
- Builder:
- Super Admin:
- Admin:
- Staff:

## Security / RLS
- result:

## Responsive
- 320:
- 360:
- 390:
- 430:
- 768:
- 1024:
- 1366:

## Bugs Found
- Bug IDs or None

## Fixes Done
- Bug IDs or None

## Docs Updated
- MANUAL_VERIFICATION.md
- BUGS_AND_FIXES.md
- FEATURE_REGISTRY.md
- CHANGELOG.md
- brain.md

## Pending Issues
- issue or None

## Next Phase
- next prompt path
```

Do not write “all good” without details.

---

## 47. Human Manual Verification Notes Format

When the user or human tester manually checks the website, notes should be added like this:

```md id="wjdbny"
## HUMAN-CHECK-YYYYMMDD-000 — Short Title

### Tester
- Name:
- Role:

### Environment
- URL:
- Device:
- Browser:
- Screen size:
- Login role:

### Checked Flow
- Flow:

### Expected
- Expected result:

### Actual
- Actual result:

### Screenshots / Evidence
- File/path/link:

### Result
PASS / PARTIAL / BLOCKED / FAIL

### Bug Created
- BUG ID or None

### Notes
-
```

Human notes are valid verification evidence.

---

## 48. Evidence Rules

Allowed evidence:

* screenshot path
* video path
* route path
* browser/device
* screen size
* exact safe error text
* relevant log excerpt
* SQL/migration filename
* test command output summary
* redacted provider event ID
* redacted payment order ID

Do not include:

* OTP
* password
* access token
* refresh token
* API key
* service role key
* Razorpay secret
* provider secret
* private document URL
* full hidden contact list
* full private user data
* raw database credentials
* long logs

Only include relevant 20–30 lines of logs if needed.

---

## 49. Required Docs Update Verification

Before phase final answer, verify docs:

| Doc                         | Required Update Condition                       |
| --------------------------- | ----------------------------------------------- |
| `brain.md`                  | Every phase                                     |
| `FEATURE_REGISTRY.md`       | Every feature/status/QA change                  |
| `CHANGELOG.md`              | Every completed change                          |
| `BUGS_AND_FIXES.md`         | Every bug/fix/workaround                        |
| `MANUAL_VERIFICATION.md`    | Every verification                              |
| `API_PROVIDER_STATUS.md`    | Provider/API changes                            |
| `DEPLOYMENT_ROLLBACK.md`    | Deployment/migration/backup/rollback changes    |
| `SECURITY_RLS_CHECKLIST.md` | Auth/RLS/security/privacy/admin/contact changes |
| `PERFORMANCE_CHECKLIST.md`  | Performance/cache/query/image/load changes      |
| detailed docs               | Requirement/behavior/rule changes               |

If docs are not updated, final verification cannot be `PASS`.

---

## 50. Final Phase PASS Checklist

Before marking any phase `PASS`, Claude must answer yes to all relevant items:

* [ ] Relevant docs were read.
* [ ] Existing files/routes/components/tables/RLS were inspected.
* [ ] No duplicate/conflicting implementation added.
* [ ] Existing working features were not removed.
* [ ] Changed files are listed.
* [ ] SQL/migration files are listed or `None`.
* [ ] DB/RLS changes have migration files.
* [ ] RLS was tested where relevant.
* [ ] Role access was tested.
* [ ] Direct URL bypass was tested where relevant.
* [ ] Hidden contact privacy was tested where relevant.
* [ ] Private document privacy was tested where relevant.
* [ ] Provider states were tested or marked setup-required.
* [ ] Payment states were tested where relevant.
* [ ] UI states were tested.
* [ ] Responsive widths were checked.
* [ ] No horizontal scroll.
* [ ] No overlap.
* [ ] No critical text wrap issue.
* [ ] No dead primary CTA.
* [ ] No `href="#"`.
* [ ] Lint passed or reason documented.
* [ ] Typecheck passed or reason documented.
* [ ] Build passed or reason documented.
* [ ] Tests passed or reason documented.
* [ ] Bugs are tracked.
* [ ] Blocking bugs fixed/retested.
* [ ] `brain.md` updated.
* [ ] `FEATURE_REGISTRY.md` updated.
* [ ] `CHANGELOG.md` updated.
* [ ] `BUGS_AND_FIXES.md` updated if needed.
* [ ] `MANUAL_VERIFICATION.md` updated.
* [ ] Other relevant docs updated.
* [ ] Pending issues honestly listed.
* [ ] Next phase listed.
* [ ] No fake completion.
* [ ] No secrets exposed.

If any required item is no, final result is not `PASS`.

---

## 51. Final Rule

Manual verification is not optional.

Fix errors first, then mark `PASS`.

If not fully passed, mark `PARTIAL`, `BLOCKED` or `FAIL` with exact reason.

Do not continue to next phase unless:

1. current phase is `PASS`, or
2. user explicitly approves moving ahead with tracked `PARTIAL` or `BLOCKED`.

Nothing should be skipped, hidden or faked.
