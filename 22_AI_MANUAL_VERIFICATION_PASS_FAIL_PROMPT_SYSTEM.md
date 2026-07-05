# MY GUJARAT PROPERTY

# AI MANUAL VERIFICATION, PASS/FAIL, AUTO-FIX & QA PROMPT SYSTEM

## FILE NAME

`22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete AI/manual verification system for **My Gujarat Property**.

This file must be used after every development phase to verify that Claude/AI/developer has actually built the website correctly.

This file covers:

* Manual verification rules
* AI testing workflow
* PASS/FAIL criteria
* Auto-fix loop
* Role-based testing
* Guest vs logged-in testing
* Mobile/tablet/desktop testing
* Auth testing
* Dashboard testing
* Property posting testing
* Requirement/proposal testing
* Admin testing
* Provider missing state testing
* Payment/subscription testing
* Banner ad testing
* Verification/report testing
* CMS/legal page testing
* Database/RLS/security testing
* No-fake UI testing
* Feature Registry update
* Claude verification prompt
* Claude auto-fix prompt
* Retest prompt
* Final QA report format

The goal is to force AI/developer to actually test the product instead of only writing code and assuming it works.

---

# 2. CORE VERIFICATION PRINCIPLE

A feature is not complete just because code exists.

A feature is complete only when:

* It is visible in correct place.
* It works for correct role.
* It is blocked for wrong role.
* It uses real database/provider state.
* It works on mobile.
* It has loading, empty, error and success states.
* It does not show fake data.
* It does not expose private data.
* It passes manual verification.

No feature should be marked PASS without testing.

---

# 3. NO SCREENSHOT / VIDEO DEPENDENCY RULE

Verification does not require old screenshot/video capture workflow.

AI/developer should verify by:

* Running app locally
* Opening pages
* Logging in as roles
* Clicking buttons
* Filling forms
* Submitting data
* Checking dashboard updates
* Checking database records where needed
* Checking mobile responsive layout
* Checking console/network errors
* Checking server logs
* Checking RLS/security behavior
* Writing PASS/FAIL report

Screenshots are optional for human review but not required.

Do not depend on sample screenshots, external videos or image references.

---

# 4. DEVELOPMENT TEST DATA RULE

Development test users/data are allowed only for testing.

Rules:

* Test users must be clearly test/demo.
* Test listings must be clearly test/demo.
* Test requirements must be clearly test/demo.
* Test payments must use test mode only.
* Test banner ads must be clearly demo/test.
* Demo data must not appear as real production data.
* Production must remove or hide demo records.

Use fields like:

```txt id="095jxu"
is_demo = true
```

or clear naming:

```txt id="4m2erz"
TEST Broker User
TEST Property Rajkot
```

Do not create fake production marketplace data.

---

# 5. VERIFICATION ENVIRONMENTS

Verification can happen in:

* Development
* Staging
* Production pre-launch

## Development

Allowed:

* Dev OTP
* Test provider modes
* Demo users
* Test payment mode
* Demo property data

Not allowed:

* Marking production ready without security checks

## Staging

Allowed:

* Near-production testing
* Test payments
* Test provider credentials
* Demo users

## Production Pre-launch

Required:

* No dev OTP
* No fake data
* No exposed secrets
* Real provider settings or safe disabled state
* RLS active
* Admin protected

---

# 6. PASS / FAIL DEFINITIONS

## PASS

Feature works correctly and safely.

Must satisfy:

* Correct UI
* Correct role access
* Correct backend action
* Correct database update
* Correct mobile layout
* No fake data
* No security issue
* No critical console/server errors

## FAIL

Feature is broken, unsafe or fake.

Examples:

* Button does nothing
* Route crashes
* Wrong role can access
* Fake data shown as real
* Private data exposed
* Payment success faked
* Verification badge faked
* Mobile layout broken
* Missing RLS
* Provider success faked

## PARTIAL

Feature partly works but has missing pieces.

Example:

* Form opens but submit fails.
* Desktop works but mobile broken.
* UI works but backend not connected.
* Backend works but empty/error states missing.

## BLOCKED

Feature cannot be tested because dependency missing.

Example:

* Payment provider not configured.
* SMS provider missing.
* Database table missing.
* Feature flag disabled intentionally.

---

# 7. SEVERITY LEVELS

Use these severity levels:

```txt id="za0t8j"
CRITICAL
HIGH
MEDIUM
LOW
COSMETIC
```

## CRITICAL

Blocks launch.

Examples:

* Public can access admin.
* Service role key exposed.
* Fake payment activates subscription.
* Hidden phone exposed.
* Private documents public.
* Dev OTP works in production.

## HIGH

Important but may not expose system-wide security.

Examples:

* Role dashboard wrong.
* Property submit broken.
* Payment callback fails.
* Mobile primary form unusable.

## MEDIUM

Needs fix but not launch-breaking if feature disabled.

Examples:

* Empty state missing.
* Some filter not working.
* Admin action missing note.

## LOW

Minor usability issue.

## COSMETIC

Spacing/visual polish.

---

# 8. AUTO-FIX LOOP

AI must use this loop:

```txt id="t7aa5k"
1. Read docs and Feature Registry.
2. Run app.
3. Test feature manually.
4. Record PASS/FAIL.
5. If FAIL, identify root cause.
6. Fix code.
7. Retest.
8. Update Feature Registry.
9. Repeat until PASS or clearly BLOCKED.
```

Do not stop after detecting failure.

Do not ask user to test if AI can test locally.

---

# 9. VERIFICATION ORDER

Recommended order:

1. Project starts and builds
2. Environment variables safe
3. Database connection
4. Auth/register/login
5. Public pages
6. Role-based profile
7. Header/sidebar/mobile menu
8. Search/homepage filters
9. Property posting
10. Property card/detail/contact
11. Requirement/proposal/leads
12. Dashboards
13. Admin/Super Admin
14. Banner ads
15. Subscription/payment
16. Provider modes
17. Storage/RLS/security
18. Notifications/expiry/archive
19. Verification/report/fraud
20. CMS/legal pages
21. Mobile full QA
22. No-fake sweep
23. Feature Registry update
24. Final PASS/FAIL report

---

# 10. REQUIRED TEST USERS

Create/use test users for each role where possible.

## Public/Guest

No login.

## Buyer

Test buyer browsing and requirement posting.

## Tenant

Test rental/PG requirement.

## Owner

Test property posting and owner dashboard.

## Broker

Test broker profile, listings, requirements feed, proposals.

## Agency Owner

Test agency dashboard, agents, listings, leads, banner ads if enabled.

## Agency Agent

Test assigned leads/site visits only.

## Builder

Test project posting, units, project leads, banner ads.

## Admin

Test moderation and management.

## Super Admin

Test provider/settings/feature flags/security controls.

Do not allow public registration to create Admin/Super Admin.

---

# 11. TEST USER NAMING RULE

Use clear names:

```txt id="wptkvl"
TEST Buyer Rajkot
TEST Tenant Ahmedabad
TEST Owner Rajkot
TEST Broker Rajkot
TEST Agency Owner Rajkot
TEST Agency Agent Rajkot
TEST Builder Ahmedabad
TEST Admin
TEST Super Admin
```

Use test phone/email.

Mark demo/test data.

---

# 12. DEVICE TESTING REQUIREMENT

Test each major flow on:

* Desktop
* Tablet
* Mobile

Mobile checks:

* No horizontal scroll
* Header does not wrap badly
* Sidebar/drawer works
* Bottom nav works if present
* Forms usable
* Keyboard does not hide important CTA
* Cards replace tables
* Modals/bottom sheets close on outside tap
* Buttons large enough
* Sticky CTA visible where needed
* Search filters usable
* Dashboard cards usable

A feature cannot PASS if mobile primary flow is broken.

---

# 13. BROWSER / CONSOLE CHECK

During verification:

* Check browser console errors.
* Check failed network requests.
* Check server terminal logs.
* Check hydration errors.
* Check route crashes.
* Check 404/500 errors.
* Check auth/session errors.
* Check RLS permission errors.
* Check provider errors.

Console warnings are not always FAIL, but critical errors must be fixed.

---

# 14. AUTH VERIFICATION CHECKLIST

Test:

* Login/Register button visible to guest.
* Logged-in user sees profile icon, not Login/Register.
* New user cannot login directly before register if system rule applies.
* Register flow includes role selection.
* OTP flow works in dev mode.
* Dev OTP clearly dev-only.
* Production/static OTP not allowed.
* Existing user login works.
* Session persists.
* Logout works.
* Protected dashboard redirects guest to auth.
* Intent preserved after login.
* Admin role not public.
* Role-based redirect works.

PASS only if auth state is real.

---

# 15. PROFILE / ROLE VERIFICATION CHECKLIST

Test:

* Buyer profile opens.
* Tenant profile opens.
* Owner profile opens.
* Broker profile has broker fields.
* Agency profile has logo/company fields.
* Builder profile has builder/company fields.
* Avatar/logo upload works or hidden.
* Role switcher works only for approved roles.
* Role change request works.
* Role approval required.
* Pending role does not grant access.
* Header/sidebar changes by active role.
* Subscription impact shown for role change.

---

# 16. PUBLIC WEBSITE VERIFICATION CHECKLIST

Test:

* Homepage opens.
* Header responsive.
* Mobile menu works.
* Search bar works.
* City selector works.
* Category tabs work.
* Banner section works or hidden if disabled.
* Footer links work.
* Static pages open.
* Login/register modal opens.
* No broken links.
* No fake city/property counts.
* No horizontal scroll.

---

# 17. SEARCH / FILTER VERIFICATION CHECKLIST

Test:

* Homepage search submits.
* Search result route opens.
* Buy filters show relevant fields.
* Rent filters show rent/deposit fields.
* Land filters hide BHK.
* Commercial filters hide BHK.
* Project filters show project fields.
* PG filters show PG fields.
* City/locality filters work.
* Sort works if implemented.
* Empty result state works.
* Mobile filter bottom sheet works.
* Search count is real or hidden.
* No fake properties.

---

# 18. PROPERTY POSTING VERIFICATION CHECKLIST

Test by Owner/Broker/Agency/Builder:

* Post Property CTA visible for eligible role.
* Guest redirected to login/register.
* Type selection appears first.
* Dynamic fields change by property type.
* Land does not show BHK.
* Commercial does not show residential fields.
* Required fields validate.
* Location selector works.
* Media upload shows size/ratio.
* Image preview/crop works or hidden.
* Draft save works.
* Submit for approval works.
* Pending property not public.
* Admin approval makes active.
* Rejection shows reason.
* Expiry field exists if required.
* No fake listing created as production.

---

# 19. PROPERTY CARD / DETAIL / CONTACT VERIFICATION CHECKLIST

Test:

* Card shows correct source tag.
* Card shows real price/location.
* Card image loads.
* Detail page opens.
* Contact visibility follows rules.
* Guest contact opens login/register if required.
* Lead form works.
* Current number option works.
* Alternate number option works.
* Receiver dashboard shows alternate number badge.
* WhatsApp button follows provider mode.
* Call button works if allowed.
* Save/share/report works if implemented.
* Expired listing does not show active contact.
* Hidden phone not in public payload.

---

# 20. REQUIREMENT / PROPOSAL VERIFICATION CHECKLIST

Test Buyer/Tenant:

* Post requirement CTA works.
* Dynamic fields change by requirement type.
* Land requirement hides BHK.
* Rental requirement shows rent fields.
* Requirement submits.
* Pending requirement not visible to responders.
* Approved requirement visible to eligible broker/agency/builder.
* Buyer can edit/close/renew if allowed.

Test Broker/Agency/Builder:

* Requirement feed visible if plan/role allows.
* Sender can view safe buyer summary.
* Sender cannot see private phone unless shared.
* Send proposal works.
* Attach listing/project if implemented.
* Buyer receives proposal.
* Buyer can shortlist/reject/contact.
* Proposal creates lead when buyer engages.

---

# 21. LEAD VERIFICATION CHECKLIST

Test:

* Lead created from contact form.
* Lead created from requirement/proposal if enabled.
* Lead source is correct.
* Receiver sees lead.
* Sender sees allowed status only if policy.
* Agency owner can assign lead.
* Agent sees assigned lead only.
* Unassigned agent cannot see lead.
* Lead status updates.
* Alternate number badge works.
* No fake leads.

---

# 22. SITE VISIT VERIFICATION CHECKLIST

Test:

* Buyer/tenant can request site visit.
* Date/time selection works.
* Profile/alternate number works.
* Receiver gets request.
* Receiver can approve/reject/reschedule.
* Assigned agent sees assigned visit.
* Cancelled visit does not trigger reminder.
* Completed/no-show statuses work if implemented.
* Mobile visit cards work.
* No fake confirmed visit.

---

# 23. MESSAGING VERIFICATION CHECKLIST

If messaging enabled:

* Thread created from property/proposal/lead.
* Participants can send/read messages.
* Non-participant cannot access thread.
* Agency agent sees only assigned/participant threads.
* Report message works if implemented.
* Attachments work or hidden.
* Empty/error states work.

If messaging disabled:

* Message buttons hidden.
* No broken routes.

---

# 24. DASHBOARD VERIFICATION CHECKLIST

Test dashboards:

## Buyer

* Saved properties
* Requirements
* Proposals
* Site visits
* Messages if enabled

## Tenant

* Rental/PG requirements
* Proposals
* Visits

## Owner

* My properties
* Leads
* Visits
* Expiry
* Plan usage

## Broker

* Listings
* Requirement feed
* Proposals
* Leads
* Visits
* Plan usage

## Agency Owner

* Listings
* Agents
* Leads
* Assignments
* Banner ads
* Plan usage

## Agency Agent

* Assigned leads only
* Assigned site visits only
* No agency billing unless permitted

## Builder

* Projects
* Units
* Leads
* Visits
* Banner ads

All dashboards must be role-specific.

No generic same dashboard for all roles.

---

# 25. ADMIN / SUPER ADMIN VERIFICATION CHECKLIST

Test:

* Normal user cannot access `/admin`.
* Admin can access admin dashboard.
* Super Admin can access Super Admin settings.
* Admin cannot access Super Admin provider settings without permission.
* Moderation queues show pending items.
* Approve/reject property works.
* Approve/reject requirement works.
* Approve/reject banner ad works if enabled.
* Verification center works.
* Reports center works.
* Staff/role settings protected.
* Feature flags work.
* Provider settings masked.
* Audit logs record sensitive changes.

---

# 26. BANNER ADS VERIFICATION CHECKLIST

Test:

* Eligible role can open banner ad dashboard.
* Buyer/Tenant cannot create ads.
* Upload desktop/tablet/mobile images.
* Recommended size/ratio shown.
* Preview works.
* Payment pending blocks display.
* Admin approval required if enabled.
* Active approved paid ad displays.
* Rejected ad does not display.
* Expired ad hides.
* City targeting works.
* Rajkot selected city shows Rajkot ads first.
* Ahmedabad selected city shows Ahmedabad ads first.
* Sponsored label visible.
* Analytics only if real.

---

# 27. SUBSCRIPTION / PAYMENT VERIFICATION CHECKLIST

Test:

* Pricing page visible to guest.
* Purchase requires login.
* Role mismatch handled.
* Order creation works.
* Failed payment does not activate plan.
* Pending payment does not activate plan.
* Verified success activates plan.
* Plan usage updates.
* Listing limits enforce.
* Lead credits deduct correctly.
* Boost/featured starts only after payment/credit.
* Subscription expiry removes paid benefits.
* First 100 launch offer count real.
* Admin manual activation requires audit note.
* No fake payment success.

---

# 28. PROVIDER VERIFICATION CHECKLIST

Test:

* WhatsApp free mode opens wa.me.
* WhatsApp API mode sends only if configured.
* WhatsApp API missing shows safe fallback.
* Map disabled hides maps.
* Map API missing does not fake map.
* Email verification requires provider.
* SMS missing does not fake send.
* OTP dev mode only in development.
* Static OTP blocked in production.
* Payment provider secrets not exposed.
* Provider health is real or not checked.
* Provider test button shows real result.

---

# 29. DATABASE / RLS / STORAGE VERIFICATION CHECKLIST

Test:

* RLS enabled on sensitive tables.
* Public can read only approved active public data.
* Public cannot read leads/payments/private docs.
* Hidden phone not in public query.
* User can manage own data only.
* Agent cannot view unassigned leads.
* Admin access permission-based.
* Private verification docs not public.
* Service role key not in client bundle.
* Feature flags block backend actions.
* Demo data marked and hidden from production.

---

# 30. NOTIFICATION / EXPIRY / ARCHIVE VERIFICATION CHECKLIST

Test:

* In-app notification creates real record.
* User sees own notifications only.
* Listing expiry hides from active search.
* Requirement expiry stops proposals.
* Banner ad expiry stops display.
* Subscription expiry stops benefits.
* Boost/featured expiry removes label.
* Renewal works.
* Archive preserves history.
* External notification not marked sent if provider missing.
* Cron/job endpoints protected if implemented.

---

# 31. VERIFICATION / FRAUD / REPORT VERIFICATION CHECKLIST

Test:

* User can submit verification.
* Documents stored private.
* Admin can approve/reject.
* Badge appears only after approval.
* Badge removed if revoked/expired.
* Property report works.
* “Broker pretending owner” reason exists.
* Report reaches admin queue.
* Admin can take action.
* Fraud flags are admin-only.
* RERA provided vs RERA verified are different.
* No fake ratings/trust score.

---

# 32. CMS / BLOG / LEGAL VERIFICATION CHECKLIST

Test:

* About page opens.
* Contact page opens.
* FAQ page opens.
* Privacy Policy opens.
* Terms opens.
* Refund Policy opens.
* Listing Policy opens.
* Advertising Policy opens.
* Safety page opens.
* Blog list/detail works.
* Draft content not public.
* CMS admin protected.
* Content Manager cannot access provider/payment settings.
* Contact form does not fake sent status.
* Footer links work.
* Mobile pages no horizontal scroll.

---

# 33. NO-FAKE SWEEP CHECKLIST

Search entire app for fake UI/data.

Check:

* Fake leads
* Fake properties
* Fake users
* Fake dashboards
* Fake analytics
* Fake payment status
* Fake subscriptions
* Fake verified badges
* Fake RERA
* Fake banner ads
* Fake provider health
* Fake storage usage
* Fake API usage
* Fake reviews
* Fake ratings
* Fake admin toggles
* Fake notifications
* Fake job logs

If fake found:

* Remove
* Hide behind dev-only flag
* Mark demo clearly
* Replace with empty state
* Update Feature Registry

---

# 34. MOBILE FULL QA CHECKLIST

Test mobile:

* Homepage
* Search
* Search filters
* Property detail
* Contact form
* Login/register
* OTP
* Profile
* Post property
* Post requirement
* Dashboard
* Leads
* Proposals
* Site visits
* Messages
* Admin queues if needed
* Pricing
* CMS pages

Must confirm:

* No horizontal scroll
* No clipped header
* No tiny text/buttons
* No broken modals
* Tables converted to cards
* Filter bottom sheets work
* Sticky CTA visible
* Forms usable

---

# 35. FEATURE REGISTRY UPDATE RULE

After QA, update Feature Registry:

* Feature status
* PASS/FAIL
* Production readiness
* Fake/data status
* Mobile QA status
* RLS status
* Provider dependency
* Blockers
* Bug list
* Fix status
* Retest result

Do not leave registry stale.

---

# 36. MASTER AI VERIFICATION PROMPT

Use this prompt with Claude/AI after a development phase.

```md id="ei23ge"
# PROMPT — AI MANUAL VERIFICATION PASS/FAIL

