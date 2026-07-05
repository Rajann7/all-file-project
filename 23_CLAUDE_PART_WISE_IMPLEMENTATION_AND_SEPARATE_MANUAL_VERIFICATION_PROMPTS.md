MY GUJARAT PROPERTY
CLAUDE PART-WISE IMPLEMENTATION + SEPARATE MANUAL VERIFICATION PROMPTS
FILE NAME
23_CLAUDE_PART_WISE_IMPLEMENTATION_AND_SEPARATE_MANUAL_VERIFICATION_PROMPTS.md
________________________________________
1. PURPOSE
This is the final Claude AI prompt file for My Gujarat Property.
This file is written exactly for this workflow:
1.	Send Implementation Prompt first.
2.	Claude builds that part.
3.	Claude gives implementation report.
4.	Then send Manual Verification Prompt separately.
5.	Claude manually verifies that exact part.
6.	Claude fixes bugs.
7.	Claude retests.
8.	Claude gives PASS / PARTIAL / FAIL / BLOCKED.
9.	Then move to next part.
This file keeps implementation and manual verification as two different prompts.
This prevents Claude from skipping verification.
________________________________________
2. HOW TO USE
For every part, use this order:
1. Copy PART X — IMPLEMENTATION PROMPT
2. Paste in Claude
3. Wait for Claude to implement
4. Then copy PART X — MANUAL VERIFICATION PROMPT
5. Paste in Claude
6. Wait for PASS/PARTIAL/FAIL/BLOCKED report
7. If PASS, move to next part
8. If FAIL/PARTIAL, ask Claude to fix and retest before next part
Do not give next implementation prompt until manual verification is complete.
________________________________________
3. GLOBAL DEVELOPMENT RULES
Claude must always follow:
•	Next.js 15 App Router
•	TypeScript
•	Tailwind CSS
•	Supabase Auth
•	Supabase Postgres
•	Supabase Storage
•	Supabase RLS
•	Supabase SSR/cookie-based auth
•	Role-based UI
•	Role-based backend checks
•	Mobile-first responsive design
•	White-first clean UI
•	No fake production UI
•	No fake production data
•	No fake payment
•	No fake verification badge
•	No fake RERA verified
•	No fake provider status
•	No fake WhatsApp/SMS/email sent
•	No fake dashboard metrics
•	No broken buttons
•	No broken placeholder routes
•	No service role key in client
•	No private document public URL
•	No hidden contact leak
•	No admin route public access
•	If feature is not ready, hide it or show safe setup-required/disabled state
•	Feature Registry must be updated after implementation and verification

## GLOBAL DEVELOPMENT OTP RULE

For development only, OTP testing must be easy.

If `OTP_DEV_MODE=true` and the app is running in development mode, any 4/6 digit OTP must be accepted for login/register testing.

Example:
123456, 111111, 999999 or any random OTP should work only in development.

In production, random/static/dev OTP must never work.

Production must use a real OTP provider.

If production OTP provider is not configured, show setup-required state and do not fake login/register success.

Claude must apply this rule globally in all auth, login, register, OTP, role registration, provider and manual verification work.


________________________________________
4. DOCS CLAUDE MUST READ
Claude must read and follow these docs:
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
23_CLAUDE_PART_WISE_IMPLEMENTATION_AND_SEPARATE_MANUAL_VERIFICATION_PROMPTS.md
________________________________________
5. IMPLEMENTATION REPORT FORMAT
Every implementation prompt must end with:
## IMPLEMENTATION REPORT

### Part Implemented
[Part name]

### Files Created/Changed
[List files]

### Features Implemented
[List]

### Database / Supabase Changes
[List or None]

### Routes Added/Updated
[List or None]

### Components Added/Updated
[List or None]

### Feature Registry Update
[List]

### Build / Type / Lint Check
PASS / FAIL / NOT RUN

### Implementation Status
PASS / PARTIAL / BLOCKED

### Notes / Blockers
[List]
Implementation status is not final QA status.
Final QA comes only after separate manual verification prompt.
________________________________________
6. MANUAL VERIFICATION REPORT FORMAT
Every manual verification prompt must end with:
## MANUAL VERIFICATION REPORT

### Part Verified
[Part name]

### Without Login Check
PASS / FAIL / BLOCKED  
Details:

### With Login Check
PASS / FAIL / BLOCKED  
Details:

### Role-wise Check
- Buyer:
- Tenant:
- Owner:
- Broker:
- Agency Owner:
- Agency Agent:
- Builder:
- Admin:
- Super Admin:

### Desktop UI Check
PASS / FAIL / BLOCKED  
Details:

### Mobile UI Check
PASS / FAIL / BLOCKED  
Details:

### Functionality Check
PASS / FAIL / BLOCKED  
Details:

### Database / RLS / Security Check
PASS / FAIL / BLOCKED  
Details:

### No-Fake UI / No-Fake Data Check
PASS / FAIL / BLOCKED  
Details:

### Bugs Found
[List]

### Fixes Applied
[List]

### Retest Result
PASS / FAIL / BLOCKED

### Feature Registry Update
[List]

### Final Status
PASS / PARTIAL / FAIL / BLOCKED
________________________________________
7. MASTER START PROMPT
PROMPT — MASTER START
You are Claude AI acting as a senior full-stack architect, Next.js developer, Supabase architect, product engineer, QA engineer and security reviewer.

Project: My Gujarat Property.

Stack:
- Next.js 15 App Router
- TypeScript
- Tailwind CSS
- Supabase Auth
- Supabase Postgres
- Supabase Storage
- Supabase RLS
- Supabase SSR cookie auth

Read all documentation files inside /docs.

Rules:
- No fake production UI.
- No fake data.
- No fake payment success.
- No fake verified badge.
- No fake provider success.
- No hidden phone leak.
- No private document public URL.
- No admin route public access.
- No service role key in client.
- No broken placeholder buttons.
- If feature is missing, show empty/setup-required/disabled state.
- Always update Feature Registry.
- Always output clear report.

Task:
1. Inspect current project.
2. Inspect docs.
3. Inspect folder structure.
4. Identify missing setup.
5. Give safe next-step plan.
6. Do not implement unrelated future modules yet.

Output:
- Project status
- Missing setup
- Next recommended part
- Risks/blockers
________________________________________
8. PART 1 — PROJECT FOUNDATION
PROMPT 1A — IMPLEMENTATION: PROJECT FOUNDATION
Implement Part 1: Project foundation, common rules, app structure and Feature Registry.

Read:
- 00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md
- 01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md
- 02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. If project is empty, initialize Next.js 15 App Router with TypeScript and Tailwind.
2. Create clean folder structure:
   - app/
   - components/
   - components/common/
   - components/layout/
   - components/forms/
   - components/cards/
   - components/dashboard/
   - components/admin/
   - lib/
   - lib/supabase/
   - lib/auth/
   - lib/rbac/
   - lib/validators/
   - lib/utils/
   - types/
   - docs/
3. Add base app layout.
4. Add global styles.
5. Add white-first clean design tokens.
6. Add safe common states:
   - Loading
   - Empty
   - Error
   - Success
   - Disabled
   - Setup Required
7. Add Supabase client setup safely:
   - browser client
   - server client
   - service role client server-only placeholder
8. Add environment example file without real secrets.
9. Create/update Feature Registry.
10. Add initial registry entries for all modules:
   - auth
   - public UI
   - search
   - property
   - requirement
   - dashboard
   - admin
   - banner ads
   - subscription
   - provider
   - database/RLS
   - notification
   - verification
   - CMS
   - QA

Do not:
- Do not create fake marketplace data.
- Do not create fake listings.
- Do not create fake dashboard metrics.
- Do not expose service role key in client.
- Do not build unrelated feature flows.

At the end output the IMPLEMENTATION REPORT.
PROMPT 1B — MANUAL VERIFICATION: PROJECT FOUNDATION
Manually verify Part 1: Project foundation.

Run the app and check the foundation setup.

Verify:
1. App starts without crash.
2. Homepage/base route loads.
3. Tailwind/global styles are applied.
4. Base layout does not break.
5. Mobile width has no horizontal scroll.
6. Folder structure exists:
   - app
   - components
   - lib
   - types
   - docs
7. Common state components exist:
   - loading
   - empty
   - error
   - success
   - disabled/setup-required
8. Supabase clients are separated:
   - browser client safe
   - server client safe
   - service role only server-side
