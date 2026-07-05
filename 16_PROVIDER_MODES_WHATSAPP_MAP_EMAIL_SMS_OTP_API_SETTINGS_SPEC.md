# MY GUJARAT PROPERTY

# PROVIDER MODES, WHATSAPP, MAP, EMAIL, SMS, OTP & API SETTINGS SPEC

## FILE NAME

`16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete provider settings, provider modes, WhatsApp mode, Map mode, Email provider, SMS provider, OTP provider, payment provider connection rules, API settings, feature toggles, secrets security and provider health behavior for **My Gujarat Property**.

This file must be read before building or redesigning:

* WhatsApp settings
* Free WhatsApp link mode
* WhatsApp API mode
* Map settings
* Google Maps embed/free/trial mode
* Google Maps premium API mode
* OTP provider settings
* Development OTP mode
* Production OTP mode
* Email provider settings
* Email verification provider
* SMS provider settings
* Payment provider settings connection
* Storage provider settings display
* API settings panel
* Provider health/status panel
* Provider fallback behavior
* Feature flags
* Admin/Super Admin provider controls
* Secrets storage
* Environment variables
* Provider missing states
* No-fake provider behavior

The goal is to let Super Admin control provider behavior without fake buttons or broken integrations.

---

# 2. CORE PROVIDER PRINCIPLE

Every external service must have a clear provider mode.

If a provider is not configured:

* Hide the related feature, or
* Show setup-required state in Admin/Super Admin, or
* Show safe unavailable message to users.

Do not pretend provider is working.

Do not show fake success.

Do not expose secrets.

Provider mode must control real behavior across the platform.

---

# 3. PROVIDER CATEGORIES

The platform may use providers for:

* WhatsApp
* Maps
* OTP
* SMS
* Email
* Payment
* Storage
* Analytics
* Push notifications
* AI/automation if implemented
* Search indexing if implemented

Each provider category needs:

* Enabled/disabled state
* Active mode
* Configuration status
* Secret handling
* Runtime behavior
* Admin test action if safe
* Error handling
* Audit logging for setting changes
* Feature flag connection

---

# 4. SUPER ADMIN CONTROL RULE

Only Super Admin should control global provider settings.

Admin may view limited status if permitted.

Normal users must not see provider secrets/settings.

Provider settings affect platform-wide behavior.

Examples:

If Super Admin sets WhatsApp mode to free:

* Contact buttons use `wa.me`.

If Super Admin sets WhatsApp mode to API:

* Platform uses configured WhatsApp API.

If Super Admin disables Maps:

* Map buttons/sections hide or show text location only.

If OTP provider is missing in production:

* OTP login must not fake success.

---

# 5. PROVIDER SETTINGS ROUTES

Recommended routes:

```txt id="mkdwzy"
/admin/super/providers
/admin/super/providers/whatsapp
/admin/super/providers/maps
/admin/super/providers/otp
/admin/super/providers/email
/admin/super/providers/sms
/admin/super/providers/payment
/admin/super/providers/storage
/admin/super/providers/analytics
/admin/super/providers/health
/admin/super/providers/logs
```

Only show routes/features that exist.

---

# 6. PROVIDER SETTINGS UI RULE

Provider settings page should show:

* Provider category
* Current mode
* Enabled/disabled state
* Configuration status
* Last updated
* Updated by
* Test connection if safe
* Error message if broken
* Feature usage areas
* Save button
* Reset/cancel
* Audit log link

Do not show raw secret values after save.

Use masked secrets.

Example:

```txt id="65l5q1"
API Key: ************abcd
```

---

# 7. PROVIDER MODE STATUS

Each provider can have status:

```txt id="851f07"
Disabled
Not Configured
Configured
Active
Error
Testing
Deprecated
Maintenance
```

Public features should use only active/configured providers.

Do not show provider status as Active unless actually configured and usable.

---

# 8. WHATSAPP PROVIDER PURPOSE

WhatsApp is important for Indian real estate contact flow.

WhatsApp can be used for:

* Property contact
* Project enquiry
* Broker/agency contact
* Lead notification
* Site visit notification
* Requirement/proposal contact
* Support if enabled
* Banner ad CTA
* Admin alerts if implemented

WhatsApp must support both free and API mode.

---

# 9. WHATSAPP MODES

WhatsApp modes:

```txt id="8r31vi"
Disabled
Free wa.me Mode
API Mode
```

## Disabled

* Hide WhatsApp buttons.
* Use lead form/call/message if enabled.

## Free wa.me Mode

* Opens WhatsApp app/web using `wa.me`.
* Does not send automatic messages from platform.
* Can use prefilled message.
* Can track click if tracking implemented.

## API Mode

* Sends real WhatsApp message through configured API.
* Requires provider configuration.
* Requires templates if provider requires templates.
* Logs send status if real.
* Handles failures.

---

# 10. WHATSAPP ACTIVE MODE RULE

Super Admin must choose one active WhatsApp mode.

Mode affects all WhatsApp buttons.

Examples:

If mode = Free wa.me:

* Contact button opens WhatsApp link.
* No “message sent” status unless user action is only click/open tracked.

If mode = API:

* Button can trigger API send only if configured.
* If API fails, show failure.
* Do not open fake sent success.

If mode = Disabled:

* Hide WhatsApp CTA or show unavailable.

---

# 11. WHATSAPP FREE MODE SETTINGS

Free mode settings:

* Enabled
* Default country code
* Default prefilled message
* Include property URL yes/no
* Include project URL yes/no
* Include requirement/proposal context yes/no
* Track clicks yes/no
* Open in new tab yes/no
* Use receiver WhatsApp number from profile/listing

Free mode does not require paid API.

Free mode should never claim the message was delivered.

---

# 12. WHATSAPP FREE MODE MESSAGE TEMPLATE

Example property enquiry message:

```txt id="h9dqqf"
Hello, I am interested in this property listed on My Gujarat Property: {property_title} in {city}. Link: {property_url}
```

Example project enquiry:

```txt id="8l4c16"
Hello, I am interested in this project listed on My Gujarat Property: {project_name} in {city}. Link: {project_url}
```

Do not include hidden private address/contact data.

---

# 13. WHATSAPP API MODE SETTINGS

API mode settings:

* Provider name
* API endpoint
* API key/token
* Sender number
* Business account ID if needed
* Template namespace if needed
* Default templates
* Webhook secret if needed
* Retry policy
* Rate limits
* Delivery callback enabled
* Test number
* Test send button if safe

Secrets must be server-side.

Do not expose API token to client.

---

# 14. WHATSAPP API TEMPLATE TYPES

Possible templates:

* Lead received
* Site visit requested
* Site visit confirmed
* Requirement proposal received
* OTP if WhatsApp OTP is supported
* Subscription expiring
* Banner ad approved
* Support reply

If provider requires approved templates, only use approved templates.

Do not fake template approval.

---

# 15. WHATSAPP API SEND RULE

Before sending API WhatsApp message, check:

* WhatsApp mode = API
* Provider configured
* Sender configured
* Receiver number valid
* Template/message allowed
* User consent/notification preference if needed
* Rate limit
* Feature flag
* Account status

If any fail:

* Do not send.
* Log safe error.
* Show failure/setup state.

---

# 16. WHATSAPP PROVIDER MISSING STATE

If API mode is selected but provider missing:

Admin UI:

```txt id="736ec1"
WhatsApp API mode is selected but API credentials are missing.
```

Public UI:

```txt id="zxbn7d"
WhatsApp contact is currently unavailable. Please use enquiry form.
```

Do not show fake WhatsApp success.

---

# 17. MAP PROVIDER PURPOSE

Maps support:

* Property location
* Project location
* Search map view
* Nearby places if implemented
* Address autocomplete if API supports
* Map pin
* Approximate location
* Site visit route if future

Maps must support free/embed and premium/API mode.

---

# 18. MAP MODES

Map modes:

```txt id="j5vffd"
Disabled
Free / Embed / Trial Mode
Premium API Mode
```

## Disabled

* Hide map.
* Show text location.

## Free / Embed / Trial Mode

* Use allowed embed/static map approach.
* No advanced API features unless allowed.
* May show simple map.

## Premium API Mode

* Use configured map API.
* Supports interactive map, geocoding, places, autocomplete if enabled.
* Requires valid API key.

---

# 19. MAP ACTIVE MODE RULE

Super Admin chooses active map mode.

If map mode = Disabled:

* Hide map sections.
* Do not show fake map.

If map mode = Embed:

* Use safe embed.
* Do not call premium API.

If map mode = Premium API:

* Use API only if configured.
* Show setup-required if missing.

---

# 20. MAP SETTINGS

Map settings:

* Active mode
* Provider
* API key
* Embed allowed yes/no
* Default country/state
* Default center
* Default zoom
* Search map enabled
* Detail page map enabled
* Project map enabled
* Address autocomplete enabled
* Exact/approximate location setting
* Lazy loading enabled
* Cost-saving mode
* Rate limits if needed

API key must be restricted and safe.

---

# 21. MAP PRIVACY RULE

Map must respect location privacy.

If listing location is approximate:

* Show approximate pin or locality area.
* Do not show exact lat/lng publicly.

If exact address hidden:

* Do not expose exact coordinates in API/HTML.
* Use approximate location.

If exact public:

* Show map pin.

Do not leak hidden location through map data.

---

# 22. MAP PROVIDER MISSING STATE

If map provider missing:

Admin:

```txt id="ex1j25"
Map API is not configured. Premium map features are disabled.
```

Public:

* Hide map, or
* Show text location only.

Do not show fake map placeholder pretending to be real.

---

# 23. OTP PROVIDER PURPOSE

OTP is used for:

* Login
* Register
* Phone verification
* Passwordless auth if implemented
* High-risk action confirmation if implemented

OTP can use:

* SMS OTP
* WhatsApp OTP if provider supports
* Email OTP if enabled
* Development OTP mode

---

# 24. OTP MODES

OTP modes:

```txt id="yjmps4"
Disabled
Development OTP
SMS OTP
WhatsApp OTP
Email OTP
Provider OTP
```

Recommended:

* Development OTP only in development.
* Production uses real SMS/WhatsApp/email OTP provider.

Do not use dev/static OTP in production.

---

# 25. DEVELOPMENT OTP MODE

Development OTP mode may allow:

* Static OTP
* Random OTP displayed in dev logs
* Test phone numbers
* Bypass for seeded test users

Rules:

* Enabled only in development.
* Clearly marked.
* Must be impossible or blocked in production.
* Must not send real SMS unless configured.
* Must not expose OTP to production users.

Example settings:

```txt id="gc65ou"
DEV_AUTH_OTP_ENABLED=true
DEV_AUTH_STATIC_OTP=123456
```

---

# 26. PRODUCTION OTP RULE

Production OTP must be real.

Rules:

* Use configured provider.
* OTP expires.
* Resend cooldown.
* Attempt limit.
* Rate limit.
* Server verification.
* No static OTP.
* No client-side OTP verification.
* No fake success.

If provider missing, block login/register safely or hide provider.

---

# 27. OTP SETTINGS

OTP settings:

* Provider
* Mode
* OTP length
* Expiry minutes
* Resend cooldown seconds
* Max attempts
* Daily send limit
* IP/device limit
* Test numbers
* Message template
* Sender ID
* Country code
* Logging level
* Dev mode

Do not expose OTP secrets.

---

# 28. OTP RATE LIMIT RULE

Rate limit:

* Per phone
* Per IP
* Per device/session
* Per user if logged in
* Per time window

If too many attempts:

```txt id="05q5rk"
Too many OTP attempts. Please try again later.
```

Do not allow OTP spam.

---

# 29. SMS PROVIDER PURPOSE

SMS can be used for:

* OTP
* Lead notifications if enabled
* Site visit notifications
* Payment/subscription alerts
* Account alerts

SMS may be separate from OTP provider or same provider.

If SMS provider not configured:

* Hide SMS notification option.
* Do not fake SMS sent.

---

# 30. SMS SETTINGS

SMS settings:

* Provider
* API key/token
* Sender ID
* Templates
* Default country code
* Rate limits
* Webhook/status callback if provider supports
* Test SMS action
* Enabled notification types

Secrets server-side only.

---

# 31. EMAIL PROVIDER PURPOSE

Email provider can be used for:

* Email verification
* Login/magic link if enabled
* Payment receipts
* Subscription alerts
* Lead notifications
* Site visit notifications
* Support tickets
* CMS/contact form
* Admin alerts

Email must be configured before email-based features claim success.

---

# 32. EMAIL MODES

Email modes:

```txt id="agdi54"
Disabled
SMTP
API Provider
Supabase/Auth Email if used
Development Console Email
```

Development console email can log messages locally in dev.

Production must use real provider if emails are promised.

---

# 33. EMAIL SETTINGS

Email settings:

* Provider
* From name
* From email
* Reply-to email
* API key/SMTP credentials
* Email verification enabled
* Magic link enabled
* Template management
* Test email address
* Bounce handling if provider supports
* Unsubscribe/marketing preference if marketing email

Do not expose credentials.

---

# 34. EMAIL VERIFICATION RULE

Email verification from profile requires real email send.

Flow:

```txt id="4yzeqb"
User adds email
Clicks Verify Email
System sends verification code/link
User verifies
email_verified = true
```

If email provider missing:

* Do not mark verified.
* Show provider missing/setup-required.

---

# 35. PAYMENT PROVIDER CONNECTION

Payment provider settings are detailed in monetization document but provider page can show summary.

Payment settings may include:

* Provider
* Mode test/live
* Key configured status
* Webhook configured status
* Currency
* Tax/GST setting
* Last webhook event
* Test payment if safe

Payment secret keys must not be exposed.

Payment success must be server verified.

---

# 36. STORAGE PROVIDER CONNECTION

Storage provider settings may show:

* Public bucket status
* Private bucket status
* Upload limits
* File type rules
* Storage usage if available
* Bucket privacy status
* Signed URL support
* CDN/public URL status if available

If usage cannot be fetched, show setup-required.

Do not fake storage usage.

---

# 37. ANALYTICS PROVIDER CONNECTION

Analytics is optional.

If implemented, may track:

* Page views
* Search queries
* Listing views
* Contact clicks
* Banner impressions/clicks
* Conversion events
* Dashboard usage

Analytics settings:

* Provider
* Tracking ID
* Enabled pages
* Privacy/consent behavior
* Event tracking enabled
* Admin reporting enabled

If analytics missing:

* Hide analytics metrics.
* Do not fake analytics.

---

# 38. PUSH NOTIFICATION PROVIDER

Push notifications are optional.

If implemented:

* Provider
* VAPID keys if web push
* Device token storage
* User opt-in
* Notification templates
* Test push
* Rate limits

If not implemented, hide push UI.

---

# 39. PROVIDER SECRETS SECURITY

Secrets must be protected.

Rules:

* Secrets only server-side.
* Never expose service role keys to client.
* Never expose API keys that must be private.
* Use environment variables or encrypted settings.
* Mask secrets in admin UI.
* Audit secret changes.
* Restrict Super Admin access.
* Do not log full secrets.
* Do not return secrets in API responses.

---

# 40. ENVIRONMENT VARIABLES

Possible environment variables:

```txt id="2peo70"
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

