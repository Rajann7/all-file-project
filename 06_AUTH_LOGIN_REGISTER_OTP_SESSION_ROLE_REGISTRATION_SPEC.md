# MY GUJARAT PROPERTY

# AUTH, LOGIN, REGISTER, OTP, SESSION & ROLE REGISTRATION SPEC

## FILE NAME

`06_AUTH_LOGIN_REGISTER_OTP_SESSION_ROLE_REGISTRATION_SPEC.md`

---

# 1. DOCUMENT PURPOSE

This document defines the complete authentication, login, register, OTP, session, role registration and public auth experience for **My Gujarat Property**.

This file must be read before building or redesigning:

* Login popup
* Register popup
* OTP screen
* Mobile auth flow
* Desktop auth flow
* Public auth button
* Admin login separation
* Role-based registration
* Role selection cards
* New-user registration flow
* Existing-user login flow
* Phone OTP login
* Development OTP mode
* Production OTP mode
* OTP autofill
* Email field behavior
* Email verification from profile
* Google login if enabled
* Session persistence
* Admin-controlled session timeout
* Intent preservation
* Login-required actions
* Auth state in header/sidebar
* Role-based redirect
* Protected route fallback
* Account suspended/banned state
* Provider missing states
* Auth security rules

Authentication is not only a login form.

Authentication includes:

* Identity
* Phone verification
* Optional email verification
* Role selection
* Active role
* Session
* Permissions
* Profile state
* Provider availability
* Device/session behavior
* Redirect intent
* Security
* No-fake UI rules

---

# 2. CORE AUTH PRINCIPLE

My Gujarat Property must use a real, role-aware authentication system.

The public website must have a simple login/register popup, but the backend logic must be secure and role-aware.

Auth must support:

* Guest browsing
* Phone-based login
* Role-based registration
* OTP verification
* Development OTP mode
* Production OTP provider
* Session persistence
* Profile creation
* Active role setup
* Role-based header/sidebar update
* Role-based dashboard redirect
* Protected route access
* Provider missing states
* Admin/staff separation

Claude must never build only a simple generic login form and call auth complete.

---

# 3. PRIMARY AUTH METHOD

Primary public auth method:

```txt id="jha01x"
Mobile number + OTP
```

Reason:

* Indian real estate users are more comfortable with phone-based login.
* Contact/lead flow depends on phone number.
* Buyers, tenants, owners, brokers and agencies need quick mobile access.
* Phone number helps reduce friction in lead forms.

Email can be collected but phone remains primary.

---

# 4. AUTH PROVIDERS

The platform may support:

1. Phone OTP
2. Email field
3. Email verification from profile
4. Email/password if enabled later
5. Google login if configured later
6. Magic link if enabled later
7. Development OTP mode
8. Admin/staff separate login flow

Only show providers that are implemented/configured.

No fake provider buttons.

No fake login success.

No fake OTP success in production.

---

# 5. PUBLIC LOGIN/REGISTER BUTTON RULE

Public header should show one clear auth entry:

```txt id="os1d8c"
Login / Register
```

Clicking it should open popup/modal.

The popup should allow user to choose:

* Login
* Register

If user is already logged in, the public header must not show Login/Register as the main action.

Logged-in user must see:

* Profile icon/avatar
* Active role if useful
* Dashboard/profile menu
* Logout option inside menu

This rule applies globally.

It is not only for header.

Any place where auth state is shown must show correct guest/logged-in state.

---

# 6. ADMIN LOGIN SEPARATION RULE

Admin login must not be shown inside public login/register popup.

Public login/register is for:

* Buyer
* Tenant
* Owner
* Broker
* Agency Owner
* Agency Agent if invited
* Builder
* Real Estate Group if enabled

Admin/staff roles must not be publicly selectable.

Admin/staff login should be separate and protected.

Possible admin login route:

```txt id="8fmx0w"
/admin/login
```

or secure existing admin auth route.

Public users must not see:

* Admin role selection
* Super Admin role selection
* Moderator role selection
* Support Executive role selection
* Verification Executive role selection
* City Manager role selection
* Staff registration button

Admin/staff accounts should be created or invited by Admin/Super Admin.

---

# 7. LOGIN VS REGISTER RULE

New user cannot directly login.

If a phone number does not exist in the system and user tries login:

Show safe message:

```txt id="qrcn4g"
This mobile number is not registered. Please register first.
```

Then show Register option.

Existing user can login with OTP.

Registration flow must create user profile and role.

Do not auto-create a new user from login flow unless product intentionally allows it and still collects required role registration.

