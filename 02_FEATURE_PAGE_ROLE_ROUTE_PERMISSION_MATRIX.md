# MY GUJARAT PROPERTY

# FEATURE, PAGE, ROLE, ROUTE, DASHBOARD, MODAL & PERMISSION MATRIX

## FILE NAME

`02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete feature-to-page, role-to-dashboard, route-to-permission, modal-to-action and mobile-to-desktop behavior matrix for **My Gujarat Property**.

Claude must read this file before creating or changing:

* Routes
* Public pages
* Search pages
* Property pages
* Project pages
* Requirement pages
* Login/register flow
* Profile pages
* Role-based dashboards
* Admin pages
* Super Admin settings
* Forms
* Modals
* Drawers
* Bottom sheets
* Banner ad flows
* Subscription flows
* Lead/contact flows
* Site visit flows
* Messaging flows
* SEO pages
* CMS pages
* Provider settings
* Feature flags
* Permission checks

The goal is to make sure no feature, role, page, modal, dashboard, route, permission or mobile behavior is missed.

Claude must not build pages randomly.

Every feature must be mapped to:

* Role
* User intent
* Route
* UI component
* Dashboard area
* Admin control if required
* Permission
* Feature flag
* Database table if applicable
* Provider dependency if applicable
* Loading state
* Empty state
* Error state
* Success state
* Mobile behavior
* Desktop behavior
* Security rule
* No-fake UI rule

---

# 2. CORE MATRIX RULE

No feature should exist only visually.

Every visible feature must answer:

1. Who can see it?
2. Who can use it?
3. Which role can manage it?
4. Which route owns it?
5. Which dashboard shows it?
6. Which admin setting controls it?
7. Which permission protects it?
8. Which database table stores it?
9. Which provider is needed?
10. What happens when provider is missing?
11. What happens on mobile?
12. What happens on desktop?
13. What happens when data is empty?
14. What happens when user is not logged in?
15. What happens when user has wrong role?
16. What happens when subscription is expired?
17. What happens when admin disables feature?
18. What happens when item is pending approval?
19. What happens after expiry?
20. What is shown to Super Admin?

If these answers are missing, the feature is incomplete.

---

# 3. ABSOLUTE NO-SKIP RULE

Claude must not skip anything from:

* Current uploaded documents
* Regenerated docs
* User chat instructions
* Current codebase
* Feature registry
* Phase reports

If a feature exists in docs but is not implemented in current phase:

* Add it to feature registry
* Mark status correctly
* Do not pretend it exists
* Do not show fake UI
* Do not silently remove it
* Do not create dead buttons

Status options:

```txt id="pvvah4"
Not Started
In Progress
Implemented
Verified
Needs Fix
Blocked
Disabled
Future
Removed by User Instruction
```

---

# 4. FEATURE REGISTRY CONNECTION

Every feature in this matrix must eventually be tracked in:

```txt id="4wjyfy"
/docs/feature-registry.md
```

or regenerated file:

```txt id="i7pagq"
21_FEATURE_REGISTRY_TEMPLATE.md
```

Required feature registry fields:

* Feature name
* Feature group
* Related document
* Route
* Component
* Dashboard
* Admin screen
* Database table
* Storage bucket
* Server action/API
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
* Current implementation status
* Manual verification status

No visible UI feature should be missing from the registry.

---

# 5. GLOBAL ROLE LIST

The platform must support these roles.

## Public Role

* Guest

## Demand-Side Roles

* Buyer
* Tenant
* Investor
* NRI Buyer if implemented later
* Commercial Buyer if implemented later

## Supply-Side Roles

* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Developer if separated later
* Real Estate Group if implemented separately

## Operational Roles

* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager

## Administrative Roles

* Admin
* Super Admin

---

# 6. GLOBAL FEATURE GROUPS

All platform features belong to one or more of these groups:

1. Public website
2. City/location system
3. Homepage search
4. Dynamic filters
5. Property listings
6. Property detail
7. Project listings
8. Buyer requirements
9. Broker proposals
10. Leads/contact requests
11. Site visits
12. Messaging
13. Notifications
14. Login/register/OTP
15. Role-based profiles
16. Role change approvals
17. Owner dashboard
18. Broker dashboard
19. Agency dashboard
20. Agent dashboard
21. Builder dashboard
22. Buyer dashboard
23. Tenant dashboard
24. Admin panel
25. Super Admin settings
26. Banner ads carousel
27. Subscriptions/pricing
28. Payments/credits/boosts
29. Provider modes
30. SEO/city/locality pages
31. CMS/blog/static pages
32. Verification/trust
33. Fraud/reporting
34. Storage/media upload
35. Analytics if implemented
36. Audit logs
37. Support tickets
38. Feature flags
39. Manual verification
40. Production cleanup

---

# 7. GUEST ROLE MATRIX

Guest means user is not logged in.

## 7.1 Guest Can

Guest can:

* Visit homepage
* Select city
* Use homepage search
* Search properties
* View search results
* View active public properties
* View active public projects
* View public broker profiles
* View public agency profiles
* View public builder profiles
* View city pages
* View locality pages
* View SEO pages
* View pricing/subscription page
* View blogs
* View FAQ
* View About page
* View Contact page
* View Help/Support public pages
* Open login/register popup
* Start contact flow but must login if required
* Start save flow but must login
* Start post property flow but must register/login
* Start post requirement flow but must register/login
* View approved homepage banner ads
* View approved sponsored placements
* View public CMS/static pages

## 7.2 Guest Cannot

Guest cannot:

* Post property
* Post requirement
* Save property
* Compare property if login required
* Book site visit
* Send message
* View hidden contact numbers
* Access dashboards
* Access admin
* Send proposal
* Manage listings
* Manage ads
* Buy subscription without login
* Upload media
* Access private documents
* View leads
* View messages
* View notifications
* Change role
* Access profile
* Access billing
* Access restricted banner ad submission

## 7.3 Guest UI Requirements

Guest desktop header:

* Logo
* City selector
* Search entry
* Navigation
* Pricing
* Post Property CTA if enabled
* Login/Register button

Guest mobile header:

* Compact logo
* City selector
* Search icon or search entry
* Login/Register or menu
* Hamburger menu
* Post Property inside menu if space is limited

Guest mobile menu:

* Login/Register card
* City selector
* Buy
* Rent
* Commercial
* Land/Plots
* Projects
* PG/Hostel
* Buyer Requirements
* Post Property
* Post Requirement
* Pricing
* Blog/Guides
* Help
* Contact
* Legal links

Restricted guest actions must open login/register popup with preserved intent.

---

# 8. BUYER ROLE MATRIX

Buyer searches and buys property.

## 8.1 Buyer Can

Buyer can:

* Search properties
* Save properties
* Compare properties if implemented
* Save searches
* Post buyer requirements
* Edit own requirements
* Close own requirements
* Receive proposals
* View proposal details
* Respond to proposals
* Contact sellers/brokers if allowed
* Submit lead forms
* Use current profile number for lead
* Use alternate number for lead
* Book site visits
* View own site visits
* View messages if implemented
* View notifications
* View buyer dashboard
* Manage profile
* Verify email from profile
* Request role change
* View subscription/pricing
* Buy buyer-related optional plan if enabled
* Report property
* View public banner ads

## 8.2 Buyer Cannot

Buyer cannot:

* Approve listings
* Manage other users
* Access admin
* Send broker proposals unless active broker role exists
* Manage property listings unless owner/broker role exists
* View hidden seller/admin data
* View other buyers’ private requirements
* Self-change role without approval
* Self-edit subscription status

## 8.3 Buyer Routes

Recommended routes:

```txt id="1q7w06"
/dashboard/buyer
/dashboard/buyer/saved-properties
/dashboard/buyer/saved-searches
/dashboard/buyer/compare
/dashboard/buyer/requirements
/dashboard/buyer/requirements/new
/dashboard/buyer/requirements/[id]
/dashboard/buyer/requirements/[id]/proposals
/dashboard/buyer/site-visits
/dashboard/buyer/messages
/dashboard/buyer/notifications
/dashboard/buyer/profile
/dashboard/buyer/subscription
/dashboard/buyer/settings
```

Only implemented routes should appear in navigation.

## 8.4 Buyer Dashboard

Buyer dashboard should show:

* Saved properties
* Saved searches
* Active requirements
* New proposals
* Upcoming site visits
* Recent contact activity
* Messages if implemented
* Notifications
* Profile completion
* Plan/subscription status if enabled
* Recommended actions

## 8.5 Buyer Mobile UX

Buyer dashboard must be card-based.

No wide tables.

Important mobile cards:

* Saved property card
* Requirement card
* Proposal card
* Site visit card
* Message preview
* Notification card

---

# 9. TENANT ROLE MATRIX

Tenant focuses on rent, PG, hostel and co-living.

## 9.1 Tenant Can

Tenant can:

* Search rental properties
* Search PG/hostel/co-living
* Save rental listings
* Save searches
* Post rental requirements
* Receive proposals
* Contact owners/brokers if allowed
* Use current or alternate number for leads
* Book site visits
* View tenant dashboard
* View messages if implemented
* View notifications
* Manage profile
* Request role change
* View pricing/subscription
* Report listing

## 9.2 Tenant Cannot

Tenant cannot:

* Approve listings
* Manage admin data
* Manage other users
* Send broker proposals unless broker role exists
* View restricted landlord/broker data
* Access owner/broker dashboards unless role exists
* Self-upgrade to business roles without approval if required

## 9.3 Tenant Routes

```txt id="j5yw85"
/dashboard/tenant
/dashboard/tenant/saved-rentals
/dashboard/tenant/saved-searches
/dashboard/tenant/requirements
/dashboard/tenant/requirements/new
/dashboard/tenant/requirements/[id]
/dashboard/tenant/proposals
/dashboard/tenant/site-visits
/dashboard/tenant/messages
/dashboard/tenant/notifications
/dashboard/tenant/profile
/dashboard/tenant/subscription
/dashboard/tenant/settings
```

## 9.4 Tenant Dynamic Filters

Tenant search should support:

* Rent amount
* Deposit
* Furnishing
* Tenant type
* Family/bachelor
* PG boys/girls/co-ed
* Food included
* Sharing type
* AC/non-AC
* Move-in date
* Nearby area
* Rules/preferences

Do not show irrelevant purchase filters for rental/PG flow.

---

# 10. OWNER ROLE MATRIX

Owner is an individual property seller/landlord.

## 10.1 Owner Can

Owner can:

* Create own property listing
* Edit own property listing
* Upload property media
* Upload documents if enabled
* Set contact visibility
* Submit property for approval
* Pause property
* Mark sold/rented/leased
* Archive listing
* Renew listing
* Promote listing if enabled
* View own leads
* View contact requests
* Approve/reject contact requests if mode requires it
* Manage site visits
* Approve/reject/reschedule visits
* View analytics if real
* Manage owner profile
* View subscription/plan
* Buy owner plan
* Request role change
* View notifications
* Report support issue

## 10.2 Owner Cannot

Owner cannot:

* Approve properties
* Manage other users
* View other owners’ leads
* Access broker requirement feed unless broker role exists
* Pretend to be broker if broker behavior detected
* Access admin
* Self-edit subscription status
* View platform revenue

## 10.3 Owner Routes

```txt id="hx72xs"
/dashboard/owner
/dashboard/owner/properties
/dashboard/owner/properties/new
/dashboard/owner/properties/[id]
/dashboard/owner/properties/[id]/edit
/dashboard/owner/properties/[id]/analytics
/dashboard/owner/properties/[id]/leads
/dashboard/owner/properties/[id]/visits
/dashboard/owner/contact-requests
/dashboard/owner/site-visits
/dashboard/owner/messages
/dashboard/owner/notifications
/dashboard/owner/subscription
/dashboard/owner/billing
/dashboard/owner/profile
/dashboard/owner/support
/dashboard/owner/settings
```

## 10.4 Owner Dashboard

Owner dashboard should show real data:

* Active properties
* Pending approval
* Expiring listings
* New leads
* Contact requests
* Upcoming visits
* Profile completion
* Plan usage
* Recent activity

No fake metrics.

---

# 11. BROKER ROLE MATRIX

Broker manages multiple listings and buyer requirements.

## 11.1 Broker Can

Broker can:

* Create listings
* Manage listings
* Upload listing media
* View buyer requirements based on plan/permission
* Send proposals
* Manage leads
* Manage lead pipeline
* View contact requests
* Manage site visits
* Use WhatsApp/contact tools if allowed
* Manage broker profile
* Upload broker photo/logo
* View subscription/plan
* Buy broker plan
* Promote listings
* Buy banner ads if enabled for broker
* View dashboard analytics if real
* Request agency role if needed
* View messages if implemented
* View notifications
* Manage operating cities/localities

## 11.2 Broker Cannot

Broker cannot:

* Approve listings
* Access admin
* Manage other brokers
* View platform revenue
* Bypass requirement view limits
* Misrepresent as owner
* Self-verify broker account
* Self-edit subscription status
* View agency team features unless agency role exists

## 11.3 Broker Routes

```txt id="6i2vv8"
/dashboard/broker
/dashboard/broker/listings
/dashboard/broker/listings/new
/dashboard/broker/listings/[id]
/dashboard/broker/listings/[id]/edit
/dashboard/broker/requirements
/dashboard/broker/requirements/[id]
/dashboard/broker/proposals
/dashboard/broker/proposals/new
/dashboard/broker/leads
/dashboard/broker/lead-pipeline
/dashboard/broker/site-visits
/dashboard/broker/messages
/dashboard/broker/notifications
/dashboard/broker/analytics
/dashboard/broker/subscription
/dashboard/broker/billing
/dashboard/broker/profile
/dashboard/broker/verification
/dashboard/broker/banner-ads
/dashboard/broker/support
/dashboard/broker/settings
```

## 11.4 Broker Dashboard

Broker dashboard should show:

* Active listings
* Pending listings
* Requirement views used
* Proposals sent
* New leads
* Lead stages
* Site visits
* Plan usage
* Expiring listings
* Verification status
* Banner ads if enabled

No fake analytics.

---

# 12. AGENCY OWNER ROLE MATRIX

Agency Owner manages agency business and team.

## 12.1 Agency Owner Can

Agency Owner can:

* Create/manage agency profile
* Upload agency logo
* Add agents
* Remove agents
* Activate/deactivate agents
* Assign properties
* Assign leads
* Assign site visits
* Manage agency listings
* Manage buyer requirements
* Send proposals
* View agency leads
* View agent performance if real
* Manage subscription
* Buy agency plan
* Submit homepage banner ads
* Manage banner ads
* View banner ad analytics if implemented
* Promote listings
* Manage agency verification
* View messages if implemented
* View notifications
* Manage billing
* Request role changes
* Manage operating cities

## 12.2 Agency Owner Cannot

Agency Owner cannot:

* Access platform admin
* Manage other agencies
* Approve public listings unless admin permission
* View platform revenue
* Bypass plan limits
* Self-verify agency
* Self-edit subscription status
* Access Super Admin settings

## 12.3 Agency Routes

```txt id="oaq2dj"
/dashboard/agency
/dashboard/agency/profile
/dashboard/agency/agents
/dashboard/agency/agents/new
/dashboard/agency/listings
/dashboard/agency/listings/new
/dashboard/agency/requirements
/dashboard/agency/proposals
/dashboard/agency/leads
/dashboard/agency/lead-pipeline
/dashboard/agency/site-visits
/dashboard/agency/messages
/dashboard/agency/notifications
/dashboard/agency/analytics
/dashboard/agency/subscription
/dashboard/agency/billing
/dashboard/agency/banner-ads
/dashboard/agency/banner-ads/new
/dashboard/agency/banner-ads/[id]
/dashboard/agency/verification
/dashboard/agency/support
/dashboard/agency/settings
```

## 12.4 Agency Dashboard

Agency dashboard should show:

* Agency profile completion
* Active listings
* Active agents
* Assigned leads
* Unassigned leads
* New requirements
* Proposals
* Site visits
* Plan usage
* Banner ads
* Banner ad status
* Subscription expiry
* Verification status

---

# 13. AGENCY AGENT ROLE MATRIX

Agent works under agency.

## 13.1 Agent Can

Agent can:

* View assigned leads
* View assigned listings if allowed
* View assigned site visits
* Update lead notes if permitted
* Update lead status if permitted
* Contact leads if permitted
* View messages if implemented
* View notifications
* Manage own profile
* View assigned tasks

## 13.2 Agent Cannot

Agent cannot:

* Manage agency subscription
* Remove other agents
* Access all agency leads unless permitted
* Manage billing
* Submit agency banner ads unless permitted
* Approve listings
* Access admin
* Change agency settings
* View platform revenue
* Self-expand permissions

## 13.3 Agent Routes

```txt id="gz6x8m"
/dashboard/agent
/dashboard/agent/leads
/dashboard/agent/listings
/dashboard/agent/site-visits
/dashboard/agent/tasks
/dashboard/agent/messages
/dashboard/agent/notifications
/dashboard/agent/profile
/dashboard/agent/settings
```

Agent UI must always be assignment-scoped.

---

# 14. BUILDER ROLE MATRIX

Builder manages projects and units.

## 14.1 Builder Can

Builder can:

* Create builder profile
* Upload builder logo
* Create projects
* Manage projects
* Add units
* Upload project media
* Upload brochures
* Add amenities
* Submit projects for approval
* View project leads
* Manage site visits
* Manage builder subscription
* Buy builder plan
* Submit homepage banner ads if enabled
* Promote projects
* View real analytics if implemented
* Manage team if implemented
* View messages if implemented
* View notifications
* Manage verification

## 14.2 Builder Cannot

Builder cannot:

* Access admin
* Approve own projects
* View other builders’ leads
* View platform revenue
* Self-verify builder account
* Self-edit subscription status
* Manage unrelated properties unless role permits

## 14.3 Builder Routes

```txt id="ebojb5"
/dashboard/builder
/dashboard/builder/profile
/dashboard/builder/projects
/dashboard/builder/projects/new
/dashboard/builder/projects/[id]
/dashboard/builder/projects/[id]/edit
/dashboard/builder/projects/[id]/units
/dashboard/builder/projects/[id]/leads
/dashboard/builder/projects/[id]/visits
/dashboard/builder/leads
/dashboard/builder/site-visits
/dashboard/builder/messages
/dashboard/builder/notifications
/dashboard/builder/analytics
/dashboard/builder/subscription
/dashboard/builder/billing
/dashboard/builder/banner-ads
/dashboard/builder/verification
/dashboard/builder/support
/dashboard/builder/settings
```

---

# 15. REAL ESTATE GROUP ROLE MATRIX

Real Estate Group can be implemented separately or mapped to Agency/Builder/Broker plan depending product decision.

## 15.1 Real Estate Group Can

If implemented, Real Estate Group can:

* Create group profile
* Upload logo
* Manage group listings if allowed
* Submit paid banner ads
* Manage banner ad campaigns
* Target cities
* View ad status
* View ad expiry
* View ad analytics if implemented
* Manage subscription/payment
* View leads if connected
* Manage verification

## 15.2 Real Estate Group Cannot

Real Estate Group cannot:

* Access admin
* Approve its own ads
* Run unpaid ads if paid feature is required
* Bypass approval
* Bypass expiry
* Fake impressions/clicks
* Self-edit billing status

## 15.3 Real Estate Group Routes

```txt id="ih7ber"
/dashboard/real-estate-group
/dashboard/real-estate-group/profile
/dashboard/real-estate-group/banner-ads
/dashboard/real-estate-group/banner-ads/new
/dashboard/real-estate-group/banner-ads/[id]
/dashboard/real-estate-group/subscription
/dashboard/real-estate-group/billing
/dashboard/real-estate-group/verification
/dashboard/real-estate-group/settings
```

If not implemented separately, use Agency dashboard banner ad module.

---

# 16. MODERATOR ROLE MATRIX

Moderator handles content and listing review.

## 16.1 Moderator Can

Moderator can:

* View moderation dashboard
* Review pending properties
* Review reported properties
* Review pending requirements
* Review reported requirements
* Review project submissions if permitted
* Review reviews/comments if implemented
* Approve/reject/request changes if permission allows
* Add moderation notes
* View limited user info required for moderation
* View fraud queues if assigned

## 16.2 Moderator Cannot

Moderator cannot:

* Manage payments
* Manage subscriptions
* Manage Super Admin settings
* Manage admin roles
* View platform secrets
* Delete Super Admin
* Change provider settings
* Change revenue settings
* Access unrelated user private data

## 16.3 Moderator Routes

```txt id="nt9ary"
/admin/moderation
/admin/properties/pending
/admin/properties/reported
/admin/requirements/pending
/admin/requirements/reported
/admin/projects/pending
/admin/reviews
/admin/reports
```

---

# 17. SUPPORT EXECUTIVE ROLE MATRIX

Support Executive handles user support.

## 17.1 Support Executive Can

Support Executive can:

* View support tickets
* Reply to tickets
* Add internal notes
* Escalate tickets
* View related user/profile summary
* View related property/lead reference if needed
* Mark ticket status
* Assign ticket if permitted

## 17.2 Support Executive Cannot

Support Executive cannot:

* Approve listings unless separate permission
* Manage payments unless separate permission
* Change user roles
* Access Super Admin settings
* View provider secrets
* Change platform settings

## 17.3 Support Routes

```txt id="w7gfvg"
/admin/support
/admin/support/tickets
/admin/support/tickets/[id]
```

---

# 18. VERIFICATION EXECUTIVE ROLE MATRIX

Verification Executive handles trust and document checks.

## 18.1 Verification Executive Can

Verification Executive can:

* Review user verification
* Review broker verification
* Review agency verification
* Review builder verification
* Review property verification
* Review documents
* Approve/reject/request changes if permitted
* Add verification notes
* View required private documents securely

## 18.2 Verification Executive Cannot

Verification Executive cannot:

* Manage subscriptions
* Manage payments
* Change provider settings
* Manage Super Admins
* Access unrelated private documents
* Download/export sensitive documents unless permitted

## 18.3 Verification Routes

```txt id="i33ru9"
/admin/verification
/admin/verification/users
/admin/verification/brokers
/admin/verification/agencies
/admin/verification/builders
/admin/verification/properties
/admin/verification/documents
```

---

# 19. CONTENT MANAGER ROLE MATRIX

Content Manager handles CMS, blog and SEO content if permitted.

## 19.1 Content Manager Can

Content Manager can:

* Create/edit blogs
* Manage blog categories
* Manage FAQ
* Manage CMS pages
* Manage static content
* Edit SEO metadata if permitted
* Manage city/locality SEO text if permitted
* Upload CMS/blog media
* Preview content
* Publish content if allowed

## 19.2 Content Manager Cannot

Content Manager cannot:

* Manage users
* Manage payments
* Manage provider settings
* Manage subscriptions
* Access private leads
* Approve properties unless assigned
* Access Super Admin settings

## 19.3 Content Routes

```txt id="4m5w9e"
/admin/cms
/admin/cms/pages
/admin/blogs
/admin/blogs/new
/admin/blogs/[id]
/admin/faq
/admin/seo
/admin/seo/city-pages
/admin/seo/locality-pages
```

---

# 20. ADVERTISEMENT MANAGER ROLE MATRIX

Advertisement Manager handles banner ads and sponsored placements.

## 20.1 Advertisement Manager Can

Advertisement Manager can:

* View banner ad submissions
* Review pending banner ads
* Approve/reject ads
* Request creative changes
* Manage ad placements if permitted
* View ad payments if permission allows
* View ad analytics if real
* Manage ad categories
* Manage sponsored placement queues
* Add rejection reason
* Archive expired ads if needed

## 20.2 Advertisement Manager Cannot

Advertisement Manager cannot:

* Fake impressions
* Fake clicks
* Mark unpaid ad as paid unless admin permission
* Bypass payment verification
* Manage Super Admin settings
* Manage provider secrets
* Change subscription plans unless permitted

## 20.3 Advertisement Routes

```txt id="ibc1lh"
/admin/advertisements
/admin/advertisements/banner-ads
/admin/advertisements/banner-ads/pending
/admin/advertisements/banner-ads/active
/admin/advertisements/banner-ads/expired
/admin/advertisements/banner-ads/[id]
/admin/advertisements/placements
/admin/advertisements/pricing
```

---

# 21. CITY MANAGER ROLE MATRIX

City Manager handles assigned city operations.

## 21.1 City Manager Can

City Manager can:

* View assigned city data
* Review properties in assigned city if permitted
* Review requirements in assigned city if permitted
* Manage city support tickets if permitted
* View city leads summary if permitted
* View city SEO/content if permitted
* View city banner ads if permitted
* Manage location requests for assigned city if permitted

## 21.2 City Manager Cannot

City Manager cannot:

* Manage other cities
* Access Super Admin settings
* View platform-wide revenue unless permitted
* Manage provider secrets
* Manage global settings
* Manage other city users unless assigned

## 21.3 City Manager Routes

```txt id="zi4oa9"
/admin/city-manager
/admin/city-manager/properties
/admin/city-manager/requirements
/admin/city-manager/leads
/admin/city-manager/banner-ads
/admin/city-manager/locations
/admin/city-manager/support
```

Every query must enforce city scope server-side.

---

# 22. ADMIN ROLE MATRIX

Admin manages platform operations based on permissions.

## 22.1 Admin Can

Admin can:

* Access admin panel
* Manage users if permitted
* Manage properties if permitted
* Manage requirements if permitted
* Manage projects if permitted
* Manage leads if permitted
* Manage support tickets if permitted
* Manage CMS if permitted
* Manage SEO if permitted
* Manage ads if permitted
* Manage verification if permitted
* Manage reports if permitted
* Manage subscriptions if permitted
* View payments if permitted
* Manage settings if permitted
* View audit logs if permitted

## 22.2 Admin Cannot

Admin cannot:

* Delete Super Admin
* Manage Super Admin unless explicitly allowed
* Access service secrets directly
* Bypass audit logs
* Self-escalate permissions
* Disable security without permission
* Access private data without permission

## 22.3 Admin Routes

```txt id="f2tu0g"
/admin
/admin/users
/admin/users/[id]
/admin/roles
/admin/permissions
/admin/properties
/admin/projects
/admin/requirements
/admin/leads
/admin/site-visits
/admin/messages
/admin/advertisements
/admin/subscriptions
/admin/payments
/admin/verification
/admin/reports
/admin/support
/admin/cms
/admin/blogs
/admin/seo
/admin/settings
/admin/audit-logs
/admin/fraud
/admin/system-health
```

---

# 23. SUPER ADMIN ROLE MATRIX

Super Admin controls everything.

## 23.1 Super Admin Can

Super Admin can:

* Manage all users
* Manage roles
* Manage permissions
* Manage admins
* Manage staff
* Manage platform settings
* Manage feature flags
* Manage providers
* Manage subscriptions
* Manage payments
* Manage pricing
* Manage banner ad pricing
* Manage cities/locations
* Manage SEO
* Manage CMS
* Manage verification settings
* Manage moderation settings
* View audit logs
* Manage system health
* Manage API/provider modes
* View database/storage/API usage if available
* Configure session timeout
* Configure maintenance mode
* Manage fraud settings
* Manage platform-wide access

## 23.2 Super Admin Restrictions

Even Super Admin must not:

* Expose secrets in client
* Fake payment success
* Fake provider send
* Bypass legal/safety rules
* Delete audit history without explicit safe process
* Publicly expose private documents
* Use service role in client

## 23.3 Super Admin Routes

```txt id="pe8b84"
/admin/super
/admin/super/settings
/admin/super/platform
/admin/super/brand
/admin/super/cities
/admin/super/locations
/admin/super/providers
/admin/super/feature-flags
/admin/super/roles
/admin/super/permissions
/admin/super/admins
/admin/super/subscriptions
/admin/super/payments
/admin/super/banner-ads
/admin/super/seo
/admin/super/cms
/admin/super/security
/admin/super/sessions
/admin/super/storage
/admin/super/api-usage
/admin/super/audit-logs
/admin/super/system-health
/admin/super/maintenance
```

---

# 24. PUBLIC PAGE MATRIX

Public pages:

```txt id="vdkuc4"
/                Homepage
/search          Search results
/properties/[slug]
/projects/[slug]
/city/[city-slug]
/city/[city-slug]/[property-type]
/locality/[city-slug]/[locality-slug]
/brokers
/brokers/[slug]
/agencies
/agencies/[slug]
/builders
/builders/[slug]
/requirements
/pricing
/blog
/blog/[slug]
/faq
/about
/contact
/privacy
/terms
/refund-policy
/listing-policy
/ad-policy
/support
/login
/register
```

Direct `/login` and `/register` may exist as fallback routes, but public UX should primarily use popup/modal.

Admin login must not be mixed into public login/register.

---

# 25. AUTH PAGE AND MODAL MATRIX

Auth surfaces:

| Surface               | Guest           | Logged-In                  | Admin                           |
| --------------------- | --------------- | -------------------------- | ------------------------------- |
| Header Login/Register | Show            | Hide                       | Not public                      |
| Login Popup           | Show            | Hide                       | Not for admin                   |
| Register Popup        | Show            | Hide                       | Not for admin                   |
| OTP Screen            | During auth     | Not needed                 | Separate admin auth if required |
| Role Selection        | During register | Role change request        | Staff/admin created separately  |
| Forgot/Email Flow     | If enabled      | Profile email verification | Admin separate                  |
| Profile Icon          | Hide            | Show                       | Show in admin                   |

Auth routes:

```txt id="yqnvtr"
/login
/register
/verify-otp
/profile
/profile/edit
/profile/security
/profile/verification
/profile/role-change
/profile/subscription
/profile/sessions
/account-suspended
/account-banned
/unauthorized
```

---

# 26. PROFILE ROUTE MATRIX

Common profile routes:

```txt id="h2rqbf"
/profile
/profile/edit
/profile/avatar
/profile/email-verification
/profile/phone
/profile/security
/profile/sessions
/profile/roles
/profile/role-change
/profile/verification
/profile/subscription
/profile/billing
/profile/notifications
/profile/privacy
/profile/settings
```

Role-specific profile sections:

* Buyer preference
* Tenant preference
* Owner details
* Broker business details
* Agency business details
* Agent assignment info
* Builder company details
* Staff/admin profile scope

---

# 27. LOCATION FEATURE MATRIX

Location features:

| Feature                  | Public            | User              | Admin                | Super Admin  |
| ------------------------ | ----------------- | ----------------- | -------------------- | ------------ |
| City selector            | View/use          | View/use/save     | Manage if permitted  | Full control |
| District/taluka          | Search/post       | Use in forms      | Manage               | Full control |
| Village/locality         | Search/post       | Request/add       | Approve/manage       | Full control |
| Missing location request | Submit if allowed | Submit            | Review               | Configure    |
| City SEO page            | View              | View              | Edit if permitted    | Configure    |
| City banner targeting    | View result       | Submit ad if role | Approve              | Configure    |
| Nearby city fallback     | View              | View              | Configure if allowed | Full control |

Location routes:

```txt id="7zl0kf"
/city/[city-slug]
/locality/[city-slug]/[locality-slug]
/admin/locations
/admin/locations/states
/admin/locations/districts
/admin/locations/talukas
/admin/locations/cities
/admin/locations/villages
/admin/locations/localities
/admin/locations/requests
```

---

# 28. PROPERTY FEATURE MATRIX

Property features:

| Feature          | Guest          | Buyer/Tenant         | Owner/Broker/Agency/Builder | Admin            |
| ---------------- | -------------- | -------------------- | --------------------------- | ---------------- |
| View property    | Yes public     | Yes                  | Yes                         | Yes              |
| Search           | Yes            | Yes                  | Yes                         | Yes              |
| Save             | Login required | Yes                  | Optional                    | N/A              |
| Contact          | Mode-based     | Mode-based           | Receive leads               | Monitor          |
| Post property    | Login/register | If role upgrade      | Yes if allowed              | Manage           |
| Edit property    | No             | No unless owner role | Own/assigned                | All if permitted |
| Approve property | No             | No                   | No                          | Yes              |
| Promote property | No             | No                   | If plan allows              | Manage           |
| Archive property | No             | No                   | Own/assigned                | Manage           |

Property routes:

```txt id="ygo3vu"
/properties/[slug]
/dashboard/owner/properties
/dashboard/broker/listings
/dashboard/agency/listings
/admin/properties
/admin/properties/pending
/admin/properties/reported
```

---

# 29. PROJECT FEATURE MATRIX

Project features:

| Feature         | Guest      | Buyer/Tenant | Builder        | Admin   |
| --------------- | ---------- | ------------ | -------------- | ------- |
| View project    | Yes        | Yes          | Yes            | Yes     |
| Search project  | Yes        | Yes          | Yes            | Yes     |
| Contact project | Mode-based | Mode-based   | Receive leads  | Monitor |
| Create project  | No         | No           | Yes            | Yes     |
| Edit project    | No         | No           | Own projects   | Yes     |
| Manage units    | No         | No           | Yes            | Yes     |
| Approve project | No         | No           | No             | Yes     |
| Promote project | No         | No           | If plan allows | Manage  |

Project routes:

```txt id="0plcyr"
/projects/[slug]
/dashboard/builder/projects
/dashboard/builder/projects/new
/dashboard/builder/projects/[id]
/admin/projects
/admin/projects/pending
```

---

# 30. REQUIREMENT FEATURE MATRIX

Requirement features:

| Feature                  | Guest          | Buyer/Tenant   | Broker/Agency/Builder         | Admin   |
| ------------------------ | -------------- | -------------- | ----------------------------- | ------- |
| View public requirements | If allowed     | Yes own/public | Plan/permission based         | Yes     |
| Post requirement         | Login required | Yes            | Only buyer role if allowed    | Manage  |
| Edit requirement         | No             | Own            | No                            | Yes     |
| View requirement feed    | No             | Own            | Plan/permission based         | Yes     |
| Send proposal            | No             | No             | Yes if allowed                | Monitor |
| Respond to proposal      | No             | Own            | Proposal sender sees response | Yes     |
| Approve requirement      | No             | No             | No                            | Yes     |

Requirement routes:

```txt id="gyq3k0"
/requirements
/requirements/[id]
/dashboard/buyer/requirements
/dashboard/tenant/requirements
/dashboard/broker/requirements
/dashboard/agency/requirements
/admin/requirements
/admin/requirements/pending
```

---

# 31. PROPOSAL FEATURE MATRIX

Proposal features:

| Feature               | Buyer/Tenant   | Broker/Agency/Builder          | Admin             |
| --------------------- | -------------- | ------------------------------ | ----------------- |
| Receive proposal      | Yes            | No                             | View if permitted |
| Send proposal         | No             | Yes                            | Monitor           |
| Edit proposal         | No             | Own before response if allowed | Manage            |
| Accept/respond        | Yes            | View response                  | Monitor           |
| Reject/close          | Yes            | View status                    | Monitor           |
| Message from proposal | If implemented | If implemented                 | Permission-based  |

Proposal routes:

```txt id="b937mg"
/dashboard/buyer/requirements/[id]/proposals
/dashboard/tenant/requirements/[id]/proposals
/dashboard/broker/proposals
/dashboard/agency/proposals
/dashboard/builder/proposals
/admin/proposals
```

---

# 32. LEAD FEATURE MATRIX

Lead sources:

* Phone view
* WhatsApp click
* Lead form
* Contact request
* Site visit
* Proposal
* Brochure download
* Banner ad click if connected
* Project enquiry
* Requirement response

Lead access:

| Role         | Lead Access                      |
| ------------ | -------------------------------- |
| Buyer/Tenant | Own submitted enquiries if shown |
| Owner        | Leads for own properties         |
| Broker       | Leads for own listings/proposals |
| Agency Owner | Agency leads                     |
| Agent        | Assigned leads only              |
| Builder      | Project leads                    |
| Admin        | Permission-based                 |
| Super Admin  | Full                             |

Lead routes:

```txt id="b8wnv2"
/dashboard/owner/leads
/dashboard/broker/leads
/dashboard/agency/leads
/dashboard/agent/leads
/dashboard/builder/leads
/admin/leads
```

Lead UI must show alternate number if used.

---

# 33. SITE VISIT FEATURE MATRIX

Site visit access:

| Role         | Can Do                                       |
| ------------ | -------------------------------------------- |
| Buyer/Tenant | Request, view, reschedule/cancel if allowed  |
| Owner        | Approve/reject/reschedule own listing visits |
| Broker       | Manage own listing visits                    |
| Agency       | Assign/manage agency visits                  |
| Agent        | Manage assigned visits                       |
| Builder      | Manage project visits                        |
| Admin        | Monitor/manage if permitted                  |

Routes:

```txt id="2v2xm2"
/dashboard/buyer/site-visits
/dashboard/tenant/site-visits
/dashboard/owner/site-visits
/dashboard/broker/site-visits
/dashboard/agency/site-visits
/dashboard/agent/site-visits
/dashboard/builder/site-visits
/admin/site-visits
```

Site visit must not handle property token or booking money.

---

# 34. MESSAGING FEATURE MATRIX

Messaging if implemented:

| Role         | Access                               |
| ------------ | ------------------------------------ |
| Buyer/Tenant | Own conversations                    |
| Owner        | Conversations linked to own listings |
| Broker       | Own conversations                    |
| Agency Owner | Agency conversations                 |
| Agent        | Assigned conversations               |
| Builder      | Project conversations                |
| Admin        | Policy-based only                    |
| Super Admin  | Policy-based, audit-logged           |

Routes:

```txt id="egqgab"
/dashboard/messages
/dashboard/buyer/messages
/dashboard/tenant/messages
/dashboard/owner/messages
/dashboard/broker/messages
/dashboard/agency/messages
/dashboard/agent/messages
/dashboard/builder/messages
/admin/messages
```

If messaging is not implemented, hide it.

Do not show fake unread counts.

---

# 35. BANNER ADS FEATURE MATRIX

Banner ads are paid and approval-based.

Eligible roles:

* Agency Owner
* Real Estate Group
* Builder if enabled
* Broker if enabled
* Developer if enabled

Guest/user sees approved active ads only.

## 35.1 Banner Ad User Flow

1. Eligible user opens dashboard.
2. User opens Banner Ads.
3. User selects plan/placement/city/duration.
4. User uploads desktop/tablet/mobile images.
5. System shows size/ratio requirements.
6. User pays or uses eligible credit/plan.
7. Ad is submitted.
8. Admin reviews.
9. Admin approves/rejects.
10. Approved ad becomes active by schedule.
11. City-priority carousel displays it.
12. System notifies before expiry.
13. Ad expires.
14. Ad auto-hides.
15. Ad archives.
16. User can renew if allowed.

## 35.2 Banner Ad Routes

User routes:

```txt id="qf7zb0"
/dashboard/agency/banner-ads
/dashboard/agency/banner-ads/new
/dashboard/agency/banner-ads/[id]
/dashboard/broker/banner-ads
/dashboard/builder/banner-ads
/dashboard/real-estate-group/banner-ads
```

Admin routes:

```txt id="xvqsh5"
/admin/advertisements/banner-ads
/admin/advertisements/banner-ads/pending
/admin/advertisements/banner-ads/active
/admin/advertisements/banner-ads/expired
/admin/advertisements/banner-ads/[id]
/admin/advertisements/pricing
```

Super Admin routes:

```txt id="sxui5w"
/admin/super/banner-ads
/admin/super/banner-ads/settings
/admin/super/banner-ads/pricing
/admin/super/banner-ads/placements
```

No unpaid unapproved ad should appear.

No expired ad should appear.

No fake analytics.

---

# 36. SUBSCRIPTION FEATURE MATRIX

Subscription access:

| Role         | View Pricing             | Buy Plan                          | Manage Plan |
| ------------ | ------------------------ | --------------------------------- | ----------- |
| Guest        | Yes                      | Login required                    | No          |
| Buyer/Tenant | Yes                      | If enabled                        | Own         |
| Owner        | Yes                      | Owner plans                       | Own         |
| Broker       | Yes                      | Broker plans                      | Own         |
| Agency       | Yes                      | Agency plans                      | Own         |
| Builder      | Yes                      | Builder plans                     | Own         |
| Admin        | View/manage if permitted | Manual admin actions if permitted | Yes         |
| Super Admin  | Full                     | Full                              | Full        |

Routes:

```txt id="rj2tg4"
/pricing
/dashboard/subscription
/dashboard/billing
/dashboard/owner/subscription
/dashboard/broker/subscription
/dashboard/agency/subscription
/dashboard/builder/subscription
/admin/subscriptions
/admin/payments
/admin/super/subscriptions
/admin/super/payments
```

Payment must be server verified.

No fake plan activation.

---

# 37. PROVIDER MODE MATRIX

Provider modes controlled by Admin/Super Admin.

## WhatsApp

Modes:

* Disabled
* Free wa.me mode
* API mode

## Map

Modes:

* Disabled
* Embed/free/trial mode
* Premium Google Maps API mode

## OTP

Modes:

* Development OTP
* Production provider OTP
* Disabled/setup-required

## Email

Modes:

* Disabled
* Provider configured
* Setup-required

## Payment

Modes:

* Disabled
* Razorpay/provider configured
* Setup-required

Provider routes:

```txt id="5r2mm1"
/admin/super/providers
/admin/super/providers/whatsapp
/admin/super/providers/maps
/admin/super/providers/otp
/admin/super/providers/email
/admin/super/providers/payments
```

Provider missing = no fake success.

---

# 38. SEO FEATURE MATRIX

SEO pages:

```txt id="lcqc5b"
/city/[city-slug]
/city/[city-slug]/property-sale
/city/[city-slug]/flats
/city/[city-slug]/plots
/city/[city-slug]/commercial
/city/[city-slug]/rent
/locality/[city-slug]/[locality-slug]
/builders/[slug]
/brokers/[slug]
/agencies/[slug]
/projects/[slug]
/blog/[slug]
```

SEO admin routes:

```txt id="91fien"
/admin/seo
/admin/seo/city-pages
/admin/seo/locality-pages
/admin/seo/templates
/admin/seo/sitemap
/admin/seo/redirects
```

SEO pages must use real data.

Thin/empty pages should be noindex or safely handled.

---

# 39. CMS FEATURE MATRIX

CMS pages:

* About
* Contact
* FAQ
* Privacy
* Terms
* Refund Policy
* Listing Policy
* Ad Policy
* Blog
* Guides
* Help

Routes:

```txt id="9vg3se"
/about
/contact
/faq
/privacy
/terms
/refund-policy
/listing-policy
/ad-policy
/blog
/blog/[slug]
/help
/admin/cms
/admin/blogs
/admin/faq
```

CMS access:

* Guest: view public pages
* Content Manager: manage if permitted
* Admin: manage if permitted
* Super Admin: full

---

# 40. VERIFICATION FEATURE MATRIX

Verification applies to:

* User phone
* User email
* Broker verification
* Agency verification
* Builder verification
* Property verification
* Project verification
* Role upgrade verification
* Banner ad advertiser verification if required

Routes:

```txt id="xpqg33"
/profile/verification
/dashboard/broker/verification
/dashboard/agency/verification
/dashboard/builder/verification
/admin/verification
/admin/verification/brokers
/admin/verification/agencies
/admin/verification/builders
/admin/verification/properties
```

No fake verified badge.

---

# 41. FRAUD AND REPORT FEATURE MATRIX

Fraud/reporting applies to:

* Fake property
* Duplicate listing
* Broker pretending owner
* Wrong price
* Wrong location
* Expired listing
* Misleading banner ad
* Spam requirement
* Contact abuse
* Fake profile
* Payment abuse
* Message abuse

Routes:

```txt id="e2cwo2"
/properties/[slug]/report
/admin/reports
/admin/fraud
/admin/fraud/duplicates
/admin/fraud/fake-listings
/admin/fraud/contact-abuse
/admin/fraud/banner-ads
```

Fraud score must not be fake.

If automated fraud is not implemented, use manual report queue only.

---

# 42. NOTIFICATION FEATURE MATRIX

Notification channels:

* In-app
* Email if configured
* WhatsApp if configured
* SMS if configured
* Push if implemented

Notification triggers:

* OTP
* Login/security
* Role approval/rejection
* Property approval/rejection
* Requirement approval/rejection
* Proposal received
* Lead received
* Site visit requested
* Site visit updated
* Subscription expiry
* Payment status
* Banner ad approval/rejection
* Banner ad expiry
* Verification status
* Support reply

Routes:

```txt id="xeeluw"
/notifications
/dashboard/notifications
/admin/notifications
/admin/super/notifications
```

Do not fake sent status.

---

# 43. MODAL, DRAWER AND BOTTOM SHEET MATRIX

Common modals/drawers:

| UI Surface          | Used For                | Mobile Behavior             |
| ------------------- | ----------------------- | --------------------------- |
| Login popup         | Login/register          | Bottom sheet or full screen |
| OTP popup           | OTP verification        | Full screen/step            |
| Role selection      | Register/role change    | Card selection              |
| City selector       | City selection          | Searchable sheet            |
| Search overlay      | Mobile search           | Full screen                 |
| Filter bottom sheet | Filters                 | Bottom sheet                |
| Contact popup       | Lead form               | Bottom sheet                |
| Site visit popup    | Visit booking           | Bottom sheet                |
| Image crop modal    | Avatar/logo/banner crop | Full screen on mobile       |
| Payment modal       | Payment flow            | Provider-safe               |
| Admin drawer        | Review details          | Full screen on mobile       |
| Confirm modal       | Delete/archive/reject   | Center/sheet                |

All must close on outside click/tap where safe.

---

# 44. PERMISSION NAMING EXAMPLES

Permission examples:

```txt id="kq7o26"
property.view.public
property.create
property.update.own
property.update.assigned
property.approve
property.reject
property.archive

