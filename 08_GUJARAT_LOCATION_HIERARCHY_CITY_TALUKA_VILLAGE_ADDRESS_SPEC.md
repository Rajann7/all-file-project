# MY GUJARAT PROPERTY

# GUJARAT LOCATION HIERARCHY, CITY, DISTRICT, TALUKA, VILLAGE & ADDRESS SPEC

## FILE NAME

`08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete Gujarat-first location, address, district, taluka, city, village, locality, society, building and map-location system for **My Gujarat Property**.

This file must be read before building or redesigning:

* City selector
* State selector
* District selector
* Taluka selector
* City selector
* Village selector
* Locality selector
* Society selector
* Building selector
* Landmark field
* Property posting address form
* Project address form
* Requirement location form
* Broker/agency/builder operating area form
* Banner ad city targeting
* Homepage city priority
* SEO city/locality pages
* Admin location management
* Location approval workflow
* Custom missing-location request
* Cascading no-refresh dropdowns
* Map point/location selection
* IP/location fallback
* Nearby city fallback
* Search location filters

The goal is to make location data accurate, structured, searchable, SEO-friendly and scalable from Gujarat to all India later.

---

# 2. CORE LOCATION PRINCIPLE

My Gujarat Property is Gujarat-first.

Location must be treated as a core database system, not a simple text field.

Every important real estate feature depends on location:

* Homepage search
* Property search
* Property posting
* Requirement posting
* Project posting
* Broker profile
* Agency profile
* Builder profile
* Banner ads targeting
* City-first SEO
* Locality SEO
* Admin moderation
* Lead routing
* City manager scope
* Nearby city fallback
* Mobile discovery
* Map display
* Analytics if implemented

Location must be structured and consistent.

Do not store only one free-text address field.

Do not force users to type all location manually.

Use dropdowns, search and controlled data wherever possible.

---

# 3. UI LANGUAGE RULE

Location field labels should be in English.

Use:

* State
* District
* Taluka
* City
* Village
* Area
* Locality
* Society
* Building
* Landmark
* Address Line
* Pin Code
* Map Location

Do not show primary UI labels as:

* Jillo
* Taluko
* Gam
* Gaam

If Gujarati/Hindi language mode is implemented later, translations can be added.

Initial UI should use English labels because user specifically requested English fields.

---

# 4. LOCATION HIERARCHY

Required location hierarchy:

```txt id="b3dc95"
Country
  → State
    → District
      → Taluka
        → City / Village
          → Area
            → Locality
              → Society
                → Building
                  → Landmark
                    → Address Line
                    → Pin Code
                    → Map Location
