# MY GUJARAT PROPERTY

# MASTER PRODUCT, DESIGN, UX, RESPONSIVE & MARKETPLACE REQUIREMENTS

## FILE NAME

`01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`

---

# 1. DOCUMENT PURPOSE

This document defines the master product, design, user experience, responsive behavior and marketplace direction for **My Gujarat Property**.

This file is the main product and UX foundation document.

It must be read before designing or developing:

* Public website
* Homepage
* Search experience
* City pages
* Property listing pages
* Property detail pages
* Login/register popup
* Role-based profile
* Role-based dashboards
* Admin panel
* Super Admin settings
* Subscription/pricing pages
* Banner ads carousel
* SEO pages
* Mobile navigation
* Forms
* Upload flows
* Lead/contact flows
* Requirement marketplace
* Provider-based features
* Responsive UI
* Mobile app-like experience

This document does not replace detailed feature-specific documents.

Instead, it gives the master direction and non-negotiable rules that every detailed document and every Claude phase must follow.

---

# 2. PROJECT VISION

**My Gujarat Property** is an AI-first, mobile-first, Gujarat-first real estate marketplace.

The platform should help people discover, list, promote, manage and connect around real estate properties in Gujarat with trust, speed and transparency.

The platform should feel like a serious Indian real estate property listing website, not a basic template.

The website must feel:

* Professional
* Trusted
* Clean
* Fast
* Mobile-app-like
* Search-first
* Role-aware
* Real estate focused
* Gujarat-localized
* Business-ready
* Admin-controlled
* Scalable to all India later

The platform should eventually support buyers, tenants, owners, brokers, agencies, agents, builders, developers, real estate groups, advertisers, admins and super admins.

---

# 3. PRODUCT POSITIONING

My Gujarat Property is not only a simple property listing board.

It is a real estate marketplace and operating system.

It includes:

* Property discovery
* Property posting
* Project discovery
* Project posting
* Buyer requirement marketplace
* Broker proposal system
* Lead generation
* Contact request system
* Site visit coordination
* Role-based dashboards
* Admin moderation
* Super Admin controls
* Subscriptions
* Paid promotions
* Homepage banner ads
* City-based SEO pages
* Gujarat location database
* Provider integrations
* Verification and trust workflows

The website must be designed as a long-term scalable product.

Do not design it like a temporary landing page.

Do not design it like a basic SaaS dashboard.

Do not design it like a generic classified website.

---

# 4. CORE MARKETPLACE MODEL

The platform supports both supply-side and demand-side marketplace flows.

## 4.1 Supply-Side Flow

```txt id="xp7jea"
Owner / Broker / Agency / Builder posts property or project
Admin verifies/moderates if required
Property becomes visible
Buyer/Tenant searches
Buyer/Tenant contacts
Lead is generated
Site visit or discussion happens
```

## 4.2 Demand-Side Flow

```txt id="5lbz76"
Buyer / Tenant posts requirement
Broker / Agency / Builder views requirement if permitted
Broker / Agency / Builder sends proposal
Buyer / Tenant reviews proposal
Lead / message / site visit is created
```

## 4.3 Promotion Flow

```txt id="44e8rn"
Agency / Real Estate Group / Broker / Builder buys banner ad or promotion
User submits creative
Admin approves
Ad becomes active
City-priority carousel shows ad
Ad expires after time limit
System notifies and archives/hides automatically
```

All three flows must be treated as important.

---

# 5. PRIMARY USER TYPES

The platform must support these user types:

* Guest
* Buyer
* Tenant
* Investor
* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Developer if separated later
* Real Estate Group if implemented separately
* Advertiser if implemented separately
* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager
* Admin
* Super Admin

Every role must have relevant UI, permissions and dashboard behavior.

Do not build only for one generic user.

---

# 6. ROLE-BASED EXPERIENCE PRINCIPLE

The entire website must be role-based.

Role-based behavior applies to:

* Header
* Sidebar
* Mobile menu
* Bottom navigation
* Homepage CTAs
* Search actions
* Property detail actions
* Contact actions
* Requirement actions
* Pricing plans
* Profile sections
* Dashboard cards
* Admin access
* Banner ad access
* Subscription access
* Notifications
* Forms
* Empty states
* Error states
* Upgrade prompts

