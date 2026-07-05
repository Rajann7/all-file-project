# MY GUJARAT PROPERTY

# PUBLIC WEBSITE, HOMEPAGE, HEADER, SIDEBAR, MOBILE APP-LIKE UX SPEC

## FILE NAME

`03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete public website, homepage, header, sidebar, mobile navigation and mobile app-like user experience for **My Gujarat Property**.

This file must be read before building or redesigning:

* Homepage
* Public website shell
* Guest header
* Logged-in header
* Role-based header
* Mobile header
* Desktop header
* City selector
* Search entry
* Login/Register popup trigger
* Mobile hamburger/sidebar
* Mobile bottom navigation
* Homepage hero/search
* Homepage banner ads carousel placement
* Homepage quick filters
* Homepage public sections
* Pricing entry
* Public footer
* Public page layout
* Overlay close behavior
* Back navigation behavior
* Responsive public UI

This file focuses on public-facing user experience.

Detailed search logic, SEO, auth, property cards, banner ads, pricing, provider settings and dashboards are handled in their own dedicated documents, but this file defines how they appear in the public website shell.

---

# 2. CORE PUBLIC UX PRINCIPLE

The public website must be:

* Search-first
* Mobile-first
* Fast
* Clean
* Real estate marketplace style
* Gujarat-localized
* Role-aware
* Trust-focused
* Conversion-focused
* White-first
* App-like on mobile
* Easy for Indian users
* No fake UI
* No horizontal scroll

The homepage should immediately help users answer:

1. Where am I searching?
2. What can I search?
3. How can I find a property?
4. How can I post property?
5. How can I post requirement?
6. How can I login/register?
7. How can I view pricing?
8. Which city is selected?
9. Which role/action is relevant to me?

The website must not feel like:

* A basic landing page
* A generic SaaS template
* A broken responsive layout
* A desktop website squeezed into mobile
* A dark admin template
* A classified board with random cards
* A fake demo UI with fake counts

---

# 3. DESIGN TARGET

The public UI must feel like a premium Indian real estate property listing platform.

It should follow the quality level of leading property portals in behavior and polish, but must use original My Gujarat Property branding and product logic.

Allowed behavior inspiration:

* Search-first homepage
* City selector
* Buy/rent/commercial/plot/project tabs
* Property discovery flow
* Mobile header compactness
* Mobile drawer polish
* Filter bottom sheet behavior
* Sticky mobile CTAs
* Clean cards
* Real estate trust hierarchy
* Pricing visibility
* Public profile browsing

Not allowed:

* Copying any website’s logo
* Copying exact colors
* Copying exact design
* Copying exact layout
* Copying exact CSS/code
* Copying images/assets
* Copying sample screenshots
* Depending on screenshot/video/sample photo references

The new documentation system must not require sample photos, screenshot capture or video capture.

---

# 4. PUBLIC WEBSITE ROUTES

Recommended public routes:

```txt id="i1njbn"
/                         Homepage
/search                    Search results
/properties/[slug]          Property detail
/projects/[slug]            Project detail
/city/[city-slug]           City page
/city/[city-slug]/[type]    City + property type SEO page
/locality/[city-slug]/[locality-slug]
/brokers                    Broker directory
/brokers/[slug]             Broker profile
/agencies                   Agency directory
/agencies/[slug]            Agency profile
/builders                   Builder directory
/builders/[slug]            Builder profile
/requirements               Public requirements if enabled
/pricing                    Pricing/subscription plans
/blog                       Blog listing
/blog/[slug]                Blog detail
/faq                        FAQ
/about                      About
/contact                    Contact
/support                    Help/support
/privacy                    Privacy Policy
/terms                      Terms
/refund-policy              Refund Policy if payment enabled
/listing-policy             Listing Policy
/ad-policy                  Advertisement Policy
/login                      Full page fallback
/register                   Full page fallback
/verify-otp                 Full page fallback
/unauthorized               Unauthorized state
/account-suspended          Suspended state
/account-banned             Banned state
```

The primary public auth UX should be popup/modal based.

Direct `/login`, `/register` and `/verify-otp` routes should exist as fallback for direct URL access.

Admin login must not be mixed with public login/register.

---

# 5. PUBLIC WEBSITE SHELL

Every public page should share a consistent public shell.

Public shell includes:

1. Header
2. City context
3. Main content
4. Mobile bottom navigation if enabled
5. Footer
6. Toast area
7. Modal/drawer/bottom-sheet provider
8. Login/register popup provider
9. Search overlay provider if needed
10. Feature flag awareness
11. Role-aware UI awareness

The shell must detect:

* Guest state
* Logged-in state
* Active role
* Current city
* Feature flags
* Provider mode
* Subscription visibility
* Public route type

The shell must not show broken actions.

---

# 6. HEADER TYPES

The platform needs different header states:

1. Guest desktop header
2. Guest mobile header
3. Logged-in desktop header
4. Logged-in mobile header
5. Role-based dashboard header
6. Admin header
7. Super Admin header
8. Search results sticky header
9. Property detail compact header
10. Mobile full-screen search header

This document covers public website header.

Dashboard and admin headers are detailed in dashboard/admin docs but must follow the same role-aware principle.

---

# 7. GUEST DESKTOP HEADER

Guest desktop header should include:

* Logo
* Brand name
* City selector
* Search entry or search shortcut
* Navigation links
* Pricing link
* Post Property CTA
* Login/Register button
* Menu items only if implemented

Recommended nav links:

* Buy
* Rent
* Commercial
* Plots/Land
* Projects
* PG/Hostel if enabled
* Buyer Requirements if enabled
* Pricing
* Blog/Guides
* Help

Rules:

* Do not show fake links.
* Do not use `href="#"`.
* Hide unimplemented nav items.
* If a feature is disabled by Super Admin, hide or disable safely.
* Header text must not wrap badly.
* Header must stay clean and not overloaded.

---

# 8. GUEST MOBILE HEADER

Guest mobile header must be compact.

Mobile header should include:

* Compact logo or logo mark
* City selector
* Search icon or compact search entry
* Login/Register or profile/menu entry depending space
* Hamburger menu
* Post Property CTA inside menu if space is limited

Priority order on small screens:

1. Logo mark
2. City selector
3. Search icon
4. Menu icon
5. Login/Register inside menu
6. Post Property inside menu

Recommended height:

```txt id="bir4ht"
56px to 64px
```

Header must not become two rows unless intentionally used on search page.

No horizontal scroll.

No logo wrapping.

No overlapping icons.

---

# 9. LOGGED-IN DESKTOP HEADER

Logged-in desktop header should include:

* Logo
* City selector
* Search entry
* Main navigation
* Active role indicator if useful
* Dashboard link
* Notification icon if implemented
* Message icon if implemented
* Profile/avatar menu
* Post Property or role-relevant CTA

Logged-in user must not see the main Login/Register button.

Profile/avatar menu should include:

* User name
* Active role
* Profile completion
* Dashboard
* Role switch if implemented
* Subscription/Plan
* Saved properties if buyer/tenant
* My Requirements if buyer/tenant
* My Listings if owner/broker/agency/builder
* Banner Ads if role eligible
* Settings
* Logout

Only show implemented and permitted items.

---

# 10. LOGGED-IN MOBILE HEADER

Logged-in mobile header should include:

* Logo or logo mark
* City selector
* Search icon
* Profile/avatar icon
* Notification icon if implemented and space allows
* Hamburger/menu if needed

Small width priority:

1. Logo mark
2. City selector
3. Search icon
4. Profile/avatar
5. Hamburger/menu

If notification/message icons are not implemented, do not show them.

No fake notification badges.

No fake unread counts.

---

# 11. ROLE-BASED HEADER RULE

Header must change according to role.

Example role-based CTA:

* Guest: Login/Register, Post Property
* Buyer: Saved, Requirements, Profile
* Tenant: Saved Rentals, Requirements, Profile
* Owner: My Properties, Post Property
* Broker: Listings, Requirements Feed, Leads
* Agency: Agency Dashboard, Leads, Banner Ads
* Agent: Assigned Leads, Tasks
* Builder: Projects, Leads, Banner Ads
* Admin: Admin Panel
* Super Admin: Super Admin Panel

Do not show irrelevant actions.

Do not show business dashboard link to a buyer unless that user has that role.

Do not show admin entry to normal users.

---

# 12. HEADER NO-WRAP RULE

Header text must not break awkwardly.

Wrong:

```txt id="d3pfk1"
My Gujarat
Property
```

Correct:

```txt id="t5zwr1"
My Gujarat Property
```

If screen is small:

* Use compact logo
* Use logo mark only
* Shorten brand text
* Use `white-space: nowrap`
* Reduce gap
* Hide lower priority actions
* Move actions into hamburger
* Use icon-only actions

Header must be manually checked on:

```txt id="x2h4qu"
320px
360px
375px
390px
430px
768px
1366px
```

---

# 13. HEADER STICKY BEHAVIOR

Public header should be sticky on most public pages.

Rules:

* Header remains visible on scroll.
* Header has solid background.
* Header gets subtle border/shadow after scroll if useful.
* Header must not cover important content.
* Header must not jump.
* Header must not flicker.
* Header height should remain stable.
* Header must respect safe area on mobile.

On property detail pages, header may be compact and supported by sticky bottom CTA.

On search results pages, search bar may become sticky under header.

---

# 14. CITY SELECTOR UX

City selector is a core feature.

City selector should be visible in header/homepage.

It should support:

* Current selected city
* Search city
* Popular Gujarat cities
* Recently selected city
* Detect location if implemented and permission granted
* Use profile city if logged in
* Use IP/location estimate only as fallback
* Manual city selection always allowed
* Clear fallback if city unknown

City selector should never block the user.

If location permission denied, user can still select city manually.

City selector should affect:

* Homepage search
* Search results
* Banner ads priority
* City SEO pages
* Locality suggestions
* Property suggestions
* Requirement feed
* Broker/agency/builder suggestions if implemented

Recommended Gujarat city examples:

* Ahmedabad
* Surat
* Rajkot
* Vadodara
* Jamnagar
* Bhavnagar
* Gandhinagar
* Junagadh
* Morbi
* Anand
* Nadiad
* Mehsana
* Bhuj
* Gandhidham
* Porbandar
* Bharuch
* Vapi
* Navsari
* Valsad
* Palanpur
* Amreli
* Surendranagar
* Botad
* Veraval
* Godhra
* Dahod
* Patan
* Modasa
* Himmatnagar

Detailed location hierarchy belongs to location document.

---

# 15. CITY SELECTOR MOBILE BEHAVIOR

On mobile, city selector can open as:

* Bottom sheet, or
* Full-screen search sheet

It should include:

* Search input
* Current city
* Popular cities
* Recent cities
* Use current location if implemented
* Manual close
* Outside tap close where applicable
* Back icon
* No horizontal scroll

City selector must not require page refresh.

After city selection, homepage/search context updates smoothly.

---

# 16. LOGIN/REGISTER ENTRY

Public header must have one clear auth entry.

Button text can be:

```txt id="g7mli6"
Login / Register
```

or equivalent.

Clicking opens a popup/modal.

Popup must allow:

* Login
* Register
* Role-based registration
* OTP
* Intent preservation

New user cannot directly login if not registered.

Registration must include role selection.

Admin login must not appear in this public popup.

If user is logged in, this button must be replaced with profile/avatar.

---

# 17. PUBLIC LOGIN/REGISTER POPUP RULE

Login/register popup should open from:

* Header
* Mobile menu
* Contact button
* Save button
* Post Property
* Post Requirement
* Pricing purchase
* Banner ad purchase
* Site visit
* Message action
* Dashboard access

Popup must preserve intent.

Examples:

If user clicks Contact on property and then logs in, user should return to same property/contact flow.

If user clicks Post Property and then registers, user should continue post property flow.

If user clicks banner ad purchase and then logs in, user should continue banner ad flow if role eligible.

---

# 18. MOBILE HAMBURGER / SIDEBAR MENU

Mobile menu must feel app-like and polished.

It can be:

* Left drawer
* Right drawer
* Full-screen sheet

Recommended:

* Right drawer or full-screen sheet for public mobile

Behavior:

* Smooth open
* Overlay background
* Close button
* Outside tap closes
* Back support where applicable
* Scrollable content
* No page horizontal scroll
* No hidden buttons
* No broken z-index

---

# 19. GUEST MOBILE MENU CONTENT

Guest menu should show:

1. Login/Register card
2. City selector
3. Buy
4. Rent
5. Commercial
6. Land / Plots
7. Projects
8. PG / Hostel if enabled
9. Buyer Requirements
10. Post Property
11. Post Requirement
12. Pricing
13. Blog / Guides
14. Help / Support
15. About
16. Contact
17. Language selector if implemented
18. Legal links

Guest login card text example:

```txt id="lir4z9"
Login to save properties, contact sellers and post requirements.
```

Do not show fake user data in guest menu.

---

# 20. LOGGED-IN MOBILE MENU CONTENT

Logged-in mobile menu should show:

1. User avatar
2. User name
3. Active role
4. Profile completion
5. Dashboard link
6. Role switch if implemented
7. Role-specific menu
8. Saved properties if buyer/tenant
9. Requirements if buyer/tenant
10. My listings if owner/broker/agency/builder
11. Leads if business role
12. Site visits
13. Messages if implemented
14. Notifications if implemented
15. Subscription / Plan
16. Banner Ads if role eligible
17. Profile Settings
18. Account/Security Settings
19. Logout

Do not show guest-only menu after login.

---

# 21. ROLE-BASED MOBILE MENU

## Buyer Menu

* Buyer Dashboard
* Saved Properties
* Saved Searches
* Compare
* My Requirements
* Proposals
* Site Visits
* Messages
* Notifications
* Profile
* Subscription

## Tenant Menu

* Tenant Dashboard
* Saved Rentals
* Rental Requirements
* PG Searches
* Site Visits
* Messages
* Notifications
* Profile
* Subscription

## Owner Menu

* Owner Dashboard
* My Properties
* Post Property
* Leads
* Contact Requests
* Site Visits
* Messages
* Plan
* Profile
* Support

## Broker Menu

* Broker Dashboard
* Listings
* Add Listing
* Requirements Feed
* Proposals
* Leads
* Lead Pipeline
* Site Visits
* Messages
* Plan
* Broker Profile
* Verification

## Agency Menu

* Agency Dashboard
* Agency Profile
* Agents
* Listings
* Requirements
* Leads
* Site Visits
* Banner Ads
* Subscription
* Verification
* Settings

## Agent Menu

* Agent Dashboard
* Assigned Leads
* Assigned Listings
* Assigned Visits
* Tasks
* Messages
* Profile

## Builder Menu

* Builder Dashboard
* Builder Profile
* Projects
* Units
* Leads
* Site Visits
* Banner Ads
* Subscription
* Verification

## Admin Menu

* Admin Dashboard
* Users
* Properties
* Requirements
* Projects
* Ads
* Verification
* Support
* CMS
* SEO
* Settings

## Super Admin Menu

* Super Admin Dashboard
* Platform Settings
* Feature Flags
* Providers
* Roles
* Permissions
* Subscriptions
* Payments
* Banner Ads
* SEO
* Locations
* Audit Logs
* System Health

Only show items the user has permission to access.

---

# 22. MOBILE BOTTOM NAVIGATION

Mobile bottom navigation can be used for app-like experience.

It should be role-aware.

Do not show too many items.

Recommended max:

```txt id="idfo7d"
4 to 5 primary items
```

## Guest Bottom Nav Example

* Home
* Search
* Post
* Pricing
* Menu

## Buyer Bottom Nav Example

* Home
* Search
* Saved
* Requirements
* Profile

## Tenant Bottom Nav Example

* Home
* Rent/PG
* Saved
* Requirements
* Profile

## Owner Bottom Nav Example

* Dashboard
* Properties
* Leads
* Visits
* Profile

## Broker Bottom Nav Example

* Dashboard
* Listings
* Requirements
* Leads
* Profile

## Agency Bottom Nav Example

* Dashboard
* Listings
* Leads
* Ads
* Profile

## Builder Bottom Nav Example

* Dashboard
* Projects
* Leads
* Ads
* Profile

## Admin Bottom Nav Example

* Queues
* Users
* Ads
* Settings
* Profile

Bottom nav must not cover page content.

Add bottom padding to pages when bottom nav is present.

---

# 23. BACK ICON RULE

Use a back icon where users need to return to a previous flow.

Examples:

* Mobile search overlay
* City selector
* Login/register popup steps
* OTP step
* Role selection step
* Property detail from search
* Full-screen image gallery
* Property posting stepper
* Requirement posting stepper
* Filter bottom sheet
* Profile edit
* Dashboard nested detail
* Admin review drawer

Back behavior must be logical.

Do not trap users.

---

# 24. HOMEPAGE FIRST SCREEN

On mobile first screen should show:

1. Compact header
2. City selector
3. Search-first hero
4. Intent tabs
5. Main search input
6. Quick filters
7. Primary CTA
8. Secondary CTAs
9. Banner ads carousel if active and not harming search priority

Important:

Search must remain primary.

Banner ads must not push search too far down on mobile.

If banner ads are placed near hero, make sure first screen still explains search clearly.

---

# 25. HOMEPAGE HERO

Hero should be clean.

Hero may include:

* Short headline
* City-aware search
* Search tabs
* Search input
* Quick filters
* Primary Search CTA
* Post Property CTA
* Post Requirement CTA
* Pricing link

Avoid long paragraphs.

Example tone:

```txt id="2lz31l"
Find properties in Gujarat faster.
```

or:

```txt id="zj8js1"
Search homes, plots, commercial spaces and projects in Gujarat.
```

Do not use fake claim like “No.1 platform” unless verified.

---

# 26. HOMEPAGE SEARCH ENTRY

Search entry should support:

* City
* Locality
* Society
* Project
* Builder
* Broker
* Agency
* Property ID
* RERA number
* Keyword
* Budget intent
* BHK intent
* Property type intent

Example queries:

```txt id="u8bkjs"
Rajkot 3 BHK
Property sale in Rajkot
Plot in Ahmedabad
Commercial shop in Surat
Girls PG Vadodara
Kalawad Road flat
RERA number
PROP-12345
```

Autocomplete must be real if shown.

If autocomplete is not implemented, show simple search input without fake suggestions.

---

# 27. HOMEPAGE SEARCH TABS

Required intent tabs:

* Buy
* Rent
* Commercial
* Land / Plots
* Projects
* PG / Hostel
* Buyer Requirements

Mobile behavior:

* Horizontal scroll if needed
* Clear active tab
* No ugly wrapping
* Large touch target
* Selected tab changes filters

If a tab is not implemented, hide it.

Do not show dead tabs.

---

# 28. HOMEPAGE QUICK FILTERS

Quick filters should change by selected tab.

Buy example:

* BHK
* Budget
* Property Type
* Ready to Move
* Owner/Broker
* Verified

Rent example:

* Rent budget
* Deposit
* Furnishing
* Family/Bachelor
* Move-in
* Property Type

Commercial example:

* Shop
* Office
* Showroom
* Warehouse
* Budget
* Area

Land/Plot example:

* Plot
* Agricultural Land
* NA Land
* Area
* Road Access
* Budget

PG/Hostel example:

* Boys
* Girls
* Co-living
* Sharing
* Food
* AC

Projects example:

* Builder
* Project Status
* Possession
* Unit Type
* Budget

Buyer Requirements example:

* Requirement Type
* City
* Budget
* Property Type
* Urgency

Do not show irrelevant quick filters.

---

# 29. HOMEPAGE BANNER ADS PLACEMENT

Homepage may include banner ads carousel.

Placement options:

1. Below search hero
2. Between hero and featured sections
3. After first content block
4. City-specific sponsored section

Recommended:

* On mobile, do not place huge banner before search.
* On desktop, banner can be placed near hero without hurting search.
* Use responsive size.
* Use sponsored label.
* Use carousel only if active approved ads exist.
* Hide if no active ads.

Banner ad carousel should prioritize user city.

Example:

If selected city = Rajkot:

1. Rajkot active approved ads
2. Nearby city ads if configured
3. Gujarat-wide ads
4. Other city ads

If selected city = Ahmedabad:

1. Ahmedabad active approved ads
2. Nearby city ads if configured
3. Gujarat-wide ads
4. Other city ads

Do not show pending/rejected/expired ads.

---

# 30. HOMEPAGE PUBLIC SECTIONS

Homepage may include these sections only if real data exists or safe empty state is planned:

* Banner ads carousel
* Popular searches
* Featured properties
* Latest properties
* Verified properties
* Projects
* Popular localities
* Top brokers
* Top agencies
* Builders
* Buyer requirements if enabled
* City guides
* Blog/guides
* Pricing preview
* Trust and safety
* How it works
* Footer SEO links

No fake counts.

No fake ratings.

No fake “top” profiles unless ranking is real/admin controlled.

---

# 31. HOMEPAGE PRICING ENTRY

Pricing must be visible to:

* Guests
* Logged-in users

Homepage can show:

* Pricing link in header
* Pricing card/section
* “View Plans” CTA
* Launch offer if active
* Role-based plan groups

If user is guest and clicks buy plan:

* Open login/register popup.
* Preserve selected plan.
* After login/register, continue plan purchase if role matches.
* If role does not match, show role selection/upgrade flow.

Do not fake active plan.

---

# 32. POST PROPERTY CTA

Post Property CTA should be visible but smart.

Guest clicks Post Property:

1. Open login/register popup.
2. Ask role during registration.
3. Continue property posting after OTP success.
4. If user chooses Buyer/Tenant only, explain owner/broker role required or allow role upgrade.

Logged-in buyer clicks Post Property:

* Ask to request Owner/Broker/Agency/Builder role if not available.
* Do not silently allow wrong role.

Logged-in owner/broker/agency/builder:

* Continue to property posting.

---

# 33. POST REQUIREMENT CTA

Post Requirement CTA should be available for demand-side users.

Guest clicks Post Requirement:

1. Open login/register popup.
2. Register as Buyer/Tenant.
3. OTP verification.
4. Continue requirement form.

Logged-in owner/broker trying to post requirement:

* Ask to switch/request buyer/tenant role if multi-role is supported.
* Do not post as broker unless buyer intent is allowed.

---

# 34. SAVE PROPERTY PUBLIC FLOW

Guest clicks Save:

1. Open login/register popup.
2. Preserve property ID.
3. After login, save property.
4. Show success toast.
5. Keep user on same page.

Logged-in user clicks Save:

* Save immediately.
* Toggle saved state.
* Show toast.

If save feature disabled, hide button.

---

# 35. CONTACT CTA PUBLIC FLOW

Contact CTA behavior depends on contact visibility mode.

Possible modes:

* Public Contact
* Login Required
* Lead Form Required
* Request Contact
* Premium Contact Only
* Hidden Contact

Guest click contact:

* If public contact allowed, show safe public contact.
* If login required, open login/register popup.
* If lead form required, open lead form after login if needed.
* If request contact, open request flow after login.
* If premium required, show plan/permission state.
* If hidden, show unavailable/safe state.

Never expose hidden phone/email in public query.

---

# 36. PUBLIC FOOTER

Footer should include:

* Logo
* Short description
* City links
* Property type links
* Public pages
* Pricing
* Blog
* Help
* Contact
* Social links if real
* Legal links
* Listing policy
* Ad policy
* Privacy
* Terms

Footer should not be too heavy on mobile.

Use accordion sections on mobile if needed.

Do not include fake social links.

---

# 37. PUBLIC PAGE LAYOUTS

Public page layouts should use consistent spacing.

Recommended structure:

```txt id="d6zx3c"
Header
Main content
Optional sticky CTA / bottom nav
Footer
```

Page container should have max-width on desktop.

Mobile should use full-width cards with safe padding.

Avoid content stretching too wide on large desktop.

---

# 38. PUBLIC STATIC PAGES

Static pages include:

* About
* Contact
* FAQ
* Help
* Privacy
* Terms
* Refund Policy
* Listing Policy
* Ad Policy

Static pages must be:

* Clean
* Readable
* Mobile-friendly
* SEO-ready
* CMS-editable if CMS implemented
* No fake claims
* No unsupported legal promises

If payment is enabled, refund policy should exist.

If banner ads are enabled, ad policy should exist.

---

# 39. PUBLIC PROFILE ENTRY POINTS

Public users may view:

* Broker profiles
* Agency profiles
* Builder profiles
* Project pages
* Property pages

Profiles should show only public-safe data.

Broker profile may show:

* Broker name
* Photo/logo
* Verification status if real
* Operating cities
* Property types
* Listings
* Contact CTA based on mode
* Reviews only if real

Agency profile may show:

* Agency name
* Logo
* Verification status if real
* Agents if public
* Listings
* Projects if applicable
* Contact CTA

Builder profile may show:

* Builder logo
* Projects
* Verification if real
* RERA info if provided
* Contact CTA

No fake ratings/reviews.

---

# 40. SEARCH RESULTS ENTRY FROM HOMEPAGE

When user searches from homepage:

The system should route to a result view such as:

```txt id="pv30jp"
/search?city=rajkot&purpose=buy&type=flat
```

or SEO-friendly routes if applicable.

Search results should preserve:

* City
* Query
* Purpose
* Property type
* Filters
* Sort
* Page state where needed

Back from property detail should return to search context.

---

# 41. SEO ENTRY FROM GOOGLE

If user enters through Google:

Example query:

```txt id="vlhlpt"
property sale in Rajkot
```

The page should open relevant Rajkot property page or search result.

SEO landing page should show:

* Relevant title
* Relevant H1
* Real Rajkot listings
* Filters
* Internal links
* City/locality context
* Safe intro text

Do not show irrelevant city results first.

Do not show fake Rajkot property count.

---

# 42. LOADING STATES

Public pages must have loading states.

Examples:

* Homepage sections loading
* Search suggestions loading
* City selector loading
* Banner ads loading
* Property cards loading
* Pricing loading
* Profile menu loading
* Auth state loading

Use skeletons where useful.

Avoid layout shift.

Do not show blank page.

---

# 43. EMPTY STATES

Use clear empty states.

Examples:

No properties in selected city:

```txt id="gtv2cl"
No properties found in Rajkot. Try changing filters or view nearby cities.
```

No active banner ads:

* Hide banner section.
* Do not show empty ad placeholder to public unless useful.

No blog posts:

* Hide blog preview section or show safe empty state.

No user saved properties:

* Show helpful dashboard empty state.

No city data:

* Show fallback and allow search.

---

# 44. ERROR STATES

Errors must be clear.

Examples:

* Search failed
* City load failed
* Login provider unavailable
* OTP failed
* Payment unavailable
* Banner ads unavailable
* Property not found
* Page not found
* Unauthorized
* Account suspended
* Feature disabled

Error state should include:

* Short explanation
* Retry if useful
* Back/home action
* Support link if relevant

Do not expose technical errors to users.

---

# 45. TOAST AND FEEDBACK

Use toast/feedback for actions:

* Login success
* Register success
* OTP sent
* Saved property
* Removed saved property
* Lead submitted
* Site visit requested
* Requirement posted
* Profile updated
* Banner ad submitted
* Payment pending/success/fail
* Error occurred

Toast must not lie.

Do not show success before server confirms.

---

# 46. RESPONSIVE PUBLIC CHECKLIST

Every public UI phase must check:

## Mobile

* Header fits
* Logo does not wrap
* City selector fits
* Search usable
* Tabs scroll
* Filters usable
* CTA visible
* Menu opens/closes
* Popup fits
* No horizontal scroll
* Cards readable
* Footer usable

## Tablet

* Header adapts
* Cards use proper grid
* Search layout remains clear
* Drawer/bottom sheet works

## Desktop

* Header full nav works
* Container max-width correct
* Search hierarchy clear
* Footer organized
* Banner carousel not too large
* Content not stretched

---

# 47. ACCESSIBILITY REQUIREMENTS

Public website must support:

* Real buttons and links
* Keyboard focus where possible
* Labelled inputs
* Icon aria-labels
* Readable contrast
* Large touch targets
* Error messages
* Screen-reader friendly modal labels where possible
* Focus trap for modal if implemented
* Escape close where safe

Do not rely on color only for state.

---

# 48. PERFORMANCE REQUIREMENTS

Public website must load fast.

Rules:

* Optimize images
* Use responsive images
* Lazy load below-fold sections
* Lazy load maps
* Do not load dashboard code on homepage
* Do not load admin code on public pages
* Keep carousel lightweight
* Avoid heavy animations
* Avoid layout shift
* Use pagination/load-more
* Cache public data carefully
* Do not fetch private data publicly

Homepage should be fast even with banner ads.

---

# 49. PUBLIC SECURITY RULES

Public pages must not expose:

* Hidden phone numbers
* Hidden emails
* Private addresses if hidden
* Verification documents
* User private notes
* Admin notes
* Payment data
* Subscription private data
* Provider secrets
* Private storage URLs
* RLS-protected data
* Draft/pending listings
* Rejected ads
* Expired private promotions

Public query must only return public-safe fields.

---

# 50. FEATURE FLAG PUBLIC RULES

If a feature is disabled:

* Hide related public UI.
* Remove route from nav if needed.
* Show safe disabled state only when useful.
* Do not show dead button.

Examples:

If banner ads disabled:

* Hide banner carousel and banner ad CTAs.

If pricing disabled:

* Hide pricing CTA or show contact-sales if intentionally configured.

If requirements disabled:

* Hide Post Requirement and Requirements tab.

If maps disabled:

* Hide map or show unavailable state.

---

# 51. PUBLIC UI ACCEPTANCE CRITERIA

Public website passes only if:

* Homepage is search-first.
* Mobile design is app-like.
* Header is role-aware.
* Logged-in user sees profile icon.
* Guest sees Login/Register.
* Admin login is not public.
* City selector works or safe state exists.
* Search tabs do not break.
* Dynamic filters do not show irrelevant fields.
* Banner ads show only approved active ads.
* Pricing visible to guest and logged-in users.
* Public CTAs preserve intent.
* Overlay outside tap closes.
* No fake UI.
* No horizontal scroll.
* Loading/empty/error states exist.
* No private data leaks.
* No screenshot/video/sample image dependency exists.

---

# 52. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`
* `05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Claude must use detailed docs for implementation details.

---

# 53. END OF FILE

This file defines the public website, homepage, header, sidebar, mobile navigation and mobile app-like UX requirements for My Gujarat Property.

The public website must be mobile-first, search-first, role-aware, clean, fast, original, no-fake and Gujarat-focused.

Nothing from uploaded docs or user chat instructions should be skipped.
