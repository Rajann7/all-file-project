# MY GUJARAT PROPERTY

# FEATURE REGISTRY TEMPLATE — NO SKIP, NO FAKE, QA TRACKING SYSTEM

## FILE NAME

`21_FEATURE_REGISTRY_TEMPLATE.md`

---

# 1. DOCUMENT PURPOSE

This document defines the **Feature Registry Template** for My Gujarat Property.

The Feature Registry is a mandatory tracking file that records every feature, page, role, permission, database table, route, provider dependency, feature flag, UI state and verification status.

This file must be maintained during development so that Claude/AI/developer does not skip important features, does not create fake UI and does not lose track between phases.

The Feature Registry helps track:

* What is planned
* What is built
* What is pending
* What is blocked
* What is fake/demo only
* What is production ready
* What needs verification
* What passed manual QA
* What failed manual QA
* What needs auto-fix
* What depends on providers
* What depends on database/RLS
* What depends on admin settings
* What depends on subscription/payment
* What depends on feature flags

---

# 2. CORE RULE

Every major feature must have a registry entry.

If a feature is visible in UI, it must be in the registry.

If a feature has a route, it must be in the registry.

If a feature has a database table, it must be in the registry.

If a feature has a provider dependency, it must be in the registry.

If a feature is not implemented, it must not appear as working production UI.

---

# 3. FEATURE REGISTRY LOCATION

Recommended file location:

```txt id="qzmq8e"
docs/21_FEATURE_REGISTRY_TEMPLATE.md
```

or:

```txt id="kz4rvg"
docs/FEATURE_REGISTRY.md
```

Claude should update this file after every development phase.

---

# 4. FEATURE STATUS VALUES

Use these exact status values:

```txt id="jzq31q"
PLANNED
IN_PROGRESS
PARTIAL
BLOCKED
READY_FOR_QA
PASS
FAIL
DEFERRED
DISABLED
REMOVED
```

Status meaning:

## PLANNED

Feature is documented but not started.

## IN_PROGRESS

Feature is being built.

## PARTIAL

Feature is partially built but not complete.

## BLOCKED

Feature cannot be completed due to missing dependency.

## READY_FOR_QA

Feature is built and ready for manual verification.

## PASS

Feature passed manual verification.

## FAIL

Feature failed manual verification.

## DEFERRED

Feature intentionally postponed.

## DISABLED

Feature exists but is disabled by feature flag/admin setting.

## REMOVED

Feature was removed and should not appear in UI.

---

# 5. PRODUCTION READINESS VALUES

Use these values:

```txt id="lac4jv"
DEV_ONLY
TEST_READY
QA_READY
PRODUCTION_READY
NOT_READY
```

## DEV_ONLY

Allowed only in development.

## TEST_READY

Feature can be tested but not production ready.

## QA_READY

Feature ready for formal QA.

## PRODUCTION_READY

Feature safe for production.

## NOT_READY

Feature incomplete or blocked.

---

# 6. FAKE / DEMO DATA VALUES

Use these values:

```txt id="rvxma2"
NO_FAKE
DEV_DEMO_ONLY
FAKE_UI_FOUND
FAKE_DATA_FOUND
PLACEHOLDER_ONLY
REMOVED_FAKE
```

Rules:

* Production features must be `NO_FAKE`.
* Demo data must be `DEV_DEMO_ONLY`.
* If fake UI found, mark `FAKE_UI_FOUND`.
* If fake data found, mark `FAKE_DATA_FOUND`.
* Placeholder features must not look production-ready.
* After removing fake UI/data, mark `REMOVED_FAKE`.

---

# 7. FEATURE PRIORITY VALUES

Use these values:

```txt id="dsplvq"
P0_CRITICAL
P1_HIGH
P2_MEDIUM
P3_LOW
FUTURE
```

## P0_CRITICAL

Required for launch/core safety.

## P1_HIGH

Important for launch but not security-critical.

