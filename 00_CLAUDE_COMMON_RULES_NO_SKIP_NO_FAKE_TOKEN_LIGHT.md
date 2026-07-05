# MY GUJARAT PROPERTY

# CLAUDE COMMON RULES — NO SKIP, NO FAKE UI, TOKEN-LIGHT DEVELOPMENT SYSTEM

## FILE NAME

`00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`

---

# 1. DOCUMENT PURPOSE

This document is the master rulebook for Claude / AI developer working on **My Gujarat Property**.

Every development phase, documentation phase, prompt phase, refactor phase, UI phase, backend phase, admin phase, database phase, SEO phase, dashboard phase, payment phase, provider phase and QA phase must follow this file first.

This file exists to make sure:

1. Nothing from the user’s uploaded documents is skipped.
2. Nothing from the user’s chat instructions is skipped.
3. Development remains token-light for Claude.
4. Detailed requirements stay inside documentation files.
5. Prompts remain medium-sized and phase-based.
6. No fake production UI is created.
7. Mobile-first design remains highest priority.
8. Role-based behavior is applied across the entire website.
9. Super Admin gets full platform control.
10. Manual verification is separated from common rules and handled in a dedicated verification prompt system.
11. Screenshot, video and sample-image-reference instructions are removed from the new documentation system.

This file is not a feature document by itself.

This file tells Claude how to work, what to respect, what to avoid, what to inspect, what to verify, and how to decide priority when instructions conflict.

---

# 1B. DEVELOPMENT TEST / SEED / DEMO DATA RULE (USER DIRECTIVE)

During active development, **test users, seed/demo listings, demo leads and other
development fixtures MUST NOT be deleted.** The user keeps this data in the live
project on purpose so each part can be built and visually checked against
realistic content.

Rules:

1. Do **not** auto-clean up test users, demo properties, demo media or demo leads
   after a verification run while development is ongoing.
2. Seed/demo data may be created and may persist in the live Supabase project
   during development. This is an explicit, authorized exception to the
   "no fake data" rule — which still fully applies to **production launch** and to
   never *faking success* (no fake OTP/payment/WhatsApp-sent/verified badge/counts).
3. Only delete seed/demo/test data when the **user explicitly says development is
   complete** (e.g. "development complete, remove fake data"). Until then, leave it.
4. Mark seeded rows so they can be cleanly removed later — e.g. `details.seed = true`
   on properties — and keep the seed script in the repo (`scripts/seed-dev-data.mjs`).
5. Real, user-created data must never be touched by seed cleanup — only rows flagged
   as seed.

This rule overrides any earlier "clean up test users after the run" guidance for the
development phase.

---

# 2. PROJECT IDENTITY

## Project Name

```txt
My Gujarat Property
```

## Project Type

```txt
AI-first real estate property marketplace for Gujarat, later scalable to all India.
```

## Primary Launch Market

```txt
Gujarat, India
```

## Future Scale

```txt
All India
```

## Core Platform Purpose

My Gujarat Property helps:

* Buyers find properties.
* Tenants find rentals, PG, hostel and co-living options.
* Owners list their properties.
* Brokers manage listings, leads and buyer requirements.
* Agencies manage teams, agents, listings and leads.
* Builders and developers manage projects, units and enquiries.
* Real estate groups and agencies promote themselves through approved paid banner ads.
* Admin and Super Admin control moderation, settings, pricing, subscriptions, SEO, providers, users, roles, verification and platform operations.

The platform is a property listing, discovery, lead generation and real estate operating system.

The platform is not a property transaction settlement platform.

---

# 3. WHAT THE PLATFORM CAN HANDLE

My Gujarat Property can handle:

* Property listings
* Project listings
* Buyer requirements
* Tenant requirements
* Requirement marketplace
* Broker proposals
* Seller/broker/agency/builder leads
* Contact requests
* WhatsApp contact flow
* Lead forms
* Site visit coordination
* Messaging if implemented
* In-app notifications
* Search and filters
* City/locality SEO pages
* Broker/agency/builder public profiles
* Role-based dashboards
* Admin moderation
* Verification workflows
* Subscription plans
* Paid listing plans
* Featured listings
* Boosts
* Homepage banner ads
* City-targeted banner ads
* Sponsored placements
* Credits if implemented
* Platform payments
* Invoices if implemented
* CMS/blog/FAQ/static pages
* Super Admin settings and feature flags

---

# 4. WHAT THE PLATFORM MUST NOT HANDLE

My Gujarat Property must not handle:

* Property token amount
* Property booking amount
* Sale deed payment
* Ownership transfer payment
* Legal registration payment
* Escrow
* Rent collection
* Loan disbursement
* Buyer-seller settlement
* Builder booking payment
* Agreement signing payment
* Land registration payment
* Any actual real estate transaction settlement between buyer and seller

The platform only connects, lists, promotes, generates leads, coordinates visits and supports platform-level monetization.

Any payment system must be limited to:

* Subscription plans
* Listing fees
* Featured boosts
* Banner ads
* Sponsored placements
* Credits
* Requirement promotion
* Profile promotion
* Platform services

---

# 5. DEFAULT TECHNOLOGY STACK

Unless the actual codebase is different, the planned stack is:

* Next.js 15
* App Router
* TypeScript
* Tailwind CSS
* Supabase Auth
* Supabase PostgreSQL
* Supabase Storage
* Supabase RLS
* Supabase SSR
* Server Components
* Client Components where needed
* Server Actions
* Route Handlers
* Zod or equivalent validation
* Role-based access control
* Mobile-first responsive UI

Claude must inspect the current project before coding.

Claude must not assume the project is empty unless the project folder is actually empty.

Claude must not assume the stack blindly if the existing codebase is different.

If the stack differs, Claude must adapt carefully and report the difference.

