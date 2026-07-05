# MY GUJARAT PROPERTY

# VERIFICATION, FRAUD PREVENTION, TRUST, REPORTING & SAFETY SYSTEM SPEC

## FILE NAME

`19_VERIFICATION_FRAUD_TRUST_REPORTING_SYSTEM_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete verification, fraud prevention, trust badge, report abuse, fake listing detection, role verification, business verification, property verification and safety system for **My Gujarat Property**.

This file must be read before building or redesigning:

* Verification center
* Owner verification
* Broker verification
* Agency verification
* Builder verification
* Property verification
* Project verification
* Role verification
* RERA verification if implemented
* Document upload/review
* Verified badges
* Trust signals
* Report property system
* Report profile system
* Report requirement system
* Report proposal system
* Report banner ad system
* Fraud detection
* Duplicate listing review
* Broker pretending owner handling
* Fake listing moderation
* Contact abuse handling
* Admin verification workflow
* Public trust display
* Private document storage
* No-fake verification behavior

The goal is to build a trustworthy real estate marketplace where users can identify source, verify authenticity and report suspicious activity.

---

# 2. CORE TRUST PRINCIPLE

Trust must be real.

The platform must clearly show:

* Who posted the listing
* Whether the source is owner/broker/agency/builder
* Whether the profile is verified
* Whether the property is verified
* Whether RERA/project info is verified if shown
* Whether brokerage is included/extra/negotiable/no brokerage
* Whether listing is active/sold/rented/expired
* Whether a listing was reported or under review if public policy allows

Do not show fake verified badges.

Do not show fake RERA.

Do not show fake ratings.

Do not show fake “trusted” labels.

---

# 3. TRUST SIGNALS

Trust signals may include:

* Listing source tag
* Verified profile badge
* Verified property badge
* Verified agency badge
* Verified builder badge
* RERA number if real
* Property status
* Brokerage transparency
* Date updated
* Report listing option
* Contact visibility controls
* Public profile
* Admin approved listing
* Verified documents if approved
* Active subscription/plan if public policy allows

Trust signals should be simple and understandable.

---

# 4. LISTING SOURCE TAG

Every listing must show source tag.

Source tags:

* Direct Owner
* Broker
* Agency
* Builder
* Developer
* Real Estate Group if applicable
* Admin Added if allowed

Source tag is derived from posting role/entity.

User must not manually fake source tag.

If a broker posts a listing, it must not show Direct Owner unless admin-approved special case exists.

This is critical for transparency.

---

# 5. BROKERAGE TRANSPARENCY

Brokerage information should be clearly shown where relevant.

Options:

* No Brokerage
* Brokerage Extra
* Brokerage Included
* Brokerage Negotiable
* As per discussion

Owner direct listings can show No Brokerage if true.

Broker/Agency listings should show brokerage policy.

Do not hide brokerage if user provided it.

Do not claim no brokerage falsely.

---

# 6. VERIFICATION TYPES

Verification types:

* Phone verification
* Email verification
* User identity verification if implemented
* Owner verification
* Broker verification
* Agency verification
* Builder verification
* Developer verification
* Real Estate Group verification
* Property verification
* Project verification
* RERA verification if implemented
* Document verification
* Address/office verification if implemented
* Payment/subscription verification is separate

Each verification type must have its own status.

---

# 7. VERIFICATION STATUS

Verification statuses:

```txt id="m5o6qu"
Not Submitted
Draft
Submitted
Pending Review
Under Review
Need More Details
Verified
Rejected
Expired
Suspended
Revoked
Archived
```

Only `Verified` status can show verified badge.

Pending verification should not show verified badge.

Rejected verification should not show verified badge.

Expired verification should not show verified badge unless revalidated.

---

# 8. VERIFIED BADGE RULE

Verified badge appears only when verification is approved.

Badge examples:

* Verified Owner
* Verified Broker
* Verified Agency
* Verified Builder
* Verified Property
* Verified Project
* RERA Verified if actually verified

Rules:

* Badge must come from verification table/status.
* Badge cannot be manually toggled by public user.
* Admin/Super Admin action required unless automated verification is real.
* Badge should disappear if verification expires/suspends/revokes.
* Badge must be audit logged when changed.

Do not show fake badge for design.

---

# 9. PHONE VERIFICATION

Phone verification usually happens during OTP login/register.

Phone verified means:

* User controls the phone number.
* It does not mean property/business is genuine.
* It does not mean owner/broker/builder is verified.

Public UI should not confuse phone verification with business verification.

---

# 10. EMAIL VERIFICATION

Email verification is optional from profile.

Email verified means:

* User controls email.
* It does not mean business/property verified.

If email provider missing, do not fake email verification.

---

# 11. OWNER VERIFICATION

Owner verification may collect:

* Owner name
* Phone verified
* Property ownership document if required
* Address proof if policy
* Property tax/utility document if needed
* Consent declaration
* Property details match
* Admin note

Owner verification can be optional or required based on admin settings.

Owner verification documents must be private.

---

# 12. BROKER VERIFICATION

Broker verification may collect:

* Broker full name
* Business name
* Phone verified
* Email optional
* Office address
* Operating city/locality
* Broker photo/logo
* RERA/license if applicable
* Business card if accepted
* Identity/business proof if policy
* Social/website link if real
* Experience declaration
* Admin note

Broker verification improves trust but must not be fake.

---

# 13. AGENCY VERIFICATION

Agency verification may collect:

* Agency name
* Agency owner name
* Agency logo
* Office address
* Phone/email
* Business registration if applicable
* GST if applicable
* RERA/license if applicable
* Website/social link if real
* Team/agent list if needed
* Office proof if policy
* Admin note

Agency verification badge belongs to agency entity.

Agent does not automatically become verified unless policy says agent is verified under agency.

---

# 14. AGENCY AGENT TRUST RULE

Agency Agent trust depends on:

* Linked agency
* Agency verification status
* Agent profile completeness
* Agent assigned permissions
* Agent phone verification
* Agency Owner approval

Agent should not show independent broker verified badge unless separately verified.

Public display can show:

```txt id="y2l7x0"
Agent under Verified Agency
```

only if agency is verified.

---

# 15. BUILDER VERIFICATION

Builder verification may collect:

* Builder company name
* Authorized person
* Company logo
* Office address
* Phone/email
* Company registration if applicable
* GST if applicable
* RERA/company credentials if applicable
* Website/social profile if real
* Project list
* Admin note

Builder verification badge belongs to builder company/entity.

---

# 16. PROJECT VERIFICATION

Project verification may collect:

* Project name
* Builder entity
* Project location
* RERA number if applicable
* RERA document/link if provided
* Approved plan if policy
* Brochure
* Site photos
* Possession timeline
* Admin verification checklist

Project verification must not claim RERA verified unless actual RERA verification process exists.

---

# 17. PROPERTY VERIFICATION

Property verification may collect:

* Property owner/entity
* Listing details
* Location validation
* Photos validation
* Ownership/authorization proof if policy
* Price sanity review if desired
* Duplicate check
* Contact verification
* Admin review

Verified property badge should mean admin/platform reviewed authenticity to defined standard.

If only listing is approved, label should be “Approved Listing”, not “Verified Property”.

---

# 18. RERA VERIFICATION RULE

RERA verification is sensitive.

If RERA verification is implemented:

* Store RERA number.
* Validate format if possible.
* Verify against official source/manual review.
* Store verification status.
* Store verified date.
* Show RERA badge only if verified.
* If only user-submitted, show “RERA number provided” not “RERA Verified”.

Do not show fake RERA verified.

---

# 19. VERIFICATION DOCUMENT STORAGE

Verification documents must be private.

Store in private bucket:

```txt id="ca9d3b"
verification-documents
property-private-documents
business-private-documents
```

Access:

* Uploading user
* Verification staff
* Admin/Super Admin with permission
* Not public
* Not indexed
* Not exposed in public URL

Use signed URLs only after permission check.

---

# 20. DOCUMENT UPLOAD RULE

Document upload must show:

* Purpose
* Accepted file types
* Max file size
* Privacy notice
* Upload progress
* Replace/remove
* Status
* Rejection reason if any

Accepted formats:

* PDF
* JPG
* JPEG
* PNG
* WEBP if needed

Do not allow unsafe files.

Do not place documents in public storage.

---

# 21. VERIFICATION REQUEST FLOW

User/business verification flow:

```txt id="tbmrxq"
Open Verification section
Select verification type
Fill required details
Upload documents
Submit
Status becomes Pending Review
Admin reviews
Admin approves/rejects/requests more details
User receives notification
Badge/status updates if approved
```

No instant verified badge unless verified by real automated process.

---

# 22. ADMIN VERIFICATION FLOW

Admin verification review:

```txt id="2169vk"
Open Verification Center
View pending request
Review user/entity/profile/listings/documents
Check risk flags/reports
Approve / Reject / Request More Details
Add note
Notify user
Audit log action
```

Admin review must be permission-based.

Verification Executive can review only permitted categories.

Super Admin can override if needed.

---

# 23. VERIFICATION REJECTION

If verification rejected:

User should see:

* Status: Rejected
* Reason
* What to fix
* Resubmit option if allowed
* Support link if needed

Admin can include internal note separately.

Rejected verification must not show badge.

---

# 24. NEED MORE DETAILS

If admin requests more details:

* Status becomes Need More Details.
* User can edit/upload additional documents.
* Original documents/history remain.
* User resubmits.
* Admin continues review.

Do not force user to restart entire verification if not needed.

---

# 25. VERIFICATION EXPIRY

Some verification can expire.

Examples:

* Business verification after 1 year if policy
* Document verification if document expired
* RERA/project status if changed
* Subscription-based public badge if policy

Expiry job should:

* Mark verification expired.
* Remove badge.
* Notify user.
* Allow re-verification.

Do not keep expired verification badge.

---

# 26. VERIFICATION SUSPENSION / REVOCATION

Admin can suspend/revoke verification if:

* Fraud found
* False documents
* User reports validated
* Business closed
* Role revoked
* Legal/policy issue

Suspended/revoked badge removed immediately.

Audit log required.

---

# 27. TRUST SCORE NOTE

Trust score is optional.

If implemented, it must be real and explainable.

Possible factors:

* Phone verified
* Email verified
* Business verified
* Property verified
* Low reports
* Listing quality
* Admin review
* Active history

If not implemented, do not show trust score.

Do not fake “98% trusted”.

---

# 28. RATINGS / REVIEWS NOTE

Ratings/reviews are optional and risky.

If implemented:

* Only real users can review.
* Prevent spam.
* Admin moderation.
* No fake reviews.
* Clear review policy.
* Show verified review only when real.

If not implemented, hide ratings.

Do not show fake 4.8 stars.

---

# 29. REPORT SYSTEM PURPOSE

Users must be able to report suspicious or wrong content.

Reportable entities:

* Property
* Project
* Broker profile
* Agency profile
* Builder profile
* Requirement
* Proposal
* Message
* Banner ad
* User profile
* Lead/contact abuse
* Site visit issue

Report system improves trust and moderation.

---

# 30. REPORT PROPERTY REASONS

Property report reasons:

* Fake listing
* Wrong price
* Wrong location
* Already sold/rented
* Duplicate listing
* Broker pretending owner
* Wrong photos
* Contact not working
* Spam listing
* Fraud/scam
* Offensive content
* Misleading title/details
* Wrong property type
* Brokerage not disclosed
* Other

---

# 31. BROKER PRETENDING OWNER RULE

This is a major trust issue.

If user reports:

```txt id="nr9nm8"
Broker pretending owner
```

Admin should review:

* Listing source tag
* User role
* Contact number
* Business profile
* Other listings by same user
* Reports history
* Listing description
* Documents if available

Admin actions:

* Change source tag if verified
* Request clarification
* Warn user
* Suspend listing
* Suspend user/entity
* Reject listing
* Require broker verification

Do not ignore this report.

---

# 32. REPORT PROJECT REASONS

Project report reasons:

* Fake project
* Wrong builder
* Wrong RERA
* Wrong location
* Misleading price
* Project not active
* Duplicate project
* Fake photos
* Contact issue
* Fraud/scam
* Offensive content
* Other

---

# 33. REPORT PROFILE REASONS

Profile report reasons:

* Fake profile
* Wrong identity
* Fake verified badge suspicion
* Broker pretending owner
* Spam user
* Fraud/scam
* Contact abuse
* Offensive content
* Misleading business claim
* Other

---

# 34. REPORT REQUIREMENT REASONS

Requirement report reasons:

* Fake requirement
* Spam
* Wrong category
* Unrealistic/fake budget
* Contact abuse
* Duplicate requirement
* Offensive content
* Fraud/scam
* Other

---

# 35. REPORT PROPOSAL REASONS

Proposal report reasons:

* Irrelevant proposal
* Spam proposal
* Fake property
* Wrong price
* Contact abuse
* Offensive message
* Fraud/scam
* Duplicate proposal
* Broker misrepresentation
* Other

---

# 36. REPORT BANNER AD REASONS

Banner ad report reasons:

* Misleading ad
* Fake offer
* Wrong city
* Broken link
* Offensive content
* Fraud/scam
* Fake project/builder claim
* Policy violation
* Other

---

# 37. REPORT FLOW

User report flow:

```txt id="w61qus"
Click Report
Select reason
Add optional note
Submit
System creates report
Admin/moderator reviews
Action taken
Reporter may be notified if policy allows
```

Guest reports:

* Allowed or login required based on admin setting.
* Spam-protected if guest allowed.

Report submission must be real.

Do not fake “report received”.

---

# 38. REPORT STATUS

Report statuses:

```txt id="1r7p2q"
Submitted
Under Review
Need More Info
Valid
Invalid
Action Taken
Rejected
Closed
Archived
```

Admin should update status.

Reporter may see basic status if policy.

Reported user/entity may be notified only if policy allows.

---

# 39. REPORT ADMIN REVIEW

Admin report review should show:

* Reported entity
* Report reason
* Reporter
* Report note
* Entity details
* Related reports
* Prior history
* Risk flags if real
* Admin notes
* Actions

Actions:

* Mark valid
* Mark invalid
* Request info
* Hide/suspend entity
* Warn user
* Verify/change source tag
* Archive listing
* Ban/suspend user if severe
* Close report

No fake action.

---

# 40. FRAUD PREVENTION PURPOSE

Fraud prevention should reduce:

* Fake listings
* Duplicate listings
* Wrong price bait
* Contact harvesting
* Broker pretending owner
* Fake builder/project
* Fake RERA
* Spam requirements
* Proposal spam
* Payment abuse
* Banner ad scam
* Message abuse

Start with rule-based checks.

AI/advanced checks can come later.

---

# 41. FRAUD FLAGS

Possible fraud flags:

* Duplicate phone across many owner listings
* Same photos used in multiple listings
* Many reports on same user
* Broker-like behavior under owner role
* Too many contact reveals
* Too many proposals
* Unrealistic price
* Repeated rejected listings
* Same property posted many times
* External scam links
* Suspicious payment callback
* Misleading banner text
* RERA mismatch if verified process exists

Fraud flags should be real.

If automated fraud scoring is not implemented, do not show fake risk score.

---

# 42. DUPLICATE LISTING CHECK

Duplicate detection can check:

* Same user + same location + same title
* Same phone + same property details
* Same images
* Same address/locality + similar price
* Same project/unit
* Same broker reposting same listing
* Same title/description copied

If duplicate suspected:

* Flag for admin.
* Show warning to user.
* Allow merge/archive.
* Avoid public duplicate spam.

Do not auto-delete without safe review unless policy.

---

# 43. IMAGE MISUSE CHECK

Image misuse is optional but useful.

Possible checks:

* Same image hash across many listings
* Low quality image
* Watermarked competitor image
* Stock image suspicion if AI/advanced implemented
* Wrong property image report

If not implemented, allow report/manual review.

Do not fake image verification.

---

# 44. CONTACT ABUSE CHECK

Protect users from contact abuse.

Checks:

* Too many contact reveals
* Too many lead submissions
* Duplicate contact requests
* Spam messages
* Repeated alternate number abuse
* Suspicious WhatsApp/call click pattern

Actions:

* Rate limit
* Warn user
* Require verification
* Temporarily block contact
* Admin review

Do not allow scraping of phone numbers.

---

# 45. REQUIREMENT/PROPOSAL SPAM CHECK

Checks:

* Too many requirements posted
* Duplicate requirements
* Irrelevant proposals
* Same proposal text repeated
* Too many proposals per day
* User reports proposal spam

Actions:

* Rate limit
* Proposal limit
* Admin review
* Suspend ability
* Require verified broker/agency plan

---

# 46. BANNER AD FRAUD CHECK

Banner ad review should check:

* Fake offer
* Misleading “guaranteed” claim
* Wrong project name
* Wrong builder
* Fake logo
* Offensive content
* Unsafe external link
* Wrong city targeting
* Payment not verified

Admin can pause/remove ad.

---

# 47. VERIFICATION AND PLAN RELATION

Verification can affect plan benefits.

Examples:

* Verified brokers may get higher trust display.
* Unverified business may have lower limits.
* Banner ads may require verified business.
* Requirement feed access may require verification.
* Lead unlock may require phone verified.
* Featured listing may require approved listing.

Rules must be configured by Admin/Super Admin.

Do not fake verification to unlock features.

---

# 48. PUBLIC TRUST DISPLAY

Public UI can show:

* Source tag
* Verified badge if real
* Listing updated date
* Brokerage info
* Report button
* Property status
* RERA number provided/verified distinction
* Profile link
* Business logo if uploaded
* Seller type

Public UI should not show:

* Private documents
* Admin notes
* Risk scores unless policy
* Internal fraud flags
* Reporter details
* Hidden contact

---

# 49. TRUST SAFETY COPY

Public safety text examples:

```txt id="6sozps"
Always verify property documents before making any payment.
```

```txt id="6swzzb"
My Gujarat Property does not collect property purchase token/payment.
```

```txt id="1261pt"
Report suspicious listings to help keep the platform safe.
```

This improves trust without making false guarantees.

---

# 50. PAYMENT SAFETY WARNING

Because real estate scams are serious, show safety warning where needed.

Examples:

* Property detail page
* Contact form
* Site visit booking
* Proposal acceptance
* Message thread

Warning:

```txt id="i6zxbq"
Do not pay property token or advance without verifying documents and meeting the genuine owner/seller. My Gujarat Property payments are only for platform services.
```

Do not imply platform guarantees property transaction.

---

# 51. REPORT BUTTON PLACEMENT

Report button should be available on:

* Property detail
* Project detail
* Business profile
* Requirement detail
* Proposal detail
* Message thread
* Banner ad menu
* Dashboard listing card
* Admin detail page

Report button should be visible but not intrusive.

Mobile report can be inside overflow menu.

---

# 52. ADMIN VERIFICATION CENTER ROUTES

Recommended routes:

```txt id="bvcop7"
/admin/verification
/admin/verification/users
/admin/verification/owners
/admin/verification/brokers
/admin/verification/agencies
/admin/verification/builders
/admin/verification/properties
/admin/verification/projects
/admin/verification/documents
/admin/verification/[id]
```

---

# 53. ADMIN REPORT CENTER ROUTES

Recommended routes:

```txt id="i9syyh"
/admin/reports
/admin/reports/properties
/admin/reports/projects
/admin/reports/profiles
/admin/reports/requirements
/admin/reports/proposals
/admin/reports/messages
/admin/reports/banner-ads
/admin/reports/[id]
```

---

# 54. FRAUD CENTER ROUTES

Recommended routes:

```txt id="bzb0ih"
/admin/fraud
/admin/fraud/flags
/admin/fraud/duplicates
/admin/fraud/contact-abuse
/admin/fraud/proposal-spam
/admin/fraud/suspicious-users
```

Only show if implemented.

---

# 55. DATABASE MODULES

Possible tables:

```txt id="qq8cqs"
verification_requests
verification_documents
verification_status_history
verification_notes
reports
report_status_history
fraud_flags
fraud_flag_history
moderation_actions
duplicate_candidates
blocked_entities
trust_badges
badge_history
```

Private document storage must be separate.

---

# 56. VERIFICATION REQUEST FIELDS

`verification_requests` may include:

* id
* requester_user_id
* entity_type
* entity_id
* verification_type
* status
* submitted_at
* reviewed_by
* reviewed_at
* rejection_reason
* user_visible_note
* internal_note
* expires_at
* created_at
* updated_at

---

# 57. REPORT FIELDS

`reports` may include:

* id
* reporter_user_id
* reporter_contact if guest allowed
* entity_type
* entity_id
* reason
* note
* status
* reviewed_by
* reviewed_at
* action_taken
* admin_note
* created_at
* updated_at

---

# 58. FRAUD FLAG FIELDS

`fraud_flags` may include:

* id
* entity_type
* entity_id
* flag_type
* severity
* source
* status
* evidence
* created_by_system
* reviewed_by
* reviewed_at
* resolved_at
* note

Severity:

```txt id="kdq3n5"
low
medium
high
critical
```

Do not show severity publicly unless policy.

---

# 59. STORAGE SECURITY

Verification documents go into private storage.

Report evidence attachments also private unless safe.

Storage rules:

* Public cannot access.
* Owner can access own submitted document if policy allows.
* Verification staff can access assigned documents.
* Admin/Super Admin can access with permission.
* Access should be logged if possible.

Do not make document URL public.

---

# 60. RLS / PERMISSION RULES

Verification RLS:

* User can view own verification request.
* User can create own request.
* User cannot approve own request.
* Verification staff/admin can view based on permission.
* Public cannot access documents.

Report RLS:

* User can create report.
* User may view own report status if policy.
* Admin/moderator can manage reports.
* Reported user cannot see reporter details unless policy.

Fraud flags:

* Admin only.
* No public access.

---

# 61. NOTIFICATIONS

Verification notifications:

* Verification submitted
* Need more details
* Verified
* Rejected
* Expired
* Suspended/revoked

Report notifications:

* Report received
* Report action taken if policy
* Listing removed if user owns it
* Warning/suspension notice

Admin notifications:

* New verification request
* New report
* High-risk fraud flag
* Duplicate listing alert

No fake external notification.

---

# 62. TRUST FEATURE FLAGS

Possible feature flags:

```txt id="5l5nwe"
verification.enabled
verification.owner.enabled
verification.broker.enabled
verification.agency.enabled
verification.builder.enabled
verification.property.enabled
verification.project.enabled
verification.rera.enabled
verification.documents.enabled

