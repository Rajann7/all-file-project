# MY GUJARAT PROPERTY

# ROLE-BASED PROFILE, ROLE CHANGE APPROVAL & BUSINESS PROFILE SPEC

## FILE NAME

`07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete role-based profile, business profile, role upgrade/change request, admin approval, profile completion, verification and subscription impact rules for **My Gujarat Property**.

This file must be read before building or redesigning:

* User profile
* Role-based profile sections
* Buyer profile
* Tenant profile
* Owner profile
* Broker profile
* Agency profile
* Agent profile
* Builder profile
* Real Estate Group profile
* Admin/staff profile
* Profile avatar upload
* Broker photo/logo upload
* Agency logo upload
* Builder logo upload
* Image crop option
* Email verification from profile
* Phone verification display
* Active role selector
* Role change/upgrade request
* Role approval workflow
* Role rejection workflow
* Role-based subscription display
* Subscription migration rules
* Profile completion
* Verification status
* Public profile pages
* Business verification
* Admin role review
* Profile security/session settings

The goal is to make sure every role has the correct profile, correct permissions, correct visible data and correct business workflow.

---

# 2. CORE PROFILE PRINCIPLE

Profile must be role-based.

A buyer profile must not look like a broker profile.

A broker profile must not look like a builder profile.

An agency profile must not look like a simple user profile.

A builder profile must have company/project identity.

Every profile must show only relevant fields and actions.

Role-based profile controls:

* Header avatar/profile menu
* Dashboard identity
* Public profile if applicable
* Subscription display
* Verification status
* Role permissions
* Contact flow
* Lead flow
* Property posting eligibility
* Requirement posting eligibility
* Banner ad eligibility
* Admin approval needs

---

# 3. PROFILE TYPES

The platform must support these profile types:

## Public/User Profiles

* Buyer profile
* Tenant profile
* Investor profile if enabled
* Owner profile
* Broker profile
* Agency Owner profile
* Agency Agent profile
* Builder profile
* Developer profile if enabled
* Real Estate Group profile if enabled

## Operational Profiles

* Support Executive profile
* Moderator profile
* Verification Executive profile
* Content Manager profile
* Advertisement Manager profile
* City Manager profile

## Administrative Profiles

* Admin profile
* Super Admin profile

Each type must have correct fields, access, visibility and UI.

---

# 4. COMMON PROFILE FIELDS

Every logged-in user profile may include:

* User ID
* Full name
* Mobile number
* Phone verified status
* Email address
* Email verified status
* Profile avatar
* Active role
* Available roles
* Account status
* City
* District
* Taluka if relevant
* Language preference
* Notification preferences
* Created date
* Last updated date
* Last login if available
* Profile completion percentage
* Subscription/plan summary if applicable
* Verification summary if applicable
* Security/session settings if implemented

Common profile fields must not replace role-specific fields.

---

# 5. PROFILE IMAGE / AVATAR RULE

Profile image upload must support:

* Recommended size display
* Recommended ratio display
* Preview
* Crop option
* Replace option
* Remove option
* File type validation
* File size validation
* Safe compression
* Safe fallback avatar
* Mobile-friendly crop UI

Recommended avatar ratio:

```txt id="ostmsk"
1:1 square
```

Example recommended size:

```txt id="z6o3bu"
400x400 px or higher
```

If uploaded image is different ratio, crop/fit safely.

Do not break UI because of wrong image size.

Do not use fake profile images.

---

# 6. LOGO UPLOAD RULE

Broker/Agency/Builder/Real Estate Group logos must support:

* Recommended size display
* Recommended ratio display
* Preview
* Crop/fit option
* Transparent/logo background handling
* Replace option
* Remove option
* File type validation
* File size validation
* Mobile-friendly upload UI

Recommended logo ratios may include:

```txt id="du5hcl"
1:1 square logo
4:1 wide logo
16:9 cover-style brand image if needed
```

Exact recommendations should be shown in each upload UI.

Business logos should not be stretched.

---

# 7. PROFILE COMPLETION RULE

Profile completion should guide the user but not overload them.

Profile completion may include:

* Basic details
* Contact details
* City/locality
* Role-specific details
* Profile image/logo
* Email verification
* Business verification
* Documents if required
* Subscription if required for premium actions

Profile completion must be role-specific.

Example:

Buyer completion:

* Name
* Phone verified
* City
* Budget preference
* Saved search preference

Broker completion:

* Name
* Phone verified
* Broker photo/logo
* Business name
* Operating cities
* Brokerage policy
* Verification documents if required

Agency completion:

* Agency name
* Agency logo
* Office address
* Operating cities
* Team size
* Verification documents if required

Builder completion:

* Builder company name
* Builder logo
* Office address
* Projects
* RERA/company verification if required

Profile completion percent must be real if shown.

Do not show fake completion progress.

---

# 8. BUYER PROFILE SPEC

Buyer profile is for users who want to buy property.

## 8.1 Buyer Profile Fields

Buyer profile may include:

* Full name
* Mobile number
* Email
* City
* Preferred cities
* Preferred localities
* Property purpose
* Property types interested
* Budget range
* BHK preference
* Area preference
* Possession preference
* Loan/pre-approved status if implemented
* Contact preference
* Saved properties
* Saved searches
* Posted requirements
* Proposal responses
* Site visits
* Notification preferences

## 8.2 Buyer Profile Actions

Buyer can:

* Edit basic profile
* Upload avatar
* Verify email
* Manage saved properties
* Manage saved searches
* Post buyer requirement
* Edit own requirement
* View received proposals
* Book site visits
* Request role change
* View optional plans if enabled
* Manage notifications
* Logout

## 8.3 Buyer Cannot

Buyer cannot:

* Post property unless owner/broker/agency/builder role exists
* Access broker requirement feed
* Submit business banner ads
* Access admin
* Self-assign business role
* Self-edit subscription status

## 8.4 Buyer Public Visibility

Buyer profile should generally be private.

Public buyer profile should not be shown unless product later enables public requirement identity and user consents.

Buyer phone/email must not be public.

---

# 9. TENANT PROFILE SPEC

Tenant profile is for users looking for rent, PG, hostel or co-living.

## 9.1 Tenant Profile Fields

Tenant profile may include:

* Full name
* Mobile number
* Email
* City
* Preferred rental cities
* Preferred localities
* Rental budget
* Deposit preference
* Property type preference
* BHK preference
* PG/hostel preference
* Gender preference if PG/hostel flow requires it
* Food preference
* Sharing preference
* Move-in date
* Tenant type
* Family/bachelor/company lease preference
* Saved rentals
* Posted rental requirements
* Site visits
* Contact preference

## 9.2 Tenant Actions

Tenant can:

* Edit profile
* Upload avatar
* Verify email
* Save rentals
* Post rental requirement
* Post PG/hostel requirement
* View proposals
* Book site visits
* Request role change
* Manage notifications
* View optional plans if enabled

## 9.3 Tenant Privacy

Tenant identity and contact must remain private unless explicitly shared through lead/contact flow.

---

# 10. INVESTOR PROFILE SPEC

Investor role is optional.

If implemented, Investor profile may include:

* Preferred cities
* Budget range
* Investment type
* Residential/commercial/land preference
* ROI preference if implemented
* Rental yield interest if implemented
* Project interest
* Plot/land interest
* Requirement posts
* Saved properties
* Contact preference

Investor can behave similar to Buyer with investment-specific filters.

If Investor role is not implemented, hide it.

---

# 11. OWNER PROFILE SPEC

Owner profile is for individual property owners.

## 11.1 Owner Profile Fields

Owner profile may include:

* Full name
* Mobile number
* Email
* Avatar
* City
* Address optional/private
* Owner verification status
* Preferred contact method
* Public display name
* Properties posted
* Leads received
* Site visits
* Listing plan
* Documents if verification required

## 11.2 Owner Actions

Owner can:

* Edit profile
* Upload avatar
* Verify email
* Post property
* Manage own properties
* Manage leads
* Manage site visits
* Renew listings
* Mark sold/rented
* Archive listings
* View subscription/plan
* Buy/renew owner plan
* Request role change
* Submit verification if required

## 11.3 Owner Public Profile

Owner public profile should be limited.

May show:

* Display name
* Source tag: Direct Owner
* Verified owner badge only if real
* Active public listings
* Contact CTA based on contact mode

Do not expose private address, email or phone unless contact mode allows.

---

# 12. BROKER PROFILE SPEC

Broker profile is a business profile.

## 12.1 Broker Required Fields

Broker profile should include:

* Broker display name
* Full name
* Mobile number
* Email
* Broker photo or logo
* Business name
* Operating cities
* Operating localities
* Property types handled
* Sale/rent/commercial/land focus
* Experience
* Brokerage policy
* Office address optional/public-safe
* RERA/license number if applicable
* Verification documents if required
* Public profile slug
* Profile description
* Contact preference
* Subscription plan
* Verification status

## 12.2 Broker Optional Fields

Optional fields:

* Website
* Instagram/Facebook/LinkedIn
* WhatsApp number if different
* Team size
* Languages spoken
* Awards if real
* Specialization
* Working hours
* Service areas
* Google Business link if real

No fake awards.

No fake verification.

## 12.3 Broker Actions

Broker can:

* Edit broker profile
* Upload broker photo/logo
* Crop image/logo
* Manage listings
* View buyer requirements if plan allows
* Send proposals
* Manage leads
* Manage site visits
* View subscription
* Buy/renew broker plan
* Request agency role
* Submit verification
* Promote listings if allowed
* Buy banner ads if enabled for brokers
* Manage public profile

## 12.4 Broker Public Profile

Broker public profile may show:

* Broker name
* Photo/logo
* Verified badge if real
* Operating cities
* Localities
* Property types
* Active listings
* Contact CTA
* WhatsApp CTA if provider/mode allows
* Brokerage policy
* About section
* Public reviews only if real

Do not show fake ratings.

Do not show fake number of deals.

Do not show fake years of experience.

---

# 13. AGENCY OWNER PROFILE SPEC

Agency Owner profile represents a real estate agency/business.

## 13.1 Agency Required Fields

Agency profile should include:

* Agency name
* Agency logo
* Agency owner name
* Mobile number
* Email
* Office address
* Operating cities
* Operating localities
* Business type
* Team/agents
* Property categories served
* Agency description
* Verification status
* Subscription plan
* Public agency slug
* Contact preference

## 13.2 Agency Optional Fields

Optional:

* Website
* Social media links
* GST number if relevant
* RERA/license if applicable
* Business registration number
* Office photos if enabled
* Working hours
* Team size
* Specialization
* Branches
* Service areas

Show only real data.

## 13.3 Agency Owner Actions

Agency Owner can:

* Edit agency profile
* Upload/crop agency logo
* Add agents
* Remove agents
* Assign listings
* Assign leads
* Manage agency listings
* View requirements
* Send proposals
* Manage site visits
* Manage subscription
* Buy/renew agency plan
* Submit banner ads
* Manage banner ad campaigns
* Submit verification
* Manage agency public profile
* View real analytics if implemented

## 13.4 Agency Public Profile

Agency public profile may show:

* Agency logo
* Agency name
* Verification status if real
* Operating cities/localities
* Public listings
* Agents if public
* Contact CTA
* About
* Specialization
* Banner/sponsored status if active and labeled

Do not show fake team members.

---

# 14. AGENCY AGENT PROFILE SPEC

Agency Agent works under an Agency Owner.

## 14.1 Agent Profile Fields

Agent profile may include:

* Full name
* Mobile number
* Email
* Avatar
* Assigned agency
* Role within agency
* Assigned cities/localities
* Assigned listings
* Assigned leads
* Assigned site visits
* Permissions
* Active/inactive status
* Joined date

## 14.2 Agent Actions

Agent can:

* Edit own basic profile
* Upload avatar
* View assigned leads
* View assigned listings if allowed
* Update assigned lead status if permitted
* View assigned site visits
* Manage own tasks
* View messages if implemented
* View notifications

## 14.3 Agent Cannot

Agent cannot:

* Manage agency billing
* Manage subscription
* Submit agency banner ads unless permission allows
* Remove other agents
* Access all agency leads unless allowed
* Change own permissions
* Access admin

Agent access must be assignment-scoped.

---

# 15. BUILDER PROFILE SPEC

Builder profile is a company/project profile.

## 15.1 Builder Required Fields

Builder profile should include:

* Builder company name
* Builder logo
* Authorized person name
* Mobile number
* Email
* Office address
* Operating cities
* Project categories
* Builder description
* RERA/company details if applicable
* Verification status
* Public builder slug
* Subscription plan

## 15.2 Builder Optional Fields

Optional:

* Website
* Social links
* Company registration number
* GST number if relevant
* Years in business if real
* Completed projects count if real
* Ongoing projects count if real
* Team contact
* Brochure/company profile
* Awards if real

No fake completed project counts.

No fake awards.

## 15.3 Builder Actions

Builder can:

* Edit builder profile
* Upload/crop builder logo
* Add projects
* Manage projects
* Add project units
* Upload project images
* Upload brochures
* View project leads
* Manage site visits
* Manage subscription
* Buy/renew builder plan
* Submit banner ads if enabled
* Promote projects
* Submit verification
* Manage public profile

## 15.4 Builder Public Profile

Builder public profile may show:

* Builder logo
* Builder name
* Verification if real
* Projects
* Operating cities
* About
* Contact CTA
* RERA/company info if public
* Sponsored status if active and labeled

---

# 16. DEVELOPER PROFILE SPEC

Developer role can be separate from Builder if business decides.

If implemented, Developer profile may include:

* Developer company name
* Logo
* Projects
* Land/development focus
* RERA/company details
* Office address
* Operating cities
* Subscription plan
* Verification status

If not implemented separately, map Developer to Builder.

Do not show Developer role if not active.

---

# 17. REAL ESTATE GROUP PROFILE SPEC

Real Estate Group can be separate or mapped to Agency.

This role is important for homepage banner ads.

## 17.1 Real Estate Group Fields

* Group name
* Group logo
* Contact person
* Mobile number
* Email
* City
* Operating cities
* Business description
* Website/social links
* Verification status
* Subscription/banner ad eligibility
* Public profile if enabled

## 17.2 Real Estate Group Actions

Real Estate Group can:

* Edit profile
* Upload/crop logo
* Buy banner ad package
* Submit banner ads
* Manage banner ads
* View ad status
* Renew ads
* View ad analytics if implemented
* Manage subscription/billing
* Submit verification

If Real Estate Group is not separate, Agency profile should include this functionality.

---

# 18. ADMIN / STAFF PROFILE SPEC

Staff profiles include:

* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager
* Admin
* Super Admin

## 18.1 Staff Profile Fields

* Full name
* Staff email/phone
* Staff role
* Permissions
* Assigned city if applicable
* Account status
* Last login
* Created by
* Activity/audit summary if permitted
* Security/session settings

## 18.2 Staff Restrictions

Staff cannot:

* Self-increase permissions
* Self-change admin role
* Delete Super Admin
* Access provider secrets unless permitted
* Use public role change flow for staff roles

Staff accounts should be created/invited by Admin/Super Admin.

---

# 19. ACTIVE ROLE PROFILE SWITCHER

Users with multiple approved roles should have role switcher.

Role switcher should show:

* Active role
* Approved roles
* Pending role requests
* Rejected role requests
* Request new role button

Role switch should:

* Update active role
* Update header
* Update sidebar
* Update dashboard route
* Update profile sections
* Update subscription display
* Update permissions

Do not allow switching to pending/rejected role.

---

# 20. ROLE CHANGE REQUEST FLOW

Role change request flow:

```txt id="39k16p"
User opens Profile
User opens Roles / Upgrade Role
User selects requested role
System shows required information
User fills role-specific details
User uploads required documents if needed
System shows subscription impact note
User submits request
Admin reviews
Admin approves/rejects/asks changes
User receives notification
Approved role becomes available
User can switch active role
```

Role change must not instantly grant protected business/admin access unless the role is configured as auto-approve.

Business roles should usually require approval/verification depending settings.

---

# 21. ROLE CHANGE REQUEST TYPES

Possible role requests:

* Buyer → Owner
* Buyer → Broker
* Buyer → Agency
* Buyer → Builder
* Tenant → Owner
* Owner → Broker
* Broker → Agency
* Broker → Builder
* Agency Agent → Broker independent
* Owner/Broker/Agency/Builder → Real Estate Group if separate
* Any public role → Investor if enabled

Admin/staff roles must not be requested publicly unless Super Admin explicitly creates a staff invite system.

---

# 22. ROLE CHANGE STATUS

Role request statuses:

```txt id="p0ua69"
Draft
Submitted
Under Review
Need More Details
Approved
Rejected
Cancelled
Expired
Archived
```

User should see:

* Current status
* Submitted date
* Requested role
* Admin message
* Missing requirements
* Rejection reason
* Resubmit option if allowed

Admin should see:

* User details
* Current role
* Requested role
* Existing subscription
* Submitted fields
* Documents
* Risk signals if real
* Approval actions
* Audit history

---

# 23. ROLE APPROVAL RULE

Admin approval should be required for sensitive roles.

Recommended approval requirement:

| Requested Role    | Approval Recommended |
| ----------------- | -------------------- |
| Buyer             | No / auto            |
| Tenant            | No / auto            |
| Owner             | Optional             |
| Broker            | Yes                  |
| Agency            | Yes                  |
| Builder           | Yes                  |
| Real Estate Group | Yes                  |
| Staff/Admin       | Super Admin only     |
| Super Admin       | Never public         |

Admin approval actions:

* Approve
* Reject
* Request changes
* Add internal note
* Add user-visible note
* Assign verification status
* Attach role validity if needed

Role approval must be server-side.

---

# 24. ROLE REJECTION RULE

If admin rejects role request:

User should see:

* Rejected status
* Reason
* What to fix
* Resubmit option if allowed
* Support contact if needed

Do not remove user’s current role.

Do not cancel current active subscription unless policy requires and user is informed.

Rejected role should not grant access.

---

# 25. ROLE CHANGE AND SUBSCRIPTION IMPACT

This is critical.

If user has active subscription in current role and requests new role, system must handle plan impact clearly.

Important principle:

```txt id="t7y1rf"
Do not silently transfer, upgrade, downgrade, cancel or misuse subscription without clear rule.
```

Subscription plans are usually role-specific.

Examples:

* Owner plan is not automatically Broker plan.
* Broker plan is not automatically Agency plan.
* Agency plan may include agents and banner ads.
* Builder plan may include projects/units.
* Banner ads may be separate paid feature.

---

# 26. SUBSCRIPTION MIGRATION OPTIONS

System can support one or more migration strategies.

## Option A — Keep Current Plan Until Expiry

Recommended safe default.

User keeps current role plan active.

New role requires separate plan purchase if needed.

Example:

Owner has active Owner plan.

Owner requests Broker role.

Admin approves Broker role.

Owner plan remains active until expiry for owner listings.

Broker features require Broker plan.

## Option B — Upgrade with Credit

If payment system supports credit/proration:

* Calculate unused value from current plan.
* Apply credit to new role plan.
* User pays difference.
* Record credit.
* Show invoice/adjustment.
* Admin/Super Admin can override.

## Option C — Admin Manual Migration

Admin can manually migrate plan.

Use when:

* User contacted support.
* Plan compatibility is unclear.
* Business wants manual control.

Must create audit log.

## Option D — Compatible Plan Mapping

If plans are intentionally compatible:

Example:

Agency plan includes Broker features.

Broker upgrading to Agency may use upgrade path.

Must be explicitly defined.

## Option E — Downgrade After Expiry

If user downgrades to lower role:

* Current plan remains until expiry.
* New lower plan applies after expiry.
* Or admin-approved downgrade.

Prevent abuse.

---

# 27. SUBSCRIPTION MIGRATION RECOMMENDED RULE

Recommended default for My Gujarat Property:

```txt id="n88jt7"
Keep existing active plan active for its original role until expiry.
New role access requires compatible plan, upgrade purchase, or admin-approved migration.
```

This is safest because it avoids:

* Wrong plan benefits
* Free upgrade abuse
* Billing confusion
* Manual calculation errors
* Support disputes

User must see clear message before role change.

Example message:

```txt id="p4qneo"
Your current Owner plan will remain active until expiry. Broker features may require a Broker plan after your Broker role is approved.
```

---

# 28. ROLE CHANGE WITH ACTIVE BANNER ADS

If user has active banner ads and changes role:

Rules:

* Active paid banner ads should continue until expiry if advertiser entity remains valid.
* If role/entity becomes invalid, Admin review required.
* Do not auto-cancel paid ads without policy.
* Do not allow new ads if new role is not eligible.
* Archive expired ads normally.
* Show clear status.

Example:

Agency with active banner ad changes to Builder.

Admin must decide whether banner ad entity should remain Agency, convert, or expire normally.

---

# 29. ROLE CHANGE WITH ACTIVE LISTINGS

If user changes role:

Existing listings should remain linked to original owner/business entity.

Examples:

Owner becomes Broker:

* Owner’s old listings remain owner listings unless changed/admin approved.
* Broker listings should use broker source type.

Broker becomes Agency:

* Existing broker listings may stay under broker profile or migrate to agency if admin/user chooses.
* Migration must be explicit.

Do not silently change listing source tags.

---

# 30. ROLE CHANGE WITH LEADS

Existing leads should remain accessible according to original ownership.

Examples:

Owner leads remain under owner listing.

Broker leads remain under broker listing.

Agency leads remain under agency account.

If role changes, do not leak leads to wrong role.

Lead access migration must be explicit and audit-logged.

---

# 31. PROFILE AND SUBSCRIPTION DISPLAY

Profile must show role-based plan status.

For each active role, show:

* Role name
* Plan name
* Plan status
* Start date
* Expiry date
* Usage limits
* Used limits
* Renewal CTA
* Upgrade CTA
* Payment/billing link
* Role-specific benefits

If user has multiple roles, show plan per role.

Example:

```txt id="uewjxi"
Owner Role: Free Plan, 2/3 listings used
Broker Role: No active plan
Agency Role: Pending approval
```

Do not show one generic plan if plans are role-specific.

---

# 32. VERIFICATION STATUS

Verification should be role-specific.

Possible statuses:

```txt id="a7s0sp"
Not Submitted
Pending
Under Review
Verified
Rejected
Expired
Need More Details
Suspended
```

Buyer/Tenant may not need full verification.

Owner may need optional verification.

Broker/Agency/Builder should support verification.

Verification badge must only show when verified.

Do not show fake verified badge.

---

# 33. PROFILE PUBLIC / PRIVATE VISIBILITY

Every profile field must define visibility.

Visibility options:

* Private
* Public
* Admin only
* Team only
* Lead receiver only
* Verification team only

Examples:

Phone:

* Private by default
* Used in leads/contact if allowed

Email:

* Private by default

Business logo:

* Public

Agency name:

* Public

Verification documents:

* Admin/verification team only

Lead notes:

* Private/internal

Do not expose private profile data publicly.

---

# 34. CONTACT PREFERENCE

Profile can include contact preference.

Options:

* Phone
* WhatsApp
* Lead form
* Message
* Email if verified and allowed
* Business hours only
* Hide direct number
* Request contact approval

Contact preference must work with contact visibility settings.

Do not show WhatsApp API send if provider not configured.

---

# 35. PROFILE NOTIFICATION PREFERENCES

Notification preferences may include:

* Lead alerts
* Requirement alerts
* Proposal alerts
* Site visit alerts
* Subscription alerts
* Banner ad expiry alerts
* Verification alerts
* Support alerts
* Marketing alerts if allowed

Channels:

* In-app
* Email if verified/provider configured
* WhatsApp if provider/mode configured
* SMS if provider configured
* Push if implemented

Do not fake notification delivery.

---

# 36. SECURITY PROFILE SECTION

Profile security section may include:

* Phone verification status
* Email verification status
* Active sessions
* Logout all devices
* Login history if implemented
* Password settings if email/password enabled
* Connected providers
* Delete account request if implemented
* Privacy settings

If not implemented, hide.

Do not show fake device/session list.

---

# 37. PROFILE IMAGE CROP REQUIREMENT

Crop option is required wherever profile image/logo is uploaded.

Applies to:

* User avatar
* Broker photo
* Broker logo
* Agency logo
* Builder logo
* Real Estate Group logo
* Staff profile image if enabled

Crop UI should support:

* Square crop
* Zoom
* Move
* Preview
* Save
* Cancel
* Mobile full-screen crop
* Desktop modal crop

Do not stretch logos/photos.

---

# 38. BUSINESS COVER IMAGE OPTIONAL

Business profiles may support optional cover image.

Applies to:

* Broker profile
* Agency profile
* Builder profile
* Real Estate Group profile

If implemented, show recommended size.

Example:

```txt id="qz8gj4"
Recommended cover image: 1600x500 px
```

Should support:

* Desktop crop
* Mobile crop/focal point
* Preview
* Replace/remove

If not implemented, hide.

---

# 39. PUBLIC PROFILE SEO

Public business profiles should support SEO.

Broker:

```txt id="1v7c97"
/brokers/[broker-slug]
```

Agency:

```txt id="7vmfd1"
/agencies/[agency-slug]
```

Builder:

```txt id="x2ng27"
/builders/[builder-slug]
```

Public profile metadata should use real data.

No fake ratings/reviews.

No fake “top broker” unless curated/ranked.

Profile slug should be clean.

---

# 40. PROFILE ROUTES

Common profile routes:

```txt id="1eum4v"
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