9. Environment example has no real secrets.
10. Feature Registry exists and has initial module entries.
11. No fake production listings/dashboard data exist.
12. No service role key is imported into client components.
13. Check console/server for errors.

If anything fails:
1. Mark FAIL.
2. Fix it.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
9. PART 2 — PUBLIC WEBSITE UI
PROMPT 2A — IMPLEMENTATION: PUBLIC WEBSITE + HEADER + SIDEBAR + FOOTER
Implement Part 2: Public website layout, homepage shell, header, footer, mobile sidebar and app-like public UI.

Read:
- 01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md
- 02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md
- 03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md
- 04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md
- 20_CMS_BLOG_STATIC_PAGES_LEGAL_CONTENT_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Public homepage shell.
2. Responsive header:
   - logo
   - main navigation
   - Login/Register button for guest
   - profile icon placeholder for logged-in state
   - Post Property CTA
   - Post Requirement CTA if enabled
3. Mobile sidebar/drawer:
   - opens
   - closes
   - closes on outside click
   - role-aware menu placeholder
   - footer/legal/support links
4. Public footer:
   - About
   - Contact
   - FAQ
   - Blog
   - Pricing
   - Privacy Policy
   - Terms
   - Refund Policy
   - Listing Policy
   - Advertising Policy
   - Safety
5. Public static page shells with safe non-fake content.
6. Mobile-first layout:
   - no horizontal scroll
   - touch-friendly
   - clean white UI
   - no cramped header

Do not:
- Do not create fake property cards.
- Do not create fake reviews/testimonials.
- Do not create fake city/property counts.
- Do not claim No.1 portal or 100% verified listings.
- Do not create broken footer/header links.

At the end output the IMPLEMENTATION REPORT.
PROMPT 2B — MANUAL VERIFICATION: PUBLIC WEBSITE + HEADER + SIDEBAR + FOOTER
Manually verify Part 2: Public website, header, sidebar and footer.

Run the app and test public UI.

Without login:
1. Open homepage.
2. Check header logo.
3. Check desktop navigation.
4. Check Login/Register button visible.
5. Check Post Property CTA visible.
6. Check Post Requirement CTA if enabled.
7. Open mobile view.
8. Open mobile sidebar.
9. Close mobile sidebar by close button.
10. Close mobile sidebar by outside click.
11. Check no horizontal scroll.
12. Check footer links:
   - About
   - Contact
   - FAQ
   - Blog
   - Pricing
   - Privacy
   - Terms
   - Refund
   - Listing Policy
   - Advertising Policy
   - Safety
13. Open each footer page and confirm no 404/broken page.
14. Confirm no fake property cards/counts/reviews.

With login if auth exists:
1. Login with any saved test user.
2. Header must show profile icon.
3. Login/Register must not show after login.
4. Logout returns Login/Register.

Design check:
1. Desktop layout clean.
2. Mobile layout clean.
3. Header does not wrap badly.
4. Touch targets usable.
5. Footer readable.

If anything fails:
1. Mark FAIL.
2. Fix UI/routing/responsiveness.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
10. PART 3 — AUTH / LOGIN / ROLE / PROFILE
PROMPT 3A — IMPLEMENTATION: AUTH + OTP + ROLE REGISTRATION + PROFILE
Implement Part 3: Auth, Login/Register, OTP, role registration, session, profile and role-based access.

Read:
- 06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md
- 07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md
- 16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Login/Register in same modal/popup.
2. Public button text: Login/Register.
3. New users must register first.
4. Existing users can login.
5. OTP flow:
   - dev OTP only in development
   - production must not allow fake/static OTP
6. Role selection during registration:
   - Buyer
   - Tenant
   - Owner
   - Broker
   - Agency
   - Builder
7. Admin/Super Admin roles must not be public.
8. Create/update auth tables:
   - profiles
   - user_roles
   - active role logic
   - role change requests if included
9. Role-based redirects.
10. Preserve intent after login/register.
11. Logged-in header shows profile icon.
12. Login/Register hides after login.
13. Logout works.
14. Protected route guard.
15. Profile completion screen.
16. Role change request:
   - pending
   - approved
   - rejected
17. Pending role must not grant access.

Do not:
- Do not fake successful login.
- Do not fake OTP in production.
- Do not expose Admin/Super Admin roles publicly.
- Do not show Login/Register after login.
- Do not grant access to pending role.
- Do not expose service role key in client.

At the end output the IMPLEMENTATION REPORT.
PROMPT 3B — MANUAL VERIFICATION: AUTH + OTP + ROLE REGISTRATION + PROFILE
Manually verify Part 3: Auth, OTP, role registration, profile and role access.

Run the app and test real flows.

Without login:
1. Homepage shows Login/Register.
2. Protected dashboard routes redirect/block correctly.
3. Public pages still open.
4. Post Property/Post Requirement preserves intent or opens auth safely.

Registration:
1. Open Login/Register.
2. Register new Buyer test user.
3. Register new Tenant test user if needed.
4. Register new Owner test user.
5. Register new Broker test user.
6. Register new Agency test user.
7. Register new Builder test user.
8. Confirm role selection saves.
9. Confirm profile record creates.
10. Confirm user_roles record creates.
11. Confirm correct redirect after registration.

Login:
1. Login existing saved Buyer.
2. Login existing saved Owner.
3. Login existing saved Broker.
4. Login existing saved Agency.
5. Login existing saved Builder.
6. OTP works in dev mode only.
7. Session persists.
8. Logout works.

Header/session:
1. After login, profile icon visible.
2. Login/Register hidden after login.
3. After logout, Login/Register visible.

Role access:
1. Buyer dashboard opens for Buyer.
2. Owner dashboard opens for Owner.
3. Broker dashboard opens for Broker.
4. Agency dashboard opens for Agency.
5. Builder dashboard opens for Builder.
6. Wrong dashboard blocked.
7. Admin dashboard blocked for normal user.
8. Public cannot register as Admin/Super Admin.

Role change:
1. Request role change.
2. Pending role does not grant access.
3. Approved role can switch if approval exists.
4. Rejected role shows reason if implemented.

Mobile:
1. Login/Register modal usable.
2. OTP input usable.
3. Role selection cards usable.
4. Keyboard does not hide main CTA.

Security:
1. Dev OTP not production-enabled.
2. No service role key in client.
3. No fake login success.

If anything fails:
1. Mark FAIL.
2. Fix auth/session/role issue.
3. Retest all affected roles.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
11. PART 4 — LOCATION / SEARCH / FILTERS / SEO
PROMPT 4A — IMPLEMENTATION: LOCATION + HOMEPAGE SEARCH + DYNAMIC FILTERS + SEO
Implement Part 4: Gujarat location hierarchy, homepage search, dynamic filters and SEO-ready routes.

Read:
- 04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md
- 05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md
- 08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Gujarat location hierarchy:
   - state
   - district
   - taluka
   - city
   - village
   - locality
   - society
   - landmark
2. Homepage search.
3. Search tabs:
   - Buy
   - Rent
   - Commercial
   - Land
   - Projects
   - PG
   - Requirements if enabled
4. Dynamic filters:
   - Residential shows BHK
   - Rent shows rent/deposit
   - Land hides BHK
   - Commercial hides BHK
   - PG shows PG filters
   - Projects show project filters
5. Search results route with query params.
6. Mobile filter bottom sheet.
7. Real empty result state.
8. SEO-ready city/locality/search route structure.
9. Basic metadata where possible.

Do not:
- Do not fake property results.
- Do not fake property counts.
- Do not show BHK for land/commercial.
- Do not index thin fake SEO pages.
- Do not create broken filters.

At the end output the IMPLEMENTATION REPORT.
PROMPT 4B — MANUAL VERIFICATION: LOCATION + SEARCH + FILTERS + SEO
Manually verify Part 4: Location, homepage search, dynamic filters and SEO routes.

Without login:
1. Open homepage.
2. Use search.
3. Select city.
4. Select category tab Buy.
5. Select category tab Rent.
6. Select category tab Commercial.
7. Select category tab Land.
8. Select category tab Projects.
9. Select category tab PG if enabled.
10. Submit search.
11. Confirm search results route opens.
12. Confirm query params update/read correctly.

Dynamic filters:
1. Buy/Residential shows BHK.
2. Rent shows rent/deposit.
3. Land does not show BHK.
4. Commercial does not show BHK.
5. PG shows PG-related fields.
6. Project shows project-related filters.
7. Irrelevant filters disappear when category changes.