```

Not every listing requires every level.

But database must support deep hierarchy.

Examples:

Urban flat:

```txt id="d02qec"
India → Gujarat → Rajkot District → Rajkot Taluka → Rajkot City → Kalawad Road → Mota Mava → ABC Society → Tower A → Near XYZ Landmark
```

Village land:

```txt id="771h0g"
India → Gujarat → Rajkot District → Gondal Taluka → Village Name → Farm Area → Survey/Block Area → Landmark
```

Commercial shop:

```txt id="oacipz"
India → Gujarat → Ahmedabad District → Ahmedabad City → Satellite → Main Road → Commercial Complex → Shop Number
```

Builder project:

```txt id="97bb07"
India → Gujarat → Surat District → Surat City → Vesu → Project Locality → Project Name → Tower/Phase
```

---

# 5. LOCATION DATA SOURCE RULE

Location database should be built from reliable sources.

Recommended approach:

1. Seed Gujarat state.
2. Seed all Gujarat districts.
3. Seed all Gujarat talukas.
4. Seed cities, towns and villages.
5. Add localities and societies through admin/user growth.
6. Allow user-submitted missing locations.
7. Admin verifies and approves missing locations.
8. Maintain slugs for SEO.

Initial data should include all important Gujarat cities and districts.

For complete district/taluka/village accuracy, use official/current administrative data source during implementation.

Do not rely only on a small manually typed city list.

---

# 6. GUJARAT-FIRST REQUIREMENT

The platform must include Gujarat as the default launch state.

State field:

```txt id="podgg6"
Gujarat
```

Country field:

```txt id="21v8t4"
India
```

Initial launch can focus only on Gujarat but should be scalable later.

Database should support other states in future.

Do not hardcode Gujarat in a way that makes future India expansion impossible.

---

# 7. INITIAL GUJARAT DISTRICT SUPPORT

The system must support all Gujarat districts.

District data should be imported/seeded from official/current source at implementation time.

Examples of Gujarat districts include:

* Ahmedabad
* Amreli
* Anand
* Aravalli
* Banaskantha
* Bharuch
* Bhavnagar
* Botad
* Chhota Udaipur
* Dahod
* Dang
* Devbhoomi Dwarka
* Gandhinagar
* Gir Somnath
* Jamnagar
* Junagadh
* Kheda
* Kutch
* Mahisagar
* Mehsana
* Morbi
* Narmada
* Navsari
* Panchmahal
* Patan
* Porbandar
* Rajkot
* Sabarkantha
* Surat
* Surendranagar
* Tapi
* Vadodara
* Valsad

Implementation must verify the current district list using official source before final seed.

If a district changes in future, Admin/Super Admin should update location records.

---

# 8. INITIAL GUJARAT CITY SUPPORT

The system must support Gujarat cities, towns and major real estate markets.

Initial city examples include:

* Ahmedabad
* Surat
* Vadodara
* Rajkot
* Jamnagar
* Bhavnagar
* Gandhinagar
* Junagadh
* Anand
* Nadiad
* Morbi
* Mehsana
* Bharuch
* Vapi
* Navsari
* Valsad
* Bhuj
* Gandhidham
* Porbandar
* Surendranagar
* Botad
* Amreli
* Palanpur
* Patan
* Himmatnagar
* Modasa
* Dahod
* Godhra
* Veraval
* Ankleshwar
* Jetpur
* Gondal
* Kalol
* Sanand
* Dholka
* Deesa
* Unjha
* Visnagar
* Mahesana
* Khambhat
* Petlad
* Kapadvanj
* Vyara
* Mandvi
* Dwarka
* Somnath
* Una
* Diu-connected market if later applicable
* Savarkundla
* Dhoraji
* Upleta
* Wadhwan
* Limbdi
* Halol
* Padra
* Dabhoi
* Borsad
* Bardoli
* Olpad
* Kadi
* Sidhpur
* Tharad
* Rapar
* Anjar
* Mundra
* Keshod
* Manavadar
* Talaja
* Mahuva
* Bagasara

This is not the final complete city database.

Implementation must support importing all Gujarat cities/towns and updating them from Admin/Super Admin.

---

# 9. TALUKA SUPPORT

Every district should have linked talukas.

User flow:

```txt id="owjtx9"
User selects District
System fetches Talukas for selected District
User selects Taluka
System fetches Cities/Villages/Areas for selected Taluka
```

Taluka field must be available in:

* Property posting
* Land posting
* Agriculture land posting
* Village property posting
* Requirement posting if rural/land
* Location admin
* Search filters where relevant
* SEO pages if taluka pages are enabled later

Do not force urban users to always select taluka if simplified mode is enabled, but database should support it.

---

# 10. VILLAGE SUPPORT

Village support is important for:

* Land
* Agricultural land
* Farm land
* Open land
* Plot
* Village property
* Investment land
* Rural property

Village field should appear when relevant.

Examples:

If user selects property type:

* Agricultural Land
* Farm Land
* Village House
* Rural Plot
* Industrial Land near village
* Open Land

Then village/taluka fields become more important.

If user selects urban flat, village field may be hidden.

Do not show irrelevant village field for all urban flows unless needed.

---

# 11. CITY VS VILLAGE LOGIC

City and Village can be separate fields or same entity type with type flag.

Recommended structure:

```txt id="haq8ra"
places table:
- id
- name
- slug
- type: city | town | village | locality | society | building | landmark
- parent_id
- district_id
- taluka_id
- state_id
```

or separate tables.

Important:

* City and village must be distinguishable.
* Village must not be treated as locality only.
* Urban locality must not be treated as village.
* Search should handle both.

---

# 12. LOCALITY SUPPORT

Locality is important for city search.

Examples:

Rajkot localities:

* Kalawad Road
* Mavdi
* Mota Mava
* Nana Mava
* Raiya Road
* University Road
* Yagnik Road
* Kotecha Chowk
* 150 Feet Ring Road
* Gondal Road
* Jamnagar Road
* Morbi Road
* Kuvadva Road
* Amin Marg
* Sadhu Vasvani Road

Ahmedabad localities:

* Satellite
* Bopal
* South Bopal
* SG Highway
* Prahlad Nagar
* Vastrapur
* Chandkheda
* Gota
* Thaltej
* Maninagar
* Nikol
* Naroda
* Vastral
* Shela
* Shilaj
* Science City
* Motera

These are examples.

The actual locality database should grow through admin/user submissions.

---

# 13. SOCIETY / PROJECT / BUILDING SUPPORT

Property listing should support society/building/project level detail.

Fields:

* Society name
* Project name
* Building name
* Tower/block
* Floor
* Unit number if private
* Landmark

Visibility rules:

* Society/project/building can be public.
* Exact unit number can be private by default.
* Exact full address can be hidden or partially shown based on contact policy.

Do not expose private address if owner wants hidden location.

---

# 14. ADDRESS FORM STRUCTURE

Recommended property address form:

```txt id="yvx7gh"
State
District
Taluka
City / Village
Area
Locality
Society / Project
Building / Tower
Landmark
Address Line
Pin Code
Map Location
```

Optional additional fields:

* Road name
* Near by landmark
* Survey/block number for land
* Plot number
* Shop number
* Office number
* Unit number
* Phase
* Sector
* Zone

Fields should be dynamic by property type.

---

# 15. PROPERTY-TYPE LOCATION VARIATION

Location form must adapt to property type.

## Flat / Apartment

Show:

* State
* District
* City
* Locality
* Society/Project
* Building/Tower
* Landmark
* Pin Code
* Map Location

Optional:

* Taluka
* Area

## Independent House / Villa

Show:

* State
* District
* City
* Locality
* Society/Area
* Landmark
* Address Line
* Pin Code
* Map Location

## Plot / Land

Show:

* State
* District
* Taluka
* City/Village
* Area
* Survey/Block area if needed
* Road access
* Landmark
* Pin Code if available
* Map Location

## Agricultural Land

Show:

* State
* District
* Taluka
* Village
* Survey/Block number if allowed
* Farm/area name
* Road access
* Landmark
* Map Location

## Commercial

Show:

* State
* District
* City
* Locality
* Commercial complex/building
* Road/landmark
* Shop/office/showroom number optional/private
* Pin Code
* Map Location

## Project

Show:

* State
* District
* City
* Locality
* Project site address
* Landmark
* Pin Code
* Map Location
* RERA location if applicable

## PG / Hostel

Show:

* State
* District
* City
* Locality
* Building/Society
* Landmark
* Address Line
* Pin Code
* Map Location

Do not show the same exact address fields for every property type.

---

# 16. CASCADING SELECT RULE

Location dropdowns must be cascading.

Example flow:

```txt id="dzrl0y"
Select State → Load Districts
Select District → Load Talukas
Select Taluka → Load Cities/Villages
Select City/Village → Load Areas/Localities
Select Locality → Load Societies/Projects
Select Society/Project → Load Buildings/Towers
```

No page refresh.

Use dynamic fetching.

Use loading indicators.

Use empty states.

Use search within long dropdowns.

Do not load every village/locality into first page bundle.

---

# 17. NO PAGE REFRESH RULE

Selecting location must not reload the full page.

When user selects Rajkot:

* Taluka/locality options should fetch dynamically.
* Current form data should remain.
* No full page reload.
* No lost typed values.
* No broken state.

When user changes district after selecting taluka:

* Clear dependent taluka/city/village/locality fields.
* Show confirmation if data loss is significant.
* Fetch new options.

---

# 18. SEARCHABLE DROPDOWN RULE

Large lists must be searchable.

Applies to:

* District
* Taluka
* City
* Village
* Locality
* Society
* Project
* Building

Searchable dropdown should support:

* Typing
* Debounced search
* Loading state
* No result state
* Add/request missing option
* Keyboard navigation if possible
* Mobile-friendly bottom sheet

Do not use very long native dropdowns for thousands of villages.

---

# 19. MISSING LOCATION RULE

If location is missing, user must have a way to continue safely.

Options:

* Request new location
* Add custom location for review
* Enter manual text field
* Select nearby/other option
* Contact support if blocked

Example UI:

```txt id="8xf8t5"
Can’t find your village/locality? Request new location
```

or:

```txt id="dwbqm4"
Add custom location
```

Missing location request should collect:

* Requested name
* Type: city/village/locality/society/building/landmark
* Parent location
* User note
* Map point if useful
* User ID
* Status
* Admin decision

---

# 20. LOCATION REQUEST STATUS

Location request statuses:

```txt id="7alrng"
Submitted
Under Review
Approved
Rejected
Duplicate
Merged
Need More Details
Archived
```

If approved:

* Location becomes available in dropdowns.
* User can use it.
* Linked entity updates if needed.

If rejected:

* Show reason.
* Allow resubmit if appropriate.

If duplicate:

* Link to existing location.

---

# 21. CUSTOM LOCATION IN PROPERTY POSTING

If user writes custom location during property posting:

Options:

1. Save property as draft until location approved.
2. Allow listing pending moderation with custom location.
3. Admin reviews property and location together.
4. Admin maps custom location to existing/new location.

Do not publish unverified messy location if it breaks search/SEO.

Admin should be able to normalize.

---

# 22. ADMIN LOCATION MANAGEMENT

Admin/Super Admin should manage:

* States
* Districts
* Talukas
* Cities
* Villages
* Areas
* Localities
* Societies
* Buildings
* Landmarks
* Location requests
* Duplicate locations
* Slugs
* Active/inactive status
* SEO enable/disable
* Nearby city mapping
* Popular city/locality order
* Banner ad city targeting
* City manager assignment

Admin location changes must be audit logged if implemented.

---

# 23. LOCATION DUPLICATE HANDLING

Duplicate locations must be handled.

Examples:

* “Kalavad Road”
* “Kalawad Road”
* “Kalawad Rd”
* “Kld Road”

System should allow aliases.

Location record can include:

* Canonical name
* Alternative names
* Common misspellings
* Gujarati/Hindi names if later multilingual
* Slug
* Parent location

Admin can merge duplicates.

When merging:

* Update linked properties
* Update linked requirements
* Update SEO URLs/redirects
* Preserve audit log

---

# 24. LOCATION SLUG RULE

Every SEO-relevant location needs slug.

Slug examples:

```txt id="1kh3up"
rajkot
ahmedabad
kalawad-road
mota-mava
satellite
vesu
```

Slug rules:

* Lowercase
* Hyphen-separated
* Unique within parent
* Stable after publishing
* Redirect if changed
* English preferred for initial SEO

Do not create duplicate slugs.

---

# 25. LOCATION SEO RULE

City/locality data powers SEO.

SEO pages:

```txt id="s3rln3"
/city/rajkot
/city/rajkot/property-sale
/city/rajkot/flats
/locality/rajkot/kalawad-road
```

Location data must support:

* SEO title
* Meta description
* H1
* Slug
* Parent city
* Breadcrumb
* Active status
* Index/noindex status
* Listing count if real
* Popular localities
* Nearby localities
* Redirects

Do not index empty/thin location pages.

Do not show fake property count.

---

# 26. LOCATION AND HOMEPAGE SEARCH

Homepage search must use selected location.

If user selects Rajkot:

* Search starts with Rajkot context.
* Quick filters use Rajkot.
* Banner ads prioritize Rajkot.
* SEO links show Rajkot.
* Popular localities show Rajkot.
* Property cards show Rajkot first.
* Buyer requirement suggestions use Rajkot if applicable.

If city changes, homepage context updates.

Do not require full page refresh.

---

# 27. LOCATION AND BANNER ADS

Banner ads use city targeting.

Advertiser can select:

* City
* Multiple cities if plan allows
* District if allowed
* Gujarat-wide if package allows
* Specific localities if future feature

Display priority:

1. User selected city
2. User profile city
3. Browser/IP city estimate
4. Gujarat-wide ads
5. Other city ads

Example:

Rajkot user:

* Rajkot ads first
* Gujarat-wide ads next
* Other city ads after

Ahmedabad user:

* Ahmedabad ads first
* Gujarat-wide ads next
* Other city ads after

Banner ad location must be structured, not free text.

---

# 28. LOCATION AND REQUIREMENTS

Buyer/Tenant requirements must support structured location.

Requirement form may include:

* Preferred state
* Preferred city
* Preferred localities
* Nearby areas
* Taluka/village for land
* Multiple locations if allowed
* Radius/nearby preference if map supported
* Must-have location vs flexible location

Broker/Agency/Builder can search/filter requirements by location.

Do not expose buyer private address.

---

# 29. LOCATION AND BROKER/AGENCY/BUILDER PROFILES

Business profiles should have operating areas.

Broker profile:

* Operating cities
* Operating localities
* Property types by area

Agency profile:

* Head office city
* Operating cities
* Localities
* Branches if implemented

Builder profile:

* Project cities
* Office city
* Operating markets

Real Estate Group:

* Target cities for ads
* Operating city

These locations help search, SEO and lead relevance.

---

# 30. LOCATION AND ADMIN CITY MANAGER

City Manager role should be scoped by location.

City Manager can manage assigned city/district data only if permissions allow.

Server-side checks must enforce:

* Assigned city
* Assigned district
* Assigned taluka if applicable
* Permission scope

Do not rely only on UI hiding.

City Manager must not see or manage unrelated cities unless assigned.

---

# 31. LOCATION AND MAP

Map location is optional/provider-controlled.

Map modes:

* Disabled
* Free/embed/trial mode
* Premium API mode

Property/project location can store:

* Latitude
* Longitude
* Map address
* Place ID if Google Maps API is used
* Accuracy level
* Approximate vs exact location flag

Privacy rule:

* Some listings may show approximate map only.
* Exact location can be hidden until contact/lead if policy allows.

Do not fake map.

Do not show interactive map if provider missing.

---

# 32. EXACT VS APPROXIMATE LOCATION

Property owners may want privacy.

Support location visibility:

* Exact public location
* Approximate locality only
* Landmark only
* Exact after contact
* Hidden exact address

Public card may show:

```txt id="xgh5km"
Kalawad Road, Rajkot
```

Detail page may show approximate map.

Lead receiver/admin sees exact location if permitted.

Do not expose exact address if hidden.

---

# 33. PIN CODE SUPPORT

Pin Code should be supported.

Use cases:

* Property posting
* Search filters if useful
* Address validation
* SEO/locality mapping
* Lead relevance

Pin Code should be optional in some rural cases but recommended.

Pin Code must be validated format:

```txt id="jy68jd"
6-digit Indian PIN code
```

Do not force wrong pin codes.

---

# 34. LANDMARK SUPPORT

Landmark is useful for Indian real estate.

Landmark should be free-text or selected from database.

Examples:

* Near school
* Near hospital
* Near temple
* Near main road
* Near mall
* Near railway station
* Near bus stand

Landmark can be public-safe.

Do not use landmark as replacement for structured location.

---

# 35. ADDRESS PRIVACY RULE

Address fields need privacy levels.

Public-safe:

* City
* Locality
* Society/project if allowed
* Landmark if allowed

Private or conditional:

* Full address
* Unit number
* Floor/unit exact detail
* Owner address
* Survey number if sensitive
* Private land documents

Admin can see more based on permission.

Public search must not expose private location fields.

---

# 36. LOCATION VALIDATION RULE

Location form validation:

Required based on type.

Common required fields:

* State
* District
* City or Village
* Locality/Area where applicable

Land/agriculture required:

* District
* Taluka
* Village or land area
* Area unit

Urban property required:

* City
* Locality/Area
* Society/Project if known

Project required:

* City
* Locality
* Project address
* Map point if required by admin

Validation should be dynamic.

Do not require irrelevant fields.

---

# 37. LOCATION FORM UX

Location form should be user-friendly.

Rules:

* Step-by-step when long
* Searchable dropdowns
* Auto-fetch dependent data
* Show loading indicators
* Show “not found” actions
* Preserve entered data
* Clear dependent fields when parent changes
* Mobile bottom sheet for large selectors
* No page refresh
* No horizontal scroll
* Clear error messages

---

# 38. MOBILE LOCATION UX

On mobile:

* Use bottom sheets for large lists.
* Search input should auto-focus.
* Current selection visible.
* Back icon available.
* List items large enough to tap.
* Add missing location option visible.
* No tiny dropdowns.
* No long native select for large village lists.
* Keyboard should not hide CTA.

Mobile location selection must feel app-like.

---

# 39. LOCATION SEARCH PERFORMANCE

Location data can be large.

Performance rules:

* Do not load all villages at once.
* Use API/server action with parent ID.
* Use debounced search.
* Cache common city/locality lists.
* Index parent_id/name/slug/type.
* Paginate large location lists if needed.
* Keep dropdown response lean.
* Avoid huge JSON on homepage.

---

# 40. LOCATION DATABASE DESIGN

Possible tables:

## countries

* id
* name
* slug
* iso_code
* active

## states

* id
* country_id
* name
* slug
* active

## districts

* id
* state_id
* name
* slug
* active

## talukas

* id
* district_id
* name
* slug
* active

## places

* id
* state_id
* district_id
* taluka_id
* parent_id
* name
* slug
* type
* pin_code
* latitude
* longitude
* active
* seo_enabled
* noindex
* created_by
* approved_by
* status

Place type examples:

```txt id="ytzrbx"
city
town
village
area
locality
society
project
building
landmark
```

Alternative design can use separate tables, but must support hierarchy.

---

# 41. LOCATION REQUEST TABLE

Location request may include:

* id
* requested_by_user_id
* requested_name
* requested_type
* parent_state_id
* parent_district_id
* parent_taluka_id
* parent_city_id
* parent_locality_id
* note
* latitude
* longitude
* status
* admin_note
* approved_location_id
* created_at
* updated_at

Statuses:

```txt id="mnsk14"
submitted
under_review
approved
rejected
duplicate
merged
need_more_details
archived
```

---

# 42. PROPERTY LOCATION FIELDS

Property table should store:

* state_id
* district_id
* taluka_id
* city_id
* village_id
* area_id
* locality_id
* society_id
* building_id
* landmark_text
* address_line
* pin_code
* latitude
* longitude
* location_visibility
* map_accuracy
* custom_location_text if pending
* location_request_id if used

Do not rely only on address text.

---

# 43. PROJECT LOCATION FIELDS

Project table should store:

* state_id
* district_id
* city_id
* locality_id
* project_location_id if using places
* address_line
* landmark
* pin_code
* latitude
* longitude
* rera_location_text if needed
* location_visibility
* map_accuracy

---

# 44. REQUIREMENT LOCATION FIELDS

Requirement table should support:

* preferred_state_ids
* preferred_district_ids
* preferred_taluka_ids
* preferred_city_ids
* preferred_village_ids
* preferred_locality_ids
* location_flexible boolean
* nearby_allowed boolean
* radius_km if map/radius implemented
* custom_location_note

Requirements can have multiple preferred locations.

---

# 45. BUSINESS PROFILE LOCATION FIELDS

Broker/Agency/Builder profile should support:

* office_state_id
* office_district_id
* office_city_id
* office_locality_id
* office_address
* operating_city_ids
* operating_locality_ids
* operating_district_ids
* service_area_notes
* latitude/longitude if office map enabled

---

# 46. BANNER ADS LOCATION FIELDS

Banner ad campaign should support:

* target_city_ids
* target_district_ids if allowed
* target_state_ids if Gujarat-wide
* target_locality_ids if future
* fallback_scope
* priority_city_id
* display_order if admin override
* active status
* start_at
* end_at

City targeting must be structured.

---

# 47. LOCATION API / SERVER ACTIONS

Required actions may include:

* Get states
* Get districts by state
* Get talukas by district
* Get cities by district/taluka
* Get villages by taluka
* Search localities
* Search societies/projects
* Request missing location
* Approve location request
* Merge duplicate location
* Get nearby cities
* Get popular locations
* Get city SEO data

All actions must validate permissions.

Admin actions must be protected.

---

# 48. LOCATION FEATURE FLAGS

Possible feature flags:

```txt id="5etawq"
locations.enabled
locations.gujarat_only.enabled
locations.taluka.enabled
locations.village.enabled
locations.locality.enabled
locations.society.enabled
locations.building.enabled
locations.missing_location_request.enabled
locations.admin_approval_required
locations.map_point.enabled
locations.pin_code.enabled
locations.nearby_city_fallback.enabled
locations.city_seo.enabled
locations.locality_seo.enabled
locations.banner_city_targeting.enabled
locations.city_manager_scope.enabled
```

If feature flag is off, hide related UI and block backend actions where needed.

---

# 49. LOCATION ADMIN ROUTES

Admin routes:

```txt id="a1aqdi"
/admin/locations
/admin/locations/states
/admin/locations/districts
/admin/locations/talukas
/admin/locations/cities
/admin/locations/villages
/admin/locations/localities
/admin/locations/societies
/admin/locations/buildings
/admin/locations/landmarks
/admin/locations/requests
/admin/locations/duplicates
/admin/locations/import
/admin/locations/seo
/admin/locations/nearby
```

Super Admin routes:

```txt id="bu4v5n"
/admin/super/locations
/admin/super/locations/settings
/admin/super/locations/feature-flags
/admin/super/locations/import-export
/admin/super/locations/city-manager-scope
```

Only show implemented routes.

---

# 50. LOCATION USER ROUTES / SURFACES

User-facing surfaces:

* Header city selector
* Homepage search city selector
* Search results filters
* Property posting address form
* Requirement posting location form
* Profile operating area form
* Banner ad targeting form
* City SEO page
* Locality SEO page
* Contact/support location field if needed

No random duplicate location UI.

---

# 51. LOCATION IMPORT RULE

Admin/Super Admin should eventually support importing locations.

Import file can include:

* State
* District
* Taluka
* City/Village
* Locality
* Pin Code
* Slug
* Latitude
* Longitude

Import should validate:

* Duplicate names
* Parent hierarchy
* Slug uniqueness
* Required fields
* Invalid characters
* Existing records

Import should preview before applying.

If import is not implemented, document manual seed process.

---

# 52. LOCATION EXPORT RULE

Optional export:

* Export location data
* Export location requests
* Export duplicates
* Export city SEO data

Only Admin/Super Admin can export.

Respect privacy.

---

# 53. LOCATION AUDIT LOG RULE

Audit logs should track:

* Location created
* Location edited
* Location deleted/deactivated
* Location merged
* Location request approved/rejected
* Slug changed
* SEO status changed
* Nearby city mapping changed
* City manager assignment changed

Audit logs must be real if visible.

---

# 54. LOCATION AND NO-FAKE UI RULE

Do not fake:

* Current city detection
* IP city detection
* Browser location
* Map location
* Location suggestions
* Popular localities
* Listing count by city
* Nearby city logic
* Location approval status
* City SEO data

If data/provider is missing:

* Show manual city selector.
* Show empty state.
* Hide unsupported suggestions.
* Show setup-required in admin/dev context.

---

# 55. LOCATION EMPTY STATE

Empty state examples:

No talukas found:

```txt id="1kgzba"
No talukas found for this district. You can request a new location.
```

No village found:

```txt id="y6f992"
Village not found. Add or request a village for admin review.
```

No locality found:

```txt id="bfbwky"
Locality not found. You can type a custom locality or request it.
```

No city data:

```txt id="d1g98f"
City data is not available yet. Please select another city or request location support.
```

---

# 56. LOCATION ERROR STATE

Error state examples:

```txt id="cy9vyd"
Could not load districts. Please try again.
```

```txt id="9e1k8s"
Could not submit location request. Please check details and try again.
```

```txt id="93cfh1"
This location already exists. Please select it from the list.
```

Do not expose raw database errors.

---

# 57. LOCATION SUCCESS STATE

Success examples:

```txt id="4girri"
Location request submitted for admin review.
```

```txt id="ti5mtt"
Location added successfully.
```

```txt id="l4zuq8"
Location updated.
```

```txt id="4mne69"
Duplicate location merged.
```

Success only after server confirmation.

---

# 58. LOCATION MANUAL VERIFICATION CHECKLIST

Manual verification prompt should check:

* State dropdown loads Gujarat.
* District dropdown loads after state.
* Taluka dropdown loads after district.
* City/village dropdown loads after taluka.
* Locality dropdown loads after city.
* No full page refresh happens.
* Data is preserved when possible.
* Dependent fields clear correctly when parent changes.
* Missing location request works.
* Admin can approve/reject location request if implemented.
* Approved location appears in dropdown.
* Property posting uses structured location.
* Land posting shows taluka/village fields.
* Flat posting hides irrelevant village fields.
* Search uses selected city.
* Homepage city selector affects search context.
* Banner ads can target city.
* SEO city route uses city slug.
* Mobile dropdown/bottom sheet is usable.
* No horizontal scroll.
* No fake city counts.
* No screenshot/video capture required.

---

# 59. LOCATION PASS / FAIL RULE

Location phase is PASS only if:

* Location hierarchy is implemented or clearly planned in registry.
* Gujarat state is supported.
* District/taluka/city/village structure exists.
* Cascading dropdowns work without page refresh.
* Missing location request exists or safe fallback exists.
* Property posting stores structured location.
* Land/village flows support taluka/village.
* Search uses city/location.
* Header city selector works.
* Admin can manage locations if phase includes admin.
* No fake location detection.
* No hidden private address leaks.
* Mobile location UI works.
* Feature registry updated.
* Manual verification completed.

If property posting uses only one free-text address field, mark FAIL or PARTIAL depending phase.

If city selection reloads page and loses form data, mark FAIL.

If village/taluka requirement is ignored, mark PARTIAL or FAIL depending phase scope.

---

# 60. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`
* `05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those docs for search, SEO, property posting, banner ads, provider modes, RBAC and manual verification details.

---

# 61. END OF FILE

This file defines the Gujarat location hierarchy, city, district, taluka, village, locality, society, building and address system for My Gujarat Property.

Location must be structured, cascading, no-refresh, searchable, admin-manageable, SEO-ready, banner-ad-ready, property-posting-ready and scalable beyond Gujarat.

Nothing from uploaded docs or user chat instructions should be skipped.