Dashboard role-specific profile routes:

```txt id="xl1j0f"
/dashboard/buyer/profile
/dashboard/tenant/profile
/dashboard/owner/profile
/dashboard/broker/profile
/dashboard/agency/profile
/dashboard/agent/profile
/dashboard/builder/profile
/dashboard/real-estate-group/profile
```

Public profile routes:

```txt id="k4y6jc"
/brokers/[slug]
/agencies/[slug]
/builders/[slug]
/real-estate-groups/[slug]
```

Only show routes that are implemented.

---

# 41. PROFILE UI LAYOUT

Profile UI should use:

* Profile header card
* Avatar/logo section
* Role tabs or role cards
* Completion checklist
* Basic details card
* Contact details card
* Role-specific details card
* Verification card
* Subscription card
* Security card
* Notification card
* Danger zone if implemented

Mobile:

* Stacked cards
* Sticky save button if editing
* Back icon
* No wide tables
* Large inputs
* Crop modal full-screen if needed

Desktop:

* Sidebar/profile nav
* Main content cards
* Two-column sections where useful

---

# 42. PROFILE EDIT UX

Profile edit should include:

* Clear sections
* Save/cancel
* Inline validation
* Loading state
* Success state
* Error state
* Unsaved changes warning if needed
* Mobile-friendly inputs
* Image crop/preview
* Privacy hints

