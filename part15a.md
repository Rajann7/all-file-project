PART 15A — IMPLEMENTATION PROMPT: UX CONVERSION REDESIGN + PROPERTY POSTING FIELD COMPLETION + WEBP MEDIA SYSTEM

You are Claude AI acting as a senior full-stack engineer, product designer, conversion UX expert, real estate marketplace architect, Supabase engineer, QA engineer and security reviewer.

Project: My Gujarat Property.

Current project state:

* Prompts/Parts 1 to 14 are already implemented.
* Supabase API is configured.
* No external provider APIs are configured yet.
* OTP random/static mode is allowed only in development for testing.
* Production must never allow random/static/dev OTP.
* If any provider is missing, show setup-required/disabled state and do not fake success.
* This phase is not for adding new unrelated advanced features.
* This phase is for conversion-focused redesign, UI/UX cleanup, role-wise flow correction, property posting completion, media upload improvement and no-confusion user experience.

Read these docs first:

* 00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md
* 01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md
* 02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md
* 03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md
* 04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md
* 05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md
* 06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md
* 07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md
* 08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md
* 09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md
* 10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md
* 11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md
* 12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md
* 13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md
* 14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md
* 15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md
* 16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md
* 17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md
* 18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md
* 19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md
* 20_CMS_BLOG_STATIC_PAGES_LEGAL_CONTENT_SPEC.md
* 21_FEATURE_REGISTRY_TEMPLATE.md
* 22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md
* 23_CLAUDE_PART_WISE_IMPLEMENTATION_AND_SEPARATE_MANUAL_VERIFICATION_PROMPTS.md

Core goal:
Make the full website user-friendly, easy to understand, high-conversion, mobile-first, role-aware and professional. A new user should not be confused after opening the website. Every screen must clearly guide the user to the correct next action.

Strict rules:

* No fake production UI.
* No fake production data.
* No fake property cards.
* No fake counts.
* No fake leads.
* No fake verification badge.
* No fake payment success.
* No fake provider success.
* No fake WhatsApp/SMS/email sent.
* No hidden phone leak.
* No private document public URL.
* No admin route public access.
* No service role key in client.
* No broken placeholder routes.
* No dead buttons.
* No confusing CTA.
* No horizontal scroll.
* No important text wrap.
* If feature is incomplete, hide it or show safe setup-required/disabled state.
* Always update Feature Registry.
* Always output implementation report.

IMPORTANT MEDIA UPLOAD CHANGE:
The property image upload UI must NOT show maximum MB text to normal users.
Remove text like:

* “Maximum 5MB”
* “Max size 10MB”
* “Upload up to X MB”
* Any visible maximum MB guidance on property image upload UI.

Instead show user-friendly guidance:

* “Upload clear property photos.”
* “Images will be optimized automatically.”
* “Recommended ratio: 4:3 or 16:9.”
* “Use clear daylight photos for better response.”
* “You can reorder photos after upload.”

Backend/storage must still be safe:

* Do not allow unsafe huge upload to break app.
* Do not show raw technical file-size errors.
* If upload fails because file is too large/system cannot process, show friendly message:
  “This image could not be processed. Please try another clear photo.”
* Do not expose raw Supabase/storage errors.

WEBP IMAGE COMPRESSION REQUIREMENT:
Implement a real image optimization pipeline for property/project/profile media where applicable:

1. Accept common user image formats:

   * jpg
   * jpeg
   * png
   * webp
   * heic/heif only if current stack can support safely; otherwise show friendly unsupported message.
2. Convert uploaded property/project images to WebP before final storage.
3. Compress/resize images safely for web performance.
4. Store optimized WebP version in storage.
5. Generate/use responsive variants if feasible:

   * thumbnail
   * card
   * detail/gallery
