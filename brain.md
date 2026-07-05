# brain.md

# My Gujarat Property — Project Memory, Status And Resume Guide

This file is the live project memory for **My Gujarat Property**.

Claude must update this file after every phase, every major implementation, every important decision, every conflict, every temporary workaround, every bug fix, every migration, every verification result and every pending issue.

This file exists so another Claude account can continue the project without needing chat history.

---

## 1. How Claude Must Use This File

Before starting any task, Claude must read:

1. `CLAUDE.md`
2. `brain.md`
3. `FEATURE_REGISTRY.md`
4. the current phase prompt
5. only the relevant detailed docs listed in the current phase prompt

Claude must not depend on chat memory only.

Claude must update this file at the end of every phase with:

* current phase
* completed work
* changed files summary
* SQL/migration summary
* RLS/security notes
* test results
* manual verification result
* pending issues
* conflicts found
* temporary workarounds
* resume guide for next Claude

---

## 2. Current Project Snapshot

Project name: **My Gujarat Property**

Project type: Gujarat-focused real estate marketplace and admin operating system.

Current status: `DOCUMENTATION_GENERATION_IN_PROGRESS`

Current major task: Generate full Claude-ready documentation and prompt pack from the complete user-provided project requirements.

Current generated file number: `2`

Generated files completed:

* `CLAUDE.md`
* `brain.md`

Generated files pending:

* `FEATURE_REGISTRY.md`
* `CHANGELOG.md`
* `BUGS_AND_FIXES.md`
* `MANUAL_VERIFICATION.md`
* `API_PROVIDER_STATUS.md`
* `DEPLOYMENT_ROLLBACK.md`
* `SECURITY_RLS_CHECKLIST.md`
* `PERFORMANCE_CHECKLIST.md`
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
* all prompt files

---

## 3. Core Product Memory

My Gujarat Property must be built as a real production-grade marketplace, not a demo.

The website must support:

* guest browsing
* mobile OTP login/register for public users
* role selection during registration
* owner flow
* broker/agent flow
* builder/developer flow
* property posting
* project posting
* requirement posting
* inquiry/contact reveal
* leads CRM
* proposals
* site visits
* messages
* notifications
* billing and subscription
* free trials
* Razorpay payments
* GST/invoice support
* banner ads/promotions
* verification
* public profiles and microsites
* admin/staff operating system
* Super Admin full control
* SEO pages
* CMS/blog/legal pages
* provider modes
* Cloudflare R2 media storage
* security/RLS
* deployment/rollback
* production readiness

The platform must be Gujarat-focused but technically structured so future scale is possible.

---

## 4. Absolute Master Decisions

These decisions are approved and must not be changed silently.

### 4.1 Tech Stack

Frontend:

* Next.js 15 App Router
* React
* TypeScript
* Tailwind CSS

Backend:

* Next.js Server Actions
* Next.js Route Handlers
* Supabase Server Client

Database:

* Supabase PostgreSQL

Authentication:

* Supabase Auth
* mobile OTP login/register for public users
* email/Google-only login for admin/staff

Authorization:

* Role-Based Access Control
* permissions
* protected routes
* Supabase RLS

Validation:

* Zod or equivalent schema validation

Storage:

* Cloudflare R2
* Cloudflare CDN
* optimized public image variants
* private signed document access

Payments:

* Razorpay

Providers:

* OTP provider
* WhatsApp free/API mode
* Google Maps embed/API mode
* Email provider
* SMS provider
* Analytics provider
* Error tracking provider

### 4.2 No-Fake Rules

The following must never be faked:

* UI functionality
* database data
* listing counts
* lead counts
* view counts
* analytics
* verified badge
* RERA verified badge
* payment success
* provider success
* notification sent status
* WhatsApp sent status
* email/SMS sent status
* admin metrics
* user reviews/ratings
* SEO city counts
* search result counts

### 4.3 Security Decisions

* Service role key must never be exposed to client.
* RLS must protect sensitive data.
* Frontend-only access control is not enough.
* Public users must never register as Admin or Super Admin.
* Admin/staff login must be separate and noindex.
* Admin/staff public create account must never show.
* Admin/staff mobile login is not allowed.
* Hidden contact numbers must not leak in public HTML, metadata, API response or SEO page.
* Direct URL unauthorized access must be blocked server-side.
* Rate limits must protect OTP, login, search, contact reveal and public actions.
* Provider failure must show safe error or setup-required state.

---

## 5. Role Memory

### 5.1 Public Role: Guest

Guest can:

* view homepage
* search property/project public data
* view public detail pages
* view public SEO pages
* view public profile pages where allowed
* use filters and city selector
* browse recently viewed locally

Guest cannot:

* see hidden contact number
* send inquiry without login/register
* save/shortlist without login
* post property
* post project
* post requirement
* access dashboards
* access admin/staff pages

When guest tries inquiry/contact reveal/save/post action, show login/register popup and preserve return intent.

### 5.2 Public Role: Owner

Owner can:

* access owner-specific home page
* see owner-specific header/footer
* access owner dashboard
* post property
* post requirement
* receive own property inquiry leads
* receive own requirement inquiry leads
* see analytics
* manage billing/subscription
* manage profile
* request verification where enabled
* use help/support

Owner cannot:

* post project
* access broker-only modules
* access builder-only modules
* access admin/staff modules

### 5.3 Public Role: Broker / Agent

Broker can:

* access broker-specific home page
* see broker-specific header/footer
* access broker dashboard
* post property
* post requirement
* receive posted property leads
* receive requirement-related leads
* send relevant proposals
* manage own requirement leads
* view other people posted requirement feeds where allowed
* manage analytics
* manage billing/subscription
* submit broker verification
* use help/support