Do not save partial invalid data silently.

---

# 43. ROLE-BASED HEADER CONNECTION

Profile affects header.

If logged-in user has avatar:

Show avatar.

If no avatar:

Show initials.

Header profile menu should show:

* Name
* Active role
* Profile completion
* Dashboard
* Role switch
* Subscription
* Settings
* Logout

Do not show Login/Register to logged-in user.

---

# 44. ROLE-BASED DASHBOARD CONNECTION

Profile affects dashboard.

Dashboard should show:

* Correct avatar/logo
* Correct role name
* Correct business name
* Correct plan
* Correct verification status
* Correct profile completion
* Correct role actions

Example:

Broker dashboard header should show broker/business identity.

Agency dashboard should show agency name/logo.

Builder dashboard should show builder company/logo.

---

# 45. PROFILE COMPLETION GATING

Some features may require profile completion.

Examples:

Owner cannot submit listing until required owner profile fields complete.

Broker cannot send proposals until broker profile complete if setting requires.

Agency cannot add agents until agency profile created.

Builder cannot submit project until builder profile complete.

Banner ads may require agency/builder/group profile and plan/payment.

If blocked, show clear checklist.

Do not silently fail.

---

# 46. PROFILE VERIFICATION GATING

Some features may require verification.

Examples:

* Verified badge
* Higher listing limits
* Lead access
* Requirement feed access
* Banner ad eligibility
* Builder project approval speed
* Agency public trust badge

If verification required and missing:

* Show requirement
* Show submit verification CTA
* Do not fake verified state

---

# 47. PROFILE DATA SECURITY

Profile data must be protected.

Rules:

* Users can edit their own profile only.
* Agency Owner can manage agency profile.
* Agent can edit own profile but not agency profile unless permitted.
* Admin can edit/manage based on permission.
* Super Admin has full access.
* Private fields should not appear publicly.
* Server-side permission checks required.
* RLS policies required if using Supabase.
* Storage policies required for images/documents.

---

# 48. PROFILE DOCUMENT STORAGE

Verification/business documents must be private.

Private documents:

* ID proof if collected
* Business registration
* RERA/license
* Agency documents
* Builder documents
* Address proof
* Verification files

These must not be in public storage buckets.

Only permitted admin/verification roles can access.

Public images/logos can be in public bucket.

---

# 49. ACCOUNT STATUS IN PROFILE

Profile should show account status if relevant.

Statuses:

* Active
* Pending
* Suspended
* Banned
* Deleted
* Archived

If suspended:

* Show safe message.
* Block restricted actions.
* Allow support contact if policy.