Example:

If user is logged in, show profile icon/avatar.

Do not show Login/Register as the main action to a logged-in user.

This is a global rule, not only a header rule.

---

# 7. DESIGN TARGET

The design target is:

```txt id="5wq1lr"
Premium Indian real estate marketplace UX quality with original My Gujarat Property branding.
```

The user experience should match the quality level users expect from top Indian real estate property listing websites.

Allowed reference direction:

* Search-first homepage
* Property discovery style
* Filter-rich search behavior
* Real estate card hierarchy
* Sticky contact CTA behavior
* Mobile app-like navigation
* City/locality browsing
* Login/register ease
* Role-based dashboard clarity
* Clean pricing visibility
* Admin operational clarity

Not allowed:

* Copying exact design from any website
* Copying brand colors
* Copying logo
* Copying images
* Copying exact text
* Copying CSS/code
* Copying proprietary layouts
* Using sample photos as final design source
* Requiring screenshot/video capture as part of design documentation

My Gujarat Property must remain original.

---

# 8. REMOVED DESIGN DEPENDENCIES

The regenerated documentation system must not depend on:

* Website screenshots
* Design screenshots
* Video recordings
* User sample UI photos
* Sample image folder
* Screenshot comparison reports
* Screenshot evidence
* Video evidence

Design must be driven by:

1. Product requirements
2. Role requirements
3. Mobile-first UX rules
4. Indian real estate marketplace behavior
5. Original My Gujarat Property brand
6. Actual implementation state
7. Real data availability
8. Admin-configurable rules

Claude may still visually inspect the website during manual browser QA, but screenshot/video capture is not required and must not be included as a mandatory task.

---

# 9. BRAND FEEL

My Gujarat Property should feel:

* Local but premium
* Gujarat-focused but scalable
* Professional but simple
* Real estate-specific
* Trust-first
* Clear and conversion-focused
* White-first
* Mobile-first
* Modern but not flashy
* Admin-controlled
* Practical for Indian users

Avoid:

* Dark dashboard template look
* Heavy gradients
* Neon colors
* Overdesigned luxury-only style
* Too many decorative cards
* Startup-style generic SaaS look
* Complex unnecessary animations
* Tiny text
* Cramped spacing
* Broken mobile layouts

---

# 10. WHITE-FIRST UI RULE

The website must use a white-first design.

Primary UI characteristics:

* White background
* Clean cards
* Light borders
* Soft shadows
* Clear typography
* Strong content hierarchy
* Proper spacing
* Clear CTAs
* Trust badges only when real
* Neutral surfaces
* Real estate image-forward layout
* Mobile-friendly spacing

Dashboard and admin panels should also be white-first and operational.

Do not use dark admin templates unless user explicitly asks later.

---

# 11. MOBILE-FIRST RULE

Most public users will come from mobile.

Therefore:

```txt id="xx4z5s"
Mobile is primary. Desktop is expanded.
```

Every public page, dashboard and form must be designed first for mobile.

Mobile must not feel like desktop squeezed into a small screen.

Mobile must feel app-like.

Important mobile rules:

* No horizontal scroll
* Header must fit
* Brand text must not wrap badly
* Buttons must be tappable
* CTA must be visible
* Property cards must be readable
* Forms must be step-based where needed
* Tables must become cards
* Popups must fit screen
* Bottom sheets must work
* Filter UI must be thumb-friendly
* Sticky CTA must not cover content
* Navigation must be clear
* Back icon should appear where needed

---

# 12. RESPONSIVE DEVICE SUPPORT

Every important UI must support:

## Small Mobile

* 320px
* 360px

## Normal Mobile

* 375px
* 390px

## Large Mobile

* 414px
* 430px

## Tablet

* 768px
* 834px

## Laptop

* 1024px
* 1280px

## Desktop

* 1366px
* 1440px

## Large Desktop

* 1536px and above if applicable

At minimum, every UI phase must check:

```txt id="p4lgxc"
360px
390px
430px
768px
1366px
```

If full matrix is not checked, report partial.

---

# 13. RESPONSIVE NON-NEGOTIABLES

The website must never show:

* Horizontal scrolling
* Text breaking awkwardly
* Logo split into two lines
* Header overlapping
* Header items overflowing
* Buttons going outside screen
* Cards squeezed unreadably
* Filters unusable on mobile
* Tiny touch targets
* Hidden CTAs
* Layout jump during loading
* Modal overflow
* Drawer overflow
* Bottom sheet broken
* Desktop tables on mobile
* Unreadable form inputs
* Sticky CTA covering last content
* Sidebar stuck open
* Footer overlap
* Map breaking layout

If any of these occur, the UI phase should be marked as FAIL or PARTIAL until fixed.

---

# 14. HEADER EXPERIENCE

Header must be designed separately for:

* Guest desktop
* Guest mobile
* Logged-in desktop
* Logged-in mobile
* Dashboard
* Admin
* Super Admin
* Role-specific profile mode

## Guest Header

Guest header should show:

* Logo
* City selector
* Search entry or search icon
* Main navigation
* Post Property CTA if enabled
* Login/Register button
* Menu/hamburger on mobile

## Logged-In Header

Logged-in header should show:

* Logo
* City selector
* Search entry or search icon
* Profile/avatar icon
* Active role or role switch entry if implemented
* Notification icon if implemented
* Message icon if implemented
* Dashboard link
* Menu/hamburger on mobile

Logged-in user must not see the main Login/Register button.

## Admin Header

Admin header should show:

* Admin/Super Admin identity
* Operational search
* Notifications/queues if implemented
* Profile
* Role/permission scope
* Quick actions where needed

---

# 15. HEADER NO-WRAP RULE

Brand name and important header text must not wrap badly.

Wrong:

```txt id="wt3nng"
My Gujarat
Property
```

Correct:

```txt id="8q6u6f"
My Gujarat Property
```

If screen is too small:

Use:

* Logo mark
* Short brand text
* Icon-only actions
* Ellipsis
* Reduced spacing
* Move lower priority items into menu

Do not allow ugly wrapping.

---

# 16. MOBILE NAVIGATION

Mobile navigation should feel like a real app.

Use where appropriate:

* Sticky compact header
* Bottom navigation
* Bottom action bar
* Hamburger menu
* Full-screen menu
* Drawer
* Bottom sheet
* Back icon
* Profile menu
* Role switch menu

Mobile bottom navigation may include role-based items.

Examples:

Guest:

* Home
* Search
* Post
* Pricing
* Login/Menu

Buyer/Tenant:

* Home
* Search
* Saved
* Requirements
* Profile

Owner:

* Dashboard
* Properties
* Leads
* Visits
* Profile

Broker:

* Dashboard
* Listings
* Requirements
* Leads
* Profile

Agency:

* Dashboard
* Team
* Leads
* Ads
* Profile

Builder:

* Dashboard
* Projects
* Leads
* Ads
* Profile

Admin:

* Queues
* Users
* Settings
* Reports
* Profile

Only show implemented and allowed items.

Do not show fake routes.

---

# 17. SIDEBAR, DRAWER, POPUP AND MODAL UX

All overlays must be polished.

Applies to:

* Mobile menu
* Login/register popup
* Role selection popup
* OTP popup
* City selector
* Search overlay
* Filter bottom sheet
* Contact form
* Lead form
* Image crop modal
* Payment popup
* Banner ad submit drawer
* Admin detail drawer
* Dashboard drawer
* Confirm modal

Required behavior:

* Open smoothly
* Close icon visible
* Outside click/tap closes overlay
* Escape key closes where applicable
* Back behavior on mobile where applicable
* No body scroll issue
* No content cut
* No horizontal scroll
* Proper z-index
* Focus returned where practical
* Touch targets large enough

User should not be forced to click only close icon.

---

# 18. HOMEPAGE EXPERIENCE

Homepage must be search-first.

First screen should quickly explain:

* What the website does
* Which city is selected
* What the user can search
* How to search
* How to post property
* How to post requirement
* How to login/register
* How to view pricing if needed

Homepage should not be filled with unnecessary text above the main search.

Homepage should support:

* City selector
* Buy/Rent/Commercial/Land/Plots/Projects/PG/Requirements tabs
* Search input
* Dynamic quick filters
* Main search CTA
* Post Property CTA
* Post Requirement CTA if enabled
* Pricing entry
* Banner ads carousel if active
* Featured properties if real
* New properties if real
* Projects if real
* Popular localities if real
* Blog/guide links if real
* Trust section
* Footer