6. Keep original only if required for crop/edit workflow; otherwise do not store unnecessary original.
7. Use safe filenames and storage paths.
8. Keep public property/project images in public-approved media bucket.
9. Keep private documents in private bucket.
10. Do not put verification/ownership documents in public storage.
11. Preview image after compression.
12. Reorder images.
13. Replace image.
14. Remove image.
15. Set cover image.
16. Crop/fit image if crop feature exists.
17. Do not fake upload success.
18. Success only after actual upload/storage record exists.

MEDIA UI REQUIREMENT:
For property images:

* Show drag/drop on desktop if implemented.
* Show large tap upload card on mobile.
* Show photo grid preview.
* Show cover image label.
* Show image count based on real plan/limit if implemented.
* If image count limit is not implemented, do not fake limit.
* Do not show maximum MB in property image UI.
* Show recommended ratio only.
* Show user-friendly error only.

For project images:

* Same compression and WebP rule.
* Support project gallery.
* Support unit/floor plan images if implemented.
* Support brochure upload separately.
* Brochure can remain PDF if real file.
* Do not convert documents to WebP.

For banner ads:

* Keep separate banner image rules.
* Desktop/tablet/mobile banner variants can show recommended ratio.
* Banner upload must not be confused with property image upload.

STEP 1 — FULL CURRENT APP UX AUDIT
Before changing code, inspect current app screen by screen.

Audit without login:

* Homepage
* Header
* Mobile header
* City selector
* Search
* Banner carousel
* Homepage feed
* Property category sections
* Search result page
* Property detail page
* Login/Register modal
* Post Property intent
* Post Requirement intent
* Pricing page
* Footer pages
* Public profile pages

Audit with roles:

* Buyer
* Tenant
* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Admin
* Super Admin

For every screen check:

* What is visible?
* What should be visible?
* What should not be visible?
* Is CTA clear?
* Is page easy to understand?
* Is user confused?
* Is redirect correct?
* Is role correct?
* Is data real?
* Are filters present where needed?
* Is mobile usable?
* Is text wrapping?
* Is scroll/back/touch behavior smooth?
* Are loading/empty/error/success states good?
* Are click actions opening useful details?
* Are important IDs visible in dashboards/admin only?
* Are private fields hidden publicly?

STEP 2 — HOMEPAGE CONVERSION REDESIGN
Improve homepage after existing implementation.

Requirements:

1. Homepage must be search-first and city-first.
2. Header must show city selector on desktop and mobile.
3. Mobile header must show logo + “My Gujarat Property” in one line without text wrap.
4. Add Gujarat/state context in city selector.
5. City change must update homepage feed without full page reload.
6. Search tabs/intent should be clean:

   * Buy
   * Rent
   * Commercial
   * Land / Plot
   * Projects
   * PG / Hostel if enabled
   * Requirements if enabled
7. Banner ads carousel must remain real-data based.
8. Banner ads must not dominate the full page.
9. After banner carousel, show real-data-based property sections:

   * Flats / Apartments
   * Houses / Villas
   * Rent Properties
   * Plots / Land
   * Agricultural / Farm Land if data exists
   * Commercial Properties
   * Shops / Offices if data exists
   * Warehouse / Industrial if data exists
   * Projects
   * PG / Hostel if enabled
   * Latest Properties
   * Recently Updated
   * Direct Owner Properties if real
   * Verified Properties if real
   * Requirements if enabled and public/allowed
10. Each section must have:

* title
* short helper line
* carousel or horizontal cards
* View All button
* selected city/location filtering
* real empty state or hide if no data
* no fake listing
* no fake count
* no fake verified badge

11. Homepage should have clear conversion CTAs:

* Search Property
* Post Property
* Post Requirement
* View Pricing
* For Brokers
* For Agencies
* For Builders

12. Keep CTA hierarchy clear:

* one primary CTA per section
* secondary actions smaller
* never show 10 equal buttons.

STEP 3 — HEADER, ROLE UI AND REDIRECT FIXES
Fix global role-based UI.

Guest:

* Show Login/Register.
* Show city selector.
* Show search.
* Show Post Property CTA.
* Show Post Requirement CTA if enabled.
* Contact/Post actions open Login/Register and preserve intent.

