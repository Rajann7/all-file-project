# MY GUJARAT PROPERTY

# ADMIN, SUPER ADMIN, SETTINGS, MODERATION, VERIFICATION & CONTROL PANEL SPEC

## FILE NAME

`13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete Admin and Super Admin control panel for **My Gujarat Property**.

This file must be read before building or redesigning:

* Admin dashboard
* Super Admin dashboard
* User management
* Role management
* Permission management
* Staff management
* Property moderation
* Project moderation
* Requirement moderation
* Proposal monitoring
* Lead monitoring
* Site visit monitoring
* Banner ads moderation
* Verification center
* Report/fraud center
* Subscription management
* Payment management
* CMS management
* Blog management
* SEO management
* Location management
* Provider settings
* WhatsApp settings
* Map settings
* OTP/email/payment settings
* Feature flags
* Platform settings
* Session timeout settings
* Storage/API/database usage view
* System health
* Audit logs
* Support tickets
* City manager scope
* Moderation workflows
* No-fake admin controls

The goal is to make the platform fully admin-controlled without requiring code changes for every business setting.

---

# 2. CORE ADMIN PRINCIPLE

Admin panel is not decorative.

Admin panel must be operational.

Every visible admin button, setting, toggle, metric and action must work or be hidden/clearly marked as disabled/future.

Admin panel must allow the platform owner/team to control:

* Users
* Listings
* Projects
* Requirements
* Leads
* Ads
* Payments
* Subscriptions
* Verification
* Content
* SEO
* Locations
* Providers
* Feature availability
* Platform rules
* Staff permissions
* Reports/fraud
* System status

No fake admin settings.

No disconnected toggles.

No fake charts.

No fake revenue numbers.

---

# 3. ADMIN VS SUPER ADMIN RULE

Admin and Super Admin are different.

## Admin

Admin manages day-to-day platform operations based on permissions.

Admin may manage:

* Users
* Properties
* Projects
* Requirements
* Leads
* Ads
* Verification
* Support
* CMS
* SEO
* Payments if permitted
* Subscriptions if permitted
* Moderation queues
* Reports

Admin cannot automatically control everything.

## Super Admin

Super Admin controls entire platform.

Super Admin can manage:

* Platform settings
* Admin/staff users
* Roles and permissions
* Provider modes
* Feature flags
* API/storage/database visibility
* Subscription plans
* Payment settings
* Banner ad pricing/settings
* Session timeout
* Security settings
* Maintenance mode
* Global SEO
* Audit logs
* Full system controls

Super Admin is the highest authority.

Super Admin access must be protected.

---

# 4. ADMIN ROLE TYPES

Operational admin/staff roles may include:

* Super Admin
* Admin
* Moderator
* Verification Executive
* Support Executive
* Content Manager
* Advertisement Manager
* City Manager
* Payment/Billing Manager if needed
* SEO Manager if needed

Each staff role must have scoped permissions.

Do not give everyone full admin access.

---

# 5. ADMIN ACCESS RULE

Admin access must never be available from public registration.

Public users must not select:

* Admin
* Super Admin
* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager

Admin/staff accounts should be:

* Created by Super Admin, or
* Invited by Admin if permission allows, or
* Seeded during secure setup

Admin login must be separate from public login/register or protected by role guard.

---

# 6. ADMIN ROUTE STRUCTURE

Recommended Admin routes:

```txt id="cycx6l"
/admin
/admin/dashboard
/admin/users
/admin/users/[id]
/admin/roles
/admin/permissions
/admin/staff
/admin/properties
/admin/properties/pending
/admin/properties/reported
/admin/projects
/admin/projects/pending
/admin/requirements
/admin/requirements/pending
/admin/proposals
/admin/leads
/admin/site-visits
/admin/messages
/admin/advertisements
/admin/advertisements/banner-ads
/admin/subscriptions
/admin/payments
/admin/verification
/admin/reports
/admin/fraud
/admin/support
/admin/cms
/admin/blogs
/admin/seo
/admin/locations
/admin/settings
/admin/audit-logs
/admin/system-health
```

Recommended Super Admin routes:

```txt id="m1ckmq"
/admin/super
/admin/super/platform
/admin/super/settings
/admin/super/brand
/admin/super/providers
/admin/super/feature-flags
/admin/super/roles
/admin/super/permissions
/admin/super/admins
/admin/super/subscriptions
/admin/super/payments
/admin/super/banner-ads
/admin/super/locations
/admin/super/seo
/admin/super/cms
/admin/super/security
/admin/super/sessions
/admin/super/storage
/admin/super/api-usage
/admin/super/database
/admin/super/audit-logs
/admin/super/system-health
/admin/super/maintenance
```

Only show routes that exist and are permitted.

---

# 7. ADMIN DASHBOARD OVERVIEW

Admin dashboard should show operational queues.

Dashboard cards may include:

* Pending properties
* Pending projects
* Pending requirements
* Pending banner ads
* Pending role change requests
* Pending verifications
* New reports
* New support tickets
* Payment issues
* Subscription expiring
* Suspicious activity
* Location requests
* CMS drafts
* System alerts

Only show real counts.

If data not available, hide or show empty state.

---

# 8. SUPER ADMIN DASHBOARD OVERVIEW

Super Admin dashboard should show platform control summary.

Cards may include:

* Total users
* Active users if tracked
* Active listings
* Pending moderation
* Revenue/payment summary if real
* Active subscriptions
* Active banner ads
* Provider health
* Storage usage
* API usage if available
* Database usage if available
* Feature flags summary
* System health
* Audit alerts
* Staff users
* Maintenance mode status

Do not show fake platform statistics.

If API/storage/database usage cannot be fetched, show setup-required or hide.

---

# 9. ADMIN UI DESIGN RULE

Admin panel should be:

* White-first
* Clean
* Operational
* Fast
* Filterable
* Searchable
* Queue-based
* Mobile-friendly
* Permission-aware
* Role-scoped
* Table on desktop
* Card-based on mobile
* No horizontal scroll on mobile

Admin must not be a cluttered dark template.

---

# 10. ADMIN MOBILE RULE

Admin mobile must work.

On mobile:

* Tables become cards.
* Sidebar becomes drawer.
* Filters become bottom sheet.
* Review details open full screen.
* Buttons are large enough.
* Bulk actions are hidden or simplified.
* No horizontal scroll.
* Admin forms remain usable.

Admin staff may use mobile for quick approvals.

---

# 11. USER MANAGEMENT

Admin can manage users based on permission.

User management should show:

* User name
* Phone
* Email
* Active role
* All roles
* Account status
* Verification status
* Subscription status
* Created date
* Last login if available
* City
* Reports/flags if real

User actions:

* View profile
* Edit limited fields if permitted
* Suspend
* Ban
* Restore
* Assign role if permitted
* Remove role if permitted
* View listings
* View leads summary if permitted
* View payments if permitted
* View audit log
* Reset session/revoke sessions if permitted

Do not expose private data without permission.

---

# 12. ROLE MANAGEMENT

Super Admin controls roles.

Roles may include:

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
* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager
* Admin
* Super Admin

Role management should allow:

* View roles
* Enable/disable public roles
* Configure role approval requirement
* Configure role default permissions
* Configure role dashboard route
* Configure role subscription requirement
* Configure role verification requirement
* Configure role visibility

Do not allow public users to choose admin/staff roles.

---

# 13. PERMISSION MANAGEMENT

Permissions should control access.

Permission examples:

* user.view
* user.manage
* role.manage
* permission.manage
* property.approve
* property.reject
* project.approve
* requirement.approve
* banner_ad.approve
* verification.approve
* payment.view
* payment.manage
* subscription.manage
* cms.manage
* seo.manage
* location.manage
* provider.manage
* feature_flag.manage
* audit.view
* admin.access
* super_admin.access

Permissions must be enforced server-side.

Do not rely only on UI hiding.

---

# 14. STAFF MANAGEMENT

Super Admin/Admin with permission can manage staff.

Staff management fields:

* Name
* Email/phone
* Staff role
* Permissions
* Assigned city if city-scoped
* Status
* Last login
* Created by
* Created date

Staff actions:

* Invite/create staff
* Change role
* Change permissions
* Assign city
* Suspend
* Deactivate
* Revoke sessions
* View audit activity

Staff cannot self-escalate.

---

# 15. CITY MANAGER SCOPE

City Manager should be location-scoped.

City Manager may manage:

* Properties in assigned city
* Requirements in assigned city
* Leads summary in assigned city if permitted
* Support tickets in assigned city
* Location requests in assigned city
* Banner ads in assigned city if permitted

Server-side query must enforce city scope.

City Manager cannot manage other cities unless assigned.

---

# 16. PROPERTY MODERATION

Property moderation queue should show:

* Pending properties
* Reported properties
* Rejected properties
* Need changes
* Expired/archived
* Duplicate suspicion if real
* User/source info
* Property type
* Location
* Price/rent
* Photos
* Documents if required
* Contact visibility
* Source tag
* Verification status
* Submitted date

Admin actions:

* Approve
* Reject
* Request changes
* Edit allowed fields
* Verify
* Mark duplicate
* Mark suspicious
* Archive
* Delete/soft delete
* Add internal note
* Add user-visible note

User should be notified.

No fake approval.

---

# 17. PROPERTY REVIEW DETAIL

Property review page/drawer should include:

* Full property details
* Media gallery
* Location
* Contact settings
* Owner/broker/agency/builder profile
* Plan/subscription context
* Previous moderation history
* Reports
* Duplicate candidates if implemented
* Verification documents if required
* Approval checklist
* Admin notes
* Audit log

Mobile review should open as full-screen detail.

---

# 18. PROJECT MODERATION

Project moderation for builder projects.

Review fields:

* Project name
* Builder
* Location
* RERA number if submitted
* Project status
* Unit configs
* Price range
* Brochure
* Images
* Amenities
* Contact settings
* Builder verification status

Admin actions:

* Approve
* Reject
* Request changes
* Verify RERA if process exists
* Archive
* Mark suspicious
* Add note

No fake RERA verification.

---

# 19. REQUIREMENT MODERATION

Requirement moderation queue should show:

* Buyer/Tenant requirement
* Requirement type
* City/locality
* Budget
* Property preferences
* Privacy setting
* Contact preference
* Submitted user
* Duplicate/spam risk if real
* Submitted date

Admin actions:

* Approve
* Reject
* Request changes
* Archive
* Mark spam
* Edit category/location if permitted

Do not expose buyer private contact to responders unless allowed.

---

# 20. PROPOSAL MONITORING

Admin may monitor proposals if permission allows.

Proposal monitoring should show:

* Requirement
* Sender role/entity
* Attached property/project
* Proposal message
* Status
* Created date
* Reports
* Spam flags if real

Admin actions:

* View
* Remove/disable if abusive
* Mark spam
* Warn user
* Archive
* Handle report

Do not unnecessarily expose private messages unless policy allows.

---

# 21. LEAD MANAGEMENT

Admin lead management should be permission-based.

Lead page may show:

* Lead source
* Property/project/requirement
* Sender
* Receiver
* Phone used
* Alternate number badge
* Status
* Created date
* Assigned agent
* Reports/issues

Admin actions:

* View
* Reassign if allowed
* Mark spam/invalid
* Resolve dispute
* Export if permitted
* Archive

Do not expose lead data to unauthorized staff.

---

# 22. SITE VISIT MANAGEMENT

Admin site visit page should show:

* Requested by
* Receiver/entity
* Property/project/proposal
* Date/time
* Status
* Assigned agent
* Phone used
* Alternate number badge
* Created date

Admin actions:

* View
* Reschedule if permitted
* Cancel if permitted
* Mark issue
* Resolve support case

Do not fake confirmed/completed visits.

---

# 23. MESSAGE MONITORING

Messages are private.

Admin should not freely browse all private messages unless policy/permission allows.

Allowed admin message access may include:

* Reported messages
* Support escalated threads
* Abuse cases
* Legal/compliance cases if defined

Admin actions:

* Review reported message
* Remove abusive content
* Warn/suspend user
* Close report
* Escalate

Do not expose private messages unnecessarily.

---

# 24. VERIFICATION CENTER

Verification center manages:

* User phone/email status
* Owner verification
* Broker verification
* Agency verification
* Builder verification
* Property verification
* Project verification
* Documents
* Role upgrade verification

Verification statuses:

```txt id="hsynoq"
Not Submitted
Pending
Under Review
Need More Details
Verified
Rejected
Expired
Suspended
```

Actions:

* Approve
* Reject
* Request more details
* Mark expired
* Suspend verification
* Add note

Verified badge must only appear after real approval.

---

# 25. ROLE CHANGE APPROVAL CENTER

Admin/Super Admin should manage role requests.

Role request queue shows:

* User
* Current role
* Requested role
* Submitted details
* Documents
* Current subscription
* Subscription impact
* Existing listings/leads
* Risk flags if real
* Status
* Submitted date

Actions:

* Approve
* Reject
* Request changes
* Add note
* Assign verification requirement
* Adjust subscription manually if permitted

Do not allow public self-approval.

---

# 26. SUBSCRIPTION IMPACT REVIEW

When approving role change, admin should see subscription impact.

Example:

* Current role: Owner
* Current plan: Owner Plan active until date
* Requested role: Broker
* Required plan: Broker Plan
* Migration rule: Keep current plan until expiry, new broker plan required

Admin actions if permitted:

* Keep existing plan
* Require new plan
* Apply credit if system supports
* Manual migration
* Reject until payment
* Add note

Do not silently migrate plans.

---

# 27. BANNER ADS MODERATION

Banner ads are approval-based.

Admin banner ads queue should show:

* Advertiser role/entity
* City targeting
* Placement
* Duration
* Payment status
* Desktop image
* Tablet image
* Mobile image
* Link/landing page
* Start date
* End date
* Status
* Sponsored label
* Rejection history

Actions:

* Approve
* Reject
* Request changes
* Schedule
* Pause
* Archive
* Renew if permitted
* View payment
* View analytics if real

Do not show unpaid/unapproved/expired ads publicly.

---

# 28. BANNER ADS STATUS

Banner statuses:

```txt id="e935lt"
Draft
Payment Pending
Submitted
Pending Review
Approved
Scheduled
Active
Paused
Rejected
Need Changes
Expired
Archived
Cancelled
```

Admin must be able to filter by status.

Expired ads auto-hide.

---

# 29. PAYMENT MANAGEMENT

Payment management should show only real payment data.

Payment records may include:

* Payment ID
* User/entity
* Plan/package
* Amount
* GST/tax if configured
* Provider
* Provider order ID
* Provider payment ID
* Status
* Created date
* Verified date
* Refund status if any

Statuses:

* Created
* Pending
* Success
* Failed
* Cancelled
* Refunded
* Partially Refunded
* Disputed
* Manually Verified

Payment success must be provider-verified.

No fake payment success.

---

# 30. SUBSCRIPTION MANAGEMENT

Admin/Super Admin can manage subscriptions if permitted.

Subscription records:

* User/entity
* Role
* Plan
* Start date
* Expiry date
* Status
* Usage limits
* Payment link
* Trial status
* Renewal status
* Manual override flag
* Admin note

Actions:

* View
* Activate manually if permitted
* Extend
* Cancel
* Expire
* Upgrade/downgrade
* Apply credit if implemented
* Renew
* View invoice/payment

Manual changes must be audit logged.

---

# 31. PLAN MANAGEMENT

Super Admin manages plans.

Plan configuration may include:

* Role
* Plan name
* Price
* Billing period
* Listing limit
* Image limit
* Requirement view limit
* Proposal limit
* Lead unlock limit
* Agent limit
* Project limit
* Unit limit
* Banner ad eligibility
* Featured/boost credits
* Trial days
* Active/inactive
* Public visibility
* Display order

Visible plans must actually control system behavior.

No fake plan features.

---

# 32. FREE LAUNCH OFFER CONTROL

Super Admin can manage launch offer.

Example:

```txt id="mqxn6e"
First 100 users free listing
```

Settings:

* Offer enabled
* Eligible roles
* Max users
* Max listings
* Start date
* End date
* Used count
* Remaining count
* Manual override
* Auto-disable when limit reached

Counts must be real.

No fake scarcity.

---

# 33. PROVIDER SETTINGS

Super Admin controls provider modes.

Provider categories:

* WhatsApp
* Maps
* OTP
* Email
* SMS if implemented
* Payment
* Storage
* Analytics if implemented
* AI if implemented

Provider settings must be server-side safe.

Secrets must not be exposed in client.

---

# 34. WHATSAPP SETTINGS

WhatsApp modes:

* Disabled
* Free wa.me mode
* API mode

Settings:

* Active mode
* API provider
* API key/server secret
* Sender number if API
* Default message templates
* Contact button enabled/disabled
* Fallback mode if allowed
* Logging enabled
* Rate limits

If API mode selected but not configured:

* Show setup-required.
* Do not fake message send.

---

# 35. MAP SETTINGS

Map modes:

* Disabled
* Free/embed/trial mode
* Premium API mode

Settings:

* Active mode
* Provider
* API key server/client config as appropriate
* Embed allowed domains
* Default map zoom
* Exact vs approximate location behavior
* Map on detail enabled
* Map on search enabled
* Lazy load setting

If API missing:

* Hide map or show setup-required.
* Do not fake map.

---

# 36. OTP SETTINGS

OTP settings:

* Provider
* API key/server secret
* Sender ID/template
* OTP length
* OTP expiry
* Resend cooldown
* Attempt limit
* Rate limit
* Development OTP mode
* Static dev OTP
* Public registration enabled
* Login enabled

Dev OTP must be development-only.

Production must not allow static OTP.

---

# 37. EMAIL SETTINGS

Email settings:

* Provider
* From email
* Templates
* Email verification enabled
* Notification email enabled
* Support email
* SMTP/API settings if used

If email provider missing:

* Do not show fake email sent.
* Show setup-required state.

---

# 38. PAYMENT SETTINGS

Payment settings:

* Payment provider
* Provider keys
* Webhook secret
* Currency
* Tax/GST settings if configured
* Payment mode test/live
* Refund settings if enabled
* Invoice numbering if implemented
* Payment verification required

Payment must be verified server-side.

Do not activate plan before verified payment unless admin manually overrides with audit.

---

# 39. STORAGE SETTINGS

Super Admin should view/manage storage settings where possible.

Storage areas:

* Public property images
* Project images
* Logos
* Banner ads
* Blog/CMS images
* Private verification documents
* Support attachments

Storage view may show:

* Bucket names
* Usage
* Limits
* Public/private status
* Upload limits
* File type rules

If actual usage cannot be fetched, show setup-required/hide.

Do not fake storage usage.

---

# 40. API / DATABASE / SYSTEM USAGE

Super Admin should have visibility into technical usage if available.

Possible panels:

* Database size
* Storage usage
* API request usage
* Auth users count
* Edge/server function errors
* Payment webhook status
* Provider health
* Queue jobs if implemented
* Cron jobs
* Email/OTP send counts if real

If not available, show:

```txt id="0u8dzl"
Usage data not configured.
```

Do not show fake usage.

---

# 41. FEATURE FLAGS

Super Admin controls feature flags.

Possible flags:

* Auth providers
* Public registration
* Property posting
* Requirement posting
* Proposals
* Site visits
* Messaging
* Banner ads
* Subscriptions
* Payments
* Free launch offer
* Maps
* WhatsApp
* SEO city pages
* Blog/CMS
* Verification
* Reports/fraud
* Public broker profiles
* Public agency profiles
* Public builder profiles
* Owner requirement access
* Agent system
* AI/manual verification

Feature flag behavior:

* Hide UI
* Block backend action
* Avoid dead routes
* Show safe disabled state if needed

No disconnected toggles.

---

# 42. PLATFORM SETTINGS

Super Admin platform settings may include:

* Site name
* Logo
* Favicon
* Brand color if implemented
* Default city
* Default state
* Maintenance mode
* Public registration enabled
* Property approval required
* Requirement approval required
* Banner ad approval required
* Default listing expiry
* Default requirement expiry
* Session timeout
* Contact visibility defaults
* Free/paid mode
* Launch offer settings
* Support contact
* Legal links
* Social links

Every visible setting must work.

---

# 43. SESSION SETTINGS

Super Admin should control session settings if implemented.

Settings:

* Public user session duration
* Staff/admin session duration
* Inactivity timeout
* Remember device duration
* Max active sessions
* Force logout all users
* Force logout role/user
* Admin session strict mode
* Suspended/banned auto logout

No fake session setting.

---

# 44. LOCATION MANAGEMENT

Admin/Super Admin manages:

* Countries
* States
* Districts
* Talukas
* Cities
* Villages
* Localities
* Societies
* Buildings
* Landmarks
* Missing location requests
* Duplicate merges
* Nearby city mapping
* City SEO settings
* City manager assignments

Detailed location rules are in location document.

---

# 45. SEO MANAGEMENT

Admin/Super Admin SEO controls:

* City SEO templates
* Locality SEO templates
* Meta title
* Meta description
* H1 templates
* Sitemap
* Robots
* Canonical settings
* Redirects
* Blog SEO
* CMS page SEO
* Noindex thin pages
* SEO enabled/disabled by page type

Do not create fake SEO controls.

---

# 46. CMS MANAGEMENT

CMS can manage:

* About
* Contact
* FAQ
* Privacy
* Terms
* Refund Policy
* Listing Policy
* Ad Policy
* Blog posts
* Guides
* Help pages
* Homepage content blocks if enabled

Content Manager role may manage CMS if permitted.

CMS should have draft/published status.

---

# 47. SUPPORT MANAGEMENT

Support panel should show:

* Tickets
* User
* Subject
* Category
* Priority
* Status
* Assigned staff
* Created date
* Last reply
* Attachments if any

Statuses:

* Open
* In Progress
* Waiting for User
* Resolved
* Closed

Actions:

* Reply
* Add internal note
* Assign
* Change status
* Escalate

Do not expose support tickets to wrong users/staff.

---

# 48. REPORT / FRAUD CENTER

Reports may include:

* Fake listing
* Wrong price
* Duplicate listing
* Broker pretending owner
* Already sold/rented
* Wrong location
* Spam requirement
* Proposal spam
* Message abuse
* Fake profile
* Payment issue
* Banner ad misleading
* Contact abuse

Admin actions:

* Review
* Mark valid/invalid
* Warn user
* Suspend listing/user
* Request changes
* Archive
* Close report

Fraud score should only show if real.

---

# 49. AUDIT LOGS

Audit logs are critical.

Log important actions:

* Admin login
* Staff creation
* Role change approval
* User suspension
* Property approval/rejection
* Project approval/rejection
* Requirement approval/rejection
* Banner ad approval/rejection
* Payment manual change
* Subscription manual change
* Provider setting change
* Feature flag change
* Plan change
* Location merge
* Verification approval/rejection
* Session revoke
* Maintenance mode change

Audit logs must include:

* Actor
* Action
* Entity
* Old value if safe
* New value if safe
* Timestamp
* IP/device if available
* Reason/note if applicable

Audit logs should not be editable by normal admin.

---

# 50. SYSTEM HEALTH

System health page may show:

* App status
* Database status
* Auth status
* Storage status
* Payment webhook status
* OTP provider status
* Email provider status
* WhatsApp provider status
* Map provider status
* Recent errors
* Cron jobs if implemented
* Queue jobs if implemented

If health checks are not implemented, hide or show setup-required.

No fake green status.

---

# 51. MAINTENANCE MODE

Super Admin can enable maintenance mode.

Settings:

* Maintenance enabled
* Public message
* Allowed admin access
* Estimated end text optional
* Disable public actions
* Keep admin accessible
* Emergency disable payments/posting if needed

Do not use maintenance mode without clear user message.

---

# 52. MODERATION QUEUE UX

All moderation queues should support:

* Search
* Filters
* Status tabs
* Bulk selection if implemented
* Detail drawer
* Quick approve/reject
* Reason required for rejection
* Internal note
* User-visible note
* Audit log
* Mobile card view

Mobile detail should open full-screen.

No horizontal scroll.

---

# 53. REJECTION REASON RULE

When rejecting:

* Require reason.
* Allow templates.
* Allow custom message.
* Show to user when appropriate.
* Store admin note separately.
* Allow resubmit if allowed.

Do not reject silently.

---

# 54. REQUEST CHANGES RULE

For property/project/requirement/banner/verification, admin can request changes.

User sees:

* What needs to change
* Status: Need Changes
* Edit/resubmit CTA
* Due date if any
* Support link if needed

System should not delete user’s submission.

---

# 55. ADMIN NOTIFICATIONS

Admin/staff notifications:

* New property pending
* New project pending
* New requirement pending
* New banner ad pending
* New verification pending
* New support ticket
* New report
* Payment failed issue
* Provider error
* Suspicious activity
* Location request

No fake alerts.

---

# 56. ADMIN SEARCH

Admin should have global search if implemented.

Searchable entities:

* Users
* Properties
* Projects
* Requirements
* Leads
* Payments
* Subscriptions
* Banner ads
* Tickets
* Locations
* CMS pages

Admin search must respect permissions.

City Manager search must respect city scope.

---

# 57. ADMIN EXPORTS

Exports are sensitive.

If implemented:

* Permission required.
* Audit logged.
* Role/city scope enforced.
* Mask private data if policy.
* Export only necessary fields.
* Rate limit export.

Export examples:

* Leads
* Properties
* Payments
* Users
* Subscriptions
* Banner ads

Do not expose all platform data to every admin.

---

# 58. ADMIN BULK ACTIONS

Bulk actions may include:

* Approve selected
* Reject selected
* Archive selected
* Assign selected
* Export selected
* Mark read
* Update status

Bulk actions must be permission-protected.

Require confirmation.

Do not bulk approve high-risk items without review if policy requires.

---

# 59. ADMIN DATA SECURITY

Admin panel must protect sensitive data.

Rules:

* Admin routes require admin/staff role.
* Super Admin routes require Super Admin.
* Server-side permission checks required.
* RLS policies required.
* Service role only server-side.
* Provider secrets never exposed to client.
* Private documents not public.
* Audit sensitive actions.
* Hide unauthorized data.
* Prevent self-escalation.
* Prevent deleting last Super Admin.

---

# 60. ADMIN STORAGE SECURITY

Private files:

* Verification documents
* Ownership documents
* ID proof
* Support private attachments
* Admin files

Only permitted staff can access.

Public files:

* Approved property images
* Project images
* Logos
* Banner ads
* Blog images

Do not mix private and public storage.

---

# 61. ADMIN LOADING STATES

Admin loading states:

* Dashboard loading
* Queue loading
* Detail loading
* Saving setting
* Approving item
* Rejecting item
* Uploading
* Exporting
* Provider status loading
* Audit log loading

Use skeleton/table placeholders.

Do not show blank admin panel.

---

# 62. ADMIN EMPTY STATES

Empty states:

```txt id="3qqgab"
No pending properties.
```

```txt id="vlqs0h"
No banner ads awaiting review.
```

```txt id="vfm4q3"
No support tickets open.
```

```txt id="2v3ntr"
No location requests.
```

No fake rows.

---

# 63. ADMIN ERROR STATES

Error states:

* Permission denied
* Failed to load queue
* Failed to approve
* Failed to reject
* Provider unavailable
* Payment verification failed
* Setting save failed
* Audit log unavailable
* Export failed
* Storage usage unavailable

Show clear messages.

Do not expose raw secrets/errors.

---

# 64. ADMIN SUCCESS STATES

Success states:

* Property approved
* Property rejected
* Changes requested
* Role approved
* Verification approved
* Banner ad approved
* Setting saved
* Feature flag updated
* Plan updated
* Payment manually verified
* Staff created
* Location approved
* Ticket replied

Show success only after server confirmation.

---

# 65. ADMIN NO-FAKE RULE

Do not fake:

* Dashboard metrics
* Revenue
* Payments
* Subscription status
* Provider health
* API usage
* Database usage
* Storage usage
* Approval status
* Verification status
* Staff permissions
* Audit logs
* Support tickets
* Leads
* Banner impressions/clicks
* SEO indexing status

If not implemented, hide or mark setup-required.

---

# 66. ADMIN FEATURE FLAGS

Possible feature flags:

```txt id="xzq5jv"
admin.enabled
admin.user_management.enabled
admin.role_management.enabled
admin.permission_management.enabled
admin.property_moderation.enabled
admin.project_moderation.enabled
admin.requirement_moderation.enabled
admin.banner_ads_moderation.enabled
admin.verification_center.enabled
admin.payment_management.enabled
admin.subscription_management.enabled
admin.cms.enabled
admin.blog.enabled
admin.seo.enabled
admin.location_management.enabled
admin.support.enabled
admin.audit_logs.enabled
admin.system_health.enabled
admin.exports.enabled
admin.bulk_actions.enabled
super_admin.enabled
super_admin.provider_settings.enabled
super_admin.feature_flags.enabled
super_admin.storage_usage.enabled
super_admin.api_usage.enabled
super_admin.database_usage.enabled
super_admin.maintenance.enabled
```

If feature flag off, hide routes/actions and block backend.

---

# 67. ADMIN COMPONENTS

Recommended components:

* AdminShell
* AdminHeader
* AdminSidebar
* AdminMobileDrawer
* AdminDashboardCards
* QueueTabs
* AdminDataTable
* AdminMobileCardList
* ReviewDrawer
* ReviewFullScreenMobile
* ApprovalActions
* RejectReasonModal
* RequestChangesModal
* UserManagementTable
* RolePermissionMatrix
* StaffManagementPanel
* PropertyReviewPanel
* ProjectReviewPanel
* RequirementReviewPanel
* BannerAdReviewPanel
* VerificationReviewPanel
* PaymentManagementTable
* SubscriptionManagementTable
* FeatureFlagPanel
* ProviderSettingsPanel
* PlatformSettingsPanel
* AuditLogTable
* SystemHealthPanel
* SupportTicketPanel
* LocationManagementPanel

Avoid duplicate random admin components.

---

# 68. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Normal user cannot access `/admin`.
* Admin can access admin dashboard.
* Super Admin can access super admin pages.
* Admin cannot access Super Admin settings unless permitted.
* Public registration does not show admin roles.
* Admin sidebar is permission-based.
* Admin tables become cards on mobile.
* Property approve/reject works.
* Project approve/reject works if implemented.
* Requirement approve/reject works if implemented.
* Banner ad approve/reject works if implemented.
* Role request approve/reject works.
* Verification badge appears only after real approval.
* Feature flag toggle works or is hidden.
* Provider settings save works or setup-required shown.
* WhatsApp mode affects public contact behavior.
* Map mode affects map display.
* Session timeout setting works or is hidden.
* Payment status is real.
* Subscription manual changes are audit logged.
* Storage/API/database usage is real or setup-required.
* Audit log records key admin actions.
* Mobile admin has no horizontal scroll.
* No screenshot/video capture required.

---

# 69. PASS / FAIL RULE

Admin/Super Admin phase is PASS only if:

* Admin routes are protected.
* Super Admin routes are protected separately.
* Admin/staff roles are not publicly selectable.
* Moderation queues work.
* Approval/rejection requires correct permissions.
* Settings shown in UI actually affect system.
* Provider modes affect related features.
* Feature flags hide/block related features.
* Payments/subscriptions are not fake.
* Banner ads approval works if ads enabled.
* Verification badge is real.
* Audit logs exist for important actions if implemented.
* Mobile admin is usable.
* No fake metrics/usage/provider health.
* Feature registry updated.
* Manual verification completed.

If normal user can access admin pages, mark FAIL.

If fake provider/payment/admin settings are visible, mark FAIL.

If Super Admin settings are accessible to normal Admin without permission, mark FAIL.

---

# 70. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md`
* `20_CMS_BLOG_STATIC_PAGES_LEGAL_CONTENT_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for specialized implementation details.

---

# 71. END OF FILE

This file defines Admin and Super Admin control panel requirements for My Gujarat Property.

Admin panel must be secure, role/permission-based, operational, mobile-friendly, no-fake, provider-aware, moderation-ready and capable of controlling the platform without unnecessary code changes.

Nothing from uploaded docs or user chat instructions should be skipped.