Location:
1. City selection works.
2. District/taluka/locality works if implemented.
3. Missing/custom location safe behavior works if implemented.
4. No page refresh bug during cascading selection.

Search results:
1. Empty state appears if no real properties.
2. No fake results appear.
3. No fake counts appear.
4. Sort/filter works if implemented.

Mobile:
1. Filter bottom sheet opens.
2. Filter bottom sheet closes.
3. No horizontal scroll.
4. Search fields usable.
5. Chips/buttons usable.

SEO:
1. City/search route has title/meta if implemented.
2. No fake property count in SEO content.
3. Empty/thin pages noindex if implemented.

Logged-in:
1. Search still works.
2. Save search only works if implemented; otherwise hidden.

If anything fails:
1. Mark FAIL.
2. Fix filter/search/location/mobile/SEO issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
12. PART 5 — PROPERTY POSTING
PROMPT 5A — IMPLEMENTATION: PROPERTY POSTING + TYPE-BASED FIELDS + MEDIA
Implement Part 5: Property posting with type-based fields, media upload, draft and approval status.

Read:
- 09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md
- 08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md
- 12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Post Property flow for:
   - Owner
   - Broker
   - Agency
   - Builder if project/unit flow exists
2. Guest Post Property opens Login/Register and preserves intent.
3. First step: purpose/property type selection.
4. Dynamic forms:
   - Flat/Apartment
   - House/Villa
   - Plot/Land
   - Agricultural Land
   - Shop
   - Office
   - Showroom
   - Warehouse
   - PG if enabled
   - Project/Unit if enabled
5. Correct field visibility:
   - Land hides BHK
   - Commercial hides residential fields
   - Rent shows rent/deposit
6. Source tag from active role.
7. Brokerage information.
8. Location hierarchy.
9. Price/rent/area fields.
10. Media upload:
   - recommended size
   - allowed file types
   - max size
   - preview
   - crop/fit if possible
11. Draft save.
12. Submit for approval.
13. Dashboard listing status.
14. Pending listing not public.

Do not:
- Do not create fake real listing.
- Do not skip validation.
- Do not show pending listing publicly.
- Do not allow wrong role to post.
- Do not put private docs in public bucket.

At the end output the IMPLEMENTATION REPORT.
PROMPT 5B — MANUAL VERIFICATION: PROPERTY POSTING
Manually verify Part 5: Property posting, type-based fields and media upload.

Without login:
1. Click Post Property.
2. Login/Register opens.
3. Intent preserved after login if implemented.

Owner:
1. Login as Owner.
2. Open Post Property.
3. Select residential property.
4. Fill required fields.
5. Add Gujarat location.
6. Add price/area.
7. Upload/check image if available.
8. Save draft.
9. Submit for approval.
10. Check Owner dashboard listing status.

Broker:
1. Login as Broker.
2. Post property.
3. Source tag must be Broker.
4. Brokerage field visible/required as per rules.
5. Submit and check dashboard.

Agency:
1. Login as Agency Owner.
2. Post property.
3. Source tag must be Agency.
4. Check agency dashboard listing.

Builder:
1. Login as Builder.
2. Project/unit posting works if implemented.
3. If not implemented, it is hidden safely.

Type-based fields:
1. Flat/Apartment shows BHK.
2. House/Villa shows residential fields.
3. Land/Plot does not show BHK.
4. Agricultural Land does not show BHK.
5. Commercial Shop/Office does not show residential fields.
6. Rent shows rent/deposit.

Media:
1. Recommended size/ratio visible.
2. Valid image uploads.
3. Invalid file type blocked.
4. Large file blocked if limit exists.
5. Preview works.

Public visibility:
1. Pending listing does not appear in search.
2. Approved listing appears only after admin approval if approval enabled.

Mobile:
1. Step form usable.
2. No horizontal scroll.
3. Next/Submit buttons visible.
4. Upload UI usable.

Security:
1. Wrong role blocked.
2. User cannot edit another user listing.
3. No fake listing data appears.

If anything fails:
1. Mark FAIL.
2. Fix property form/data/role/storage issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
13. PART 6 — PROPERTY CARD / DETAIL / CONTACT / LEAD
PROMPT 6A — IMPLEMENTATION: PROPERTY CARD + DETAIL + CONTACT + LEAD
Implement Part 6: Property card, detail page, contact visibility and lead generation.

Read:
- 10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md
- 16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Property card:
   - image
   - title
   - price/rent
   - location
   - property type
   - source tag
   - status
   - real verified badge only
   - real featured/boost only
2. Property detail page:
   - gallery
   - quick facts
   - description
   - location/map based on provider mode
   - seller card
   - contact CTA
   - report button
3. Contact visibility:
   - guest auth prompt if needed
   - logged-in lead form
   - profile number option
   - alternate number option
4. Lead creation.
5. Receiver dashboard lead display.
6. Alternate number badge for receiver.
7. WhatsApp behavior:
   - free wa.me
   - API only if configured
   - disabled/setup-required fallback
8. Call button if allowed.
9. Hidden phone/private data protected.

Do not:
- Do not expose hidden phone publicly.
- Do not create fake lead.
- Do not fake WhatsApp sent.
- Do not show fake verified badge.
- Do not show expired/pending property as active.

At the end output the IMPLEMENTATION REPORT.
PROMPT 6B — MANUAL VERIFICATION: PROPERTY CARD + DETAIL + CONTACT + LEAD
Manually verify Part 6: Property card, detail, contact visibility and lead.

Without login:
1. Open property search/detail.
2. Property card displays correct safe data.
3. Contact CTA requires login if configured.
4. Hidden phone is not visible.
5. Hidden phone is not present in public payload if you can inspect.
6. Report button appears or safely hidden.

Logged-in buyer/tenant:
1. Open property detail.
2. Submit contact form with profile number.
3. Submit contact form with alternate number.
4. Confirm lead created.
5. Confirm success state real.
6. Confirm duplicate behavior safe if repeated.

Receiver:
1. Login as Owner/Broker/Agency/Builder who owns listing.
2. Open leads dashboard.
3. Confirm lead appears.
4. Confirm alternate number badge appears when alternate used.
5. Confirm lead source/property correct.

Card/detail:
1. Source tag correct.
2. Price/location correct.
3. Status correct.
4. Verified badge appears only if real verification exists.
5. Featured/boost label appears only if real active status exists.

Provider behavior:
1. WhatsApp free mode opens wa.me.
2. WhatsApp API mode sends only if configured.
3. Missing API does not show fake sent.
4. Map respects map provider mode.

Mobile:
1. Detail page usable.
2. Gallery usable.
3. Sticky contact CTA works.
4. Contact form usable.
5. No horizontal scroll.

Security:
1. Public cannot access lead data.
2. Buyer cannot see receiver private lead dashboard.
3. Wrong receiver cannot see lead.

If anything fails:
1. Mark FAIL.
2. Fix public payload/contact/lead/security issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
14. PART 7 — REQUIREMENT / PROPOSAL / SITE VISIT / MESSAGING
PROMPT 7A — IMPLEMENTATION: REQUIREMENT + PROPOSAL + SITE VISIT + MESSAGING
Implement Part 7: Buyer/Tenant requirement marketplace, proposal, lead, site visit and messaging flow.

Read:
- 11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md
- 10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md
- 12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Post requirement flow for Buyer/Tenant/Investor if enabled.
2. Guest intent preservation.
3. Requirement types:
   - Buy
   - Rent
   - Commercial
   - Land
   - PG
   - Project/Investment if enabled
4. Dynamic fields by type.
5. Requirement privacy/contact preference.
6. Requirement approval/status.
7. Requirement feed for eligible responders.
8. Proposal creation by Broker/Agency/Builder/Owner if allowed.
9. Attach listing/project if implemented.
10. Buyer receives proposal.
11. Buyer shortlist/reject/contact.
12. Proposal/contact creates lead.
13. Site visit request/approve/reject/reschedule if enabled.
14. Messaging if enabled; otherwise hide safely.

Do not:
- Do not expose buyer private phone unless shared.
- Do not allow wrong role proposal.
- Do not show pending requirement in feed.
- Do not create fake proposal/lead/site visit.
- Do not create broken message button.

