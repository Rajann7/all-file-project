# MY GUJARAT PROPERTY

# HOMEPAGE SEARCH, DYNAMIC FILTERS, CITY-FIRST PROPERTY DISCOVERY SPEC

## FILE NAME

`04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete homepage search, dynamic filter, city-first discovery and real estate search experience for **My Gujarat Property**.

This file must be read before building or redesigning:

* Homepage search
* Hero search
* Search tabs
* City selector
* Search input
* Search autocomplete
* Dynamic filters
* Quick filters
* Property category filters
* Buy/rent/commercial/land/plot/project/PG filters
* Buyer requirement search
* Search result entry
* Search query handling
* City-first result logic
* Nearby city fallback
* Search empty state
* Search SEO connection
* Mobile search overlay
* Mobile filter bottom sheet
* Search chips
* Sort controls
* Save search if implemented
* Map toggle if implemented
* Search analytics if implemented

The goal is to make the user able to find a relevant property quickly, especially on mobile.

Search is one of the most important features of My Gujarat Property.

---

# 2. CORE SEARCH PRINCIPLE

The platform must be search-first.

User should be able to start searching directly from the homepage.

The homepage should feel like an Indian real estate property listing website where users immediately search by city, locality, property type, budget and purpose.

Search must be:

* Fast
* City-first
* Mobile-first
* Real-data-driven
* Easy to understand
* Filter-rich
* Intent-aware
* Property-type-aware
* Role-aware where needed
* SEO-friendly
* No-fake
* No dead filters
* No irrelevant filters
* No horizontal scroll

User should not feel lost.

User should not need to open many pages just to start searching.

---

# 3. HOMEPAGE SEARCH RULE

Search must be present on the homepage.

The homepage should not only show static marketing content.

Primary public flow:

```txt id="wrplcu"
User opens homepage
User selects city or sees selected city
User selects purpose/property type
User enters search/locality/project/society/budget
User applies filters
User sees relevant property results or is routed to result view
```

Important:

The website should not have a separate empty “search landing page” that users must visit before searching.

Search entry must be built into the homepage itself.

A search results route can exist after the user searches, but search must begin from homepage.

Possible result behavior:

1. Search results appear below homepage search section, or
2. User is routed to `/search` with query parameters, or
3. User is routed to SEO-friendly city/property route.

Whatever approach is chosen, homepage search remains the primary entry.

---

# 4. SEARCH EXPERIENCE TARGET

The search experience should feel like:

```txt id="z7m4zm"
Search → filter → discover → contact
```

Not like:

```txt id="zhovgc"
Click many menus → open form → guess filters → broken result
```

Search must prioritize user intent.

Examples:

If user searches:

```txt id="kqoo5x"
Rajkot 3 BHK
```

System should understand:

* City: Rajkot
* BHK: 3 BHK
* Purpose: buy by default if not selected
* Property type: residential if not specified

If user searches:

```txt id="k4d52a"
Plot in Ahmedabad
```

System should understand:

* City: Ahmedabad
* Type: plot/land
* Hide BHK filters
* Show land/plot filters

If user searches:

```txt id="z4oig3"
Commercial shop in Surat
```

System should understand:

* City: Surat
* Purpose/type: commercial
* Show commercial filters
* Hide residential-only filters

---

# 5. SEARCH SOURCE OF TRUTH

Search results must come from real system data.

Allowed sources:

* Approved active properties
* Approved active projects
* Approved active public broker profiles
* Approved active public agency profiles
* Approved active public builder profiles
* Public buyer requirements if enabled
* City/locality records
* Admin-approved SEO/location data
* Real saved search history
* Admin-configured popular searches if implemented
* Real trending searches if tracking exists

Not allowed:

* Fake property cards
* Fake results
* Fake result count
* Fake city count
* Fake autocomplete suggestions
* Fake trending searches
* Fake “popular locality” if not real/admin configured
* Fake map pins
* Fake broker/agency/builder profiles
* Fake rating/review
* Fake “verified” badge

If data is unavailable, show empty state or hide section.

---

# 6. CITY-FIRST SEARCH RULE

City selection affects the entire search experience.

Selected city should prioritize:

* Properties in selected city
* Projects in selected city
* Brokers in selected city
* Agencies in selected city
* Builders in selected city
* Requirements in selected city
* Banner ads in selected city
* Localities in selected city
* SEO content for selected city

Example:

If selected city is Rajkot:

1. Rajkot properties appear first.
2. Rajkot projects appear first.
3. Rajkot banner ads appear first.
4. Rajkot localities suggested first.
5. Rajkot brokers/agencies/builders prioritized if relevant.

If selected city is Ahmedabad:

1. Ahmedabad properties appear first.
2. Ahmedabad banner ads appear first.
3. Ahmedabad localities suggested first.

Do not silently mix unrelated city results at top.

---

# 7. CITY SOURCE PRIORITY

System can determine city from multiple sources.

Priority order:

1. User manually selected city
2. Search query city
3. Logged-in user profile city
4. Active dashboard/business city context
5. Browser location if permission granted
6. IP-based estimate if available
7. Default Gujarat city or platform default

Manual city selection must always override automatic detection.

If city is unknown, use safe default and ask user to select city.

Do not block search because city is unknown.

---

# 8. NEARBY CITY FALLBACK

If selected city has enough results:

Show selected city results first.

If selected city has limited results:

Show selected city results first, then nearby cities.

If selected city has no results:

Show clear message and then fallback.

Example:

```txt id="scs5w3"
No exact properties found in Rajkot. Showing nearby city properties.
```

Nearby city mapping must be admin-configurable.

Example nearby mapping:

Rajkot may include:

* Gondal
* Morbi
* Jamnagar
* Jetpur

Ahmedabad may include:

* Gandhinagar
* Sanand
* Bavla
* Kalol

Do not mix fallback results without explanation.

---

# 9. HOMEPAGE SEARCH LAYOUT

Homepage search layout should include:

1. City selector
2. Purpose tabs
3. Search input
4. Dynamic quick filters
5. Primary Search CTA
6. Secondary actions
7. Optional advanced filter trigger
8. Optional location/current-city indicator
9. Optional recent/popular searches if real

Mobile layout:

```txt id="yr09qs"
City Selector
Search Tabs
Search Input
Quick Filters
Search CTA
Post Property / Post Requirement CTAs
```

Desktop layout:

```txt id="ra3ilu"
City Selector + Tabs
Search Input + CTA
Quick Filters Row
Advanced Filters / Popular Searches
```

Keep first screen clean.

Do not overload hero section with too much text.

---

# 10. SEARCH TABS

Required search tabs:

* Buy
* Rent
* Commercial
* Land / Plots
* Projects
* PG / Hostel
* Buyer Requirements

Tab behavior:

* Selected tab controls filters.
* Selected tab controls search query purpose.
* Selected tab controls result type.
* Selected tab controls placeholders.
* Selected tab controls CTAs.
* Selected tab must be clear visually.
* On mobile, tabs can be horizontally scrollable.
* Tabs must not wrap into ugly two-line layout.

If a tab feature is not implemented:

* Hide it, or
* Disable with setup/future state only if useful.

No dead tabs.

---

# 11. SEARCH INPUT SCOPE

Main search input should support:

* City
* District
* Taluka
* Village
* Area
* Locality
* Society
* Building
* Landmark
* Project name
* Builder name
* Broker name
* Agency name
* Property ID
* RERA number
* BHK
* Budget
* Property type
* Keyword

Example search inputs:

```txt id="lc843k"
Rajkot 3 BHK
Kalawad Road flat
2 BHK under 60 lakh
Plot near Mavdi
Commercial shop in Rajkot
Girls PG Rajkot
Property sale in Rajkot
Best property in Rajkot
Sunrise Heights
ABC Builders
PROP-12345
RERA number
```

Search parsing can improve over time.

Initial implementation can use structured filters plus keyword search.

---

# 12. SEARCH PLACEHOLDER TEXT

Placeholder should change by selected tab.

Buy:

```txt id="c5o4js"
Search city, locality, society, project or property ID
```

Rent:

```txt id="ucpxj4"
Search rentals by city, area, society or landmark
```

Commercial:

```txt id="1n0utx"
Search shops, offices, showrooms or commercial spaces
```

Land / Plots:

```txt id="953yow"
Search plots, land, village, survey area or locality
```

Projects:

```txt id="vj8n9a"
Search projects, builders or RERA number
```

PG / Hostel:

```txt id="j3m6eu"
Search PG, hostel, co-living or area
```

Buyer Requirements:

```txt id="vvydsp"
Search buyer requirements by city, budget or property type
```

Do not use generic placeholder for all tabs if better context is possible.

---

# 13. SEARCH AUTOCOMPLETE

Autocomplete should feel premium and useful.

Autocomplete can show groups:

* Cities
* Localities
* Societies
* Projects
* Builders
* Brokers
* Agencies
* Property IDs
* RERA numbers
* Popular searches
* Recent searches
* Admin-configured suggestions

Example when user types:

```txt id="g860rl"
Raj
```

Suggestions may show:

```txt id="j8kf7f"
Rajkot Properties
Rajkot 2 BHK
Rajkot 3 BHK
Rajkot Flats
Rajkot Commercial Shops
Rajkot Plots
Raiya Road
Kalawad Road
Rajkot Projects
Rajkot Brokers
Rajkot Buyer Requirements
```

Autocomplete must not be fake.

If real/autocomplete engine is not implemented:

* Do not show fake suggestions.
* Show basic input only.
* Or show admin-configured real suggestions.

---

# 14. MOBILE AUTOCOMPLETE UX

On mobile, autocomplete can open as:

* Full-screen search overlay, or
* Large dropdown panel, or
* Bottom sheet

Recommended mobile overlay should include:

* Back icon
* Search input focused
* Current city
* Recent searches if real
* Popular searches if real/admin-configured
* Suggestions
* Clear input
* Close action
* No horizontal scroll

Do not create tiny dropdown that is hard to tap.

---

# 15. RECENT SEARCHES

Recent searches can be stored as:

* Logged-in user: database/user preferences
* Guest user: local storage if allowed

Recent searches should include:

* Query
* City
* Purpose
* Filters summary
* Timestamp

User should be able to clear recent searches if implemented.

Do not show fake recent searches.

---

# 16. POPULAR / TRENDING SEARCHES

Popular/trending searches can be:

1. Real analytics-generated, or
2. Admin-configured

Examples:

* Rajkot 2 BHK
* Rajkot Kalawad Road
* Ahmedabad Flats
* Surat Commercial Shop
* Vadodara PG
* Jamnagar Plots

If analytics engine is not implemented, use only admin-configured values.

Do not show fake trending claims.

---

# 17. DYNAMIC FILTER MASTER RULE

Filters must change according to selected purpose and property type.

Wrong:

```txt id="yt2ftf"
User selects Land but sees BHK filter.
```

Correct:

```txt id="y19ghq"
User selects Land and sees land area, land type, road access and zoning filters.
```

Wrong:

```txt id="r927py"
User selects PG but sees plot area and commercial frontage.
```

Correct:

```txt id="8xtzmh"
User selects PG and sees sharing, gender, food and AC filters.
```

Every visible filter must work.

If filter logic is not implemented, hide that filter.

---

# 18. COMMON FILTERS

Common filters across multiple tabs:

* City
* Locality
* Budget
* Property type
* Area
* Area unit
* Availability/status
* Posted by
* Verification status if real
* Source type
* Sort
* Clear filters

Common property source filters:

* Owner
* Broker
* Agency
* Builder
* Developer

Common status filters:

* Active
* Ready
* Under Construction
* Resale
* New Launch
* Verified if real

Do not show fake verification status.

---

# 19. BUY FILTERS

Buy search filters may include:

* City
* Locality
* Society
* Property type
* BHK
* Budget min
* Budget max
* Area min
* Area max
* Area unit
* Construction status
* Possession
* Furnishing
* Floor
* Total floors
* Parking
* Bathrooms
* Balconies
* Amenities
* Posted by
* Brokerage
* Verification status
* RERA if applicable
* Property age
* Facing if implemented
* Vastu if implemented
* Loan availability if implemented

Property types for Buy:

* Flat/Apartment
* Independent House
* Villa
* Bungalow
* Row House
* Penthouse
* Studio
* Farm House
* Plot
* Residential Land

Only show fields relevant to selected type.

---

# 20. RENT FILTERS

Rent search filters may include:

* City
* Locality
* Society
* Monthly rent min/max
* Deposit
* Property type
* BHK
* Furnishing
* Available from
* Tenant type
* Family allowed
* Bachelor allowed
* Company lease
* Preferred tenants
* Parking
* Floor
* Bathrooms
* Balconies
* Amenities
* Brokerage
* Maintenance included
* Pet allowed if implemented
* Food not applicable unless PG

Rental property types:

* Flat
* House
* Villa
* Room
* Shared room
* Commercial rental if under commercial tab

Do not show sale price filters as primary in rent mode.

---

# 21. COMMERCIAL FILTERS

Commercial filters may include:

* City
* Locality
* Commercial type
* Purpose: sale/rent/lease
* Budget/rent
* Area
* Area unit
* Floor
* Frontage
* Road width
* Parking
* Washroom
* Power load if implemented
* Suitable for
* Furnishing
* Occupancy status
* Possession
* Business type suitability
* Main road
* Corner property
* Lift
* Loading/unloading
* Brokerage

Commercial types:

* Shop
* Office
* Showroom
* Warehouse
* Industrial Shed
* Factory
* Co-working Space
* Restaurant/Cafe Space
* Clinic/Medical Space
* Godown
* Commercial Land

Do not show BHK for commercial unless a subtype truly needs rooms.

---

# 22. LAND / PLOT FILTERS

Land/plot filters may include:

* City
* District
* Taluka
* Village
* Locality
* Land type
* Purpose
* Budget
* Area
* Area unit
* Road access
* Road width
* Corner plot
* Boundary wall
* NA/NOC status if applicable
* Agriculture/non-agriculture
* Zoning
* Water availability
* Electricity availability
* Drainage
* Facing if implemented
* Survey/block number if allowed
* Nearby landmark
* Soil/irrigation if agriculture land
* Brokerage
* Ownership type if implemented

Land types:

* Residential Plot
* Commercial Plot
* Industrial Land
* Agricultural Land
* Farm Land
* NA Land
* Open Land
* Warehouse Land
* Investment Land

Hide BHK, floor, furnishing and bathroom filters.

---

# 23. PROJECT FILTERS

Project filters may include:

* City
* Locality
* Builder
* Project name
* RERA number
* Unit type
* BHK
* Price range
* Area range
* Possession date
* Construction status
* New launch
* Ready to move
* Under construction
* Amenities
* Project size
* Towers
* Floors
* Parking
* Brochure available
* Verified/RERA if real

Project result type should show projects, not individual resale listings unless intentionally mixed.

---

# 24. PG / HOSTEL FILTERS

PG/Hostel filters may include:

* City
* Locality
* Gender
* Sharing type
* Rent
* Deposit
* Food included
* AC/non-AC
* Furnishing
* Attached bathroom
* Wi-Fi
* Laundry
* Housekeeping
* Parking
* Curfew rules
* Visitor rules
* Student/professional
* Boys/girls/co-ed
* Available from
* Minimum stay
* Meals type

PG/Hostel property types:

* Boys PG
* Girls PG
* Co-living
* Student Hostel
* Working Men Hostel
* Working Women Hostel
* Shared Room
* Private Room

Do not show irrelevant sale filters.

---

# 25. BUYER REQUIREMENT FILTERS

Buyer requirement filters may include:

* Requirement type
* City
* Locality
* Budget
* Property type
* BHK
* Area
* Urgency
* Possession requirement
* Buyer type
* Contact preference
* Visibility allowed
* Requirement status
* Posted date

Visible to:

* Buyer/Tenant for own requirements
* Broker/Agency/Builder based on plan/permission
* Admin based on permission
* Public only if admin allows public requirement visibility

Do not expose buyer private contact unless allowed.

---

# 26. FILTER DEPENDENCY RULE

Some filters depend on other selections.

Examples:

If purpose = Buy and property type = Flat:

Show BHK.

If purpose = Buy and property type = Plot:

Hide BHK.

If purpose = Rent and property type = Flat:

Show rent/deposit/furnishing.

If purpose = PG:

Show sharing/gender/food.

If purpose = Commercial and type = Warehouse:

Show loading/unloading, power, height if implemented.

If city changes:

Update locality/society/project suggestions.

If district changes:

Update taluka/city/village.

If taluka changes:

Update village/locality.

All dependent filters should update without full page refresh.

---

# 27. LOCATION FILTERS

Location filters should support Gujarat hierarchy:

```txt id="d3nrxa"
State → District → Taluka → City / Village → Area → Locality → Society → Building → Landmark
```

Public search can start simple:

* City
* Locality
* Society
* Landmark

Advanced/property posting can use deeper hierarchy:

* State
* District
* Taluka
* Village
* Area

If location is missing:

* Allow request location
* Allow manual keyword search
* Admin review if needed

Do not reload full page on every location selection.

Use dynamic fetching.

---

# 28. AREA UNIT FILTERS

Area unit should be flexible.

Supported units may include:

* Sq Ft
* Sq Yard
* Sq Meter
* Var
* Bigha
* Acre
* Guntha
* Hectare

Area units should adapt to property type.

Residential:

* Sq Ft
* Sq Yard
* Sq Meter

Plot/Land:

* Sq Yard
* Var
* Bigha
* Acre
* Guntha
* Hectare

Commercial:

* Sq Ft
* Sq Yard
* Sq Meter

Avoid forcing one unit for all property types.

---

# 29. BUDGET FILTERS

Budget filters should adapt to purpose.

Buy:

* Min price
* Max price
* Price range chips

Rent:

* Monthly rent
* Deposit

Commercial:

* Sale price or rent/lease depending purpose

Land:

* Total price
* Price per unit if implemented

PG:

* Monthly rent
* Deposit

Requirement:

* Budget min
* Budget max

Display Indian formats:

* ₹25 Lakh
* ₹50 Lakh
* ₹1 Cr
* ₹2 Cr
* ₹10,000/month
* ₹25,000/month

Do not confuse sale price and rent.

---

# 30. SELECTED FILTER CHIPS

After filters are selected, show chips.

Examples:

```txt id="y3d46w"
Rajkot
3 BHK
₹50L - ₹80L
Flat
Owner
Ready to Move
```

Chips should support:

* Remove individual filter
* Clear all
* Mobile horizontal scroll if needed
* No layout overflow

Chips should update URL/query state if supported.

---

# 31. SORTING

Sort options may include:

* Relevance
* Newest
* Price Low to High
* Price High to Low
* Area Low to High
* Area High to Low
* Recently Updated
* Verified First if real
* Featured/Sponsored placement clearly labeled
* Possession Soon for projects
* Rent Low to High for rent/PG

Sponsored/featured listings can have placement rules, but must be labeled.

Do not hide paid ranking.

---

# 32. SEARCH RESULT TYPES

Search can return different result types:

* Properties
* Projects
* Buyer Requirements
* Brokers
* Agencies
* Builders
* Localities
* Blog/guide content if relevant

Result type depends on selected tab and query.

Example:

If user searches builder name:

Show builder profile and builder projects.

If user searches property ID:

Show exact property if active and public.

If user searches RERA number:

Show matching project/property if available.

If user selects Buyer Requirements:

Show requirement results according to permission.

---

# 33. SEARCH RESULT ROUTING

Possible search route:

```txt id="ddtm5b"
/search?city=rajkot&purpose=buy&type=flat&bhk=3
```

SEO-friendly route examples:

```txt id="hu2nk6"
/city/rajkot/property-sale
/city/rajkot/flats
/city/rajkot/plots
/city/rajkot/commercial
/locality/rajkot/kalawad-road
```

Rules:

* Homepage search should generate clean query state.
* URL should be shareable if possible.
* Back from property detail should preserve search context.
* Filters should not reset randomly.
* Search should not require login.

---

# 34. MOBILE SEARCH UX

Mobile search must feel app-like.

Mobile search flow:

1. User taps search input.
2. Full-screen search overlay or focused panel opens.
3. User sees current city.
4. User types query.
5. Suggestions appear if real.
6. User selects suggestion or presses search.
7. Results show.
8. Filters available through bottom sheet.
9. Selected chips visible.
10. Back returns logically.

Mobile must avoid:

* Tiny filter controls
* Desktop sidebar filters
* Horizontal scroll
* Cramped search tabs
* Keyboard covering important CTA
* Popover cut-off
* Sticky header overlap

---

# 35. MOBILE FILTER BOTTOM SHEET

Mobile filters should open in bottom sheet or full-screen sheet.

Bottom sheet should include:

* Filter categories
* Selected count
* Clear all
* Apply button
* Close button
* Outside tap close
* Back support
* Scrollable content
* Sticky Apply button
* No hidden fields under CTA

For complex filters, use grouped sections:

* Budget
* Property Type
* BHK/Rooms
* Area
* Location
* Amenities
* Posted By
* More Filters

Filter groups must change by selected tab/type.

---

# 36. DESKTOP SEARCH RESULTS UX

Desktop search results may include:

* Header
* Sticky search bar
* Result count
* Sort dropdown
* Selected filter chips
* Filter sidebar
* Results list/grid
* Optional map panel if enabled
* Banner/sponsored placements if enabled
* Pagination or load more

Filter sidebar should be sticky.

Map should not load if disabled.

Sponsored placements must be labeled.

---

# 37. TABLET SEARCH UX

Tablet should adapt between mobile and desktop.

Possible layout:

* Sticky header
* Search bar full width
* Filters as drawer or side panel
* 2-column property cards
* Bottom sheet if width is tight

No desktop-only cramped layout.

---

# 38. MAP TOGGLE

Map is optional and provider-controlled.

Map modes:

* Disabled
* Embed/free/trial mode
* Premium API mode

Search map behavior:

* If map disabled, hide map toggle.
* If provider missing, show setup-required only in admin/dev context.
* If embed mode, use allowed embed behavior.
* If premium mode, use real API.
* Do not fake map pins.
* Do not load heavy maps by default on mobile.

Map should not block search.

---

# 39. SAVE SEARCH

Save search may be implemented.

Guest behavior:

* Click Save Search opens login/register popup.
* Intent preserved.
* After login, save search.

Logged-in behavior:

* Save query, city and filters.
* Allow alert preference if implemented.
* Show saved search in dashboard.

Do not show save search if not implemented.

Do not fake alerts.

---

# 40. SEARCH ALERTS

Search alerts can notify users when matching properties appear.

Possible channels:

* In-app
* Email if verified/configured
* WhatsApp if configured
* Push if implemented

Alerts must be real.

If notification providers are missing, do not fake alert delivery.

---

# 41. NO-RESULT RECOVERY

No-result page must help user.

No-result state may show:

* Clear message
* Remove filters
* Show nearby cities
* Expand budget
* Try different property type
* Post requirement CTA
* Save search CTA if implemented
* Contact support if needed

Example:

```txt id="iu7w89"
No flats found in Rajkot under ₹40 lakh. Try increasing budget or post your requirement.
```

Do not show fake results just to fill page.

---

# 42. SEARCH EMPTY STATE BY TYPE

Buy empty state:

```txt id="f7rlsq"
No properties found. Try changing budget, BHK or locality.
```

Rent empty state:

```txt id="ot5urm"
No rentals found. Try changing rent range or move-in preference.
```

Land empty state:

```txt id="furlrv"
No land or plots found. Try changing area, location or budget.
```

Commercial empty state:

```txt id="avv7aw"
No commercial spaces found. Try changing business type or area.
```

PG empty state:

```txt id="6hs6y4"
No PG/hostel options found. Try changing sharing type or locality.
```

Requirement empty state:

```txt id="j85y03"
No matching requirements found. Try changing city or property type.
```

---

# 43. SEARCH RESULT COUNT RULE

Counts must be real.

If exact count is expensive, use safe count strategy or hide count.

Allowed:

```txt id="o6nn5g"
Showing properties in Rajkot
```

Allowed if real:

```txt id="dqsxia"
128 properties found in Rajkot
```

Not allowed:

```txt id="ev26tu"
5000+ properties
```

unless real and verified.

---

# 44. SPONSORED / FEATURED RESULT RULE

Sponsored or featured results can appear in search if monetization supports it.

Rules:

* Must be paid/eligible.
* Must be approved.
* Must be active.
* Must be labeled clearly.
* Must respect city/category targeting.
* Must not hide organic results unfairly without label.
* Must expire according to plan.
* Must not show fake sponsored badge.

Sponsored search logic belongs to monetization/ads docs.

---

# 45. SEARCH AND BANNER ADS CONNECTION

Homepage banner ads and search are connected through city context.

If selected city is Rajkot:

* Search results prioritize Rajkot.
* Banner ads prioritize Rajkot.
* Localities prioritize Rajkot.
* SEO content matches Rajkot.

If selected city changes:

* Search context updates.
* Banner ad priority updates.
* Popular searches update if configured.
* City/locality suggestions update.

Banner ads must never replace search.

Search remains primary.

---

# 46. SEARCH AND SEO CONNECTION

Search should support SEO growth.

Examples:

Google query:

```txt id="voza4f"
property sale in Rajkot
```

Landing page should show:

* Rajkot property sale page
* Relevant H1
* Real Rajkot listings
* Useful filters
* Intro copy
* City/locality links

Search query should connect to SEO pages where appropriate.

SEO pages should use search/filter logic but must avoid thin/fake pages.

---

# 47. ROLE-BASED SEARCH ACTIONS

Search results actions change by user role.

Guest:

* View property
* Contact triggers login if needed
* Save triggers login
* Post property/register CTA

Buyer/Tenant:

* Save
* Contact
* Book visit
* Post requirement
* Compare if implemented

Owner:

* View public search
* Post property
* Manage own property from dashboard if relevant

Broker:

* View properties
* View requirements if plan allows
* Send proposal from requirement result if permitted
* Post listing

Agency:

* Similar to broker plus team/agency actions

Builder:

* Project/search leads
* Requirement proposal if allowed
* Project posting

Admin:

* Public search plus admin moderation shortcuts only in admin context if safe

Do not show wrong role actions.

---

# 48. SEARCH PERMISSION RULE

Search is public for safe data.

Public search must not return:

* Hidden contact numbers
* Hidden emails
* Private addresses if hidden
* Admin notes
* Verification documents
* Internal risk scores
* Payment data
* Private user data
* Lead data
* Draft listings
* Pending listings unless admin context
* Rejected listings
* Expired hidden listings

Admin search can show more data based on permission.

---

# 49. SEARCH DATABASE PERFORMANCE RULE

Search must be scalable.

Important indexes may include:

* city_id
* locality_id
* property_type
* purpose
* price
* rent
* area
* bhk
* status
* approval_status
* verification_status
* created_at
* updated_at
* slug
* rera_number
* posted_by_user_id
* source_type

Search should use:

* Pagination
* Limit/offset or cursor pagination
* Full-text search where useful
* Composite indexes for common filters
* Lean card queries
* Avoid loading full detail data for cards
* Avoid N+1 queries
* Cached location lists where safe

---

# 50. SEARCH URL STATE

Filters should be reflected in URL where practical.

Example:

```txt id="t8pdkm"
/search?city=rajkot&purpose=buy&type=flat&bhk=3&min_price=5000000&max_price=8000000
```

Benefits:

* Shareable links
* Back button works
* SEO-friendly routing support
* Saved search support
* Browser refresh preserves filters

Do not store sensitive data in URL.

---

# 51. SEARCH LOADING STATE

Loading state should be smooth.

Use:

* Skeleton property cards
* Filter skeleton if needed
* Search input loading for suggestions
* City selector loading
* Result count loading
* Spinner only where appropriate

Avoid:

* Blank white screen
* Layout jump
* Blocking entire page unnecessarily
* Showing stale city without indication

---

# 52. SEARCH ERROR STATE

Error state should show:

* Clear message
* Retry button
* Back/home option
* Support link if needed

Example:

```txt id="jwx7bc"
Search could not load right now. Please try again.
```

Do not expose technical database errors to users.

---

# 53. SEARCH SUCCESS STATE

Successful search should show:

* Current city
* Current purpose
* Selected filters
* Result list
* Sort
* Clear filters
* Save search if implemented
* No hidden/private data
* Correct cards for result type

Success state should feel fast and clear.

---

# 54. SEARCH SECURITY RULE

Search queries must be validated.

Prevent:

* SQL injection
* Unsafe query strings
* Excessive query load
* Large unbounded result sets
* Private data leakage
* Draft/pending/rejected listing leakage
* Hidden contact leakage
* Unauthorized requirement access

All public search should use safe public views or safe selected fields.

---

# 55. SEARCH ANALYTICS

Search analytics can be implemented for:

* Popular searches
* No-result queries
* City demand
* Property type demand
* Filter usage
* SEO opportunities
* Buyer demand trends

But analytics must be real.

If analytics is not implemented:

* Do not show fake trending searches.
* Do not show fake dashboard search insights.

Search analytics should help Super Admin improve platform.

---

# 56. ADMIN SEARCH CONTROLS

Admin/Super Admin should control:

* Active cities
* Popular searches
* Search tabs visibility
* Property type filters
* Requirement visibility
* Nearby city mapping
* SEO templates
* Featured/sponsored placement rules
* Autocomplete configuration if admin-controlled
* Disabled filters
* Map mode
* Search result ad placement if implemented
* Noindex rules for empty pages

If setting is visible, it must work.

---

# 57. SEARCH FEATURE FLAGS

Possible feature flags:

```txt id="ydnwzi"
search.enabled
search.homepage.enabled
search.autocomplete.enabled
search.recent_searches.enabled
search.popular_searches.enabled
search.save_search.enabled
search.alerts.enabled
search.map.enabled
search.city_fallback.enabled
search.requirements_tab.enabled
search.projects_tab.enabled
search.pg_tab.enabled
search.commercial_tab.enabled
search.land_tab.enabled
search.dynamic_filters.enabled
search.sponsored_results.enabled
```

If a feature flag is off, hide related UI and block backend action if needed.

---

# 58. SEARCH COMPONENTS

Recommended components:

* HomeSearch
* SearchTabs
* CitySelector
* SearchInput
* SearchAutocomplete
* QuickFilters
* DynamicFilterPanel
* MobileFilterSheet
* SelectedFilterChips
* SearchResultHeader
* SortDropdown
* PropertyResultCard
* ProjectResultCard
* RequirementResultCard
* BrokerResultCard
* AgencyResultCard
* BuilderResultCard
* SearchEmptyState
* SearchErrorState
* SearchSkeleton
* SaveSearchButton
* MapToggle
* NearbyCityFallback
* PopularSearches
* RecentSearches

Do not create duplicate random components.

---

# 59. MOBILE SEARCH ACCEPTANCE CHECKLIST

Mobile search passes only if:

* Search visible on homepage first screen.
* Tabs fit or scroll horizontally.
* Selected tab is clear.
* Search input is easy to tap.
* Keyboard does not break layout.
* Filters open in bottom sheet/full-screen sheet.
* Apply button visible.
* Selected chips do not overflow badly.
* Property cards are readable.
* No horizontal scroll.
* Back icon works in search overlay.
* City selector works.
* Irrelevant filters are hidden.
* No fake suggestions/results/counts.
* Empty state is helpful.
* Contact/save actions preserve intent.

---

# 60. DESKTOP SEARCH ACCEPTANCE CHECKLIST

Desktop search passes only if:

* Homepage search is clear.
* Header does not feel crowded.
* Search tabs are readable.
* Filter sidebar is usable.
* Result cards are readable.
* Sort and chips work.
* City context is visible.
* Results do not stretch too wide.
* Sponsored items are labeled.
* Map toggle hidden if disabled.
* No fake data.
* No broken buttons.

---

# 61. GENERAL SEARCH ACCEPTANCE RULE

Search phase should be marked PASS only if:

* Homepage search exists.
* City-first search works or is clearly implemented.
* Dynamic filters change by type.
* Irrelevant filters are hidden.
* Public search uses safe real data or safe empty states.
* No fake counts are shown.
* No fake suggestions are shown.
* No hidden contacts are exposed.
* Mobile search is usable.
* Loading/empty/error states exist.
* Feature registry is updated.
* Manual verification is completed according to verification prompt.

If any visible filter does nothing, mark FAIL or PARTIAL.

---

# 62. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those docs for deeper implementation details.

---

# 63. END OF FILE

This file defines homepage search, dynamic filters and city-first property discovery for My Gujarat Property.

Search must be homepage-first, city-first, mobile-first, property-type-aware, real-data-driven and no-fake.

Nothing from uploaded docs or user chat instructions should be skipped.