If banned:

* Block login/actions based on auth document.
* Do not allow normal usage.

Admin can update status based on permission.

---

# 50. PROFILE DELETE / DEACTIVATE ACCOUNT

Optional feature.

If implemented:

* User can request account deletion/deactivation.
* Admin may review if business data exists.
* Do not delete records that break audit/payment/compliance.
* Anonymize where policy allows.
* Preserve required audit logs.
* Block active paid plan misuse.

If not implemented, hide.

---

# 51. PROFILE ADMIN REVIEW

Admin profile review should show:

* User details
* Current roles
* Requested roles
* Verification status
* Subscription status
* Listings
* Leads summary
* Reports/fraud flags if real
* Documents
* Activity history
* Audit logs
* Approve/reject actions

Admin should not see private data beyond permission.

---

# 52. ROLE CHANGE ADMIN PANEL

Admin role change review should include:

* User name
* Phone
* Email
* Current role
* Requested role
* Submitted data
* Documents
* Active subscription info
* Existing listings/leads
* Verification status
* Risk/fraud notes if real
* Approval buttons
* Rejection reason
* Request more info
* Internal note
* Audit log

Admin must not approve staff/admin role from public request unless Super Admin controlled.

---

# 53. ROLE CHANGE NOTIFICATIONS

User should be notified when:

* Role request submitted
* Role request under review
* More details requested
* Role approved
* Role rejected
* Role expired/cancelled
* Subscription impact requires action

Channels:

* In-app
* Email if verified/configured
* WhatsApp if configured
* SMS if configured

Do not fake external notifications.

---

# 54. PROFILE AND BANNER ADS CONNECTION

Banner ads require eligible business profile.

Eligible entities:

* Agency
* Real Estate Group
* Builder if enabled
* Broker if enabled
* Developer if enabled

Before banner ad submission, check:

* Role eligibility
* Profile completeness
* Verification requirement if enabled
* Plan/payment requirement
* Logo/image upload ability
* City targeting availability
* Contact/business details

If buyer/tenant tries to submit ad:

* Show role request/upgrade flow.

---

# 55. PROFILE AND PROPERTY POSTING CONNECTION

Property posting requires correct role.

Owner:

* Can post own property.

Broker:

* Can post broker listing.

Agency:

* Can post agency listing.

Builder:

* Can post project/unit.

Buyer/Tenant:

* Cannot post property unless role upgrade/owner role exists.

Role decides listing source tag.

Do not let a broker post as Direct Owner unless policy allows and admin verifies.

---

# 56. PROFILE AND LEAD CONNECTION

Lead receiver identity should come from listing/entity profile.