## P2_MEDIUM

Useful after core launch.

## P3_LOW

Nice-to-have.

## FUTURE

Advanced feature for later.

---

# 8. FEATURE TYPE VALUES

Feature types:

```txt id="ob58yb"
PAGE
COMPONENT
FLOW
API
DATABASE
STORAGE
AUTH
RBAC
RLS
ADMIN
DASHBOARD
PAYMENT
PROVIDER
SEO
CMS
NOTIFICATION
AUTOMATION
SECURITY
QA
```

A feature can have multiple types.

---

# 9. FEATURE OWNER / ROLE SCOPE VALUES

Role scope can include:

* Guest
* Buyer
* Tenant
* Investor
* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Developer
* Real Estate Group
* Support Executive
* Moderator
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager
* Admin
* Super Admin

Every feature should define who can access it.

---

# 10. MASTER FEATURE REGISTRY TABLE TEMPLATE

Use this table format for every feature.

```md id="dmjbyg"
| ID | Feature | Module | Type | Priority | Status | Production Readiness | Fake/Data Status | Roles | Routes | Feature Flag | DB Tables | RLS Needed | Provider Dependency | Admin Control | QA Status | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F-001 | Login/Register OTP Modal | Auth | FLOW | P0_CRITICAL | PLANNED | NOT_READY | NO_FAKE | Guest, User | /login, modal | auth.otp.enabled | profiles, user_roles | Yes | OTP Provider | Yes | NOT_TESTED | Login/register in same popup |
```

This table should be updated phase by phase.

---

# 11. DETAILED FEATURE ENTRY TEMPLATE

For complex features, use detailed entry.

```md id="cqdg1p"
## FEATURE ID: F-XXX

### Feature Name
[Feature name]

### Module
[Auth / Search / Property / Requirement / Dashboard / Admin / Payment / Provider / CMS / etc.]

### Priority
[P0_CRITICAL / P1_HIGH / P2_MEDIUM / P3_LOW / FUTURE]

### Current Status
[PLANNED / IN_PROGRESS / PARTIAL / BLOCKED / READY_FOR_QA / PASS / FAIL / DEFERRED / DISABLED / REMOVED]

### Production Readiness
[DEV_ONLY / TEST_READY / QA_READY / PRODUCTION_READY / NOT_READY]

### Fake/Data Status
[NO_FAKE / DEV_DEMO_ONLY / FAKE_UI_FOUND / FAKE_DATA_FOUND / PLACEHOLDER_ONLY / REMOVED_FAKE]

### User Roles
- Guest
- Buyer
- Tenant
- Owner
- Broker
- Agency Owner
- Agency Agent
- Builder
- Admin
- Super Admin

### Routes
- `/route/example`

### Components
- ComponentName

### Database Tables
- table_name

### RLS / Security
- Required:
- Current status:
- Notes:

### Permissions
- permission.key

### Feature Flags
- feature.flag.key

### Provider Dependencies
- OTP / Email / WhatsApp / Map / Payment / Storage / None

### Admin Controls
- Setting:
- Route:
- Permission:

### UI States Required
- Loading
- Empty
- Error
- Success
- Disabled
- Setup Required

### Mobile Requirements
- Card layout
- Bottom sheet
- No horizontal scroll
- Sticky CTA if needed

### QA Checklist
- [ ] Test guest state
- [ ] Test logged-in state
- [ ] Test role permission
- [ ] Test mobile
- [ ] Test error state
- [ ] Test no-fake state
- [ ] Test backend enforcement

### PASS / FAIL
- Result:
- Failed reason:
- Fix required:
```

---

# 12. ROUTE REGISTRY TEMPLATE

Every route should be tracked.

