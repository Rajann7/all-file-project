# MY GUJARAT PROPERTY

# BUYER/TENANT REQUIREMENT, PROPOSAL, LEADS, SITE VISIT & MESSAGING SPEC

## FILE NAME

`11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete buyer/tenant requirement marketplace, proposal system, lead system, site visit booking system and messaging system for **My Gujarat Property**.

This file must be read before building or redesigning:

* Post Requirement flow
* Buyer requirement dashboard
* Tenant requirement dashboard
* Requirement feed
* Broker requirement feed
* Agency requirement feed
* Builder requirement feed
* Owner requirement access if enabled
* Send proposal flow
* Proposal detail
* Proposal response
* Lead generation from requirement
* Contact request from requirement
* Call request
* WhatsApp request
* Site visit booking
* Site visit approval/rejection/reschedule
* Messaging threads
* Requirement notifications
* Proposal notifications
* Lead assignment
* Requirement moderation
* Requirement expiry
* Requirement search filters
* Requirement privacy
* Current number/alternate number rule inside requirement/contact
* Mobile requirement UX
* No-fake lead/proposal behavior

The goal is to make My Gujarat Property more powerful than a normal property listing website by allowing buyers and tenants to post their demand and allowing sellers/brokers/agencies/builders to respond with matching properties.

---

# 2. CORE REQUIREMENT MARKETPLACE IDEA

A buyer or tenant should be able to say:

```txt id="6pk0w3"
I want to buy/rent a property in this city/locality with this budget and these details.
```

Then relevant supply-side users should be able to see that requirement and send matching proposals.

Supply-side users include:

* Owner if enabled
* Broker
* Agency
* Builder
* Developer if implemented
* Real Estate Group if applicable

Example buyer requirement:

```txt id="x02emo"
I want to buy a 3 BHK flat in Rajkot, near Kalawad Road, budget ₹60L to ₹80L.
```

Example seller/broker response:

```txt id="lkwl4h"
I have a 3 BHK flat in Kalawad Road matching your requirement. Here are details, photos and proposal.
```

This feature creates a reverse marketplace.

---

# 3. REQUIREMENT MARKETPLACE PRINCIPLE

Requirement system must be:

* Buyer/tenant friendly
* Seller/broker/agency useful
* Privacy-safe
* Moderated if required
* Plan/permission controlled
* Spam protected
* Mobile-first
* Searchable
* Location-first
* Type-aware
* No-fake

Requirement should not expose private buyer contact unless user allows contact or lead flow is triggered.

Requirement should help serious sellers/brokers respond with relevant property.

---

# 4. REQUIREMENT USER TYPES

## Requirement Creators

Can create requirements:

* Buyer
* Tenant
* Investor if enabled
* Guest after login/register
* Owner/Broker/Agency/Builder only if they also have buyer/tenant role or multi-role support

## Requirement Responders

Can respond with proposals:

* Broker
* Agency
* Builder
* Developer if enabled
* Owner if enabled
* Admin if permitted for support/test

## Admin/Staff

Can manage/moderate:

* Admin
* Super Admin
* Moderator
* City Manager if scoped
* Support Executive if permitted

---

# 5. REQUIREMENT ACCESS RULE

Guest clicks Post Requirement:

1. Open login/register popup.
2. Preserve requirement intent.
3. Register/login.
4. Prefer Buyer/Tenant role.
5. Continue requirement posting.

Logged-in Buyer/Tenant:

* Can post requirement.

Logged-in Owner/Broker/Agency/Builder:

* If multi-role allowed, user may switch/request buyer role.
* If business allows business user to post personal requirement, use separate buyer intent.
* Do not mix broker identity into buyer requirement unless user chooses.

Admin:

* Can create/manage requirement if permission allows.

---

# 6. REQUIREMENT TYPES

Requirement types:

* Buy Residential
* Rent Residential
* Commercial Buy
* Commercial Rent/Lease
* Land / Plot Buy
* Agricultural Land Buy
* PG / Hostel
* Builder Project Interest
* Investment Requirement
* Other if enabled

Requirement type controls fields.

Do not use one generic requirement form for all types.

---

# 7. POST REQUIREMENT FLOW

Recommended flow:

```txt id="r6hqj9"
Step 1: Select requirement purpose
Step 2: Select property type
Step 3: Select city/location
Step 4: Add budget/rent
Step 5: Add property-specific preferences
Step 6: Add urgency/contact preference
Step 7: Privacy and visibility
Step 8: Preview
Step 9: Submit
Step 10: Approval if required
```

Mobile must be step-based.

Desktop can use sections/stepper.

---

# 8. REQUIREMENT PURPOSE SELECTION

First screen should ask:

```txt id="yhx0sp"
What are you looking for?
```

Options:

* Buy Property
* Rent Property
* Commercial Space
* Land / Plot
* PG / Hostel
* New Project
* Investment

Each option should have short description.

Example:

Buy Property:

```txt id="k9jyy2"
I want to buy a home, flat, house or plot.
```

Rent Property:

```txt id="u9fydy"
I want to rent a home, flat, room or PG.
```

Commercial Space:

```txt id="lb3qfr"
I need shop, office, showroom, warehouse or commercial space.
```

---

# 9. REQUIREMENT COMMON FIELDS

Common requirement fields:

* Requirement title
* Purpose
* Property category
* Property type
* City
* Preferred localities
* Budget/rent range
* Area range
* Area unit
* Timeline/urgency
* Contact preference
* Message/notes
* Visibility
* Privacy setting
* Status
* Expiry date
* User profile number
* Alternate number if used
* Email optional

Title can be auto-generated.

Example:

```txt id="naqylt"
Need 3 BHK Flat in Rajkot under ₹80 Lakh
```

---

# 10. BUY RESIDENTIAL REQUIREMENT FIELDS

Required:

* City
* Preferred localities
* Property type
* BHK
* Budget min/max
* Timeline
* Contact preference

Optional:

* Area range
* Furnishing preference
* Possession preference
* Floor preference
* Parking required
* Amenities
* Source preference: owner/broker/agency/builder
* Brokerage preference
* Loan/pre-approved status if implemented
* Notes

Example:

```txt id="ei6x2s"
Need 2 BHK flat in Rajkot, Kalawad Road or Mavdi, budget ₹50L to ₹65L, ready to move preferred.
```

---

# 11. RENT REQUIREMENT FIELDS

Required:

* City
* Preferred localities
* Property type
* BHK/room type
* Rent budget
* Move-in date
* Tenant type
* Contact preference

Optional:

* Deposit limit
* Furnishing
* Family/bachelor/company lease
* Pet allowed if needed
* Parking
* Food not applicable unless PG
* Preferred floor
* Notes

Example:

```txt id="psmvau"
Need 2 BHK rent in Rajkot for family, budget ₹15,000 to ₹20,000, semi-furnished preferred.
```

---

# 12. COMMERCIAL REQUIREMENT FIELDS

Required:

* City
* Preferred localities
* Commercial type
* Buy/rent/lease
* Budget/rent range
* Area range
* Business use
* Timeline

Optional:

* Frontage
* Road width
* Ground floor preference
* Parking
* Power load
* Washroom
* Main road
* Corner
* Nearby market
* Notes

Commercial types:

* Shop
* Office
* Showroom
* Warehouse
* Godown
* Industrial Shed
* Factory
* Co-working
* Clinic/Medical Space
* Restaurant/Cafe Space
* Commercial Land

Do not show BHK.

---

# 13. LAND / PLOT REQUIREMENT FIELDS

Required:

* District
* Taluka if relevant
* City/Village
* Land type
* Area range
* Area unit
* Budget
* Purpose
* Timeline

Optional:

* Road access
* Road width
* NA status
* Agriculture/non-agriculture
* Water
* Electricity
* Boundary
* Corner plot
* Nearby highway
* Survey/block preference
* Notes

Do not show BHK/furnishing.

---

# 14. AGRICULTURAL LAND REQUIREMENT FIELDS

Required:

* District
* Taluka
* Village/area
* Land area
* Area unit
* Budget
* Road access
* Timeline

Optional:

* Irrigation
* Borewell
* Electricity
* Soil type
* Crop preference
* Fencing
* Farmhouse requirement
* Water source
* Notes

---

# 15. PG / HOSTEL REQUIREMENT FIELDS

Required:

* City
* Locality
* Gender
* Sharing type
* Monthly budget
* Move-in date
* Food preference
* Contact preference

Optional:

* AC/non-AC
* Attached bathroom
* Wi-Fi
* Laundry
* Curfew preference
* Student/professional
* Minimum stay
* Notes

---

# 16. PROJECT / BUILDER REQUIREMENT FIELDS

Required:

* City
* Locality preference
* Unit type
* BHK
* Budget
* Possession timeline
* Project status preference

Optional:

* Builder preference
* RERA required
* Amenities
* Floor preference
* Payment plan preference
* Notes

Builder/agency can respond with project/unit proposals.

---

# 17. REQUIREMENT LOCATION RULE

Requirement location must use structured location.

Fields can include:

* State
* District
* Taluka
* City
* Village
* Locality
* Nearby area
* Flexible location
* Multiple preferred localities
* Radius if map supported

Examples:

Buyer can select:

```txt id="vvotmu"
Rajkot → Kalawad Road, Mavdi, Mota Mava
```

Land buyer can select:

```txt id="de0i3r"
Rajkot District → Gondal Taluka → nearby villages
```

If missing location:

* Allow request new location.
* Allow custom note.
* Admin can review.

---

# 18. REQUIREMENT PRIVACY RULE

Requirement privacy must protect buyer/tenant.

Visibility options:

* Private to approved responders
* Visible to brokers/agencies/builders only
* Public summary without contact
* Public if admin allows
* Hidden from public search
* Admin only
* Draft

Default should be privacy-safe.

Buyer contact should not be public unless user explicitly shares through lead/contact.

---

# 19. REQUIREMENT CONTACT PREFERENCE

Requirement creator can choose:

* Call request
* WhatsApp request
* Message first
* Proposal only
* Site visit after proposal
* Email optional
* Hide contact until accepted

Contact preference controls proposal/contact flow.

Do not expose phone if user chooses proposal/message first.

---

# 20. CURRENT NUMBER / ALTERNATE NUMBER RULE

This rule applies to requirement contact also.

When buyer/tenant posts requirement or responds to proposal:

Show option:

```txt id="cf5rtt"
Use my profile number
```

and:

```txt id="b3dltv"
Use a different number
```

If alternate number used:

* Store alternate number separately.
* Mark contact number as alternate.
* Do not overwrite profile number unless user confirms.
* Proposal sender/dashboard must clearly show “Alternate number used” if contact is shared.

This matches lead/contact rules from property detail.

---

# 21. REQUIREMENT STATUS

Requirement statuses:

```txt id="n0o5tf"
Draft
Pending Approval
Active
Paused
Matched
Closed
Expired
Rejected
Need Changes
Archived
Deleted
```

Public/responders should only see allowed statuses.

Draft/pending/rejected should not be visible to responders.

Expired requirements should not receive new proposals unless renewed.

---

# 22. REQUIREMENT EXPIRY

Requirements should have expiry.

Default expiry can be:

* 15 days
* 30 days
* 60 days
* Admin-configured

Before expiry:

* Notify user.
* Allow renew.
* Allow close.

After expiry:

* Hide from active requirement feed.
* Stop new proposals.
* Move to expired/archived state.
* Keep history in dashboard.

Do not show expired requirement as active.

---

# 23. REQUIREMENT MODERATION

Requirement approval may be required.

Moderation checks:

* Spam
* Fake requirement
* Offensive text
* Wrong category
* Unrealistic contact abuse
* Duplicate requirement
* Private data exposure
* Location validity

Admin can:

* Approve
* Reject
* Request changes
* Archive
* Mark spam
* Edit category/location if permitted
* Add note

User sees reason.

No fake approval.

---

# 24. REQUIREMENT FEED

Requirement feed shows active requirements to eligible responders.

Feed can be available to:

* Broker
* Agency
* Builder
* Developer if enabled
* Owner if enabled
* Admin

Feed visibility depends on:

* Role
* Plan
* Permission
* City/operating area
* Requirement privacy
* Requirement type
* Subscription limits
* Verification status if required

Do not show all requirements to everyone if privacy/plan restricts it.

---

# 25. REQUIREMENT FEED FILTERS

Requirement feed filters:

* City
* Locality
* District
* Taluka
* Village
* Requirement type
* Property type
* Budget
* BHK
* Area
* Urgency
* Posted date
* Contact preference
* New/unread
* Matching listing available
* Source: buyer/tenant/investor
* Status

Filter set must change by requirement type.

Land requirements should not show BHK.

---

# 26. REQUIREMENT CARD

Requirement card should show safe summary.

Fields:

* Requirement title
* City/locality
* Property type
* Budget/rent
* BHK/area if relevant
* Timeline/urgency
* Posted date
* Contact preference
* Match badge if real
* Proposal count if visible/real
* Send Proposal CTA
* Save/shortlist if implemented

Do not show buyer phone publicly.

Do not show fake proposal count.

---

# 27. REQUIREMENT DETAIL PAGE

Requirement detail page for eligible responders should show:

* Requirement summary
* Full preferences
* Location
* Budget
* Timeline
* Buyer contact preference
* Privacy-safe buyer info
* Send proposal button
* Matching own listings if implemented
* Existing proposal status
* Report requirement
* Admin moderation state if admin

Buyer’s private data stays hidden until allowed.

---

# 28. MATCHING LOGIC

Matching can be simple or advanced.

Initial simple matching:

* City match
* Locality match
* Property type match
* Budget overlap
* BHK match
* Purpose match
* Availability match

Advanced matching later:

* Area match
* Amenities match
* Timeline match
* Map radius
* User behavior
* AI match score

If match score is not implemented, do not show fake score.

---

# 29. PROPOSAL SYSTEM PURPOSE

Proposal allows a responder to offer a matching property/project to a requirement creator.

A proposal should answer:

* Which property are you offering?
* Why does it match?
* What is price/rent?
* Where is it located?
* Can buyer contact you?
* Can site visit be scheduled?

Proposal must be relevant.

Do not allow spam proposals.

---

# 30. SEND PROPOSAL FLOW

Responder flow:

```txt id="bs1jkr"
Open requirement
Click Send Proposal
Select existing listing/project/unit or create quick proposal
Add message
Add price/rent if needed
Add photos/details if allowed
Choose contact option
Submit proposal
Buyer/Tenant receives notification
```

If responder has no matching listing:

Options:

* Attach existing listing later
* Create quick proposal if allowed
* Create listing first
* Send message-only proposal if plan allows

Admin can control this.

---

# 31. PROPOSAL FIELDS

Proposal may include:

* Requirement ID
* Sender user/entity
* Attached property ID
* Attached project/unit ID
* Proposal title
* Message
* Offered price/rent
* Location summary
* Matching notes
* Availability
* Contact preference
* Photos if allowed
* Site visit option
* Expiry date
* Status

Proposal should not duplicate entire property unless needed.

---

# 32. PROPOSAL STATUS

Proposal statuses:

```txt id="kif9z6"
Draft
Sent
Viewed
Interested
Shortlisted
Rejected
Need More Details
Contact Shared
Site Visit Requested
Site Visit Scheduled
Closed
Expired
Archived
```

Status must be real.

Do not fake viewed/interested.

---

# 33. PROPOSAL RECEIVER UX

Buyer/Tenant dashboard should show proposals.

Proposal card should show:

* Property/project summary
* Sender type: Broker/Agency/Builder/Owner
* Price/rent
* Location
* Match details if real
* Message
* Contact CTA
* Site visit CTA
* Reject/shortlist
* Report if needed

Do not show fake verification.

---

# 34. PROPOSAL RESPONSE ACTIONS

Buyer/Tenant can:

* View proposal
* Shortlist
* Ask for more details
* Contact sender
* Share current/alternate number
* Book site visit
* Reject
* Report
* Close requirement if satisfied

Responder can:

* View status
* Follow up if allowed
* Update proposal if allowed
* Mark closed if buyer not interested

Contact privacy must be respected.

---

# 35. PROPOSAL LIMITS

Proposal limits may depend on plan.

Examples:

* Broker free plan: limited proposals/month
* Broker paid plan: more proposals
* Agency plan: team proposals
* Builder plan: project proposals
* Credit-based proposal unlock if implemented

System must check limits server-side.

Do not fake proposal limit usage.

---

# 36. LEAD CREATION FROM PROPOSAL

A lead can be created when:

* Buyer shows interest
* Buyer contacts sender
* Buyer shares number
* Buyer requests site visit
* Buyer asks for more details
* Buyer accepts proposal
* Sender requests call and buyer accepts

Lead source should be:

```txt id="fc9hwy"
requirement_proposal
```

Lead should include:

* Requirement ID
* Proposal ID
* Buyer user ID
* Sender entity
* Phone used
* Alternate number flag
* Message
* Status

---

# 37. CALL REQUEST FLOW

Call request is useful when contact is not directly shared.

Possible flow:

```txt id="8ni78d"
Responder sends proposal
Buyer clicks Request Call
Buyer chooses profile number or alternate number
System creates lead/call request
Responder sees call request
Responder contacts buyer
Status updates
```

Or:

```txt id="b5y2ho"
Responder requests call
Buyer accepts/rejects
If accepts, phone is shared according to chosen number
```

Admin should define allowed mode.

Do not expose buyer phone without consent.

---

# 38. WHATSAPP REQUEST FLOW

WhatsApp flow depends on provider mode.

Free wa.me mode:

* Open WhatsApp with safe prefilled message if number share allowed.

API mode:

* Send real WhatsApp message only if configured.

If contact not shared:

* Use platform message/proposal flow.

Do not fake WhatsApp send.

---

# 39. SITE VISIT SYSTEM PURPOSE

Site visit helps buyer/tenant schedule visit to property/project.

Site visit should connect:

* Property detail
* Project detail
* Requirement proposal
* Lead
* Buyer/Tenant dashboard
* Owner/Broker/Agency/Builder dashboard
* Agent assignment
* Notifications

Site visit must not handle property token/booking payment.

---

# 40. SITE VISIT REQUEST FLOW

Buyer/Tenant flow:

```txt id="wjsi30"
Open property/project/proposal
Click Book Site Visit
Select date
Select time slot
Choose profile number or alternate number
Add note
Submit request
Receiver approves/rejects/reschedules
User gets notification
```

If guest:

* Login/register first.
* Preserve intent.

If listing unavailable:

* Disable site visit.

---

# 41. SITE VISIT FIELDS

Site visit fields:

* Visit ID
* Property ID
* Project ID
* Proposal ID if from proposal
* Lead ID if linked
* Requested by user
* Receiver user/entity
* Assigned agent if any
* Requested date
* Requested time
* Confirmed date/time
* Phone used
* Alternate number flag
* Visit note
* Status
* Created date
* Updated date

---

# 42. SITE VISIT STATUS

Site visit statuses:

```txt id="x8r8bl"
Requested
Pending Confirmation
Confirmed
Rescheduled
Rejected
Cancelled by Buyer
Cancelled by Seller
Completed
No Show
Expired
Archived
```

Statuses must be real.

Do not show fake completed visits.

---

# 43. SITE VISIT RECEIVER ACTIONS

Owner/Broker/Agency/Builder can:

* View visit request
* Approve
* Reject
* Suggest new time
* Assign agent if agency
* Add note
* Mark completed
* Mark no-show
* Cancel with reason

Agent can manage only assigned visits.

Admin can monitor/manage if permitted.

---

# 44. SITE VISIT TIME SLOT RULE

Time slots may be:

* User requested custom time
* Receiver-defined availability
* Business hours
* Admin-configured slots

If availability system not implemented:

* Allow requested date/time and receiver confirmation.

Do not show fake available slots.

---

# 45. SITE VISIT NOTIFICATIONS

Notifications:

* Visit requested
* Visit confirmed
* Visit rescheduled
* Visit rejected
* Visit cancelled
* Visit reminder
* Visit completed
* No-show marked

Channels:

* In-app
* Email if configured
* WhatsApp if configured
* SMS if configured
* Push if implemented

No fake external notifications.

---

# 46. MESSAGING SYSTEM PURPOSE

Messaging allows safe communication without immediately exposing phone.

Messaging can connect:

* Property enquiry
* Requirement proposal
* Site visit
* Support
* Lead follow-up

Messaging is optional but useful.

If not implemented, hide message buttons.

---

# 47. MESSAGING PARTICIPANTS

Message participants may include:

* Buyer/Tenant
* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Support/Admin if support chat
* Moderator only if permission

Messaging should be scoped to:

* Property
* Project
* Requirement
* Proposal
* Lead
* Site visit

Do not create open spam messaging between all users unless moderated.

---

# 48. MESSAGE THREAD TYPES

Thread types:

* Property enquiry thread
* Project enquiry thread
* Requirement proposal thread
* Site visit thread
* Lead follow-up thread
* Support thread

Each thread should have context.

Example:

```txt id="2h36dd"
Thread: 3 BHK Flat in Rajkot
Participants: Buyer + Broker
```

---

# 49. MESSAGE PRIVACY RULE

Messages are private.

Users can see only their own threads.

Agency owner can see agency-related threads if policy allows.

Agent can see assigned threads only.

Admin can view only if policy/permission allows.

Do not expose messages publicly.

---

# 50. MESSAGE SAFETY RULE

Messaging should prevent abuse.

Possible safety features:

* Report message
* Block user if implemented
* Spam detection if implemented
* Rate limit messages
* Attachment limits
* Admin moderation for reported messages
* Phone/email masking if policy
* No offensive content if moderation enabled

Do not fake moderation.

---

# 51. MESSAGE ATTACHMENTS

Message attachments are optional.

If implemented:

* Use file validation.
* Store safely.
* Limit file size.
* Restrict dangerous file types.
* Use private storage.
* Allow images/PDF only if policy.
* Scan if available.
* Show upload progress.

If not implemented, hide attachment button.

---

# 52. LEAD PIPELINE

Leads from properties, requirements, proposals and site visits should be consistent.

Lead statuses:

* New
* Viewed
* Contacted
* Interested
* Follow-up
* Site Visit Requested
* Site Visit Scheduled
* Site Visit Done
* Converted
* Not Interested
* Invalid
* Duplicate
* Closed
* Archived

Business dashboards should use same lead pipeline.

Do not create separate inconsistent status systems.

---

# 53. BUYER REQUIREMENT DASHBOARD

Buyer dashboard should show:

* Active requirements
* Draft requirements
* Pending requirements
* Received proposals
* Shortlisted proposals
* Site visits
* Messages
* Closed/expired requirements
* Notifications
* Recommended actions

Buyer can:

* Edit requirement
* Pause requirement
* Close requirement
* Renew requirement
* View proposals
* Contact proposal sender
* Book site visit
* Report proposal

---

# 54. TENANT REQUIREMENT DASHBOARD

Tenant dashboard should show:

* Rental requirements
* PG requirements
* Proposals
* Site visits
* Saved rentals
* Messages
* Notifications
* Expired/closed requirements

Tenant can:

* Edit/close/renew requirement
* View proposals
* Book visits
* Contact sender

---

# 55. BROKER REQUIREMENT DASHBOARD

Broker dashboard should show:

* Requirement feed
* Matching requirements
* Saved requirements
* Proposals sent
* Proposal statuses
* Requirement leads
* Site visits
* Plan usage
* Proposal limit
* Notifications

Broker can:

* Filter requirements
* Send proposal
* Attach listing
* Contact if allowed
* Manage proposal follow-up
* View buyer response
* Book/schedule visit

---

# 56. AGENCY REQUIREMENT DASHBOARD

Agency dashboard should show:

* Requirement feed
* Team proposal activity
* Agency proposals
* Agent assignments
* Leads from requirements
* Site visits
* Matching listings
* Plan usage
* Notifications

Agency Owner can:

* Assign requirement/lead to agent
* Send proposal as agency
* Manage proposals
* View agent activity if real

Agent can:

* View assigned requirements/leads
* Send proposal only if permission
* Follow up assigned leads

---

# 57. BUILDER REQUIREMENT DASHBOARD

Builder dashboard should show:

* Project buyer requirements
* New project interest
* Unit matching requirements
* Proposals sent
* Project leads
* Site visits
* Plan usage
* Notifications

Builder can:

* Send proposal with project/unit
* Attach project brochure
* Schedule project visit
* Manage project lead pipeline

---

# 58. OWNER REQUIREMENT ACCESS

Owner requirement access is optional.

If enabled:

Owner can:

* View buyer requirements matching own property
* Send proposal with own property
* Receive lead if buyer interested

If disabled:

Owner cannot browse requirement feed.

Admin/Super Admin should control this.

Do not show requirement feed to owner if not enabled.

---

# 59. ADMIN REQUIREMENT MANAGEMENT

Admin can manage:

* Requirements
* Proposals
* Reports
* Spam
* Duplicate requirements
* Proposal abuse
* Site visits
* Messaging reports
* Lead disputes
* Visibility settings
* Feature flags
* Plan limits

Admin routes:

```txt id="ttvy4k"
/admin/requirements
/admin/requirements/pending
/admin/requirements/active
/admin/requirements/rejected
/admin/requirements/reported
/admin/proposals
/admin/leads
/admin/site-visits
/admin/messages
```

---

# 60. REQUIREMENT ROUTES

Public/user routes:

```txt id="l2xt44"
/requirements
/requirements/[id]
/dashboard/buyer/requirements
/dashboard/buyer/requirements/new
/dashboard/buyer/requirements/[id]
/dashboard/buyer/requirements/[id]/proposals
/dashboard/tenant/requirements
/dashboard/tenant/requirements/new
/dashboard/tenant/requirements/[id]
```

Responder routes:

```txt id="4kfaeu"
/dashboard/broker/requirements
/dashboard/broker/requirements/[id]
/dashboard/broker/proposals
/dashboard/agency/requirements
/dashboard/agency/requirements/[id]
/dashboard/agency/proposals
/dashboard/builder/requirements
/dashboard/builder/proposals
```

Site visit routes:

```txt id="3x4sr9"
/dashboard/buyer/site-visits
/dashboard/tenant/site-visits
/dashboard/owner/site-visits
/dashboard/broker/site-visits
/dashboard/agency/site-visits
/dashboard/agent/site-visits
/dashboard/builder/site-visits
```

Messaging routes:

```txt id="nw4sto"
/dashboard/messages
/dashboard/buyer/messages
/dashboard/tenant/messages
/dashboard/broker/messages
/dashboard/agency/messages
/dashboard/agent/messages
/dashboard/builder/messages
```

Only show implemented routes.

---

# 61. DATABASE MODULES

Possible tables:

* requirements
* requirement_locations
* requirement_preferences
* requirement_status_history
* requirement_reports
* proposals
* proposal_properties
* proposal_status_history
* leads
* lead_events
* lead_assignments
* lead_notes
* site_visits
* site_visit_status_history
* messages
* message_threads
* message_participants
* message_attachments
* notification_events

Detailed schema belongs to database document.

---

# 62. PERMISSIONS

Permission examples:

```txt id="brrdkv"
requirement.create
requirement.update.own
requirement.delete.own
requirement.close.own
requirement.renew.own
requirement.view.own
requirement.view.feed
requirement.view.public
requirement.approve
requirement.reject
requirement.report