At the end output the IMPLEMENTATION REPORT.
PROMPT 7B — MANUAL VERIFICATION: REQUIREMENT + PROPOSAL + SITE VISIT + MESSAGING
Manually verify Part 7: Requirement, proposal, lead, site visit and messaging.

Without login:
1. Click Post Requirement.
2. Login/Register opens.
3. Intent preserved if implemented.

Buyer/Tenant:
1. Login as Buyer.
2. Create buy requirement.
3. Create rent requirement if applicable.
4. Create land requirement.
5. Confirm land requirement has no BHK.
6. Submit requirement.
7. Check buyer dashboard.
8. Login as Tenant and test rental/PG requirement if applicable.

Approval/status:
1. Pending requirement does not appear in responder feed.
2. Approved requirement appears if approval enabled.
3. Expired/closed requirement does not accept proposals.

Responder roles:
1. Login as Broker.
2. Open requirement feed.
3. Send proposal.
4. Attach property if implemented.
5. Login as Agency/Builder and repeat if relevant.
6. Wrong role blocked.

Buyer proposal flow:
1. Buyer receives proposal.
2. Shortlist works.
3. Reject works.
4. Contact action works.
5. Lead created if contact/proposal action requires.

Privacy:
1. Buyer phone hidden before allowed action.
2. Alternate phone handled clearly if used.
3. Non-related users cannot view private proposal/lead.

Site visit:
1. Request visit.
2. Receiver approve/reject/reschedule.
3. Assigned agency agent sees assigned visit if implemented.
4. Cancelled visit does not remain active.

Messaging:
1. If enabled, thread works only for participants.
2. Non-participant blocked.
3. If disabled, message buttons hidden.

Mobile:
1. Requirement form usable.
2. Requirement feed cards usable.
3. Proposal cards usable.
4. Site visit form usable.
5. No horizontal scroll.

If anything fails:
1. Mark FAIL.
2. Fix flow/privacy/permission issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
15. PART 8 — ROLE DASHBOARDS
PROMPT 8A — IMPLEMENTATION: ROLE-BASED DASHBOARDS
Implement Part 8: Role-based dashboards for all platform roles.

Read:
- 12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md
- 02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md
- 07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement dashboards:
1. Buyer:
   - saved properties
   - requirements
   - proposals
   - site visits
2. Tenant:
   - rental/PG requirements
   - proposals
   - site visits
3. Owner:
   - properties
   - leads
   - site visits
   - expiry
   - plan usage if enabled
4. Broker:
   - listings
   - requirement feed
   - proposals
   - leads
   - site visits
5. Agency Owner:
   - agency profile
   - agents
   - listings
   - leads
   - lead assignment
   - banner ads if enabled
6. Agency Agent:
   - assigned leads only
   - assigned visits only
   - no agency billing unless permitted
7. Builder:
   - projects
   - units
   - leads
   - site visits
   - banner ads if enabled

Do not:
- Do not create same generic dashboard for all roles.
- Do not show fake dashboard counts.
- Do not show fake leads.
- Do not allow wrong role dashboard access.
- Do not show agent all agency data unless assigned/allowed.

At the end output the IMPLEMENTATION REPORT.
PROMPT 8B — MANUAL VERIFICATION: ROLE-BASED DASHBOARDS
Manually verify Part 8: Role-based dashboards.

Without login:
1. Open each dashboard route.
2. Confirm route redirects/blocks.

Buyer:
1. Login as Buyer.
2. Buyer dashboard opens.
3. Buyer-only items visible.
4. Broker/Owner/Admin items hidden.

Tenant:
1. Login as Tenant.
2. Tenant dashboard opens.
3. Rental/PG requirement items visible.

Owner:
1. Login as Owner.
2. Owner properties visible.
3. Owner leads visible.
4. Owner site visits visible.
5. Broker requirement feed hidden unless role allowed.

Broker:
1. Login as Broker.
2. Broker listings visible.
3. Requirement feed visible if allowed.
4. Proposals/leads/site visits visible.

Agency Owner:
1. Login as Agency Owner.
2. Agency agents visible.
3. Agency listings visible.
4. Agency leads visible.
5. Lead assignment works if implemented.
6. Billing/settings visible only if allowed.

Agency Agent:
1. Login as Agency Agent.
2. Assigned leads visible.
3. Assigned site visits visible.
4. Unassigned leads hidden.
5. Agency billing/settings blocked unless permission.

Builder:
1. Login as Builder.
2. Projects/units visible.
3. Project leads visible.
4. Banner ads visible if enabled.

Admin/Super Admin:
1. Admin dashboard separate from role dashboards.
2. Normal role dashboards not mixed with admin panel.

Mobile:
1. Tables become cards.
2. Sidebar/drawer works.
3. No horizontal scroll.
4. Dashboard actions usable.

No-fake:
1. Counts real or hidden.
2. Empty state shown if no data.
3. No fake leads/proposals/listings.

If anything fails:
1. Mark FAIL.
2. Fix role routing/scope/mobile issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
16. PART 9 — ADMIN / SUPER ADMIN
PROMPT 9A — IMPLEMENTATION: ADMIN + SUPER ADMIN + MODERATION + SETTINGS
Implement Part 9: Admin/Super Admin panel, moderation queues, staff permissions and settings.

Read:
- 13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Protected admin routes.
2. Protected Super Admin routes.
3. Admin dashboard:
   - pending properties
   - pending requirements
   - pending banner ads if enabled
   - verification queue
   - reports queue
   - users
4. Moderation:
   - approve
   - reject
   - request changes
   - rejection reason
5. User/role management basics.
6. Role change approval.
7. Super Admin settings:
   - platform settings
   - feature flags
   - provider settings links
   - plan settings links
8. Audit logs for sensitive actions where possible.

Do not:
- Do not let normal user access admin.
- Do not let Admin access Super Admin-only settings unless allowed.
- Do not show fake admin metrics.
- Do not make decorative settings that do nothing.
- Do not expose provider secrets.

At the end output the IMPLEMENTATION REPORT.
PROMPT 9B — MANUAL VERIFICATION: ADMIN + SUPER ADMIN + MODERATION + SETTINGS
Manually verify Part 9: Admin/Super Admin, moderation and settings.

Without login:
1. /admin blocked.
2. /admin/super blocked.

Normal logged-in user:
1. Login as Buyer/Owner/Broker.
2. /admin blocked.
3. /admin/super blocked.

Admin:
1. Login as Admin.
2. Admin dashboard opens.
3. Pending property queue opens.
4. Approve property works.
5. Reject property requires reason.
6. Approved property becomes public if all rules allow.
7. Rejected property does not become public.
8. Requirement moderation works if implemented.
9. Banner ad moderation works if implemented.
10. Verification queue works if implemented.
11. Report queue works if implemented.

Super Admin:
1. Login as Super Admin.
2. Super Admin settings open.
3. Feature flags visible.
4. Provider settings links visible.
5. Secrets masked.
6. Settings save if implemented.

Permission:
1. Admin cannot access Super Admin-only provider/secrets if not allowed.
2. Staff cannot self-escalate.
3. Public cannot create admin role.

Settings effect:
1. Feature flag affects UI and backend or hidden safely.
2. Admin setting is not decorative/fake.

Audit:
1. Sensitive action audit log created if implemented.

Mobile:
1. Admin queues usable.
2. Tables become cards.
3. No horizontal scroll.

No-fake:
1. No fake admin counts.
2. No fake queue items.
3. No fake provider health.

If anything fails:
1. Mark FAIL.
2. Fix admin guard/moderation/settings.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
17. PART 10 — BANNER ADS
PROMPT 10A — IMPLEMENTATION: BANNER ADS + CITY TARGETING
Implement Part 10: Homepage banner ads, advertiser dashboard, city targeting and admin approval.

Read:
- 14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md
- 15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md
- 13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Banner ad creation for eligible roles:
   - Agency
   - Real Estate Group if implemented
   - Builder
   - Broker only if enabled
2. Buyer/Tenant cannot create banner ads.
3. Banner ad dashboard:
   - draft
   - pending
   - active
   - rejected
   - expired
4. Image upload:
   - desktop
   - tablet
   - mobile
   - size/ratio guidance
   - preview/crop if possible
5. City targeting.
6. Public homepage carousel:
   - approved only
   - paid/eligible only
   - active date only
   - local city priority
   - sponsored label
7. Admin approval queue.
8. Expiry hide logic.
9. Analytics only if real.