Logged-in user:

* Hide Login/Register.
* Show profile/avatar.
* Show active role.
* Show correct dashboard link.
* Show role switcher only if user has approved roles.
* Pending role must not grant access.

Buyer/Tenant:

* Show search, saved, requirements, profile.
* Do not show broker/agency/admin tools.
* Post Property should show role request/upgrade, not direct posting.

Owner:

* Show dashboard, properties, leads, post property, profile.

Broker:

* Show dashboard, listings, requirement feed, leads, proposals, profile.

Agency Owner:

* Show agency dashboard, listings, agents/team, leads, assignments, banner ads if enabled.

Agency Agent:

* Show assigned leads, assigned site visits, tasks, profile.
* Do not show property posting by default.
* Do not show agency billing/subscription unless permission allows.
* Do not show all agency data unless permission allows.

Builder:

* Show projects, units, leads, site visits, banner ads if enabled.

Admin/Super Admin:

* Show admin workspace.
* Normal public user actions should not mix with admin workspace.
* Super Admin default route should prefer super admin control center unless preserving safe next route.

STEP 4 — PROPERTY POSTING FLOW REBUILD / COMPLETION
Property posting must start with listing purpose and property type. Do not show one huge generic form.

Required step flow:

1. Select Listing Purpose
2. Select Property Category / Type
3. Location
4. Basic Details
5. Pricing / Rent / Financial Details
6. Type-Specific Details
7. Amenities / Features
8. Media Upload
9. Contact / Visibility
10. Preview
11. Save Draft / Submit for Approval
12. Status / Approval / Next Action

Mobile:

* Step-based.
* Progress indicator.
* Back button.
* Save draft.
* Sticky Next button.
* Keyboard-safe layout.
* Bottom sheet selectors.
* Full-screen crop if crop exists.
* No horizontal scroll.
* No long desktop form.

Desktop:

* Stepper or section cards.
* Optional sticky progress sidebar.
* Optional preview panel.
* Clean layout.
* Do not show irrelevant fields.

POST PROPERTY ACCESS:
Allowed:

* Owner
* Broker
* Agency Owner
* Builder for projects/units
* Admin/Super Admin if permission allows
* Agency Agent only if agency owner explicitly delegates posting permission

Restricted:

* Guest
* Buyer
* Tenant
* Agency Agent without posting delegation

Guest:

* Opens Login/Register.
* Preserves intent.

Buyer/Tenant:

* Show role change/request screen.

Agency Agent:

* By default cannot post.
* If delegated, listing source remains Agency and audit trail must show agent posted under agency permission.

SOURCE TAG:
Source tag must be derived from active role/entity:

* Direct Owner
* Broker
* Agency
* Builder
* Developer if implemented
* Real Estate Group if applicable
* Admin Added if allowed

User must not manually fake source tag.

STEP 5 — COMPLETE PROPERTY TYPE FIELD MATRIX
Audit existing property posting fields against docs and add missing fields. Nothing important should be missing. Type-specific fields must control:

* visible form fields
* required fields
* optional fields
* validations
* search filters
* card display
* detail page sections
* admin fields
* database schema
* API/server actions
* RLS/storage rules

COMMON FIELDS FOR MOST LISTINGS:

* listing_title
* listing_purpose
* property_category
* property_type
* description
* state
* district
* taluka if relevant
* city_or_village
* locality_or_area
* society_name
* project_name if relevant
* building_name
* tower_or_block
* landmark
* address_line public/private rules
* pin_code
* map_location if provider available
* area
* area_unit
* price_or_rent
* availability_status
* ownership_type if relevant
* contact_preference
* contact_visibility
* listing_source
* brokerage_policy
* media
* terms_acceptance
* draft_status
* approval_status
* expiry_date if enabled
* last_verified_at
* next_verification_due_at

COMMON STATUS OPTIONS:

* Draft
* Pending Approval
* Active
* Need Changes
* Rejected
* Sold
* Rented
* Leased
* Expired
* Hidden
* Archived
* Deleted

COMMON AVAILABILITY OPTIONS:

* Available Now
* Available From Date
* Ready to Move
* Under Construction
* Possession Date
* Occupied
* Vacant
* Pre-launch
* New Launch
* Resale
* Upcoming

COMMON PRICE FIELDS:
Sale:

* expected_price
* price_negotiable
* price_per_area_unit
* all_inclusive_price if applicable
* maintenance_charges if relevant
* other_charges if relevant
* brokerage_policy

Rent:

* monthly_rent
* security_deposit
* maintenance
* rent_negotiable
* advance_months
* lock_in_period
* available_from
* brokerage_policy

Lease:

* lease_amount
* deposit
* lease_term
* lock_in_period
* escalation if implemented
* CAM/maintenance if commercial

Land:

* total_price
* price_per_area_unit
* negotiable
* brokerage_policy
* platform must not collect property token/booking amount

BROKERAGE OPTIONS:

* No Brokerage
* Brokerage Extra
* Brokerage Included
* Brokerage Negotiable
* As per discussion

STEP 6 — RESIDENTIAL PROPERTY FIELD MATRIX
Residential types:

* Flat / Apartment
* Independent House
* Villa
* Bungalow
* Row House
* Penthouse
* Studio Apartment
* Duplex
* Farm House
* Residential Plot if treated under residential
* Serviced Apartment if enabled

Residential required/important fields:

* BHK / 1RK / studio type
* bathrooms
* balconies
* super_built_up_area
* built_up_area
* carpet_area if available
* area_unit
* floor_number
* total_floors
* furnishing_status
* parking
* property_age
* facing
* possession_status
* available_from if rent
* ownership_type
* society_name
* tower/block
* lift
* power_backup
* water_supply
* gas_pipeline
* security
* amenities
* maintenance_charges
* preferred_tenant if rent
* family/bachelor allowed if rent
* pet_allowed if implemented
* description
* photos
* floor_plan if available
* brochure if project-linked

Flat/Apartment should show:

* BHK
* floor
* total floors
* carpet/built-up/super built-up
* bathrooms
* balconies
* furnishing
* parking
* society/project
* lift
* maintenance
* amenities

Independent House/Villa/Bungalow/Row House should show:

* BHK
* plot_area if relevant
* built_up_area
* floors
* bedrooms/bathrooms
* balconies
* parking
* garden/open space
* road width if relevant
* facing
* ownership
* construction age
* water/electricity
* boundary/wall if relevant

Studio Apartment should show:

* studio type
* area
* bathroom
* furnishing
* floor
* rent/sale pricing
* amenities

Farm House under residential/farm must show:

* land area
* built-up area
* room count
* water source
* electricity
* road access
* boundary
* farm/garden details
* pool if applicable
* village/taluka if rural

Do not show irrelevant land survey fields for urban flat.

STEP 7 — COMMERCIAL PROPERTY FIELD MATRIX
Commercial types:

* Shop
* Office
* Showroom
* Warehouse
* Godown
* Industrial Shed
* Factory
* Commercial Land
* Co-working Space
* Restaurant / Cafe Space
* Clinic / Medical Space
* Hotel / Guest House if implemented
* Retail Space
* Business Center
* Plot for Commercial Use

Commercial required/important fields:

* commercial_type
* purpose sale/rent/lease
* area
* area_unit
* floor
* total_floors if building
* frontage
* road_width
* main_road
* corner_property
* parking
* washroom
* power_load
* ceiling_height for warehouse/factory/shed
* loading_unloading
* shutter_size if shop/warehouse
* lift/service_lift
* fire_safety if relevant
* water_supply
* electricity
* furnishing/fitout
* occupancy_status
* suitable_for
* business_type_suitability
* possession/available_from
* rent/deposit/lease terms
* CAM/maintenance
* brokerage_policy