Owner lead goes to owner.

Broker lead goes to broker.

Agency lead goes to agency/assigned agent if configured.

Builder lead goes to builder/project team.

If profile contact settings hide direct phone, lead form should be used.

Alternate number from lead sender must be stored separately.

---

# 57. PROFILE AND SEO CONNECTION

Public business profiles should support SEO only if public/approved.

Indexable profiles:

* Approved broker profile
* Approved agency profile
* Approved builder profile
* Approved public project profile

Noindex:

* Private buyer/tenant profile
* Suspended profile
* Pending/rejected business profile
* Staff/admin profile
* Incomplete spam profile

---

# 58. PROFILE FEATURE FLAGS

Possible feature flags:

```txt id="mumh3n"
profile.enabled
profile.avatar_upload.enabled
profile.logo_upload.enabled
profile.image_crop.enabled
profile.email_verification.enabled
profile.role_switch.enabled
profile.role_change_request.enabled
profile.business_profiles.enabled
profile.public_broker_profiles.enabled
profile.public_agency_profiles.enabled
profile.public_builder_profiles.enabled
profile.verification.enabled
profile.session_management.enabled
profile.delete_account.enabled
profile.notification_preferences.enabled
```

If feature flag is off, hide UI and block backend action if needed.

---

# 59. PROFILE COMPONENTS