Do not:
- Do not show fake banner ads.
- Do not show unpaid/unapproved banner publicly.
- Do not show expired ad publicly.
- Do not fake impressions/clicks.
- Do not allow wrong role.

At the end output the IMPLEMENTATION REPORT.
PROMPT 10B — MANUAL VERIFICATION: BANNER ADS + CITY TARGETING
Manually verify Part 10: Banner ads and city targeting.

Without login:
1. Homepage opens.
2. Banner carousel shows only active approved paid/eligible ads.
3. If no ads, section hides or shows safe empty state.
4. Sponsored/ad label visible when ads show.

Buyer/Tenant:
1. Login as Buyer/Tenant.
2. Banner ad creation route blocked/hidden.

Agency/Builder/eligible role:
1. Login as Agency Owner or Builder.
2. Open banner ad dashboard.
3. Create draft ad.
4. Upload desktop image.
5. Upload tablet image.
6. Upload mobile image.
7. Select target city.
8. Submit for approval.
9. Dashboard status becomes pending.

Admin:
1. Pending ad appears in queue.
2. Approve ad.
3. Reject ad with reason.
4. Rejected ad not public.

Public display:
1. Approved active ad appears.
2. Pending ad does not appear.
3. Rejected ad does not appear.
4. Unpaid ad does not appear if payment required.
5. Expired ad does not appear.

City targeting:
1. Rajkot selected city prioritizes Rajkot ads.
2. Ahmedabad selected city prioritizes Ahmedabad ads.
3. Gujarat-wide fallback works.

Mobile:
1. Banner carousel responsive.
2. Mobile image used if available.
3. Image not stretched.
4. CTA usable.

No-fake:
1. No fake ads.
2. No fake analytics.
3. No fake impressions/clicks.

If anything fails:
1. Mark FAIL.
2. Fix ad status/payment/city/display.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
18. PART 11 — SUBSCRIPTION / PAYMENT / CREDIT / BOOST
PROMPT 11A — IMPLEMENTATION: SUBSCRIPTION + PAYMENT + CREDIT + BOOST
Implement Part 11: Subscription, payment, credits, boost, featured listing and first 100 free launch offer.

Read:
- 15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md
- 16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Public pricing page.
2. Role-based plans.
3. Purchase requires login.
4. Subscription records.
5. Payment states:
   - pending
   - success
   - failed
   - cancelled
6. Server-side payment verification.
7. No activation from client-only success.
8. Provider missing state.
9. Plan limits:
   - listings
   - images
   - proposals
   - leads
   - credits
   - agents
   - projects
10. Credit system if enabled.
11. Boost/featured listing.
12. First 100 free launch offer if enabled.
13. Billing dashboard.
14. Admin manual activation with audit note.

Do not:
- Do not fake payment success.
- Do not activate failed/pending payment.
- Do not fake invoices.
- Do not expose payment secrets.
- Do not bypass plan limits.

At the end output the IMPLEMENTATION REPORT.
PROMPT 11B — MANUAL VERIFICATION: SUBSCRIPTION + PAYMENT + CREDIT + BOOST
Manually verify Part 11: Subscription, payment, credits and boost.

Without login:
1. Pricing page visible.
2. Plan details visible.
3. Purchase button opens login/register.
4. No payment starts without required auth.

Logged-in roles:
1. Buyer plan behavior safe.
2. Owner plan visible.
3. Broker plan visible.
4. Agency plan visible.
5. Builder plan visible.
6. Wrong role plan handled safely.

Payment provider missing:
1. Shows setup-required/disabled state.
2. No fake success.

Payment states:
1. Pending payment does not activate subscription.
2. Failed payment does not activate subscription.
3. Cancelled payment does not activate subscription.
4. Verified server-side success activates plan only when valid.

Subscription:
1. Active plan appears in dashboard.
2. Plan expiry visible if implemented.
3. Expired plan removes benefits if implemented.
4. Grace period works only if configured.

Limits:
1. Listing limit enforced.
2. Image limit enforced.
3. Proposal/lead/credit limit enforced.
4. Agent/project limits enforced if implemented.

Credits:
1. Credit balance real.
2. Deduction real.
3. No negative/free fake credits.

Boost/Featured:
1. Starts only after valid credit/payment.
2. Label appears only while active.
3. Expiry removes label.

Admin:
1. Manual activation requires permission.
2. Manual activation requires audit note.
3. Normal admin cannot change protected billing if not allowed.

Mobile:
1. Pricing cards responsive.
2. Payment state usable.

Security:
1. Payment secret not exposed.
2. Client-only success cannot activate plan.

If anything fails:
1. Mark FAIL.
2. Fix payment/subscription/limits.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
19. PART 12 — PROVIDER MODES
PROMPT 12A — IMPLEMENTATION: PROVIDER MODES
Implement Part 12: Provider modes and Super Admin provider settings.

Read:
- 16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
- 13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Super Admin provider settings.
2. WhatsApp modes:
   - disabled
   - free wa.me
   - API
3. Map modes:
   - disabled
   - embed/free
   - API
4. OTP modes:
   - dev only
   - production provider
5. Email provider settings.
6. SMS provider settings.
7. Payment/storage summary if useful.
8. Mask secrets.
9. Provider health:
   - real check
   - or not checked
10. Provider test buttons if real.
11. Public UI follows provider mode.

Do not:
- Do not fake provider health.
- Do not fake WhatsApp sent.
- Do not fake SMS/email sent.
- Do not allow dev OTP in production.
- Do not expose secrets.
- Do not create decorative settings.

At the end output the IMPLEMENTATION REPORT.
PROMPT 12B — MANUAL VERIFICATION: PROVIDER MODES
Manually verify Part 12: Provider modes.

Super Admin:
1. Login as Super Admin.
2. Open provider settings.
3. Save provider settings.
4. Confirm secrets are masked.
5. Confirm settings are not visible to normal users.

WhatsApp:
1. Disabled mode hides/disables WhatsApp action.
2. Free mode opens wa.me.
3. API mode sends only if configured.
4. Missing API does not fake sent.

Maps:
1. Disabled mode hides map.
2. Embed/free mode shows safe map if configured.
3. API missing does not fake map.

OTP:
1. Dev OTP works only in development.
2. Dev/static OTP blocked outside development.
3. Missing OTP provider shows safe state.

Email/SMS:
1. Missing provider shows unavailable/setup-required.
2. No fake sent.
3. No fake verified.

Public effect:
1. Property contact follows WhatsApp mode.
2. Property detail map follows map mode.
3. Email verification follows email provider.

Security:
1. Secrets not in client.
2. Provider settings not public.
3. Service role not exposed.

Mobile:
1. Provider forms usable.
2. No horizontal scroll.

No-fake:
1. Provider health real or not checked.
2. No fake success.

If anything fails:
1. Mark FAIL.
2. Fix provider setting/runtime behavior.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
20. PART 13 — DATABASE / RLS / STORAGE / SECURITY
PROMPT 13A — IMPLEMENTATION: DATABASE + RBAC + RLS + STORAGE + SECURITY
Implement Part 13: Database, RBAC, RLS, storage and security hardening.

Read:
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md
- 21_FEATURE_REGISTRY_TEMPLATE.md
- 22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md

Implement:
1. Review all tables used so far.
2. Enable/fix RLS for sensitive tables.
3. Add/fix policies for:
   - profiles
   - user_roles
   - properties
   - requirements
   - proposals
   - leads
   - site_visits
   - messages
   - payments
   - subscriptions
   - banner_ads
   - verification
   - reports
4. Create public-safe views where needed.
5. Protect hidden phone/email/private address.
6. Protect private documents.
7. Ensure service role server-only.
8. Review storage buckets:
   - public images
   - private verification documents
   - support/message attachments
9. Add audit logs where possible.
10. Mark/remove demo data correctly.

Do not:
- Do not leave sensitive table public.
- Do not expose service role key.
- Do not make private documents public.
- Do not expose hidden phone in public payload.
- Do not bypass RLS with unsafe client calls.

At the end output the IMPLEMENTATION REPORT.
PROMPT 13B — MANUAL VERIFICATION: DATABASE + RLS + STORAGE + SECURITY
Manually verify Part 13: Database, RBAC, RLS, storage and security.

Public/anon:
1. Can read only approved active public data.
2. Cannot read leads.
3. Cannot read payments.
4. Cannot read private documents.
5. Cannot read hidden phone/email.
6. Cannot read admin settings/provider secrets.

