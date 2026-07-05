# CLAUDE.md

# My Gujarat Property — Claude Code Master Rules

This file is the short global rulebook for Claude Code while building **My Gujarat Property**.

Claude must always follow this file first, then read only the relevant detailed docs for the current task. Do not paste or repeat the full long documentation in every prompt. Use file references and exact paths to keep prompts token-light.

---

## 1. Project Identity

Project name: **My Gujarat Property**

Project type: Gujarat-focused real estate marketplace and admin operating system.

Core users:

* Guest visitor
* Owner
* Broker / Agent
* Builder / Developer
* Super Admin
* Admin
* Staff roles

Main platform purpose:

* Search and view real estate listings
* Post properties
* Post projects
* Post requirements
* Send inquiries
* Manage leads
* Manage proposals
* Manage site visits
* Manage subscriptions and billing
* Manage banner ads/promotions
* Manage verification
* Manage admin moderation
* Manage SEO, CMS, legal pages and platform settings

---

## 2. Absolute Non-Negotiable Rules

Claude must never violate these rules:

1. No fake UI.
2. No fake data.
3. No fake counts.
4. No fake leads.
5. No fake views.
6. No fake analytics.
7. No fake payment success.
8. No fake verified badge.
9. No fake RERA verified badge.
10. No fake provider active status.
11. No hidden contact number leak.
12. No public admin/staff access.
13. No service role key in client.
14. No secrets exposed in frontend, logs, docs, screenshots or chat.
15. No dead buttons.
16. No broken links.
17. No `href="#"`.
18. No incomplete feature shown as working.
19. No feature removal without explicit user approval.
20. No security bypass through direct URL access.
21. No frontend-only protection for protected actions.
22. No production dev OTP.
23. No test payment mode in production.
24. No demo/test data in production unless clearly flagged and hidden from real users.
25. No long unbounded database reads.
26. No N+1 queries.
27. No unsafe file uploads.
28. No raw database errors or stack traces shown to users.
29. No skipping documentation updates after major changes.
30. No phase PASS without verification.

If a feature is not ready, missing provider/API, or unsafe to expose, Claude must mark it as:

* `SETUP_REQUIRED`
* `PARTIAL`
* `BLOCKED`
* or hidden behind a feature flag

Never pretend it works.

---

## 3. Required Tech Stack

Use this stack unless the user explicitly approves a change:

* Frontend: Next.js 15 App Router
* React
* TypeScript
* Tailwind CSS
* Backend: Next.js Server Actions and Route Handlers
* Database: Supabase PostgreSQL
* Auth: Supabase Auth
* Server data access: Supabase Server Client
* Authorization: Role-Based Access Control and Supabase RLS
* Validation: Zod or equivalent schema validation
* Storage: Cloudflare R2 + Cloudflare CDN
* Payment: Razorpay
* Maps: Google Maps Embed/API modes
* Notifications: database-backed in-app notifications
* Email/SMS/WhatsApp only when real providers are configured

Development time priority:

1. Supabase Auth
2. Supabase Database
3. RLS
4. Core backend
5. UI and role flows
6. Provider setup-required states
7. Real provider integration later

Do not connect or fake third-party APIs before their phase unless the prompt explicitly asks for it.

---

## 4. Main Documentation Files

Claude must use the project docs as the source of truth.

Root docs:

* `CLAUDE.md`
* `brain.md`
* `FEATURE_REGISTRY.md`
* `CHANGELOG.md`
* `BUGS_AND_FIXES.md`
* `MANUAL_VERIFICATION.md`
* `API_PROVIDER_STATUS.md`
* `DEPLOYMENT_ROLLBACK.md`
* `SECURITY_RLS_CHECKLIST.md`
* `PERFORMANCE_CHECKLIST.md`

Detailed docs:

* `docs/01_PROJECT_MASTER_AND_SCOPE.md`
* `docs/02_CLAUDE_WORKFLOW_AND_TOKEN_LIGHT_RULES.md`
* `docs/03_ARCHITECTURE_TECH_STACK_DATABASE_RLS.md`
* `docs/04_AUTH_LOGIN_REGISTER_ROLES_PERMISSIONS.md`
* `docs/05_PUBLIC_ROLES_HOME_PROFILE_DASHBOARD.md`
* `docs/06_PROPERTY_PROJECT_REQUIREMENT_FULL_MATRIX.md`
* `docs/07_LEADS_CRM_PROPOSALS_SITE_VISITS_MESSAGES.md`
* `docs/08_ADMIN_SUPER_ADMIN_STAFF_MODULES.md`
* `docs/09_BILLING_SUBSCRIPTION_PAYMENT_GST_TRIAL.md`
* `docs/10_ADS_PROMOTION_NOTIFICATION_PROVIDER_MODES.md`
* `docs/11_LOCATION_SEARCH_SEO_CMS_BLOG_LEGAL.md`
* `docs/12_MEDIA_UPLOAD_STORAGE_IMAGE_VIDEO_PDF.md`
* `docs/13_UI_UX_DESIGN_SYSTEM_RESPONSIVE_RULES.md`
* `docs/14_SECURITY_PRIVACY_CONSENT_FRAUD_LEGAL.md`
* `docs/15_PERFORMANCE_DEPLOYMENT_ROLLBACK_QA.md`
* `docs/16_ADVANCED_FEATURES_PWA_LOCALIZATION_ANALYTICS.md`

Prompt files:

* `prompts/00_PROMPT_USAGE_RULES.md`
* phase prompt files
* phase manual verification prompt files

Claude must not depend on chat memory only. Another Claude account must be able to continue by reading these files.

---

## 5. Token-Light Workflow Rules

Claude prompts must stay token-light.

Do:

* Read only relevant docs before coding.
* Use exact file paths.
* Use summaries and file references.
* Update docs after changes.
* Keep final responses concise.
* Mention changed files, SQL files, tests, verification result and pending issues.
* Paste only relevant 20–30 log lines when needed.
* Use existing docs as memory.

Do not:

* Paste full long docs repeatedly.
* Paste large files in chat.
* Paste full logs.
* Repeat the same rules in every response.
* Depend only on current chat context.
* Mark work done without actual changes and tests.

When context becomes heavy:

* Use `/compact` for the same long task.
* Use `/clear` for a new unrelated task.
* Use `/context` to inspect context pressure.
* Use `/cost` if token/API cost concern exists.

Suggested model usage:

* Sonnet for most coding.
* Opus for hard planning, architecture or complex debugging.
* Haiku for quick lookup, small repetitive edits or simple fixes.

---

## 6. Phase Workflow

Every development phase must follow this cycle:

1. Read `CLAUDE.md`.
2. Read `brain.md`.
3. Read `FEATURE_REGISTRY.md`.
4. Read the current phase prompt.
5. Read only the detailed docs listed in that prompt.
6. Inspect existing routes, components, database tables, migrations and RLS policies before coding.
7. Create a short implementation plan.
8. Implement changes.
9. Add or update SQL migrations if DB/RLS changes are needed.
10. Update relevant docs.
11. Run lint, typecheck, build and relevant tests.
12. Run or prepare manual verification.
13. Fix errors first.
14. Mark verification as `PASS`, `PARTIAL`, `BLOCKED` or `FAIL`.
15. Update `brain.md` with resume guide.
16. Update `FEATURE_REGISTRY.md`.
17. Update `CHANGELOG.md`.
18. Update `BUGS_AND_FIXES.md` if bugs/fixes exist.
19. Update `MANUAL_VERIFICATION.md`.
20. Final response must list changed files, SQL files, tests run, verification result, pending issues and next phase.

A phase must not move forward unless:

* current phase is `PASS`, or
* the user explicitly approves moving forward with `PARTIAL` or `BLOCKED`.

---

## 7. Required Final Response Format For Claude

Claude’s final response after any implementation phase must include:

```md
## Changed Files
- path/to/file

## SQL / Migration Files
- path/to/migration.sql
- None

## Tests Run
- command
- result

## Verification Result
PASS / PARTIAL / BLOCKED / FAIL

## Pending Issues
- issue or None

## Docs Updated
- brain.md
- FEATURE_REGISTRY.md
- CHANGELOG.md
- MANUAL_VERIFICATION.md
- other docs

## Next Phase
- next prompt file path
```

Do not write fake completion. If tests were not run, say exactly why and mark `PARTIAL` or `BLOCKED`.

---

## 8. Documentation Update Rules

After every major change, Claude must update these files where relevant:

* `brain.md`
* `FEATURE_REGISTRY.md`
* `CHANGELOG.md`
* `BUGS_AND_FIXES.md`
* `MANUAL_VERIFICATION.md`

If provider/API status changes, update:

* `API_PROVIDER_STATUS.md`

If deployment, migration, backup or rollback changes, update:

* `DEPLOYMENT_ROLLBACK.md`

If security, auth, RLS, privacy, permissions or contact visibility changes, update:

* `SECURITY_RLS_CHECKLIST.md`

If performance, caching, image optimization, pagination, load testing or query optimization changes, update:

* `PERFORMANCE_CHECKLIST.md`

Docs must use exact file paths, not vague references.

When docs conflict with code:

1. Mention the conflict.
2. Follow latest/current master rule.
3. Update docs/code to match approved behavior.
4. Add conflict note in `brain.md`.

Duplicate rules should be merged without losing meaning.

---

## 9. Feature Registry Rules

`FEATURE_REGISTRY.md` must track every feature, route, module, DB table and QA result.

Allowed statuses:

* `NOT_STARTED`
* `IN_PROGRESS`
* `DONE`
* `PARTIAL`
* `BLOCKED`
* `SETUP_REQUIRED`

No feature should silently disappear between docs, prompts, code and verification.

Feature Registry must include:

* feature/module name
* role access
* route path if applicable
* related DB tables
* status
* QA result
* provider dependency if any
* pending issue
* last updated phase

---

## 10. Brain Memory Rules

`brain.md` must store project memory so another Claude account can continue without chat history.

It must include:

* current phase
* latest completed phase
* active task
* important decisions
* current architecture notes
* completed modules
* pending modules
* known issues
* temporary workarounds
* conflict notes
* provider setup status
* database/RLS notes
* latest migration notes
* resume guide

Every phase must add a small resume guide.

---

## 11. SQL, Database And Migration Rules

Any database change must create or update SQL migration files.

Database changes include:

* table
* column
* enum
* index
* trigger
* function
* policy
* RLS rule
* seed/setup data
* storage bucket policy

Migration files must be saved in project folder using phase-wise or timestamp-wise naming.

Migrations must be:

* idempotent where possible
* reviewed before apply
* documented
* rollback-aware
* safe for production
* compatible with RLS
* not destructive without approval

Before destructive DB/code changes:

* document backup steps
* document rollback steps
* get explicit approval if required

Claude must not only update app code. DB schema, RLS, seed/setup and migrations must also be updated where needed.

---

## 12. Supabase And RLS Rules

Supabase RLS is mandatory for sensitive tables.

Backend and DB must enforce security. Frontend hiding is not enough.

RLS tests must include:

* allowed user access
* denied guest access
* denied wrong-owner access
* denied wrong-role access
* admin/staff scoped access
* service role server-only access

Private fields must not be exposed in public queries, public views, HTML, metadata or SEO pages.

Contact number must stay hidden unless the allowed reveal rules permit it.

Service role key must only be used in trusted server-side code.

Never expose service role key in:

* client code
* browser bundle
* docs
* screenshots
* logs
* migration files
* chat

---

## 13. Auth Rules

Public users:

* Login/register with mobile OTP.
* Registration role options: Owner, Broker/Agent, Builder/Developer.
* Guest can search/view public site.
* Guest cannot see hidden contact number.
* Guest must login/register to send inquiry or reveal contact.
* Logged-in users must not see Login/Register buttons.

Admin/staff:

* Separate login URL.
* Admin/staff URL must be noindex.
* No public create account.
* No mobile login.
* Email/Google login only.
* Staff invite-only.
* Staff access permission-based.
* Admin/staff accounts must not be creatable from public registration.

Post-login redirect must respect user intent:

* Login/register button intent goes to home/dashboard.
* Inquiry/search/listing action returns to the same action/page.
* Unauthorized direct URL access must be blocked safely.

---

## 14. Role Rules

Public roles must be role-aware:

* Guest
* Owner
* Broker / Agent
* Builder / Developer

Internal roles must be permission-aware:

* Super Admin
* Admin
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

Super Admin must see all modules and all features.

If any staff role can see or do something, Super Admin must also be able to see or do it.

Public users must never register as Admin or Super Admin.

---

## 15. UI And Responsive Rules

Design must be:

* mobile-first
* white-first
* clean
* premium
* Apple-style
* real-estate marketplace focused
* trust-focused
* fast
* responsive

Avoid:

* heavy gradients
* neon colors
* glassmorphism
* clutter
* flashy animation
* generic SaaS look
* broken layout
* horizontal scroll
* overlap
* cramped cards
* tiny fonts

