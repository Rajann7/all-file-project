# MY GUJARAT PROPERTY

# PROPERTY POSTING, PROPERTY-TYPE BASED FIELDS & MEDIA UPLOAD SPEC

## FILE NAME

`09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete property posting, project posting, property-type based dynamic fields, required/optional fields, media upload rules, image ratio rules, document upload rules, crop/resize behavior and posting UX for **My Gujarat Property**.

This file must be read before building or redesigning:

* Post Property flow
* Add Listing flow
* Property type selection
* Dynamic property fields
* Residential property fields
* Rent property fields
* Commercial property fields
* Land/plot fields
* Agricultural land fields
* PG/hostel fields
* Builder project fields
* Project unit fields
* Media upload
* Property image upload
* Floor plan upload
* Brochure upload
* Document upload
* Profile/logo/image crop if shared upload components are used
* Draft listing
* Listing preview
* Submit for approval
* Edit property
* Renew listing
* Mark sold/rented
* Listing expiry
* Admin property moderation
* Mobile property posting
* No-fake property data rules

The goal is to make property posting accurate, type-aware, mobile-friendly and ready for real estate marketplace use.

---

# 2. CORE PROPERTY POSTING PRINCIPLE

Property posting must start with selecting property/listing type.

User must not see one huge generic form for all properties.

The selected type decides:

* Which fields appear
* Which fields are required
* Which fields are optional
* Which filters will later apply
* Which card fields appear
* Which detail page sections appear
* Which search index fields are stored
* Which media/document rules apply
* Which approval rules apply
* Which subscription limits apply
* Which listing source tag applies

Wrong:

```txt id="sxdwi0"
User selects Land and still sees BHK, bathroom, furnishing and floor fields.
```

Correct:

```txt id="7ofk08"
User selects Land and sees land area, land type, road access, zoning, NA/agriculture status, boundary and village/taluka fields.
```

---

# 3. POST PROPERTY ACCESS RULE

Post property access depends on role.

Allowed roles:

* Owner
* Broker
* Agency Owner
* Agency Agent if permission allows
* Builder for projects/units
* Developer if implemented
* Admin/Super Admin if permitted

Restricted roles:

* Guest
* Buyer
* Tenant

Guest clicks Post Property:

1. Open login/register popup.
2. Preserve post property intent.
3. Register/login.
4. Ask role if new user.
5. Continue posting only if user has eligible role.
6. If not eligible, show role request/upgrade.

Buyer/Tenant clicks Post Property:

* Show role change request to Owner/Broker/Agency/Builder.
* Do not silently allow wrong role listing.

Admin/staff can create listings only if permission allows.

---

# 4. LISTING SOURCE TAG RULE

Every property must have listing source tag.

Possible source tags:

* Direct Owner
* Broker
* Agency
* Builder
* Developer
* Real Estate Group if applicable
* Admin Added if allowed

Source tag must be derived from active role/entity.

Do not allow user to fake source tag.

Example:

Broker active role posting property should show:

```txt id="weqrza"
Broker
```

Owner active role posting own property should show:

```txt id="ptugyu"
Direct Owner
```

Agency listing should show:

```txt id="pq5klh"
Agency
```

Builder project should show:

```txt id="zw9ex2"
Builder
```

Do not let broker post as Direct Owner unless admin-approved special case exists.

---

# 5. PROPERTY POSTING FLOW OVERVIEW

Recommended posting flow:

```txt id="7kjzkp"
Step 1: Select Listing Purpose
Step 2: Select Property Category / Type
Step 3: Location
Step 4: Basic Details
Step 5: Price / Rent / Financial Details
Step 6: Property-Specific Details
Step 7: Amenities / Features
Step 8: Media Upload
Step 9: Contact / Visibility
Step 10: Preview
Step 11: Submit / Save Draft
Step 12: Admin Approval if required
```

Mobile flow should be step-based.

Desktop can use stepper or sections.

Do not show a long unstructured form.

---

# 6. LISTING PURPOSE TYPES

Supported listing purposes:

* Sell
* Rent
* Lease
* PG/Hostel
* Project Sale
* Commercial Sale
* Commercial Rent
* Land Sale
* Agricultural Land Sale
* Investment
* Requirement Match if used internally

Purpose controls fields.

Examples:

Sell:

* Price
* Ownership
* Possession
* Sale availability

Rent:

* Monthly rent
* Deposit
* Tenant type
* Available from

Lease:

* Lease price
* Lease duration
* Deposit
* Terms

PG/Hostel:

* Rent per bed/room
* Sharing
* Gender
* Food

Project:

* Project details
* Units
* Builder
* RERA

Land:

* Land area
* Land type
* Road access
* Taluka/village

---

# 7. PROPERTY CATEGORY GROUPS

Main category groups:

1. Residential
2. Commercial
3. Land / Plot
4. Agricultural / Farm
5. PG / Hostel / Co-living
6. Project / Builder Inventory
7. Industrial
8. Mixed-use if implemented

Each group has subtypes.

---

# 8. RESIDENTIAL PROPERTY TYPES

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
* Serviced Apartment if implemented

Residential fields must not be mixed with land/commercial-only fields unless relevant.

---

# 9. COMMERCIAL PROPERTY TYPES

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

Commercial fields must focus on business suitability.

---

# 10. LAND / PLOT TYPES

Land and plot types:

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

Land fields must include taluka/village support where relevant.

---

# 11. PG / HOSTEL TYPES

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

PG fields must not show sale property fields.

---

# 12. PROJECT TYPES

Project types:

* Residential Project
* Commercial Project
* Mixed-use Project
* Villa Project
* Plotting Project
* Apartment Project
* Township
* Industrial Project if implemented

Builder project posting is different from individual property posting.

Project can have multiple units/configurations.

---

# 13. STEP 1 — SELECT PURPOSE

First screen should ask:

```txt id="ftq1s1"
What do you want to post?
```

Options:

* Property for Sale
* Property for Rent
* Commercial Property
* Land / Plot
* PG / Hostel
* Builder Project
* Project Unit
* Other if enabled

Each option should have short description.

Mobile UI:

* Card grid
* Large touch targets
* Icon
* Short text
* Continue button

Do not make user fill details before choosing type.

---

# 14. STEP 2 — SELECT PROPERTY TYPE

After purpose, show matching property types.

Example:

If purpose = Property for Sale:

Show:

* Flat / Apartment
* Independent House
* Villa
* Bungalow
* Row House
* Penthouse
* Studio
* Residential Plot

If purpose = Land / Plot:

Show:

* Residential Plot
* Commercial Plot
* Agricultural Land
* Farm Land
* Industrial Land
* NA Land
* Open Land

If purpose = Commercial:

Show:

* Shop
* Office
* Showroom
* Warehouse
* Godown
* Industrial Shed
* Factory
* Commercial Land
* Co-working Space

If purpose = PG / Hostel:

Show:

* Boys PG
* Girls PG
* Co-living
* Student Hostel
* Working Men Hostel
* Working Women Hostel

If purpose = Builder Project:

Show:

* Residential Project
* Commercial Project
* Mixed-use Project
* Plotting Project
* Villa Project
* Township

---

# 15. COMMON BASIC FIELDS

Common fields for most listings:

* Listing title
* Listing purpose
* Property category
* Property type
* Description
* State
* District
* Taluka if relevant
* City/Village
* Locality/Area
* Address/landmark
* Price/rent
* Area
* Area unit
* Availability status
* Contact preference
* Listing source
* Media
* Terms acceptance
* Draft/submit status

Title may be auto-generated but user can edit.

Example auto title:

```txt id="x9d9h5"
3 BHK Flat for Sale in Kalawad Road, Rajkot
```

Do not generate misleading title.

---

# 16. COMMON STATUS FIELDS

Property status options:

* Draft
* Pending Approval
* Active
* Rejected
* Need Changes
* Sold
* Rented
* Leased
* Expired
* Hidden
* Archived
* Deleted

Public should see only allowed statuses.

Draft/pending/rejected should not appear publicly.

---

# 17. COMMON AVAILABILITY FIELDS

Availability fields may include:

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

Only show relevant options.

---

# 18. COMMON PRICE FIELDS

Sale price fields:

* Expected price
* Price negotiable
* Price per unit if relevant
* All inclusive price if applicable
* Brokerage included/extra/none/negotiable
* Maintenance charges if relevant
* Other charges if relevant

Rent fields:

* Monthly rent
* Security deposit
* Maintenance
* Rent negotiable
* Advance months
* Brokerage
* Lock-in period if applicable

Commercial lease fields:

* Rent/lease amount
* Deposit
* CAM/maintenance if applicable
* Lease term
* Lock-in period
* Escalation if implemented

Land fields:

* Total price
* Price per area unit
* Negotiable
* Brokerage
* Token/booking not collected by platform

Do not handle property sale transaction payment.

Platform payment is only for listings/promotions/subscriptions.

---

# 19. BROKERAGE FIELD

Brokerage options:

* No Brokerage
* Brokerage Extra
* Brokerage Included
* Brokerage Negotiable
* As per discussion

Brokerage must be shown clearly where relevant.

Owner direct listing can default to No Brokerage but user/admin should control if needed.

Broker/Agency listing should include brokerage policy.

Do not hide brokerage if user provided it.

---

# 20. RESIDENTIAL FLAT / APARTMENT FIELDS

Required fields may include:

* Purpose: Sell/Rent
* Property type: Flat/Apartment
* City
* Locality
* Society/Project name
* BHK
* Bathrooms
* Area
* Area unit
* Price/rent
* Floor number
* Total floors
* Furnishing
* Availability/possession
* Property age
* Photos
* Contact preference

Optional fields:

* Balconies
* Parking
* Facing
* Vastu
* Lift
* Power backup
* Water supply
* Gas pipeline
* Maintenance
* Ownership type
* RERA/project info if applicable
* Amenities
* Floor plan
* Video link if enabled
* Description
* Landmark
* Map location

Residential flat should not show land survey fields.

---

# 21. INDEPENDENT HOUSE / VILLA / BUNGALOW FIELDS

Required fields may include:

* Purpose
* Property type
* City
* Locality/Area
* BHK/rooms
* Bathrooms
* Plot area
* Built-up area
* Price/rent
* Floors
* Furnishing
* Availability
* Photos
* Contact preference

Optional:

* Parking
* Garden
* Terrace
* Balcony
* Servant room
* Facing
* Vastu
* Property age
* Ownership type
* Water source
* Electricity
* Boundary wall
* Society/gated community
* Landmark
* Map location

Villa/bungalow should support plot area + built-up area.

---

# 22. ROW HOUSE / DUPLEX / PENTHOUSE / STUDIO FIELDS

Use residential base fields with subtype-specific adjustments.

Row House/Duplex:

* Floors
* Plot area
* Built-up area
* Parking
* Terrace

Penthouse:

* BHK
* Floor
* Terrace area
* View if implemented
* Lift
* Amenities

Studio:

* Area
* Furnishing
* Rent/sale
* Suitable for single/family/bachelor if rent

Do not show irrelevant land/agriculture fields.

---

# 23. RESIDENTIAL PLOT FIELDS

Required:

* Purpose: Sale
* Property type: Residential Plot
* District
* Taluka if relevant
* City/Village
* Locality/Area
* Plot area
* Area unit
* Price
* Road access
* Photos if available
* Contact preference

Optional:

* Plot dimensions
* Frontage
* Road width
* Corner plot
* Boundary wall
* Facing
* NA status
* Zoning
* Water
* Electricity
* Drainage
* Society/plotting scheme
* Survey/block number if safe
* Landmark
* Map location

Hide BHK, bathrooms, furnishing and floor.

---

# 24. AGRICULTURAL LAND / FARM LAND FIELDS

Required:

* Purpose: Sale/Lease if enabled
* Property type
* State
* District
* Taluka
* Village
* Land area
* Area unit
* Price
* Road access
* Water availability
* Contact preference

Optional:

* Survey/block number if safe
* Irrigation source
* Soil type if needed
* Borewell
* Electricity
* Boundary/fencing
* Crop history if relevant
* Farm house present
* Tree/plantation details
* Ownership type
* Title clear note
* NA conversion possibility
* Nearby road/highway
* Landmark
* Map location
* Photos
* Documents private upload if enabled

Hide BHK/furnishing/floor/bathroom unless farmhouse structure exists.

---

# 25. COMMERCIAL SHOP FIELDS

Required:

* Purpose: Sale/Rent/Lease
* Commercial type: Shop
* City
* Locality
* Building/complex
* Area
* Area unit
* Price/rent
* Floor/ground floor
* Frontage if relevant
* Availability
* Contact preference

Optional:

* Road width
* Main road
* Corner shop
* Parking
* Washroom
* Shutter width
* Ceiling height
* Power load
* Water connection
* Suitable business types
* Existing tenant
* Maintenance
* Brokerage
* Landmark
* Map location
* Photos

Do not show BHK.

---

# 26. COMMERCIAL OFFICE FIELDS

Required:

* Purpose: Sale/Rent/Lease
* Type: Office
* City
* Locality
* Building/complex
* Area
* Price/rent
* Furnishing
* Floor
* Availability
* Contact preference

Optional:

* Cabin count
* Workstations
* Meeting room
* Reception
* Pantry
* Washroom
* Parking
* Lift
* Power backup
* Internet readiness
* Maintenance
* Business center/co-working
* Landmark
* Map location
* Photos

---

# 27. SHOWROOM / RETAIL SPACE FIELDS

Required:

* Purpose
* Type: Showroom/Retail
* City
* Locality
* Main road/market area
* Area
* Price/rent
* Frontage
* Floor
* Availability

Optional:

* Road width
* Corner
* Glass frontage
* Parking
* Signage visibility
* Power load
* Washroom
* Suitable business
* Nearby brands/market
* Maintenance
* Brokerage

---

# 28. WAREHOUSE / GODOWN FIELDS

Required:

* Purpose
* Type: Warehouse/Godown
* District
* City/Taluka/Village
* Area
* Price/rent
* Road access
* Availability
* Contact preference

Optional:

* Ceiling height
* Loading/unloading
* Truck access
* Dock
* Power load
* Flooring type
* Fire safety
* Security
* Office space
* Washroom
* Parking
* Nearby highway
* Industrial zone
* Water/electricity
* Landmark
* Map location

---

# 29. INDUSTRIAL SHED / FACTORY FIELDS

Required:

* Purpose
* Type: Industrial Shed/Factory
* District
* Taluka/City
* Area
* Price/rent
* Power availability
* Road access
* Availability

Optional:

* Power load
* Shed height
* Plot area
* Built-up area
* Office area
* Worker facilities
* Loading/unloading
* Water
* Drainage
* Fire safety
* Industrial estate
* Pollution category if relevant
* Machinery included if relevant
* Landmark
* Map location

---

# 30. COMMERCIAL LAND FIELDS

Required:

* Purpose
* Type: Commercial Land
* District
* Taluka/City/Village
* Area
* Area unit
* Price
* Road access
* Zoning
* Contact preference

Optional:

* Road width
* Frontage
* NA status
* Commercial permission
* Corner
* Nearby highway
* Suitable for
* Water/electricity
* Boundary
* Landmark
* Map location

Hide BHK/furnishing.

---

# 31. PG / HOSTEL / CO-LIVING FIELDS

Required:

* Purpose: PG/Hostel
* Type
* City
* Locality
* Gender allowed
* Sharing type
* Monthly rent
* Deposit
* Food included
* Availability
* Photos
* Contact preference

Optional:

* AC/non-AC
* Attached bathroom
* Wi-Fi
* Laundry
* Housekeeping
* Parking
* Power backup
* Curfew time
* Visitor rules
* Minimum stay
* Student/professional
* Security
* CCTV
* Drinking water
* Meals type
* Bed count
* Room count
* Landmark
* Map location

Do not show sale price/BHK as primary.

---

# 32. BUILDER PROJECT FIELDS

Builder project posting is different.

Required:

* Project name
* Builder profile/entity
* Project type
* City
* Locality
* Address
* RERA number if applicable/available
* Project status
* Possession date
* Unit configurations
* Price range
* Project images
* Contact preference

Optional:

* Project logo
* Brochure
* Floor plans
* Towers
* Floors
* Total units
* Land area
* Amenities
* Parking
* Phases
* Construction updates
* Sample flat info
* Payment plan info
* Location map
* Nearby landmarks
* Approvals
* Specifications
* Builder description
* Video link if enabled

No fake RERA.

No fake project count.

---

# 33. PROJECT UNIT FIELDS

Project units/configurations may include:

* Unit type
* BHK
* Carpet area
* Built-up area
* Super built-up area if used
* Price
* Floor plan
* Availability
* Tower
* Floor range
* Bathroom
* Balcony
* Parking
* Possession
* Unit status

Unit status:

* Available
* Sold
* Booked
* Hold
* Hidden

Do not expose fake inventory.

---

# 34. AREA UNIT RULES

Supported area units:

* Sq Ft
* Sq Yard
* Sq Meter
* Var
* Bigha
* Acre
* Guntha
* Hectare

Residential default:

* Sq Ft

Land default:

* Sq Yard / Var / Bigha / Acre / Guntha depending user choice

Commercial default:

* Sq Ft / Sq Yard

Area unit conversion can be implemented later.

If conversion is shown, it must be accurate.

Do not fake conversion.

---

# 35. AMENITIES RULES

Amenities should be type-specific.

Residential amenities:

* Lift
* Parking
* Security
* CCTV
* Garden
* Gym
* Clubhouse
* Swimming pool
* Power backup
* Gas pipeline
* Children play area
* Temple nearby if not misleading
* Water supply
* Fire safety

Commercial amenities:

* Parking
* Lift
* Power backup
* Security
* Washroom
* Fire safety
* Loading/unloading
* Internet readiness
* Signage
* Main road access

PG amenities:

* Food
* Wi-Fi
* Laundry
* Housekeeping
* CCTV
* AC
* Parking
* Security
* Drinking water

Land features:

* Road access
* Boundary
* Water
* Electricity
* Drainage
* Borewell
* Fencing
* Corner
* Main road
* NA status

Do not show irrelevant amenity groups.

---

# 36. OWNERSHIP / LEGAL FIELDS

Optional legal/ownership fields may include:

* Ownership type
* Title clear note
* RERA number
* Approved plan
* NA status
* Loan availability
* Society NOC if relevant
* Property tax status if relevant
* Document availability

These can be public/private depending policy.

Do not collect sensitive documents as public media.

Private documents must go to private storage.

---

# 37. CONTACT / VISIBILITY FIELDS

Posting user should choose contact mode.

Options may include:

* Show phone directly
* Login required to contact
* Lead form only
* WhatsApp only
* Request contact approval
* Hide exact contact
* Contact via platform

Available modes depend on role, plan and admin settings.

Contact visibility affects property detail page.

Hidden contact must not leak.

---

# 38. EXACT LOCATION VISIBILITY

User should choose location visibility if allowed.

Options:

* Show exact location
* Show approximate locality
* Show after contact
* Hide exact address
* Show map pin approximate

System must respect selected privacy.

Do not expose full address in public SEO metadata if hidden.

---

# 39. DRAFT RULE

Users should be able to save draft.

Draft listing:

* Not public
* Editable by owner/assigned user
* Not indexed
* Not searchable
* Can be submitted later
* Can have incomplete fields

Draft should not count as active listing unless plan says draft limit.

---

# 40. PREVIEW RULE

Before submit, user should preview listing.

Preview should show:

* Card preview
* Detail page preview
* Images
* Price/rent
* Location display
* Source tag
* Contact mode
* Visibility settings
* Missing required fields
* Terms/policy confirmation

Preview must not publish listing.

---

# 41. SUBMIT FOR APPROVAL RULE

Submission flow:

```txt id="sf7655"
User completes form
User previews listing
User submits
System validates fields
System checks role/plan limits
System sets status pending approval or active based on settings
Admin reviews if approval required
Listing becomes public only when allowed
```

If admin approval is required:

* Status = Pending Approval
* Public visibility = false
* Notify user
* Show dashboard status

If auto-approval enabled:

* Status = Active after validation
* Still allow moderation/reporting

---

# 42. ADMIN MODERATION RULE

Admin can:

* View pending listings
* Approve
* Reject
* Request changes
* Edit limited fields if permitted
* Add internal note
* Add user-visible note
* Archive
* Mark suspicious
* Verify listing
* Check duplicate
* Check media
* Check documents if required

User should see:

* Pending status
* Approved status
* Rejected status
* Need changes status
* Rejection reason
* Resubmit option

No fake approval.

---

# 43. LISTING EXPIRY RULE

Listings can expire based on plan/settings.

Listing expiry should support:

* Active until date
* Expiring soon notice
* Expired status
* Auto-hide after expiry
* Archive after grace period if configured
* Renew option
* Admin override

Expired listing should not appear as active.

Do not fake active status.

---

# 44. SOLD / RENTED / LEASED RULE

User/admin can mark listing as:

* Sold
* Rented
* Leased
* Unavailable
* On hold

Public behavior:

* Hide from active results, or
* Show status if policy allows
* No new leads if disabled
* SEO noindex/redirect if needed

Do not keep sold/rented property as active without status.

---

# 45. MEDIA UPLOAD GLOBAL RULE

Every media upload area must show:

* Recommended size
* Recommended ratio
* Accepted file types
* Maximum file size
* Minimum resolution if needed
* Preview
* Replace option
* Delete option
* Reorder option where useful
* Crop option where relevant
* Auto-resize/fit behavior
* Upload progress
* Error state

Applies to:

* Property images
* Project images
* Floor plans
* Brochures
* Property videos if enabled
* Profile avatars if using shared media component
* Broker logos/photos
* Agency logos
* Builder logos
* Banner ads
* Blog images
* CMS images
* Verification documents
* Support attachments

---

# 46. PROPERTY IMAGE REQUIREMENTS

Property images:

Recommended ratios:

```txt id="ww3649"
16:9 for cover/gallery preview
4:3 acceptable for property gallery
1:1 allowed for small card thumbnails if cropped safely
```

Recommended sizes:

```txt id="66exm5"
Minimum: 1200x800 px preferred
Card/cover: 1200x675 px or higher
Gallery: 1600px wide preferred
```

Accepted formats:

* JPG
* JPEG
* PNG
* WEBP

Optional future:

* HEIC conversion if supported

Rules:

* First image can be cover image.
* User can reorder images.
* User can delete image.
* User can crop cover thumbnail.
* Auto-compress safely.
* Do not stretch images.
* Use placeholder if no image but do not fake real image.
* Watermark optional if platform policy.

---

# 47. PROJECT IMAGE REQUIREMENTS

Project images:

Recommended:

```txt id="kcwuec"
16:9 for project cover
4:3 for gallery
```

Suggested sizes:

```txt id="vhr18r"
Cover: 1600x900 px
Gallery: 1600px wide or higher
```

Images may include:

* Exterior
* Interior
* Amenities
* Layout
* Location
* Construction update
* Sample unit if real

Do not use fake project photos.

---

# 48. FLOOR PLAN REQUIREMENTS

Floor plan upload:

Accepted:

* JPG
* PNG
* WEBP
* PDF if enabled

Recommended:

```txt id="c4mv93"
Clear readable image/PDF, minimum 1200px wide for image
```

Floor plan should support:

* Unit type association
* BHK association
* Preview
* Replace/delete
* Private/public flag if needed

Do not show unreadable tiny floor plans.

---

# 49. BROCHURE REQUIREMENTS

Brochure upload:

Accepted:

* PDF

Rules:

* Show file size limit.
* Preview/download if public.
* Mark as public/private.
* Virus/safety scanning if available.
* Do not expose private documents as brochure.

Builder projects commonly need brochure.

---

# 50. VIDEO RULE

Video is optional.

If implemented:

* Support video URL such as YouTube/Vimeo, or
* Support upload if storage plan allows

Do not require video.

Do not fake video.

Do not include screenshot/video capture instruction from old docs.

If video URL invalid, show error.

---

# 51. DOCUMENT UPLOAD RULE

Documents are different from images.

Private documents may include:

* Ownership document
* RERA certificate
* Approval letter
* Property tax receipt
* Identity proof
* Agency verification document
* Builder verification document

Rules:

* Private storage bucket
* Access controlled
* Not public
* Admin/verification only
* File type validation
* File size validation
* Clear purpose
* Upload status

Do not expose documents publicly.

---

# 52. IMAGE CROP RULE

Crop option must be available where image presentation matters.

Required crop areas:

* Profile avatar
* Broker photo/logo
* Agency logo
* Builder logo
* Property cover image
* Project cover image
* Banner ads
* Blog/CMS cover image

Crop behavior:

* Mobile full-screen crop
* Desktop modal crop
* Zoom
* Move
* Aspect ratio lock where needed
* Preview
* Save
* Cancel

Do not stretch/cut important image content without preview.

---

# 53. BANNER ADS IMAGE NOTE

Banner ads are detailed in separate document.

However shared media upload component must support:

* Desktop banner image
* Tablet banner image
* Mobile banner image
* Different ratio per device
* Recommended size text
* Crop/fit/preview
* Admin review

Banner ad upload must never be confused with property image upload.

---

# 54. IMAGE SIZE ERROR STATES

Image upload errors:

* File too large
* Invalid file type
* Image too small
* Upload failed
* Crop failed
* Network error
* Storage permission error
* Too many images
* Unsupported format

Errors should be user-friendly.

Example:

```txt id="8dwt90"
Image is too small. Recommended minimum size is 1200x800 px.
```

Do not show raw storage error to user.

---

# 55. IMAGE UPLOAD LIMITS

Limits depend on plan/role.

Example limits:

Owner free plan:

* 3 property images

Owner paid plan:

* 10 property images

Broker plan:

* 10-20 images per listing

Builder project:

* More project images if plan allows

Exact limits belong to subscription document.

UI must show:

```txt id="icq4gf"
3 of 10 images uploaded
```

if limits are implemented.

Do not show fake limit/usage.

---

# 56. MEDIA STORAGE RULE

Storage should separate public and private files.

Public storage:

* Property images
* Project images
* Public logos
* Public brochures if approved
* Blog images
* CMS images

Private storage:

* Verification documents
* Ownership documents
* ID proof
* Admin files
* Private attachments

Storage policies must enforce access.

Do not put private documents in public bucket.

---

# 57. PROPERTY POSTING MOBILE UX

Mobile posting should be step-based.

Mobile requirements:

* Progress indicator
* Step title
* Back button
* Save draft
* Sticky next button
* Large inputs
* Bottom sheet selectors
* Image upload preview
* Crop full-screen
* No horizontal scroll
* Keyboard-safe layout
* Errors near fields
* No giant desktop form
* Resume draft

Mobile steps should be short.

---

# 58. PROPERTY POSTING DESKTOP UX

Desktop posting can use:

* Stepper
* Two-column layout
* Section cards
* Sticky progress sidebar
* Preview panel
* Save draft button
* Submit button

Desktop must still remain clean.

Do not show all fields if not relevant.

---

# 59. PROPERTY POSTING VALIDATION

Validation must be dynamic by property type.

Common validation:

* Required fields
* Valid price/rent
* Valid area
* Valid city/location
* Valid contact preference
* Valid image count if required
* Valid status
* Plan limit check
* Role permission check

Type-specific validation:

Land:

* Area unit required
* Taluka/village if rural
* Road access if required

Flat:

* BHK required
* Floor details if required
* Area required

Commercial:

* Commercial type required
* Area required
* Purpose required

PG:

* Gender/sharing/rent required

Project:

* Project name
* Builder
* Location
* Unit configuration

---

# 60. PLAN LIMIT CHECK

Before submission, system must check:

* User role
* Active plan
* Listing limit
* Image limit
* Featured/boost eligibility
* Project limit
* Banner ad eligibility separate
* Expiry rules
* Free launch offer if active

If limit reached:

* Show upgrade/renew CTA.
* Save draft if possible.
* Do not publish beyond plan.

Do not fake plan availability.

---

# 61. FREE LAUNCH RULE

If first 100 users free listing offer is enabled:

* Admin/Super Admin setting controls it.
* Eligibility must be server-checked.
* Usage count must be real.
* Offer must expire/stop when limit reached.
* User must see clear message.
* No fake “first 100” count.

Detailed monetization belongs to subscription document.

---

# 62. PROPERTY POSTING AND SEO

Property posting should generate SEO data.

Generated fields may include:

* Slug
* SEO title
* Meta description
* Search keywords
* City/locality route links
* Structured data fields

Example title:

```txt id="ps5uhr"
3 BHK Flat for Sale in Kalawad Road, Rajkot
```

Meta should not expose hidden contact/address.

Do not index draft/pending/rejected listings.

---

# 63. PROPERTY POSTING AND SEARCH INDEX

When listing becomes active, update search index fields:

* City
* Locality
* Property type
* Purpose
* Price/rent
* Area
* BHK
* Source type
* Status
* Verification
* Amenities
* Created/updated date
* Featured/sponsored status if real
* Coordinates if map enabled

If listing is edited, update search fields.

If listing is expired/archived, remove from active search.

---

# 64. PROPERTY POSTING AND LEADS

Listing contact settings decide lead flow.

Lead receiver:

* Owner
* Broker
* Agency
* Agent if assigned
* Builder project team

Contact form can use sender profile number or alternate number.

Alternate number must be shown in receiver dashboard.

Detailed lead rules belong to contact/lead document.

---

# 65. PROPERTY POSTING AND NOTIFICATIONS

Notifications may trigger:

* Draft saved
* Listing submitted
* Listing approved
* Listing rejected
* Need changes
* Listing expired soon
* Listing expired
* Listing renewed
* Lead received
* Site visit requested
* Property marked sold/rented

Do not fake external notifications if provider missing.

---

# 66. PROPERTY POSTING ADMIN ROUTES

Admin routes:

```txt id="wj9uyh"
/admin/properties
/admin/properties/pending
/admin/properties/active
/admin/properties/rejected
/admin/properties/reported
/admin/properties/expired
/admin/properties/archived
/admin/properties/[id]
```

Admin actions:

* View
* Approve
* Reject
* Request changes
* Verify
* Feature/boost if permitted
* Archive
* Mark duplicate
* Mark suspicious
* Edit if permitted
* View audit log

---

# 67. PROPERTY POSTING USER ROUTES

Owner routes:

```txt id="is0i2p"
/dashboard/owner/properties
/dashboard/owner/properties/new
/dashboard/owner/properties/[id]
/dashboard/owner/properties/[id]/edit
```

Broker routes:

```txt id="h3k3m1"
/dashboard/broker/listings
/dashboard/broker/listings/new
/dashboard/broker/listings/[id]
/dashboard/broker/listings/[id]/edit
```

Agency routes:

```txt id="chpka5"
/dashboard/agency/listings
/dashboard/agency/listings/new
/dashboard/agency/listings/[id]
/dashboard/agency/listings/[id]/edit
```

Builder routes:

```txt id="ap5we7"
/dashboard/builder/projects
/dashboard/builder/projects/new
/dashboard/builder/projects/[id]
/dashboard/builder/projects/[id]/edit
/dashboard/builder/projects/[id]/units
```

---

# 68. PROPERTY POSTING DATABASE MODULES

Possible tables:

* properties
* property_details
* property_media
* property_documents
* property_amenities
* property_pricing
* property_location
* property_contact_settings
* property_status_history
* property_moderation
* property_reports
* property_boosts
* projects
* project_units
* project_media
* project_documents
* property_drafts

Detailed schema belongs to database/security document.

---

# 69. PROPERTY POSTING PERMISSIONS

Permission examples:

```txt id="y2i1wd"
property.create
property.create.owner
property.create.broker
property.create.agency
property.create.builder
property.update.own
property.update.assigned
property.delete.own
property.archive.own
property.submit_for_approval
property.approve
property.reject
property.request_changes
property.verify
property.feature
property.view.private
property.view.admin
project.create
project.update.own
project.approve
project.reject
media.upload.property
document.upload.private
```

Permissions must be server-side.

---

# 70. PROPERTY POSTING FEATURE FLAGS

Possible feature flags:

```txt id="b3u5rk"
property.posting.enabled
property.drafts.enabled
property.approval_required
property.auto_approve_owner
property.auto_approve_broker
property.auto_approve_agency
property.auto_approve_builder
property.media_upload.enabled
property.image_crop.enabled
property.floor_plan.enabled
property.brochure.enabled
property.video.enabled
property.documents.enabled
property.location_exact_visibility.enabled
property.expiry.enabled
property.boost.enabled
property.featured.enabled
property.free_launch.enabled
project.posting.enabled
pg.posting.enabled
commercial.posting.enabled
land.posting.enabled
```

If flag is off, hide UI and block backend action where needed.

---

# 71. PROPERTY POSTING COMPONENTS

Recommended components:

* PostPropertyShell
* ListingPurposeSelector
* PropertyTypeSelector
* DynamicPropertyForm
* LocationStep
* PricingStep
* ResidentialFields
* CommercialFields
* LandFields
* AgricultureLandFields
* PGHostelFields
* ProjectFields
* UnitConfigurationFields
* AmenitiesSelector
* MediaUploadStep
* ImageUploader
* ImageCropModal
* FloorPlanUploader
* BrochureUploader
* DocumentUploader
* ContactVisibilityStep
* ListingPreview
* SaveDraftButton
* SubmitForApprovalButton
* ListingStatusBadge
* ListingApprovalState
* ListingExpiryCard

Avoid duplicate random forms.

---

# 72. PROPERTY POSTING LOADING STATES

Loading states:

* Loading draft
* Saving draft
* Uploading image
* Cropping image
* Loading location options
* Loading plan limits
* Submitting listing
* Loading preview
* Loading moderation status

Use skeleton/progress.

Do not freeze page without feedback.

---

# 73. PROPERTY POSTING EMPTY STATES

Empty states:

* No properties yet
* No drafts yet
* No images uploaded
* No floor plans uploaded
* No project units yet
* No amenities selected
* No leads yet for listing
* No moderation history

Empty states should guide action.

Example:

```txt id="8m8k7f"
You have not posted any property yet. Start by selecting property type.
```

---

# 74. PROPERTY POSTING ERROR STATES

Error states:

* Missing required field
* Invalid price
* Invalid area
* Invalid location
* Plan limit reached
* Role not allowed
* Upload failed
* File too large
* Invalid file type
* Approval failed
* Save draft failed
* Network error
* Permission denied

Show clear user-friendly errors.

Do not show raw DB/storage errors.

---

# 75. PROPERTY POSTING SUCCESS STATES

Success states:

* Draft saved
* Image uploaded
* Profile/contact saved
* Listing submitted
* Listing approved
* Listing updated
* Listing archived
* Listing renewed
* Listing marked sold/rented

Success only after server confirmation.

---

# 76. PROPERTY POSTING NO-FAKE RULE

Do not fake:

* Listing creation
* Listing approval
* Image upload
* Media preview
* Verification
* RERA status
* Plan limit
* Payment/subscription activation
* Location
* Map pin
* Owner/broker source tag
* Sold/rented status
* Lead count
* View count
* Featured status
* Boost status
* Expiry date

If not implemented, hide or show setup/pending state.

---

# 77. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Guest click Post Property opens login/register.
* Buyer/Tenant cannot post without role upgrade.
* Owner can open post property.
* Broker can open listing form.
* Agency can open listing form.
* Builder can open project form.
* First step asks property purpose/type.
* Selecting land hides BHK/floor/furnishing.
* Selecting flat shows BHK/floor/furnishing.
* Selecting commercial hides BHK.
* Selecting PG shows PG fields.
* Location cascade works.
* Missing location request works.
* Image upload shows recommended size/ratio.
* Image crop works where required.
* Invalid image shows error.
* Draft save works.
* Submit for approval works.
* Admin can approve/reject if phase includes admin.
* Active approved listing appears in search.
* Draft/pending does not appear publicly.
* Mobile form has no horizontal scroll.
* Sticky next/back buttons work.
* No screenshot/video capture required.

---

# 78. PASS / FAIL RULE

Property posting phase is PASS only if:

* Posting starts with type selection.
* Dynamic fields change by selected type.
* Land does not show BHK.
* Commercial does not show residential-only fields.
* PG does not show sale fields.
* Location is structured.
* Media upload shows size/ratio guidance.
* Crop works where required or is marked pending.
* Draft/submission states are clear.
* Role permissions are enforced.
* Plan limits are checked if monetization active.
* Admin approval works if required.
* Public search does not show draft/pending/rejected listings.
* No fake data or fake success is shown.
* Mobile posting is usable.
* Feature registry updated.
* Manual verification completed.

If one generic property form is used for all types without dynamic behavior, mark FAIL.

---

# 79. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`
* `05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for search, SEO, location, contact, dashboard, subscription, database and manual verification details.

---

# 80. END OF FILE

This file defines property posting, property-type based dynamic fields and media upload rules for My Gujarat Property.

Property posting must start with type selection, show only relevant fields, support structured location, real media upload, crop/resize rules, approval workflow, plan checks, mobile step UX and no-fake behavior.

Nothing from uploaded docs or user chat instructions should be skipped.