User’s instruction:

```txt id="j6amja"
New user must register with role selection first, then OTP verification, then success.
```

---

# 8. PUBLIC REGISTER FLOW

Standard public registration flow:

```txt id="89lnt8"
Open Login/Register popup
Choose Register
Enter mobile number
Enter basic details if required
Select role
Enter email optional if field exists
Accept terms/privacy
Send OTP
Verify OTP
Create auth user/session
Create profile
Assign selected role
Set active role
Show success
Redirect to homepage or preserved intent/query
```

Required registration fields:

* Mobile number
* Role selection
* Full name if required
* Terms/privacy acceptance if required
* Email optional if enabled

Optional registration fields:

* Email
* City
* Language
* Referral/source
* Business name for broker/agency/builder if using quick registration

Do not overload public registration form.

Detailed business profile can be completed after login.

---

# 9. ROLE SELECTION DURING REGISTRATION

Public role selection must include only allowed public roles.

Allowed role cards may include:

* Buyer
* Tenant
* Owner
* Broker
* Agency
* Builder
* Real Estate Group if enabled

Optional roles if business decides:

* Investor
* Developer

Do not include:

* Admin
* Super Admin
* Moderator
* Support Executive
* Verification Executive
* Content Manager
* Advertisement Manager
* City Manager

Role cards should explain purpose.

Example:

## Buyer

```txt id="gz82x8"
I want to buy property.
```

## Tenant

```txt id="k95pbs"
I want to rent property, PG or hostel.
```

## Owner

```txt id="hrj76b"
I want to post my own property.
```

## Broker

```txt id="ahmjzu"
I manage property listings and leads.
```

## Agency

```txt id="l6idau"
I manage a real estate agency/team.
```

## Builder

```txt id="frqze1"
I want to list projects and units.
```

## Real Estate Group

```txt id="seynjp"
I want to promote real estate business or run banner ads.
```

If Real Estate Group is not separate, map it to Agency or Builder depending business decision.

---

# 10. ROLE SELECTION UI RULE

Role selection UI must be:

* Mobile-friendly
* Card-based
* Easy to understand
* Large touch targets
* Not too many long paragraphs
* Clear selected state
* Back button supported
* Continue button sticky on mobile if needed

Each role card may show:

* Icon
* Role name
* Short description
* Key benefit
* Verification/approval note if applicable

Example note for Broker/Agency/Builder:

```txt id="qsopcj"
Some business features may require admin approval or verification.
```

Do not scare users with too much complexity during registration.

---

# 11. ROLE-BASED REGISTRATION OUTCOME

After OTP success:

Buyer:

* Create buyer role.
* Redirect to homepage or current saved/contact/search intent.
* Show buyer profile completion later.

Tenant:

* Create tenant role.
* Redirect to homepage or rental/PG flow.

Owner:

* Create owner role.
* Redirect to post property if intent was post property.
* Otherwise owner dashboard/profile completion.

Broker:

* Create broker role in pending/active state based on admin setting.
* Ask for broker profile completion.
* Verification may be required for full access.

Agency:

* Create agency owner role.
* Ask for agency profile completion.
* Verification may be required.
* Banner ads feature may require plan/payment.

Builder:

* Create builder role.
* Ask for builder profile completion.
* Verification may be required.

Real Estate Group:

* Create real estate group/agency-like role if enabled.
* Ask for group profile completion.
* Banner ads feature may require plan/payment and approval.

---

# 12. LOGIN FLOW

Existing user login flow:

```txt id="ghu6hl"
Open Login/Register popup
Choose Login
Enter mobile number
System checks if user exists
If exists, send OTP
User verifies OTP
Session created
Profile loaded
Active role loaded
Header/sidebar updated
Redirect to preserved intent or homepage/dashboard
```

If user does not exist:

```txt id="3yxgi5"
Show “number not registered” and offer Register.
```

Login should not create incomplete ghost accounts.

---

# 13. OTP FLOW

OTP flow must be simple and mobile-friendly.

Steps:

1. User enters phone number.
2. Validate phone number.
3. Send OTP if provider available.
4. Show OTP input.
5. User enters OTP.
6. Verify OTP.
7. Create/load session.
8. Load profile.
9. Load roles.
10. Set active role.
11. Continue intent.

OTP UI should include:

* Phone number display
* Edit phone number
* 6-digit input or provider-based length
* Numeric keyboard
* Auto-focus next digit
* Backspace previous digit
* Paste full OTP support
* OTP autofill support
* Resend timer
* Wrong OTP error
* Expired OTP error
* Provider error
* Loading state
* Success state