Required checks:

* 320px
* 360px
* 390px
* 430px
* 768px
* 1024px
* 1366px
* desktop wide layouts

Header brand name **My Gujarat Property** must not wrap or break into two lines.

Tables must become cards on mobile.

Modals, drawers, dropdowns and bottom sheets must be responsive.

Overlay outside click/tap should close popup, but inside content click must not close it.

Sticky CTA must not cover content.

Every new page/component must handle:

* loading state
* empty state
* error state
* success state where applicable
* disabled state
* unauthorized state
* setup-required state where applicable

---

## 16. Interaction Safety Rules

Claude must prevent accidental actions.

Required behavior:

* image drag disabled where needed
* `draggable=false` for property images, logos, banners and cards where suitable
* scroll gesture and tap gesture separated
* carousel drag threshold
* no accidental click while scrolling
* no auto-copy on text click
* copy only through visible copy button
* nested buttons must not trigger parent card click
* modal content click must not trigger overlay close
* bottom sheet must lock background scroll
* double submit must be blocked
* submit buttons must show loading and disabled state
* payment, lead, inquiry, posting and verification actions must be duplicate-submit protected

---

## 17. Property, Project And Requirement Rules

Owner:

* can post property
* can post requirement
* cannot post project

Broker:

* can post property
* can post requirement
* can manage leads/proposals based on role permissions

Builder / Developer:

* can post project only
* can manage project leads
* can add agents and assign permissions
* can run eligible banner ads/promotions

Every property, project and requirement must require team approval before public display.

Edit/update after approval must require approval again.

Pause/resume may not require approval unless detailed docs say otherwise.

Property/project/requirement can support:

* draft
* preview
* submit for approval
* need changes
* approved
* rejected
* paused
* resumed
* scheduled
* expired
* deleted/soft deleted
* archived

---

## 18. Admin Rules

Admin panel must be:

* white-first
* clean
* operational
* queue-based
* mobile-friendly
* role/permission-aware

Every admin row must be clickable.

Admin detail views must show full related details where allowed:

* user details
* property details
* project details
* requirement details
* leads
* payments
* billing
* failed payments
* verification
* reports
* actions
* logs
* timeline
* public preview link
* admin notes

No fake admin metrics.

Sensitive data must show only to roles with permission.

Admin/staff actions requiring audit log must include reason where needed.

---

## 19. Billing And Payment Rules

No payment success without real gateway verification or approved manual audited action.

Razorpay integration must include:

* order creation
* callback handling
* webhook signature verification
* failed payment state
* pending payment state
* duplicate payment handling
* refund request flow if enabled
* invoice/receipt generation
* payment reconciliation
* idempotency

Invoices must support:

* email delivery
* download
* custom billing details
* optional GSTIN
* GST/tax settings
* sequential invoice number
* B2B/B2C where applicable
* audit logs for manual changes

Plan activation only after:

* verified payment
* valid trial
* valid free plan
* approved manual activation with audit log

---

## 20. Provider Rules

Provider modes must be real or setup-required.

Do not fake provider success.

Providers include:

* OTP provider
* WhatsApp free/API mode
* Google Maps embed/API mode
* Email provider
* SMS provider
* Razorpay payment provider
* Cloudflare R2/CDN
* Analytics provider
* Error tracking provider

If provider is missing:

* hide feature if appropriate
* or show clear `SETUP_REQUIRED`
* never show fake active/sent/success status

Production must disable:

* dev OTP
* test payment
* mock provider
* demo provider
* fake provider status

---

## 21. Media And Upload Rules

Uploads must validate:

* file type
* file size
* access permission
* storage bucket policy
* corrupt/invalid file
* unsafe file risks

Images:

* allow safe image formats where supported
* convert public display images to optimized WebP/AVIF where supported
* keep original for backup/reprocessing where defined
* generate multiple sizes
* lazy-load below-fold images
* reserve layout dimensions
* avoid stretch/distortion
* support cover image selection
* support reorder
* support crop where required

PDF brochures:

* store as PDF
* do not convert to image
* show preview/name/download/view where allowed

Private documents:

* must stay private
* must not use public bucket unless explicitly approved
* must require signed/private access
* must log sensitive access where required

---

## 22. Notifications Rules

Notifications must be database-backed.

Badge count must use real unread count.

No fake notification count.

Notification click must:

* navigate to related page
* mark notification as read
* reduce unread badge count

