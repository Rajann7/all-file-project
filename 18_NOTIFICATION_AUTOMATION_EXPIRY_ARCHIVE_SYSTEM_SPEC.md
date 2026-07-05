# MY GUJARAT PROPERTY

# NOTIFICATION, AUTOMATION, EXPIRY, RENEWAL & ARCHIVE SYSTEM SPEC

## FILE NAME

`18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete notification, automation, reminder, expiry, renewal, auto-hide and archive system for **My Gujarat Property**.

This file must be read before building or redesigning:

* In-app notifications
* Email notifications
* WhatsApp notifications
* SMS notifications
* Push notifications if implemented
* Notification preferences
* Notification templates
* Notification delivery logs
* Scheduled jobs
* Cron jobs
* Listing expiry
* Requirement expiry
* Subscription expiry
* Banner ad expiry
* Trial expiry
* Boost expiry
* Featured listing expiry
* Project expiry
* Draft reminders
* Follow-up reminders
* Site visit reminders
* Auto-hide expired items
* Archive system
* Renewal flow
* No-fake notification delivery

The goal is to make the platform automatically manage expiring content, alert users at the right time and keep public data clean.

---

# 2. CORE AUTOMATION PRINCIPLE

Automation must be real and reliable.

If the system says:

```txt id="kx3naa"
Your listing will expire tomorrow.
```

then the listing must have a real expiry date.

If the system says:

```txt id="q15cp3"
WhatsApp sent.
```

then WhatsApp must actually be sent by configured provider.

If provider is missing, show only in-app notification or safe unavailable state.

No fake delivery.

No fake scheduled jobs.

No fake reminders.

---

# 3. NOTIFICATION TYPES

The platform may support these notification channels:

* In-app notification
* Email
* WhatsApp
* SMS
* Push notification if implemented
* Dashboard alerts
* Admin alerts

In-app notification should be the default.

External channels depend on provider configuration and user preferences.

---

# 4. NOTIFICATION CHANNEL RULE

Each channel must follow provider status.

## In-app

* Can work without external provider.
* Stored in database.
* Visible inside dashboard/header.

## Email

* Requires email provider.
* If provider missing, do not mark as sent.

## WhatsApp

* Requires WhatsApp free/API mode depending use case.
* Free wa.me is user-click based and cannot be used as automatic send.
* API mode required for automatic WhatsApp notifications.

## SMS

* Requires SMS provider.
* If missing, do not mark as sent.

## Push

* Requires push setup and user opt-in.
* If not implemented, hide.

---

# 5. NOTIFICATION EVENTS

Notification events may include:

## Auth/Profile

* Registration completed
* OTP sent if logged
* Email verification sent
* Email verified
* Profile incomplete reminder
* Role change request submitted
* Role approved
* Role rejected
* Verification submitted
* Verification approved/rejected

## Property

* Property draft saved
* Property submitted
* Property approved
* Property rejected
* Property needs changes
* Property expiring soon
* Property expired
* Property archived
* Property renewed
* Property marked sold/rented
* New lead received
* New site visit request

## Requirement

* Requirement submitted
* Requirement approved
* Requirement rejected
* Requirement expiring soon
* Requirement expired
* Requirement renewed
* New proposal received
* Proposal shortlisted/rejected
* Contact shared

## Proposal/Lead/Site Visit

* Proposal sent
* Proposal received
* Lead received
* Lead assigned
* Lead status updated
* Site visit requested
* Site visit confirmed
* Site visit rescheduled
* Site visit cancelled
* Site visit reminder
* Site visit completed

## Subscription/Payment

* Trial started
* Trial ending soon
* Trial expired
* Payment success
* Payment failed
* Subscription activated
* Subscription expiring soon
* Subscription expired
* Plan renewed
* Credits low
* Credits added
* Boost started/expired
* Featured listing started/expired

## Banner Ads

* Banner ad draft saved
* Banner ad payment pending
* Banner ad submitted
* Banner ad approved
* Banner ad rejected
* Banner ad active
* Banner ad expiring soon
* Banner ad expired
* Banner ad renewed

## Admin

* New moderation item
* New verification request
* New support ticket
* New report
* Provider issue
* Payment issue
* Suspicious activity
* Location request

---

# 6. IN-APP NOTIFICATION SYSTEM

In-app notifications should be database-backed.

Notification fields:

* id
* user_id
* entity_type
* entity_id
* event_type
* title
* message
* link_url
* status
* priority
* read_at
* created_at
* expires_at if needed

Statuses:

```txt id="zz65no"
unread
read
archived
deleted
```

In-app notifications should be visible in:

* Header notification icon
* Dashboard notifications page
* Role dashboard alerts
* Admin alert center

---

# 7. NOTIFICATION PRIORITY

Priority levels:

```txt id="77vq9b"
low
normal
high
urgent
```

Examples:

Low:

* Blog update if subscribed
* General announcement

Normal:

* Listing approved
* Proposal received

High:

* Payment failed
* Listing expiring soon
* Role rejected

Urgent:

* Account suspended
* Provider failure for admin
* Payment security issue

Priority affects display, not fake urgency.

---

# 8. NOTIFICATION PREFERENCES

Users should control notification preferences where applicable.

Preference categories:

* Leads
* Proposals
* Requirements
* Site visits
* Messages
* Subscription/billing
* Verification
* Banner ads
* Support
* Marketing

Channels:

* In-app
* Email
* WhatsApp
* SMS
* Push

System-critical notifications may be required and not fully disabled.

Marketing notifications must be optional.

Do not send external notifications if user opted out, except required service/legal notifications.

---

# 9. ROLE-BASED NOTIFICATION ROUTING

Notification receiver depends on role/entity.

Owner:

* Property leads
* Listing approval
* Expiry
* Site visits

Broker:

* Listing leads
* Requirement feed alerts
* Proposal responses
* Site visits
* Subscription

Agency Owner:

* Agency leads
* Agent assignments
* Banner ads
* Plan usage
* Verification
* Agency listing updates

Agency Agent:

* Assigned leads
* Assigned site visits
* Messages
* Tasks

Builder:

* Project leads
* Project approvals
* Site visits
* Banner ads
* Subscription

Buyer/Tenant:

* Requirement proposals
* Site visits
* Saved search alerts
* Contact responses

Admin:

* Queues and moderation alerts

Do not send agency-wide notifications to unrelated agents.

---

# 10. NOTIFICATION TEMPLATE SYSTEM

Templates should be configurable.

Template fields:

* key
* channel
* title
* body
* variables
* active
* language
* updated_by
* updated_at

Variables examples:

```txt id="5dp60l"
{user_name}
{property_title}
{city}
{expiry_date}
{plan_name}
{lead_name}
{requirement_title}
{project_name}
{banner_ad_title}
```

Templates should not include hidden private data unless allowed.

---

# 11. EMAIL NOTIFICATION RULE

Email notification requires email provider.

Before sending email:

* Check provider configured.
* Check user email exists.
* Check email verified if required.
* Check notification preference.
* Use template.
* Send through provider.
* Log delivery result.

If email provider missing:

* Create in-app notification if required.
* Do not mark email as sent.

---

# 12. WHATSAPP NOTIFICATION RULE

Automatic WhatsApp notification requires API mode.

Free `wa.me` mode is not automatic.

Before sending WhatsApp API message:

* Check WhatsApp mode = API.
* Check API configured.
* Check receiver phone exists.
* Check user preference/consent if needed.
* Check template approved if provider requires.
* Send message.
* Log delivery result.

If WhatsApp mode = Free:

* Do not send automatic notification.
* Use in-app notification.
* Contact buttons can open wa.me manually.

Do not fake WhatsApp sent.

---

# 13. SMS NOTIFICATION RULE

SMS requires SMS provider.

Before sending SMS:

* Check SMS provider configured.
* Check phone number valid.
* Check user preference/consent if needed.
* Check template if required.
* Check rate limit.
* Send.
* Log delivery result.

If SMS provider missing, do not mark as sent.

---

# 14. PUSH NOTIFICATION RULE

Push is optional.

If implemented:

* User must opt in.
* Device token stored securely.
* Send through push provider.
* Handle invalid tokens.
* Log delivery if provider supports.
* Respect preferences.

If not implemented, hide push options.

---

# 15. NOTIFICATION DELIVERY LOG

External delivery logs should store real status.

Fields:

* id
* notification_id
* channel
* provider
* recipient
* status
* provider_message_id
* error_code
* error_message safe
* sent_at
* delivered_at if available
* failed_at
* retry_count

Statuses:

```txt id="pgl1d9"
queued
sent
delivered
failed
skipped
cancelled
provider_unavailable
```

Do not mark delivered unless provider confirms delivery.

If only sent confirmation exists, show sent, not delivered.

---

# 16. NOTIFICATION RETRY RULE

Retry should be limited.

Retry rules:

* Retry failed provider calls if temporary.
* Do not retry invalid phone/email.
* Limit retry count.
* Use backoff if possible.
* Do not spam users.
* Log retries.

If retry fails, keep in-app notification if needed.

---

# 17. SCHEDULED JOB SYSTEM

Automations need scheduled jobs.

Scheduled jobs may run:

* Hourly
* Daily
* Weekly
* Event-driven

Examples:

* Check expiring listings daily.
* Expire listings daily.
* Send site visit reminders hourly/daily.
* Expire banner ads hourly/daily.
* Send subscription reminders daily.
* Archive old records weekly/monthly.

Jobs must be idempotent.

If job runs twice, it should not send duplicate notifications.

---

# 18. JOB TYPES

Possible scheduled jobs:

* listing_expiry_reminder_job
* listing_expiry_job
* listing_archive_job
* requirement_expiry_reminder_job
* requirement_expiry_job
* banner_ad_expiry_reminder_job
* banner_ad_expiry_job
* subscription_expiry_reminder_job
* subscription_expiry_job
* trial_expiry_job
* boost_expiry_job
* featured_listing_expiry_job
* site_visit_reminder_job
* unpaid_payment_cleanup_job
* draft_cleanup_job
* notification_retry_job
* notification_archive_job
* sitemap_refresh_job if implemented
* provider_health_check_job if implemented

Only implement jobs actually needed.

---

# 19. JOB EXECUTION LOG

Every scheduled job should log:

* job name
* started_at
* finished_at
* status
* records_checked
* records_updated
* notifications_created
* errors
* duration
* triggered_by

Statuses:

```txt id="4kilcj"
success
partial_success
failed
skipped
running
```

Do not show fake job success.

---

# 20. IDEMPOTENCY RULE

Automated jobs must avoid duplicates.

Examples:

If listing expiry reminder sent today:

* Do not send same reminder repeatedly unless configured.

Use notification/event keys:

```txt id="z0q0il"
listing:{listing_id}:expiry_reminder:3_days
```

or store reminder state.

Do not spam users with repeated identical messages.

---

# 21. LISTING EXPIRY SYSTEM

Listings must have expiry if plan/settings require.

Listing expiry fields:

* published_at
* expires_at
* expiry_status
* renewal_allowed
* grace_period_until if enabled
* archived_at
* archive_reason

Expiry statuses:

```txt id="43dnfq"
active
expiring_soon
expired
grace_period
archived
renewed
```

When expires_at passes:

* Mark expired.
* Hide from active search.
* Disable new contacts if policy.
* Notify owner/entity.
* Show renew CTA.
* Archive later if configured.

Do not show expired listing as active.

---

# 22. LISTING EXPIRY REMINDERS

Reminder schedule example:

* 7 days before expiry
* 3 days before expiry
* 1 day before expiry
* On expiry day
* After expiry if grace period

Admin/Super Admin can configure.

Notification content:

```txt id="7rbdtg"
Your property listing will expire on {expiry_date}. Renew now to keep it active.
```

Do not send reminder if listing already sold/rented/archived.

---

# 23. LISTING AUTO-HIDE RULE

When listing expires:

* Remove from active search.
* Remove from homepage sections.
* Remove from city pages active results.
* Keep visible in user dashboard as expired.
* Public detail page may show expired/unavailable or noindex/redirect based on SEO policy.
* Disable lead/contact actions if policy.

Auto-hide must be real.

---

# 24. LISTING ARCHIVE RULE

Archive is different from expire.

Archive means older/inactive record is moved out of active workflow.

Archive triggers:

* Expired for X days
* User manually archives
* Admin archives
* Property sold/rented and old
* Rejected/abandoned draft cleanup
* Policy violation

Archived listings:

* Not public
* Still visible to owner/admin if allowed
* Can be restored/renewed if allowed
* Keep audit history

Do not delete important records without policy.

---

# 25. REQUIREMENT EXPIRY SYSTEM

Requirements should expire.

Requirement fields:

* created_at
* expires_at
* status
* renewed_at
* closed_at
* archived_at

When requirement expires:

* Hide from requirement feed.
* Stop new proposals.
* Notify buyer/tenant.
* Show renew/close option.
* Keep proposals history.

Do not show expired requirements to brokers as active.

---

# 26. REQUIREMENT EXPIRY REMINDERS

Reminder schedule example:

* 3 days before expiry
* 1 day before expiry
* On expiry

Message:

```txt id="xm6vbl"
Your requirement will expire soon. Renew it to keep receiving proposals.
```

Do not send if requirement already closed.

---

# 27. BANNER AD EXPIRY SYSTEM

Banner ads must expire exactly based on campaign duration.

Banner ad expiry fields:

* start_at
* end_at
* status
* expired_at
* renewed_from_ad_id if renewed
* payment_status
* approval_status

When expired:

* Stop displaying publicly.
* Status becomes expired.
* Notify advertiser.
* Show renew CTA.
* Keep analytics/history if real.

Do not show expired banner ad.

---

# 28. BANNER AD REMINDERS

Reminder schedule:

* 3 days before expiry
* 1 day before expiry
* On expiry

Message:

```txt id="yk38pd"
Your banner ad campaign will expire on {expiry_date}. Renew to keep it active.
```

Only send if ad is active/scheduled and not cancelled.

---

# 29. SUBSCRIPTION EXPIRY SYSTEM

Subscription expiry fields:

* started_at
* expires_at
* status
* grace_period_until
* renewed_at
* cancelled_at
* expired_at

When subscription expires:

* Status becomes expired or grace_period.
* Paid benefits stop or continue only during configured grace.
* Notify user/entity.
* Show renewal CTA.
* Enforce plan limits.

Do not allow paid benefits after expiry unless grace configured.

---

# 30. SUBSCRIPTION REMINDERS

Reminder schedule example:

* 7 days before expiry
* 3 days before expiry
* 1 day before expiry
* On expiry
* Grace period ending

Message:

```txt id="f2ygmg"
Your {plan_name} plan will expire on {expiry_date}. Renew to continue benefits.
```

No fake expiry.

---

# 31. TRIAL EXPIRY SYSTEM

Trial plan must expire.

Trial fields:

* trial_started_at
* trial_ends_at
* status
* converted_to_paid_at
* expired_at

When trial ends:

* Trial status becomes expired.
* Trial features disabled.
* User sees upgrade CTA.
* Notify user.
* Prevent trial reset abuse.

Do not allow infinite trial.

---

# 32. BOOST EXPIRY SYSTEM

Boost should expire by end time.

Boost fields:

* listing_id
* started_at
* ends_at
* status
* credit/payment source

When expired:

* Remove boost ranking/label.
* Status expired.
* Notify user if configured.
* Keep history.

Do not keep listing boosted after expiry.

---

# 33. FEATURED LISTING EXPIRY SYSTEM

Featured listing expires by end time.

When expired:

* Remove Featured label.
* Remove featured placement.
* Status expired.
* Notify user.
* Allow renewal.

Do not show featured after expiry.

---

# 34. PROJECT EXPIRY SYSTEM

Builder projects may have plan/visibility expiry.

Project expiry rules:

* Project package duration
* Project active status
* Project promotion expiry
* Project archive for inactive/old projects
* Unit status independent if needed

Do not hide active paid project before expiry unless policy violation/admin action.

---

# 35. DRAFT REMINDERS

Draft reminders are optional.

Examples:

* Property draft incomplete
* Requirement draft incomplete
* Banner ad draft incomplete
* Project draft incomplete

Rules:

* Do not spam.
* Send only if user consent/setting.
* Archive/delete old drafts based on settings.
* Show dashboard reminder.

---

# 36. SITE VISIT REMINDERS

Site visit reminder schedule example:

* 24 hours before
* 2 hours before
* 30 minutes before if enabled

Reminder receivers:

* Buyer/Tenant
* Owner/Broker/Agency/Agent/Builder
* Assigned agent if any

Message:

```txt id="y8tvta"
Site visit reminder: {property_title} on {visit_date_time}.
```

Do not send for cancelled/rejected/completed visits.

---

# 37. FOLLOW-UP REMINDERS

Lead follow-up reminders are optional.

User can set:

* Follow-up date
* Follow-up time
* Note
* Assigned agent

When due:

* Notify assigned user.
* Show dashboard alert.
* Do not notify unrelated users.

If not implemented, hide follow-up reminders.

---

# 38. NOTIFICATION CENTER UI

Notification center should include:

* All notifications
* Unread
* Read
* Archived
* Filters by type
* Mark as read
* Mark all as read
* Delete/archive if allowed
* Link to related entity
* Mobile card layout

Do not show notifications without working links unless informational.

---

# 39. HEADER NOTIFICATION BADGE

Header notification icon should show unread count.

Rules:

* Count real unread notifications.
* Do not fake count.
* Update after mark read.
* Mobile friendly.
* Role-aware if user has multiple roles.

If notification system disabled, hide icon.

---

# 40. DASHBOARD ALERT CARDS

Dashboards should show urgent alerts.

Examples:

Owner:

* 2 listings expiring soon
* 1 new lead
* Profile incomplete

Broker:

* 5 new requirements
* 3 proposals viewed
* Plan expiring soon

Agency:

* 4 unassigned leads
* Banner ad expiring
* Agent seat limit reached

Builder:

* Project pending approval
* Site visit tomorrow
* Plan expiring

Alerts must come from real data.

---

# 41. ADMIN ALERTS

Admin alerts:

* New pending moderation
* Verification queue
* Payment issue
* Provider failure
* Support ticket
* Report/fraud
* Failed scheduled job

Admin alerts should be permission-scoped.

City Manager sees city-specific alerts.

---

# 42. ARCHIVE SYSTEM

Archive is a general system for older/inactive records.

Archivable entities:

* Properties
* Projects
* Requirements
* Proposals
* Leads
* Site visits
* Banner ads
* Notifications
* Support tickets
* Drafts
* Reports

Archive should preserve history.

Do not hard delete important business records unless policy.

---

# 43. ARCHIVE STATUS

Archive fields:

* archived_at
* archived_by
* archive_reason
* previous_status
* restore_allowed
* restored_at
* restored_by

Archive reasons:

* Expired
* User archived
* Admin archived
* Sold/rented
* Duplicate
* Policy violation
* Old/inactive
* Payment expired

---

# 44. RESTORE RULE

Some archived records can be restored.

Restore requires:

* Permission
* Entity still valid
* Plan/subscription valid if needed
* Status transition allowed
* Audit log

Example:

Expired property can be renewed/restored if user pays/renews.

Policy violation item may require admin approval.

---

# 45. DELETE VS ARCHIVE RULE

Use archive for business records.

Use delete only for:

* User cancels draft
* Soft delete with recovery if needed
* Legal/account deletion workflows
* Temporary files cleanup
* Invalid abandoned records

Important records should be soft deleted or archived.

Do not permanently delete payment/audit records casually.

---

# 46. CLEANUP JOBS

Cleanup jobs may handle:

* Old abandoned drafts
* Failed payment orders
* Temporary uploads
* Expired OTP records
* Old notifications
* Old logs if retention policy
* Orphan media
* Expired signed URLs if stored

Cleanup must be safe.

Do not delete active user content.

---

# 47. NOTIFICATION RETENTION

Notification retention policy:

* Keep unread notifications.
* Archive old read notifications after X days if configured.
* Delete old low-priority notifications after X days if configured.
* Keep billing/security notifications longer if needed.

Super Admin can configure retention.

---

# 48. SCHEDULED JOB SECURITY

Scheduled jobs must be protected.

Rules:

* Use secure secret/token for cron endpoints.
* Do not expose public unauthenticated dangerous jobs.
* Log execution.
* Prevent duplicate overlapping job if needed.
* Run with service role only server-side.
* Validate job permissions.
* Avoid leaking data in logs.

---

# 49. TIME ZONE RULE

All stored timestamps should be UTC.

Display time in user/admin timezone.

Default platform/user timezone:

```txt id="kueen7"
Asia/Kolkata
```

Expiry calculations should be consistent.

Do not expire early due to timezone confusion.

---

# 50. AUTOMATION SETTINGS

Super Admin can configure automation.

Settings:

* Listing expiry days
* Requirement expiry days
* Banner ad reminder days
* Subscription reminder days
* Trial reminder days
* Archive after expiry days
* Grace period days
* Notification channels
* Job enabled/disabled
* Retry count
* Cleanup retention days

Visible settings must work.

No fake toggles.

---

# 51. AUTOMATION FEATURE FLAGS

Possible feature flags:

```txt id="dcgrq5"
notifications.enabled
notifications.in_app.enabled
notifications.email.enabled
notifications.whatsapp.enabled
notifications.sms.enabled
notifications.push.enabled