proposal.create
proposal.view.own
proposal.view.received
proposal.update.own
proposal.respond
proposal.close
proposal.report

lead.create
lead.view.own
lead.view.assigned
lead.assign
lead.update.status
lead.add_note

site_visit.create
site_visit.view.own
site_visit.view.assigned
site_visit.approve
site_visit.reject
site_visit.reschedule
site_visit.cancel
site_visit.complete

message.create
message.view.thread
message.report
message.moderate
```

Permissions must be server-side.

---

# 63. FEATURE FLAGS

Possible feature flags:

```txt id="soes1w"
requirements.enabled
requirements.approval_required
requirements.public_view.enabled
requirements.buyer.enabled
requirements.tenant.enabled
requirements.commercial.enabled
requirements.land.enabled
requirements.pg.enabled
requirements.owner_access.enabled
requirements.feed.enabled
requirements.matching.enabled
requirements.expiry.enabled

proposals.enabled
proposals.attach_property.enabled
proposals.quick_proposal.enabled
proposals.plan_limits.enabled

leads.requirement_source.enabled
leads.alternate_number.enabled
leads.assignment.enabled
leads.pipeline.enabled

site_visits.enabled
site_visits.reschedule.enabled
site_visits.time_slots.enabled
site_visits.reminders.enabled

