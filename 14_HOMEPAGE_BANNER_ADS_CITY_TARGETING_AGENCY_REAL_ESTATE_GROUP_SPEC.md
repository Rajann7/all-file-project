# MY GUJARAT PROPERTY

# HOMEPAGE BANNER ADS, CITY TARGETING, AGENCY & REAL ESTATE GROUP ADVERTISING SPEC

## FILE NAME

`14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete homepage banner ads, sponsored carousel, city targeting, advertiser role, agency advertising, real estate group advertising, banner upload, payment, approval, expiry and analytics behavior for **My Gujarat Property**.

This file must be read before building or redesigning:

* Homepage banner ads
* Sponsored banner carousel
* City-targeted ads
* Agency banner ads
* Real Estate Group banner ads
* Broker banner ads if enabled
* Builder banner ads if enabled
* Developer banner ads if enabled
* Advertiser dashboard
* Banner ad dashboard
* Banner ad upload
* Desktop/tablet/mobile banner images
* Banner ad pricing
* Banner ad payment
* Banner ad moderation
* Banner ad scheduling
* Banner ad expiry
* Banner ad carousel rotation
* Sponsored/ad label
* Admin banner ad approval
* City-first ad priority
* Banner ad analytics if implemented
* No-fake ad metrics

The goal is to create a paid advertising system where agencies, real estate groups, builders or other eligible business users can promote themselves or their listings/projects on the homepage and city-based sections.

---

# 2. CORE BANNER ADS PRINCIPLE

Homepage banner ads must be real paid/approved advertisements.

Banner ads must not be fake placeholders.

Banner ads must not display unpaid, unapproved, expired or rejected campaigns.

Banner ads must:

* Be approved by admin if approval required
* Be paid if payment required
* Be active within date range
* Be targeted correctly
* Show sponsored/ad label
* Respect city priority
* Use correct image for device
* Expire automatically
* Be manageable from advertiser dashboard
* Be controllable from admin
* Use real analytics only if tracking exists

No fake impressions.

No fake clicks.

No fake active ad status.

---

# 3. BANNER ADS BUSINESS PURPOSE

Banner ads are a monetization feature.

They allow eligible real estate businesses to promote:

* Agency brand
* Real estate group
* Builder project
* Developer project
* Broker service if enabled
* Featured property/listing if enabled
* New launch project
* City-specific offer
* Real estate service if allowed by policy

Banner ads are separate from normal property listing plans unless a plan includes banner benefits.

Banner ads can be sold:

* As separate paid package
* As plan add-on
* As included benefit in premium plans
* As admin-approved manual campaign
* As launch offer if enabled

---

# 4. ELIGIBLE ADVERTISER ROLES

Primary eligible roles:

* Agency
* Real Estate Group
* Builder
* Developer if implemented

Optional eligible roles:

* Broker
* Owner for paid property boost if business allows
* Project advertiser
* Admin-created advertiser

Default recommendation:

```txt id="h99gb6"
Agency, Real Estate Group and Builder should be primary banner advertisers.
```

Buyer/Tenant should not create banner ads.

Public users must login/register and have eligible role before submitting ads.

---

# 5. REAL ESTATE GROUP ROLE RULE

Real Estate Group can be:

1. Separate role, or
2. Mapped under Agency role, or
3. Treated as Advertiser profile

If separate role is implemented:

* Real Estate Group gets advertiser dashboard.
* Can upload logo/profile.
* Can purchase banner package.
* Can submit banner ads.
* Can target city.
* Can view ad status.

If not separate:

* Use Agency profile with banner ad access.

Do not create duplicate confusing role if not needed.

---

# 6. BANNER AD PLACEMENTS

Possible placements:

* Homepage hero carousel
* Homepage below search section
* Homepage city section
* Search results top banner
* Search results inline banner
* City page banner
* Locality page banner
* Property detail side/banner
* Project detail banner
* Dashboard promotional banner if allowed
* Mobile app-like home carousel

Initial priority:

```txt id="bm5rdu"
Homepage banner carousel with city targeting.
```

Do not implement too many placements at once unless system supports it.

---

# 7. HOMEPAGE BANNER CAROUSEL

Homepage banner carousel should look premium and real-estate focused.

Carousel behavior:

* Shows approved active ads.
* Prioritizes selected city.
* Supports multiple banners.
* Rotates banners.
* Shows sponsored/ad label.
* Supports click/CTA.
* Supports manual swipe on mobile.
* Supports navigation dots/arrows.
* Uses correct image by device.
* Lazy loads where appropriate.
* Does not block search.
* Does not dominate entire homepage.

Homepage search must remain primary.

Banner ads should support monetization without damaging user experience.

---

# 8. CITY-FIRST AD PRIORITY

Banner ads must prioritize selected/current city.

Priority order:

1. User manually selected city
2. Search city context
3. Logged-in user profile city
4. Browser location if permission granted
5. IP-based estimate if available
6. Default city
7. Gujarat-wide ads
8. Other active ads

Example:

If user selected Rajkot:

* Rajkot ads first
* Gujarat-wide ads next
* Nearby city ads if enabled
* Other active ads after

If user selected Ahmedabad:

* Ahmedabad ads first
* Gujarat-wide ads next
* Other active ads after

Do not show Ahmedabad ad first to Rajkot user if Rajkot ads are available and active.

---

# 9. CITY TARGETING OPTIONS

Advertiser can target:

* Single city
* Multiple cities if package allows
* District if package allows
* Gujarat-wide if package allows
* Locality if future feature enabled

Basic launch should support:

* City targeting
* Gujarat-wide targeting

Advanced later:

* Locality targeting
* Property type targeting
* Audience role targeting
* Search intent targeting
* Budget targeting
* Device targeting

Do not show targeting options that do not work.

---

# 10. AD TARGETING FALLBACK

If no city-specific ad exists:

Show fallback ads in this order:

1. Gujarat-wide active ads
2. Nearby city ads if enabled
3. Platform default house ad if real/admin-created
4. Hide banner section

Do not show fake ad.

If using platform house ad, label appropriately only if it is internal promotion, not paid ad.

---

# 11. BANNER AD CAROUSEL ROTATION

Rotation rules:

* Rotate only active approved ads.
* Prioritize city-relevant ads.
* Respect package priority if configured.
* Respect ad start/end dates.
* Avoid showing same ad repeatedly if multiple ads available.
* Allow admin priority override if enabled.
* Do not show expired ads.
* Do not show rejected ads.

If multiple Rajkot ads exist, rotate between them.

If only one Rajkot ad exists, show it and optionally mix Gujarat-wide ads.

---

# 12. SPONSORED / AD LABEL RULE

Every paid banner ad must show label:

* Sponsored
* Ad
* Promoted

Label must be visible but not ugly.

Examples:

```txt id="7cz5jc"
Sponsored
```

or:

```txt id="8penxt"
Ad
```

Do not hide ad label.

Do not make paid ad look like organic platform recommendation without disclosure.

---

# 13. BANNER AD CONTENT TYPES

Banner ads can promote:

* Agency profile
* Builder profile
* Project page
* Property detail
* Search result page
* External website if admin allows
* WhatsApp lead link if admin allows
* Landing page if approved
* Real Estate Group page
* Banner ad campaign page if implemented

Default safer click destinations:

* Internal agency profile
* Internal builder profile
* Internal project page
* Internal property page
* Internal search page

External links should require admin approval.

---

# 14. BANNER AD CTA OPTIONS

CTA text examples:

* View Details
* Contact Now
* View Project
* View Agency
* Call Now
* WhatsApp
* Explore Properties
* Book Site Visit
* Get Offers
* Learn More

CTA must match destination.

Do not show “Book Now” if booking/payment is not supported.

Do not imply property transaction payment through platform.

---

# 15. BANNER AD CREATION FLOW

Advertiser flow:

```txt id="rbndw9"
Login/Register
Select eligible role
Open Banner Ads Dashboard
Choose package/placement
Select target city/cities
Upload desktop/tablet/mobile banner images
Add title/CTA/link
Preview
Pay or use eligible plan benefit
Submit for admin approval
Admin approves/rejects
Ad becomes scheduled/active
Ad expires automatically
```

If payment required before approval:

* Payment Pending → Submitted → Pending Review → Approved → Active

If approval before payment:

* Draft → Pending Review → Approved → Payment Pending → Scheduled/Active

Business can choose flow.

Recommended:

```txt id="hrvbfc"
Payment first or package selection first, then admin approval before public display.
```

---

# 16. BANNER AD STATUS

Banner statuses:

```txt id="w2vz52"
Draft
Payment Pending
Payment Failed
Submitted
Pending Review
Need Changes
Rejected
Approved
Scheduled
Active
Paused
Expired
Archived
Cancelled
Refunded
```

Public display allowed only when:

```txt id="liq1zw"
status = Active
payment_status = Success or plan benefit valid
approval_status = Approved
current_date between start_date and end_date
```

No other status should display publicly.

---

# 17. BANNER AD PAYMENT RULE

If banner ad is paid:

* Payment must be real.
* Payment must be verified server-side.
* Payment status must update from provider/webhook/manual admin verification.
* Ad must not go active before payment success unless admin manually approves special case.
* Manual override must be audit logged.

Payment statuses:

```txt id="xc7eds"
Not Required
Pending
Success
Failed
Cancelled
Refunded
Partially Refunded
Manually Verified
```

Do not fake successful payment.

---

# 18. BANNER AD PACKAGE TYPES

Possible packages:

* Homepage City Banner
* Homepage Gujarat-wide Banner
* Search Result Banner
* City Page Banner
* Locality Page Banner
* Project Promotion Banner
* Featured Agency Banner
* Featured Builder Banner
* Short Duration Campaign
* Monthly Campaign
* Weekly Campaign

Package fields:

* Name
* Placement
* Price
* Duration
* City count limit
* Image count/device variants
* Priority level
* Impression/click analytics enabled if tracked
* Approval required
* Active/inactive
* Role eligibility

Exact pricing belongs to subscription/payment document.

---

# 19. BANNER AD DURATION

Duration options:

* 1 day if enabled
* 3 days
* 7 days
* 15 days
* 30 days
* Custom admin duration

Each ad must have:

* Start date
* End date
* Time zone
* Status
* Auto-expire behavior

When end date passes:

* Ad stops showing.
* Status becomes Expired.
* Advertiser sees renew option.
* Admin can archive.

Do not show expired ad.

---

# 20. BANNER AD IMAGE VARIANTS

Every banner ad should support device-specific images.

Required variants:

* Desktop image
* Tablet image
* Mobile image

Optional:

* Square social-like image
* Dark/light variant
* High-resolution retina variant

If only one image is uploaded, system may auto-fit/crop for other devices only if preview is shown and advertiser accepts.

Recommended: separate upload for each device.

---

# 21. BANNER IMAGE SIZE GUIDELINES

Upload UI must show recommended sizes.

Recommended desktop:

```txt id="i4wxgl"
Desktop banner: 1920x500 px or 1600x450 px, wide 16:4 to 16:5 style
```

Recommended tablet:

```txt id="42a8c7"
Tablet banner: 1200x450 px
```

Recommended mobile:

```txt id="w0lnp4"
Mobile banner: 1080x1080 px or 1080x1350 px depending carousel design
```

Alternative mobile hero wide:

```txt id="nyun2w"
Mobile wide banner: 1080x600 px
```

Actual size should match final UI layout.

The upload component must display final accepted size/ratio.

---

# 22. BANNER IMAGE UPLOAD RULE

Banner upload must include:

* Recommended size
* Recommended ratio
* Accepted formats
* Max file size
* Preview
* Crop
* Fit
* Replace
* Remove
* Upload progress
* Error state
* Device preview
* Desktop preview
* Tablet preview
* Mobile preview

Accepted formats:

* JPG
* JPEG
* PNG
* WEBP

Optional future:

* GIF/video only if explicitly supported and performance-safe

Do not allow huge unoptimized images.

Do not stretch banner.

---

# 23. BANNER IMAGE CROP RULE

Crop/fit must work.

For each device image:

* Show crop frame.
* Allow zoom.
* Allow move.
* Preview final result.
* Save crop.
* Cancel crop.
* Show safe area for text/CTA if possible.

If uploaded image is wrong size:

* Allow crop/fit.
* Warn user.
* Do not break layout.
* Do not silently crop important content.

---

# 24. BANNER TEXT RULE

Banner ad may have text inside image or separate overlay text.

If separate overlay text is implemented, fields may include:

* Headline
* Subheadline
* CTA
* Brand name
* Offer text
* Disclaimer

Overlay text must be responsive.

If not implemented, require advertiser to include text in banner image.

Do not show fake offer.

Admin should review misleading text.

---

# 25. BANNER AD REVIEW CHECKLIST

Admin should review:

* Image quality
* Correct size/preview
* No misleading claims
* No fake “No.1” claim unless verified
* No illegal content
* No offensive content
* No wrong city targeting
* Payment status
* Advertiser role eligibility
* Landing link safety
* Contact details validity
* Sponsored label
* Duration
* Start/end date

Admin can approve/reject/request changes.

---

# 26. BANNER AD REJECTION REASONS

Common rejection reasons:

* Low quality image
* Wrong image size
* Misleading claim
* Invalid landing link
* Payment not received
* Not eligible role
* Wrong city targeting
* Offensive content
* Duplicate ad
* Contact information issue
* Policy violation
* Missing required image variant

User should see reason and resubmit.

---

# 27. ADVERTISER DASHBOARD

Advertiser dashboard should show:

* Active banner ads
* Pending ads
* Rejected ads
* Draft ads
* Expired ads
* Payment pending ads
* City targeting
* Start/end date
* Status
* Package
* Image preview
* Renewal CTA
* Analytics if real
* Create new ad CTA

Eligible dashboards:

* Agency dashboard
* Real Estate Group dashboard
* Builder dashboard
* Broker dashboard if enabled
* Developer dashboard if enabled

---

# 28. ADVERTISER DASHBOARD ACTIONS

Advertiser can:

* Create ad
* Upload images
* Preview ad
* Save draft
* Submit for review
* Pay
* View status
* Edit draft
* Edit rejected/need changes
* Pause if allowed
* Renew expired ad
* Archive
* View analytics if implemented

Advertiser cannot:

* Approve own ad
* Change payment status
* Extend duration without payment/admin approval
* Fake impressions/clicks
* Force ad active

---

# 29. ADMIN BANNER ADS DASHBOARD

Admin banner ads dashboard should show:

* Pending review
* Active ads
* Scheduled ads
* Expired ads
* Rejected ads
* Payment pending
* City targeting
* Advertiser entity
* Package
* Placement
* Start/end date
* Payment status
* Approval status
* Preview
* Analytics if real

Admin actions:

* Approve
* Reject
* Request changes
* Pause
* Resume
* Archive
* Edit schedule if permitted
* View payment
* View audit log

Super Admin can manage packages/settings.

---

# 30. SUPER ADMIN BANNER SETTINGS

Super Admin controls:

* Banner ads enabled/disabled
* Eligible roles
* Placements
* Package pricing
* Duration options
* City targeting rules
* Gujarat-wide allowed
* Approval required
* Payment required
* Desktop/tablet/mobile image requirements
* Max file size
* Carousel rotation settings
* Priority settings
* Auto-expiry
* Sponsored label text
* External link allowed
* Analytics tracking enabled
* Refund/cancellation policy if implemented

Visible settings must work.

No fake settings.

---

# 31. CITY TARGETING DISPLAY LOGIC

Banner query should filter by:

* Placement
* Active status
* Approved status
* Payment success/valid plan
* Start date <= now
* End date >= now
* Target city match
* Gujarat-wide fallback
* Role eligibility if placement-specific
* Priority/sort logic

Sort priority example:

```txt id="s2pndz"
1. Exact selected city ads
2. Multi-city ads containing selected city
3. District ads if enabled
4. Gujarat-wide ads
5. Nearby city ads if enabled
6. Other active fallback ads if allowed
```

Do not fetch inactive ads for public display.

---

# 32. BANNER AD CLICK TRACKING

Click tracking is optional but useful.

If implemented, track:

* Ad ID
* Placement
* City context
* Device type
* User ID if logged in
* Anonymous session ID if guest
* Timestamp
* Destination
* Referrer/page
* IP/user-agent if policy allows

If click tracking not implemented:

* Do not show click count.
* Do not show CTR.

---

# 33. BANNER AD IMPRESSION TRACKING

Impression tracking is optional.

If implemented, count impression only when ad is actually viewed.

Avoid fake impression counting.

Track:

* Ad ID
* Placement
* City context
* Device
* Timestamp
* Session/user
* View threshold if implemented

If not implemented:

* Hide impressions.

---

# 34. BANNER AD ANALYTICS

Analytics can show:

* Impressions
* Clicks
* CTR
* City-wise views
* Device-wise views
* Leads if connected
* Date-wise performance

Only show if real tracking exists.

Do not show fake analytics.

If analytics partial, label clearly.

---

# 35. BANNER AD LEAD CONNECTION

Banner ads can create leads if connected.

Possible actions:

* Click to agency profile
* Click to builder project
* Click to WhatsApp
* Click to enquiry form
* Click to call
* Click to project/property detail

If lead generated:

* Source = banner_ad
* Store ad ID
* Store advertiser entity
* Store city context
* Store phone used/alternate number if lead form applies

Lead connection must be real.

---

# 36. BANNER AD WHATSAPP CONNECTION

If banner CTA is WhatsApp:

* Use WhatsApp provider mode.
* Free mode opens wa.me.
* API mode sends real message only if configured.
* Log click/send only if real.
* Do not fake message sent.

Admin can allow/block WhatsApp CTA.

---

# 37. BANNER AD PAYMENT + APPROVAL COMBINATIONS

Possible workflows:

## Workflow A — Pay Then Review

```txt id="vdaync"
Draft → Payment Pending → Paid → Pending Review → Approved → Scheduled/Active
```

## Workflow B — Review Then Pay

```txt id="v8b8wl"
Draft → Pending Review → Approved → Payment Pending → Paid → Scheduled/Active
```

## Workflow C — Plan Benefit

```txt id="zx9999"
Draft → Plan Benefit Selected → Pending Review → Approved → Scheduled/Active
```

## Workflow D — Admin Manual Campaign

```txt id="6mwdsk"
Admin Creates → Approved → Scheduled/Active
```

All workflows must be clear.

No ad should appear unless final active conditions are met.

---

# 38. BANNER AD RENEWAL

Expired ads can be renewed.

Renewal flow:

* User opens expired ad.
* Click Renew.
* Select same/different package.
* Confirm city/duration.
* Pay or use plan benefit.
* Submit if approval required.
* New start/end date created.

Do not simply extend expired ad without payment/admin rule.

---

# 39. BANNER AD PAUSE / RESUME

Pause rules:

* Admin can pause any ad if permission.
* Advertiser can pause own ad if setting allows.
* Paused ad does not display.
* Resume only if still within date range.
* If end date passed, require renewal.

Pause/resume must be audit logged if admin action.

---

# 40. BANNER AD REFUND / CANCELLATION

Refund/cancellation is optional.

If implemented:

* Follow payment provider rules.
* Show policy.
* Admin can approve refund if permitted.
* Refund status tracked.
* Cancelled ad stops displaying.
* Audit log required.

If not implemented, show clear policy/no refund terms.

Do not fake refund status.

---

# 41. BANNER AD EXTERNAL LINK RULE

External links are higher risk.

If allowed:

* Require admin approval.
* Validate URL.
* Block unsafe URLs.
* Open safely.
* Add nofollow/sponsored where applicable.
* Keep audit log.
* Show destination preview to admin.

If not allowed:

* Only internal links.

Recommended default:

```txt id="07eu1d"
Use internal links only at launch.
```

---

# 42. BANNER AD INTERNAL DESTINATION RULE

Allowed internal destinations:

* Agency profile
* Builder profile
* Broker profile if enabled
* Project detail
* Property detail
* Search results
* City page
* Contact/enquiry form
* Requirement page if relevant
* Pricing page for platform internal ad

Destination must exist and be public/allowed.

Do not link to draft/private pages.

---

# 43. BANNER AD SEO RULE

Banner ads should not create thin SEO pages.

Rules:

* Banner ad itself does not need indexable page.
* Destination page handles SEO.
* Ad links can be sponsored/nofollow if external.
* Do not put fake SEO text inside ad system.
* Expired ads should not be indexable.
* Ad archive pages should be noindex unless purposely built.

---

# 44. BANNER AD ACCESS CONTROL

Access rules:

Advertiser can view/edit only own ads.

Agency Owner can manage agency ads.

Agency Agent can manage ads only if permission allows.

Builder can manage builder ads.

Broker can manage broker ads only if enabled.

Admin can manage ads based on permission.

Super Admin can manage all.

Server-side checks required.

---

# 45. BANNER AD DATA SECURITY

Do not expose:

* Payment details to public
* Admin notes
* Rejection internal notes
* Draft ads
* Pending ads
* User private data
* Provider payment IDs publicly
* Internal targeting priority scores if private

Public API should return only active public ad fields.

---

# 46. PUBLIC BANNER API FIELDS

Public banner query should return:

* Ad ID
* Image URL for device
* Alt text
* CTA text
* Destination URL
* Sponsored label
* Advertiser display name if needed
* Placement
* City targeting public-safe
* Tracking token if implemented

Should not return:

* Payment status
* Admin notes
* Private contact
* Internal priority
* Rejected/draft data
* Secret URLs

---

# 47. BANNER AD DATABASE MODULES

Possible tables:

* banner_ad_packages
* banner_ads
* banner_ad_images
* banner_ad_targets
* banner_ad_payments
* banner_ad_status_history
* banner_ad_clicks
* banner_ad_impressions
* banner_ad_moderation
* banner_ad_audit_logs

Detailed schema belongs to database document.

---

# 48. BANNER AD STATUS HISTORY

Status history should track:

* Created
* Submitted
* Paid
* Approved
* Rejected
* Changes requested
* Scheduled
* Active
* Paused
* Expired
* Renewed
* Archived
* Cancelled

Each event:

* Actor
* Timestamp
* Old status
* New status
* Note/reason if any

---

# 49. BANNER AD AUDIT LOG

Audit important actions:

* Package created/updated
* Ad submitted
* Payment verified
* Admin approved/rejected
* Admin changed schedule
* Ad paused/resumed
* Ad expired
* Ad renewed
* Ad archived
* Target city changed
* Image changed
* External link approved

Audit logs must be real if visible.

---

# 50. BANNER AD NOTIFICATIONS

Advertiser notifications:

* Draft saved
* Payment pending
* Payment success
* Payment failed
* Submitted for review
* Approved
* Rejected
* Need changes
* Scheduled
* Active
* Expiring soon
* Expired
* Renewed
* Paused by admin

Admin notifications:

* New ad submitted
* Payment received
* Ad needs review
* Ad reported
* Provider/payment issue

No fake external notifications.

---

# 51. BANNER AD REPORTING

Users/admin can report ad if needed.

Report reasons:

* Misleading ad
* Wrong city
* Offensive content
* Fake project/agency claim
* Broken link
* Spam
* Fraud
* Policy violation

Admin can review and pause/remove ad.

---

# 52. BANNER AD PERFORMANCE RULE

Banner system must not slow homepage.

Rules:

* Use optimized images.
* Serve correct device image.
* Lazy load lower banners.
* Do not load all ads.
* Limit carousel items.
* Use caching where safe.
* Avoid large uncompressed files.
* Avoid heavy scripts.
* Do not block search loading.

Homepage search remains priority.

---

# 53. BANNER AD EMPTY STATE

If no ads:

Options:

* Hide banner section.
* Show internal platform announcement if real.
* Show city guide/search block instead.
* Show “Advertise here” CTA if desired.

Do not show fake advertiser banners.

Advertiser dashboard empty:

```txt id="auyybf"
You have not created any banner ads yet. Create your first city-targeted banner ad.
```

Admin queue empty:

```txt id="170qmu"
No banner ads pending review.
```

---

# 54. BANNER AD ERROR STATE

Error examples:

Image too small:

```txt id="dq2tk1"
Image is too small for desktop banner. Recommended size is 1920x500 px.
```

Payment failed:

```txt id="zdnws5"
Payment failed. Please try again or contact support.
```

Approval missing:

```txt id="ctvlyu"
This ad is not active yet. Admin approval is required.
```

Provider missing:

```txt id="s8b6sp"
Payment provider is not configured. Please contact support.
```

Do not show raw errors.

---

# 55. BANNER AD SUCCESS STATE

Success examples:

```txt id="53hmih"
Banner ad saved as draft.
```

```txt id="19xosa"
Banner ad submitted for review.
```

```txt id="wa1t7k"
Payment successful. Your ad is pending admin approval.
```

```txt id="0n1hif"
Banner ad approved and scheduled.
```

Success only after server confirmation.

---

# 56. BANNER AD PERMISSIONS

Permission examples:

```txt id="9ne16m"
banner_ad.create
banner_ad.view.own
banner_ad.update.own
banner_ad.submit
banner_ad.pay
banner_ad.pause.own
banner_ad.renew
banner_ad.view.analytics.own