No fake property cards.

No fake counts.

No fake city statistics.

If data is not available, hide section or show real empty state.

---

# 19. HOMEPAGE BANNER ADS UX

Homepage should support paid banner ads carousel.

This is a key new feature.

Banner ads are for:

* Agencies
* Real estate groups
* Brokers if enabled
* Builders if enabled
* Developers if enabled

Banner ads must be:

* Paid or plan/credit controlled
* Submitted from dashboard
* Reviewed by admin
* Approved before public display
* City-targeted
* Expiring after time limit
* Auto-hidden after expiry
* Archived after expiry
* Notified before expiry
* Shown in carousel
* Labeled as sponsored/ad
* Responsive across desktop/tablet/mobile

City-priority display:

* Rajkot users see Rajkot banners first.
* Ahmedabad users see Ahmedabad banners first.
* If local banners are not enough, show other city banners after local banners.
* If user city is unknown, use selected city, profile city or default Gujarat/global fallback.

Do not fake banner impressions/clicks.

Do not show unapproved ads.

Do not show expired ads.

---

# 20. SEARCH EXPERIENCE

Search must feel like a real Indian property listing website.

Homepage search must be powerful.

Search page or results page can exist, but search must begin from homepage.

Search should support:

* City
* District
* Taluka
* Village
* Area
* Locality
* Society
* Building
* Landmark
* Property ID
* RERA number
* Builder
* Broker
* Agency
* Project
* Keyword
* Budget
* BHK
* Property type
* Purpose
* Amenities
* Possession
* Land area
* Commercial type
* PG/Hostel type

Search must be city-first.

If user searches Rajkot property, Rajkot results should appear.

If no exact city results, show nearby/fallback with explanation.

---

# 21. DYNAMIC FILTER UX

Filters must change according to selected purpose and property type.

Do not show irrelevant filters.

Example:

If user selects Land:

Show:

* Land type
* Area
* Area unit
* Road access
* Zoning
* NA/agriculture if applicable
* Boundary
* Water/electricity if applicable

Hide:

* BHK
* Floor number
* Furnishing

If user selects Residential Flat:

Show:

* BHK
* Carpet/built-up area
* Floor
* Furnishing
* Parking
* Possession
* Amenities

If user selects Commercial:

Show:

* Shop/office/showroom/warehouse
* Frontage
* Floor
* Road width
* Parking
* Business suitability
* Rent/sale

If user selects PG/Hostel:

Show:

* Boys/girls/co-ed
* Sharing type
* Food included
* AC/non-AC
* Deposit
* Rules
* Availability

Filters must be real and connected.

Hide filters that are not implemented.

---

# 22. PROPERTY CARD UX

Property cards must be clean and informative.

Cards should show:

* Real image or safe placeholder
* Price/rent
* Title
* Location
* Property type
* BHK/area where relevant
* Source type: owner/broker/agency/builder
* Verification badge only if real
* Featured/sponsored badge only if real
* Short highlights
* Contact CTA
* Save button if implemented
* Share button if implemented
* Compare button if implemented
* Status where needed

Cards must work on mobile.

Do not show fake badges.

Do not show fake views.

Do not show fake ratings.

Do not show fake contact count.

---

# 23. PROPERTY DETAIL UX

Property detail page should be conversion-focused and trust-focused.

It should include:

* Gallery
* Price/rent
* Title
* Location
* Quick facts
* Description
* Amenities
* Property details
* Map state depending provider
* Seller/broker/agency/builder card
* Contact CTA
* WhatsApp CTA if enabled
* Lead form
* Site visit CTA if enabled
* Similar properties if real
* Report property
* Save/share if implemented
* Mobile sticky CTA
* Desktop sticky contact panel

Hidden contact must not leak.

Private documents must not be public.

---

# 24. LOGIN / REGISTER UX

Login/register should be popup-based for public users.

User should not be taken away unnecessarily.

Triggered from:

* Header Login/Register
* Mobile menu
* Contact button
* Save property
* Post property
* Post requirement
* Site visit
* Message
* Pricing purchase
* Banner ad purchase
* Dashboard access

Intent must be preserved.

Examples:

If user clicks Contact Property, then logs in, continue contact flow.