---

# 14. OTP AUTOFILL RULE

OTP input should support mobile OTP autofill where possible.

Use attributes such as:

```txt id="i74uzo"
autocomplete="one-time-code"
inputMode="numeric"
```

OTP UI should allow:

* SMS code autofill where browser/OS supports it
* Paste full OTP
* Manual entry
* Backspace correction
* Resend OTP

Do not rely only on autofill.

Manual entry must always work.

---

# 15. DEVELOPMENT OTP RULE

During development, OTP cost should be avoided.

Development mode may allow:

* Static OTP
* Random OTP displayed in dev console/admin dev state
* OTP bypass for test users
* Local test auth mode

Example development variables:

```txt id="y792b6"
NEXT_PUBLIC_APP_ENV=development
DEV_AUTH_OTP_ENABLED=true
DEV_AUTH_STATIC_OTP=123456
```

Development OTP rules:

* Only enabled in development.
* Must be disabled in production.
* Must be clearly marked as dev-only.
* Must not expose production bypass.
* Must not be enabled on live website.
* Must not send real SMS when dev mode is active unless intentionally configured.

Production must use real OTP provider.

---

# 16. PRODUCTION OTP RULE

Production OTP must use real provider.

Production rules:

* OTP sent through configured provider.
* OTP verification is real.
* OTP expiry enforced.
* Rate limit OTP sends.
* Rate limit verification attempts.
* Log provider errors safely.
* Do not expose OTP in UI.
* Do not bypass OTP.
* Do not use static OTP.
* Do not allow random OTP success.
* Do not show fake success.

If OTP provider is missing in production:

* Hide phone login, or
* Show setup-required only in admin/dev context, or
* Block auth with clear safe error.

Do not pretend OTP was sent.

---

# 17. PHONE NUMBER RULE

Phone number is primary identity/contact field.

Phone rules:

* Validate Indian phone number format.
* Store normalized format.
* Prevent duplicate active accounts with same phone unless system supports multi-account linking.
* Use phone for OTP login.
* Use phone for lead/contact default.
* Allow user to use profile phone in lead form.
* Allow alternate lead number without overwriting profile.

Phone number should not be publicly exposed unless contact mode allows it.

---

# 18. EMAIL FIELD RULE

Email can be collected but is not primary verification during public register.

Email behavior:

* Email field may be optional during registration.
* User can add/edit email from profile.
* Email can be verified later from profile.
* Email verification can use code or confirmation link.
* Email must not be marked verified until real verification.
* Email login may be enabled later if provider configured.

Do not force email verification before phone OTP unless business decides later.

Do not show fake email verified state.

---

# 19. EMAIL VERIFICATION FROM PROFILE

Email verification flow:

```txt id="hb2ncl"
User opens profile
User adds or edits email
System validates email format
User clicks Verify Email
System sends code/link if email provider configured
User enters code or opens link
System verifies email
Profile email_verified becomes true
```

If email provider missing:

* Show setup-required state in admin/dev context.
* Do not fake email sent.
* Do not mark email verified.

Email verification is separate from phone OTP login.

---

# 20. OPTIONAL EMAIL/PASSWORD LOGIN

Email/password login is optional.

If enabled:

* Show only when provider/auth config exists.
* Validate email.
* Use secure password rules.
* Support forgot password if enabled.
* Use Supabase/Auth provider securely.
* Do not show if disabled.

If disabled:

* Hide email/password login from public UI.

Phone OTP remains primary unless business changes later.

---

# 21. OPTIONAL GOOGLE LOGIN

Google login is optional.

If enabled:

* Show Google login button.
* Use configured OAuth provider.
* On callback, create/load profile.
* If new user, ask role selection before completing onboarding.
* Continue preserved intent.

If Google OAuth is not configured:

* Hide Google button, or
* Show setup-required only in admin/dev context.

Do not show Google login button that does nothing.

Do not fake Google login.

---

# 22. MAGIC LINK

Magic link is optional future feature.

If enabled:

* User enters email.
* System sends magic link.
* User opens link.
* Session created.
* New user completes role selection.
* Existing user continues intent.

If provider missing, hide.

Do not fake magic link sent.

---

# 23. INTENT PRESERVATION RULE

Login/register must preserve user intent.

Restricted actions should continue after auth.

Examples:

## Contact Property

Guest clicks contact.

System opens login/register.

After login:

* Return to same property.
* Continue contact reveal/lead form.
* Do not send randomly to dashboard unless user chose dashboard.

## Save Property

Guest clicks save.

After login:

* Save the property.
* Show success.
* Keep user on same page.

## Post Property

Guest clicks post property.

After register/login:

* Continue to role check.
* If user has owner/broker/agency/builder role, open property post flow.
* If not, ask role upgrade/request.

## Post Requirement

Guest clicks post requirement.

After register/login:

* Continue requirement post flow.
* Buyer/Tenant role preferred.

## Pricing Purchase

Guest clicks plan.

After login:

* Continue selected plan purchase.
* If role mismatch, show role selection/upgrade.

## Banner Ad Purchase

Guest or wrong role clicks banner ad purchase.

After login:

* Check role eligibility.
* If eligible, continue banner ad purchase/submission.
* If not, show role upgrade/agency/group/business role flow.

Do not lose intent.

---

# 24. AUTH INTENT STORAGE

Intent can be stored using:

* URL query parameter
* Session storage
* Server-side pending action
* Auth redirect state
* Temporary intent context

Intent should include:

* Action type
* Route
* Entity ID
* Selected plan ID
* Selected property ID
* Selected requirement ID
* Selected banner ad package
* Search query
* City
* Filters

Intent must not store sensitive data insecurely.

Expired/invalid intent should fail safely.

---

# 25. SESSION PERSISTENCE RULE

After login, user should remain logged in when returning later unless session expires.

Session must persist across:

* Page refresh
* Browser reopen if cookie/session allows
* Return after 2-3 days if within configured session duration

User instruction:

```txt id="opx926"
If I open website after 2-3 days, it should still open logged-in if session time has not expired.
```

Session duration should be Admin/Super Admin configurable if implemented.

---

# 26. SESSION TIMEOUT SETTINGS

Super Admin should control session behavior.

Possible settings:

* Default session duration
* Inactivity timeout
* Remember device duration
* Force re-login after X days
* Max active sessions per user
* Revoke all sessions
* Device/session management
* Staff/admin shorter timeout
* Public user longer timeout
* Suspended user auto-logout
* Banned user auto-logout

If session settings are visible in admin, they must work.

Do not create fake session settings.

---

# 27. DEVICE AND SESSION MANAGEMENT

Optional but recommended:

User profile/security may show:

* Current session
* Logged-in devices
* Last login time
* Logout from all devices
* Revoke device

Admin may view/revoke sessions if permitted.

If device/session list is not implemented, hide it.

Do not show fake device list.

---

# 28. PROFILE CREATION RULE

After successful registration, system must create profile.

Profile should include:

* User ID
* Full name if provided
* Phone
* Email if provided
* Phone verified status
* Email verified status
* Default role
* Active role
* Status
* City if provided
* Language if provided
* Profile completion
* Created date
* Updated date

Profile must not be incomplete in a way that breaks dashboard.

If required fields are missing, show profile completion flow.

---

# 29. ACTIVE ROLE RULE

Every logged-in user must have active role.

Active role controls:

* Header
* Sidebar
* Dashboard route
* Profile sections
* Permissions
* Plan visibility
* Contact actions
* Requirement access
* Lead access
* Banner ad access
* Admin access

Active role must be stored securely.

Do not rely only on client state.

If active role is missing:

* Set default role if available.
* Ask user to choose active role.
* Do not crash.

---

# 30. ROLE SWITCH RULE

If user has multiple approved roles, allow role switch.

Role switch UI may appear in:

* Profile menu
* Dashboard header
* Profile page
* Mobile menu

Role switch should:

* Show available approved roles.
* Show pending roles separately.
* Hide rejected roles or show status.
* Update active role securely.
* Redirect to correct dashboard if needed.
* Update header/sidebar immediately.

Do not allow switching to unapproved role.

---

# 31. ROLE CHANGE / UPGRADE REQUEST ENTRY

If user wants another role, profile should include role request.

Flow:

```txt id="j0oehv"
Profile → Roles → Request New Role → Select Role → Fill Details → Submit → Admin Review
```

This document covers auth entry.

Detailed role change approval behavior belongs to role profile document.

Still, auth must support:

* Pending role status
* Approved role status
* Rejected role status
* Active role switch only after approval
* Admin-created staff roles

---

# 32. ROLE-BASED REDIRECT AFTER LOGIN

After login/register:

Priority:

1. Preserved intent/action
2. Current query/search route
3. Role onboarding/profile completion
4. Role-specific dashboard if user clicked dashboard
5. Homepage

Examples:

Buyer login from homepage:

* Stay homepage or continue search.

Owner register from Post Property:

* Continue property post flow.

Broker login from Requirements Feed:

* Continue requirements feed if plan/permission allows.

Agency login from Banner Ads:

* Continue banner ad dashboard if eligible.

Admin login:

* Go to admin dashboard.

Do not always redirect everyone to generic dashboard.

---

# 33. AUTH STATE IN HEADER

Header must update after auth.

Guest state:

* Show Login/Register

Logged-in state:

* Show avatar/profile icon
* Hide Login/Register
* Show role-aware actions
* Show dashboard/profile menu

Loading auth state:

* Show skeleton or neutral state
* Avoid flickering between login/profile
* Do not show wrong state for long

If session exists, restore logged-in UI.

---

# 34. AUTH STATE IN MOBILE SIDEBAR

Guest sidebar:

* Login/Register card
* City selector
* Public links
* Post Property
* Post Requirement
* Pricing

Logged-in sidebar:

* Avatar
* User name
* Active role
* Profile completion
* Dashboard
* Role-based menu
* Subscription
* Settings
* Logout

After login, sidebar must not continue showing only guest menu.

---

# 35. PROTECTED ROUTE RULE

Protected routes require login.

If guest opens protected route:

* Show login/register popup or full page login.
* Preserve intended route.
* After auth, return if permission allows.

If logged-in user lacks role/permission:

* Show unauthorized state.
* Offer role request if appropriate.
* Offer switch role if user has another role.
* Do not show protected data.

Protected routes include:

* Dashboard routes
* Profile routes
* Saved properties
* Requirements management
* Leads
* Site visits
* Messages
* Billing
* Subscription management
* Banner ad submission
* Admin pages
* Super Admin pages

---

# 36. UNAUTHORIZED STATE

Unauthorized page/state should explain clearly.

Example:

```txt id="bm8ya5"
You do not have permission to access this page.
```

If role upgrade can help:

```txt id="alpg5h"
Request Broker role to access buyer requirements.
```

Actions:

* Go back
* Go home
* Switch role
* Request role
* Contact support

Do not show blank page.

Do not expose protected data.

---

# 37. ACCOUNT STATUS RULE

User account statuses may include:

* Active
* Pending
* Suspended
* Banned
* Deleted
* Archived

If suspended:

* Block protected actions.
* Show account suspended state.
* Allow support contact if appropriate.

If banned:

* Logout or block session.
* Show banned message.
* Do not allow login unless policy allows appeal.

If deleted:

* Block login or handle recovery if implemented.

Account status must be checked server-side.

---

# 38. REGISTERED BUT INCOMPLETE PROFILE

If user registered but profile incomplete:

* Allow basic browsing.
* Prompt profile completion where needed.
* Block actions requiring profile completion if necessary.
* Show profile completion card.
* Do not break session.

Examples:

Owner cannot submit property until required owner details complete.

Broker cannot access full broker tools until broker profile/verification steps complete if required.

Agency cannot submit banner ads until agency profile/plan requirements met if configured.

---

# 39. BUSINESS ROLE VERIFICATION ENTRY

Broker/Agency/Builder may need verification.

Registration should not collect too many business details.

After login, show profile completion/verification flow.

Verification fields may include:

Broker:

* Business name
* Broker photo/logo
* Operating cities
* RERA/license if applicable
* Experience
* Address
* Documents if required

Agency:

* Agency name
* Agency logo
* Office address
* Operating cities
* Agents/team
* Registration documents if required

Builder:

* Builder company name
* Logo
* Projects
* RERA/company docs
* Office address

Detailed fields belong to role profile document.

---

# 40. AUTH UI COMPONENTS

Recommended components:

* AuthProvider
* AuthModal
* AuthTabs
* LoginForm
* RegisterForm
* RoleSelectionCards
* PhoneInput
* OTPInput
* OTPResendTimer
* AuthIntentHandler
* AuthRedirectHandler
* ProviderMissingState
* DevOTPNotice
* ProfileBootstrapper
* ActiveRoleLoader
* ProtectedRouteGuard
* PermissionGuard
* UnauthorizedState
* AccountStatusGuard
* SessionManager
* LogoutButton

Do not create duplicate random auth components.

---

# 41. AUTH MODAL MOBILE UX

Mobile auth modal can be:

* Bottom sheet, or
* Full-screen modal

Recommended:

* Bottom sheet for simple login trigger
* Full-screen for multi-step registration/OTP if needed

Mobile auth must support:

* Back button
* Close button
* Outside tap close where safe
* Large inputs
* Numeric keyboard for phone/OTP
* Sticky CTA
* Clear error messages
* No horizontal scroll
* No cut-off OTP input
* Keyboard-safe layout