NEXT_PUBLIC_SITE_URL=
NEXT_PUBLIC_APP_ENV=

DEV_AUTH_OTP_ENABLED=
DEV_AUTH_STATIC_OTP=

OTP_PROVIDER=
OTP_API_KEY=
OTP_SENDER_ID=

SMS_PROVIDER=
SMS_API_KEY=
SMS_SENDER_ID=

EMAIL_PROVIDER=
EMAIL_API_KEY=
EMAIL_FROM=

WHATSAPP_MODE=
WHATSAPP_API_URL=
WHATSAPP_API_TOKEN=
WHATSAPP_SENDER_NUMBER=

MAP_PROVIDER=
NEXT_PUBLIC_MAP_CLIENT_KEY=
MAP_SERVER_KEY=

PAYMENT_PROVIDER=
PAYMENT_KEY_ID=
PAYMENT_KEY_SECRET=
PAYMENT_WEBHOOK_SECRET=

ANALYTICS_PROVIDER=
NEXT_PUBLIC_ANALYTICS_ID=
```

Only public-safe keys should use `NEXT_PUBLIC_`.

---

# 41. PROVIDER SETTINGS STORAGE

Provider settings can be stored in:

* Environment variables
* Secure database settings
* Encrypted secrets manager
* Admin settings table for non-secret values

Secret values should not be stored plain text if avoidable.

Settings table may include:

* category
* key
* value
* encrypted_value
* is_secret
* updated_by
* updated_at

Do not expose secret values.

---

# 42. PROVIDER TEST ACTIONS

Super Admin may test provider.

Test actions:

* Send test WhatsApp
* Load test map
* Send test OTP to test number
* Send test SMS
* Send test email
* Test payment webhook/status
* Test storage upload/delete

Test actions must:

* Require permission
* Use safe test data
* Show real success/failure
* Rate-limit if needed
* Log audit event

Do not fake test success.

---

# 43. PROVIDER HEALTH PANEL

Health panel can show:

* WhatsApp status
* Map status
* OTP status
* SMS status
* Email status
* Payment status
* Storage status
* Analytics status

Statuses must be real or clearly “not checked”.

Allowed labels:

```txt id="0sik18"
Configured
Not Configured
Last Test Passed
Last Test Failed
Not Checked
Disabled
```

Do not show green Active if not checked/configured.

---

# 44. PROVIDER LOGS

Provider logs may include:

* OTP sent/failed
* Email sent/failed
* SMS sent/failed
* WhatsApp send/click
* Payment webhook
* Map API error
* Storage upload error
* Provider test result

Logs should avoid sensitive data.

Mask phone/email where appropriate.

Do not log secrets.

---

# 45. PROVIDER FALLBACK RULE

Fallback must be explicit.

Example:

WhatsApp API fails:

* Option A: fallback to wa.me if allowed.
* Option B: show failure and use lead form.
* Option C: retry.

Map API missing:

* Show location text.
* Hide map.

Email missing:

* Use in-app notification only.
* Do not claim email sent.

Payment missing:

* Disable paid purchase.
* Show contact support/admin setup.

Fallback must not fake original provider.

---

# 46. PROVIDER MODE IMPACT MATRIX

## WhatsApp Mode Impact

| Mode     | Public Button          | Lead Notifications | Status                        |
| -------- | ---------------------- | ------------------ | ----------------------------- |
| Disabled | Hidden                 | No WhatsApp        | Disabled                      |
| Free     | wa.me link             | No automatic send  | Click only                    |
| API      | API send if configured | Real API send      | Delivery if provider supports |

## Map Mode Impact

| Mode        | Detail Map         | Search Map      | Address Autocomplete  |
| ----------- | ------------------ | --------------- | --------------------- |
| Disabled    | Hidden             | Hidden          | Disabled              |
| Embed       | Simple embed       | Limited/hidden  | Disabled              |
| Premium API | Full if configured | Full if enabled | Enabled if configured |

## OTP Mode Impact

| Mode         | Login/Register  | Production Allowed |
| ------------ | --------------- | ------------------ |
| Dev OTP      | Test only       | No                 |
| SMS OTP      | Yes             | Yes                |
| WhatsApp OTP | Yes if provider | Yes                |
| Email OTP    | Optional        | Yes if provider    |
| Disabled     | Block/hide      | N/A                |

---

# 47. PROVIDER SETTINGS AUDIT LOG

Audit changes:

* Provider enabled/disabled
* Mode changed
* API key updated
* Webhook secret updated
* Test action run
* Feature flag changed
* Dev OTP enabled/disabled
* Payment provider mode changed
* Map mode changed
* WhatsApp mode changed

Audit log must include:

* Actor
* Action
* Provider category
* Old value if safe
* New value if safe
* Timestamp
* Reason/note if provided

Never log full secrets.

---

# 48. PROVIDER PERMISSIONS

Permission examples:

```txt id="s1g03s"
provider.view
provider.manage
provider.test
provider.whatsapp.manage
provider.map.manage
provider.otp.manage
provider.sms.manage
provider.email.manage
provider.payment.manage
provider.storage.view
provider.analytics.manage
provider.logs.view
provider.health.view
```

Only Super Admin should manage global provider settings by default.

---

# 49. PROVIDER FEATURE FLAGS

Possible feature flags:

```txt id="fxz90d"
providers.enabled
providers.health.enabled
providers.logs.enabled
providers.test_actions.enabled