```md id="l67af0"
| Route | Page Name | Public/Private | Allowed Roles | Auth Required | Feature Flag | Data Source | Status | Mobile QA | Notes |
|---|---|---|---|---|---|---|---|---|---|
| / | Homepage | Public | Guest, All | No | public.home.enabled | Real DB / fallback empty | PLANNED | NOT_TESTED | Search-first homepage |
| /dashboard/broker | Broker Dashboard | Private | Broker | Yes | dashboard.broker.enabled | Real DB | PLANNED | NOT_TESTED | Broker-specific dashboard |
```

Rules:

* No route should be left unknown.
* Private routes must have role guard.
* Admin routes must have admin guard.
* Super Admin routes must have Super Admin guard.

---

# 13. COMPONENT REGISTRY TEMPLATE

Every reusable major component should be tracked.

```md id="fd05xw"
| Component | Module | Used In | Status | Mobile Ready | Loading State | Empty State | Error State | No-Fake Verified | Notes |
|---|---|---|---|---|---|---|---|---|---|
| PropertyCard | Search | Search, Saved, Similar | PLANNED | NO | NO | NO | NO | NO | Must be type-aware |
```

Component must include all states.

---

# 14. DATABASE REGISTRY TEMPLATE

Every table should be tracked.

```md id="w5g2s7"
| Table | Module | Purpose | RLS Enabled | Public Read | User Read | User Write | Admin Access | Status | Notes |
|---|---|---|---|---|---|---|---|---|---|
| properties | Property | Store property listings | Required | Active approved only via view | Own records | Own draft/update | Permission-based | PLANNED | No hidden contacts public |
```

Rules:

* Sensitive tables must have RLS.
* Public should use safe views.
* Private documents must not be public.

---

# 15. STORAGE REGISTRY TEMPLATE

Every bucket should be tracked.

```md id="zha0tm"
| Bucket | Public/Private | Used For | Upload Roles | Read Access | RLS/Policy Status | Max File Size | Allowed Types | Status | Notes |
|---|---|---|---|---|---|---|---|---|---|
| property-images | Public | Property gallery | Owner, Broker, Agency, Builder | Public for approved listings | PLANNED | TBD | jpg,png,webp | PLANNED | Optimize images |
| verification-documents | Private | Verification docs | Users/business roles | Admin/verification only | PLANNED | TBD | pdf,jpg,png | PLANNED | Never public |
```

---

# 16. RLS POLICY REGISTRY TEMPLATE

Track important RLS policies.

```md id="l6k6o0"
| Table | Policy Name | Operation | Role/User Scope | Status | Tested | Notes |
|---|---|---|---|---|---|---|
| properties | Public active approved read | SELECT | anon/authenticated | PLANNED | NO | Exclude hidden contact |
| leads | Receiver reads own leads | SELECT | authenticated receiver | PLANNED | NO | Agency/agent scope required |
```

---

# 17. PERMISSION REGISTRY TEMPLATE

Track permissions.

```md id="gnopwd"
| Permission Key | Module | Description | Default Roles | Status | Notes |
|---|---|---|---|---|---|
| property.create | Property | Create property listing | Owner, Broker, Agency, Builder | PLANNED | Role-specific checks |
| banner_ad.approve | Ads | Approve banner ad | Admin, Super Admin | PLANNED | Payment check required |
```

---

# 18. FEATURE FLAG REGISTRY TEMPLATE

Track feature flags.

```md id="c10xac"
| Feature Flag | Module | Default | Controlled By | UI Impact | Backend Impact | Status | Notes |
|---|---|---|---|---|---|---|---|
| banner_ads.enabled | Banner Ads | false | Super Admin | Hide ad UI | Block ad actions | PLANNED | Enable after payment/admin ready |
| otp.dev_mode.enabled | Auth | dev only | Super Admin/Env | Show dev warning | Allow static OTP in dev | PLANNED | Never production |
```

Every feature flag must affect backend if it controls sensitive action.

---

# 19. PROVIDER DEPENDENCY REGISTRY TEMPLATE

Track provider requirements.