Shop should show:

* floor/ground floor
* frontage
* road width
* main road/corner
* shutter
* washroom
* parking
* suitable business
* footfall/market nearby if implemented

Office should show:

* carpet/built-up area
* seats/cabins if fitted
* conference room if fitted
* pantry
* washroom
* lift
* parking
* power backup
* furnishing
* building type

Showroom should show:

* frontage
* ceiling height
* road width
* glass frontage if implemented
* parking
* ground/main road
* suitable for

Warehouse/Godown should show:

* covered area
* plot area if relevant
* ceiling height
* loading dock
* truck access
* road width
* power load
* water
* fire safety
* floor type
* office cabin if any

Industrial Shed/Factory should show:

* plot area
* built-up area
* power load
* crane facility if any
* shed height
* entry gate size
* road access
* water
* drainage
* zoning/industrial estate
* pollution category if implemented

Do not show BHK, bedrooms, balconies or family tenant fields in commercial.

STEP 8 — LAND / PLOT / AGRICULTURAL FIELD MATRIX
Land/plot types:

* Residential Plot
* Commercial Plot
* Industrial Plot
* Open Land
* NA Land
* Agricultural Land
* Farm Land
* Investment Land
* Warehouse Land
* Mixed-use Land
* Farm House Land
* Village Land
* Roadside Land

Land/plot required/important fields:

* land_type
* district
* taluka
* city_or_village
* locality/area
* survey_number/block_number if allowed
* plot_number if allowed
* total_area
* area_unit
* frontage
* depth if available
* road_access
* road_width
* corner_plot
* boundary_wall
* gated_plotting if applicable
* title_clear if declared
* NA/NOC status
* agriculture/non-agriculture
* zoning
* FSI/FAR if available
* water_availability
* electricity_availability
* drainage
* irrigation if agriculture
* soil_type if agriculture
* borewell/well/canal access
* farm road access
* nearby landmark
* distance from highway/main road if relevant
* ownership_type
* price_per_area_unit
* total_price
* brokerage_policy
* documents availability flag only, documents private
* map/location if provider available
* possession/availability

Residential Plot should show:

* plot area
* dimensions
* road width
* society/project/plotting scheme
* NA status
* boundary
* water/electricity
* nearby landmark

Commercial/Industrial Plot should show:

* zoning
* road width
* frontage
* power
* water
* transport access
* industrial estate
* commercial use permission

Agricultural/Farm Land should show:

* district
* taluka
* village
* survey/block number if allowed
* area in bigha/acre/hectare/guntha
* irrigation
* water source
* electricity
* soil type
* crop history if implemented
* road access
* boundary
* farmhouse/structure if any
* agriculture status
* conversion/NA status if applicable

Do not show BHK, bathrooms, furnishing, floor or balconies for land.

STEP 9 — PG / HOSTEL / CO-LIVING FIELD MATRIX
PG/Hostel types:

* Boys PG
* Girls PG
* Co-living
* Student Hostel
* Working Men Hostel
* Working Women Hostel
* Shared Room
* Private Room
* Dormitory
* Paying Guest Home

Required/important fields:

* pg_type
* gender_allowed
* tenant_type student/working professional
* room_type
* sharing_type
* rent_per_bed_or_room
* security_deposit
* food_included
* meal_type
* AC/non-AC
* attached_bathroom
* furnishing
* Wi-Fi
* laundry
* housekeeping
* parking
* curfew_rules
* visitor_rules
* minimum_stay
* available_from
* total_beds
* available_beds
* occupancy_status
* rules
* photos
* contact_preference
* brokerage if applicable

Do not show sale price, ownership type, BHK as primary, land survey, commercial frontage.

STEP 10 — PROJECT / BUILDER INVENTORY FIELD MATRIX
Project types:

* Residential Project
* Commercial Project
* Mixed-use Project
* Villa Project
* Plotting Project
* Apartment Project
* Township
* Industrial Project if implemented

