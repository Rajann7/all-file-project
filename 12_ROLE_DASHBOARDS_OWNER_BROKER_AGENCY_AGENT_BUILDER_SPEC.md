# MY GUJARAT PROPERTY

# ROLE-BASED DASHBOARDS — OWNER, BROKER, AGENCY, AGENT, BUILDER & USER DASHBOARD SPEC

## FILE NAME

`12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete role-based dashboard experience for **My Gujarat Property**.

This file must be read before building or redesigning:

* Buyer dashboard
* Tenant dashboard
* Owner dashboard
* Broker dashboard
* Agency Owner dashboard
* Agency Agent dashboard
* Builder dashboard
* Developer dashboard if enabled
* Real Estate Group dashboard if enabled
* Dashboard header
* Dashboard sidebar
* Dashboard mobile navigation
* Role-based dashboard cards
* Listing management
* Lead management
* Requirement feed
* Proposal management
* Site visit management
* Message dashboard
* Notification dashboard
* Subscription usage
* Banner ad management entry
* Team/agent assignment
* Profile completion cards
* Verification cards
* Dashboard empty/loading/error states
* Mobile dashboard table-to-card behavior
* No-fake dashboard metrics

The goal is to ensure every role sees only the correct dashboard, correct data, correct actions and correct permissions.

---

# 2. CORE DASHBOARD PRINCIPLE

Every role must have a dashboard that answers:

```txt id="1nq7kl"
What needs my attention today?
```

A dashboard should not be only a menu page.

It should show:

* Important status
* Pending work
* Leads
* Listings
* Proposals
* Requirements
* Site visits
* Plan usage
* Profile/verification status
* Notifications
* Quick actions
* Expiry warnings
* Admin-required tasks
* Real data only

Do not show fake numbers.

Do not show empty fake charts.

Do not show dashboard cards that do nothing.

---

# 3. ROLE-BASED DASHBOARD RULE

Dashboard must change according to active role.

Active role controls:

* Dashboard route
* Sidebar items
* Mobile bottom nav
* Header actions
* Data scope
* Quick actions
* Cards
* Tables
* Permissions
* Subscription/plan
* Notification filters
* Empty states

A buyer dashboard must not show broker tools.

A broker dashboard must not show agency billing unless broker has agency role.

An agent dashboard must not show all agency leads unless assigned/permissioned.

A builder dashboard must focus on projects/units/leads.

Admin dashboard is separate and covered in admin document.

---

# 4. DASHBOARD ROUTE MAP

Recommended dashboard routes:

## Demand Roles

```txt id="kh4czh"
/dashboard/buyer
/dashboard/tenant
```

## Supply Roles

```txt id="zsr45f"
/dashboard/owner
/dashboard/broker
/dashboard/agency
/dashboard/agent
/dashboard/builder
/dashboard/developer
/dashboard/real-estate-group
```

## Shared Dashboard Areas

```txt id="7jtdhf"
/dashboard/profile
/dashboard/notifications
/dashboard/messages
/dashboard/subscription
/dashboard/billing
/dashboard/settings
/dashboard/support
```

## Admin

```txt id="83b6wg"
/admin
/admin/super
```

Only show implemented routes.

No dead dashboard links.

---

# 5. DASHBOARD SHELL

Every role dashboard should share a consistent shell.

Dashboard shell includes:

* Dashboard header
* Role-aware sidebar
* Mobile role bottom nav
* Main content area
* Breadcrumb/back link where needed
* Notification area
* Toast system
* Modal/drawer provider
* Loading states
* Permission guard
* Role guard
* Subscription/plan guard where needed

Dashboard shell must be white-first, clean and mobile-friendly.

---

# 6. DASHBOARD HEADER

Dashboard header should show:

* Logo or dashboard brand
* Active role
* Business/profile identity
* Search if useful
* Notifications icon if implemented
* Messages icon if implemented
* Profile/avatar menu
* Role switcher if multiple roles
* Quick action button based on role

Examples:

Owner quick action:

```txt id="w8bnmy"
Post Property
```

Broker quick action:

```txt id="exu4ex"
Add Listing
```

Agency quick action:

```txt id="ub1z02"
Add Listing / Add Agent
```

Builder quick action:

```txt id="kyye5k"
Add Project
```

Buyer quick action:

```txt id="i31axi"
Post Requirement
```

Do not show irrelevant quick action.

---

# 7. DASHBOARD SIDEBAR RULE

Sidebar must be role-based.

Desktop:

* Sidebar visible.
* Clear active item.
* Grouped sections.
* Collapsible if needed.

Mobile:

* Sidebar becomes drawer.
* Outside tap closes.
* Back icon/close icon.
* No horizontal scroll.
* Role-based bottom nav may be used.

Do not show all roles’ items in one sidebar.

Do not show admin items to normal users.

---

# 8. DASHBOARD MOBILE RULE

Dashboard mobile must use cards instead of wide tables.

Every table should transform into cards on mobile.

Examples:

Lead table → lead cards.

Property table → property cards.

Site visit table → visit cards.

Subscription usage table → usage cards.

Agent table → agent cards.

Mobile dashboard must have:

* Sticky header if useful
* Bottom nav or drawer
* Large touch targets
* Clear cards
* Filter bottom sheet
* No horizontal scroll
* No tiny actions
* No broken tables
* Back icon on nested pages

---

# 9. DASHBOARD NO-FAKE METRICS RULE

Dashboard metrics must be real.

Allowed if real:

```txt id="vvsl18"
12 active listings
5 new leads
3 site visits pending
```

Not allowed:

```txt id="mzi5pb"
1,000+ views
99% conversion
Top broker
```

unless backed by real tracked data.

If analytics not implemented:

* Hide analytics card.
* Show simple operational cards.
* Do not fake charts.

---

# 10. COMMON DASHBOARD CARDS

Common cards across roles:

* Profile completion
* Verification status
* Plan/subscription status
* Quick actions
* Notifications
* Recent activity
* Expiring items
* Support/help
* Empty onboarding checklist

Role-specific cards should appear only when relevant.

---

# 11. BUYER DASHBOARD OVERVIEW

Buyer dashboard helps buyer manage discovery.

## 11.1 Buyer Dashboard Cards

Buyer dashboard may show:

* Saved properties
* Saved searches
* Active requirements
* New proposals
* Shortlisted proposals
* Upcoming site visits
* Recent enquiries
* Messages
* Notifications
* Profile completion
* Recommended search actions

## 11.2 Buyer Quick Actions

* Search Properties
* Post Requirement
* View Saved
* View Proposals
* Book Site Visit
* Complete Profile

## 11.3 Buyer Routes

```txt id="lajtnn"
/dashboard/buyer
/dashboard/buyer/saved-properties
/dashboard/buyer/saved-searches
/dashboard/buyer/requirements
/dashboard/buyer/requirements/new
/dashboard/buyer/requirements/[id]
/dashboard/buyer/proposals
/dashboard/buyer/site-visits
/dashboard/buyer/messages
/dashboard/buyer/notifications
/dashboard/buyer/profile
/dashboard/buyer/settings
```

Do not show business tools unless buyer has additional role.

---

# 12. TENANT DASHBOARD OVERVIEW

Tenant dashboard focuses on rent/PG needs.

## 12.1 Tenant Dashboard Cards

Tenant dashboard may show:

* Saved rentals
* Rental requirements
* PG/hostel requirements
* New proposals
* Upcoming visits
* Recent enquiries
* Messages
* Notifications
* Move-in preference
* Profile completion

## 12.2 Tenant Quick Actions

* Search Rentals
* Search PG/Hostel
* Post Rental Requirement
* View Proposals
* Book Visit

## 12.3 Tenant Routes

```txt id="b4lx07"
/dashboard/tenant
/dashboard/tenant/saved-rentals
/dashboard/tenant/requirements
/dashboard/tenant/requirements/new
/dashboard/tenant/proposals
/dashboard/tenant/site-visits
/dashboard/tenant/messages
/dashboard/tenant/notifications
/dashboard/tenant/profile
/dashboard/tenant/settings
```

---

# 13. OWNER DASHBOARD OVERVIEW

Owner dashboard is for individual property owners.

Owner should quickly see:

* My properties
* Listing approval status
* Leads
* Contact requests
* Site visits
* Expiring listings
* Plan usage
* Profile/verification
* Renew/upgrade actions

---

# 14. OWNER DASHBOARD CARDS

Owner dashboard cards:

* Active Properties
* Pending Approval
* Rejected / Need Changes
* Draft Listings
* New Leads
* Contact Requests
* Upcoming Site Visits
* Expiring Listings
* Sold/Rented Listings
* Plan Usage
* Profile Completion
* Verification Status
* Recent Activity

Only show cards with real data.

If no data, show onboarding card.

---

# 15. OWNER QUICK ACTIONS

Owner quick actions:

* Post Property
* View My Properties
* View Leads
* View Site Visits
* Renew Listing
* Upgrade Plan
* Complete Profile
* Submit Verification if required

---

# 16. OWNER SIDEBAR

Owner sidebar:

* Dashboard
* My Properties
* Add Property
* Leads
* Contact Requests
* Site Visits
* Messages if enabled
* Notifications
* Subscription / Plan
* Billing
* Profile
* Verification
* Support
* Settings

Hide messages if messaging disabled.

---

# 17. OWNER ROUTES

```txt id="dbe393"
/dashboard/owner
/dashboard/owner/properties
/dashboard/owner/properties/new
/dashboard/owner/properties/[id]
/dashboard/owner/properties/[id]/edit
/dashboard/owner/properties/[id]/leads
/dashboard/owner/properties/[id]/visits
/dashboard/owner/leads
/dashboard/owner/contact-requests
/dashboard/owner/site-visits
/dashboard/owner/messages
/dashboard/owner/notifications
/dashboard/owner/subscription
/dashboard/owner/billing
/dashboard/owner/profile
/dashboard/owner/verification
/dashboard/owner/support
/dashboard/owner/settings
```

---

# 18. OWNER PROPERTY MANAGEMENT

Owner property list should show:

* Property image
* Title
* Location
* Price/rent
* Status
* Approval status
* Leads count if real
* Expiry date
* Actions

Actions:

* View
* Edit
* Preview
* Submit
* Archive
* Mark Sold
* Mark Rented
* Renew
* View Leads
* View Visits

Mobile should show property cards.

No desktop table overflow.

---

# 19. OWNER LEADS

Owner lead dashboard should show:

* Lead name
* Phone used
* Alternate number badge if used
* Property
* Source
* Message
* Status
* Created date
* Call/WhatsApp action based on mode
* Notes if implemented
* Follow-up if implemented

Owner can update status if allowed.

Do not show fake leads.

---

# 20. BROKER DASHBOARD OVERVIEW

Broker dashboard is a professional business dashboard.

Broker should quickly see:

* Listings
* Leads
* Requirement feed
* Proposals
* Site visits
* Plan limits
* Expiring listings
* Verification status
* Lead pipeline
* Profile completion

---

# 21. BROKER DASHBOARD CARDS

Broker dashboard cards:

* Active Listings
* Pending Listings
* Draft Listings
* New Leads
* Requirement Matches
* Requirement Views Used
* Proposals Sent
* Proposal Responses
* Upcoming Site Visits
* Follow-ups
* Plan Usage
* Verification Status
* Expiring Listings
* Profile Completion
* Recent Activity

Do not show fake requirement matches.

If matching is not implemented, hide match count.

---

# 22. BROKER QUICK ACTIONS

Broker quick actions:

* Add Listing
* View Requirements
* Send Proposal
* View Leads
* Manage Pipeline
* Book/Manage Site Visit
* Upgrade Plan
* Complete Verification

---

# 23. BROKER SIDEBAR

Broker sidebar:

* Dashboard
* Listings
* Add Listing
* Requirements Feed
* Proposals
* Leads
* Lead Pipeline
* Site Visits
* Messages if enabled
* Notifications
* Analytics if real
* Subscription
* Billing
* Broker Profile
* Verification
* Support
* Settings

Hide analytics if not real.

---

# 24. BROKER ROUTES

```txt id="y0n6cw"
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
/dashboard/broker/support
/dashboard/broker/settings
```

---

# 25. BROKER REQUIREMENT FEED

Requirement feed should show buyer/tenant requirements the broker can access.

Access depends on:

* Broker role
* Active plan
* Requirement visibility
* City/operating area
* Verification if required
* Proposal limits

Feed card should show safe summary.

No buyer phone unless shared.

Actions:

* View Requirement
* Send Proposal
* Save Requirement if implemented
* Report Requirement
* Contact only if permitted

---

# 26. BROKER PROPOSALS

Proposal dashboard should show:

* Proposal title
* Requirement
* Attached listing
* Buyer/tenant status
* Proposal status
* Sent date
* Response
* Contact shared status
* Site visit status
* Actions

Actions:

* View
* Edit if allowed
* Follow up if allowed
* Archive
* Create lead if buyer responds

Do not show fake viewed/interested status.

---

# 27. BROKER LEAD PIPELINE

Lead pipeline may use kanban/list.

Stages:

* New
* Contacted
* Interested
* Follow-up
* Site Visit Scheduled
* Site Visit Done
* Converted
* Not Interested
* Closed

If kanban not implemented, use list/cards.

No fake conversion.

---

# 28. AGENCY DASHBOARD OVERVIEW

Agency dashboard is for agency owner/team management.

Agency dashboard should include:

* Agency profile status
* Listings
* Agents
* Leads
* Lead assignment
* Requirement feed
* Proposals
* Site visits
* Banner ads
* Subscription
* Verification
* Team activity if real

Agency dashboard must be more powerful than broker dashboard.

---

# 29. AGENCY DASHBOARD CARDS

Agency cards:

* Active Listings
* Pending Listings
* Total Agents
* Active Agents
* Unassigned Leads
* Assigned Leads
* New Leads
* Requirement Matches
* Proposals Sent
* Site Visits
* Banner Ads Active
* Banner Ads Pending
* Banner Ads Expiring
* Plan Usage
* Verification Status
* Profile Completion
* Billing Status

Only real metrics.

No fake team performance.

---

# 30. AGENCY QUICK ACTIONS

Agency quick actions:

* Add Listing
* Add Agent
* View Leads
* Assign Leads
* View Requirements
* Send Proposal
* Create Banner Ad
* Manage Subscription
* Complete Verification
* Edit Agency Profile

---

# 31. AGENCY SIDEBAR

Agency sidebar:

* Dashboard
* Agency Profile
* Agents
* Listings
* Add Listing
* Requirements Feed
* Proposals
* Leads
* Lead Pipeline
* Site Visits
* Messages if enabled
* Banner Ads
* Analytics if real
* Subscription
* Billing
* Verification
* Notifications
* Support
* Settings

Banner Ads must show if enabled and agency is eligible.

---

# 32. AGENCY ROUTES

```txt id="zy1edf"
/dashboard/agency
/dashboard/agency/profile
/dashboard/agency/agents
/dashboard/agency/agents/new
/dashboard/agency/agents/[id]
/dashboard/agency/listings
/dashboard/agency/listings/new
/dashboard/agency/listings/[id]
/dashboard/agency/listings/[id]/edit
/dashboard/agency/requirements
/dashboard/agency/requirements/[id]
/dashboard/agency/proposals
/dashboard/agency/leads
/dashboard/agency/lead-pipeline
/dashboard/agency/site-visits
/dashboard/agency/messages
/dashboard/agency/banner-ads
/dashboard/agency/banner-ads/new
/dashboard/agency/banner-ads/[id]
/dashboard/agency/analytics
/dashboard/agency/subscription
/dashboard/agency/billing
/dashboard/agency/verification
/dashboard/agency/notifications
/dashboard/agency/support
/dashboard/agency/settings
```

---

# 33. AGENCY AGENT MANAGEMENT

Agency Owner can manage agents.

Agent fields:

* Name
* Phone
* Email
* Avatar
* Role/title
* Status
* Assigned city/locality
* Assigned listings
* Assigned leads
* Permissions
* Created date

Agent statuses:

* Active
* Invited
* Pending
* Suspended
* Removed

Actions:

* Add agent
* Invite agent
* Edit permissions
* Assign listings
* Assign leads
* Deactivate
* Remove
* View activity if real

Do not fake agent activity.

---

# 34. AGENCY LEAD ASSIGNMENT

Agency lead management:

* New leads can be unassigned.
* Agency Owner can assign to agent.
* Agent sees assigned leads.
* Agency Owner can reassign.
* Assignment history can be logged.
* Agent cannot access unrelated leads.

Lead card must show:

* Assigned agent
* Alternate number badge if used
* Source
* Status
* Property/requirement
* Follow-up

---

# 35. AGENCY BANNER ADS ENTRY

Agency dashboard must include banner ads if feature enabled.

Agency can:

* View banner ads
* Create banner ad
* Upload images
* Select target city
* Pay/use plan
* Submit for approval
* View pending/active/expired status
* Renew
* See real analytics if implemented

Do not show banner ads to agency if feature disabled.

Do not show fake impressions/clicks.

Detailed banner ads rules are in banner ads document.

---

# 36. AGENT DASHBOARD OVERVIEW

Agent dashboard is assignment-scoped.

Agent should see only:

* Assigned leads
* Assigned listings if permitted
* Assigned site visits
* Assigned tasks
* Messages
* Notifications
* Profile

Agent must not see:

* Agency billing
* Subscription
* All agency leads unless permission
* Other agents’ private tasks
* Agency settings
* Banner ad billing

---

# 37. AGENT DASHBOARD CARDS

Agent cards:

* Assigned New Leads
* Follow-ups Today
* Upcoming Site Visits
* Assigned Listings
* Messages
* Tasks
* Notifications

No agency-wide metrics unless permission.

---

# 38. AGENT QUICK ACTIONS

Agent quick actions:

* View Assigned Leads
* Update Lead Status
* View Site Visits
* Add Follow-up Note
* Message Lead if enabled
* Update Profile

---

# 39. AGENT SIDEBAR

Agent sidebar:

* Dashboard
* Assigned Leads
* Assigned Listings
* Site Visits
* Tasks
* Messages
* Notifications
* Profile
* Settings

No subscription/billing unless explicit permission.

---

# 40. AGENT ROUTES

```txt id="vtxe3i"
/dashboard/agent
/dashboard/agent/leads
/dashboard/agent/leads/[id]
/dashboard/agent/listings
/dashboard/agent/site-visits
/dashboard/agent/tasks
/dashboard/agent/messages
/dashboard/agent/notifications
/dashboard/agent/profile
/dashboard/agent/settings
```

---

# 41. BUILDER DASHBOARD OVERVIEW

Builder dashboard focuses on projects, units and project leads.

Builder should quickly see:

* Projects
* Units
* Project leads
* Site visits
* Banner ads
* Subscription
* Verification
* Project approval status
* Project expiry/renewal
* Brochure/media status

---

# 42. BUILDER DASHBOARD CARDS

Builder cards:

* Active Projects
* Pending Projects
* Draft Projects
* Active Units
* New Project Leads
* Site Visits
* Brochure Downloads if tracked
* Banner Ads Active
* Banner Ads Pending
* Project Verification
* Plan Usage
* Subscription Expiry
* Profile Completion
* Recent Activity

Do not show fake project lead count.

---

# 43. BUILDER QUICK ACTIONS

Builder quick actions:

* Add Project
* Add Unit
* View Leads
* Manage Site Visits
* Create Banner Ad
* Upload Brochure
* Complete Verification
* Upgrade Plan

---

# 44. BUILDER SIDEBAR

Builder sidebar:

* Dashboard
* Builder Profile
* Projects
* Add Project
* Units
* Leads
* Site Visits
* Messages if enabled
* Banner Ads
* Analytics if real
* Subscription
* Billing
* Verification
* Notifications
* Support
* Settings

---

# 45. BUILDER ROUTES

```txt id="mdgy4l"
/dashboard/builder
/dashboard/builder/profile
/dashboard/builder/projects
/dashboard/builder/projects/new
/dashboard/builder/projects/[id]
/dashboard/builder/projects/[id]/edit
/dashboard/builder/projects/[id]/units
/dashboard/builder/projects/[id]/leads
/dashboard/builder/projects/[id]/visits
/dashboard/builder/units
/dashboard/builder/leads
/dashboard/builder/site-visits
/dashboard/builder/messages
/dashboard/builder/banner-ads
/dashboard/builder/banner-ads/new
/dashboard/builder/analytics
/dashboard/builder/subscription
/dashboard/builder/billing
/dashboard/builder/verification
/dashboard/builder/notifications
/dashboard/builder/support
/dashboard/builder/settings
```

---

# 46. BUILDER PROJECT MANAGEMENT

Project list should show:

* Project image
* Project name
* City/locality
* Status
* RERA if real
* Units count if real
* Leads count if real
* Approval status
* Expiry/plan status
* Actions

Actions:

* View
* Edit
* Add Unit
* Upload Media
* View Leads
* View Visits
* Submit for Approval
* Archive
* Renew
* Promote if allowed

---

# 47. BUILDER UNIT MANAGEMENT

Unit list should show:

* Unit type
* BHK
* Area
* Price
* Availability
* Tower/phase
* Floor plan
* Actions

Actions:

* Add unit
* Edit unit
* Mark sold/booked/available
* Upload floor plan
* Hide unit

Do not show fake inventory.

---

# 48. REAL ESTATE GROUP DASHBOARD

If Real Estate Group role is implemented, dashboard focuses on banner ads/promotions.

Cards:

* Active Banner Ads
* Pending Banner Ads
* Expiring Banner Ads
* Target Cities
* Plan/Payment Status
* Verification Status
* Profile Completion

Routes:

```txt id="q6esry"
/dashboard/real-estate-group
/dashboard/real-estate-group/profile
/dashboard/real-estate-group/banner-ads
/dashboard/real-estate-group/banner-ads/new
/dashboard/real-estate-group/subscription
/dashboard/real-estate-group/billing
/dashboard/real-estate-group/verification
/dashboard/real-estate-group/settings
```

If not separate, map this feature to Agency dashboard.

---

# 49. DEVELOPER DASHBOARD

Developer role can be mapped to Builder unless separated.

If separated, dashboard may include:

* Development projects
* Land/project pipeline
* Leads
* Banner ads
* Subscription
* Verification

If not implemented, hide Developer role/dashboard.

---

# 50. DASHBOARD SUBSCRIPTION USAGE

Role dashboards must show subscription usage if monetization enabled.

Examples:

Owner:

* Listings used
* Images limit
* Expiry date

Broker:

* Listings used
* Requirement views used
* Proposals sent
* Lead unlocks

Agency:

* Agents used
* Listings used
* Leads
* Banner ads
* Requirement views
* Proposals

Builder:

* Projects used
* Units used
* Leads
* Banner ads

If no plan system active:

* Show free/default state if real.
* Hide usage if not implemented.

No fake usage.

---

# 51. DASHBOARD VERIFICATION CARD

Business dashboards should show verification card.

States:

* Not submitted
* Pending
* Need more details
* Verified
* Rejected
* Expired
* Suspended

Card actions:

* Submit verification
* View status
* Resubmit
* View reason
* Contact support

Verified badge only if real.

---

# 52. DASHBOARD NOTIFICATIONS

Dashboard notifications may include:

* Listing approved/rejected
* Lead received
* Requirement received
* Proposal received
* Site visit requested
* Site visit confirmed
* Subscription expiring
* Banner ad approved/rejected
* Verification update
* Support reply
* Payment update

Do not fake external notification delivery.

---

# 53. DASHBOARD MESSAGE CENTER

If messaging enabled, dashboard can include messages.

Rules:

* Buyer/Tenant sees own conversations.
* Owner sees own property conversations.
* Broker sees own conversations.
* Agency owner sees agency conversations if allowed.
* Agent sees assigned conversations.
* Builder sees project conversations.
* Admin access is permission-based.

If messaging disabled, hide message UI.

---

# 54. DASHBOARD SUPPORT

Dashboard support should allow:

* Create support ticket
* View support tickets
* Reply
* Attach file if enabled
* Track status

Ticket statuses:

* Open
* In Progress
* Waiting for User
* Resolved
* Closed

If support not implemented, show contact/help page.

---

# 55. DASHBOARD SETTINGS

Role dashboard settings may include:

* Profile settings
* Notification preferences
* Contact preferences
* Privacy settings
* Team settings for agency
* Listing defaults
* Lead preferences
* Provider preferences if user-level
* Account/security

Super Admin/provider settings are separate.

Do not show provider secrets in user dashboard.

---

# 56. DASHBOARD DATA SCOPING

Data must be scoped.

Owner:

* Own properties/leads/visits only.

Broker:

* Own listings/leads/proposals only.

Agency Owner:

* Agency data.

Agent:

* Assigned data only.

Builder:

* Own projects/leads only.

Buyer/Tenant:

* Own saved items, requirements, proposals, visits.

Server-side checks required.

RLS must enforce.

Do not rely only on UI.

---

# 57. DASHBOARD ACTION SECURITY

Every action must check:

* Authenticated user
* Active role
* Permission
* Ownership/assignment
* Plan/subscription
* Feature flag
* Entity status
* Account status
* Provider mode if needed

Examples:

Agent updating lead:

* Must be assigned to lead.
* Must have permission.
* Lead must be active.

Broker sending proposal:

* Must have broker role.
* Must have plan/limit.
* Requirement must be active/visible.

Agency creating banner ad:

* Must have agency role.
* Feature enabled.
* Plan/payment eligible.

---

# 58. DASHBOARD TABLE TO CARD RULE

Every dashboard table must be responsive.

Desktop:

* Table allowed.
* Filters and bulk actions allowed.

Mobile:

* Convert rows to cards.
* Show top important fields.
* Put actions in menu.
* Use filter bottom sheet.
* No horizontal scroll.
* No hidden important data.

Applies to:

* Properties
* Leads
* Requirements
* Proposals
* Site visits
* Agents
* Projects
* Units
* Banner ads
* Payments
* Subscriptions

---

# 59. DASHBOARD FILTERS

Dashboard lists should support filters.

Examples:

Properties:

* Status
* City
* Type
* Approval
* Expiry

Leads:

* Status
* Source
* Property
* Assigned agent
* Date

Requirements:

* City
* Type
* Budget
* Urgency

Site visits:

* Status
* Date
* Assigned agent

Banner ads:

* Status
* City
* Date
* Payment

Filters should be mobile-friendly.

---

# 60. DASHBOARD BULK ACTIONS

Bulk actions are optional.

If implemented:

* Desktop only or carefully mobile-adapted.
* Permission-checked.
* Confirm before destructive action.
* Audit logged where needed.

Examples:

* Archive multiple listings
* Assign multiple leads
* Mark notifications read
* Export selected leads if allowed

If not implemented, hide.

---

# 61. DASHBOARD EXPORT RULE

Export is optional and sensitive.

If implemented:

* Permission required.
* Role scope enforced.
* Export only allowed data.
* Mask phone/email if policy.
* Audit log export.
* Plan restriction if business decides.

Do not expose all leads to wrong role.

---

# 62. DASHBOARD ANALYTICS RULE

Analytics can include:

* Listing views
* Leads
* Contact clicks
* Proposal responses
* Site visits
* Banner ad impressions/clicks
* Conversion if tracked

But only show if real tracking exists.

If not implemented:

* Hide analytics.
* Show operational cards only.

No fake charts.

---

# 63. DASHBOARD LOADING STATES

Loading states:

* Dashboard summary loading
* Cards loading
* Table/list loading
* Filters loading
* Detail drawer loading
* Action submitting
* Uploading
* Saving
* Assigning
* Approving

Use skeleton cards/tables.

Do not show blank dashboard.

---

# 64. DASHBOARD EMPTY STATES

Empty states should guide user.

Owner no properties:

```txt id="074bwd"
You have not posted any property yet. Post your first property.
```

Broker no requirements:

```txt id="4am5l0"
No matching requirements found in your selected city.
```

Agency no agents:

```txt id="gp1fqy"
No agents added yet. Add your first agent to assign leads.
```

Builder no projects:

```txt id="sciibr"
You have not added any project yet. Add your first project.
```

No fake data.

---

# 65. DASHBOARD ERROR STATES

Error states:

* Failed to load dashboard
* Permission denied
* Subscription required
* Verification required
* Feature disabled
* Action failed
* Upload failed
* Assignment failed
* Lead not found
* Listing not found
* Provider missing

Show clear message and retry/support action.

Do not expose raw technical error.

---

# 66. DASHBOARD SUCCESS STATES

Success states:

* Listing added
* Listing updated
* Lead assigned
* Lead status updated
* Proposal sent
* Site visit confirmed
* Agent added
* Project added
* Banner ad submitted
* Profile updated
* Subscription updated
* Verification submitted

Show success only after server confirmation.

---

# 67. DASHBOARD NO-FAKE RULE

Do not fake:

* Leads
* Views
* Contact clicks
* Proposal counts
* Site visits
* Agent activity
* Banner ad impressions
* Payment status
* Subscription status
* Verification status
* Listing approval
* Analytics charts
* Revenue
* Conversion rate

If data tracking is not implemented, hide related UI.

---

# 68. DASHBOARD FEATURE FLAGS

Possible feature flags:

```txt id="cpslje"
dashboard.enabled
dashboard.buyer.enabled
dashboard.tenant.enabled
dashboard.owner.enabled
dashboard.broker.enabled
dashboard.agency.enabled
dashboard.agent.enabled
dashboard.builder.enabled
dashboard.real_estate_group.enabled
dashboard.analytics.enabled
dashboard.mobile_bottom_nav.enabled
dashboard.messages.enabled
dashboard.support.enabled
dashboard.exports.enabled
dashboard.bulk_actions.enabled
dashboard.lead_pipeline.enabled
dashboard.agent_assignment.enabled
dashboard.banner_ads_entry.enabled
```

If feature flag off, hide related UI and block routes/actions.

---

# 69. DASHBOARD COMPONENTS

Recommended components:

* DashboardShell
* DashboardHeader
* RoleSidebar
* MobileDashboardNav
* RoleSwitcher
* DashboardSummaryCards
* ProfileCompletionCard
* VerificationCard
* SubscriptionUsageCard
* QuickActionsCard
* RecentActivityCard
* PropertyManagementList
* LeadCard
* LeadPipeline
* RequirementFeed
* ProposalList
* SiteVisitList
* AgentManagementList
* ProjectManagementList
* UnitManagementList
* BannerAdsList
* DashboardEmptyState
* DashboardErrorState
* DashboardSkeleton
* MobileCardList
* FilterSheet
* ActionMenu
* ConfirmDialog

Avoid duplicate random dashboard components.

---

# 70. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Buyer dashboard shows buyer items only.
* Tenant dashboard shows tenant items only.
* Owner dashboard shows own properties/leads.
* Broker dashboard shows listings/requirements/proposals.
* Agency dashboard shows agents/leads/banner ads if enabled.
* Agent dashboard shows assigned items only.
* Builder dashboard shows projects/units/leads.
* Header changes by active role.
* Sidebar changes by active role.
* Role switch changes dashboard.
* Buyer cannot access broker dashboard.
* Agent cannot access agency billing.
* Owner cannot view broker requirement feed unless enabled.
* Agency lead assignment works.
* Builder project management works.
* Dashboard tables become cards on mobile.
* No horizontal scroll on mobile.
* Empty states are real.
* Metrics are real or hidden.
* No fake analytics.
* Subscription usage is real or hidden.
* Banner ads entry visible only to eligible roles.
* No screenshot/video capture required.

---

# 71. PASS / FAIL RULE

Dashboard phase is PASS only if:

* Dashboards are role-specific.
* Header/sidebar are role-aware.
* Mobile dashboard is card-based.
* Data is scoped correctly.
* Agent sees assigned data only.
* Agency owner can manage team if implemented.
* Builder has project/unit workflow.
* Broker has requirement/proposal workflow.
* Owner has property/lead workflow.
* Buyer/Tenant have requirement/saved/proposal workflow.
* No fake metrics.
* No fake leads.
* No fake analytics.
* Permission guards work.
* Feature registry updated.
* Manual verification completed.

If all roles share same generic dashboard, mark FAIL.

If agent can see all agency data without permission, mark FAIL.

If mobile dashboard uses broken wide tables, mark FAIL.

---

# 72. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for profile, auth, property, lead, requirement, admin, banner ads, subscription, database and manual verification details.

---

# 73. END OF FILE

This file defines role-based dashboards for buyer, tenant, owner, broker, agency, agent, builder and related business roles.

Dashboards must be role-aware, mobile-first, data-scoped, permission-protected, useful, no-fake and connected to listings, leads, requirements, proposals, site visits, subscriptions and banner ads.

Nothing from uploaded docs or user chat instructions should be skipped.