```md id="mrj1dj"
| Provider | Feature | Mode | Required For | Missing Behavior | Status | Notes |
|---|---|---|---|---|---|---|
| OTP | Login/Register | SMS/Dev | Phone login | Block or dev mode | PLANNED | Dev OTP only in development |
| WhatsApp | Contact CTA | Free/API | WhatsApp contact | Hide/show enquiry fallback | PLANNED | API mode cannot fake sent |
```

---

# 20. ADMIN CONTROL REGISTRY TEMPLATE

Track admin settings and controls.

```md id="7inlwd"
| Admin Setting | Module | Controlled By | Route | Affects UI | Affects Backend | Audit Required | Status |
|---|---|---|---|---|---|---|---|
| listing_approval_required | Property | Super Admin | /admin/super/settings | Yes | Yes | Yes | PLANNED |
| whatsapp_mode | Provider | Super Admin | /admin/super/providers/whatsapp | Yes | Yes | Yes | PLANNED |
```

No fake admin setting allowed.

---

# 21. QA REGISTRY TEMPLATE

Track manual QA per feature.

```md id="y46f9z"
| Feature ID | Feature | QA Date | Tested By | Desktop | Tablet | Mobile | Guest | Logged-in | Role Test | Backend Test | Result | Fail Reason | Fix Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F-001 | OTP Login | TBD | AI/Manual | NO | NO | NO | NO | NO | NO | NO | NOT_TESTED | - | - |
```

---

# 22. MOBILE QA REGISTRY TEMPLATE

Mobile verification must be tracked.

```md id="7azell"
| Feature | Mobile Layout | Bottom Nav/Drawer | No Horizontal Scroll | Form Usable | CTA Visible | Status | Notes |
|---|---|---|---|---|---|---|---|
| Property Posting | Step form | Drawer | NOT_TESTED | NOT_TESTED | NOT_TESTED | PLANNED | Must not show desktop table |
```

---

# 23. NO-FAKE QA TEMPLATE

Use this for every module.

```md id="pa9a9d"
| Module | Fake UI Found | Fake Data Found | Placeholder Found | Real Empty State | Real Error State | Removed/Fixed | Status |
|---|---|---|---|---|---|---|---|
| Dashboard | NO | NO | NO | NOT_TESTED | NOT_TESTED | N/A | PLANNED |
```

Production cannot pass with fake UI.

---

# 24. PHASE TRACKING TEMPLATE

Track every development phase.

```md id="d91hwa"
| Phase | Scope | Start Status | End Status | Features Updated | QA Status | Blockers | Notes |
|---|---|---|---|---|---|---|---|
| D0 | Project setup | PLANNED | PLANNED | None | NOT_TESTED | None | Initialize Next.js/Supabase |
| D1 | Auth/Profile | PLANNED | PLANNED | Auth, Profile, Roles | NOT_TESTED | OTP provider/dev mode | - |
```

---

# 25. BLOCKER REGISTRY TEMPLATE

Track blockers.

```md id="90fwm4"
| Blocker ID | Feature | Blocker | Type | Impact | Owner | Status | Resolution |
|---|---|---|---|---|---|---|---|
| B-001 | OTP Login | OTP provider not configured | Provider | Production OTP blocked | Super Admin | OPEN | Use dev OTP only in dev |
```

Blocker types:

* Provider
* Database
* RLS
* Design
* Payment
* Data
* Legal
* Admin Setting
* Unknown

---

# 26. BUG / FIX REGISTRY TEMPLATE

Track bugs.

```md id="ha124m"
| Bug ID | Feature | Bug | Severity | Found In | Status | Fix | Retest Result |
|---|---|---|---|---|---|---|---|
| BUG-001 | Property Card | Hidden phone visible in public payload | Critical | QA | OPEN | Remove from public query | NOT_TESTED |
```

Severity:

* Critical
* High
* Medium
* Low

Critical bugs block production.

---

# 27. ACCEPTANCE CRITERIA TEMPLATE