If user clicks Post Property, then registers, continue post property flow.

If user clicks Pricing plan, then logs in, continue plan purchase.

---

# 25. OTP UX

OTP UI must be mobile-friendly.

Requirements:

* Numeric input
* OTP autofill support
* Paste full OTP support
* Resend timer
* Wrong OTP error
* Expired OTP state
* Provider missing state
* Dev OTP state only in development
* Large touch-friendly input
* Clear back button
* Clear phone number edit option

No fake OTP success in production.

---

# 26. ROLE-BASED PROFILE UX

Profile should not be generic.

Each role profile must show different sections.

Profile should include:

* Basic info
* Avatar/logo/crop
* Active role
* Plan/subscription
* Verification status
* Role-specific details
* Role change request
* Email verification
* Phone verification
* Security/session settings
* Notification preferences

Role-specific public profile pages must exist where useful:

* Broker public profile
* Agency public profile
* Builder public profile
* Project profile
* Owner public info if allowed

---

# 27. ROLE CHANGE UX

Role change must be approval-based.

User can request new role from profile.

Role change request should show:

* Current role
* Requested role
* Required details
* Required documents if any
* Plan impact
* Subscription impact
* Approval status
* Admin decision
* Rejection reason
* Resubmit option

If current role has active plan, show clear rules.

Do not silently change role.

---

# 28. DASHBOARD UX

Dashboards must be role-specific.

Every dashboard should answer:

* What needs my attention?
* What changed today?
* Which leads are new?
* Which listings need action?
* Which visits are pending?
* Which plan limit is near expiry?
* Which ads/promotions are active?
* What should I do next?

Dashboard design should use:

* Cards
* Metrics only if real
* Quick actions
* Priority tasks
* List/cards
* Mobile table-to-card
* Role-based sidebar
* Role-based bottom nav where useful
* Empty states
* Loading states
* Error states

No fake metrics.

No fake revenue.

No fake leads.

---

# 29. ADMIN UX

Admin panel is operational, not decorative.

Admin must manage:

* Users
* Roles
* Permissions
* Properties
* Projects
* Requirements
* Leads
* Site visits
* Banner ads
* Subscriptions
* Payments
* SEO
* CMS
* Blogs
* Support
* Reports
* Verification
* Fraud
* Settings
* Providers
* Feature flags
* Audit logs

Admin UI should be:

* Clean
* White-first
* Queue-first
* Table on desktop
* Card-based on mobile
* Filterable
* Searchable
* Drawer-based for details
* Permission-aware

No fake admin settings.

No fake admin metrics.

---

# 30. SUPER ADMIN UX

Super Admin must control the platform.

Super Admin should manage:

* Platform settings
* Branding
* Cities
* Locations
* Feature flags
* Provider modes
* WhatsApp mode
* Map mode
* OTP provider
* Email provider
* API/database/storage limits if available
* Session timeout
* Payment settings
* Subscription plans
* Banner ads pricing
* Banner ads duration
* SEO settings
* CMS settings
* Admin/staff access
* Audit logs
* Maintenance mode

If a setting is visible, it must actually work.

---

# 31. SUBSCRIPTION AND PRICING UX

Pricing/subscription must be visible to guests and logged-in users.

Guests can view plans.

Purchase requires login.

Plan display should be role-based.

Examples:

Guest sees role tabs or plan groups.

Owner sees owner plans.

Broker sees broker plans.

Agency sees agency plans.

Builder sees builder plans.

Banner ads show separate pricing if enabled.

Pricing page should be mobile-friendly.

No fake payment success.

No fake active plan.

---

# 32. IMAGE UPLOAD UX

Every upload field must show:

* Recommended size
* Recommended ratio
* Max file size
* Accepted file types
* Preview
* Crop option where relevant
* Replace/delete option
* Error if invalid
* Auto-fit behavior where allowed

Banner ads should support separate images for:

* Desktop
* Tablet
* Mobile

Profile and logo upload should support crop.

Property gallery should support reorder.

Documents should be separate from media.

Private documents must not be public.

---

# 33. LOCATION UX

Location selection should be smooth.

No page refresh.

Use cascading selects:

* State
* District
* Taluka
* City/Village
* Area
* Locality
* Society
* Building
* Landmark