Logged-in user:
1. Can read/update own profile.
2. Cannot update another user profile.
3. Can manage own listings only.
4. Cannot edit another user listing.

Role access:
1. Owner sees own leads.
2. Broker sees own leads.
3. Agency owner sees agency leads.
4. Agency agent sees assigned leads only.
5. Buyer cannot access broker leads.
6. Wrong role blocked.

Admin:
1. Admin access permission-based.
2. Super Admin access separate.
3. Normal user cannot access admin data.

Storage:
1. Public images load.
2. Private verification documents are not public.
3. Private support/message attachments are not public.
4. Signed URL/access check works if implemented.

Service role:
1. Service role key not imported in client.
2. Service role key not in public env.
3. Client bundle does not expose secret.

Feature flags:
1. Disabled feature blocks backend action if sensitive.

Demo/no-fake:
1. Demo data marked dev-only.
2. No fake production records.

If anything fails:
1. Mark FAIL.
2. Fix policies/storage/security.
3. Retest allowed and blocked users.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
21. PART 14 — NOTIFICATIONS / EXPIRY / ARCHIVE
PROMPT 14A — IMPLEMENTATION: NOTIFICATIONS + EXPIRY + ARCHIVE
Implement Part 14: Notifications, expiry, renewal, archive and automation hooks.

Read:
- 18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md
- 16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
- 15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. In-app notifications.
2. Notification center/header badge.
3. Notification preferences if possible.
4. External delivery only if provider configured.
5. Delivery logs real or hidden.
6. Expiry logic for:
   - listings
   - requirements
   - subscriptions
   - banner ads
   - boosts
   - featured listings
7. Archive/restore where needed.
8. Protected cron/job endpoint if implemented.
9. Dashboard expiry alerts.

Do not:
- Do not fake sent/delivered status.
- Do not fake job logs.
- Do not show expired active content.
- Do not leave cron endpoint public/dangerous.
- Do not spam duplicate notifications.

At the end output the IMPLEMENTATION REPORT.
PROMPT 14B — MANUAL VERIFICATION: NOTIFICATIONS + EXPIRY + ARCHIVE
Manually verify Part 14: Notifications, expiry and archive.

Notifications:
1. User receives own in-app notification.
2. Notification unread/read works.
3. Other user cannot see it.
4. Header badge count real.
5. Empty state works.

External channels:
1. Email missing does not fake sent.
2. WhatsApp API missing does not fake sent.
3. SMS missing does not fake sent.
4. Delivery logs real or hidden.

Listing expiry:
1. Expired listing hidden from active search.
2. Owner dashboard shows expired.
3. Renew CTA works if implemented.
4. Expired listing contact disabled if policy.

Requirement expiry:
1. Expired requirement hidden from feed.
2. New proposals blocked.

Banner ad expiry:
1. Expired ad hidden from homepage.

Subscription expiry:
1. Expired plan removes benefits unless grace configured.

Boost/Featured:
1. Expired boost label removed.
2. Expired featured label removed.

Archive:
1. Archived item hidden publicly.
2. History preserved.
3. Restore works if allowed.

Cron/job:
1. Endpoint protected if implemented.
2. Job logs real or hidden.
3. No fake success.

Mobile:
1. Notification center usable.
2. Expiry alerts usable.
3. No horizontal scroll.

If anything fails:
1. Mark FAIL.
2. Fix notification/expiry/archive issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
22. PART 15 — VERIFICATION / FRAUD / REPORTING
PROMPT 15A — IMPLEMENTATION: VERIFICATION + FRAUD + REPORTING + TRUST
Implement Part 15: Verification, fraud prevention, trust badges and reporting.

Read:
- 19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md
- 10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md
- 13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Verification request:
   - owner
   - broker
   - agency
   - builder
   - property/project if enabled
2. Private document upload.
3. Admin verification review:
   - approve
   - reject
   - need more details
4. Verified badge only after approval.
5. Expired/revoked verification removes badge.
6. RERA provided vs RERA verified distinction.
7. Report system:
   - property
   - profile
   - requirement
   - proposal
   - banner ad
   - message if enabled
8. Include “Broker pretending owner”.
9. Admin report queue.
10. Fraud flags admin-only.
11. Public safety warning.
12. Source tag and brokerage transparency.

Do not:
- Do not fake verified badge.
- Do not fake RERA verified.
- Do not make verification docs public.
- Do not fake ratings/reviews/trust score.
- Do not ignore reports.
- Do not allow broker to fake Direct Owner tag.

At the end output the IMPLEMENTATION REPORT.
PROMPT 15B — MANUAL VERIFICATION: VERIFICATION + FRAUD + REPORTING + TRUST
Manually verify Part 15: Verification, fraud, trust and reporting.

Verification:
1. Submit broker verification.
2. Submit agency verification if implemented.
3. Submit builder verification if implemented.
4. Upload document.
5. Confirm document stored private.
6. Verification status pending.

Admin:
1. Verification request appears in admin queue.
2. Approve verification.
3. Badge appears after approval.
4. Reject verification.
5. Badge does not appear after rejection.
6. Need more details works if implemented.
7. Revoke/expire removes badge if implemented.

Public trust:
1. Source tag visible.
2. Brokerage visible.
3. Verified badge only if real.
4. Pending/rejected has no badge.
5. Safety warning visible where needed.

RERA:
1. RERA provided does not show RERA Verified.
2. RERA Verified appears only if verified process/status exists.

Reports:
1. Report property works.
2. “Broker pretending owner” reason exists.
3. Report profile works if implemented.
4. Report requirement/proposal/banner ad works if implemented.
5. Report reaches admin queue.
6. Admin can mark valid/invalid/action taken.

Fraud:
1. Fraud flags are admin-only.
2. Public cannot see internal risk flags.
3. Reporter private details protected.

Storage/security:
1. Verification docs not publicly accessible.
2. Signed/private access only if permitted.

Mobile:
1. Report modal/bottom sheet usable.
2. Verification form usable.

No-fake:
1. No fake trust score.
2. No fake rating.
3. No fake review.
4. No fake badge.

If anything fails:
1. Mark FAIL.
2. Fix verification/report/privacy issue.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
23. PART 16 — CMS / BLOG / LEGAL
PROMPT 16A — IMPLEMENTATION: CMS + BLOG + LEGAL + STATIC PAGES
Implement Part 16: CMS, blog, static pages, legal pages, FAQ and support content.

Read:
- 20_CMS_BLOG_STATIC_PAGES_LEGAL_CONTENT_SPEC.md
- 05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md
- 13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
- 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
- 21_FEATURE_REGISTRY_TEMPLATE.md

Implement:
1. Public pages:
   - About
   - Contact
   - FAQ
   - Help/Support
   - Safety
2. Legal pages:
   - Privacy Policy
   - Terms & Conditions
   - Refund Policy
   - Listing Policy
   - Advertising Policy
   - Disclaimer
3. Safe disclaimer:
   - platform is listing/advertising/lead-generation platform
   - users verify property documents independently
   - platform payments are for platform services, not property token/purchase
4. Blog list/detail.
5. Admin CMS:
   - pages
   - blogs
   - FAQ
   - legal pages
6. Draft/publish.
7. SEO fields:
   - title
   - meta description
   - slug
   - noindex
8. CMS image upload safe.
9. Contact form creates support ticket or sends real provider email if configured.

Do not:
- Do not publish fake legal content as final.
- Do not fake contact form sent.
- Do not show draft content publicly.
- Do not make false legal/market claims.
- Do not show fake author/updated date.
- Do not use private docs as public CMS media.

At the end output the IMPLEMENTATION REPORT.
PROMPT 16B — MANUAL VERIFICATION: CMS + BLOG + LEGAL + STATIC PAGES
Manually verify Part 16: CMS, blog, legal and static pages.

Public pages:
1. About opens.
2. Contact opens.
3. FAQ opens.
4. Help/Support opens.
5. Safety opens.

Legal pages:
1. Privacy Policy opens.
2. Terms opens.
3. Refund Policy opens.
4. Listing Policy opens.
5. Advertising Policy opens.
6. Disclaimer opens.
7. Safety disclaimer is clear.
8. Platform does not claim property transaction guarantee.

Footer:
1. All legal/support links work.
2. No broken links.