Every feature should have acceptance criteria.

```md id="jtrwo4"
## Acceptance Criteria — [Feature Name]

- [ ] Feature is visible only to allowed roles.
- [ ] Backend enforces permission.
- [ ] RLS protects private data.
- [ ] Mobile layout works.
- [ ] Loading state exists.
- [ ] Empty state exists.
- [ ] Error state exists.
- [ ] No fake data appears.
- [ ] Feature flag works.
- [ ] Admin setting works if applicable.
- [ ] Manual QA completed.
```

---

# 28. DEFAULT MODULE REGISTRY LIST

The Feature Registry should include these modules:

* Common Rules
* Master Design UX
* Feature Matrix
* Public Website
* Homepage Search
* SEO
* Auth/Login/Register
* Role Profile
* Location Hierarchy
* Property Posting
* Property Card/Detail/Contact
* Requirement/Proposal/Lead/Site Visit
* Dashboards
* Admin/Super Admin
* Banner Ads
* Subscription/Payment/Credits
* Provider Modes
* Database/Supabase/RBAC/RLS
* Notification/Automation/Expiry
* Verification/Fraud/Trust
* CMS/Blog/Legal
* AI Manual Verification
* Claude Phase Prompts

---

# 29. REQUIRED INITIAL FEATURE IDS

Use a consistent ID format.

Suggested IDs:

```txt id="7wxbgz"
AUTH-001
PROFILE-001
LOC-001
SEARCH-001
PROP-001
CARD-001
REQ-001
DASH-001
ADMIN-001
ADS-001
BILLING-001
PROVIDER-001
DB-001
NOTIF-001
VERIFY-001
CMS-001
QA-001
```

Do not create duplicate IDs.

---

# 30. EXAMPLE FEATURE ENTRIES

## AUTH-001 — Login/Register OTP Modal

```md id="cainht"
| Field | Value |
|---|---|
| Feature | Login/Register OTP Modal |
| Module | Auth |
| Priority | P0_CRITICAL |
| Status | PLANNED |
| Production Readiness | NOT_READY |
| Fake/Data Status | NO_FAKE |
| Roles | Guest, Public User |
| Routes | Login/Register modal, /login if route exists |
| Feature Flag | auth.otp.enabled |
| DB Tables | profiles, user_roles |
| RLS Needed | Yes |
| Provider Dependency | OTP Provider / Dev OTP in development |
| Admin Control | OTP mode, session timeout |
| QA Status | NOT_TESTED |
```

## PROP-001 — Type-Based Property Posting

```md id="w5s612"
| Field | Value |
|---|---|
| Feature | Type-Based Property Posting |
| Module | Property |
| Priority | P0_CRITICAL |
| Status | PLANNED |
| Production Readiness | NOT_READY |
| Fake/Data Status | NO_FAKE |
| Roles | Owner, Broker, Agency, Builder |
| Routes | /dashboard/owner/properties/new, /dashboard/broker/listings/new |
| Feature Flag | property.posting.enabled |
| DB Tables | properties, property_locations, property_media |
| RLS Needed | Yes |
| Provider Dependency | Storage |
| Admin Control | Approval required, listing expiry |
| QA Status | NOT_TESTED |
```

## ADS-001 — City Targeted Homepage Banner Ads

```md id="ejimdf"
| Field | Value |
|---|---|
| Feature | City Targeted Homepage Banner Ads |
| Module | Banner Ads |
| Priority | P1_HIGH |
| Status | PLANNED |
| Production Readiness | NOT_READY |
| Fake/Data Status | NO_FAKE |
| Roles | Agency, Real Estate Group, Builder, Admin |
| Routes | /dashboard/agency/banner-ads, /admin/advertisements/banner-ads |
| Feature Flag | banner_ads.enabled |
| DB Tables | banner_ads, banner_ad_targets, banner_ad_images |
| RLS Needed | Yes |
| Provider Dependency | Storage, Payment if paid |
| Admin Control | Approval, package, city targeting |
| QA Status | NOT_TESTED |
```