You are the QA engineer and senior full-stack reviewer for My Gujarat Property.

Read all project documentation and the Feature Registry before testing.

Your job is not only to inspect code. You must run the app, use the website like real users, test guest and logged-in flows, test every relevant role, fill forms, submit records, verify dashboards, verify mobile responsiveness, check console/server errors, check database/RLS/security behavior where possible, detect fake UI/data, and produce a PASS/FAIL report.

Rules:
- Do not mark any feature PASS without testing.
- Do not ignore mobile.
- Do not allow fake data as production data.
- Do not allow fake payment/provider/verification success.
- Do not expose hidden phone/private documents.
- Do not ask the user to manually check things you can test.
- If a feature fails, identify root cause, fix it, then retest.
- Update the Feature Registry after verification.

Test roles:
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

Test areas:
1. Auth/Login/Register/OTP
2. Role profiles and role switch
3. Public homepage/header/sidebar/mobile
4. Search and dynamic filters
5. Property posting
6. Property card/detail/contact/lead
7. Requirement/proposal/site visit/messaging
8. Role dashboards
9. Admin/Super Admin
10. Banner ads
11. Subscriptions/payments/credits/boost
12. Provider modes
13. Database/RLS/storage security
14. Notifications/expiry/archive
15. Verification/fraud/report
16. CMS/blog/legal pages
17. Full mobile QA
18. No-fake sweep