Blog:
1. Blog list opens.
2. Published blog detail opens.
3. Draft blog not public.
4. SEO title/meta/slug works if implemented.

Admin CMS:
1. CMS admin protected.
2. Normal user cannot access CMS admin.
3. Content Manager permissions work if implemented.
4. Create/edit draft works.
5. Publish works if permission.
6. Draft content hidden from public.

Contact:
1. Contact form creates support ticket or sends real email.
2. If provider missing, safe unavailable/setup-required state.
3. No fake sent status.

CMS media:
1. Image upload safe.
2. Private verification docs not used as public CMS media.

Mobile:
1. Static pages readable.
2. Blog cards responsive.
3. No horizontal scroll.

No-fake:
1. No fake legal claim.
2. No fake market data.
3. No fake updated date.
4. No fake author if author system missing.

If anything fails:
1. Mark FAIL.
2. Fix CMS/legal/contact/mobile.
3. Retest.
4. Update Feature Registry.

At the end output the MANUAL VERIFICATION REPORT.
________________________________________
24. PART 17 — FULL QA / AUTO-FIX
PROMPT 17A — FULL QA IMPLEMENTATION PREP
Prepare for full QA and auto-fix.

Read:
- 22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
- 21_FEATURE_REGISTRY_TEMPLATE.md
- All docs from 00 to 23

Task:
1. Review Feature Registry.
2. Review all implemented routes.
3. Review known blockers.
4. Review known fake/data risks.
5. Prepare test user/role list.
6. Prepare QA checklist.
7. Do not run final QA yet unless next manual verification prompt is given.

Output:
- QA readiness summary
- Test roles available
- Missing roles/data
- Known blockers
- Recommended QA order
PROMPT 17B — MANUAL VERIFICATION: FULL AI QA + AUTO-FIX
Run full manual QA and auto-fix for My Gujarat Property.

Read:
- 22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
- 21_FEATURE_REGISTRY_TEMPLATE.md
- All docs from 00 to 23

You must run the app and test like real users.

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

Test modules:
1. Public website
2. Auth/Login/Register/OTP
3. Profile/role switching
4. Location/search/filters
5. Property posting
6. Property card/detail/contact/leads
7. Requirement/proposal/site visit/messaging
8. Role dashboards
9. Admin/Super Admin
10. Banner ads
11. Subscription/payment/credits/boost
12. Provider modes
13. Database/RLS/storage
14. Notifications/expiry/archive
15. Verification/fraud/reporting
16. CMS/blog/legal
17. Mobile full QA
18. No-fake sweep

Mandatory:
1. Test without login.
2. Test with login.
3. Test all relevant roles.
4. Test wrong-role blocked access.
5. Test mobile.
6. Test database save/update.
7. Test RLS/security.
8. Test provider missing states.
9. Test no-fake behavior.

If anything fails:
1. Mark FAIL.
2. Fix root cause.
3. Retest.
4. Update Feature Registry.
5. Repeat until PASS or clearly BLOCKED.

Do not:
- Do not ask user to manually check what you can test.
- Do not claim done without testing.
- Do not hide bugs.
- Do not introduce fake UI to cover missing functionality.

Final output:
- Overall status
- PASS modules
- FAIL modules
- PARTIAL modules
- BLOCKED modules
- Critical security issues
- Mobile issues
- Fake UI/data issues
- Fixes applied
- Retest result
- Feature Registry updates
- Final launch readiness: YES/NO
________________________________________
25. PART 18 — FINAL PRODUCTION SAFETY
PROMPT 18A — FINAL PRODUCTION SAFETY PREP
Prepare final production safety review for My Gujarat Property.

Read:
- All docs
- Feature Registry
- Latest QA reports

Task:
1. Review known production blockers.
2. Review provider modes.
3. Review security-sensitive modules.
4. Review payment/subscription status.
5. Review no-fake status.
6. Review mobile status.
7. Do not declare production ready yet.
8. Wait for separate manual verification prompt for final safety review.

Output:
- Production readiness preparation summary
- Known blockers
- Modules needing final check
- Safe disabled features
PROMPT 18B — MANUAL VERIFICATION: FINAL PRODUCTION SAFETY REVIEW
Perform final production safety manual verification for My Gujarat Property.

Do not add new features unless needed to fix critical/high issue.

Verify:
1. No dev OTP in production.
2. No service role key in client.
3. Admin routes protected.
4. Super Admin routes protected.
5. Public registration cannot create admin/staff roles.
6. RLS enabled on sensitive tables.
7. Private documents not public.
8. Hidden phone/email not public.
9. Payment activation requires server verification.
10. No fake payment success.
11. No fake verified badge.
12. No fake RERA verified.
13. No fake provider health.
14. No fake banner ads.
15. No fake dashboard data.
16. Expired listing/ad/subscription does not remain active.
17. Mobile key flows work.
18. Legal pages exist.
19. Report system works.
20. Feature Registry updated.

Manual testing:
1. Public guest flow.
2. Logged-in user flow.
3. All role dashboard access.
4. Admin access.
5. Super Admin access.
6. Public/private data access.
7. Mobile key flows.
8. No-fake sweep.
9. Payment safety.
10. Provider safety.

If fail:
1. Mark FAIL.
2. Fix critical/high issue.
3. Retest.
4. Do not mark production ready.

Final output:
- PRODUCTION READY: YES/NO
- Critical blockers
- High issues
- Safe disabled features
- Required fixes
- Final notes
________________________________________
26. SMALL FIX PROMPTS
PROMPT — SMALL FIX IMPLEMENTATION
Fix this specific issue in My Gujarat Property:

Issue:
[PASTE ISSUE HERE]

Rules:
- Fix only this issue and direct root cause.
- Do not rewrite unrelated modules.
- Do not remove working features.
- Preserve role permissions.
- Preserve RLS/security.
- Preserve mobile responsiveness.
- Do not introduce fake UI/data.
- If provider/payment missing, use safe setup-required state.

Output:
- Root cause
- Files changed
- Fix applied
- Build/type result
- Status
PROMPT — SMALL FIX MANUAL VERIFICATION
Manually verify the small fix just implemented.

Verify:
1. Reproduce original issue.
2. Confirm issue is fixed.
3. Test affected feature without login if relevant.
4. Test affected feature with relevant roles.
5. Test wrong-role blocked access if relevant.
6. Test mobile if UI affected.
7. Check console/server errors.
8. Confirm no fake UI/data introduced.
9. Update Feature Registry if status changed.

If fail:
1. Fix again.
2. Retest.

Output:
- Original issue
- Verification steps
- PASS items
- FAIL items
- Fixes applied
- Final status
________________________________________
27. ERROR FIX PROMPTS
PROMPT — ERROR FIX IMPLEMENTATION
Debug and fix this error in My Gujarat Property:

Error:
[PASTE FULL ERROR HERE]

Context:
[PASTE WHAT YOU WERE DOING]

Rules:
- Identify root cause.
- Fix smallest safe file set.
- Do not delete important features to silence error.
- Do not bypass TypeScript/security.
- Do not expose secrets.
- Do not create fake placeholder logic.
- Preserve existing behavior.

Output:
- Root cause
- Files changed
- Fix summary
- Build/type/lint result
- Remaining warnings
PROMPT — ERROR FIX MANUAL VERIFICATION
Manually verify the error fix.

Verify:
1. Run build/type/lint check if available.
2. Open affected route.
3. Test affected UI/action.
4. Test mobile if UI affected.
5. Check console/server errors.
6. Confirm no new broken route.
7. Confirm no fake data/UI added.
8. Update Feature Registry if needed.

If fail:
1. Fix again.
2. Retest.

Output:
- Error verified fixed: YES/NO
- Steps tested
- Remaining errors
- Final status
________________________________________
28. MOBILE FIX PROMPTS
PROMPT — MOBILE FIX IMPLEMENTATION
Fix this mobile/responsive issue in My Gujarat Property:

Issue:
[PASTE MOBILE ISSUE HERE]

Rules:
- Mobile-first.
- No horizontal scroll.
- Tables must become cards.
- Modals should become bottom sheets/full-screen where needed.
- Header must not wrap badly.
- CTA must remain visible.
- Forms must be usable with keyboard open.
- Tap targets must be large.
- Do not break desktop.
- Do not remove functionality.
- Do not use fake data.

Output:
- Issue found
- Files changed
- Fix applied
- Status
PROMPT — MOBILE FIX MANUAL VERIFICATION
Manually verify the mobile/responsive fix.