---

# 31. FEATURE REGISTRY UPDATE RULE

After every phase, Claude/AI must update:

* Feature status
* Production readiness
* Fake/data status
* Routes created
* Components created
* Tables created
* RLS added
* Feature flags added
* Admin controls added
* QA checklist status
* Bugs/blockers
* Notes

Do not leave registry outdated.

---

# 32. WHEN FEATURE IS NOT BUILT

If a feature is not built yet:

* Mark status as PLANNED or DEFERRED.
* Do not show it as working in UI.
* Hide route/link if not available.
* Add blocker if needed.
* Add note.

Wrong:

```txt id="8nylj7"
Show Payment Success dashboard with fake data.
```

Correct:

```txt id="ca740w"
Payment feature is disabled until provider is configured.
```

---

# 33. WHEN FEATURE IS PARTIAL

If feature is partial:

* Mark status PARTIAL.
* State what works.
* State what does not work.
* Hide broken parts.
* Add QA tasks.
* Add blockers if needed.

Example:

```md id="30l65h"
Status: PARTIAL
Works: User can upload property images.
Missing: Image crop and plan-based image limit.
Production Readiness: NOT_READY
```

---

# 34. WHEN FAKE UI IS FOUND

If fake UI is found:

1. Mark `Fake/Data Status = FAKE_UI_FOUND`.
2. Add bug entry.
3. Hide or replace with empty/setup state.
4. Retest.
5. Mark `REMOVED_FAKE` after fixed.
6. Mark `NO_FAKE` only after confirmed.

No production pass allowed with fake UI.

---

# 35. WHEN PROVIDER IS MISSING

If provider is missing:

* Mark provider dependency as blocked.
* Show setup-required state in admin.
* Hide public feature or show safe fallback.
* Do not fake provider success.
* Add blocker.

Example:

```md id="q1e0qq"
Blocker: WhatsApp API provider missing.
Fallback: Use wa.me mode if Super Admin selects free mode.
```

---

# 36. WHEN RLS IS MISSING

If RLS is missing for sensitive table:

* Mark feature FAIL or BLOCKED.
* Add Critical bug.
* Do not mark production ready.
* Add policy task.
* Retest after fix.

Sensitive tables cannot pass without access control.

---

# 37. WHEN MOBILE QA FAILS

If mobile QA fails:

* Mark feature PARTIAL or FAIL.
* Add bug.
* Specify device/screen issue.
* Fix layout.
* Retest.

Examples:

* Horizontal scroll
* Hidden CTA
* Table not converted to cards
* Modal not closing
* Keyboard covers form
* Tap targets too small

---

# 38. WHEN ADMIN SETTING IS FAKE

If admin setting does not affect real behavior:

* Mark FAKE_UI_FOUND.
* Add bug.
* Connect setting to backend/UI behavior.
* Or hide setting.
* Retest.

Admin toggles must not be decorative.

---

# 39. FINAL LAUNCH READINESS TABLE

Before launch, create final readiness table.

```md id="b8w5lv"
| Module | Required For Launch | Status | Production Ready | Critical Bugs | Notes |
|---|---|---|---|---|---|
| Auth | Yes | PASS | Yes | 0 | OTP dev disabled in production |
| Property Posting | Yes | PASS | Yes | 0 | Owner/Broker/Agency tested |
| Payments | Optional/Yes | READY_FOR_QA | No | 1 | Provider webhook pending |
```

Launch should not proceed with critical FAIL items.

---

# 40. CRITICAL LAUNCH BLOCKERS

Critical blockers include:

* Public can access admin routes.
* Service role key exposed.
* Hidden phone visible in public API.
* Fake payment activates subscription.
* Fake verified badge shown.
* RLS missing on sensitive tables.
* Private documents public.
* Dev OTP enabled in production.
* Unapproved listings public.
* Unpaid banner ads public.
* Expired paid content still active.
* Mobile unusable on key flows.