Output format:
- Summary
- PASS modules
- FAIL modules
- PARTIAL modules
- BLOCKED modules
- Critical issues
- Security issues
- Mobile issues
- Fake UI/data issues
- Fixes applied
- Retest results
- Feature Registry updates
- Final launch readiness

Start testing now.
```

---

# 37. AUTO-FIX PROMPT

Use this prompt after QA finds issues.

```md id="wdb0u6"
# PROMPT — AUTO-FIX FAILED QA ITEMS

You are the senior full-stack developer for My Gujarat Property.

Read the QA PASS/FAIL report and Feature Registry.

Fix every FAIL and PARTIAL item that can be fixed now.

Rules:
- Fix root cause, not surface symptoms.
- Preserve role-based access.
- Preserve RLS/security.
- Preserve no-fake rules.
- Do not create placeholder fake UI to hide bugs.
- If provider/payment is missing, implement safe disabled/setup-required state instead of fake success.
- If mobile layout fails, convert tables to cards and remove horizontal scroll.
- If data is private, remove it from public queries.
- If feature is not ready, hide behind feature flag and mark status correctly.

After fixing:
1. Run build/lint/type check if available.
2. Retest affected flows manually.
3. Update Feature Registry.
4. Produce fix report with before/after status.

Do not stop until all fixable critical/high issues are resolved.
```

---

# 38. RETEST PROMPT

Use after auto-fix.

```md id="u7mjvl"
# PROMPT — RETEST FIXED ITEMS