messaging.enabled
messaging.attachments.enabled
messaging.report.enabled
```

If feature flag is off, hide UI and block backend actions.

---

# 64. SUBSCRIPTION CONNECTION

Requirement feed and proposals may be monetized.

Possible plan controls:

* Requirement view limit
* Proposal send limit
* Lead unlock limit
* City feed access
* Contact reveal access
* Site visit management
* Agent/team access
* Requirement alerts
* Priority proposals

Examples:

Broker free plan:

* Limited requirement views
* Limited proposals

Agency paid plan:

* More requirement views
* Team assignment
* More proposals
* Lead pipeline

Builder plan:

* Project requirement access
* Project proposal limit

Do not fake plan usage.

---

# 65. NOTIFICATION CONNECTION

Requirement notification triggers:

* Requirement submitted
* Requirement approved
* Requirement rejected
* Requirement expiring
* Requirement expired
* New proposal received
* Proposal viewed
* Proposal shortlisted
* Proposal rejected
* Contact shared
* Site visit requested
* Site visit confirmed
* Message received
* Lead assigned

Channels:

* In-app
* Email if configured
* WhatsApp if configured
* SMS if configured
* Push if implemented

No fake external notification.

---

# 66. SECURITY AND PRIVACY RULES

Requirement/proposal system must not expose:

* Buyer phone without consent
* Buyer email without consent
* Buyer private notes
* Hidden contact data
* Private messages
* Admin notes
* Lead notes to wrong role
* Other agents’ assigned leads
* Draft/pending/rejected requirements publicly
* Expired hidden requirements
* Internal match score if not public

All access must be checked server-side.

---

# 67. SPAM / ABUSE CONTROL

Protect against:

* Fake requirements
* Duplicate requirements
* Proposal spam
* Contact harvesting
* Message spam
* Broker pretending owner
* Fake property proposal
* Wrong city proposals
* Lead abuse
* Site visit spam

Controls may include:

* Approval workflow
* Rate limits
* Duplicate detection
* Report button
* Admin moderation
* Plan limits
* Verification requirement
* Contact reveal limits
* Message rate limits

No fake fraud score.

---

# 68. MOBILE UX REQUIREMENTS

Mobile requirement flow must be app-like.

Requirements:

* Step-based form
* Large cards
* City/locality bottom sheet
* Budget chips
* Property type chips
* Sticky next/submit button
* Back icon
* Save draft
* Proposal cards
* Lead cards
* Site visit cards
* Message thread mobile view
* No horizontal scroll
* No desktop tables

Requirement feed mobile:

* Card-based
* Filters in bottom sheet
* Clear Send Proposal CTA
* Plan limit notice
* No cramped table

---

# 69. EMPTY STATES

Requirement empty states:

Buyer:

```txt id="29p1yr"
You have not posted any requirement yet. Post your requirement to receive matching proposals.
```

Broker feed:

```txt id="o4rm96"
No matching requirements found in your selected city.
```

Proposal:

```txt id="ge51jx"
No proposals received yet.
```

Site visit:

```txt id="iuypwl"
No site visits scheduled.
```

Messages:

```txt id="ep1yuw"
No messages yet.
```

No fake records.

---

# 70. ERROR STATES

Error states:

* Failed to submit requirement
* Requirement approval pending
* Requirement expired
* Permission denied
* Plan limit reached
* Proposal send failed
* Duplicate proposal
* Lead creation failed
* Site visit slot unavailable
* Message send failed
* Provider missing
* User suspended
* Requirement not found

Show clear message.

Do not show raw database errors.

---

# 71. SUCCESS STATES

Success states:

* Requirement draft saved
* Requirement submitted
* Requirement approved
* Proposal sent
* Proposal shortlisted
* Contact shared
* Lead created
* Site visit requested
* Site visit confirmed
* Message sent
* Requirement closed
* Requirement renewed

Success only after server confirmation.

---

# 72. NO-FAKE RULE

Do not fake:

* Requirement count
* Proposal count
* Match score
* Lead count
* Viewed status
* Contact shared status
* WhatsApp sent
* Site visit confirmed
* Message delivered/read
* Plan usage
* Agent assignment
* Requirement approval
* Buyer contact
* Broker response

If tracking is not implemented, hide status.

---

# 73. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Guest post requirement opens login/register.
* Buyer can post requirement.
* Tenant can post requirement.
* Requirement type changes fields.
* Land requirement hides BHK.
* Rent requirement shows rent/deposit fields.
* PG requirement shows PG fields.
* Requirement saves draft.
* Requirement submits.
* Pending requirement not visible to responders.
* Approved active requirement visible to eligible responder.
* Broker can send proposal if allowed.
* Agency can send proposal if allowed.
* Builder can send proposal if allowed.
* Owner cannot access feed unless enabled.
* Buyer receives proposal.
* Buyer can shortlist/reject/contact.
* Buyer can use profile number or alternate number.
* Alternate number appears clearly to receiver.
* Site visit request works.
* Receiver can approve/reschedule/reject visit.
* Messaging works or is hidden if not implemented.
* Expired requirement stops proposals.
* Mobile UI has no horizontal scroll.
* No fake counts/status.
* No screenshot/video capture required.

---

# 74. PASS / FAIL RULE

This phase is PASS only if:

* Requirement posting exists and is type-aware.
* Buyer/Tenant can post.
* Guest auth intent works.
* Requirement privacy is respected.
* Requirement feed is permission/plan controlled.
* Proposal flow works.
* Buyer can receive/respond to proposals.
* Lead creation from proposal/contact works.
* Current/alternate number rule works.
* Site visit flow works if enabled.
* Messaging works or is hidden if not implemented.
* Draft/pending/rejected requirements are not exposed.
* No fake counts or fake statuses are shown.
* Mobile UI works.
* Feature registry updated.
* Manual verification completed.

If buyer private phone is exposed without consent, mark FAIL.

If broker/agency can spam unlimited proposals when plan limits are enabled, mark FAIL.

If requirement form is generic and shows irrelevant fields, mark PARTIAL or FAIL.

---

# 75. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for auth, property, contact, dashboard, subscription, provider, database and QA details.

---

# 76. END OF FILE

This file defines buyer/tenant requirement marketplace, proposals, leads, site visits and messaging for My Gujarat Property.

The system must allow real buyers/tenants to post requirements and allow eligible supply-side users to send relevant proposals while protecting privacy, preventing spam and maintaining no-fake behavior.

Nothing from uploaded docs or user chat instructions should be skipped.