Any of these means production launch must stop.

---

# 41. REQUIRED LAUNCH MODULES

Minimum launch modules:

* Auth/Register/Login
* Role-based profile
* Homepage/search
* Property posting
* Property card/detail/contact
* Owner/Broker/Agency basic dashboard
* Admin moderation
* Location system
* Database/RLS/storage security
* Basic notification/in-app status
* Legal pages
* Report property
* No-fake verification states

Payments/banner ads can launch later if not ready, but must be hidden/disabled safely.

---

# 42. FEATURE REGISTRY AND CLAUDE PROMPTS

Every Claude development prompt should say:

```txt id="yc5h1y"
Before coding, read and update the Feature Registry. After completing the phase, update feature status, routes, components, database tables, RLS, feature flags, QA status and blockers.
```

This prevents AI from forgetting previous work.

---

# 43. FEATURE REGISTRY AND MANUAL QA

Manual QA prompt must read registry and check:

* Features marked READY_FOR_QA
* Features marked PARTIAL
* Features marked FAIL
* Features with fake UI found
* Sensitive features needing RLS
* Provider-dependent features
* Mobile failing features
* Admin settings not connected

QA results must update registry.

---

# 44. FEATURE REGISTRY AND NO-SKIP RULE

If a document says a feature exists, it must appear in registry.

If a route exists in code, it must appear in registry.

If a table exists in database, it must appear in registry.

If a provider setting exists, it must appear in registry.

If a feature is deferred, it must be explicitly marked DEFERRED.

No silent skipping.

---

# 45. FEATURE REGISTRY AND NO-FAKE RULE

A feature cannot be marked PASS if:

* It uses fake production data.
* It shows fake metrics.
* It has fake provider success.
* It has fake payment success.
* It has fake verified badge.
* It has fake admin setting.
* It uses placeholder only.
* It exposes private data.
* It lacks required RLS/security.

---

# 46. FEATURE REGISTRY REVIEW FREQUENCY

Update registry:

* After project setup
* After every development phase
* After every major bug fix
* After manual QA
* Before launch
* After launch changes
* Before adding monetization
* Before enabling providers
* Before public release

Do not wait until the end.

---

# 47. FEATURE REGISTRY FILE FORMAT RULE

Keep file readable.

Use:

* Markdown tables
* Short feature IDs
* Clear status values
* Checklists
* Notes
* Links to docs/routes if useful
* No huge unrelated explanations inside registry

Do not make registry a messy essay.

---

# 48. MASTER CHECKLIST BEFORE MARKING FEATURE PASS

Before marking any feature PASS:

```md id="w8ajzy"
- [ ] Feature works on desktop.
- [ ] Feature works on mobile.
- [ ] Feature has loading state.
- [ ] Feature has empty state.
- [ ] Feature has error state.
- [ ] Feature has success state.
- [ ] Role permission is correct.
- [ ] Backend enforces permission.
- [ ] RLS/storage security is correct.
- [ ] Feature flag works if applicable.
- [ ] Admin setting works if applicable.
- [ ] Provider missing state is safe if applicable.
- [ ] No fake data/UI.
- [ ] Manual QA completed.
```

---

# 49. FINAL NOTE TO CLAUDE / AI DEVELOPER

When coding My Gujarat Property, always treat the Feature Registry as the source of truth for progress tracking.

Do not say a feature is complete unless:

* It is implemented.
* It is connected to real data.
* It is protected by permissions/RLS.
* It works on mobile.
* It has no fake UI.
* It passed QA.

---

# 50. END OF FILE

This file defines the Feature Registry Template for My Gujarat Property.

The registry must be updated continuously so that no feature is skipped, no fake UI remains, no provider/payment/security issue is hidden and every module reaches verified PASS before production.

Nothing from uploaded docs or user chat instructions should be skipped.