project.create
project.update.own
project.approve

requirement.create
requirement.update.own
requirement.view.broker
requirement.approve

proposal.create
proposal.view.own
proposal.respond

lead.view.own
lead.view.assigned
lead.assign
lead.update.status

site_visit.create
site_visit.approve
site_visit.reschedule

message.view.own
message.send

banner_ad.create
banner_ad.pay
banner_ad.submit
banner_ad.approve
banner_ad.reject
banner_ad.archive
banner_ad.manage.pricing

subscription.view
subscription.purchase
subscription.manage.own
subscription.manage.admin

payment.create_order
payment.verify
payment.refund

seo.manage
cms.manage
user.view
user.manage
role.manage
permission.manage
settings.manage
provider.manage
audit.view
admin.access
super_admin.access
```

Actual permissions should be finalized in database/security document.

---

# 45. FEATURE FLAG EXAMPLES

Feature flags may include:

```txt id="bjhdt9"
auth.phone_otp.enabled
auth.dev_otp.enabled
auth.email_login.enabled
auth.google_login.enabled

search.autocomplete.enabled
search.map.enabled
search.save_search.enabled

property.posting.enabled
property.approval_required
property.contact_reveal.enabled

requirements.enabled
requirements.approval_required
requirements.public_view.enabled

proposals.enabled
site_visits.enabled
messaging.enabled