Project is different from individual property posting.

Project required/important fields:

* project_name
* builder_entity
* developer_entity if separate
* project_type
* project_status
* launch_date if available
* possession_date
* RERA number if applicable
* RERA status:

  * RERA provided
  * RERA verified only if admin verified
* project_description
* state/district/city/locality
* address/landmark
* map location if provider available
* total_land_area
* total_towers/blocks
* total_floors
* total_units
* available_units
* unit_configurations
* price_range
* area_range
* amenities
* parking
* brochure
* project_gallery
* floor_plans
* master_plan
* approvals/documents private/admin-controlled
* contact/sales team
* site visit available
* approval/moderation status

Unit configuration fields:

* unit_type
* BHK or commercial unit type
* carpet_area
* built_up_area
* super_built_up_area
* area_unit
* price
* price_per_area_unit
* floor_plan
* bathrooms if residential
* balconies if residential
* parking
* availability
* possession
* inventory status:

  * Available
  * Sold
  * Booked
  * Hold
  * Hidden
* tower/block
* floor range if applicable

Project media:

* project cover image
* gallery
* master plan
* floor plans
* brochure PDF
* construction photos if available
* all images compressed to WebP
* documents private unless public brochure approved

Do not show project as simple single property form.

STEP 11 — INDUSTRIAL / MIXED-USE FIELD SUPPORT
If Industrial or Mixed-use is enabled:
Industrial:

* industrial type
* plot area
* built-up area
* shed height
* power load
* road width
* truck access
* loading/unloading
* crane
* water
* drainage
* fire safety
* zoning/industrial estate
* pollution category if implemented

Mixed-use:

* residential + commercial parts
* total area
* use split
* permission/zoning
* frontage
* floors
* parking
* price/rent logic

If not implemented, hide safely and mark planned in registry.

STEP 12 — SEARCH FILTER + CARD + DETAIL SYNC
After adding fields, sync them across:

* property posting form
* database
* search filters
* property card
* property detail
* dashboard listing management
* admin property detail
* moderation view
* SEO metadata where applicable

Visible filters must work.
If a filter does not work, hide it.

Type-based search rules:

* Residential shows BHK/furnishing/floor/bathroom.
* Rent shows rent/deposit/available from/tenant type.
* Commercial shows commercial type/frontage/road width/power/washroom/suitable for.
* Land shows district/taluka/village/area unit/road access/NA status/zoning/water/electricity.
* PG shows gender/sharing/food/AC/curfew/minimum stay.
* Project shows builder/project/RERA/unit/possession/status/amenities.
* Do not show irrelevant filters.

Property card should be type-aware:
Common:

* image
* title
* price/rent
* city/locality
* property type
* area
* source tag
* status
* CTA

Residential:

* BHK
* bathrooms if useful
* area
* furnishing
* floor if useful

Land:

* area + unit
* land type
* road access if important
* village/taluka if rural

Commercial:

* commercial type
* area
* floor/main road/frontage if useful

PG:

* rent per bed/room
* sharing
* gender
* food/AC badges if real

Project:

* project name
* builder
* price range
* unit types
* possession
* RERA provided/verified if real

STEP 13 — DASHBOARD CRM + STATUS IMPROVEMENTS
Add/improve role dashboards.

All dashboards:

* Add filters.
* Add sorting.
* Add status tabs.
* Add search.
* Row/card click opens full detail drawer/page.
* Desktop tables, mobile cards.
* Show IDs only in dashboard/admin:

  * property_id
  * lead_id
  * requirement_id
  * user_id where allowed
* Do not show fake counts.
* Empty state must guide action.

Lead status pipeline:

* New
* Contacted
* Qualified
* Follow-up
* Site Visit Scheduled
* Visited
* Negotiation
* Converted
* Not Interested
* Invalid
* Closed Lost

Lead fields:

* lead_id
* property_id or requirement_id
* source
* created date/time
* user/contact name
* profile phone or alternate phone badge
* assigned agent
* status
* next follow-up
* last activity
* notes
* contact actions by provider mode