You are the QA engineer for My Gujarat Property.

Retest only the items that previously failed plus any related flows that could be affected.

Rules:
- Do not assume fix works.
- Use the browser/app manually.
- Test desktop and mobile where relevant.
- Test correct role and wrong role.
- Check backend/security when relevant.
- Confirm no fake UI/data was introduced.
- Update Feature Registry.

Output:
- Retested items
- PASS after fix
- Still FAIL
- New bugs introduced
- Remaining blockers
- Final recommendation
```

---

# 39. FINAL LAUNCH QA PROMPT

Use before launch.

```md id="oshxhr"
# PROMPT — FINAL LAUNCH READINESS QA

You are the final launch QA reviewer for My Gujarat Property.

Run complete end-to-end verification before production launch.

You must confirm:
- No dev OTP in production.
- No service role key in client.
- Admin/Super Admin protected.
- RLS enabled for sensitive tables.
- Private documents not public.
- Hidden contact not exposed.
- Payment success is server verified.
- No fake verified badge.
- No fake property/lead/payment/dashboard data.
- Expired listings/ads/subscriptions do not stay active.
- Mobile key flows work.
- Legal pages exist.
- Report system works.
- Feature Registry is updated.

Output:
- LAUNCH READY: YES/NO
- Critical blockers
- High issues
- Modules PASS
- Modules FAIL
- Required fixes before launch
```

---

# 40. QA REPORT FORMAT

Every QA run should output:

```md id="zu7lxp"
# QA REPORT — My Gujarat Property