Broker cannot:

* post builder projects unless also approved under builder role rules
* access builder team/agent module unless assigned
* access admin/staff modules

### 5.4 Public Role: Builder / Developer

Builder can:

* access builder-specific home page
* see builder-specific header/footer
* access builder dashboard
* post projects only
* receive project inquiry leads
* receive matching buying requirement leads
* manage project analytics
* manage billing/subscription
* add agents
* assign agent permissions
* submit builder verification
* manage support/help
* manage eligible banner ads/promotions

Builder cannot:

* post normal owner/broker property unless a separate approved role supports it
* post PG/hostel/room as project
* access admin/staff modules

### 5.5 Internal Role: Super Admin

Super Admin must see and control every module.

If any staff role can see/do something, Super Admin must also see/do it.

Super Admin controls:

* admin dashboard
* users
* staff users
* roles
* permissions
* feature flags
* provider modes
* provider settings
* API settings
* subscription plans
* pricing
* free trials
* add-ons
* billing
* manual plan changes
* users
* properties
* projects
* requirements
* leads
* site visits
* messages if implemented
* verification queues
* support tickets
* reports
* banner ads
* payments
* refunds
* invoices
* credits
* boosts
* CMS
* blogs
* SEO
* locations
* notifications
* security settings
* audit logs
* platform settings
* maintenance mode
* system health
* database/storage/API usage views
* deployment/rollback visibility where implemented

### 5.6 Internal Role: Admin

Admin manages daily operations.

Admin can view and manage assigned operational modules.

Admin must not automatically control:

* provider secrets
* feature flags
* Super Admin settings
* staff role permissions
* database/system-level settings
* global security settings

### 5.7 Staff Roles

Staff roles must be permission-based.

Staff roles include:

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

Each staff role sees only assigned modules.

Every sensitive staff action must be audited.

---

## 6. Public Website Memory

Public website must include:

* search-first homepage
* clear city selector
* role-aware header
* role-aware footer
* guest login/register CTA
* logged-in profile icon
* responsive property/project cards
* real approved listings only
* no fake counts
* no fake verified badge
* no dead CTA
* clean white-first UI
* mobile-first layout
* SEO-friendly public pages
* legal footer links
* safe contact privacy

Footer must show only on public/home pages.

Footer must be hidden in dashboard/features unless explicitly required.

---

## 7. Auth Flow Memory

Public auth:

* mobile number entry
* if number exists, login OTP flow
* if number not registered, show register message
* role selection: Owner, Broker/Agent, Builder/Developer
* role details short description
* full name field
* email field
* mobile number field
* Terms + Privacy checkbox
* OTP confirmation
* post-login redirect based on original intent

Admin/staff auth:

* separate login URL
* noindex
* email/Google login only
* no mobile login
* no public create account
* invite/staff-created only
* permission-based dashboard access
* session timeout
* login attempt limit
* suspicious login alert
* high-risk action confirmation
* 2FA where required

---

## 8. Property System Memory

Property types:

* Residential
* Commercial
* Industrial
* Land / Plot
* PG / Hostel / Room
* Business

Property purpose:

* Buy
* Sell
* Rent

Property subtypes must cover Indian/Gujarat market examples:

* flat
* apartment
* tenament
* bungalow
* villa
* row house
* independent house
* duplex
* penthouse
* studio apartment
* farm house
* residential plot
* non-agricultural land
* agricultural land
* commercial shop
* office
* showroom
* commercial building
* co-working space
* industrial shed
* factory
* warehouse
* godown
* industrial land
* logistics space
* PG
* hostel
* room
* paying guest bed
* business property
* hotel/restaurant space
* school/hospital/institutional property where allowed
* other market-relevant subtypes

Property posting must be type-based and conditional.

Required:

* no irrelevant fields for selected property type
* all necessary fields per type
* required/optional clear
* helper text/hints
* preview before submit
* draft support
* approval flow
* edit/update reapproval
* pause/resume
* schedule
* expiry/archive
* delete/soft delete
* image uploads
* cover image
* location hierarchy
* contact visibility rules
* legal responsibility warning

Owner and broker can post property.

Builder cannot post normal property unless explicitly allowed by future role rule.

---

## 9. Project System Memory

Project types:

* Residential
* Commercial
* Industrial
* Land / Plot

Project purpose:

* Sell
* Rent

Project examples:

* apartment project
* society
* villa project
* bungalow project
* row house project
* plotting project
* township
* mixed-use project
* commercial complex
* office project
* showroom project
* industrial park
* industrial zone
* warehouse park
* logistics park
* land/plotting scheme

Project posting must include:

* project type-based fields
* RERA fields where applicable
* project name
* builder/promoter details
* location
* phases
* wings/towers
* floor-wise data
* unit-wise inventory
* BHK/unit mix
* amenities
* construction status
* possession date
* floor plans
* project brochure
* unlimited images where allowed
* one video upload
* 360°/virtual tour URL/embed where allowed
* construction progress timeline
* project approvals
* pricing/unit availability
* contact number always visible to logged-in users
* inquiry button
* project legal/RERA warning

Builder can post project.

Project must require approval before public display.

---

## 10. Requirement System Memory

Requirement system must include:

* post requirement
* requirement feed
* requirement matching
* role-based visibility
* proposal send option
* proposal relevance rules
* contact privacy
* requirement expiry
* renewal
* duplicate requirement detection
* spam prevention
* requirement status tracking
* matching score where implemented
* notification on matching listing/project
* proposal lifecycle

Proposal statuses:

* sent
* viewed
* shortlisted
* accepted
* rejected
* withdrawn
* expired
* follow-up
* negotiation where implemented

---

## 11. Leads CRM Memory

Leads CRM must include:

* lead source tracking
* lead status pipeline
* lead notes
* lead tags
* lead follow-up date
* lead duplicate protection
* lead merge
* lead ownership
* lead transfer
* lead assignment
* lead notification
* lead privacy consent
* contact reveal consent
* abuse detection
* lead quality feedback
* lead dispute where implemented

Lead statuses:

* New
* Contacted
* Interested
* Follow-up
* Site Visit
* Converted
* Lost
* Closed

Lead sources:

* property
* project
* requirement
* proposal
* banner ad
* saved search alert
* search
* contact reveal
* WhatsApp click
* call click
* public profile
* campaign/UTM where implemented

---

## 12. Site Visit Memory

Site visit system must include:

* site visit request
* approval/reschedule/cancel flow
* date/time selection
* calendar view
* reminder queue
* cancellation reason
* no-show status
* completed status
* feedback form
* safety notice
* deal-not-confirmed disclaimer
* notification links
* CRM integration

Site visit booking is not a property deal confirmation.

Users must verify property and documents independently.

---

## 13. Messaging Memory

Messaging system must include:

* lead-based threads
* proposal-based threads
* requirement-based threads
* unread count
* message notifications
* report/block option
* attachment scanning if attachments enabled
* message archive
* message delivery retry
* privacy rules
* safe moderation for reported messages

Do not show fake sent status for email/SMS/WhatsApp.

---

## 14. Saved, Shortlist And Recently Viewed Memory

Must include:

* save property
* save project
* shortlist proposal
* saved search
* recently viewed property/project
* login required for save/shortlist
* guest recently viewed in local storage
* sync guest recently viewed to account after login
* saved search alerts when matching approved listing appears
* notification preference control

---

## 15. Public Detail Pages Memory

Property and project detail pages must show:

* image gallery
* video where available
* floor plans where available
* 360°/virtual tour where available
* touch-scrollable gallery
* all public details
* inquiry button
* report option
* uploader profile
* uploader profile link
* request contact if number hidden
* inquiry status after send
* duplicate inquiry handling
* project RERA display
* brochure view/download where allowed
* nearby/location details
* legal disclaimer
* similar real results or hide section
* no fake data
* no hidden phone leak

Uploader profile click should open the profile page, preferably new tab where specified.

---

## 16. Profile And Microsite Memory

Role profiles must be role-based.

Common profile fields:

* profile image/avatar
* crop/change/remove image
* name
* contact
* address
* public/private visibility settings
* verification status
* profile completion

Broker profile extras:

* office address
* business name
* broker registration details where applicable
* RERA agent/broker registration check where applicable
* service areas
* team/agents where applicable

Builder profile extras:

* builder/developer name
* office address
* logo
* company details
* RERA/promoter information where applicable
* active projects
* past projects
* team/agents
* public microsite

Owner profile:

* privacy-safe public view
* minimum public exposure
* contact privacy rules

Public microsites:

* builder public profile page
* broker public profile page
* project list
* active/past projects
* contact info where allowed
* team where allowed
* shareable clean URL

---

## 17. Role Change Memory

Role change must be request-based and team-approved.

Before role change, show strict warning:

* current listings may be removed/restricted/archived
* subscription may be affected
* dashboard access may change
* permissions may change
* agent/team access may change
* data migration may be required
* role change cannot bypass verification

Role change must create:

* request record
* admin review
* verification if needed
* audit log
* notification
* status timeline

---

## 18. Verification Memory

Verification must be role-based and document-aware.

Verification statuses:

* not submitted
* draft
* submitted
* under review
* need changes
* rejected
* approved
* revoked
* expired where applicable

Verification applies to:

* owner verification if enabled
* broker verification
* builder verification
* business profile verification
* role change verification
* property verification
* project verification
* requirement verification
* RERA details review
* suspicious/fraud review
* duplicate listing review
* listing ownership conflict review

Verified badge shows only after real approval.

Verification review is platform trust process, not legal certification.

False document submission can cause suspension/removal.

After verified, edit/delete restrictions apply as defined.

---

## 19. Banner Ads And Promotion Memory

Builder banner ads/promotions must include:

* builder dashboard module
* select already published project
* upload desktop image
* upload tablet/mobile image where required
* image ratio/pixel recommendations
* city targeting
* all Gujarat option
* selected multiple cities
* required city selection
* submit for approval
* need changes
* approval
* rejection
* pause
* edit/update
* delete/soft delete
* team/admin control
* payment/plan eligibility
* expiry
* Sponsored/Ad public label
* city/IP targeting
* nearby city fallback
* impressions
* clicks
* ad fraud click protection
* rotation
* frequency cap
* audit logs

Unpaid, unapproved, rejected or expired ads must not show publicly as active.

---

## 20. Subscription, Billing And Payment Memory

Plans must be role-based:

* Owner plan
* Broker plan
* Builder/Developer plan

Plan required before:

* property post
* project post
* requirement post
* banner ads if plan requires eligibility
* lead/contact unlock where plan-based

Plan limits must include:

* property post limit
* project post limit
* requirement post limit
* project/unit limits
* image limits
* video limits
* brochure PDF access
* agent seat limits
* lead/contact unlock limits
* banner ad eligibility
* boost eligibility
* featured listing eligibility

Super Admin controls:

* plan create/edit/update/delete
* enable/disable plans
* monthly/yearly/trial/free/custom/manual plans
* pricing
* coupons
* discounts
* launch offers
* add-ons
* manual activation
* extension
* pause/cancel/expire/change
* credits
* boosts
* extra listing
* extra lead unlock
* billing history
* subscription status
* audit logs

Billing must include:

* invoice download
* invoice email delivery
* billing history
* optional GSTIN
* billing address
* GST/tax settings
* custom invoice edits by Super Admin where allowed
* credit note
* debit note
* payment failed state
* payment pending state
* payment success only after verification

Razorpay must include:

* order creation
* callback
* webhook signature verification
* payment idempotency
* duplicate payment handling
* refund request flow
* payment reconciliation
* settlement reconciliation
* failed payment notification
* retry flow

Invoice number must be sequential and unique for financial year.

Do not waste invoice number on failed payment.

---

## 21. Free Trial Memory

Free trial controlled by Super Admin.

Free trial can be:

* role-based
* selected user-based
* city-based
* new user-based
* verified/unverified user-based
* first-time user-based
* public pricing page offer
* private offer

Free trial must define:

* duration
* start date
* end date
* included limits
* expiry behavior
* auto-expiry
* notification
* one-time/repeat/manual approval
* abuse detection
* audit log
* dashboard real status

Free trial must not fake active state.

If no auto-renewal/payment, clearly say no automatic charge.

---

## 22. Notifications Memory

Notification system must include:

* database-backed notifications
* notification bell/icon
* real unread count badge
* popup/dropdown
* mobile bottom sheet/full-screen drawer
* latest notifications list
* clickable notification
* deep link
* mark read on click
* mark all as read
* empty state
* admin/user separation
* role-wise notification rules
* notification center page
* notification preference page
* digest settings
* delivery logs for external channels
* failure states
* retry
* fallback route if deep link missing

Notification examples:

* new lead
* site visit
* proposal
* payment failed
* payment success
* subscription expiry
* trial expiry
* property approved
* property rejected
* project need changes
* banner ad approved/rejected
* verification need changes
* support ticket update
* provider issue
* admin moderation alert

---

## 23. Location Memory

Location hierarchy:

* Country
* State
* District
* Taluka
* City / Village
* Area
* Locality
* Society
* Building
* Landmark
* Address Line
* Pin Code
* Map Location

Must include:

* Gujarat all city/taluka/district data
* cascading dropdown without page refresh
* missing location request
* admin approve/reject missing location
* nearby city fallback
* city/IP detection
* manual city override
* map pin accuracy
* pin code validation
* city/taluka/district mismatch detection
* locality alias
* society alias
* search synonyms
* typo correction
* Gujarati/Hindi/English/transliteration support where implemented

---

## 24. Search Memory

Search must include:

* search-first homepage
* city selector
* property type filters
* purpose filters
* budget filters
* BHK/unit filters
* area filters
* locality filters
* sort options
* filter chips
* mobile filter bottom sheet
* mobile sort bottom sheet
* query params
* shareable search URLs
* infinite scroll with page query support
* pagination/load more where needed
* no fake result count
* empty state
* nearby city suggestions
* no result recommendation
* save search
* map toggle if map enabled
* map fallback if provider missing
* SEO route connection
* search suggestions
* recent searches
* popular searches
* typo tolerance
* transliteration search
* sponsored vs organic separation
* real results only

Search state should persist in URL using suitable state management such as `nuqs` or equivalent if implemented.

---

## 25. SEO, CMS, Blog And Legal Memory

SEO must be real-data based.

Required SEO pages:

* homepage
* city pages
* locality pages
* property type pages
* property detail pages
* project detail pages
* project directory
* broker directory where allowed
* builder directory where allowed
* blog pages
* policy/legal pages
* guide pages where useful

SEO must include:

* unique title
* meta description
* H1
* intro text
* canonical URL
* sitemap visibility
* noindex option
* clean URL
* safe schema
* breadcrumb schema
* organization schema
* real estate listing schema where valid
* FAQ schema where valid
* image alt text
* Open Graph image
* WhatsApp share preview
* redirect manager
* 301/302/410 rules
* removed listing SEO handling
* expired listing handling
* thin page auto-noindex
* duplicate canonical handling
* Google Search Console issue tracking

CMS must include:

* About page
* Contact page
* FAQ
* Help/Support
* Safety Tips
* Privacy Policy
* Terms & Conditions
* Cookie Policy
* Refund Policy
* Cancellation Policy
* Listing Policy
* Advertising Policy
* Verification Policy
* Payment Policy
* Disclaimer
* Grievance/Support Policy
* blog category
* blog tags
* blog slug
* meta title
* meta description
* featured image
* publish status
* preview before publish

No fake SEO pages, fake counts or false claims.

---

## 26. Legal And Consent Memory

Legal notices required for:

* register/login
* OTP screen
* privacy/data consent
* cookie banner
* property posting
* project/RERA posting
* buy/sell/rent actions
* inquiry/contact reveal
* requirement/proposal
* site visit
* verification submit
* billing/subscription
* free trial
* advertisement/promotion
* report/fraud
* user uploads
* messaging/communication
* admin/staff actions
* grievance/support/takedown
* profile edit
* role change
* delete account/listing

Consent systems:

* Terms acceptance
* Privacy acceptance
* Cookie preference
* marketing opt-in/out
* communication preferences
* WhatsApp opt-in proof
* email/SMS unsubscribe
* lead sharing consent
* contact reveal consent
* verification document consent
* policy version acceptance proof

Platform must state:

* it is an online listing/lead marketplace
* it does not own listed properties
* it is not legal/financial advisor
* approval/moderation does not guarantee title/ownership/RERA/price/availability/deal closure
* user-generated content responsibility stays with posting user
* users must verify documents before deal/payment