Property status:

* Draft
* Pending Approval
* Active
* Need Changes
* Rejected
* Sold
* Rented
* Leased
* Expired
* Archived

Status history:

* previous status
* new status
* changed by
* role
* reason/note
* timestamp

30-day availability verification:

* Add last_verified_at.
* Add next_verification_due_at.
* Show “Availability verification due” after 30 days or admin-configured days.
* Owner/Broker/Agency/Builder can confirm still available.
* If not verified after grace period, mark needs verification or hide according to admin setting.
* Do not auto-hide without setting/rule.
* Admin/Super Admin can configure verification period if settings exist.
* If scheduled automation not implemented, show due state and add registry blocker.

STEP 14 — AGENCY OWNER / AGENCY AGENT CORRECTION
Agency Owner:

* Can add/invite agents.
* Can activate/deactivate agents.
* Can assign leads.
* Can assign site visits.
* Can assign tasks.
* Can view assigned agent activity if real.
* Can reassign.
* Can control permissions.
* Can view assignment history.
* Can post property from agency account.

Agency Agent:

* Cannot post property by default.
* Can only manage assigned leads.
* Can only manage assigned site visits.
* Can add notes/follow-ups if permitted.
* Can update lead status if permitted.
* Can view assigned listing context.
* Cannot manage agency billing/subscription unless permission.
* Cannot see all agency leads unless permission.
* Agent dashboard must be assignment-scoped.
* Agent actions must be audit logged.

STEP 15 — ROLE-BASED PROFILE REDESIGN
Replace generic profile with role-based profile.

Common:

* full name
* mobile
* email
* avatar
* city
* active role
* available approved roles
* account status
* phone/email verification
* notification preferences
* profile completion
* security/session settings

Buyer:

* preferred cities/localities
* budget range
* BHK/property preference
* saved properties
* requirements
* proposals
* site visits

Tenant:

* rental budget
* rental location preferences
* PG/hostel preference
* move-in date
* tenant type
* saved rentals
* rental requirements

Owner:

* owner details
* own properties
* leads
* site visits
* verification
* plan/subscription
* sold/rented controls

Broker:

* broker display name
* business name
* broker photo/logo
* operating cities/localities
* property categories handled
* brokerage policy
* experience if real
* RERA/license if applicable
* verification status
* public profile slug
* subscription

Agency:

* agency name
* agency logo
* owner name
* office address
* operating cities/localities
* agents/team
* specializations
* verification
* subscription
* public profile slug
* banner ad eligibility

Agency Agent:

* assigned agency
* title/role
* permissions
* assigned cities/localities
* assigned leads/site visits
* profile status
* active/inactive

Builder:

* builder company name
* logo
* authorized person
* office address
* operating cities
* projects
* RERA/company info if applicable
* verification
* subscription
* public profile slug

Real Estate Group if enabled:

* group name
* logo
* contact person
* operating cities
* ad eligibility
* public profile

Avatar/logo upload:

* preview
* crop
* replace
* remove
* validation
* WebP optimization where image
* safe fallback
* no fake images

STEP 16 — PUBLIC BUSINESS PROFILES
Create/improve public profiles:

* Broker
* Agency
* Builder
* Real Estate Group if enabled

Public profile style:

* professional business profile
* cover/logo/avatar
* name
* source/role
* verified badge only if real
* operating cities/localities
* about
* active listings
* projects if builder
* agents if agency and public
* contact CTA
* WhatsApp CTA based on provider mode
* no fake reviews
* no fake awards
* no fake rating
* no fake property count

STEP 17 — ADMIN / SUPER ADMIN DEEP DETAIL UI
Admin:

* users list with filters
* properties list with filters
* leads list with filters
* requirements list with filters
* proposals list with filters
* site visits list with filters
* banner ads if enabled
* verification queue
* reports/fraud queue
* support if implemented

Every item click opens full detail drawer/page.

