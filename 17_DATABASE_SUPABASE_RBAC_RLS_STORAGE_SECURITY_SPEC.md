# MY GUJARAT PROPERTY

# DATABASE, SUPABASE, RBAC, RLS, STORAGE & SECURITY SPEC

## FILE NAME

`17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete database, Supabase architecture, authentication data model, RBAC, permission system, RLS policies, storage buckets, file access, audit logs, security rules and no-fake data requirements for **My Gujarat Property**.

This file must be read before building or redesigning:

* Supabase database
* Supabase Auth integration
* User profiles
* Roles
* Permissions
* Role-based dashboards
* Row Level Security policies
* Storage buckets
* Public/private file access
* Property tables
* Requirement tables
* Lead tables
* Proposal tables
* Site visit tables
* Subscription tables
* Payment tables
* Banner ad tables
* Admin tables
* Provider settings
* Audit logs
* Notification tables
* Security policies
* Service role usage
* No-fake UI/data enforcement
* API/server actions security

The goal is to make the platform secure, scalable, permission-safe and real-data-driven.

---

# 2. CORE DATABASE PRINCIPLE

Database is the source of truth.

Frontend UI must never fake platform data.

Every visible important state must come from real database/provider state or a clear empty/setup state.

Examples:

* Active plan must come from subscription/payment data.
* Verified badge must come from verification table.
* Active listing must come from property status.
* Banner ad active status must come from approval + payment + date.
* Lead count must come from real leads.
* Storage usage must be real or hidden.
* Provider health must be real or “not checked”.
* Role permission must be server-enforced.

No fake UI in production.

---

# 3. TECH STACK ASSUMPTION

Recommended stack:

* Next.js 15 App Router
* TypeScript
* Tailwind CSS
* Supabase Auth
* Supabase Postgres
* Supabase Storage
* Supabase Row Level Security
* Supabase SSR with cookies
* Server actions / route handlers
* Service role only on server
* Client uses anon key only
* Optional Edge Functions where useful

Do not expose service role key to client.

---

# 4. SUPABASE CLIENT RULE

Use separate Supabase clients.

## Browser Client

Used in client components.

Allowed:

* Public reads permitted by RLS
* Auth session operations
* User-scoped reads/writes permitted by RLS

Uses:

```txt id="m6p5ra"
NEXT_PUBLIC_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY
```

## Server Client

Used in server components/actions with user session.

Allowed:

* User-authenticated operations
* RLS enforced operations
* Secure server-side checks

## Admin/Service Client

Used only on server.

Allowed:

* Admin operations
* Moderation
* Provider secret actions
* System tasks

Uses:

```txt id="mg8l55"
SUPABASE_SERVICE_ROLE_KEY
```

Never import service role client into client-side code.

---

# 5. AUTH USER MODEL

Supabase Auth handles identity.

Application profile table stores business/user details.

Auth user should link to profile:

```txt id="gppx37"
auth.users.id = profiles.id
```

Profile stores:

* id
* full_name
* phone
* phone_verified
* email
* email_verified
* avatar_url
* active_role_id
* account_status
* default_city_id
* language
* created_at
* updated_at

Do not rely only on auth metadata for business roles.

---

# 6. ACCOUNT STATUS

Account statuses:

```txt id="zr1gdk"
active
pending
suspended
banned
deleted
archived
```

Rules:

* Suspended/banned users cannot perform protected actions.
* Banned users may be blocked from login/session usage.
* Deleted users handled according to policy.
* Account status checked server-side.
* RLS or server actions must enforce status.

---

# 7. ROLE MODEL

Roles should be database-driven.

Roles table:

* id
* name
* slug
* type
* is_public
* is_staff
* requires_approval
* requires_verification
* default_dashboard_route
* active
* created_at
* updated_at

Role examples:

* guest
* buyer
* tenant
* investor
* owner
* broker
* agency_owner
* agency_agent
* builder
* developer
* real_estate_group
* support_executive
* moderator
* verification_executive
* content_manager
* advertisement_manager
* city_manager
* admin
* super_admin

Public registration must not expose staff/admin roles.

---

# 8. USER ROLE MODEL

Users can have multiple roles.

`user_roles` table:

* id
* user_id
* role_id
* entity_id if role belongs to agency/builder/business entity
* status
* is_active
* approved_by
* approved_at
* rejection_reason
* created_at
* updated_at

Statuses:

```txt id="0hglc4"
pending
approved
rejected
suspended
revoked
expired
```

Only approved roles can be active.

Pending role must not grant access.

---

# 9. ACTIVE ROLE RULE

Active role must be stored and checked.

A user can switch only to approved roles.

Active role affects:

* Dashboard route
* Sidebar
* Permissions
* Listing source tag
* Subscription/plan
* Leads visibility
* Proposal access
* Banner ad access

Do not rely only on client state.

Server-side function should get active role securely.

---

# 10. PERMISSION MODEL

Permissions should be granular.

`permissions` table:

* id
* key
* module
* description
* active

`role_permissions` table:

* role_id
* permission_id
* allowed

`user_permission_overrides` optional:

* user_id
* permission_id
* allowed
* reason
* expires_at

Permission examples:

```txt id="mjsm4n"
property.create
property.update.own
property.approve
requirement.create
requirement.view.feed
proposal.create
lead.view.own
lead.view.assigned
banner_ad.create
banner_ad.approve
subscription.manage
provider.manage
admin.access
super_admin.access
```

Permissions must be enforced server-side.

---

# 11. RBAC CHECK RULE

Before any protected action:

Check:

* User authenticated
* Account active
* Active role approved
* Permission exists
* Entity ownership/assignment
* Plan/subscription if needed
* Feature flag enabled
* Entity status allows action

Do not rely on UI hiding.

Server actions must validate.

RLS must restrict row access.

---

# 12. RLS CORE RULE

RLS must be enabled for all sensitive tables.

Public tables can allow limited read.

Private tables require user/role checks.

Sensitive tables must never be open with broad anon access.

RLS should be designed per module.

If uncertain, default deny.

---

# 13. PUBLIC DATA RULE

Public anon users may read:

* Approved active properties public fields
* Approved active projects public fields
* Published CMS pages
* Published blogs
* Public city/locality data
* Active approved banner ads public fields
* Public business profiles if approved
* Pricing plans marked public
* Public SEO metadata

Public anon users must not read:

* Hidden contact numbers
* Private address
* Lead data
* Payment data
* Subscription data
* Verification documents
* Admin notes
* Private messages
* Draft/pending/rejected records
* Provider settings
* Audit logs

---

# 14. PRIVATE DATA RULE

Private data must be protected.

Private data includes:

* Phone number if hidden
* Email
* Full address if hidden
* Verification documents
* Payment records
* Subscription records
* Leads
* Messages
* Support tickets
* Admin notes
* Provider secrets
* Internal risk flags
* Service role operations
* Storage private files

Never expose private data in public API.

---

# 15. NO FAKE DATA RULE

Development fake/demo data is allowed only if clearly marked.

Development/demo records must include:

* is_demo = true, or
* environment = development, or
* clear seed marker

Production:

* Fake/demo data must be removed or hidden.
* Fake cards must not appear as real listings.
* Fake counts must not appear.
* Fake dashboards must not appear.

If data absent, show empty state.

---

# 16. CORE DATABASE MODULES

Major modules:

* Auth/Profile
* Roles/Permissions
* Locations
* Properties
* Projects
* Requirements
* Proposals
* Leads
* Site Visits
* Messages
* Notifications
* Subscriptions
* Payments
* Credits
* Boost/Featured
* Banner Ads
* Verification
* Reports/Fraud
* CMS/Blog
* SEO
* Provider Settings
* Admin/Staff
* Audit Logs
* Support
* Feature Flags
* Settings

Each module should be normalized enough for real usage.

---

# 17. PROFILE TABLES

Possible tables:

```txt id="lfvba8"
profiles
user_roles
roles
permissions
role_permissions
role_change_requests
user_sessions
user_devices
user_security_events
```

Profile must be one record per auth user.

Business profiles are separate.

---

# 18. BUSINESS PROFILE TABLES

Possible tables:

```txt id="k7rwki"
broker_profiles
agency_profiles
agency_agents
builder_profiles
developer_profiles
real_estate_group_profiles
business_profile_media
business_verifications
```

Agency agents should link to agency.

Builder projects should link to builder profile.

Broker listings should link to broker profile.

---

# 19. LOCATION TABLES

Possible tables:

```txt id="xd0lbr"
countries
states
districts
talukas
places
location_aliases
location_requests
nearby_location_mappings
location_seo
```

`places` can represent:

* city
* town
* village
* area
* locality
* society
* project
* building
* landmark

Must support Gujarat hierarchy.

---

# 20. PROPERTY TABLES

Possible tables:

```txt id="xy4v9n"
properties
property_locations
property_pricing
property_details
property_amenities
property_media
property_documents
property_contact_settings
property_status_history
property_moderation
property_reports
property_boosts
featured_listings
```

Property must store structured fields, not only JSON/free text.

Some flexible fields can be JSONB but important search/filter fields should be columns.

---

# 21. PROPERTY CORE FIELDS

`properties` may include:

* id
* owner_user_id
* owner_entity_type
* owner_entity_id
* listing_source_type
* purpose
* category
* property_type
* title
* slug
* description
* status
* approval_status
* verification_status
* is_featured
* is_boosted
* is_demo
* created_at
* updated_at
* published_at
* expires_at

No public listing if not approved/active.

---

# 22. PROPERTY LOCATION FIELDS

`property_locations` may include:

* property_id
* state_id
* district_id
* taluka_id
* city_id
* village_id
* area_id
* locality_id
* society_id
* building_id
* landmark
* address_line
* pin_code
* latitude
* longitude
* location_visibility
* map_accuracy
* custom_location_text

Private exact address must not be public unless allowed.

---

# 23. PROPERTY PRICING FIELDS

`property_pricing` may include:

* property_id
* sale_price
* monthly_rent
* deposit
* maintenance
* price_per_unit
* currency
* price_on_request
* negotiable
* brokerage_type
* brokerage_amount
* other_charges
* payment_note

Do not store property transaction payments as platform payments.

---

# 24. PROJECT TABLES

Possible tables:

```txt id="5s0ftc"
projects
project_locations
project_units
project_media
project_documents
project_amenities
project_moderation
project_status_history
```

Projects link to builder/developer.

RERA data must be real if shown.

---

# 25. REQUIREMENT TABLES

Possible tables:

```txt id="gbs2ou"
requirements
requirement_locations
requirement_preferences
requirement_status_history
requirement_reports
```

Requirements must protect buyer/tenant private contact.

Requirement public/feed views should expose safe fields only.

---

# 26. PROPOSAL TABLES

Possible tables:

```txt id="k3umql"
proposals
proposal_properties
proposal_messages
proposal_status_history
proposal_reports
```

Proposal links:

* requirement_id
* sender_user_id
* sender_entity_id
* property_id or project_id if attached
* status

Do not expose proposals to unrelated users.

---

# 27. LEAD TABLES

Possible tables:

```txt id="ggjgpt"
leads
lead_contacts
lead_events
lead_notes
lead_assignments
lead_status_history
contact_reveals
call_clicks
whatsapp_clicks
```

Lead must store current/alternate number context.

Fields:

* sender_user_id
* receiver_user_id
* receiver_entity_id
* property_id
* project_id
* requirement_id
* proposal_id
* phone_source
* profile_phone_at_time
* lead_phone_used
* alternate_phone_used
* status
* source

Lead access must be ownership/assignment-scoped.

---

# 28. SITE VISIT TABLES

Possible tables:

```txt id="hq5yfl"
site_visits
site_visit_status_history
site_visit_notes
site_visit_reminders
```

Fields:

* requested_by_user_id
* receiver_user_id/entity
* property_id/project_id/proposal_id
* assigned_agent_id
* requested_date
* requested_time
* confirmed_datetime
* status
* phone_used
* alternate_phone_used

---

# 29. MESSAGE TABLES

Possible tables:

```txt id="ow50lf"
message_threads
message_participants
messages
message_attachments
message_reports
```

Messages must be private.

Participants can see only their own threads.

Agency owner/agent access must follow policy.

Reported messages can be reviewed by admin if permitted.

---

# 30. SUBSCRIPTION/PAYMENT TABLES

Possible tables:

```txt id="swmiq9"
plans
plan_features
subscriptions
subscription_usage
payments
payment_events
invoices
credits
credit_transactions
trials
launch_offers
boosts
featured_listings
refunds
coupons
```

Payment success must be verified server-side.

No subscription activation on fake client success.

---

# 31. BANNER ADS TABLES

Possible tables:

```txt id="jl9t6n"
banner_ad_packages
banner_ads
banner_ad_images
banner_ad_targets
banner_ad_payments
banner_ad_status_history
banner_ad_clicks
banner_ad_impressions
banner_ad_moderation
```

Public query returns only approved/paid/active ads.

---

# 32. VERIFICATION TABLES

Possible tables:

```txt id="q3uj0s"
verification_requests
verification_documents
verification_status_history
verification_notes
```

Verification entities:

* user
* owner
* broker
* agency
* builder
* property
* project
* banner_ad if needed

Private documents stored in private bucket.

Verified badge comes only from approved verification.

---

# 33. REPORT/FRAUD TABLES

Possible tables:

```txt id="iwkduv"
reports
report_status_history
fraud_flags
moderation_actions
blocked_entities
```

Reports can target:

* property
* project
* requirement
* proposal
* message
* profile
* banner ad
* user

Fraud flags must be real if shown.

---

# 34. CMS/SEO TABLES

Possible tables:

```txt id="me683s"
cms_pages
blog_posts
blog_categories
faq_items
seo_pages
seo_templates
redirects
sitemap_entries
```

Draft CMS/blog pages must not be public.

Published pages can be public.

SEO noindex rules must be stored/enforced.

---

# 35. PROVIDER SETTINGS TABLES

Possible tables:

```txt id="lnrg8s"
provider_settings
provider_health_checks
provider_logs
feature_flags
platform_settings
```

Secrets must be encrypted or stored server-side securely.

Do not expose secret values in client.

---

# 36. NOTIFICATION TABLES

Possible tables:

```txt id="ojbm79"
notifications
notification_preferences
notification_templates
notification_delivery_logs
```

Delivery logs must reflect real delivery.

If email/WhatsApp/SMS not sent, do not mark as sent.

---

# 37. AUDIT LOG TABLE

`audit_logs` table should include:

* id
* actor_user_id
* actor_role
* action
* module
* entity_type
* entity_id
* old_values if safe
* new_values if safe
* ip_address if available
* user_agent if available
* note
* created_at

Audit important actions:

* Role changes
* Admin approvals
* Payments manual changes
* Provider settings changes
* Feature flags changes
* Verification approvals
* Listing approvals
* User suspensions
* Staff permission changes

Audit logs should be append-only.

---

# 38. STORAGE BUCKETS

Recommended buckets:

## Public Buckets

```txt id="533rsv"
property-images
project-images
profile-avatars
business-logos
banner-ads
blog-images
cms-images
public-brochures
```

## Private Buckets

```txt id="x2twst"
verification-documents
property-private-documents
support-attachments
message-attachments-private
admin-files
payment-documents
```

Do not store private documents in public buckets.

---

# 39. STORAGE ACCESS RULE

Public files:

* Can be publicly read if approved/public.
* Upload requires authenticated user and permission.
* Delete/update requires owner/admin permission.

Private files:

* No public read.
* Signed URL only for permitted users/admin.
* Access checks server-side.
* Verification documents accessible only to permitted staff.
* Message attachments accessible only to thread participants.
* Support attachments accessible only to ticket participants/support staff.

---

# 40. STORAGE PATH RULE

Use structured paths.

Examples:

```txt id="1c3pif"
property-images/{property_id}/{file_id}.webp
project-images/{project_id}/{file_id}.webp
profile-avatars/{user_id}/{file_id}.webp
business-logos/{entity_type}/{entity_id}/{file_id}.webp
banner-ads/{ad_id}/{device}/{file_id}.webp
verification-documents/{entity_type}/{entity_id}/{file_id}.pdf
```

Avoid exposing private IDs if sensitive.

---

# 41. FILE VALIDATION RULE

Validate files by:

* MIME type
* Extension
* Size
* Dimensions for images
* Count limits
* Role/plan limits
* Virus scanning if available
* Safe filename
* Storage bucket permission

Never trust client-side validation only.

---

# 42. IMAGE PROCESSING RULE

Images should be:

* Previewed
* Cropped where needed
* Resized/compressed if possible
* Stored safely
* Served optimized
* Associated with entity record
* Deleted/cleaned if abandoned

Do not stretch images.

Do not accept huge unoptimized files without limits.

---

# 43. RLS — PROFILES

Profile RLS:

* User can read/update own profile.
* Public can read only public business-safe profile fields through public views.
* Admin can read/update based on permission.
* Super Admin can manage all.
* Private phone/email not public unless intended.

Use views for public profile data.

---

# 44. RLS — USER ROLES

User roles RLS:

* User can read own roles.
* User cannot approve own role.
* User cannot create admin/staff role.
* Admin can manage roles based on permission.
* Super Admin can manage all.
* Only approved role can be active.

---

# 45. RLS — PROPERTIES

Property RLS:

Public can read only:

* active
* approved
* non-private fields
* not expired/hidden
* public listing

Owner/entity user can read/write own drafts/listings.

Agency owner can manage agency listings.

Agent can manage assigned listings if allowed.

Admin/moderator can manage based on permission.

Hidden contact/address not included in public select.

Use public views for card/detail data.

---

# 46. RLS — REQUIREMENTS

Requirement RLS:

Buyer/Tenant can manage own requirements.

Eligible responders can read active requirements according to:

* plan
* role
* city
* visibility
* status

Public anon reads only if requirement public and safe.

Contact/private buyer info hidden unless shared.

Admin can moderate based on permission.

---

# 47. RLS — LEADS

Lead RLS:

Sender can read own submitted leads if product allows.

Receiver can read leads for own listing/entity.

Agency owner can read agency leads.

Agent can read assigned leads only.

Admin can read based on permission.

No public access.

---

# 48. RLS — PROPOSALS

Proposal RLS:

Sender can read/manage own proposals.

Requirement owner can read received proposals.

Agency owner can read agency proposals.

Agent can read assigned/own proposals.

Admin can moderate based on permission.

No public access unless safe summary intentionally created.

---

# 49. RLS — SITE VISITS

Site visit RLS:

Requester can read own visits.

Receiver can read visits for own listing/entity.

Agency agent sees assigned visits.

Admin can manage based on permission.

No public access.

---

# 50. RLS — MESSAGES

Message RLS:

Participants can read thread messages.

Agency owner access only if policy permits and thread belongs to agency.

Agent access only if participant/assigned.

Admin access only for reported/support cases if policy.

No public access.

---

# 51. RLS — PAYMENTS/SUBSCRIPTIONS

Payments/subscriptions RLS:

User/entity can read own billing records.

Agency owner can read agency billing.

Agent cannot read billing unless permitted.

Admin can read/manage based on permission.

No public access.

Manual changes require audit.

---

# 52. RLS — BANNER ADS

Banner ad RLS:

Advertiser can read/manage own draft/submitted ads.

Public can read only active approved paid public ad fields.

Admin can moderate.

Super Admin can manage packages/settings.

No public read of payment/admin notes.

---

# 53. RLS — ADMIN SETTINGS

Provider settings, feature flags and platform settings:

* Super Admin read/write by default.
* Admin read/write only if permission.
* Public cannot read secrets/settings.
* Some public-safe settings can be exposed through sanitized endpoint/view.

Never expose provider secrets.

---

# 54. DATABASE VIEWS

Use safe public views.

Examples:

* public_property_cards
* public_property_details
* public_projects
* public_banner_ads
* public_city_pages
* public_business_profiles
* public_pricing_plans

Views should exclude:

* phone if hidden
* email
* private address
* admin notes
* payment data
* provider secrets
* drafts/pending/rejected records

---

# 55. SERVER ACTION SECURITY

Every server action should:

* Validate user session
* Validate input
* Check permission
* Check ownership/assignment
* Check status
* Check plan/usage if needed
* Use transaction where needed
* Return safe errors
* Audit important action
* Never trust client values for role/price/status/payment

---

# 56. INPUT VALIDATION

Validate all input:

* Phone
* Email
* Price/rent
* Area
* Location IDs
* Role ID
* Status transitions
* File upload
* Message text
* Description text
* External URLs
* Payment IDs
* Provider settings

Use schema validation where possible.

Sanitize user content.

---

# 57. STATUS TRANSITION RULE

Do not allow random status updates.

Example property transitions:

```txt id="uphwnt"
Draft → Pending Approval → Active
Pending Approval → Rejected
Pending Approval → Need Changes
Active → Sold/Rented/Expired/Archived
Expired → Renewed/Active
```

Only permitted roles can perform transitions.

Audit important transitions.

---

# 58. PAYMENT SECURITY RULE

Payment activation must:

* Verify payment server-side.
* Match amount/plan.
* Match user/entity.
* Prevent duplicate activation.
* Store payment event.
* Activate subscription/credit/ad in transaction if possible.

Never trust client-only payment success.

---

# 59. PROVIDER SECRETS RULE

Provider secrets:

* Stored in environment or secure encrypted settings.
* Server-only access.
* Masked in admin UI.
* Never returned to client.
* Never logged full.
* Audit changes.

Includes:

* Payment secret
* OTP API key
* WhatsApp token
* Email API key
* Map server key
* Supabase service role key

---

# 60. API RATE LIMITING

Rate limit high-risk actions:

* OTP send
* OTP verify
* Login attempts
* Contact reveal
* Lead submit
* Proposal send
* Message send
* File upload
* Payment create
* Report submit
* Search autocomplete
* Location request
* Admin test provider action

Rate limits can be implemented at app level/provider level.

---

# 61. SECURITY EVENTS

Log security events:

* Failed login attempts
* OTP abuse
* Unauthorized route access
* Permission denied
* Contact scraping attempt
* Rate limit hit
* Provider test
* Admin login
* Staff permission change
* Suspicious payment callback
* Storage access denied

Do not expose security logs publicly.

---

# 62. BACKUP / MIGRATION RULE

Database changes should use migrations.

Rules:

* Use versioned migrations.
* Avoid manual production DB edits where possible.
* Seed roles/permissions carefully.
* Seed Gujarat locations from reliable source.
* Back up before destructive changes.
* Avoid dropping data without migration plan.
* Add indexes for search/filters.

---

# 63. INDEXING RULE

Add indexes for common queries.

Examples:

* properties(status, approval_status, city_id)
* properties(property_type, purpose)
* property_pricing(price)
* property_locations(city_id, locality_id)
* requirements(status, city_id)
* leads(receiver_entity_id, status)
* banner_ads(status, start_at, end_at)
* subscriptions(user_id, role_id, status)
* user_roles(user_id, role_id, status)
* places(parent_id, type)
* places(slug)

Avoid slow unindexed search.

---

# 64. DATABASE PERFORMANCE RULE

Performance rules:

* Use pagination.
* Avoid loading full records for cards.
* Avoid N+1 queries.
* Use public views.
* Use selective columns.
* Use server-side filtering.
* Cache safe static data.
* Optimize location dropdowns.
* Lazy load heavy dashboard data.
* Use indexes.

---

# 65. ENVIRONMENT SEPARATION

Separate environments:

* Development
* Staging if used
* Production

Development:

* Demo data allowed if marked.
* Dev OTP allowed.
* Test payment mode.

Production:

* No dev OTP.
* No fake demo listings.
* Live provider configs.
* Secure secrets.
* RLS enabled.
* Backups.
* Audit logs.

---

# 66. TEST USERS RULE

Test users may be created for development/manual verification.

Test users must be:

* Clearly marked
* Restricted to dev/staging
* Removed or disabled before production
* Not counted as real users
* Not shown as real brokers/builders/listings

Do not seed fake production marketplace data.

---

# 67. PRIVACY AND COMPLIANCE BASICS

Platform must protect user data.

Rules:

* Collect only needed data.
* Do not expose phone/email without consent/mode.
* Allow privacy settings where needed.
* Protect verification documents.
* Use secure authentication.
* Provide privacy policy.
* Provide terms.
* Allow account support/deletion workflow if implemented.
* Log admin access to sensitive data if possible.

---

# 68. ADMIN SECURITY

Admin security rules:

* Admin route protected.
* Super Admin route separately protected.
* Staff roles not public.
* Permission checks server-side.
* Last Super Admin cannot be removed accidentally.
* Staff cannot self-escalate.
* Sensitive settings require Super Admin.
* Audit logs for admin actions.
* Optional shorter admin session timeout.

---

# 69. NO-FAKE UI ENFORCEMENT

Every UI component should have data state:

* Real data
* Loading
* Empty
* Error
* Setup required
* Disabled by feature flag
* Coming later only if explicitly allowed

Avoid fake placeholder data.

Examples:

If no leads:

```txt id="mnmjmz"
No leads yet.
```

Not:

```txt id="bknm9e"
Showing fake sample leads as real.
```

If payment not configured:

```txt id="in69g7"
Online payment is not configured.
```

Not:

```txt id="js7vh6"
Payment successful.
```

---

# 70. FEATURE FLAGS TABLE

Feature flags table:

* key
* enabled
* module
* description
* updated_by
* updated_at

Feature flags must control both:

* UI visibility
* Backend action permission

Example:

If `banner_ads.enabled = false`:

* Hide banner ad UI.
* Block banner ad server actions.
* Do not display public ads.

---

# 71. PLATFORM SETTINGS TABLE

Platform settings table can store:

* site_name
* default_city
* default_state
* listing_approval_required
* requirement_approval_required
* banner_ad_approval_required
* default_listing_expiry_days
* default_requirement_expiry_days
* session_timeout_days
* maintenance_mode
* support_email
* support_phone
* brand settings

Public-safe settings can be exposed through sanitized endpoint.

Secret/private settings not exposed.

---

# 72. DATABASE SEEDING RULE

Seed required base data:

* Roles
* Permissions
* Role permissions
* Super Admin user/role
* Gujarat state
* Initial districts/cities/talukas if available
* Basic feature flags
* Platform settings
* Free/default plans if using subscriptions
* CMS required pages if needed

Do not seed fake production listings as real.

---

# 73. SECURITY MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* RLS is enabled for sensitive tables.
* Public can view active approved property only.
* Public cannot view draft/pending property.
* Public cannot read hidden contact.
* Public cannot read lead data.
* Buyer cannot access broker leads.
* Agent cannot access unassigned agency leads.
* Admin route protected.
* Super Admin route protected.
* Public registration cannot create admin role.
* Service role key not used in client.
* Private documents not publicly accessible.
* Payment activation requires verified payment.
* Banner ad public query returns only active approved paid ads.
* Verified badge appears only from real verification.
* Feature flag hides UI and blocks backend.
* Demo/test data marked and not shown as real.
* Provider secrets masked.
* Audit log records important admin action.
* No screenshot/video capture required.

---

# 74. PASS / FAIL RULE

Database/Security phase is PASS only if:

* Supabase clients are separated correctly.
* Service role key is server-only.
* RLS is enabled for sensitive tables.
* Public views exclude private data.
* RBAC permissions are server-enforced.
* User roles cannot self-escalate.
* Admin routes are protected.
* Storage buckets separate public/private files.
* Private documents are not public.
* Payment success is server-verified.
* Feature flags control UI and backend.
* No fake production data appears.
* Audit logs exist for critical admin actions if implemented.
* Manual verification completed.

If service role key appears in client code, mark FAIL.

If hidden contacts are publicly readable, mark FAIL.

If public can access leads/payments/private docs, mark FAIL.

If fake payment activates plan, mark FAIL.

---

# 75. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for feature-specific behavior.

---

# 76. END OF FILE

This file defines database, Supabase, RBAC, RLS, storage and security requirements for My Gujarat Property.

The system must be secure, role-aware, RLS-protected, storage-safe, no-fake, auditable and production-ready.

Nothing from uploaded docs or user chat instructions should be skipped.