trust_badges.enabled
trust_score.enabled
ratings_reviews.enabled

reports.enabled
reports.guest_reports.enabled
reports.property.enabled
reports.profile.enabled
reports.requirement.enabled
reports.proposal.enabled
reports.banner_ad.enabled

fraud.enabled
fraud.duplicate_detection.enabled
fraud.contact_abuse.enabled
fraud.proposal_spam.enabled
fraud.image_duplicate.enabled
```

If feature flag off, hide UI and block backend action.

---

# 63. COMPONENTS

Recommended components:

* VerificationCenter
* VerificationStatusCard
* VerificationRequestForm
* DocumentUploaderPrivate
* VerificationReviewPanel
* VerificationBadge
* TrustSignalBar
* ReportButton
* ReportModal
* ReportReasonSelector
* AdminReportQueue
* ReportReviewPanel
* FraudFlagBadgeAdmin
* DuplicateCandidateList
* SafetyWarningCard
* BrokerageTransparencyBadge
* SourceTagBadge
* ReraStatusBadge
* TrustEmptyState
* TrustAuditPanel

Avoid duplicate random trust components.

---

# 64. EMPTY STATES

Verification empty:

```txt id="15wt2x"
No verification submitted yet.
```

Reports empty:

```txt id="9z20i3"
No reports found.
```

Fraud flags empty:

```txt id="3eqg73"
No fraud flags found.
```

Property report empty state in admin:

```txt id="5bo5iv"
No reports for this listing.
```

No fake issues.

---

# 65. ERROR STATES

Error examples:

```txt id="12xmkt"
Could not submit verification request.
```

```txt id="lnh0pl"
Could not upload document. Please try again.
```

```txt id="f9slqi"
Could not submit report.
```

```txt id="tps6n3"
You do not have permission to view this document.
```

Do not expose raw storage/database errors.

---

# 66. SUCCESS STATES

Success examples:

```txt id="361q9n"
Verification request submitted for review.
```

```txt id="t197az"
Report submitted. Thank you for helping keep the platform safe.
```

```txt id="vx3blc"
Verification approved.
```

```txt id="f3yjka"
Report closed.
```

Success only after server confirmation.

---

# 67. NO-FAKE TRUST RULE

Do not fake:

* Verified badges
* RERA verified
* Property verified
* Profile verified
* Trust score
* Ratings
* Reviews
* Report count
* Fraud score
* Duplicate detection
* Document approval
* Safety guarantee
* Admin review
* “Top broker”
* “Most trusted”
* “No. 1 agency”

If not implemented, hide.

If user submitted RERA but not verified, show:

```txt id="snc1kl"
RERA number provided
```

not:

```txt id="d29f78"
RERA Verified
```

---

# 68. MOBILE UX RULE

Mobile trust/report UI:

* Report button in overflow menu
* Bottom sheet report form
* Large reason buttons
* Document upload mobile-friendly
* Verification status cards
* Clear badge display
* No horizontal scroll
* Admin queues become cards

Mobile admin verification detail should open full screen.

---

# 69. AUDIT LOG RULE

Audit important actions:

* Verification submitted
* Verification approved
* Verification rejected
* Verification revoked
* Document reviewed
* Report submitted
* Report marked valid/invalid
* Listing removed due to report
* User warned/suspended
* Fraud flag created/resolved
* Badge granted/removed
* RERA verification updated

Audit logs must not expose private documents publicly.

---

# 70. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Verified badge does not appear for unverified user.
* Broker can submit verification.
* Agency can submit verification.
* Builder can submit verification.
* Owner can submit verification if enabled.
* Property verification request works if enabled.
* Documents upload to private storage.
* Public cannot open private document URL.
* Admin can approve verification.
* Rejected verification shows reason.
* Badge appears only after approval.
* Expired/revoked verification removes badge.
* Property detail shows source tag.
* Brokerage info appears.
* Report property works.
* Report reason “Broker pretending owner” exists.
* Report goes to admin queue.
* Admin can mark report valid/action taken.
* Fraud flags are admin-only.
* RERA provided vs RERA verified are different.
* No fake ratings/trust scores.
* Mobile report form has no horizontal scroll.
* No screenshot/video capture required.

---

# 71. PASS / FAIL RULE

Verification/Fraud/Trust phase is PASS only if:

* Source tag is clear.
* Verified badges are real only.
* Verification requests can be submitted/reviewed if feature enabled.
* Documents are private.
* Admin verification approval/rejection works.
* Report system works for properties/profiles/requirements/proposals/ads if enabled.
* Broker pretending owner report exists.
* Report queue works.
* Fraud flags are not public.
* RERA verified is not fake.
* Trust score/rating hidden unless real.
* Safety warning exists where needed.
* Feature registry updated.
* Manual verification completed.

If fake verified badge appears, mark FAIL.

If private verification documents are public, mark FAIL.

If reports submit but disappear/no admin queue, mark FAIL.

If broker can fake Direct Owner tag, mark FAIL.

---

# 72. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for role, property, contact, admin, storage, notification and manual QA details.

---

# 73. END OF FILE

This file defines verification, fraud prevention, trust, reporting and safety rules for My Gujarat Property.

Trust must be real, badges must be verified, reports must reach admin, private documents must remain private and fake claims must never appear in production.

Nothing from uploaded docs or user chat instructions should be skipped.