---

# 42. AUTH MODAL DESKTOP UX

Desktop auth modal should be centered or right-side panel.

It should include:

* Clear title
* Login/Register tabs
* Phone input
* Role selection for register
* OTP step
* Terms/privacy text
* Close button
* Provider buttons only if configured
* Error states

Do not make desktop auth huge and cluttered.

---

# 43. REGISTER FORM FIELDS

Recommended public register fields:

* Full name
* Mobile number
* Email optional
* Role selection
* City optional
* Terms/privacy acceptance

After role selection, optionally collect very short role-specific data:

Broker:

* Business/broker name optional

Agency:

* Agency name optional

Builder:

* Builder name optional

Full profile details should be completed after login.

Do not make registration too long.

---

# 44. LOGIN FORM FIELDS

Login form fields:

* Mobile number

Optional if email login enabled:

* Email/password tab

Login form should show:

* Register link if not registered
* Forgot password only if email/password enabled
* Terms/privacy note if needed

If mobile number not found:

* Show register prompt.

---

# 45. OTP INPUT STATES

OTP states:

* Empty
* Focused
* Partially filled
* Complete
* Sending
* Sent
* Verifying
* Verified
* Wrong OTP
* Expired OTP
* Resend available
* Resend countdown
* Rate limited
* Provider missing
* Network error
* Dev OTP active

Every state should have clear UI.

---

# 46. RATE LIMITING RULE

OTP must be rate limited.

Rate limits may include:

* Send OTP per phone per time window
* Verify attempts per OTP
* Daily OTP limit
* IP-based abuse limit
* Device/browser limit
* Cooldown before resend

If rate limited, show clear message.

Example:

```txt id="bt4qx7"
Too many OTP attempts. Please try again later.
```

Do not allow unlimited OTP spam.

---

# 47. AUTH SECURITY RULES

Auth must be secure.

Rules:

* Never expose service role key in client.
* Never expose OTP secrets.
* Never store OTP in local storage.
* Never use dev OTP in production.
* Validate phone/email.
* Check account status after login.
* Check active role server-side.
* Use RLS/server checks.
* Protect admin routes.
* Protect role routes.
* Prevent role escalation.
* Prevent subscription self-edit.
* Prevent admin role public registration.
* Log security events if implemented.

---

# 48. SUPABASE AUTH RULE

If using Supabase:

Use separate clients:

* Browser client with anon key
* Server client with user session
* Admin client only server-side

Auth should use:

* Supabase SSR cookie/session handling
* Server-side route protection
* RLS-compatible user queries
* Secure admin operations

Never import service role client into client components.

---

# 49. ENVIRONMENT VARIABLES

Possible environment variables:

```txt id="y64mbr"
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
NEXT_PUBLIC_SITE_URL=

NEXT_PUBLIC_APP_ENV=
DEV_AUTH_OTP_ENABLED=
DEV_AUTH_STATIC_OTP=

OTP_PROVIDER=
OTP_PROVIDER_API_KEY=
OTP_SENDER_ID=

EMAIL_PROVIDER_API_KEY=
EMAIL_FROM=

GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
```

Only public-safe variables can be exposed with `NEXT_PUBLIC_`.

Secrets must remain server-side.

---

# 50. LOGOUT RULE

Logout must:

* Clear session
* Clear active user state
* Clear sensitive cached data
* Redirect safely
* Update header/sidebar to guest state
* Not leave private dashboard visible

Logout options:

* Logout current session
* Logout all devices if implemented

If logout fails, show error.

---

# 51. AUTH NOTIFICATIONS

Notifications may include:

* OTP sent
* Login success
* New device login
* Email verification sent
* Email verified
* Password changed if applicable
* Role request submitted
* Role approved/rejected
* Account suspended
* Account restored

If email/WhatsApp notification provider missing, do not fake external delivery.

In-app notifications can be used if implemented.

---

# 52. AUTH LOADING STATES

Auth loading states:

* Checking session
* Sending OTP
* Verifying OTP
* Creating profile
* Loading roles
* Redirecting
* Logging out
* Loading provider state

Avoid flicker.

Do not briefly show Login/Register if valid session is still loading and can be restored.

Use skeleton/profile placeholder if needed.

---

# 53. AUTH ERROR STATES

Auth errors must be user-friendly.

Examples:

Invalid phone:

```txt id="vfdkc5"
Enter a valid mobile number.
```

Number not registered:

```txt id="orb6wi"
This number is not registered. Please register first.
```

Wrong OTP:

```txt id="cmucl6"
Incorrect OTP. Please try again.
```

Expired OTP:

```txt id="q4d8hp"
OTP expired. Please request a new OTP.
```

Provider missing:

```txt id="vf3e4m"
OTP login is currently unavailable. Please try again later.
```

Account suspended:

```txt id="n7t74u"
Your account is suspended. Contact support for help.
```

Do not show raw technical errors.

---

# 54. AUTH SUCCESS STATES

Success states:

* OTP sent
* Login successful
* Registration successful
* Email verified
* Profile created
* Role selected
* Role request submitted
* Logout successful

Success should not appear before server confirmation.

---

# 55. TERMS AND PRIVACY

Register/login popup should include terms/privacy notice.

Example:

```txt id="wgdv2d"
By continuing, you agree to the Terms and Privacy Policy.
```

Links should work.

If policy pages are not created yet, create or add to CMS/static docs.

Do not use dead links.

---

# 56. ROLE-BASED PLAN DISPLAY AFTER LOGIN

After login, user profile/dashboard should show role-based plan.

Examples:

Buyer:

* Optional buyer/tenant tools if enabled

Owner:

* Owner listing plan

Broker:

* Broker plan with listing/requirement/proposal limits

Agency:

* Agency plan with agents/listings/leads/banner ads access

Builder:

* Builder plan with projects/units/leads/banner ads access

If no plan exists:

* Show free/default plan state if real.
* Show upgrade options.

Do not show fake active subscription.

---

# 57. AUTH AND SUBSCRIPTION CONNECTION

Auth must connect to subscription behavior.

Examples:

Guest clicks plan:

* Login/register first.
* Then purchase selected plan.

User role mismatch:

* Show correct role requirement.

Active plan:

* Show plan in profile/dashboard.

Expired plan:

* Show expired state and upgrade/renew.

Role change with active subscription:

* Show plan impact.
* Do not silently transfer plan unless rules exist.

Detailed subscription logic belongs to subscription document.

---

# 58. AUTH AND BANNER ADS CONNECTION

Banner ads require eligible role and payment/plan.

If guest clicks banner ad purchase:

1. Open auth popup.
2. Register/login.
3. Check role.
4. If role eligible, continue.
5. If role not eligible, show role request/upgrade.
6. Check plan/payment.
7. Continue banner ad submission.

Do not let buyer submit agency banner ad unless business rule allows role upgrade.

---

# 59. AUTH AND LEAD FORM CONNECTION

Lead form should use profile phone if logged in.

If guest contacts:

* Open login/register if mode requires login.
* After login, show lead form with current phone prefilled.
* User can choose alternate number.

If logged-in user uses alternate number:

* Store alternate number in lead.
* Show receiver that alternate number was used.
* Do not overwrite profile phone unless user confirms.

---

# 60. AUTH AND SEO CONNECTION

Public SEO pages must be browseable without login.

Login should only be required for restricted actions:

* Contact
* Save
* Post
* Book visit
* Message
* Dashboard
* Purchase
* Banner submission

Do not block Google users from viewing public SEO pages.

---

# 61. AUTH AND ADMIN AUDIT

Important auth/admin events should be audit logged if implemented:

* Admin creates staff user
* Admin changes role
* Admin approves role request
* Admin rejects role request
* User suspended/banned
* Session revoked
* Super Admin changes auth settings
* Dev OTP setting changed
* Provider settings changed

Audit logs must be real if visible.

---

# 62. AUTH ROUTE MATRIX

Public auth routes:

```txt id="e4mgmh"
/login
/register
/verify-otp
/account-suspended
/account-banned
/unauthorized
```

Profile routes:

```txt id="q1nqzc"
/profile
/profile/edit
/profile/security
/profile/sessions
/profile/verification
/profile/email-verification
/profile/roles
/profile/role-change
/profile/subscription
/profile/notifications
/profile/settings
```

Admin auth route:

```txt id="umk5cx"
/admin/login
```

or equivalent secure admin auth route.

Protected dashboard routes must use route guards.

---

# 63. AUTH DATABASE TABLES

Possible auth-related tables:

* profiles
* roles
* permissions
* role_permissions
* user_roles
* role_upgrade_requests
* user_sessions
* user_devices
* user_verifications
* user_activity_logs
* auth_provider_settings
* login_attempts
* otp_attempts

Detailed schema belongs to database/security document.

This file defines behavior.

---

# 64. AUTH FEATURE FLAGS

Possible feature flags:

```txt id="z6n85g"
auth.phone_otp.enabled
auth.dev_otp.enabled
auth.email_field.enabled
auth.email_verification.enabled
auth.email_password.enabled
auth.google_login.enabled
auth.magic_link.enabled
auth.role_registration.enabled
auth.role_change_request.enabled
auth.session_management.enabled
auth.admin_separate_login.enabled
auth.profile_completion.enabled
auth.business_verification_prompt.enabled
```

If a feature flag is off, hide related UI and block backend action where needed.

---

# 65. AUTH ADMIN SETTINGS

Admin/Super Admin may configure:

* Enabled auth methods
* Dev OTP mode
* OTP provider
* OTP expiry
* OTP resend cooldown
* OTP attempt limit
* Session duration
* Inactivity timeout
* Remember device duration
* Email verification provider
* Public registration enabled/disabled
* Allowed public roles
* Role approval requirement
* Business verification requirement
* Staff invite settings
* Account suspension rules

Visible settings must work.

No fake settings.

---

# 66. AUTH MANUAL VERIFICATION CHECKLIST

Manual verification prompt should verify:

* Guest header shows Login/Register.
* Login/Register popup opens.
* Register tab works.
* Role selection appears.
* Admin/staff roles not visible.
* New phone registration works in dev mode if enabled.
* OTP input works.
* OTP autofill attributes exist if implemented.
* Existing user login works.
* Unknown login number shows register prompt.
* Header changes to profile icon after login.
* Mobile sidebar changes after login.
* Active role loads.
* Role-based dashboard redirect works.
* Protected routes block guest.
* Unauthorized role shows safe state.
* Dev OTP disabled or marked dev-only for production.
* Email verification from profile works or shows provider missing state.
* Logout works.
* Session persists according to settings.

Do not require screenshot/video capture.

---

# 67. AUTH PASS / FAIL RULE

Auth phase is PASS only if:

* Public login/register popup works.
* New user registration includes role selection.
* Admin roles are not visible publicly.
* OTP flow works or provider missing state is safe.
* Dev OTP is development-only.
* Production does not fake OTP.
* Login detects registered user.
* New unregistered number is guided to register.
* Header/sidebar update after login.
* Active role loads.
* Protected routes work.
* Intent preservation works for at least key flows.
* Session persists correctly or settings are documented/implemented.
* No fake provider success.
* Feature registry updated.
* Manual verification completed.

If any public admin role exposure exists, mark FAIL.

If OTP fake success exists in production, mark FAIL.

If logged-in user still sees Login/Register as main action, mark FAIL.

---

# 68. RELATION TO OTHER DOCUMENTS

This document connects to:

* `00_CLAUDE_COMMON_RULES_NO_SKIP_NO_FAKE_TOKEN_LIGHT.md`
* `01_MASTER_PRODUCT_DESIGN_UX_RESPONSIVE_REQUIREMENTS.md`
* `02_FEATURE_PAGE_ROLE_ROUTE_PERMISSION_MATRIX.md`
* `03_PUBLIC_WEBSITE_HOME_HEADER_SIDEBAR_MOBILE_UX_SPEC.md`
* `07_ROLE_BASED_PROFILE_ROLE_CHANGE_APPROVAL_BUSINESS_PROFILE_SPEC.md`
* `10_PROPERTY_CARD_DETAIL_CONTACT_VISIBILITY_LEAD_SPEC.md`
* `11_REQUIREMENT_PROPOSAL_LEAD_SITE_VISIT_MESSAGING_SPEC.md`
* `12_ROLE_DASHBOARDS_OWNER_BROKER_AGENCY_AGENT_BUILDER_SPEC.md`
* `13_ADMIN_SUPER_ADMIN_CONTROL_PANEL_SETTINGS_MODERATION_SPEC.md`
* `15_SUBSCRIPTION_TRIAL_BILLING_PAYMENT_CREDIT_BOOST_SPEC.md`
* `16_PROVIDER_MODES_WHATSAPP_MAP_EMAIL_SMS_OTP_API_SETTINGS_SPEC.md`
* `17_DATABASE_SUPABASE_RBAC_RLS_STORAGE_SECURITY_SPEC.md`
* `22_AI_MANUAL_VERIFICATION_PASS_FAIL_PROMPT_SYSTEM.md`

Use those docs for role profile, provider, subscription and security details.

---

# 69. END OF FILE

This file defines authentication, login, register, OTP, session and role registration rules for My Gujarat Property.

Auth must be popup-first, mobile-first, phone OTP-first, role-aware, secure, no-fake, intent-preserving and separate from admin login.

Nothing from uploaded docs or user chat instructions should be skipped.