Final legal content requires lawyer review.

---

## 27. Media, Upload And Storage Memory

Storage architecture:

* Cloudflare R2 for media
* Cloudflare CDN for public optimized images
* private bucket/signed access for sensitive documents
* original image storage for backup/reprocessing
* optimized WebP/AVIF public display versions
* multiple image sizes
* PDF brochures stored as PDF
* image/video/PDF metadata stored in database

Image formats:

* JPG
* JPEG
* PNG
* WebP
* AVIF
* GIF
* HEIC
* HEIF
* SVG where safe

Upload rules:

* type validation
* size validation
* corrupt file handling
* malware/unsafe scan where implemented
* SVG security
* HEIC/HEIF fallback
* EXIF metadata removal
* watermark rules
* upload progress UI
* retry UI
* failed upload cleanup
* orphan file cleanup
* CDN cache purge
* signed URL expiry
* private document access log

Media features:

* gallery
* cover image selection
* reorder
* crop tool
* floor plan dedicated section
* video upload
* video compression
* video thumbnail
* 360° virtual tour embed/URL
* Matterport support where implemented
* PDF viewer/preview/download
* broken image fallback
* no image placeholder
* image safe crop

---

## 28. UI / UX Design Memory

Design direction:

* premium
* clean
* Apple-style
* white-first
* mobile-first
* trust-focused
* real estate marketplace style
* dashboard polish inspired by TailAdmin/Untitled UI/Creative Tim/Dribbble references
* original My Gujarat Property branding
* no exact copy of reference designs

Mandatory UI rules:

* no horizontal scroll
* no unwanted gap
* no cramped spacing
* no overlap
* no text wrap where it breaks layout
* brand name must not wrap
* proper spacing
* readable text
* large tap targets
* sticky CTA safe
* responsive cards
* modal/drawer/bottom sheet usable
* outside tap close
* tables to cards on mobile
* no fake UI
* no dead buttons
* no broken routes
* no hidden overlay click blocking
* no wrong z-index clicks
* all states implemented

Responsive check sizes:

* 320px
* 360px
* 390px
* 430px
* 768px
* 1024px
* 1366px
* ultra-wide desktop

Component system must include:

* buttons
* badges
* cards
* tabs
* filters
* dropdowns
* modals
* drawers
* bottom sheets
* tables
* mobile cards
* forms
* skeleton loaders
* empty states
* error states
* toasts
* confirmation dialogs
* page headers
* breadcrumbs
* pagination/load more
* charts with empty states
* admin tables
* admin detail drawers
* dashboard widgets

---

## 29. Interaction Safety Memory

Must prevent:

* accidental image drag
* accidental card open while scrolling
* accidental text auto-copy
* accidental submit
* duplicate payment
* duplicate lead
* duplicate inquiry
* wrong parent click from nested button
* wrong modal close from inside click
* background scroll during bottom sheet
* wrong redirect from dropdown
* hidden overlay click block
* mobile gallery swipe/page scroll conflict
* reorder drag during normal scroll
* tooltip accidental mobile open

Actions must only happen on clear intentional click/tap.

Double-click/double-tap duplicate submit must be blocked.

---

## 30. Admin And Staff Memory

Admin system must include:

* clean admin dashboard
* Super Admin full modules
* staff role modules
* permission-based menu
* queue-based moderation
* mobile-friendly admin
* sidebar drawer on mobile
* filters bottom sheet on mobile
* tables convert to cards on mobile
* row clickable
* preview/detail drawer
* full detail page option
* activity timeline
* audit logs
* internal notes
* public preview link
* search/filter on modules
* bulk action permission
* export permission
* sensitive data permission
* private document permission
* high-risk confirmation
* maker-checker where required
* staff task assignment
* workload queues
* SLA dashboards
* escalation
* admin notifications
* staff dashboard alerts
* internal changelog
* admin help/SOP page
* production warning banner

Staff account rules:

* invite only
* approval
* email verification
* Google/email login
* no public registration
* no mobile login
* no visible secrets
* session timeout
* login attempt limit
* suspicious login alerts
* device sessions
* scoped access
* access review
* temporary access expiry
* deactivation/suspend/restore rules
* staff delete block where needed
* activity timeline

---

## 31. Security And Fraud Memory

Security must cover:

* RLS
* server-side auth
* role route access
* API route access
* storage bucket permission
* rate limiting
* OTP cost protection
* login attempt limit
* bot protection
* search scraping protection
* contact reveal abuse detection
* mass inquiry limit
* lead spam protection
* proposal spam limit
* duplicate account detection
* suspicious activity alerts
* IP/device risk flags
* staff 2FA
* high-risk action confirmation
* CSP/security headers
* CSRF protection
* webhook signature validation
* XSS output encoding
* SSRF protection
* safe errors
* log redaction
* secret scanning
* dependency vulnerability scan
* environment variable validation
* production debug mode block

Fraud/report must include:

* report property
* report project
* report profile
* report requirement
* report proposal
* report banner ad
* duplicate listing review
* fake listing review
* suspicious profile review
* broker pretending as owner review
* fake report penalty
* report review SLA
* takedown workflow
* appeal system
* internal fraud flags admin-only
* risk score admin-only
* trust score public hidden unless approved feature

---

## 32. Performance And Scalability Memory

Performance target:

* handle 1 lakh active/live users without crash/freeze/unusable UI

Performance requirements:

* pagination
* infinite loading where suitable
* no unbounded reads
* no N+1 queries
* indexes
* query limits
* caching
* targeted revalidation
* image optimization
* lazy loading
* route prefetch where safe
* bundle size budget
* third-party script budget
* font loading optimization
* animation performance
* memory leak testing
* long task monitoring
* API response size limits
* database connection pooling
* queue/background jobs
* cron jobs
* provider failure fallback
* load testing
* stress testing
* Core Web Vitals monitoring

Core Web Vitals targets:

* LCP <= 2.5s
* INP <= 200ms
* CLS <= 0.1

Next.js 15 rules:

* explicit caching strategy
* revalidateTag/revalidatePath targeted updates
* Edge runtime for light middleware/redirect/banner localization
* Node runtime for heavy PDF/payment/Supabase complex work
* React 19 `useActionState`
* React 19 `useFormStatus`
* `useOptimistic` for safe micro-interactions

---

## 33. Deployment, Backup And Rollback Memory

Every production update requires:

* backup
* migration review
* feature flag review
* build/type/lint/test pass
* manual verification
* auth/role/RLS test
* provider impact check
* payment/contact privacy test
* responsive test
* changelog update
* feature registry update
* rollback plan

Rollback must support:

* code rollback
* database rollback/restore plan
* feature flag kill switch
* storage safety
* user data preservation
* payment/subscription caution
* audit log
* retest after rollback

Zero-downtime migration required where possible.

Production must never show blank/crash/raw DB error pages.

---

## 34. API Provider Status Memory

Provider status must be tracked in `API_PROVIDER_STATUS.md`.

Providers:

* Supabase Auth
* Supabase PostgreSQL
* Supabase RLS
* Cloudflare R2
* Cloudflare CDN
* Cloudflare image processing/worker
* OTP provider
* SMS provider
* WhatsApp free/API
* Email provider
* Razorpay
* Google Maps
* Analytics
* Error tracking
* Cron/background jobs

Provider status values:

* NOT_CONFIGURED
* DEV_ONLY
* SETUP_REQUIRED
* CONFIGURED
* TESTING
* ACTIVE
* FAILED
* DISABLED
* BLOCKED

No fake active status.

---

## 35. Production Readiness Memory

Before production launch:

* dev OTP off
* test payment off
* mock provider off
* demo data removed/hidden after user approval
* real secrets in env only
* no secrets in client
* Supabase RLS final pass
* payment webhook verified
* OTP real delivery tested
* WhatsApp click/API tested
* email provider tested
* Cloudflare R2/CDN tested
* private docs tested
* maps tested/fallback tested
* notification badge tested
* cron jobs tested
* contact privacy tested
* property/project/requirement approval tested
* lead flow tested
* banner ad flow tested
* subscription/credit/boost tested
* verification badge tested
* build/type/lint pass
* responsive all sizes pass
* cross-browser pass
* load/stress test
* backup ready
* rollback ready
* final signoffs

Final status:

* PASS
* PARTIAL
* FAIL
* BLOCKED

No fake production PASS.

---

## 36. Claude Workflow Memory

Claude must:

* keep prompts token-light
* use docs as source of truth
* read relevant docs only
* inspect files before coding
* avoid duplicates
* avoid removing working features
* update docs after changes
* create/update SQL migrations for DB/RLS changes
* run tests or document why not
* mark verification honestly
* write concise final response
* include changed files, SQL files, tests, verification, pending issues
* keep resume guide updated

Claude must not:

* paste large docs repeatedly
* paste full logs
* expose secrets
* fake completion
* skip rules
* silently ignore unclear requirements
* silently move feature to nowhere
* mark PASS with errors
* continue next phase without PASS/user approval

---

## 37. Current File Inventory

Current intended final documentation pack:

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
* `prompts/01_PROJECT_SETUP_BASELINE.md`
* `prompts/01_MANUAL_VERIFICATION_PROJECT_SETUP_BASELINE.md`
* `prompts/02_AUTH_ROLES_RLS_FOUNDATION.md`
* `prompts/02_MANUAL_VERIFICATION_AUTH_ROLES_RLS_FOUNDATION.md`
* `prompts/03_PUBLIC_UI_HOME_HEADER_FOOTER_HERO.md`
* `prompts/03_MANUAL_VERIFICATION_PUBLIC_UI_HOME_HEADER_FOOTER_HERO.md`
* `prompts/04_PROPERTY_PROJECT_REQUIREMENT_SYSTEM.md`
* `prompts/04_MANUAL_VERIFICATION_PROPERTY_PROJECT_REQUIREMENT_SYSTEM.md`
* `prompts/05_PUBLIC_SEARCH_DETAIL_PROFILE_SEO.md`
* `prompts/05_MANUAL_VERIFICATION_PUBLIC_SEARCH_DETAIL_PROFILE_SEO.md`
* `prompts/06_OWNER_BROKER_BUILDER_DASHBOARDS.md`
* `prompts/06_MANUAL_VERIFICATION_OWNER_BROKER_BUILDER_DASHBOARDS.md`
* `prompts/07_ADMIN_STAFF_SUPER_ADMIN_SYSTEM.md`
* `prompts/07_MANUAL_VERIFICATION_ADMIN_STAFF_SUPER_ADMIN_SYSTEM.md`
* `prompts/08_LEADS_CRM_REQUIREMENTS_PROPOSALS_MESSAGES.md`
* `prompts/08_MANUAL_VERIFICATION_LEADS_CRM_REQUIREMENTS_PROPOSALS_MESSAGES.md`
* `prompts/09_BILLING_PAYMENT_SUBSCRIPTION_TRIAL_GST.md`
* `prompts/09_MANUAL_VERIFICATION_BILLING_PAYMENT_SUBSCRIPTION_TRIAL_GST.md`
* `prompts/10_MEDIA_STORAGE_UPLOADS_R2_CDN.md`
* `prompts/10_MANUAL_VERIFICATION_MEDIA_STORAGE_UPLOADS_R2_CDN.md`
* `prompts/11_LOCATION_SEARCH_SEO_CMS_LEGAL.md`
* `prompts/11_MANUAL_VERIFICATION_LOCATION_SEARCH_SEO_CMS_LEGAL.md`
* `prompts/12_ADS_PROMOTION_NOTIFICATIONS_PROVIDERS.md`
* `prompts/12_MANUAL_VERIFICATION_ADS_PROMOTION_NOTIFICATIONS_PROVIDERS.md`
* `prompts/13_SECURITY_PRIVACY_FRAUD_RATE_LIMITS.md`
* `prompts/13_MANUAL_VERIFICATION_SECURITY_PRIVACY_FRAUD_RATE_LIMITS.md`
* `prompts/14_PERFORMANCE_CACHING_DEPLOYMENT_LAUNCH.md`
* `prompts/14_MANUAL_VERIFICATION_PERFORMANCE_CACHING_DEPLOYMENT_LAUNCH.md`
* `prompts/15_FINAL_PRODUCTION_API_TESTING_AND_SIGNOFF.md`
* `prompts/15_MANUAL_VERIFICATION_FINAL_PRODUCTION_API_TESTING_AND_SIGNOFF.md`