If missing:

* Allow custom request
* Allow manual entry where safe
* Send to admin review if needed

Location should support:

* Search
* SEO
* Property posting
* Requirement posting
* Broker/agency operating areas
* Banner ads targeting
* Admin city controls

---

# 34. SEO UX

SEO should help users coming from Google.

Example Google intents:

* Rajkot property
* Property sale in Rajkot
* Best property in Rajkot
* 2 BHK flat in Rajkot
* Plot for sale in Ahmedabad
* Commercial property in Surat

Clicking SEO result should open a relevant city/property page.

SEO pages should have:

* Dynamic title
* Meta description
* H1
* Intro text
* Real listings
* Filters
* Internal links
* Breadcrumbs
* Schema
* Sitemap
* Canonical URL

Do not create low-value fake pages.

---

# 35. NOTIFICATION UX

Notifications should be useful.

Possible notification triggers:

* OTP
* Login alert
* Role approval
* Role rejection
* Property approved
* Property rejected
* Requirement approved
* Proposal received
* Lead received
* Site visit requested
* Site visit approved/rejected
* Subscription expiry
* Banner ad approval
* Banner ad rejection
* Banner ad expiry
* Payment status
* Verification status
* Support response

If external providers are not configured, use in-app only if implemented.

Do not fake external send logs.

---

# 36. EXPIRY AND ARCHIVE UX

Time-limited items must show status.

Applies to:

* Properties
* Requirements
* Subscriptions
* Trials
* Boosts
* Banner ads
* Featured placements
* Sponsored profiles

Required states:

* Draft
* Pending
* Active
* Scheduled
* Expiring soon
* Expired
* Hidden
* Archived
* Rejected
* Renewed

Users should understand what happened and what to do next.

Admin should be able to control or override where allowed.

---

# 37. WHATSAPP UX

WhatsApp contact must support:

* Free wa.me mode
* API mode

If free mode:

* Open WhatsApp link.

If API mode:

* Use configured API.

Admin/Super Admin decides active mode.

Only one active required mode should be selected when WhatsApp is enabled.

Do not fake API send.

If API missing, show setup-required state or fallback only if configured.

---

# 38. MAP UX

Map should support:

* Disabled mode
* Free embed/trial mode
* Premium API mode

Admin/Super Admin chooses mode.

If API missing, do not show fake interactive map.

If map disabled, hide or show unavailable state.

Map should not slow down homepage unnecessarily.

Load maps only where useful.

---

# 39. LEAD UX

Lead form should reduce typing.

If user has profile number:

Show:

```txt id="3zxwfq"
Use my current number
```

Also allow:

```txt id="kzok9t"
Use different number
```

If user uses different number, receiver dashboard must show that alternate number was used.

Do not overwrite profile number unless user confirms.

Lead receiver should see:

* Name
* Phone used
* Alternate number badge if applicable
* Source
* Property/requirement/project
* Message
* Status
* Follow-up actions

---

# 40. ACCESSIBILITY UX

UI must be accessible.

Requirements:

* Readable font size
* Visible focus
* Real buttons
* Real links
* Form labels
* Error messages
* Icon labels
* Keyboard support where possible
* Touch targets around 44px or more
* Contrast readable
* Status not color-only

---

# 41. PERFORMANCE UX

Performance is part of design.

Rules:

* Fast first screen
* Optimized images
* Lazy-load below fold
* Lazy-load maps
* Avoid heavy homepage scripts
* Avoid unnecessary animations
* Use skeleton loading
* Avoid layout shift
* Paginate long lists
* Keep filters responsive
* Avoid loading admin/dashboard bundles publicly

---

# 42. EMPTY / ERROR / LOADING UX

Every major page must handle:

* Loading state
* Empty state
* Error state
* Success state
* Disabled state
* Permission denied state
* Provider missing state
* Expired state
* Archived state

No blank screens.

No broken routes.

No dead buttons.

No fake success.

---

# 43. TRUST AND TRANSPARENCY UX

Trust features should be real.

May include:

* Listing source tag
* Verification badge
* RERA info
* Brokerage info
* Contact visibility
* Report listing
* Admin moderation
* Verified broker/agency/builder
* Property status
* Expiry status
* Sponsored label
* Ad label

Never show fake verification.