User detail:

* user_id
* profile data
* roles
* active role
* status
* phone/email verification
* subscriptions
* properties
* leads sent/received where permitted
* requirements
* proposals
* site visits
* banner ads
* payments if implemented
* verification
* reports
* support tickets
* last 7/30 day activity logs if collected
* device/session/IP/location logs only if actually collected
* admin notes
* action history

Property detail:

* property_id
* owner/user/entity
* source tag
* status
* approval/moderation
* city/location
* all type-specific fields
* media
* leads
* visits
* reports
* status history
* edit history if available
* moderation notes

Super Admin:

* full platform overview
* users
* roles
* permissions
* feature flags
* provider modes
* OTP mode
* WhatsApp mode
* map mode
* subscription/pricing controls
* plan limits
* image count limits if implemented
* banner ad pricing/duration/city targeting
* storage/database/API usage if available
* system errors if logged
* audit logs
* staff roles
* maintenance mode
* no fake metrics
* missing data shows not-tracked/setup-required

STEP 18 — APP-LIKE UI POLISH
Improve:

* drawer open/close
* outside click close
* mobile back behavior
* sticky CTA
* sticky mobile bottom nav by role
* smooth scroll behavior
* skeleton loading
* empty states with next action
* error states with retry
* detail drawers
* filter bottom sheets
* large touch targets
* no cramped buttons
* no hidden important CTA
* no confusing route dead-end
* no desktop table on mobile
* no text wrap in important UI
* no horizontal scroll

STEP 19 — DATABASE / VALIDATION / SECURITY
Update schema/server actions if needed.

Ensure:

* properties
* property_details
* property_pricing
* property_location
* property_media
* property_documents
* property_contact_settings
* property_status_history
* property_moderation
* projects
* project_units
* project_media
* property_drafts
* leads
* lead_status_history
* agent_assignments if needed

Security:

* RLS protects private data.
* Public reads only approved active public fields.
* Hidden phone not in public payload.
* Private documents not public.
* User can edit own listing only.
* Agency agent access assignment-scoped.
* Admin actions permission-scoped.
* Service role only server-side.
* Feature flags must block backend action, not only hide UI.

STEP 20 — FEATURE REGISTRY UPDATE
Update Feature Registry for:

* UX conversion audit
* homepage feed sections
* mobile city selector
* city feed refresh without reload
* WebP image compression
* property image max MB UI removal
* media upload optimization
* type-based property fields
* project/unit fields
* property status pipeline
* lead status pipeline
* 30-day availability verification
* agency agent permission/delegation
* role-based profiles
* public business profiles
* admin deep detail views
* super admin controls
* mobile QA
* no-fake QA

At the end output:

## IMPLEMENTATION REPORT

### Part Implemented

PART 15A — UX Conversion Redesign + Property Posting Field Completion + WebP Media System

### Screens Audited

[List screens and roles checked]

### UX Problems Found

[List]

### Property Posting Problems Found

[List]

### Missing Fields Found

[List by property type]

### Media Upload Fixes

[List]

### WebP Compression Implementation

[Explain actual implementation]

### Homepage Fixes

[List]

### Header / City Selector Fixes

[List]

### Role-Based UI Fixes

[List]

### Dashboard / Lead / Status Fixes

[List]

### Property Type Field Matrix Implemented

[List by type]

### Project / Unit Fixes

[List]

### Profile Fixes

[List]

### Admin / Super Admin Fixes

[List]

### Database / Supabase Changes

[List or None]

### RLS / Security Changes

[List or None]

### Routes Added/Updated

[List]

### Components Added/Updated

[List]

### Feature Registry Update

[List]

### Build / Type / Lint Check

PASS / FAIL / NOT RUN

### Implementation Status

PASS / PARTIAL / BLOCKED

### Notes / Blockers

[List]



NOTE: IN DEVELOPMENT MODE, DO NOT DELET FAKE PROEPRTY , USED , DETAILS ETC.