Recommended components:

* ProfileShell
* ProfileHeaderCard
* AvatarUploader
* LogoUploader
* ImageCropModal
* ProfileCompletionCard
* BasicDetailsForm
* ContactDetailsForm
* EmailVerificationCard
* PhoneVerificationCard
* RoleSwitcher
* RoleCards
* RoleChangeRequestForm
* RoleRequestStatusCard
* SubscriptionSummaryCard
* VerificationStatusCard
* BusinessProfileForm
* BrokerProfileForm
* AgencyProfileForm
* AgentProfileForm
* BuilderProfileForm
* NotificationPreferencesForm
* SecuritySessionsCard
* PublicBrokerProfile
* PublicAgencyProfile
* PublicBuilderProfile
* AdminRoleReviewPanel

Avoid duplicate random profile components.

---

# 60. PROFILE LOADING STATE

Profile loading should handle:

* Auth session loading
* Profile data loading
* Role data loading
* Subscription loading
* Verification loading
* Public profile loading
* Upload loading
* Save loading

Do not show blank screen.

Use skeleton/card placeholders.

---

# 61. PROFILE EMPTY STATE

Profile empty states:

* No avatar: show initials.
* No logo: show upload logo CTA.
* No role-specific details: show completion checklist.
* No subscription: show free/no plan state.
* No verification: show submit verification CTA.
* No public listings: show empty state.
* No agents: show add agent CTA for agency owner.

No fake profile content.

---

# 62. PROFILE ERROR STATE

Profile error states:

* Failed to load profile
* Failed to save
* Upload failed
* Crop failed
* Invalid file
* Email verification failed
* Role request failed
* Permission denied
* Account suspended
* Provider missing
* Subscription mismatch

Show clear message and retry where useful.

Do not expose raw technical errors.

---

# 63. PROFILE SUCCESS STATE

Success states:

* Profile updated
* Avatar updated
* Logo updated
* Email verification sent
* Email verified
* Role request submitted
* Role approved
* Verification submitted
* Notification preferences saved
* Session logged out
* Account update saved

Success only after server confirms.

---

# 64. PROFILE AUDIT LOGS

Audit logs should be created for important changes if implemented:

* Role request submitted
* Role approved/rejected
* Admin changed user role
* Admin changed profile
* Verification submitted
* Verification approved/rejected
* Subscription manual migration
* Business profile approved
* Staff permission changed
* Account suspended/banned
* Logo/avatar changed if needed

Audit logs must be real if visible.

---

# 65. PROFILE MANUAL VERIFICATION CHECKLIST

Manual verification prompt should verify:

* Logged-in profile opens.
* Avatar upload/crop works.
* Broker logo/photo upload/crop works.
* Agency logo upload/crop works.
* Builder logo upload/crop works.
* Buyer profile shows buyer fields.
* Tenant profile shows tenant fields.
* Owner profile shows owner fields.
* Broker profile shows broker fields.
* Agency profile shows agency fields.
* Agent profile is assignment-scoped.
* Builder profile shows builder fields.
* Active role switch works for approved roles.
* Pending role cannot be activated.
* Role request submits.
* Admin review sees role request.
* Admin approval enables role.
* Admin rejection shows reason.
* Subscription impact is shown during role request.
* Header updates after active role change.
* Dashboard updates after active role change.
* Public business profile hides private data.
* Verification badge only appears when real.
* Mobile profile has no horizontal scroll.
* No screenshot/video capture required.

---

# 66. PROFILE PASS / FAIL RULE

Profile phase is PASS only if:

* Profiles are role-based.
* Buyer/Tenant/Owner/Broker/Agency/Agent/Builder differences are visible.
* Logged-in header shows profile icon.
* Profile image crop works or is clearly pending.
* Business logo upload/crop works or is clearly pending.
* Role change request exists if phase includes it.
* Admin approval/rejection works if implemented.
* Pending role does not grant access.
* Subscription impact is clear.
* Private data is not public.
* Public business profiles show only safe data.
* No fake verification badge.
* No fake plan status.
* Feature registry updated.
* Manual verification completed.

If public user can self-assign admin/business role without approval, mark FAIL.

If broker/agency/builder profile is generic and missing business identity, mark PARTIAL or FAIL depending phase scope.

---

# 67. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for auth, dashboard, property, subscription, verification, database and manual QA details.

---

# 68. END OF FILE

This file defines role-based profile, role change approval and business profile requirements for My Gujarat Property.

Profiles must be role-specific, mobile-friendly, secure, no-fake, approval-aware, subscription-aware and connected to dashboard/header/search/contact/banner ads.

Nothing from uploaded docs or user chat instructions should be skipped.
