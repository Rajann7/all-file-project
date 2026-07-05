# MY GUJARAT PROPERTY

# SUBSCRIPTION, TRIAL, BILLING, PAYMENT, CREDIT, BOOST & MONETIZATION SPEC

## FILE NAME

`15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete subscription, trial, billing, payment, credits, listing boost, featured listing, lead unlock, proposal limits, banner ad billing and monetization rules for **My Gujarat Property**.

This file must be read before building or redesigning:

* Pricing page
* Subscription plans
* Trial system
* Free launch offer
* First 100 users free listing offer
* Role-based plans
* Owner plans
* Broker plans
* Agency plans
* Builder plans
* Real Estate Group/Advertiser plans
* Banner ad packages
* Payment gateway integration
* Payment status handling
* Payment verification
* Billing dashboard
* Invoices/receipts
* Credits
* Proration/upgrade logic
* Role-change subscription impact
* Boost listing
* Featured listing
* Paid lead unlock
* Proposal limits
* Requirement feed limits
* Listing limits
* Image limits
* Project/unit limits
* Agent limits
* Expiry/renewal
* Admin manual payment/subscription controls
* No-fake payment or plan activation

The goal is to monetize the platform without breaking trust or showing fake paid features.

---

# 2. CORE MONETIZATION PRINCIPLE

My Gujarat Property monetization must be role-based and transparent.

The platform can earn from:

* Property listing plans
* Broker plans
* Agency plans
* Builder/project plans
* Banner ads
* Featured listings
* Boosted listings
* Lead unlock credits
* Proposal credits
* Requirement feed access
* Project promotion
* City advertising
* Premium verification if business decides
* Add-on services if implemented

The platform must not take property transaction money unless a future legal/regulated workflow is created.

Current rule:

```txt id="klq19u"
Platform payments are for listing, subscription, ads, boost, promotion, credits and platform services — not for buying/selling property transaction payment.
```

---

# 3. NO-FAKE PAYMENT RULE

Payment and subscription must be real.

Do not fake:

* Payment success
* Active subscription
* Trial status
* Plan usage
* Listing limit
* Credit balance
* Lead unlock
* Featured status
* Boost status
* Banner ad payment
* Invoice
* Refund
* Revenue
* Payment gateway response

A plan becomes active only when:

1. Payment is verified, or
2. Trial/launch offer is valid, or
3. Admin manually activates with audit log, or
4. Plan is free/default and truly configured.

No fake activation.

---

# 4. ROLE-BASED PLAN PRINCIPLE

Plans must be connected to roles.

A user can have different plans for different roles.

Example:

```txt id="pyzyid"
Owner Role: Free Listing Plan
Broker Role: No Active Plan
Agency Role: Premium Agency Plan
Builder Role: Project Plan
```

Do not show one generic subscription for all roles if role-specific benefits differ.

Role-specific plan logic is required for:

* Owner
* Broker
* Agency
* Builder
* Real Estate Group / Advertiser
* Developer if implemented

Buyer/Tenant may be free by default unless premium buyer features are added later.

---

# 5. PLAN TYPES

Possible plan types:

* Free Plan
* Trial Plan
* Monthly Plan
* Quarterly Plan
* Yearly Plan
* Listing Package
* Lead Credit Package
* Proposal Credit Package
* Boost Package
* Featured Listing Package
* Banner Ad Package
* Project Package
* Agent Add-on
* Manual/Admin Plan
* Launch Offer Plan

Each plan must define real limits and benefits.

---

# 6. PUBLIC PRICING PAGE RULE

Pricing page should be visible to guests and logged-in users.

Guests can view pricing.

Purchase requires login/register.

Pricing page should show:

* Role tabs
* Plan name
* Price
* Billing period
* Features
* Limits
* Expiry/duration
* CTA
* Terms
* GST/tax note if applicable
* Refund/cancellation note if applicable
* Role eligibility

Example tabs:

* Owner
* Broker
* Agency
* Builder
* Advertise / Banner Ads

Do not show plans that are not active.

---

# 7. PRICING PURCHASE FLOW

Guest purchase flow:

```txt id="fs8hs6"
Open Pricing
Select plan
Click Buy
Login/Register popup opens
Role check happens
If role matches, continue payment
If role missing, request/select role
Payment
Payment verification
Subscription active
Redirect to dashboard
```

Logged-in flow:

```txt id="iw7n3y"
Select plan
Check active role
Check eligibility
Create order
Pay
Verify payment
Activate plan
Show success
```

If payment fails:

* Keep subscription inactive.
* Show retry.
* Do not activate plan.

---

# 8. OWNER PLAN SPEC

Owner plans are for individual property owners.

Possible benefits:

* Number of active listings
* Listing duration
* Image upload limit
* Contact leads
* Featured listing if included
* Boost credits if included
* Renewal discounts if enabled
* Direct Owner tag
* Basic support

Example owner plan fields:

* Plan name
* Price
* Active listing limit
* Draft limit
* Images per listing
* Listing validity days
* Lead limit if applicable
* Boost included yes/no
* Featured included yes/no
* Approval required yes/no
* Renewal allowed yes/no

Owner plans should be simple.

Owner users should not see complex broker/agency features.

---

# 9. BROKER PLAN SPEC

Broker plans are for real estate brokers.

Possible benefits:

* Active listing limit
* Images per listing
* Requirement feed access
* Requirement view limit
* Proposal send limit
* Lead unlock limit
* Contact reveal limit
* Site visit management
* Boost credits
* Featured listings
* Broker profile visibility
* Verification badge if approved
* Analytics if real
* Support priority if enabled

Broker plan fields:

* Active listings
* Monthly proposals
* Monthly requirement views
* Lead unlocks
* Featured listings
* Boost credits
* Listing validity
* Images per listing
* City access
* Verification requirement
* Banner ads allowed yes/no

Do not show unlimited if system cannot enforce.

---

# 10. AGENCY PLAN SPEC

Agency plans are for real estate agencies.

Possible benefits:

* Agency profile
* Active listings
* Agents/team seats
* Lead assignment
* Requirement feed access
* Proposal limits
* Lead unlocks
* City access
* Featured listings
* Boost credits
* Banner ad eligibility
* Banner ad credits if included
* Analytics if real
* Priority support if enabled

Agency plan fields:

* Active listings
* Agent seats
* Lead assignment enabled
* Requirement feed access
* Proposal limit
* Lead unlock limit
* Banner ad access
* Banner ad credit/days if included
* Images per listing
* Listing validity
* City targeting
* Analytics enabled
* Verification required

Agency plan should be more advanced than broker plan.

---

# 11. AGENCY AGENT PLAN CONNECTION

Agency Agent usually does not buy plan separately.

Agent access comes from agency plan and agency permissions.

Agent seat logic:

* Agency plan includes X agents.
* Agency Owner can add agents up to limit.
* Extra agents require add-on if enabled.
* Agent cannot purchase agency subscription unless made owner/admin.

Do not show agency billing to normal agent unless permission.

---

# 12. BUILDER PLAN SPEC

Builder plans are for builders/developers/projects.

Possible benefits:

* Builder profile
* Project listing limit
* Unit/configuration limit
* Project image limit
* Brochure upload
* Project lead management
* Site visit management
* Banner ad eligibility
* Project boost
* Featured project
* RERA/project verification if approved
* Analytics if real

Builder plan fields:

* Active projects
* Units per project
* Images per project
* Brochures
* Project validity
* Lead unlocks
* Banner ad access
* Featured project credits
* Boost credits
* City access
* Verification requirement
* Support level

Do not fake RERA/verification.

---

# 13. REAL ESTATE GROUP / ADVERTISER PLAN SPEC

Real Estate Group or Advertiser plans focus on promotion.

Possible benefits:

* Banner ad access
* City targeting
* Gujarat-wide package
* Campaign duration
* Device image variants
* Click/impression analytics if real
* Agency/group profile
* Sponsored label
* Renewal
* Priority placement if paid

If Real Estate Group role is not separate, this plan can be under Agency/Builder advertiser package.

---

# 14. BUYER / TENANT PLAN SPEC

Buyer/Tenant should be free by default.

Possible future premium features:

* More saved searches
* Priority requirement visibility
* Verified buyer badge
* More proposal visibility
* Premium alerts

Do not monetize basic buyer/tenant browsing too early unless business decides.

Buyer/Tenant must be able to browse public listings.

---

# 15. FREE PLAN RULE

Free plan can include limited usage.

Examples:

Owner free plan:

* 1 active listing
* 3 images
* 30 days validity

Broker free plan:

* 1-3 listings
* Limited requirement views
* Limited proposals

Agency free plan:

* Trial profile only
* Limited listing
* No agents or limited agents

Builder free plan:

* 1 project draft or limited visibility

Free plan limits must be enforced.

No fake free usage.

---

# 16. TRIAL PLAN RULE

Trial plans allow users to test paid features.

Trial fields:

* Trial duration
* Eligible role
* One-time per user/entity
* Feature limits
* Start date
* End date
* Auto-expiry
* Payment required after trial
* Trial abuse prevention

Trial can be:

* Auto-start on registration
* Admin granted
* User activated
* Plan-specific

Do not allow endless trial reset.

---

# 17. FIRST 100 USERS FREE LISTING OFFER

Launch offer requirement:

```txt id="rawr3j"
First 100 users get free property listing service at launch.
```

System should support this as a configurable offer.

Settings:

* Offer enabled/disabled
* Eligible roles
* Eligible action: free listing
* Maximum users: 100
* Listing limit per user
* Validity days
* Start date
* End date
* Current claimed count
* Remaining count
* Auto-disable when 100 reached
* Admin manual override
* Abuse prevention
* Public display enabled/disabled

Counts must be real.

Do not show fake “only X left” unless count is real.

---

# 18. LAUNCH OFFER ELIGIBILITY

Eligibility can be based on:

* First 100 registered eligible users
* First 100 users who post property
* First 100 paid/verified users
* First 100 owners/brokers/builders
* Admin-configured rule

Recommended:

```txt id="lasqll"
First 100 eligible users who submit approved listing get free listing benefit.
```

This prevents fake accounts claiming benefit without posting.

Admin must choose rule.

---

# 19. LISTING LIMITS

Plans should control listing limits.

Limit types:

* Active listing limit
* Draft listing limit
* Monthly new listing limit
* Total listing limit
* Project limit
* Unit limit
* Image limit per listing
* Featured listing limit
* Boost limit

When limit reached:

* Show upgrade CTA.
* Allow save draft if policy.
* Block active publish.
* Do not silently delete listings.

---

# 20. IMAGE LIMITS

Plan can control image upload count.

Examples:

* Free owner: 3 images/listing
* Paid owner: 10 images/listing
* Broker: 15 images/listing
* Agency: 20 images/listing
* Builder: 30 project images

UI should show:

```txt id="5k5q0l"
3 of 10 images uploaded
```

Do not show fake usage.

---

# 21. REQUIREMENT FEED LIMITS

Broker/Agency/Builder plans can control requirement access.

Possible limits:

* Requirement feed enabled/disabled
* Requirement views per month
* Contact unlocks
* Proposal sends
* City access
* Requirement type access
* New requirement alerts

If limit reached:

* Show upgrade/credit purchase.
* Do not reveal hidden buyer contact.

---

# 22. PROPOSAL LIMITS

Plans can control proposals.

Fields:

* Monthly proposal limit
* Daily proposal limit
* Proposal credit package
* Proposal per requirement cooldown
* Duplicate proposal prevention
* Proposal attachment allowed
* Proposal priority if paid

Do not allow unlimited spam if limits enabled.

---

# 23. LEAD UNLOCK / LEAD CREDIT SYSTEM

Lead unlock can be credit-based.

Credit use cases:

* Reveal lead contact
* Unlock requirement contact
* Unlock premium buyer requirement
* Send priority proposal
* Contact hidden lead if allowed

Lead credits should store:

* Credit balance
* Credits purchased
* Credits used
* Expiry date if any
* Usage history
* Source plan/package/payment
* Entity/user role

Do not deduct credit without successful action.

Do not reveal contact without deducting if required.

---

# 24. CREDIT TYPES

Possible credits:

* Lead credits
* Proposal credits
* Boost credits
* Featured listing credits
* Banner ad credits
* Project promotion credits

Each credit must have:

* Type
* Balance
* Expiry
* Usage rules
* Role/entity owner
* Purchase source
* Audit/usage logs

Do not mix credits incorrectly.

---

# 25. BOOST LISTING SYSTEM

Boost makes a listing more visible for a defined time.

Boost can affect:

* Search ranking
* Homepage section
* City page section
* “Boosted” label if shown
* Related recommendations

Boost must be paid/credit-based/plan-based.

Boost fields:

* Listing ID
* User/entity
* Boost package
* Start date
* End date
* Status
* Payment/credit source
* Placement/ranking rule
* City scope
* Audit history

Do not show boosted status after expiry.

---

# 26. FEATURED LISTING SYSTEM

Featured listing is a premium placement.

Featured listing may appear:

* Homepage featured section
* Search result top section
* City page featured section
* Property card with Featured label

Featured rules:

* Active listing only
* Approved listing only
* Paid/credit/plan eligible
* Start/end date
* Auto-expire
* Clear Featured label
* Do not override too many organic results

Featured status must be real.

---

# 27. BOOST VS FEATURED DIFFERENCE

Boost:

* Improves visibility/ranking
* May be less prominent
* Time-limited
* Often credit-based

Featured:

* Dedicated placement or label
* More prominent
* Time-limited
* Often paid package

Do not confuse boost and featured.

---

# 28. BANNER ADS BILLING

Banner ads can be:

* Separate package
* Plan included benefit
* Credit-based
* Manual admin campaign
* Renewal package

Banner ad payment must connect to:

* Campaign
* Package
* Placement
* Target city
* Duration
* Approval status
* Active status

Do not display unpaid banner ads unless admin manually marks as internal/house campaign.

---

# 29. PAYMENT GATEWAY RULE

Payment should be handled by configured provider.

Payment flow:

```txt id="622r9b"
Create order
Redirect/open checkout
User pays
Provider confirms
Webhook/server verifies
Payment record updates
Subscription/credit/ad activates
Invoice/receipt generated if implemented
```

Do not rely only on client-side success.

Server-side verification required.

---

# 30. PAYMENT STATUS RULE

Payment statuses:

```txt id="lft7jx"
Created
Pending
Processing
Success
Failed
Cancelled
Expired
Refunded
Partially Refunded
Disputed
Manually Verified
```

Subscription activation allowed only when status is:

* Success
* Manually Verified by permitted admin
* Not Required for free/trial offer

Failed/cancelled payment must not activate plan.

---

# 31. PAYMENT WEBHOOK RULE

Payment provider webhook should:

* Verify signature/secret
* Match order/payment ID
* Update payment safely
* Prevent duplicate activation
* Record event
* Activate subscription/credit/ad only once
* Handle failed/refunded events
* Log errors safely

No fake webhook success.

---

# 32. MANUAL PAYMENT VERIFICATION

Admin/Super Admin may manually verify payment if business allows.

Manual verification must require:

* Permission
* Reason/note
* Payment reference
* Amount check
* User/entity
* Plan/package
* Audit log

Manual verification should be visible in payment record.

Do not allow normal admin to fake payments without permission.

---

# 33. INVOICE / RECEIPT SYSTEM

Invoice/receipt is optional but recommended.

Invoice fields:

* Invoice number
* User/entity
* Plan/package
* Amount
* Tax/GST if configured
* Discount if any
* Payment ID
* Date
* Billing period
* Status

If GST/tax not configured, do not generate fake GST invoice.

Use receipt instead if invoice system not ready.

---

# 34. TAX / GST RULE

If GST/tax is implemented:

* Admin/Super Admin configures tax rate.
* Tax shown on checkout.
* Invoice includes tax.
* Business GSTIN shown only if real.
* User GSTIN optional if B2B invoice supported.
* Tax calculations must be accurate.

If GST not configured:

* Show price inclusive/exclusive clearly.
* Do not show fake tax invoice.

---

# 35. DISCOUNT / COUPON SYSTEM

Discount/coupon is optional.

If implemented:

* Coupon code
* Discount type
* Discount value
* Eligible plans
* Eligible roles
* Start/end date
* Usage limit
* Per-user limit
* Active/inactive
* Minimum amount
* Audit log

Do not show coupon field if coupon system not implemented.

---

# 36. REFUND SYSTEM

Refund is optional.

If implemented:

* Refund request
* Admin review
* Provider refund
* Refund status
* Partial/full refund
* Reason
* Audit log
* Subscription impact

Refund statuses:

* Requested
* Approved
* Rejected
* Processing
* Refunded
* Failed

If not implemented, show policy clearly.

Do not fake refund.

---

# 37. RENEWAL RULE

Subscriptions/listings/ads can be renewed.

Renewal flow:

* User sees expiry warning.
* User clicks renew.
* Select plan/package.
* Pay.
* Verify payment.
* Extend subscription/listing/ad.
* Show success.

If payment fails:

* Do not renew.
* Keep previous expiry.

Auto-renewal is optional.

If auto-renewal not implemented, do not show auto-renew.

---

# 38. EXPIRY RULE

Plans/features expire.

After expiry:

* Listing may hide/expire based on settings.
* Requirement feed access stops.
* Proposal sending stops.
* Credits may expire if configured.
* Banner ad stops.
* Featured/boost stops.
* Agent seats may be disabled/limited.
* User sees renewal CTA.

Do not keep expired paid benefits active unless grace period is configured.

---

# 39. GRACE PERIOD RULE

Grace period is optional.

If enabled:

* Define days
* Define features allowed during grace
* Notify user
* Auto-disable after grace
* Admin can override

Example:

```txt id="nzr1ij"
Plan expired. You have 3 days grace period to renew.
```

Do not silently allow unlimited grace.

---

# 40. UPGRADE RULE

Upgrade can be immediate.

Upgrade options:

* Pay full new plan
* Apply unused credit/proration
* Start new plan immediately
* Replace old plan
* Add to existing plan
* Admin-controlled upgrade

Recommended safe initial rule:

```txt id="yns950"
Upgrade starts new plan after payment and replaces/extends features according to defined plan rules.
```

If proration not implemented, do not show proration.

---

# 41. DOWNGRADE RULE

Downgrade can happen:

* At next renewal
* After current plan expiry
* Immediately with feature reduction if user agrees
* Admin-managed

Recommended safe rule:

```txt id="4b3tjq"
Downgrade applies after current paid plan expiry.
```

This avoids losing paid benefits unexpectedly.

---

# 42. PRORATION / CREDIT RULE

Proration is optional and complex.

If implemented:

* Calculate unused days/value
* Convert to credit
* Apply to upgrade
* Store credit transaction
* Show clear calculation
* Audit log
* Admin override if permitted

If not implemented:

* Show no-proration policy.
* Keep current plan until expiry.
* User can buy new plan separately.

Do not fake credit calculation.

---

# 43. ROLE CHANGE SUBSCRIPTION RULE

Role change affects subscriptions.

Recommended default:

```txt id="wepk1o"
Existing active plan remains linked to original role until expiry. New role features require compatible plan, upgrade purchase or admin-approved migration.
```

Examples:

Owner → Broker:

* Owner plan remains for owner listings.
* Broker role needs broker plan.

Broker → Agency:

* Broker plan remains until expiry.
* Agency features require agency plan or admin migration.

Agency → Builder:

* Agency plan remains linked to agency entity.
* Builder plan required for builder projects.

No silent plan transfer.

---

# 44. PLAN COMPATIBILITY RULE

Some plans can be compatible if configured.

Examples:

* Agency plan includes Broker features.
* Builder premium plan includes project banner ad credit.
* Real Estate Group plan includes banner ad package.

Compatibility must be explicitly configured by Super Admin.

Do not assume compatibility.

---

# 45. SUBSCRIPTION USAGE TRACKING

Usage must be tracked.

Usage examples:

* Active listings used
* Draft listings used
* Images used
* Requirement views used
* Proposals sent
* Lead credits used
* Boost credits used
* Banner ad credits used
* Agent seats used
* Projects used
* Units used

Usage should reset according to plan period if applicable.

Do not show fake usage.

---

# 46. USAGE RESET RULE

Usage reset can be:

* Monthly
* Per billing cycle
* Never until expiry
* Credit balance based
* Per package

Example:

Broker monthly proposal limit resets every billing month.

Lead credits may not reset until used/expired.

Plan must define reset rule.

---

# 47. PLAN LIMIT ENFORCEMENT

Plan limits must be enforced server-side.

Before action:

* Check active role
* Check active plan
* Check usage
* Check limit
* Check expiry
* Check feature flag
* Check account status

Actions requiring checks:

* Post listing
* Upload more images
* Publish listing
* View requirement
* Send proposal
* Unlock lead
* Create banner ad
* Add agent
* Add project
* Add unit
* Boost listing
* Feature listing

UI-only checks are not enough.

---

# 48. BILLING DASHBOARD

User billing dashboard should show:

* Current plan
* Plan status
* Start date
* Expiry date
* Usage
* Payment history
* Invoices/receipts if implemented
* Credit balance
* Renew/upgrade buttons
* Active add-ons
* Banner ad packages
* Boost/featured packages
* Trial status
* Free offer status if applicable

Role-specific billing view required.

Agency owner sees agency billing.

Agent should not see billing unless permitted.

---

# 49. ADMIN BILLING MANAGEMENT

Admin/Super Admin can view/manage:

* Payments
* Subscriptions
* Plans
* Usage
* Credits
* Trials
* Launch offers
* Refunds
* Manual activation
* Manual expiry
* Payment failures
* Invoices/receipts

Actions require permission and audit log.

Do not expose billing to unauthorized staff.

---

# 50. PAYMENT FAILURE HANDLING

If payment fails:

* Show failure message.
* Keep plan inactive.
* Allow retry.
* Store failed payment record.
* Do not create active subscription.
* Do not activate banner ad.
* Do not add credits.

If payment status unknown:

* Show pending.
* Poll/verify.
* Do not activate until verified.

---

# 51. PAYMENT SUCCESS HANDLING

After verified success:

* Create subscription/credit/ad entitlement.
* Set start/end date.
* Update usage.
* Show success page.
* Send notification if provider configured.
* Generate receipt/invoice if implemented.
* Redirect to relevant dashboard/action.

Success page should show:

* Plan/package
* Amount
* Duration
* Next steps
* Dashboard link

---

# 52. PAYMENT CALLBACK PAGE

Payment callback page should:

* Verify payment server-side.
* Show loading.
* Show success/failure.
* Avoid exposing provider secrets.
* Handle duplicate callback.
* Handle retry.
* Redirect safely.

Callback page should be noindex.

---

# 53. SUBSCRIPTION STATUS

Subscription statuses:

```txt id="c7me7w"
Trial
Active
Paused
Expired
Cancelled
Pending Payment
Payment Failed
Grace Period
Manually Activated
Refunded
Suspended
Archived
```

Status must be real.

---

# 54. CREDIT TRANSACTION LOG

Credit transaction types:

* Purchased
* Granted by plan
* Granted manually
* Used
* Expired
* Refunded
* Reversed
* Adjusted

Each transaction:

* User/entity
* Credit type
* Amount
* Balance before
* Balance after
* Source
* Related entity
* Admin note if manual
* Timestamp

No fake credit balance.

---

# 55. BOOST / FEATURED STATUS

Boost/featured statuses:

```txt id="rg0wgk"
Draft
Payment Pending
Active
Scheduled
Expired
Cancelled
Failed
Archived
```

Boost/featured public display only if:

* Listing active
* Payment/credit valid
* Status active
* Date within start/end
* Admin approval if required

---

# 56. MONETIZATION AND SEO

Pricing page should be indexable.

Payment pages/callbacks should be noindex.

Subscription dashboard should be private/noindex.

Plan metadata should not make fake claims.

Do not create thin SEO pages for every package unless useful.

---

# 57. MONETIZATION AND NOTIFICATIONS

Notifications:

* Trial started
* Trial ending soon
* Trial expired
* Payment success
* Payment failed
* Subscription active
* Subscription expiring
* Subscription expired
* Plan upgraded
* Credits added
* Credits low
* Lead unlocked
* Boost started
* Boost expired
* Featured listing started
* Banner ad payment pending
* Banner ad active
* Renewal reminder

Channels:

* In-app
* Email if configured
* WhatsApp if configured
* SMS if configured

No fake external notifications.

---

# 58. MONETIZATION AND DASHBOARD

Dashboard should show monetization data per role.

Owner:

* Listing usage
* Expiry
* Upgrade CTA

Broker:

* Listings
* Requirement views
* Proposals
* Lead credits

Agency:

* Listings
* Agents
* Leads
* Banner ads
* Credits

Builder:

* Projects
* Units
* Leads
* Banner ads

Advertiser:

* Banner ads
* Campaign status
* Payments

---

# 59. MONETIZATION DATA PRIVACY

Payment/subscription data is private.

Users see their own billing only.

Agency owner sees agency billing.

Agent does not see agency billing unless permission.

Admin sees based on permission.

Payment provider secrets are never exposed.

Public pages do not expose private payment data.

---

# 60. MONETIZATION DATABASE MODULES

Possible tables:

* plans
* plan_features
* subscriptions
* subscription_usage
* payments
* payment_events
* invoices
* credits
* credit_transactions
* trials
* launch_offers
* coupons
* refunds
* boosts
* featured_listings
* banner_ad_packages
* user_entitlements
* manual_adjustments
* billing_audit_logs

Detailed schema belongs to database document.

---

# 61. PAYMENT PROVIDER SETTINGS

Possible environment/settings:

```txt id="o00dfw"
PAYMENT_PROVIDER=
PAYMENT_KEY_ID=
PAYMENT_KEY_SECRET=
PAYMENT_WEBHOOK_SECRET=
PAYMENT_MODE=test/live
DEFAULT_CURRENCY=INR
TAX_ENABLED=true/false
GST_RATE=
```

Secrets must stay server-side.

Do not expose payment secret keys to client.

---

# 62. MONETIZATION PERMISSIONS

Permission examples:

```txt id="dvjfco"
pricing.view
subscription.purchase
subscription.view.own
subscription.manage.own
subscription.manage.all
payment.create
payment.verify
payment.view.own
payment.view.all
payment.manual_verify
credit.purchase
credit.use
credit.manage
plan.manage
trial.manage
launch_offer.manage
boost.create
boost.manage.own
boost.manage.all
featured.create
featured.manage.own
featured.manage.all
refund.request
refund.manage
invoice.view.own
invoice.view.all
```

Permissions must be server-side.

---

# 63. MONETIZATION FEATURE FLAGS

Possible feature flags:

```txt id="bjo392"
pricing.enabled
payments.enabled
subscriptions.enabled
trials.enabled
free_launch_offer.enabled
credits.enabled
lead_unlock.enabled
proposal_credits.enabled
boost.enabled
featured_listings.enabled
banner_ad_packages.enabled
coupons.enabled
refunds.enabled
invoices.enabled
gst.enabled
manual_payment_verification.enabled
auto_renewal.enabled
grace_period.enabled
proration.enabled
```

If feature flag off, hide UI and block backend action.

---

# 64. MONETIZATION COMPONENTS

Recommended components:

* PricingPage
* RolePlanTabs
* PlanCard
* PlanFeatureList
* PlanComparisonTable
* CheckoutButton
* CheckoutSummary
* PaymentStatusPage
* PaymentCallbackHandler
* SubscriptionStatusCard
* UsageMeter
* CreditBalanceCard
* CreditTransactionList
* BillingHistoryTable
* InvoiceDownloadButton
* TrialStatusCard
* LaunchOfferBanner
* UpgradeModal
* RenewModal
* BoostListingModal
* FeaturedListingModal
* LeadUnlockModal
* AdminPlanManager
* AdminPaymentManager
* AdminSubscriptionManager
* AdminCreditManager
* AdminLaunchOfferManager

Avoid duplicate random billing components.

---

# 65. MONETIZATION LOADING STATES

Loading states:

* Loading pricing
* Creating order
* Opening checkout
* Verifying payment
* Activating plan
* Loading subscription
* Loading usage
* Loading credits
* Applying coupon
* Renewing
* Boosting listing
* Unlocking lead

Show clear progress.

Do not leave user confused after payment.

---

# 66. MONETIZATION EMPTY STATES

Examples:

No active plan:

```txt id="70hj9t"
You do not have an active plan. Choose a plan to start.
```

No payment history:

```txt id="tqnngl"
No payment history found.
```

No credits:

```txt id="815kky"
You do not have any lead credits.
```

No active boost:

```txt id="c954yi"
No active boosts.
```

No fake records.

---

# 67. MONETIZATION ERROR STATES

Error examples:

Payment failed:

```txt id="pedljc"
Payment failed. Your plan was not activated.
```

Verification pending:

```txt id="djnc1r"
Payment verification is pending. Please wait or contact support.
```

Limit reached:

```txt id="s09jwi"
You have reached your listing limit. Upgrade your plan to post more properties.
```

Credits exhausted:

```txt id="7169rq"
You do not have enough lead credits.
```

Provider missing:

```txt id="k60lb4"
Payment provider is not configured. Please contact support.
```

Do not expose raw provider errors.

---

# 68. MONETIZATION SUCCESS STATES

Success examples:

```txt id="ylqkk5"
Payment successful. Your plan is active.
```

```txt id="hn75uf"
Lead credits added.
```

```txt id="r5jv53"
Listing boost is now active.
```

```txt id="yp53lq"
Your subscription has been renewed.
```

Success only after server confirmation.

---

# 69. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Pricing page visible to guest.
* Guest purchase opens login/register.
* Logged-in user can select role-specific plan.
* Wrong role shows role/plan mismatch.
* Payment pending does not activate plan.
* Failed payment does not activate plan.
* Verified success activates plan.
* Plan usage appears real.
* Listing limit blocks publishing when reached.
* Image limit blocks upload when reached.
* Requirement/proposal limits work if enabled.
* Lead credits deduct on real unlock only.
* Credit balance updates.
* Boost starts only after payment/credit.
* Featured listing expires correctly.
* Banner ad payment affects ad activation.
* First 100 free launch offer count is real.
* Trial starts/expires correctly if enabled.
* Role change subscription impact is clear.
* Admin manual activation requires audit note.
* Agent cannot see agency billing unless permitted.
* Mobile pricing/billing has no horizontal scroll.
* No fake payment/subscription/credit shown.
* No screenshot/video capture required.

---

# 70. PASS / FAIL RULE

Monetization phase is PASS only if:

* Pricing is role-based.
* Guest can view pricing.
* Purchase requires login.
* Payment success is verified server-side.
* Failed/pending payment does not activate plan.
* Subscription usage is real.
* Plan limits are enforced server-side.
* Credits are real and tracked.
* Boost/featured status is real and expires.
* Banner ad payment is respected.
* Free launch offer is real and capped.
* Role change plan impact is handled.
* Admin manual changes are audit logged.
* No fake payment/plan/credit/revenue appears.
* Feature registry updated.
* Manual verification completed.

If fake payment activates plan, mark FAIL.

If plan limits only exist in UI and backend allows abuse, mark FAIL.

If expired plan still provides paid benefits without configured grace period, mark FAIL.

---

# 71. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for auth, roles, posting, leads, banner ads, providers, database and QA details.

---

# 72. END OF FILE

This file defines subscription, trial, billing, payment, credits, boost, featured listing and monetization rules for My Gujarat Property.

Monetization must be role-based, payment-verified, limit-enforced, no-fake, transparent, auditable and connected to property listing, requirement, lead, proposal, banner ad and dashboard workflows.

Nothing from uploaded docs or user chat instructions should be skipped.