banner_ad.view.all
banner_ad.approve
banner_ad.reject
banner_ad.request_changes
banner_ad.pause.any
banner_ad.resume.any
banner_ad.archive.any
banner_ad.manage_packages
banner_ad.manage_settings
banner_ad.view_payments
banner_ad.view_analytics.all
```

Permissions must be server-side.

---

# 57. BANNER AD FEATURE FLAGS

Possible feature flags:

```txt id="a5w4cd"
banner_ads.enabled
banner_ads.homepage.enabled
banner_ads.city_targeting.enabled
banner_ads.gujarat_wide.enabled
banner_ads.locality_targeting.enabled
banner_ads.payment_required
banner_ads.approval_required
banner_ads.desktop_image.required
banner_ads.tablet_image.required
banner_ads.mobile_image.required
banner_ads.external_links.enabled
banner_ads.analytics.enabled
banner_ads.click_tracking.enabled
banner_ads.impression_tracking.enabled
banner_ads.agency.enabled
banner_ads.real_estate_group.enabled
banner_ads.builder.enabled
banner_ads.broker.enabled
banner_ads.owner.enabled
banner_ads.admin_manual_campaign.enabled
```

If feature flag is off, hide UI and block backend action.

---

# 58. BANNER AD COMPONENTS

Recommended components:

* BannerCarousel
* CityTargetedBannerQuery
* SponsoredLabel
* BannerAdCard
* BannerAdUploader
* BannerImageCropper
* DevicePreviewTabs
* BannerPackageSelector
* BannerTargetCitySelector
* BannerAdPreview
* BannerPaymentStep
* BannerSubmitStep
* AdvertiserBannerDashboard
* AdminBannerAdQueue
* AdminBannerAdReviewPanel
* BannerAdStatusBadge
* BannerAdAnalyticsCard
* BannerAdEmptyState
* BannerAdErrorState
* BannerAdRenewalModal

Avoid duplicate random ad components.

---

# 59. BANNER AD MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Guest cannot create banner ad without login.
* Buyer/Tenant cannot create banner ad unless role upgrade allowed.
* Agency can open banner ad dashboard.
* Real Estate Group can open ad dashboard if role exists.
* Builder can open ad dashboard if enabled.
* Broker can open ad dashboard only if enabled.
* Advertiser can select city.
* Advertiser can upload desktop image.
* Advertiser can upload tablet image.
* Advertiser can upload mobile image.
* Upload UI shows recommended sizes/ratios.
* Crop/preview works.
* Payment pending blocks public display.
* Admin approval required if enabled.
* Rejected ad does not display.
* Active approved paid ad displays.
* Expired ad auto-hides.
* Rajkot selected city shows Rajkot ads first.
* Ahmedabad selected city shows Ahmedabad ads first.
* Gujarat-wide fallback works.
* Sponsored/ad label is visible.
* External link requires approval if enabled.
* Analytics only shows if real.
* Mobile carousel works without horizontal scroll.
* No screenshot/video capture required.

---

# 60. PASS / FAIL RULE

Banner Ads phase is PASS only if:

* Banner ads are real data.
* Only approved/paid/active ads display.
* City targeting works.
* Selected city priority works.
* Expired ads hide.
* Desktop/tablet/mobile image handling works.
* Upload UI shows recommended size/ratio.
* Crop/preview works or is clearly pending.
* Sponsored/ad label appears.
* Advertiser dashboard exists for eligible roles.
* Admin review exists if approval required.
* Payment state is respected if payment required.
* No fake impressions/clicks are shown.
* Feature registry updated.
* Manual verification completed.

If unpaid/unapproved ad appears publicly, mark FAIL.

If city targeting is ignored, mark FAIL.

If ad metrics are fake, mark FAIL.

---

# 61. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `04_HOME_SEARCH_DYNAMIC_FILTERS_CITY_PROPERTY_DISCOVERY_SPEC.md`
* `05_SEO_CITY_LOCALITY_PROGRAMMATIC_SEARCH_GROWTH_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `08_GUJARAT_LOCATION_HIERARCHY_CITY_TALUKA_VILLAGE_ADDRESS_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for dashboard, role, payment, provider, database and QA details.

---

# 62. END OF FILE

This file defines homepage banner ads, city targeting, agency/real estate group advertising, banner upload, payment, approval, expiry and carousel behavior for My Gujarat Property.

Banner ads must be paid/eligible, approved, city-aware, device-responsive, clearly labeled as sponsored, automatically expired, dashboard-manageable, admin-controlled and no-fake.

Nothing from uploaded docs or user chat instructions should be skipped.