---

# 6. SOURCE OF TRUTH PRIORITY

When instructions conflict, Claude must follow this priority order:

1. User’s latest direct instruction in chat
2. This file: `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
3. New regenerated documentation files
4. Uploaded current documentation files
5. Uploaded old blueprint PDFs
6. Uploaded design blueprint PDFs
7. Existing codebase
8. Public real estate UX references for behavior only
9. Claude’s own assumption last

Claude must not override the user’s latest instruction unless it causes:

* Security risk
* Illegal behavior
* Broken production behavior
* Data leak
* Fake payment
* Fake provider success
* Fake production UI
* Loss of existing working feature
* Exposure of secrets

If a latest user instruction conflicts with older docs, update behavior according to the latest user instruction.

---

# 7. ABSOLUTE NO-SKIP RULE

Claude must not skip any requirement silently.

Requirements come from:

* Uploaded Markdown files
* Uploaded PDFs
* Uploaded prompt PDFs
* Chat instructions
* New instructions from user
* Current final regenerated docs
* Existing codebase behavior that should not be broken

If something cannot be implemented in the current phase:

Claude must:

1. Mark it as pending, blocked, future or partial.
2. Add it to the phase report.
3. Add it to the feature registry.
4. Explain why it cannot be completed now.
5. Keep UI safe.
6. Never pretend it is complete.

Claude must never say:

```txt
Done
```

unless the specific feature is implemented, connected, verified and safe.

Claude must never say:

```txt
Everything is complete
```

unless all relevant checks for that phase have passed.

---

# 8. TOKEN-LIGHT RULE

The project must use a token-light Claude development system.

Detailed requirements live inside the documentation files.

Claude prompts must not repeat all details every time.

Prompts should be medium-sized.

A good phase prompt should:

1. Tell Claude which docs to read.
2. Tell Claude the exact phase scope.
3. Mention required providers/APIs at the top if needed.
4. Tell Claude what to implement.
5. Tell Claude what not to fake.
6. Tell Claude to update feature registry.
7. Tell Claude to update phase report.
8. Include manual verification instructions or reference the manual verification prompt.
9. Ask Claude for PASS / FAIL / PARTIAL.

A prompt should not dump the full 20+ documentation files into one chat.

Claude should read only the relevant docs for each phase.

Claude must not reread all docs for every small task unless the phase requires it.

---

# 9. DOCUMENTATION READ RULE

Every phase must read this file first.

Then Claude must read only the required files for that phase.

Example:

For homepage/header/search phase, read:

```txt
/docs/new-docs/00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md
/docs/new-docs/01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md
/docs/new-docs/03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md
/docs/new-docs/04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md
/docs/new-docs/22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
```

For auth phase, read:

```txt
/docs/new-docs/00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md
/docs/new-docs/06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md
/docs/new-docs/07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md
/docs/new-docs/17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
/docs/new-docs/22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
```

For banner ads phase, read:

```txt
/docs/new-docs/00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md
/docs/new-docs/14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md
/docs/new-docs/15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md
/docs/new-docs/13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
/docs/new-docs/22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
```

Claude must not guess requirements if a related doc exists.

---

# 10. NEW DOCUMENTATION FILE SET

The regenerated documentation system may include files such as:

```txt
00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md
01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md
02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md
03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md
04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md
05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md
06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md
07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md
08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md
09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md
10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md
11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md
12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md
13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md
15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md
16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md
19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md
20_CMS_BLOG_STATIC_PAGES_LEGAL_CONTENT_SPEC.md
21_FEATURE_REGISTRY_TEMPLATE.md
22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
23_TOKEN_LIGHT_CLAUDE_PHASE_PROMPTS_D0_TO_D15.md
```

Claude must use the actual files that exist in the project.

If file names change later, Claude must follow the latest provided file names.

---

# 11. REMOVED INSTRUCTION: SCREENSHOT AND VIDEO CAPTURE

The new documentation system must remove screenshot and video capture instructions.

Claude must not be required to:

* Capture website screenshots for design reference.
* Capture Housing.com screenshots.
* Capture videos.
* Store screenshot evidence.
* Create screenshot folders.
* Create video recordings.
* Fail a phase only because screenshots or videos were not captured.

Manual browser/UI verification can still happen.

The removal applies only to screenshot/video capture requirements.

Claude can still visually inspect the UI using browser tools if available, but must not make screenshot/video capture a required output.

If user explicitly asks later for screenshots or videos, that specific request can be handled separately.

---

# 12. REMOVED INSTRUCTION: SAMPLE PHOTO / SAMPLE IMAGE DESIGN REFERENCE

The new documentation system must remove dependency on user-provided sample photos or sample UI images.

Claude must not be required to:

* Use sample UI screenshots as design source of truth.
* Create sample image index.
* Create sample image README.
* Copy or follow uploaded sample photos.
* Treat sample photos as final approved UI.
* Fail a phase because sample images are missing.

The final design must be based on:

1. Documentation requirements
2. Feature matrix
3. Role logic
4. Mobile-first UX rules
5. Original My Gujarat Property brand
6. Indian real estate marketplace behavior
7. Clean professional design principles

If user later explicitly provides images for a specific comparison, Claude can analyze them for that specific task only.

But the regenerated core docs must not depend on sample-image instructions.

---

# 13. UX REFERENCE RULE

Claude may study leading Indian real estate platforms for UX behavior only.

Allowed:

* Search-first homepage behavior
* Mobile header behavior
* City selector behavior
* Filter behavior
* Property card information hierarchy
* Property detail conversion flow
* Login/OTP usability pattern
* Mobile bottom sheet behavior
* Sticky CTA behavior
* Dashboard usability pattern
* SEO city page structure
* Pricing visibility pattern

Not allowed:

* Copying logo
* Copying brand colors
* Copying exact UI
* Copying exact layout pixel-by-pixel
* Copying images
* Copying copyrighted text
* Copying CSS/classes/code
* Copying proprietary assets

My Gujarat Property must remain original.

The target is:

```txt
Premium Indian real estate marketplace UX quality with original My Gujarat Property identity.
```

---

# 14. DESIGN RULES

Design must be:

* Mobile-first
* White-first
* Clean
* Trust-focused
* Professional
* Fast
* Real estate marketplace style
* App-like on mobile
* Easy for non-technical users
* Role-aware
* Search-first
* Conversion-focused
* Dashboard-friendly
* Admin-operational
* Accessible
* Responsive
* No horizontal scroll

Avoid:

* Dark admin template look
* Random gradients
* Heavy glassmorphism
* Neumorphism
* Flashy animations
* Cluttered cards
* Tiny touch targets
* Desktop-only tables
* Broken sticky elements
* Fake metrics
* Fake badges
* Fake notifications
* Broken empty states
* Generic SaaS landing page look

---

# 15. MOBILE-FIRST RULE

Most users will come from mobile.

Therefore mobile is primary.

Desktop is secondary.

Every public page, dashboard, form, modal, drawer, bottom sheet and admin queue must work properly on mobile.

Important mobile widths:

```txt
320px
360px
375px
390px
430px
768px
1024px
1366px+
```

Minimum important manual layout checks:

```txt
360px
390px
430px
768px
1366px
```

Mobile must not have:

* Horizontal scroll
* Broken header
* Two-line broken logo
* Cut buttons
* Overflowing cards
* Hidden CTA
* Tiny form controls
* Wide tables
* Broken sidebar
* Broken popup
* Modal overflow
* Sticky CTA covering important content
* Footer overlap
* Unreadable font size

---

# 16. MOBILE APP-LIKE RULE

Mobile web should feel like a real mobile app.

Use:

* Compact sticky header
* Bottom navigation where useful
* Bottom action bar where useful
* Back icon where navigation requires it
* Full-width cards
* Large CTAs
* Bottom sheets for filters
* Drawers for menus
* Role-based quick actions
* Card-based dashboards
* Table-to-card conversion
* Touch-friendly controls
* Clear empty states
* Fast search-first flow

Do not force desktop UI into mobile.

---

# 17. HEADER RULE

Header must be role-aware and login-state-aware.

Guest header may show:

* Logo
* City selector
* Search
* Login/Register
* Post Property CTA
* Menu

Logged-in header must show:

* Logo
* City selector
* Search
* Profile icon/avatar
* Active role if useful
* Notification icon if implemented
* Message icon if implemented
* Role-based dashboard entry
* Menu

Logged-in user must not see public Login/Register as the main action.

If the user is logged in, show profile/avatar instead.

If the user is not logged in, show Login/Register.

Admin login must not be shown in the public login/register popup.

Header must not wrap badly.

Wrong:

```txt
My Gujarat
Property
```

Correct:

```txt
My Gujarat Property
```

If width is small, use:

* Logo mark
* Short brand
* Ellipsis
* Icon-only actions
* Move low priority items to menu

---

# 18. SIDEBAR, DRAWER, POPUP AND MODAL CLOSE RULE

All overlays must close in user-friendly ways.

Applies to:

* Sidebar
* Drawer
* Hamburger menu
* Login popup
* Register popup
* Role selection popup
* Bottom sheet
* Filter sheet
* City selector popup
* Contact popup
* Lead form popup
* Image crop modal
* Payment modal
* Admin drawer
* Dashboard drawer

Must support:

* Close icon
* Outside overlay click / tap
* Escape key where applicable
* Back navigation where safe
* Proper focus return where possible

User must not be forced to click only the close icon.

---

# 19. AUTH AND LOGIN RULES

Login/register must be real and role-aware.

Public login/register behavior:

1. Same button can open login/register popup.
2. Popup shows Login and Register options.
3. New user must register first.
4. Registration must include role selection.
5. Public registration must not expose admin/staff roles.
6. After registration, OTP verification appears.
7. After OTP success, redirect to homepage or preserved current intent/query.
8. Existing user can login directly with OTP.
9. OTP autofill should be supported.
10. Mobile login/register must be primary.
11. Email field can exist, but phone number is primary verification method.
12. Email verification can happen later from profile using code/link.
13. Development mode can allow random/dev OTP.
14. Production mode must use real OTP provider.
15. Admin login must not be part of public login/register popup.

Admin/staff login must be separate and protected.

No fake OTP success in production.

No fake Google login.

No fake email verification.

No fake session.

No fake profile state.

---

# 20. DEVELOPMENT OTP RULE

During development, OTP cost should be avoided.

Development mode may allow:

* Random OTP login
* Static test OTP
* Dev OTP bypass
* Test user creation
* Seed users for all roles

But this must be clearly development-only.

Production mode must not allow random OTP login.

The project must include a safe environment flag pattern such as:

```txt
NEXT_PUBLIC_APP_ENV=development
DEV_AUTH_OTP_ENABLED=true
DEV_AUTH_STATIC_OTP=123456
```

or equivalent.

Claude must never expose dangerous bypass logic in production.

Dev OTP must be disabled for production builds.

---

# 21. SESSION RULE

If a user logs in, the website should remain logged in when the user returns later, unless:

* Session expired by configured timeout
* User logged out
* Admin revoked session
* Account suspended/banned
* Security policy requires re-login

Session timeout must be configurable from Admin/Super Admin settings if implemented.

Session settings may include:

* Default session duration
* Remember device option
* Force logout after X days
* Inactivity timeout
* Admin revoke all sessions
* Device/session list if implemented

A returning logged-in user must see logged-in UI, not guest Login/Register UI.

---

# 22. ROLE SYSTEM RULES

Main roles:

* Guest
* Buyer
* Tenant
* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Developer if separated later
* Real Estate Group if implemented separately
* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager
* Admin
* Super Admin

A user may have multiple roles.

System must support:

* Active role
* Role-specific profile
* Role-specific dashboard
* Role-specific menu
* Role-specific header
* Role-specific permissions
* Role-specific subscription
* Role upgrade request
* Role change approval
* Role verification
* Admin-approved staff roles
* Protected admin roles

Admin/staff roles must not be publicly self-selectable.

---

# 23. ROLE CHANGE APPROVAL RULE

Users cannot freely switch into business/admin roles without approval if the role requires verification.

Role change flow:

1. User opens profile.
2. User selects request new role.
3. User submits required details/documents.
4. System creates role change/upgrade request.
5. Admin reviews request.
6. Admin approves, rejects or asks for more details.
7. On approval, new role becomes available.
8. User can switch active role if allowed.

If user has an active subscription in the current role and wants to move to another role, system must define plan migration rules.

Possible handling:

* Keep current plan active until expiry for current role.
* Ask user to buy plan for new role separately.
* Allow upgrade with credit adjustment if payment system supports it.
* Allow admin-controlled manual migration.
* Prevent automatic downgrade abuse.
* Prevent using one role plan for unrelated role features.
* Show clear message to user before role migration.

Do not silently transfer subscription if plan compatibility is not defined.

---

# 24. ROLE-BASED PROFILE RULE

Profile must be role-based.

Common profile fields may include:

* Full name
* Phone
* Email
* Avatar
* City
* Language
* Active role
* Profile completion
* Verification status
* Subscription/plan status
* Notification preferences
* Security settings

Buyer profile may include:

* Preferred cities
* Saved properties
* Saved searches
* Requirements
* Budget preference
* Contact preference

Tenant profile may include:

* Rental preference
* PG/hostel preference
* Move-in timeline
* Food/sharing preference
* Saved rentals

Owner profile may include:

* Owner verification
* Own properties
* Contact preference
* Listing plan

Broker profile may include:

* Broker photo/logo
* Business name
* RERA/license details if applicable
* Operating cities
* Localities served
* Experience
* Property types handled
* Brokerage policy
* Verification documents
* Public profile
* Subscription plan

Agency profile may include:

* Agency logo
* Agency name
* Registered business details
* Team/agents
* Operating cities
* Office address
* Website/social links
* Agency verification
* Subscription plan

Builder profile may include:

* Builder logo
* Company name
* RERA/builder registration details
* Projects
* Office address
* Contact team
* Verification status
* Public profile
* Subscription plan

Agent profile may include:

* Assigned agency
* Assigned leads
* Assigned listings
* Performance if implemented
* Permission scope

Admin/staff profile may include:

* Staff role
* Permission scope
* Assigned city
* Admin activity logs

---

# 25. RBAC RULE

Every protected action must check permissions.

Client hiding is not enough.

Protected actions must validate:

* Auth
* Active role
* Permission
* Ownership
* Assignment
* City scope
* Verification status
* Subscription status
* Feature flag
* Provider availability
* Rate limit if needed

Examples:

A broker cannot approve listings.

A buyer cannot access broker requirement feed.

An owner cannot manage another owner’s property.

An agent cannot view unassigned agency leads.

A city manager cannot manage other cities unless permitted.

A normal admin cannot delete Super Admin.

A user cannot self-assign admin role.

A user cannot self-edit subscription status.

---

# 26. NO-FAKE UI RULE

Never create fake production UI.

Do not fake:

* Login
* OTP success
* Email verification
* Google login
* WhatsApp API send
* SMS send
* Email send
* Push notification
* Payment success
* Subscription activation
* Invoice
* Map functionality
* Search results
* Property counts
* City counts
* Lead counts
* Contact numbers
* Messages
* Notifications
* Reviews
* Ratings
* Revenue
* Analytics
* Admin metrics
* Fraud score
* Match score
* Verification badge
* Featured badge
* Sponsored badge
* Credit balance
* Ad impression count
* Ad click count
* Realtime update
* Provider logs
* Audit logs

If a feature is not connected:

* Hide it, or
* Disable it with clear reason, or
* Show setup-required state in admin/dev context, or
* Mark it as future in docs.

Do not show fake success to users.

---

## GLOBAL RESPONSIVE UI QUALITY RULE

Every UI generated in this project must be fully responsive, clean and production-ready across desktop, laptop, tablet and mobile.

Claude must apply this rule globally to every page, layout, header, sidebar, modal, popup, form, card, dashboard, table, drawer, bottom sheet, button, navigation, filter, search section and admin screen.

Rules:

* No unwanted text wrapping.
* No broken 2-line or 3-line desktop layout unless intentionally designed.
* No horizontal scroll on mobile, tablet or desktop.
* Desktop layouts must stay clean, aligned and single-row where expected.
* Mobile layouts must be app-like, touch-friendly and readable.
* Tables must become cards on mobile.
* Modals/popups must be properly responsive.
* Mobile modals should become bottom sheet or full-screen when needed.
* Sidebars/drawers must always open above page content.
* Overlays must use correct fixed position, backdrop, body scroll lock and z-index.
* Buttons, icons, filters and form fields must be clickable and properly spaced.
* UI must not go behind header, homepage, cards, hero section or other content.
* Design must follow clean white/green brand style.
* Do not use harsh random colors that break the design.
* Do not break already good mobile or desktop design while fixing another screen.
* Every generated UI must be tested on desktop, laptop, tablet and mobile sizes.

Before marking any UI work done, Claude must manually verify:

* desktop layout
* laptop layout
* tablet layout
* mobile layout
* no horizontal scroll
* no broken wrapping
* no content overlap
* no hidden buttons
* no broken modal/drawer/sidebar
* no z-index issue
* no form usability issue
* no design inconsistency

If any responsive or design issue is found, Claude must fix it and retest before giving PASS.


# 27. DEVELOPMENT DEMO DATA RULE

For development, fake/demo/seed users and properties are allowed.

This is allowed only for:

* UI development
* Layout testing
* Role-based dashboard testing
* Search layout testing
* Form testing
* Mobile testing
* Admin queue testing
* Claude manual verification

Development demo data must be clearly marked as:

```txt
Demo / Seed / Development Only
```

Production must remove or disable demo data.

Before launch, Claude must include production cleanup:

* Remove seed users
* Remove fake properties
* Remove fake leads
* Remove fake requirements
* Remove fake ads
* Remove fake payments
* Remove demo banners
* Disable dev OTP
* Disable debug routes
* Disable unsafe provider mocks

Demo data must never be presented as real production listings.

---

# 28. PROPERTY AND SEARCH RULES

Search must be real and useful.

Homepage must include Indian real estate style property search.

Search should not be only a separate page.

Homepage search must support:

* City
* Locality
* Society
* Project
* Builder
* Broker
* Property ID
* RERA number
* Purpose
* Budget
* BHK
* Property type
* Land
* Commercial
* Plot
* Rent
* PG/Hostel
* Buyer Requirements if enabled

Filters must change by selected purpose/property type.

Example:

If user selects land, do not show BHK.

If user selects PG, show PG-relevant filters.

If user selects commercial, show commercial-relevant filters.

If user selects rent, show rent-relevant filters.

If user selects project, show project-relevant filters.

No fake counts.

No fake autocomplete.

No fake results.

If no data exists, show empty state.

---

# 29. LOCATION RULE

Location system must support Gujarat-first scaling.

Required hierarchy:

```txt
Country → State → District → Taluka → City / Village → Area → Locality → Society → Building → Landmark
```

Fields should use English labels in UI.

Examples:

* State
* District
* Taluka
* City
* Village
* Area
* Locality
* Society
* Building
* Landmark
* Address Line
* Pin Code
* Map Location

Dropdowns must be cascading and dynamic.

Example:

1. User selects Gujarat.
2. District options load.
3. User selects Rajkot district.
4. Taluka options load.
5. User selects taluka.
6. City/village/locality options load.

No page refresh should be required.

If a city, taluka, village or locality is missing, user should be able to:

* Request new location
* Add custom location if allowed
* Enter manual location text for review

Admin must be able to approve/manage locations.

---

# 30. PROPERTY POSTING RULE

Property posting must start by selecting listing/property type.

The selected type decides which fields appear.

Examples:

Residential flat fields should differ from land fields.

Commercial shop fields should differ from PG fields.

Agricultural land fields should differ from apartment fields.

Project/unit fields should differ from individual property fields.

Claude must not show irrelevant fields.

Example wrong behavior:

```txt
User selects Land, but BHK field appears.
```

Correct behavior:

```txt
User selects Land, so land area, road access, zoning, agriculture/non-agriculture, boundary, water/electricity and survey-related fields may appear.
```

Every property type must define:

* Required fields
* Optional fields
* Media rules
* Location rules
* Contact visibility
* Approval workflow
* Expiry behavior
* Plan limits

---

# 31. IMAGE UPLOAD GLOBAL RULE

Every upload UI must clearly show recommended image size and ratio.

Applies to:

* Profile avatar
* Broker photo
* Broker logo
* Agency logo
* Builder logo
* Project logo
* Property images
* Project images
* Floor plans
* Brochures
* Banner ads
* Homepage carousel banners
* Mobile banner images
* Tablet banner images
* Desktop banner images
* Blog images
* CMS images
* Verification documents
* Support attachments
* Message attachments if implemented

Image upload should support where appropriate:

* Crop
* Preview
* Replace
* Delete
* Reorder
* Auto-resize
* Auto-fit
* Safe compression
* Wrong-size warning
* Recommended size text
* File type validation
* File size validation
* Alt text where SEO image
* Separate desktop/tablet/mobile variants for banners

If uploaded size is different, system should handle it safely without breaking layout.

---

# 32. CONTACT AND LEAD RULE

Lead/contact flows must be user-friendly and data-safe.

When user submits lead/contact interest:

User should be able to choose:

1. Use current profile phone number.
2. Enter alternate phone number.

If alternate phone number is entered:

* Validate phone number.
* Store it with the lead.
* Show receiver that user used alternate number.
* Do not overwrite profile phone unless user explicitly chooses to update profile.
* Track lead source.

Lead receiver dashboard must clearly show:

```txt
Alternate number used
```

or similar.

Hidden seller contact must not leak in public queries.

Contact reveal must be server-checked.

---

# 33. WHATSAPP PROVIDER RULE

WhatsApp must support two modes:

## Mode 1 — Free Link Mode

Uses:

```txt
wa.me
```

Useful when WhatsApp API is not configured.

## Mode 2 — API Mode

Uses official/paid WhatsApp provider/API if configured.

Admin/Super Admin must be able to choose one active mode.

One mode must be mandatory if WhatsApp contact is enabled.

Rules:

* If API mode is active but API is not configured, show setup-required state.
* If free mode is active, use wa.me links.
* Do not fake API send.
* Do not show sent status unless real.
* Admin can switch mode.
* Provider keys must stay server-side.

---

# 34. MAP PROVIDER RULE

Map system must support multiple modes.

Possible modes:

* Disabled
* Free embed/trial mode
* Premium Google Maps API mode

Admin/Super Admin must choose active map mode.

Rules:

* If premium API key missing, do not fake interactive map.
* If embed mode active, use allowed embed behavior.
* If disabled, hide map or show unavailable state.
* Map provider setting must affect UI.
* Map API keys must be protected.
* Do not load heavy map scripts unnecessarily.

---

# 35. SUBSCRIPTION AND PRICING RULE

Subscription/pricing must be visible to:

* Guest users
* Logged-in users

Guests can view plans.

Purchase/activation requires login and correct role.

Plans must be role-based.

Examples:

* Owner plan
* Broker plan
* Agency plan
* Builder plan
* Banner ads plan
* Boost plan
* Credit pack
* Requirement promotion plan

Plan limits must be enforced.

No frontend-only subscription activation.

No fake payment success.

If payment provider is missing, show setup-required or disable purchase.

---

# 36. HOMEPAGE BANNER ADS RULE

Homepage banner ads are a first-class paid feature.

This feature is mainly for:

* Agencies
* Real estate groups
* Brokers if enabled
* Builders if enabled
* Developers if enabled

Banner ads must support:

* Dashboard submission
* Separate cost
* Payment/plan/credit check
* Admin approval
* Rejection reason
* Scheduled start
* Expiry date
* Notification before expiry
* Auto hide after expiry
* Archive after expiry
* City targeting
* Carousel display
* Multiple advertisers
* Fair rotation
* Sponsored/ad label
* Desktop/tablet/mobile image variants
* Image ratio guide
* Click tracking
* Impression tracking if implemented

City priority rule:

If user is from Rajkot, Rajkot banners appear first.

If user is from Ahmedabad, Ahmedabad banners appear first.

If exact city banners are not enough, show other Gujarat city banners after local banners.

Location source priority may be:

1. User selected city
2. Logged-in user profile city
3. IP/location estimate if available
4. Browser location if permission granted
5. Default Gujarat/global ads

Do not block banners only because city is unknown.

Use fallback.

No fake ad impressions.

No fake ad clicks.

---

# 37. SEO RULE

SEO must support Google search intent.

Examples:

* Property sale in Rajkot
* Best property in Rajkot
* Rajkot property listing
* 2 BHK flat in Rajkot
* Plot for sale in Ahmedabad
* Commercial shop in Surat
* PG in Vadodara

SEO pages should support:

* City pages
* Locality pages
* Property type pages
* Purpose pages
* City + property type pages
* City + BHK pages
* City + price range pages if safe
* Project pages
* Builder pages
* Broker pages
* Agency pages
* Blog pages
* FAQ pages

Each SEO page should have:

* Dynamic title
* Meta description
* H1
* Short intro text
* Real listings
* Internal links
* Breadcrumb
* Canonical URL
* Sitemap entry
* Schema where useful

Do not create fake count pages.

Do not index thin empty pages.

If no real data exists, page should be noindex or show safe empty state.

---

# 38. ADMIN AND SUPER ADMIN CONTROL RULE

Super Admin should control the platform without developer help for normal business configuration.

Super Admin should control:

* Brand settings
* Cities
* Locations
* Roles
* Permissions
* Users
* Staff
* Properties
* Projects
* Requirements
* Leads
* Site visits
* Banner ads
* Subscriptions
* Payments
* Credits
* Boosts
* Pricing
* Feature flags
* Providers
* WhatsApp mode
* Map mode
* OTP provider
* Email provider
* API usage/limits
* Database/storage usage if available
* Session timeout
* Verification settings
* Moderation queues
* CMS
* SEO
* Blog
* Notifications
* Support
* Fraud queues
* Audit logs
* Maintenance mode

If a setting is visible, it must work.

No decorative/fake toggles.

---

# 39. NOTIFICATION AND EXPIRY RULE

Any time-limited feature must support expiry behavior.

Applies to:

* Property listing
* Buyer requirement
* Subscription
* Trial
* Featured boost
* Banner ad
* Sponsored profile
* Credits if expiring
* Project promotion

Expiry system should support:

* Expiry date
* Reminder before expiry
* Expired status
* Auto hide where required
* Archive where required
* Renewal option if allowed
* Admin override
* Notification log if implemented

Do not show expired paid feature as active.

---

# 40. MANUAL VERIFICATION RULE

Manual verification is required, but heavy manual verification instructions must live in:

```txt
22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
```

This common rules file keeps only the short rule.

Claude must verify the actual phase according to the dedicated manual verification prompt.

Manual verification should include where relevant:

* Guest view
* Logged-in view
* All role views
* Login/register flow
* Profile/header/sidebar changes
* Form fill
* Create/edit/delete where relevant
* Dashboard states
* Admin states
* Mobile layout
* Error states
* Empty states
* Provider missing states
* Security checks
* Auto-fix and retest
* PASS / FAIL / PARTIAL

Manual verification must not require screenshot/video capture.

---

# 41. BUILD AND CODE QUALITY RULE

Claude must inspect `package.json` before running commands.

If scripts exist, run available equivalents:

* lint
* typecheck
* build

Possible commands:

```txt
npm run lint
npm run typecheck
npm run build
```

or:

```txt
pnpm lint
pnpm typecheck
pnpm build
```

or:

```txt
yarn lint
yarn typecheck
yarn build
```

If script is missing, report honestly.

Do not claim missing checks passed.

Example:

```txt
Lint: PASS
Typecheck: Script missing
Build: PASS
```

If a check fails:

1. Fix.
2. Re-run.
3. Report final status.

---

# 42. FEATURE REGISTRY RULE

Every feature must be tracked in:

```txt
/docs/feature-registry.md
```

or the regenerated template:

```txt
21_FEATURE_REGISTRY_TEMPLATE.md
```

Feature registry should track:

* Feature name
* Related document
* Route
* Component
* Server action/API
* Database table
* Storage bucket
* Permission
* Role access
* Feature flag
* Provider dependency
* Loading state
* Empty state
* Error state
* Success state
* Mobile status
* Desktop status
* Security status
* No-fake UI status
* Test status
* Current status

No visible feature should be missing from feature registry.

---

# 43. PHASE REPORT RULE

Every Claude phase must create/update a phase report.

Recommended folder:

```txt
/docs/phase-reports/
```

Report should include:

* Phase name
* Docs read
* Scope
* Implemented items
* Not implemented items
* Files changed
* Routes changed
* Components changed
* Database changes
* Provider dependencies
* Feature registry updates
* Manual verification result
* Build result
* Issues found
* Fixes applied
* Remaining blockers
* Final status

Final status must be one of:

```txt
STATUS: PASS
STATUS: FAIL
STATUS: PARTIAL
STATUS: BLOCKED
```

Do not use vague status.

---

# 44. SECURITY RULE

Security must be server-side.

Never rely only on frontend hiding.

Protect:

* Admin routes
* Dashboards
* Contact details
* Leads
* Messages
* Site visits
* Private documents
* Verification documents
* Payments
* Subscriptions
* Settings
* Provider keys
* Service role key
* Audit logs
* Role assignment
* User status changes

Never expose:

* Supabase service role key
* DB password
* Payment secret
* Webhook secret
* WhatsApp token
* Email API key
* SMS key
* OTP provider secret
* Private map key if not public

Only public-safe environment variables can be exposed.

---

# 45. STORAGE RULE

Use separate storage buckets where needed.

Public media:

* Property images
* Project images
* Public logos
* Blog images
* CMS images

Private files:

* KYC documents
* Verification documents
* Private property documents
* Support attachments
* Admin files
* Payment documents if any

Private files must not be stored in public buckets.

Users must not access other users’ private files.

File type and file size validation must exist.

---

# 46. ACCESSIBILITY RULE

UI must be usable and accessible.

Important rules:

* Buttons must be real buttons.
* Links must be real links.
* Forms need labels.
* Errors must be readable.
* Touch targets should be large.
* Focus state should be visible.
* Modals should manage focus where possible.
* Icons need accessible labels if icon-only.
* Color should not be the only status indicator.
* Text contrast must be readable.
* Keyboard navigation should work where practical.

---

# 47. PERFORMANCE RULE

The website must be fast.

Rules:

* Avoid huge unnecessary JavaScript.
* Lazy-load heavy sections.
* Lazy-load maps.
* Optimize images.
* Use responsive images.
* Use pagination/infinite loading carefully.
* Avoid N+1 database queries.
* Use indexes for search.
* Keep public search queries lean.
* Do not load full dashboards on public pages.
* Avoid layout shift.
* Use skeletons where useful.

---

# 48. ERROR, EMPTY, LOADING AND SUCCESS STATE RULE

Every real feature should handle:

* Loading state
* Empty state
* Error state
* Success state if action-based
* Disabled state if unavailable
* Provider missing state if provider-dependent
* Permission denied state if role-restricted
* Expired state if time-limited
* Archived state if old/hidden

No blank screen.

No broken UI.

No silent failure.

---

# 49. PROVIDER MISSING STATE RULE

Provider-based features must not fake success.

Providers may include:

* OTP
* SMS
* Email
* WhatsApp API
* Google Maps
* Payment gateway
* Push notifications
* Analytics
* Storage processing

If provider is missing:

* Hide the feature, or
* Disable with reason, or
* Show setup-required state in admin/dev context.

Example:

If WhatsApp API is not configured, use wa.me mode if selected.

If Google Maps API is not configured, use embed mode or hide map depending on setting.

If payment provider is not configured, do not allow fake payment success.

---

# 50. PAYMENT RULE

Payments must be server-verified.

Payment flow must not activate plans from frontend callback only.

Payment-related rules:

* Create order server-side.
* Verify payment server-side.
* Verify webhook signature.
* Activate plan only after verified payment.
* Store payment status.
* Store invoice if implemented.
* Handle failed payment.
* Handle pending payment.
* Handle refund/credit if implemented.
* Keep secrets server-side.

No fake payment success.

No fake subscription activation.

---

# 51. ADMIN SETTINGS RULE

If a setting exists in Admin/Super Admin UI, it must work.

Examples:

* WhatsApp mode switch must affect contact flow.
* Map mode switch must affect map UI.
* Session timeout setting must affect session behavior.
* Banner ad pricing must affect banner ad purchase.
* Feature flag must affect frontend and backend.
* City enable/disable must affect search/listing.
* Free launch setting must affect plan/listing.
* Provider setting must affect provider usage.

No decorative settings.

No disconnected toggles.

---

# 52. ROUTING RULE

Routes must be clean, role-aware and protected.

Public routes:

* Homepage
* Search/city pages
* Property detail
* Project detail
* Broker/agency/builder profile
* Pricing
* Blog
* FAQ
* About
* Contact
* Login/register fallback

Protected routes:

* Dashboard
* Profile
* Saved properties
* Requirements
* Leads
* Site visits
* Messages
* Billing
* Subscription
* Admin
* Settings

Admin routes must be separate and protected.

Unauthorized users must see clear denied/login state.

---

# 53. ROLE-BASED UI RULE

The whole website must be role-based.

This does not mean only dashboards.

Role-based behavior applies to:

* Header
* Sidebar
* Homepage CTAs
* Search actions
* Property contact actions
* Save actions
* Requirement actions
* Dashboard links
* Pricing plans
* Profile sections
* Notifications
* Mobile bottom nav
* Forms
* Admin access
* Banner ad access
* Subscription access

Example:

If user is logged in, show profile icon, not Login/Register.

This example is global logic, not only header logic.

Claude must apply the same thinking everywhere.

---

# 54. ROLE-BASED DASHBOARD RULE

Dashboards must be specific to the role.

Owner sees:

* Own properties
* Leads
* Contact requests
* Site visits
* Subscription
* Profile

Broker sees:

* Listings
* Buyer requirements
* Proposals
* Leads
* Site visits
* Profile
* Subscription

Agency sees:

* Agency listings
* Team/agents
* Assigned leads
* Banner ads if enabled
* Subscription
* Agency profile

Agent sees:

* Assigned work only
* Assigned leads
* Assigned site visits
* Assigned listings if allowed

Builder sees:

* Projects
* Units
* Leads
* Site visits
* Banner ads if enabled
* Subscription

Buyer/Tenant sees:

* Saved properties
* Requirements
* Proposals
* Site visits
* Messages
* Profile

Admin/Super Admin sees:

* Platform control
* Moderation
* Users
* Settings
* Payments
* Ads
* SEO
* CMS
* Providers
* Logs

No generic random dashboard.

No fake metrics.

---

# 55. MOBILE TABLE-TO-CARD RULE

No wide tables on mobile.

Convert tables to cards for:

* Properties
* Leads
* Requirements
* Proposals
* Site visits
* Agents
* Projects
* Units
* Users
* Payments
* Invoices
* Subscriptions
* Banner ads
* Admin queues
* Support tickets
* Reports
* Verification requests

If a table overflows mobile screen, the phase fails.

---

# 56. BACK NAVIGATION RULE

Use back icons where appropriate.

Examples:

* Mobile detail pages
* Nested dashboard pages
* Full-screen search overlay
* Login/register flow
* OTP screen
* Property posting steps
* Requirement posting steps
* Image crop screen
* Admin detail drawers
* Filter bottom sheet

Back behavior should return user to the previous logical step.

Do not trap users.

---

# 57. AUDIT LOG RULE

Important admin/system actions should create audit logs.

Examples:

* User role change
* Role approval/rejection
* Property approval/rejection
* Requirement approval/rejection
* Banner ad approval/rejection
* Subscription manual adjustment
* Payment status change
* Provider setting change
* Feature flag change
* User suspension/ban
* Super Admin setting update
* Verification decision
* Support escalation

Audit logs must be real if visible.

Do not show fake audit logs.

---

# 58. CITY-FIRST MARKETPLACE RULE

My Gujarat Property is Gujarat-first.

City behavior matters everywhere.

City affects:

* Homepage search
* Banner ads
* Property results
* SEO pages
* Brokers
* Agencies
* Builders
* Requirements
* Pricing offers if city-specific
* Admin city manager scope
* Nearby fallback
* Notifications
* Analytics if implemented

If user selects Rajkot, Rajkot data should be prioritized.

If not enough Rajkot data exists, nearby/different city data can be shown with clear fallback logic.

---

# 59. SEO NO-FAKE RULE

SEO pages must not lie.

Do not create pages with fake listing count.

Do not create “Best properties in Rajkot” page with fake properties.

Do not index empty thin pages.

Do not create duplicate low-value content pages.

Use:

* Real listings
* Real city/locality data
* Real internal links
* Safe intro content
* Admin-controlled SEO text if needed
* Noindex when thin
* Canonical URLs

---

# 60. CLAUDE RESPONSE RULE

When Claude completes a phase, final answer should be structured.

Recommended output:

```txt
STATUS: PASS / FAIL / PARTIAL / BLOCKED

