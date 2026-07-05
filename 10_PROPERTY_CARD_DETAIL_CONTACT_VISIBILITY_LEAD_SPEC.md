# MY GUJARAT PROPERTY

# PROPERTY CARD, PROPERTY DETAIL, CONTACT VISIBILITY & LEAD SPEC

## FILE NAME

`10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete property card, search result card, property detail page, project detail contact behavior, contact visibility rules, lead form, current number/alternate number behavior, WhatsApp contact behavior, lead tracking and contact security for **My Gujarat Property**.

This file must be read before building or redesigning:

* Property cards
* Search result cards
* Project cards
* Requirement result cards if connected
* Property detail pages
* Project detail pages
* Contact buttons
* Call buttons
* WhatsApp buttons
* Lead forms
* Contact reveal
* Contact visibility settings
* Alternate number behavior
* Lead receiver dashboard
* Lead status pipeline
* Hidden contact security
* Save/share/report actions
* Mobile sticky contact CTA
* Desktop sticky contact panel
* Contact logging
* Lead notification
* WhatsApp free/API mode integration
* Map visibility in detail page
* Source tag display
* Verification badge display
* No-fake card metrics

The goal is to make property discovery and contact conversion simple, trustworthy and secure.

---

# 2. CORE CONTACT PRINCIPLE

The property card and detail page must help users quickly understand and contact the right listing owner/seller/business.

But contact information must be protected.

The system must never leak hidden contact details.

The system must never show fake calls, fake leads, fake WhatsApp sends, fake views, fake ratings or fake badges.

Every contact action must respect:

* User login state
* Listing contact visibility mode
* Listing source type
* Active role
* Subscription/plan permissions
* Provider mode
* Property approval status
* Property expiry status
* Contact privacy
* Lead receiver rules
* Admin settings
* RLS/server-side permissions

---

# 3. PROPERTY CARD PURPOSE

Property card is the first decision point in search/discovery.

A good card should quickly answer:

1. What is this property?
2. Where is it?
3. What is the price/rent?
4. What type is it?
5. Is it owner/broker/agency/builder?
6. Is it verified or not?
7. Is it for sale/rent/commercial/land/PG/project?
8. What are the most important details?
9. Can I contact/save/share?
10. Is this sponsored/featured?
11. Is this still active?

Cards must be clean and mobile-friendly.

Do not overload card with every field.

---

# 4. PROPERTY CARD TYPES

The platform may need different card types:

* Residential property card
* Rental property card
* Commercial property card
* Land/plot card
* Agricultural land card
* PG/hostel card
* Project card
* Requirement card
* Broker profile card
* Agency profile card
* Builder profile card
* Saved property card
* Dashboard property card
* Admin property review card
* Mobile compact card
* Desktop expanded card

Each card should show fields relevant to its type.

Do not use one generic card that shows irrelevant fields.

---

# 5. COMMON PROPERTY CARD FIELDS

Common property card fields:

* Cover image
* Price/rent
* Title
* City
* Locality
* Property type
* Purpose
* Area
* Area unit
* Status
* Source tag
* Verification badge if real
* Sponsored/featured badge if real
* Short highlights
* Posted/updated date if useful
* Save button if implemented
* Share button if implemented
* Contact CTA
* WhatsApp CTA if enabled
* View details CTA

Optional:

* BHK
* Bathroom
* Parking
* Furnishing
* Possession
* Project name
* Builder name
* Brokerage
* RERA if real
* Map/locality indicator
* Compare checkbox if implemented

Do not show fake views, fake leads, fake rating or fake “verified”.

---

# 6. CARD IMAGE RULE

Card image should use real uploaded image.

If no image exists:

* Show safe placeholder.
* Do not show fake property photo.
* Placeholder should not mislead user.

Image display:

* Use cover image if selected.
* Use first approved image if no cover selected.
* Crop safely.
* Avoid stretching.
* Use responsive sizes.
* Lazy load below-fold images.
* Show image count if real.

Example:

```txt id="2i664z"
1 / 8 photos
```

Only show count if real.

---

# 7. CARD PRICE RULE

Price must be clear.

Sale price examples:

```txt id="x8s5xe"
₹45 Lakh
₹1.25 Cr
Price on Request
```

Rent examples:

```txt id="w1zlgj"
₹18,000/month
₹25,000/month
```

Land price:

```txt id="xvz4f4"
₹80 Lakh
₹5,500 / Sq Yard
```

Commercial:

```txt id="ugub6m"
₹40,000/month
₹1.2 Cr
```

Rules:

* Do not show sale price as rent.
* Do not show rent as sale price.
* Do not show fake discount.
* Do not show fake “lowest price”.
* If price hidden, show “Price on Request” only if listing setting allows.

---

# 8. CARD TITLE RULE

Card title can be generated or user-written.

Auto title examples:

Residential sale:

```txt id="hnswrc"
3 BHK Flat for Sale in Kalawad Road, Rajkot
```

Rent:

```txt id="n0z55d"
2 BHK Flat for Rent in Mota Mava, Rajkot
```

Commercial:

```txt id="3uz6pj"
Commercial Shop for Rent in Satellite, Ahmedabad
```

Land:

```txt id="gl7hwa"
Residential Plot for Sale in Rajkot
```

PG:

```txt id="unlivy"
Girls PG in University Road, Rajkot
```

Title must be accurate.

Do not include fake “best”, “premium” or “verified” unless real.

---

# 9. CARD SOURCE TAG RULE

Every listing must show source tag where relevant.

Source tags:

* Direct Owner
* Broker
* Agency
* Builder
* Developer
* Real Estate Group if applicable

Source tag must be derived from posting role/entity.

Do not let users manually fake it.

Public display examples:

```txt id="shsq85"
Direct Owner
Broker
Agency
Builder
```

This improves trust and transparency.

---

# 10. CARD VERIFICATION BADGE RULE

Verification badge appears only if verified.

Possible badges:

* Verified Owner
* Verified Broker
* Verified Agency
* Verified Builder
* Verified Property
* RERA Verified if real and validated
* Approved Listing

Do not show fake badges.

If verification pending:

```txt id="a1cruk"
Verification Pending
```

can be shown in dashboard/admin, not necessarily public.

If not verified:

* Hide badge or show neutral state.
* Do not mislead.

---

# 11. CARD SPONSORED / FEATURED RULE

Sponsored/featured listing must be clearly labeled.

Possible labels:

* Featured
* Sponsored
* Promoted
* Ad

Rules:

* Label only if paid/eligible/active.
* Must not show if expired.
* Must not show if unpaid.
* Must not show if not approved.
* Must respect plan/payment rules.
* Must be tracked if analytics implemented.

Do not fake sponsored status.

---

# 12. CARD STATUS RULE

Property status affects public display.

Public active statuses:

* Active
* Ready to Move
* Under Construction
* New Launch
* Resale
* Available

Restricted statuses:

* Draft
* Pending Approval
* Rejected
* Need Changes
* Hidden
* Archived
* Deleted

Conditional public statuses:

* Sold
* Rented
* Leased
* Expired

If sold/rented listing is still visible, show clear badge and disable new contact if policy.

Do not show expired listing as active.

---

# 13. RESIDENTIAL CARD FIELDS

Residential card should show:

* Price/rent
* BHK
* Area
* Property type
* City/locality
* Furnishing if rent
* Floor if useful
* Possession if sale/project
* Source tag
* Contact CTA

Example:

```txt id="bhiw36"
3 BHK Flat
1,250 Sq Ft
Kalawad Road, Rajkot
₹65 Lakh
Direct Owner
```

---

# 14. LAND / PLOT CARD FIELDS

Land/plot card should show:

* Price
* Land/plot type
* Area
* Area unit
* City/village/taluka
* Road access if important
* NA/agriculture status if provided
* Source tag
* Contact CTA

Do not show BHK.

Example:

```txt id="xf9fuf"
Residential Plot
180 Sq Yard
Rajkot
₹42 Lakh
```

---

# 15. COMMERCIAL CARD FIELDS

Commercial card should show:

* Price/rent
* Commercial type
* Area
* City/locality
* Floor/road/main road if useful
* Suitable for if provided
* Source tag
* Contact CTA

Do not show BHK.

Example:

```txt id="tyoxfz"
Shop for Rent
350 Sq Ft
Main Road, Rajkot
₹35,000/month
```

---

# 16. PG / HOSTEL CARD FIELDS

PG/Hostel card should show:

* Rent
* Type
* Gender
* Sharing
* Food included
* City/locality
* Availability
* Contact CTA

Example:

```txt id="cxa9km"
Girls PG
Double Sharing
Food Included
University Road, Rajkot
₹7,500/month
```

Do not show sale price.

---

# 17. PROJECT CARD FIELDS

Project card should show:

* Project image
* Project name
* Builder name
* City/locality
* Unit types
* Price range
* Possession/status
* RERA if real
* Contact CTA
* View project CTA

Do not show fake project status.

Do not show fake RERA.

---

# 18. PROPERTY DETAIL PAGE PURPOSE

Property detail page is the main conversion page.

It should help user:

* Understand property fully.
* View images.
* See price/location/details.
* Trust the source.
* Contact safely.
* Save/share/report.
* Book site visit if enabled.
* View similar properties if real.

The detail page must be mobile-first.

Mobile should have sticky bottom contact CTA.

Desktop can have sticky right contact panel.

---

# 19. PROPERTY DETAIL PAGE STRUCTURE

Recommended detail page structure:

```txt id="u77qzq"
Header
Breadcrumb
Gallery
Title / Price / Location
Quick Facts
Contact CTA / Sticky Contact Panel
Description
Property Details
Amenities / Features
Location / Map
Seller/Broker/Agency/Builder Card
Floor Plan / Brochure
Similar Properties
Report Listing
FAQ / Help
Footer
```

Mobile order should prioritize:

1. Gallery
2. Price/title/location
3. Sticky CTA
4. Quick facts
5. Contact actions
6. Details
7. Seller card
8. Map
9. Similar properties

---

# 20. DETAIL GALLERY RULE

Gallery should support:

* Cover image
* Multiple images
* Full-screen view
* Image count
* Swipe on mobile
* Thumbnail grid on desktop
* Lazy loading
* Safe placeholder
* No fake photos

If no images:

* Show placeholder.
* Do not use unrelated property image.

Do not expose private documents as gallery images.

---

# 21. DETAIL QUICK FACTS

Quick facts should depend on property type.

Residential:

* BHK
* Area
* Bathrooms
* Floor
* Furnishing
* Parking
* Possession

Land:

* Area
* Land type
* Road access
* Taluka/village
* NA/agriculture status
* Boundary

Commercial:

* Type
* Area
* Floor
* Frontage
* Road width
* Suitable for

PG:

* Sharing
* Gender
* Food
* Rent
* Availability

Project:

* Unit types
* Possession
* Project status
* Builder
* RERA if real

Do not show irrelevant quick facts.

---

# 22. DETAIL DESCRIPTION RULE

Description should be user-written or generated safely.

Rules:

* Show real content.
* Avoid keyword stuffing.
* Avoid fake claims.
* Avoid misleading “verified/best/top”.
* Sanitize content.
* Prevent spam links if not allowed.
* Trim excessive formatting.

If description missing, show:

```txt id="c5iruo"
Description not provided.
```

or hide section.

Do not generate fake description after posting without clear generation flow.

---

# 23. DETAIL LOCATION RULE

Location display must respect privacy.

Public location options:

* Exact address
* Locality only
* Approximate map
* Landmark only
* Show after contact

Examples:

Exact public:

```txt id="fgqzcq"
Kalawad Road, Rajkot, Gujarat
```

Approximate:

```txt id="kwntdx"
Near Kalawad Road, Rajkot
```

Hidden exact:

```txt id="m6bhpy"
Exact address shared after contact.
```

Do not expose hidden address in HTML, metadata, API response or schema.

---

# 24. DETAIL MAP RULE

Map depends on provider settings.

Map modes:

* Disabled
* Free/embed/trial mode
* Premium API mode

Detail page map behavior:

* If disabled, hide map or show location text.
* If embed mode active, show allowed embed.
* If API mode active and configured, show interactive map.
* If API missing, do not fake map.
* Respect exact/approximate location setting.
* Lazy load map.

Do not show fake map pin.

---

# 25. SELLER / BROKER / AGENCY / BUILDER CARD

Detail page should show source entity card.

Owner card:

* Display name
* Source tag: Direct Owner
* Verification if real
* Contact CTA

Broker card:

* Broker photo/logo
* Broker name/business name
* Verified badge if real
* Operating areas if useful
* View profile
* Contact CTA

Agency card:

* Agency logo
* Agency name
* Verified badge if real
* View agency profile
* Contact CTA

Builder card:

* Builder logo
* Builder name
* Verified/RERA if real
* View builder profile
* Contact CTA

Do not expose private contact unless allowed.

---

# 26. CONTACT CTA TYPES

Contact CTAs may include:

* Call
* WhatsApp
* Send Enquiry
* Request Callback
* Book Site Visit
* Message
* View Phone
* Contact Owner
* Contact Broker
* Contact Agency
* Contact Builder

Which CTAs appear depends on:

* Contact mode
* User login state
* Provider settings
* Role permissions
* Listing status
* Subscription rules
* Admin settings

Do not show non-working CTA.

---

# 27. MOBILE STICKY CTA

Mobile property detail must have sticky bottom CTA.

Possible buttons:

* Call
* WhatsApp
* Enquire
* Site Visit

If too many actions:

Use:

* Primary CTA: Contact / Enquire
* Secondary CTA: WhatsApp or Call
* More actions inside sheet

Sticky CTA must:

* Not cover content.
* Respect bottom navigation.
* Use safe bottom padding.
* Be large enough to tap.
* Hide/disable if listing unavailable.
* Show login intent if guest.

---

# 28. DESKTOP STICKY CONTACT PANEL

Desktop can use sticky right contact panel.

Panel may show:

* Price
* Contact buttons
* Lead form
* Seller card
* Short contact text
* Safety note
* Site visit CTA

Panel must not overlap footer.

Do not show hidden phone without permission.

---

# 29. CONTACT VISIBILITY MODES

Listing contact mode options:

1. Public Phone
2. Login Required
3. Lead Form Required
4. Request Contact Approval
5. WhatsApp Only
6. Platform Message Only
7. Premium/Plan Required
8. Hidden/Unavailable

Each mode must be enforced server-side.

Frontend hiding is not enough.

---

# 30. PUBLIC PHONE MODE

If public phone mode is enabled:

* Phone may be shown or revealed.
* Click-to-call can work.
* Lead/click can be logged if implemented.
* Phone should belong to listing receiver entity.
* User should still be able to submit enquiry.

Rules:

* Public phone must not be shown if owner selected hidden.
* Public phone must not appear for pending/expired listings.
* Public phone must not be exposed in API when hidden.

---

# 31. LOGIN REQUIRED MODE

If login required:

Guest clicks contact:

* Open login/register popup.
* Preserve property/contact intent.
* After login, continue contact flow.

Logged-in user:

* Show contact flow.

If user account suspended/banned:

* Block contact.

Do not lose contact intent after login.

---

# 32. LEAD FORM REQUIRED MODE

Lead form required mode means contact is not directly shown until enquiry is submitted, or contact only happens through lead system.

Lead form should collect:

* Name
* Phone
* Email optional
* Message optional
* Interest type
* Preferred contact time if implemented
* Current number/alternate number choice
* Consent/terms if needed

If logged-in:

* Prefill name
* Prefill profile phone
* Prefill email if available
* Allow alternate number

If guest:

* Ask login/register first if required, or collect guest lead only if allowed by admin.

Lead form must not overwrite profile phone unless user confirms.

---

# 33. CURRENT NUMBER / ALTERNATE NUMBER RULE

This is a critical requirement.

When logged-in user submits lead:

Show phone options:

## Option 1

```txt id="ayyyct"
Use my profile number
```

Display masked/clear number depending UI.

## Option 2

```txt id="zidbk3"
Use a different number
```

If user selects different number:

* Show phone input.
* Validate number.
* Store as alternate lead phone.
* Do not overwrite profile phone automatically.
* Ask checkbox only if user wants to update profile phone.

Lead receiver dashboard must show:

```txt id="0brj1u"
Alternate number used
```

or:

```txt id="jhpywk"
User used a different contact number for this lead.
```

This must be visible clearly.

---

# 34. LEAD PHONE DATA STRUCTURE

Lead should store:

* profile_phone_at_time
* lead_phone_used
* phone_source: profile / alternate / guest
* alternate_phone_flag
* update_profile_requested boolean if user asked
* user_id if logged in
* guest_id/session if guest leads allowed

Do not lose original phone context.

Do not overwrite profile phone silently.

---

# 35. LEAD FORM FIELDS

Common lead fields:

* Lead ID
* Property ID
* Project ID if applicable
* Sender user ID
* Sender name
* Sender phone used
* Sender profile phone
* Alternate number flag
* Sender email optional
* Message
* Interest type
* Source
* Status
* Assigned receiver
* Created date
* Updated date

Interest type examples:

* Call me
* WhatsApp me
* Need price details
* Want site visit
* Interested in buying
* Interested in renting
* Need more photos
* Need location details
* Need brochure
* Need proposal

---

# 36. LEAD SOURCES

Lead source should be tracked.

Possible sources:

* Property detail contact
* Property card contact
* WhatsApp click
* Call click
* Lead form
* Site visit request
* Brochure download
* Project enquiry
* Requirement proposal
* Banner ad click if connected
* Saved property follow-up if implemented
* Search result CTA

Lead source must be real.

Do not fake source.

---

# 37. LEAD RECEIVER RULE

Lead receiver depends on listing owner/entity.

Owner listing:

* Receiver = Owner

Broker listing:

* Receiver = Broker

Agency listing:

* Receiver = Agency
* Assigned agent if configured

Builder project:

* Receiver = Builder/project contact team

Admin-created listing:

* Receiver = assigned user/entity

If receiver missing:

* Show safe error.
* Admin queue if needed.
* Do not silently drop lead.

---

# 38. LEAD RECEIVER DASHBOARD DISPLAY

Receiver dashboard should show:

* Lead name
* Phone used
* Alternate number badge if used
* Email if provided
* Property/project
* Source
* Message
* Status
* Created time
* Contact actions
* Assignment if agency
* Notes
* Follow-up date if implemented

Alternate number must be clearly visible.

Example badge:

```txt id="7mpgcs"
Alternate Number
```

Tooltip:

```txt id="xuf2mk"
This user used a different number for this enquiry.
```

---

# 39. LEAD STATUS PIPELINE

Lead statuses may include:

* New
* Viewed
* Contacted
* Interested
* Site Visit Scheduled
* Site Visit Done
* Follow-up
* Converted
* Not Interested
* Invalid
* Duplicate
* Spam
* Closed
* Archived

Statuses should be real and user-updated.

Do not show fake conversion.

---

# 40. LEAD ASSIGNMENT RULE

Agency leads may be assigned to agents.

Assignment rules:

* Agency Owner can assign leads.
* Agent can view assigned leads.
* Agent cannot view unassigned/all leads unless permission.
* Assignment change should be logged if implemented.
* Admin may assign if permitted.

Broker/Owner leads may not need assignment unless team feature exists.

---

# 41. WHATSAPP CONTACT RULE

WhatsApp supports two modes:

1. Free `wa.me` link mode
2. API mode

Admin/Super Admin selects active mode.

## Free Mode

If free mode active:

* Use WhatsApp link.
* Can prefill message if allowed.
* Click opens WhatsApp.
* Log click if tracking implemented.

## API Mode

If API mode active:

* Use configured WhatsApp API.
* Send real message only if API configured.
* Log send status only if real.
* Show provider missing state if API not configured.

Do not fake WhatsApp sent status.

---

# 42. WHATSAPP PREFILL MESSAGE

Free wa.me mode can use safe prefilled message.

Example:

```txt id="mv4mc7"
Hello, I am interested in this property listed on My Gujarat Property: [Property Title] in [City].
```

Message should not include hidden private data unless allowed.

Use public property URL.

---

# 43. CALL CLICK RULE

Call click can work if phone is visible/allowed.

If contact hidden:

* Do not include phone number in DOM/API.
* Show lead form/request contact.

If call click is allowed:

* Use `tel:` link.
* Log click if tracking implemented.
* Do not fake successful call.

---

# 44. CONTACT REVEAL RULE

Contact reveal should be server-checked.

Before revealing contact:

Check:

* User logged in if required
* Listing active
* Contact mode
* User role if needed
* Subscription/plan if required
* Rate limits
* Abuse status
* Receiver contact availability
* User account status

If allowed:

* Reveal contact.
* Log reveal if implemented.

If denied:

* Show safe message.

Do not expose contact in client payload before permission check.

---

# 45. CONTACT RATE LIMIT RULE

To prevent abuse, contact actions may be rate-limited.

Possible limits:

* Contact reveals per day
* WhatsApp clicks per day
* Lead submissions per day
* Duplicate enquiry cooldown
* Same property contact cooldown
* Guest contact limit
* Suspicious IP limit

If rate limited:

```txt id="g3t4fu"
You have reached the contact limit. Please try again later.
```

Do not allow spam.

---

# 46. DUPLICATE LEAD RULE

If same user submits lead for same property repeatedly:

Options:

* Update existing lead timestamp
* Create follow-up note
* Block duplicate within cooldown
* Allow new lead if meaningful message
* Mark duplicate

Do not spam receiver with duplicate leads.

---

# 47. CONTACT PRIVACY RULE

Contact privacy is critical.

Never expose hidden contact via:

* HTML source
* API response
* JSON payload
* Metadata
* Schema
* Client state
* Search card data
* SEO page
* Browser dev tools
* Public storage file
* Public sitemap

Only server-approved reveal can provide contact.

---

# 48. CONTACT SECURITY RULE

Contact-related operations must be protected.

Required checks:

* Listing exists
* Listing is active
* Listing is public/approved
* Contact mode allows action
* User authentication if required
* User account active
* Receiver exists
* Rate limit
* Feature flag
* Provider mode
* Permission if dashboard/admin

Do not rely only on disabled buttons.

---

# 49. PROPERTY DETAIL SAVE ACTION

Save property behavior:

Guest:

* Open login/register.
* Preserve property ID.
* After login, save property.

Logged-in:

* Toggle save.
* Show success.
* Update UI.

If save feature disabled:

* Hide save button.

Do not fake saved state.

---

# 50. PROPERTY DETAIL SHARE ACTION

Share action can include:

* Native share API on mobile
* Copy link
* WhatsApp share
* Social share if implemented

Share URL should be public-safe.

Do not include private contact or hidden address.

---

# 51. PROPERTY REPORT ACTION

Report property helps trust.

Report reasons:

* Fake listing
* Wrong price
* Wrong location
* Already sold/rented
* Duplicate listing
* Broker pretending owner
* Fraud/scam
* Offensive content
* Wrong photos
* Contact not working
* Other

Guest may need login or can report guest depending policy.

Report goes to admin queue.

Do not fake report submission.

---

# 52. SIMILAR PROPERTIES RULE

Similar properties can show if real.

Similarity can be based on:

* Same city
* Same locality
* Same property type
* Similar price
* Similar BHK
* Similar area
* Same project
* Nearby localities

If no real similar properties:

* Hide section or show safe empty state.

Do not show fake similar properties.

---

# 53. PROPERTY CARD ACTION MATRIX

Actions by user state:

| Action      | Guest          | Buyer/Tenant         | Owner/Broker/Agency/Builder | Admin              |
| ----------- | -------------- | -------------------- | --------------------------- | ------------------ |
| View card   | Yes            | Yes                  | Yes                         | Yes                |
| View detail | Yes            | Yes                  | Yes                         | Yes                |
| Save        | Login required | Yes                  | Optional                    | N/A                |
| Contact     | Mode-based     | Mode-based           | Can receive                 | Monitor/manage     |
| WhatsApp    | Mode-based     | Mode-based           | Receive/contact             | Monitor if allowed |
| Report      | Login/policy   | Yes                  | Yes                         | Yes                |
| Edit        | No             | No unless owner role | Own/assigned                | Permission-based   |
| Approve     | No             | No                   | No                          | Yes                |
| Archive     | No             | No                   | Own/assigned                | Yes                |

---

# 54. PROPERTY DETAIL ACTION MATRIX

Actions by listing status:

| Listing Status | Public View | Contact          | Save           | Admin                     |
| -------------- | ----------- | ---------------- | -------------- | ------------------------- |
| Draft          | No          | No               | No             | Owner/Admin only          |
| Pending        | No          | No               | No             | Admin review              |
| Active         | Yes         | Yes if allowed   | Yes            | Manage                    |
| Rejected       | No          | No               | No             | User/Admin review         |
| Need Changes   | No          | No               | No             | Edit/resubmit             |
| Expired        | Maybe       | No or renew      | Maybe disabled | Renew/archive             |
| Sold           | Maybe       | Usually disabled | Maybe          | Manage                    |
| Rented         | Maybe       | Usually disabled | Maybe          | Manage                    |
| Archived       | No          | No               | No             | Admin/owner view          |
| Deleted        | No          | No               | No             | Admin only if soft delete |

---

# 55. LEAD NOTIFICATIONS

Lead notifications may be sent to receiver.

Channels:

* In-app
* Email if configured
* WhatsApp if configured
* SMS if configured
* Push if implemented

Trigger:

* New lead
* New site visit request
* New WhatsApp enquiry if tracked
* New brochure download if tracked
* Lead assigned to agent
* Lead status changed

Do not fake external delivery.

---

# 56. CONTACT AND SUBSCRIPTION CONNECTION

Contact access may depend on subscription.

Examples:

* Broker plan may unlock requirement leads.
* Owner free plan may have limited leads.
* Paid plan may show more leads.
* Lead unlock can be credit-based if implemented.
* Contact reveal may require plan in some business model.

Rules:

* Plan limits must be server-checked.
* User should see clear upgrade prompt.
* Do not hide already paid leads incorrectly.
* Do not show fake unlocked lead.

Detailed rules belong to subscription document.

---

# 57. CONTACT AND ROLE CONNECTION

Role affects contact behavior.

Buyer/Tenant:

* Can contact properties.

Owner:

* Can receive leads.
* Can contact buyer requirements only if business allows owner proposals.

Broker:

* Can receive property leads.
* Can contact requirements if plan/permission allows.

Agency:

* Can receive/manage assigned leads.
* Can assign leads to agents.

Agent:

* Can contact assigned leads only.

Builder:

* Can receive project/unit leads.

Admin:

* Can monitor/manage if permitted.

---

# 58. CONTACT AND REQUIREMENT CONNECTION

Buyer requirements and proposals create lead-like interactions.

If broker sends proposal and buyer responds:

* Create proposal interaction.
* Optionally create lead.
* Respect contact privacy.
* Use current/alternate number rule if buyer shares contact.
* Track source as requirement/proposal.

Detailed requirement flow belongs to requirement document.

---

# 59. LEAD STORAGE TABLES

Possible tables:

* leads
* lead_contacts
* lead_events
* lead_assignments
* lead_notes
* lead_status_history
* contact_reveals
* whatsapp_clicks
* call_clicks
* site_visit_requests
* property_reports

Possible lead fields:

* id
* property_id
* project_id
* requirement_id
* source
* sender_user_id
* sender_name
* profile_phone
* lead_phone
* phone_source
* alternate_phone_used
* email
* message
* receiver_user_id
* receiver_entity_id
* assigned_agent_id
* status
* created_at
* updated_at

Detailed schema belongs to database document.

---

# 60. PROPERTY CARD DATABASE FIELDS

Card query should fetch only public-safe fields:

* property id
* slug
* title
* price/rent
* city/locality display
* property type
* purpose
* area
* BHK if relevant
* cover image
* source tag
* verification badge status if public/real
* featured/sponsored status if active/real
* status
* created/updated date

Do not fetch:

* Hidden contact
* Full private address
* Admin notes
* Private documents
* Internal fraud notes
* Payment data
* Private user data

---

# 61. PROPERTY DETAIL DATABASE FIELDS

Detail query should fetch:

* Public property fields
* Public media
* Public location
* Public seller/entity summary
* Contact mode metadata
* Public amenities
* Public documents/brochure if allowed
* Related public listings

Hidden/private fields only after permission.

---

# 62. API / SERVER ACTIONS

Possible actions:

* getPropertyCards
* getPropertyDetail
* getProjectDetail
* toggleSaveProperty
* submitLead
* revealContact
* logCallClick
* logWhatsAppClick
* bookSiteVisit
* reportProperty
* getSimilarProperties
* updateLeadStatus
* assignLead
* addLeadNote

All must validate permissions and no-fake rules.

---

# 63. CONTACT FEATURE FLAGS

Possible feature flags:

```txt id="kzgj62"
property.cards.enabled
property.detail.enabled
property.save.enabled
property.share.enabled
property.report.enabled
property.contact.enabled
property.contact_reveal.enabled
property.lead_form.enabled
property.whatsapp.enabled
property.call_click.enabled
property.site_visit.enabled
property.similar_properties.enabled
property.compare.enabled
lead.alternate_number.enabled
lead.assignment.enabled
lead.pipeline.enabled
contact.rate_limit.enabled
contact.login_required.enabled
```

If feature flag off, hide UI and block backend.

---

# 64. PROPERTY DETAIL MOBILE CHECKLIST

Mobile detail page must check:

* Gallery works.
* Price/title visible.
* Location visible.
* Sticky CTA visible.
* Sticky CTA does not cover content.
* Contact sheet opens.
* Login/register intent preserved.
* Lead form fits.
* Current number/alternate number option visible.
* WhatsApp/call buttons follow provider mode.
* Seller card readable.
* Details sections not too long.
* Similar properties cards fit.
* Report action works.
* No horizontal scroll.
* Back icon works.

---

# 65. PROPERTY CARD MOBILE CHECKLIST

Mobile card must check:

* Image ratio correct.
* Price visible.
* Title does not overflow badly.
* Location visible.
* Key facts visible.
* Source tag visible.
* Contact CTA tappable.
* Save/share icons not too small.
* Sponsored label visible if active.
* No horizontal scroll.
* No fake badges.

---

# 66. CONTACT MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Guest sees public property card.
* Guest contact opens login/register if required.
* Logged-in buyer can submit lead.
* Lead form pre-fills profile number.
* User can use alternate number.
* Receiver dashboard shows alternate number badge.
* Contact does not overwrite profile phone.
* WhatsApp free mode opens wa.me.
* WhatsApp API mode handles provider correctly.
* Provider missing state is safe.
* Hidden contact is not in public API response.
* Expired listing contact disabled.
* Draft/pending listing not public.
* Seller/broker/agency/builder receiver gets correct lead.
* Agent sees only assigned leads.
* Save property works.
* Report property works.
* Mobile sticky CTA works.
* No fake lead count/analytics.
* No screenshot/video capture required.

---

# 67. PASS / FAIL RULE

This phase is PASS only if:

* Property cards show relevant real fields.
* Detail page shows type-aware real details.
* Hidden contact is not leaked.
* Contact visibility modes are enforced server-side.
* Lead form works.
* Current number/alternate number behavior works.
* Alternate number badge appears for receiver.
* WhatsApp mode respects provider setting.
* No fake WhatsApp send.
* No fake lead count.
* Mobile sticky CTA works.
* Draft/pending/rejected listings are not public.
* Feature registry updated.
* Manual verification completed.

If hidden phone appears in public API/HTML, mark FAIL.

If alternate number behavior is missing, mark FAIL or PARTIAL depending phase scope.

If logged-in user contact flow still asks phone unnecessarily without profile number option, mark PARTIAL.

---

# 68. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`
* `05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those docs for auth, location, property posting, requirement, dashboard, provider, subscription, database and verification details.

---

# 69. END OF FILE

This file defines property card, property detail, contact visibility and lead rules for My Gujarat Property.

Property contact must be conversion-friendly, mobile-first, role-aware, secure, no-fake, provider-aware and privacy-safe.

Nothing from uploaded docs or user chat instructions should be skipped.