Never show fake ratings.

Never show fake reviews.

Never show fake trust score.

---

# 44. CONTENT TONE

Website copy should be:

* Clear
* Simple
* Indian real estate-friendly
* Gujarat-focused
* Trust-focused
* Not too long
* Not fake hype
* Not confusing

Avoid:

* Overpromising
* Fake “No.1” claims unless verified
* Fake user numbers
* Fake property counts
* Fake success stories
* Misleading price claims
* Too much technical language

---

# 45. LANGUAGE STRATEGY

Primary UI can be English.

Future-ready multilingual support can include:

* English
* Gujarati
* Hindi

Do not implement fake language switch if translations do not exist.

If language selector is visible, it must work or clearly be future/disabled.

---

# 46. DESIGN SYSTEM REQUIREMENT

The project should use a consistent design system.

Required component categories:

* Buttons
* Inputs
* Selects
* Search inputs
* Cards
* Property cards
* Requirement cards
* Lead cards
* Dashboard cards
* Badges
* Status badges
* Modals
* Drawers
* Bottom sheets
* Toasts
* Skeletons
* Empty states
* Error states
* Upload components
* Image crop components
* Filter chips
* Pagination
* Tabs
* Mobile bottom nav
* Dashboard sidebar

Avoid duplicate random components.

---

# 47. FORM UX

Forms must be simple and step-based where needed.

Important forms:

* Register
* OTP
* Profile completion
* Role upgrade
* Property posting
* Requirement posting
* Banner ad submission
* Lead/contact
* Site visit booking
* Admin approval
* Plan purchase
* Support ticket

Mobile forms should use:

* Steps
* Progress indicator
* Back button
* Sticky next/submit CTA
* Large inputs
* Clear validation
* Save draft where useful

---

# 48. ADMIN APPROVAL UX

Approval workflows must be clear.

Applies to:

* Property
* Project
* Requirement
* Role upgrade
* Verification
* Banner ads
* Reviews if implemented
* CMS if workflow enabled
* Location requests

Admin should see:

* Submitted data
* User details
* Risk signals if real
* Documents/media
* Approve
* Reject
* Request changes
* Reason field
* Audit log

User should see status and rejection reason.

---

# 49. NO FAKE UI DESIGN RULE

Visual polish must not hide fake functionality.

Do not create UI that looks complete but does nothing.

If not implemented:

* Hide
* Disable with reason
* Mark setup-required
* Mark future in docs

Examples:

* Do not show WhatsApp API sent if only wa.me exists.
* Do not show Google Maps interactive if API missing.
* Do not show payment success without verification.
* Do not show admin setting if it does not affect system.
* Do not show banner ad impressions if not tracked.
* Do not show role approval if admin workflow missing.

---

# 50. FINAL DESIGN ACCEPTANCE RULE

A page or feature passes master UX only if:

* It follows mobile-first design.
* It has no horizontal scroll.
* It is role-aware.
* It uses real or safe empty data.
* It does not fake production behavior.
* It has loading/empty/error states.
* It has clear CTAs.
* It respects permissions.
* It supports responsive layout.
* It fits My Gujarat Property brand.
* It does not rely on removed screenshot/video/sample image instructions.
* It can be verified through manual browser interaction.

---

# 51. RELATION TO OTHER DOCUMENTS

This document is master product and UX direction.

Detailed behavior is defined in specific documents:

* Feature/page/role matrix
* Public website and homepage UX
* Search and filters
* SEO
* Auth and OTP
* Role profile
* Location
* Property posting
* Property detail/contact
* Requirement marketplace
* Dashboards
* Admin/Super Admin
* Banner ads
* Subscription/payment
* Provider modes
* Database/RBAC/security
* Notifications/expiry
* Verification/fraud
* CMS/legal
* Feature registry
* Manual verification prompt
* Claude phase prompts

Claude must use the correct detailed document for actual implementation.

Do not rely on this master file alone for coding.

---

# 52. END OF FILE

This file defines the master product, design, UX and responsive direction for My Gujarat Property.

Every design and development phase must follow this file.

Nothing from uploaded docs or user chat instructions should be skipped.

The design must be mobile-first, role-based, original, real-data-driven, no-fake, admin-controlled and ready for Gujarat-first real estate marketplace launch.