---

## 38. Current Known Implementation Status

No actual application implementation has been performed yet in this memory state.

Current status by area:

* Documentation generation: `IN_PROGRESS`
* Project code setup: `NOT_STARTED`
* Supabase setup: `NOT_STARTED`
* Auth implementation: `NOT_STARTED`
* RLS implementation: `NOT_STARTED`
* Public UI: `NOT_STARTED`
* Owner dashboard: `NOT_STARTED`
* Broker dashboard: `NOT_STARTED`
* Builder dashboard: `NOT_STARTED`
* Admin dashboard: `NOT_STARTED`
* Property module: `NOT_STARTED`
* Project module: `NOT_STARTED`
* Requirement module: `NOT_STARTED`
* Leads CRM: `NOT_STARTED`
* Messages: `NOT_STARTED`
* Site visits: `NOT_STARTED`
* Notifications: `NOT_STARTED`
* Billing/subscription: `NOT_STARTED`
* Razorpay: `SETUP_REQUIRED`
* GST/invoices: `NOT_STARTED`
* Banner ads: `NOT_STARTED`
* Media upload: `NOT_STARTED`
* Cloudflare R2/CDN: `SETUP_REQUIRED`
* SEO/CMS/blog/legal pages: `NOT_STARTED`
* Search/location: `NOT_STARTED`
* Security/rate limits: `NOT_STARTED`
* Deployment/rollback: `NOT_STARTED`
* Production readiness: `NOT_STARTED`

---

## 39. Current SQL / Migration Memory

Current SQL migrations created: None.

Migration folder not confirmed yet.

Future migration rules:

* Use phase-wise/timestamp-wise naming.
* Every DB/RLS/table/enum/index/trigger/function change must create/update a migration.
* Migration must include rollback notes.
* RLS policies must be created with the table.
* Public-safe views must not leak private data.
* Sensitive fields must never be exposed publicly.
* Destructive changes require backup/rollback notes and approval.

---

## 40. Current Provider Memory

Current provider implementation status:

* Supabase Auth: `NOT_STARTED`
* Supabase PostgreSQL: `NOT_STARTED`
* Supabase RLS: `NOT_STARTED`
* Cloudflare R2: `SETUP_REQUIRED`
* Cloudflare CDN: `SETUP_REQUIRED`
* OTP Provider: `SETUP_REQUIRED`
* WhatsApp free mode: `SETUP_REQUIRED`
* WhatsApp Business API: `SETUP_REQUIRED`
* Email Provider: `SETUP_REQUIRED`
* SMS Provider: `SETUP_REQUIRED`
* Razorpay: `SETUP_REQUIRED`
* Google Maps Embed/API: `SETUP_REQUIRED`
* Analytics: `SETUP_REQUIRED`
* Error Tracking: `SETUP_REQUIRED`
* Cron/Background Jobs: `NOT_STARTED`

Provider rule:

* Missing provider must show `SETUP_REQUIRED`.
* No fake success.
* Production must disable dev/mock/test modes.

---

## 41. Current UI Memory

Current UI implementation status: `NOT_STARTED`

Existing user note:

* Previous project has guest visitor and owner role home page design ready.
* Only home page exists for without-login user and logged-in Owner.
* No dashboard and no other role currently confirmed as built.
* Old home page hero search section may need to be copied/migrated from old project/live link when that phase is requested.
* If hero migration is requested, copy only existing hero search section, not header/footer, no redesign, keep same design, spacing, layout, colors, tabs, chips, badges and responsive behavior.

Global UI target:

* mobile-first
* white-first
* premium
* Apple-style
* clean
* real-estate portal style
* no horizontal scroll
* no text wrap issue
* no overlap
* no dead buttons
* all states

---

## 42. Current Security Memory

Security implementation status: `NOT_STARTED`

Security requirements to enforce during implementation:

* RLS enabled on sensitive tables
* role access matrix
* route guards
* server-side authorization
* rate limiting
* no service key client exposure
* hidden contact protection
* direct URL bypass block
* safe file upload
* safe errors
* audit logs
* staff permission scopes
* high-risk action confirmation
* payment webhook verification
* production debug block
* secrets scanning
* log redaction