Must support:

* notification popup/dropdown
* mobile bottom sheet/full-screen drawer
* mark all as read
* empty state
* role-wise notifications
* admin/user separation
* safe fallback route if deep link missing

---

## 23. SEO Rules

SEO must use real data.

Do not create fake city pages or fake listing counts.

Empty/thin pages must be noindex or hidden from sitemap.

Every public SEO page must have:

* unique title
* meta description
* H1
* intro content
* canonical URL
* useful real listings/content where applicable

Property/project pages must have:

* clean URL
* real metadata
* image alt text
* safe schema
* breadcrumb where valid

Do not claim:

* No.1
* 100% verified
* guaranteed deal
* best
* guaranteed buyer/seller/lead

unless legally and actually proven.

---

## 24. Legal And Consent Rules

Legal pages are mandatory.

Required legal/policy pages include:

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
* Grievance / Support Policy

Register/login must include Terms + Privacy acceptance.

Important actions must show relevant warning/notice:

* property posting
* project posting
* requirement posting
* inquiry/contact reveal
* payment checkout
* free trial activation
* verification submit
* banner ad submit
* report form
* role change
* delete account/listing

Platform must clearly state it is an online listing/lead marketplace, not the owner of listed properties and not a legal/financial advisor.

Final legal content must be reviewed by a lawyer before production launch.

---

## 25. Performance Rules

The platform must be designed for high traffic.

Target: 1 lakh active/live users without crash, freeze or unusable UI.

Performance requirements:

* optimized queries
* indexes
* pagination
* lazy loading
* image optimization
* safe caching
* no unbounded reads
* no large data load at once
* no N+1 queries
* rate-limited APIs
* graceful provider failure
* background jobs for heavy work
* load/stress testing before launch

Core Web Vitals targets:

* LCP <= 2.5s
* INP <= 200ms
* CLS <= 0.1

---

## 26. Next.js 15 And React Rules

Use Next.js 15 App Router patterns.

Use server actions where suitable.

Forms should use:

* React 19 `useActionState`
* React 19 `useFormStatus`
* typed server action responses
* safe validation errors

Micro-interactions such as save/shortlist may use:

* React 19 `useOptimistic`
* safe rollback on failure

Caching rules must be explicit.

Use targeted revalidation:

* `revalidatePath`
* `revalidateTag`

Do not revalidate the whole site unnecessarily.

Edge runtime may be used for lightweight tasks.

Node runtime must be used for heavy tasks such as:

* PDF generation
* complex Supabase queries
* payment verification
* image processing coordination

---

## 27. Security, Abuse And Rate Limit Rules

Security-sensitive features must include:

* input validation
* server-side authorization
* RLS
* rate limiting
* safe error handling
* audit logs where required

Rate limits required for:

* OTP request
* OTP verification
* login attempts
* search endpoints
* contact reveal
* inquiry submit
* proposal submit
* message send
* report submit
* payment actions
* admin sensitive actions

Bot/scraping protection required where appropriate.

Cloudflare Turnstile may be feature-flagged and controlled by Super Admin.

---

## 28. Soft Delete And Audit Rules

Real estate data and leads must not be immediately hard deleted.

Use soft delete where required:

* `is_deleted = true`
* deleted timestamp
* deleted by
* delete reason where needed

Restore/recycle bin rules must be followed.

Hard delete must be restricted and retention-based.

Audit logs required for:

* admin actions
* staff actions
* verification
* payment manual action
* plan/manual billing changes
* role/permission changes
* provider setting changes
* user suspension/ban
* listing removal
* rollback
* high-risk actions

Audit logs must not be silently deleted.

---

## 29. Deployment And Rollback Rules

Before production update:

* backup code
* backup database
* backup storage where needed
* review migrations
* confirm rollback plan
* run lint/type/build/tests
* verify auth/RLS/security
* verify responsive UI
* verify provider impact
* update Feature Registry
* update changelog

If update fails:

* rollback code
* rollback database if safe/needed
* use feature flag kill switch
* keep user data safe
* log rollback action
* retest affected features

Live website must not show:

* blank screen
* crash screen
* broken route
* raw DB error
* unhandled provider error

---

## 30. Production Readiness Rules

Before production launch:

* dev OTP disabled
* test payment disabled
* mock providers disabled
* demo data removed/hidden after approval
* production secrets only in environment variables
* service role server-side only
* real OTP tested
* real payment webhook tested
* real email tested
* WhatsApp free/API mode tested
* Cloudflare upload/CDN tested
* PDF privacy tested
* Google Maps/fallback tested
* notification badge/deep links tested
* cron/background jobs tested
* RLS tested
* role access tested
* contact privacy tested
* responsive tested
* load/stress tested
* backup ready
* rollback ready
* final signoff done

Final production status must be one of:

* `PASS`
* `PARTIAL`
* `FAIL`
* `BLOCKED`

No fake production PASS.

---

## 31. Manual Verification Rules

Manual verification must be detailed.

It must check:

* guest flow
* login flow
* register flow
* owner flow
* broker flow
* builder flow
* admin/staff flow
* unauthorized direct URL access
* mobile layout
* tablet layout
* desktop layout
* text wrapping
* horizontal scroll
* overlap
* modals/drawers/bottom sheets
* forms
* validation
* loading states
* empty states
* error states
* disabled states
* contact privacy
* RLS access
* provider setup-required states
* payment states
* notification behavior
* SEO basics where relevant
* build/lint/typecheck results

Manual verification result cannot be vague.

Use:

* `PASS`
* `PARTIAL`
* `BLOCKED`
* `FAIL`

If errors exist, fix them first before marking `PASS`.

---

## 32. Existing Work Preservation

Claude must inspect existing files before changes.

Do not duplicate components, routes, schemas or modules.

Do not remove working features.

Do not change core architecture without approval.

Do not delete tables, disable RLS or weaken security without approval.

Do not replace existing UI with unrelated design.

If old project/live hero section migration is requested:

* copy only the hero search section
* do not copy header/footer
* do not redesign
* preserve layout/colors/responsive behavior as requested
* do not change unrelated files

---

## 33. Error Handling Rules

User-facing errors must be safe and helpful.

Do not show:

* raw SQL errors
* stack traces
* private provider errors
* tokens
* OTPs
* secrets
* full request payloads
* internal file paths where unsafe

Server logs must redact:

* passwords
* OTPs
* tokens
* private user data
* payment secrets
* provider credentials

Every API/server action should return typed error objects.

---

## 34. Accessibility Rules

New UI must support:

* keyboard navigation
* visible focus states
* proper contrast
* alt text
* ARIA labels where needed
* screen reader-friendly form errors
* large tap targets on mobile
* usable modals and drawers
* no trapped keyboard focus bugs

Target: WCAG 2.2 AA where practical.

---

## 35. Localization Rules

UI must support future English/Gujarati/Hindi where planned.

Search must support Gujarat context.

City/locality search should handle:

* English
* Gujarati
* Hindi where implemented
* transliteration
* common spellings
* typos where feasible

Do not create fake translated content.

If translation is missing, use safe fallback.

---

## 36. Development Data Rules

Development seed/demo/test data is allowed only for development/testing.

It must be:

* clearly flagged
* removable
* not mixed with production real data
* hidden/removed before production when user says development complete

Production must not show fake demo users, fake properties, fake leads or fake metrics.

---

## 37. Claude Self-Check Before Final Response

Before final response, Claude must check:

* Did I read the relevant docs?
* Did I inspect existing code before changes?
* Did I avoid duplicate implementation?
* Did I avoid removing working features?
* Did I update required docs?
* Did I update SQL/migration files if DB changed?
* Did I update RLS if needed?
* Did I run or document lint/type/build/tests?
* Did I mark verification correctly?
* Did I list pending issues honestly?
* Did I avoid fake completion?
* Did I avoid exposing secrets?
* Did I preserve mobile-first responsive UI?
* Did I keep no fake UI/data/payment/verified rules?

If answer is no for any item, do not mark `PASS`.

---

## 38. Human Approval Required For High-Risk Changes

Claude must ask before:

* removing existing working features
* changing core architecture
* deleting tables
* disabling RLS
* weakening security
* exposing private data
* changing public role model
* changing admin/staff login model
* changing payment verification model
* hard deleting real user data
* modifying production secrets
* bypassing manual verification

---

## 39. Master Rule

When unsure:

1. Do not skip the requirement.
2. Do not fake completion.
3. Create a safe permission-based, setup-required, deferred or blocked rule.
4. Document it.
5. Add it to Feature Registry.
6. Add pending item in `brain.md`.
7. Keep the project secure and recoverable.

This project must be built as a real production-grade real estate marketplace, not a demo.