automation.enabled
automation.scheduled_jobs.enabled
automation.expiry_jobs.enabled
automation.archive_jobs.enabled
automation.notification_retry.enabled

expiry.listings.enabled
expiry.requirements.enabled
expiry.banner_ads.enabled
expiry.subscriptions.enabled
expiry.trials.enabled
expiry.boosts.enabled
expiry.featured_listings.enabled

archive.enabled
archive.auto_archive.enabled
renewal.enabled
reminders.site_visits.enabled
reminders.followups.enabled
```

If feature flag off, hide UI and block backend behavior where needed.

---

# 52. AUTOMATION DATABASE MODULES

Possible tables:

```txt id="rbk9by"
notifications
notification_preferences
notification_templates
notification_delivery_logs
scheduled_jobs
job_execution_logs
expiry_events
archive_events
reminders
reminder_logs
notification_retry_queue
automation_settings
```

Entity tables should include expiry/archive fields where needed.

---

# 53. EXPIRY EVENT TABLE

`expiry_events` may store:

* id
* entity_type
* entity_id
* event_type
* scheduled_for
* processed_at
* status
* notification_sent
* job_id
* metadata

Useful for avoiding duplicates.

---

# 54. REMINDER TABLE

`reminders` may store:

* id
* user_id
* entity_type
* entity_id
* reminder_type
* remind_at
* status
* channel_preference
* message
* created_at
* sent_at

Statuses:

```txt id="s50opm"
scheduled
sent
failed
cancelled
skipped
```

---

# 55. NOTIFICATION API / SERVER ACTIONS

Possible actions:

* getNotifications
* markNotificationRead
* markAllNotificationsRead
* archiveNotification
* updateNotificationPreferences
* createInAppNotification
* sendNotification
* retryNotification
* runExpiryJob
* renewListing
* renewRequirement
* renewSubscription
* archiveEntity
* restoreEntity

All actions must check permissions.

---

# 56. DELIVERY STATUS DISPLAY

User should see simple delivery status only where useful.

Example:

* In-app unread/read
* Email sent if confirmed
* WhatsApp sent if API confirmed
* SMS sent if confirmed

Do not show provider technical details to normal users.

Admin can see provider details if permitted.

---

# 57. NO-FAKE NOTIFICATION RULE

Do not fake:

* Notification delivery
* WhatsApp sent
* SMS sent
* Email sent
* Push sent
* Read receipt
* Reminder sent
* Expiry job completed
* Archive job completed
* Renewal success
* Subscription expiry
* Listing active status

If not implemented, hide status or show pending/unavailable.

---

# 58. LOADING STATES

Loading states:

* Loading notifications
* Marking read
* Updating preferences
* Sending notification
* Loading job logs
* Renewing
* Archiving
* Restoring
* Loading expiry status

Use skeleton/progress.

---

# 59. EMPTY STATES

Notification empty:

```txt id="7sxxgh"
No notifications yet.
```

Expiry empty:

```txt id="tg14ga"
No items expiring soon.
```

Admin job log empty:

```txt id="p4c9u6"
No scheduled job logs found.
```

No fake records.

---

# 60. ERROR STATES

Error examples:

```txt id="3bt9lp"
Could not load notifications.
```

```txt id="g9szaa"
Could not renew listing. Please try again.
```

```txt id="69f4xh"
WhatsApp provider is not configured. Notification was not sent.
```

```txt id="abpvex"
Scheduled job failed. Please check logs.
```

Do not expose secrets/raw stack traces.

---

# 61. SUCCESS STATES

Success examples:

```txt id="7hy9te"
Notification preferences updated.
```

```txt id="j23284"
Listing renewed successfully.
```

```txt id="zp4vhj"
Requirement archived.
```

```txt id="qc35iy"
Site visit reminder sent.
```

Success only after real action.

---

# 62. SECURITY RULES

Notification/automation security:

* Users see only own notifications.
* Agency owner sees agency notifications if policy.
* Agent sees assigned notifications.
* Admin alerts require permission.
* Cron endpoints protected.
* Service role server-side only.
* Notification templates sanitized.
* No hidden contact leaked in notification text.
* External notifications respect preferences and consent.
* Sensitive notifications avoid exposing private data.

---

# 63. MOBILE UX RULE

Mobile notification center:

* Card list
* Filters as tabs/chips
* Large touch targets
* Mark read action
* Swipe/archive optional
* Notification detail if needed
* No horizontal scroll

Dashboard expiry alerts:

* Compact cards
* Renew CTA
* Details link

Admin job logs on mobile:

* Cards, not wide tables.

---

# 64. ADMIN AUTOMATION PANEL

Admin/Super Admin automation panel should show:

* Expiring listings
* Expiring requirements
* Expiring subscriptions
* Expiring banner ads
* Failed jobs
* Notification failures
* Provider failures
* Retry queue
* Archive queue
* Automation settings if permitted

Super Admin can configure settings.

Admin can view/manage based on permission.

---

# 65. AUDIT LOG RULE

Audit important automation/admin actions:

* Manual archive
* Manual restore
* Manual renewal
* Automation settings changed
* Notification template changed
* Job manually triggered
* Job disabled/enabled
* Failed job acknowledged
* Provider/channel disabled
* Bulk archive/restore

Do not allow silent admin changes.

---

# 66. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* User receives in-app notification for approved listing.
* Lead notification appears to receiver.
* Alternate number is not leaked incorrectly.
* Listing expiry date exists.
* Expiry reminder triggers or can be simulated.
* Expired listing hides from active search.
* Expired listing remains in dashboard.
* Renew listing works if allowed.
* Requirement expiry hides from requirement feed.
* Banner ad expires and stops displaying.
* Subscription expiry removes paid benefits after expiry/grace.
* Boost/featured expires and label disappears.
* Site visit reminder does not send for cancelled visit.
* Email notification works only if provider configured.
* WhatsApp automatic notification works only in API mode.
* Free wa.me mode does not fake automatic send.
* SMS missing provider does not fake sent.
* Notification preferences are respected.
* Users see only own notifications.
* Admin job logs are real or hidden.
* Cron/job endpoint is protected.
* Mobile notification center has no horizontal scroll.
* No screenshot/video capture required.

---

# 67. PASS / FAIL RULE

Notification/automation phase is PASS only if:

* In-app notifications are real.
* External delivery is provider-based and not fake.
* Expiry dates are stored and enforced.
* Expired listings hide from active search.
* Expired requirements stop proposals.
* Expired banner ads stop displaying.
* Expired boosts/featured labels stop.
* Subscription expiry stops paid benefits unless grace configured.
* Renewal works through real payment/plan logic.
* Archive system preserves history.
* Scheduled jobs are protected/logged if implemented.
* Notification preferences are respected.
* No fake sent/delivered/job success appears.
* Feature registry updated.
* Manual verification completed.

If expired paid ad/listing still displays as active, mark FAIL.

If WhatsApp/SMS/email sent status is fake, mark FAIL.

If cron endpoint is public and dangerous, mark FAIL.

---

# 68. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `09_PROPERTY_POSTING_TYPE_BASED_FIELDS_MEDIA_UPLOAD_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for role, provider, database, payment and QA-specific details.

---

# 69. END OF FILE

This file defines notification, automation, expiry, renewal and archive system requirements for My Gujarat Property.

The system must notify users correctly, enforce expiry, auto-hide inactive paid/public content, archive safely, respect provider settings and never fake notification delivery or automation success.

Nothing from uploaded docs or user chat instructions should be skipped.