## Date
[Date]

## Environment
Development / Staging / Production Pre-launch

## Tested By
AI / Manual / Developer

## Summary
[Short summary]

## Overall Result
PASS / FAIL / PARTIAL / BLOCKED

## Modules Tested
- [ ] Auth
- [ ] Profile/Roles
- [ ] Public Website
- [ ] Search
- [ ] Property Posting
- [ ] Property Detail/Contact
- [ ] Requirements/Proposals
- [ ] Leads/Site Visits
- [ ] Dashboards
- [ ] Admin/Super Admin
- [ ] Banner Ads
- [ ] Payments/Subscriptions
- [ ] Providers
- [ ] Database/RLS/Storage
- [ ] Notifications/Expiry
- [ ] Verification/Reports
- [ ] CMS/Legal
- [ ] Mobile
- [ ] No-Fake Sweep

## PASS
[List]

## FAIL
[List with severity]

## PARTIAL
[List]

## BLOCKED
[List with blocker]

## Security Issues
[List]

## Mobile Issues
[List]

## Fake UI/Data Issues
[List]

## Fixes Applied
[List]

## Retest Results
[List]

## Feature Registry Updates
[List]

## Final Recommendation
[Launch ready / Not launch ready / Continue fixes]
```

---

# 41. CRITICAL FAIL CONDITIONS

Any of these means immediate FAIL:

* Service role key in client.
* Admin route accessible to normal user.
* Super Admin route accessible to Admin without permission.
* Public can read hidden phone/email.
* Public can access private verification documents.
* Fake payment activates subscription.
* Dev/static OTP works in production.
* Unapproved property visible publicly.
* Unpaid/unapproved banner ad visible publicly.
* Fake verified badge visible.
* Fake RERA verified visible.
* Expired listing/banner/subscription still active.
* Agent can see all agency leads without permission.
* Buyer can access broker/admin dashboard.
* RLS missing on sensitive tables.
* Contact scraping possible without limits.
* Legal/safety pages missing before production.

---

# 42. WHEN TO MARK BLOCKED

Mark BLOCKED only when dependency is truly missing.

Examples:

* Payment provider credentials missing.
* WhatsApp API not configured.
* Email provider not configured.
* Map API not configured.
* Database table missing from current phase.
* Feature intentionally disabled.
* Legal content not finalized.

Blocked feature must be safely hidden or show setup-required.

Blocked feature must not appear as working production UI.

---

# 43. WHEN TO MARK DEFERRED

Mark DEFERRED when intentionally postponed.

Examples:

* Push notifications later
* Advanced analytics later
* AI fraud scoring later
* Reviews/ratings later
* Auto-renewal later
* External ad links later

Deferred feature should be hidden or labelled future only in internal docs.

Do not show deferred feature as live.

---

# 44. HUMAN HANDOFF NOTE

If AI cannot verify something directly, it must say exactly what is unverified.

Example:

```txt id="87xwwh"
Payment provider webhook could not be fully tested because live/test credentials are not configured. The UI now shows setup-required state and payment activation is blocked until provider is configured.
```

Do not pretend.

---

# 45. END OF FILE

This file defines the AI Manual Verification, PASS/FAIL, Auto-Fix and QA Prompt System for My Gujarat Property.

Every phase must be tested, failed items must be fixed and retested, Feature Registry must be updated and no feature can be considered complete until it passes role, mobile, backend, security and no-fake verification.

Nothing from uploaded docs or user chat instructions should be skipped.