whatsapp.enabled
whatsapp.free_mode.enabled
whatsapp.api_mode.enabled

maps.enabled
maps.embed_mode.enabled
maps.api_mode.enabled
maps.search_map.enabled
maps.detail_map.enabled
maps.address_autocomplete.enabled

otp.enabled
otp.dev_mode.enabled
otp.sms.enabled
otp.whatsapp.enabled
otp.email.enabled

email.enabled
email.verification.enabled
email.notifications.enabled
email.magic_link.enabled

sms.enabled
sms.notifications.enabled

payments.enabled
storage.usage.enabled
analytics.enabled
push_notifications.enabled
```

If flag is off, hide feature and block backend action.

---

# 50. PROVIDER UI COMPONENTS

Recommended components:

* ProviderSettingsShell
* ProviderCard
* ProviderModeSelector
* SecretInputMasked
* ProviderStatusBadge
* ProviderHealthPanel
* ProviderTestButton
* ProviderLogsTable
* WhatsAppSettingsForm
* MapSettingsForm
* OTPSettingsForm
* SMSSettingsForm
* EmailSettingsForm
* PaymentProviderSummary
* StorageProviderSummary
* AnalyticsSettingsForm
* FeatureFlagConnector
* ProviderMissingState
* ProviderAuditLogPanel

Avoid duplicate random provider forms.

---

# 51. PROVIDER MISSING STATES BY FEATURE

Property WhatsApp CTA:

```txt id="d5r307"
WhatsApp contact is unavailable. Please use enquiry form.
```

Map detail:

```txt id="dhm1rv"
Map is unavailable. Location details are shown above.
```

Email verification:

```txt id="6v035h"
Email verification is unavailable right now. Please try later.
```

OTP login:

```txt id="b7x8s6"
OTP login is unavailable. Please try again later.
```

Payment:

```txt id="x91hj4"
Online payment is unavailable. Please contact support.
```

Do not show broken buttons.

---

# 52. PROVIDER LOADING STATES

Provider loading states:

* Loading settings
* Saving settings
* Testing provider
* Sending test message
* Loading health
* Loading logs
* Verifying webhook
* Checking storage

Show progress.

Do not leave form frozen.

---

# 53. PROVIDER ERROR STATES

Error states:

* Invalid API key
* Provider unreachable
* Missing webhook secret
* Rate limit exceeded
* Invalid phone
* Invalid email
* Map key restricted/invalid
* Payment webhook verification failed
* Storage upload denied
* SMTP failed

Errors should be safe and clear.

Do not expose secrets.

---

# 54. PROVIDER SUCCESS STATES

Success states:

* Settings saved
* Test WhatsApp sent
* Test email sent
* Test SMS sent
* Map loaded successfully
* OTP provider verified
* Payment webhook verified
* Storage upload tested
* Feature flag updated

Success only after real confirmation.

---

# 55. PROVIDER NO-FAKE RULE

Do not fake:

* WhatsApp sent
* SMS sent
* Email sent
* OTP verified
* Map loaded
* Payment verified
* Webhook verified
* Storage usage
* API health
* Analytics data
* Push sent
* Provider test success

If unavailable, say unavailable or setup-required.

---

# 56. MANUAL VERIFICATION CHECKLIST

Manual verification prompt should test:

* Super Admin can open provider settings.
* Normal user cannot access provider settings.
* Admin without permission cannot edit provider settings.
* WhatsApp free mode changes public CTA to wa.me behavior.
* WhatsApp API mode uses API only if configured.
* WhatsApp API missing shows safe unavailable state.
* Map disabled hides maps.
* Map embed/API mode changes map behavior.
* Hidden exact location is not leaked through map.
* Dev OTP works only in development.
* Production does not allow static OTP.
* Missing OTP provider blocks fake login.
* Email verification sends real email or safe missing state.
* SMS provider missing hides SMS notifications.
* Payment provider secrets are not exposed.
* Provider secrets are masked.
* Provider test action shows real result.
* Provider health does not show fake green status.
* Provider setting changes create audit log.
* Mobile provider admin pages have no horizontal scroll.
* No screenshot/video capture required.

---

# 57. PASS / FAIL RULE

Provider phase is PASS only if:

* Provider settings are Super Admin protected.
* WhatsApp mode controls real WhatsApp behavior.
* Map mode controls real map behavior.
* OTP dev mode is development-only.
* Production OTP is not fake.
* Email/SMS missing states are safe.
* Provider secrets are server-side/masked.
* Feature flags affect UI/backend behavior.
* Provider health is real or clearly not checked.
* Provider tests are real.
* Audit logs exist for sensitive changes if implemented.
* No fake provider success.
* Feature registry updated.
* Manual verification completed.

If provider secrets are exposed to client, mark FAIL.

If static/dev OTP works in production, mark FAIL.

If WhatsApp/API buttons show fake success, mark FAIL.

---

# 58. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `14_HOMEPAGE_BANNER_ADS_CITY_TARGETING_AGENCY_REAL_ESTATE_GROUP_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `18_NOTIFICATION_AUTOMATION_EXPIRY_ARCHIVE_SYSTEM_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those documents for auth, contact, notifications, admin, banner ads, payments, storage and database security details.

---

# 59. END OF FILE

This file defines provider modes, WhatsApp, Map, Email, SMS, OTP and API settings for My Gujarat Property.

Provider behavior must be mode-driven, Super Admin controlled, secure, audited, no-fake and connected to real platform behavior.

Nothing from uploaded docs or user chat instructions should be skipped.