Verify:
1. Desktop layout.
2. Tablet layout.
3. Mobile layout.
4. No horizontal scroll.
5. Header not broken.
6. CTA visible.
7. Form usable.
8. Drawer/modal closes correctly.
9. Relevant role flow still works.
10. No console errors.

If fail:
1. Fix again.
2. Retest.

Output:
- Screens tested
- Mobile PASS/FAIL
- Desktop PASS/FAIL
- Remaining issues
- Final status
________________________________________
29. RLS / SECURITY FIX PROMPTS
PROMPT — RLS SECURITY FIX IMPLEMENTATION
Fix this Supabase RLS/security issue:

Issue:
[PASTE SECURITY/RLS ISSUE HERE]

Rules:
- Default deny sensitive data.
- Public reads only approved active public-safe data.
- Users access own data.
- Agency owner accesses agency data.
- Agent accesses assigned data only.
- Admin access requires permission.
- Super Admin access separate.
- Hidden phone/email/private address not public.
- Private documents not public.
- Service role server-only.

Output:
- Tables/policies affected
- Fix applied
- Files/migrations changed
- Status
PROMPT — RLS SECURITY MANUAL VERIFICATION
Manually verify the RLS/security fix.

Verify:
1. Public/anon allowed access works.
2. Public/anon blocked access works.
3. Correct user allowed.
4. Wrong user blocked.
5. Correct role allowed.
6. Wrong role blocked.
7. Private storage blocked publicly.
8. Public view excludes sensitive fields.
9. Client bundle does not use service role.
10. Feature Registry updated.

If fail:
1. Fix policy/security issue.
2. Retest.

Output:
- Allowed tests
- Blocked tests
- Security result
- Final PASS/FAIL
________________________________________
30. PAYMENT FIX PROMPTS
PROMPT — PAYMENT FIX IMPLEMENTATION
Fix this payment/subscription issue:

Issue:
[PASTE PAYMENT ISSUE HERE]

Rules:
- Never activate subscription from client-only success.
- Verify payment server-side.
- Failed/pending payment must not activate plan.
- Manual activation requires admin permission and audit note.
- No fake payment success.
- No fake invoice.
- Provider missing shows setup-required.
- Do not expose payment secrets.
- Plan limits enforced server-side.

Output:
- Root cause
- Files changed
- Fix applied
- Payment safety status
PROMPT — PAYMENT MANUAL VERIFICATION
Manually verify the payment/subscription fix.

Verify:
1. Pricing visible.
2. Login required for purchase.
3. Pending payment does not activate.
4. Failed payment does not activate.
5. Verified success activates only after server verification.
6. Plan limits apply.
7. Admin manual activation audited.
8. Mobile checkout state works.
9. No fake payment status.
10. No exposed payment secret.

If fail:
1. Fix again.
2. Retest.

Output:
- Payment states tested
- Subscription activation result
- Security result
- Final PASS/FAIL
________________________________________
31. PROVIDER FIX PROMPTS
PROMPT — PROVIDER FIX IMPLEMENTATION
Fix this provider mode issue:

Issue:
[PASTE PROVIDER ISSUE HERE]

Rules:
- Provider setting must affect real behavior.
- Disabled means hide/disable related feature.
- Free WhatsApp opens wa.me only.
- WhatsApp API sends only if configured.
- Map disabled hides map.
- Map API missing does not fake map.
- Email/SMS/OTP missing does not fake sent/verified.
- Dev OTP is development-only.
- Secrets masked/server-side.
- Provider health real or “not checked”.

Output:
- Provider issue
- Files changed
- Fix applied
- Status
PROMPT — PROVIDER MANUAL VERIFICATION
Manually verify the provider mode fix.

Verify:
1. Super Admin setting saves.
2. Public UI changes based on setting.
3. Missing provider shows safe state.
4. No fake sent status.
5. Secrets not exposed.
6. Mobile setting UI works.
7. Feature Registry updated.

If fail:
1. Fix provider behavior.
2. Retest.

Output:
- Provider mode tested
- Public behavior
- Admin behavior
- Security result
- Final PASS/FAIL
________________________________________
32. FEATURE REGISTRY PROMPTS
PROMPT — FEATURE REGISTRY UPDATE IMPLEMENTATION
Update My Gujarat Property Feature Registry.

Read:
- 21_FEATURE_REGISTRY_TEMPLATE.md
- Current codebase
- Latest QA/fix results

Update:
- Feature status
- Routes created
- Components created
- Database tables used
- RLS status
- Storage buckets
- Provider dependencies
- Feature flags
- Admin controls
- Mobile QA status
- Fake/data status
- PASS/FAIL status
- Blockers
- Bugs
- Fix notes

Rules:
- Do not mark PASS unless tested.
- Do not mark PRODUCTION_READY if security/mobile/no-fake checks failed.
- Mark missing provider as BLOCKED or setup-required.
- Mark fake UI/data if found.
- Keep registry concise.

Output:
- Registry sections updated
- Features changed
- Remaining blockers
- Next recommended action
PROMPT — FEATURE REGISTRY MANUAL VERIFICATION
Manually verify Feature Registry accuracy.

Verify:
1. All recently implemented features have entries.
2. Routes in registry match actual routes.
3. Components in registry match actual components.
4. Database tables match actual usage.
5. RLS status is honest.
6. Storage buckets status is honest.
7. Provider dependency status is honest.
8. Mobile QA status matches latest test.
9. Fake/data status is honest.
10. PASS/FAIL status matches latest manual verification.

If mismatch:
1. Fix registry.
2. Retest registry accuracy.

Output:
- Registry accuracy PASS/FAIL
- Fixed entries
- Remaining mismatches
- Final status
________________________________________
33. FINAL ALL DONE PROMPTS
PROMPT — FINAL ALL DONE PREP
Prepare final completion check for My Gujarat Property.

Read:
- All docs
- Feature Registry
- Latest QA reports

Review whether all required modules are:
- implemented
- safely disabled
- deferred intentionally
- blocked with reason
- tested
- no-fake
- mobile-ready
- secure

Output:
- Complete modules
- Pending modules
- Safe disabled modules
- Deferred modules
- Blocked modules
- Known critical launch blockers
PROMPT — FINAL ALL DONE MANUAL VERIFICATION
Run final all-done manual verification.

Check:
1. Public website
2. Auth
3. Roles/profile
4. Location/search/SEO
5. Property posting
6. Property detail/contact/leads
7. Requirements/proposals/site visits
8. Dashboards
9. Admin/Super Admin
10. Banner ads
11. Payments/subscriptions/credits
12. Provider modes
13. Database/RLS/storage
14. Notifications/expiry/archive
15. Verification/fraud/reporting
16. CMS/legal/blog
17. Mobile QA
18. No-fake sweep
19. Feature Registry
20. Final production blockers

Manual verification:
1. Recheck critical paths.
2. Confirm no critical blocker.
3. Confirm no fake production UI/data.
4. Confirm no private data leak.
5. Confirm mobile works for key flows.
6. Confirm safe disabled features are not shown as working.

If fail:
1. Fix critical/high issues.
2. Retest.
3. Do not say all done.

Output:
- ALL DONE: YES/NO
- Complete modules
- Safe disabled modules
- Deferred modules
- Blocked modules
- Critical launch blockers
- Final next step
________________________________________
34. FINAL WORKFLOW SUMMARY
Use this workflow:
PART 1A Implementation
PART 1B Manual Verification

PART 2A Implementation
PART 2B Manual Verification

PART 3A Implementation
PART 3B Manual Verification

Continue same way for every part.
Do not move to the next implementation prompt until the current manual verification prompt gives final status PASS or the remaining issue is clearly BLOCKED/DEFERRED.
________________________________________
35. FINAL RULE
Claude can say implementation is done after implementation prompt.
But Claude cannot say feature is fully done until separate manual verification prompt is completed.
Final completion requires:
•	implementation done
•	manual verification done
•	bugs fixed
•	retest done
•	Feature Registry updated
•	final status PASS or clearly BLOCKED/DEFERRED
________________________________________
36. END OF FILE
This file defines the final separated prompt system for My Gujarat Property.
Each part has:
1.	Implementation Prompt
2.	Separate Manual Verification Prompt
This prevents missing checks and keeps coding and QA clean.
Nothing from uploaded docs or user chat instructions should be skipped.