---

## 43. Current Manual Verification Memory

Manual verification status: `NOT_STARTED`

Future manual verification must include:

* guest flow
* login/register
* wrong/unregistered mobile register message
* owner redirect
* broker redirect
* builder redirect
* admin/staff login separation
* direct URL unauthorized block
* property post
* project post
* requirement post
* inquiry/contact privacy
* lead flow
* notification badge/deep link
* responsive checks
* text wrap checks
* no horizontal scroll
* no overlap
* mobile/tablet/desktop
* loading/empty/error states
* RLS allowed/denied tests
* provider setup-required states
* payment states
* build/lint/typecheck
* cross-browser where required

Results must be:

* PASS
* PARTIAL
* BLOCKED
* FAIL

No vague “done”.

---

## 44. Current Conflict Notes

No confirmed conflicts yet.

Conflict handling rule:

If old/current docs conflict, follow the latest/current master rule from the generated documentation pack and add a note here.

Conflict log format:

```md
### Conflict YYYY-MM-DD
- Area:
- Old rule:
- Current master rule:
- Decision:
- Files updated:
- Pending action:
```

---

## 45. Current Temporary Workarounds

No temporary workarounds yet.

Temporary workaround format:

```md
### Workaround YYYY-MM-DD
- Area:
- Reason:
- Temporary behavior:
- Removal condition:
- Risk:
- Owner:
- Feature Registry item:
```

Any workaround must also be added to `BUGS_AND_FIXES.md` if it affects correctness or production readiness.

---

## 46. Current Pending Questions / Safe Defaults

If any future requirement is unclear, Claude must not skip it.

Use one of these safe defaults:

* permission-based implementation
* setup-required state
* feature flag
* blocked status
* partial status
* deferred but tracked status

Current safe defaults:

1. Missing provider/API: show `SETUP_REQUIRED`, do not fake.
2. Unclear admin permission: hide/disable module unless Super Admin or explicit permission.
3. Unclear public privacy: keep data private.
4. Unclear contact visibility: hide contact.
5. Unclear listing status: require approval before public display.
6. Unclear payment state: do not activate plan.
7. Unclear verification state: do not show verified badge.
8. Unclear media privacy: keep private.
9. Unclear SEO page data: noindex/hide until real content/listings exist.
10. Unclear destructive action: soft delete and audit, do not hard delete.

---

## 47. Phase Resume Guide

Current phase: Documentation generation.

Last completed file: `CLAUDE.md`

Current completed file: `brain.md`

Next file to generate: `FEATURE_REGISTRY.md`

Next Claude/assistant should:

1. Continue generating documentation pack in exact agreed order.
2. Do not skip any rule from the two pasted txt sources.
3. Keep root docs detailed enough for Claude Code continuity.
4. Avoid listing only prompts-to-Claude; generate actual file content.
5. Use writing blocks for reusable file content.
6. Cite source pasted txt outside writing block when responding in ChatGPT.
7. After completing each file, mention the next file number/path.
8. If a response cannot fit the full file, clearly say where to continue.
9. Do not generate code implementation yet.
10. Do not create fake status as if website has been built.

---

## 48. Resume Summary For Another Claude Account

You are building the documentation and prompt system for **My Gujarat Property**, a production-grade Gujarat real estate marketplace.

The user has provided two large pasted text requirements:

1. Full website/product/system requirements.
2. Claude Code token-light workflow, documentation, prompt and verification requirements.

The final agreed output is:

* 26 detailed documentation files
* 31 prompt files
* total 57 files

The user wants each file generated fully, one by one, with no skipped or missed requirement.

Already generated:

* `CLAUDE.md`
* `brain.md`

Next generate:

* `FEATURE_REGISTRY.md`

Do not start actual website coding yet.

Main non-negotiable principle:

Nothing from the provided requirements may be skipped or silently dropped. If something is unclear, create a safe tracked rule instead of ignoring it.

## Mandatory Role-Based Home Design Clarification

In addition to all saved docs and prompts, treat role-based home design as mandatory.

Create/design separate role-specific landing/home/dashboard experiences for:

* Guest/Public Home
* Owner Home
* Broker/Agent Home
* Builder/Developer Home

Do not use one generic dashboard/home for all roles.

Each role home must have its own layout, cards, CTAs, modules, quick actions, navigation priorities, real-data/no-data stats, notifications, billing/status blocks, support links, and mobile-first responsive design.

Guest/Public Home must focus on search, city selector, public property/project discovery, login/register popup triggers, SEO sections, public-safe content, and hidden contact protection.

Owner Home must focus on post property, post requirement, own listings, own requirements, leads, inquiries, messages, notifications, billing, profile, verification, and support.

Broker/Agent Home must focus on post property, post requirement, CRM, leads, proposals, messages, site visits, saved searches, billing, verification, public profile, and support.

Builder/Developer Home must focus on post project only, project inventory, project leads, matching buying requirements, proposals, messages, site visits, ads/promotions, RERA/payment status, billing, profile, verification, and support.

All role homes must be mobile-first, responsive, no horizontal scroll, no fake counts, no fake analytics, no fake leads, no fake payment, no fake provider data, and no private/hidden contact leaks.

Implement and verify this requirement during:

* prompts/03_PUBLIC_UI_HOME_HEADER_FOOTER_HERO.md
* prompts/06_OWNER_BROKER_BUILDER_DASHBOARDS.md
* prompts/14_PERFORMANCE_CACHING_DEPLOYMENT_LAUNCH.md
* prompts/15_FINAL_PRODUCTION_API_TESTING_AND_SIGNOFF.md