Summary:
...

Implemented:
...

Files Changed:
...

Feature Registry:
...

Manual Verification:
...

Build Checks:
- Lint:
- Typecheck:
- Build:

Issues Found:
...

Fixes Applied:
...

Remaining Blockers:
...

Next Phase:
...
```

Claude must be honest.

If something was not tested, say it.

If something was blocked, say why.

If screenshot/video was not captured, do not mention it unless asked, because screenshots/videos are no longer required.

---

# 61. PRODUCTION READINESS RULE

Before launch, Claude must ensure:

* Dev OTP disabled
* Demo data removed or hidden
* Fake/seed users removed
* Fake/seed properties removed
* Provider modes configured
* Payment provider configured if payments enabled
* WhatsApp mode selected
* Map mode selected
* RLS policies active
* Admin roles protected
* SEO sitemap generated
* Empty pages handled
* Mobile layout checked
* No horizontal scroll
* No exposed secrets
* No fake payment success
* No public private docs
* No hidden contact leak
* Error states present
* Build passes
* Critical workflows tested

---

# 62. FINAL NON-NEGOTIABLES

Claude must always remember:

1. Do not skip uploaded docs.
2. Do not skip chat instructions.
3. User’s latest instruction wins.
4. Keep prompts token-light.
5. Keep docs detailed.
6. Keep common rules short enough to be reusable.
7. Keep manual verification separate.
8. Remove screenshot/video capture instructions.
9. Remove sample image/reference photo dependency.
10. No fake production UI.
11. Demo data allowed only for development.
12. Mobile design is highest priority.
13. Role-based UI applies everywhere.
14. Logged-in user must see logged-in UI.
15. Admin login must not appear in public login/register.
16. OTP dev mode must never leak to production.
17. Every visible setting must work.
18. Every visible filter must work or be hidden.
19. Every payment must be server-verified.
20. Every secure action must be server-checked.
21. Hidden contact must never leak.
22. Banner ads must be paid, approved, city-prioritized, expiring and archived.
23. SEO must target real search intent using real data.
24. Super Admin must control the platform.
25. PASS means verified, not assumed.

---

# 63. END OF FILE

This file is the master operating rulebook for the regenerated My Gujarat Property documentation and Claude development prompt system.

Every phase must begin by reading this file.

Every phase must follow it.

Nothing from uploaded docs or user chat instructions should be skipped.