subscriptions.enabled
payments.enabled
credits.enabled
boosts.enabled

banner_ads.enabled
banner_ads.city_targeting.enabled
banner_ads.require_payment
banner_ads.require_approval

whatsapp.enabled
whatsapp.mode
maps.enabled
maps.mode

seo.city_pages.enabled
seo.locality_pages.enabled

cms.enabled
blog.enabled
support.enabled

verification.enabled
fraud_reports.enabled

admin.mobile_enabled
maintenance_mode.enabled
```

If a feature flag is off:

* Hide UI
* Block server action
* Avoid dead links
* Show safe disabled state if needed

---

# 46. DATABASE MODULE MATRIX

Major database modules:

* Auth / Identity
* Roles / Permissions
* Locations
* Properties
* Projects
* Requirements
* Proposals
* Leads
* Site Visits
* Messaging
* Notifications
* Subscriptions
* Payments
* Credits
* Boosts
* Banner Ads
* CMS
* SEO
* Verification
* Fraud Reports
* Support
* Audit Logs
* Settings
* Feature Flags
* Provider Config

Detailed schema belongs in database document.

This matrix only ensures feature coverage.

---

# 47. STORAGE MODULE MATRIX

Storage areas:

* Profile avatars
* Broker logos/photos
* Agency logos
* Builder logos
* Property images
* Project images
* Floor plans
* Brochures
* Banner ad images
* Blog/CMS images
* Verification documents
* Support attachments
* Message attachments if implemented

Every upload feature must show size/ratio/file rules.

Private files must not be public.

---

# 48. ROUTE VISIBILITY RULE

Do not show unimplemented routes in navigation.

If a route does not exist:

* Do not show menu item
* Or mark as disabled/future only in admin/dev context

No `href="#"`.

No empty click handlers.

No dead menu items.

No fake pages.

---

# 49. MOBILE BEHAVIOR RULE BY FEATURE

Mobile behavior requirements:

| Feature             | Mobile Rule                     |
| ------------------- | ------------------------------- |
| Public homepage     | Search-first                    |
| Header              | Compact, no-wrap                |
| Sidebar             | Drawer/sheet, outside tap close |
| Login/register      | Popup/bottom sheet/full screen  |
| OTP                 | Large numeric input             |
| Search filters      | Bottom sheet                    |
| Search results      | Full-width cards                |
| Property detail     | Sticky bottom CTA               |
| Property posting    | Step form                       |
| Requirement posting | Step form                       |
| Dashboards          | Cards not tables                |
| Admin queues        | Cards/drawers                   |
| Banner ads          | Card list + upload steps        |
| Pricing             | Role tabs/cards                 |
| Profile             | Section cards                   |
| Media upload        | Crop/preview                    |
| Site visits         | Status cards                    |
| Leads               | Lead cards                      |
| Messages            | Chat-like mobile UI             |

---

# 50. NO-FAKE UI MATRIX

If not implemented:

| Feature Type               | Correct Behavior              |
| -------------------------- | ----------------------------- |
| Provider missing           | Hide/disable/setup-required   |
| Payment missing            | No fake payment               |
| Search data missing        | Empty state                   |
| Map API missing            | Embed/disabled/setup-required |
| WhatsApp API missing       | wa.me if selected or disabled |
| Email missing              | No fake email sent            |
| SMS missing                | No fake SMS sent              |
| Analytics missing          | Hide analytics                |
| Banner metrics missing     | Hide metrics                  |
| Verification missing       | No badge                      |
| Match score missing        | Hide score                    |
| Admin setting disconnected | Do not show setting           |

---

# 51. IMPLEMENTATION PHASE CONNECTION

This matrix connects to Claude prompt phases.

Typical phase order:

```txt id="cip0y3"
D0 Project Discovery
D1 Design System
D2 Public Homepage/Header/Search
D3 Auth/Role/Profile
D4 Location/Property Posting/Media
D5 Property Search/Detail/Contact
D6 Requirements/Proposals/Leads/Site Visits
D7 Role Dashboards
D8 Admin/Super Admin
D9 Banner Ads
D10 Subscriptions/Payments
D11 SEO/CMS
D12 Providers
D13 Database/RBAC/RLS
D14 Manual Verification
D15 Production Cleanup
```

Every phase must update feature registry.

---

# 52. FINAL MATRIX ACCEPTANCE RULE

This matrix is satisfied only if:

* Every role has defined capabilities.
* Every major feature has routes.
* Every feature has role access.
* Every protected feature has permission.
* Every dashboard is role-specific.
* Every public feature has guest behavior.
* Every provider-based feature has missing-provider behavior.
* Every paid feature has subscription/payment rule.
* Every admin feature has permission rule.
* Every mobile feature avoids desktop table overflow.
* Every unimplemented feature is hidden/disabled/future.
* No fake UI is shown.
* Feature registry tracks visible features.

---

# 53. END OF FILE

This file defines the feature, page, role, route, dashboard, modal and permission matrix for My Gujarat Property.

Claude must use this file before creating or changing any feature, route, dashboard, modal or permission-controlled UI.

Nothing from uploaded docs or user chat instructions should be skipped.
