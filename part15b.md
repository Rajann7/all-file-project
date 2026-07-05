PART 15B — MANUAL VERIFICATION PROMPT: UX CONVERSION + PROPERTY TYPE FIELDS + WEBP MEDIA QA

Manually verify PART 15A.

Do not only inspect code. Run the app and test in browser.

Use test roles:

* Guest
* Buyer
* Tenant
* Owner
* Broker
* Agency Owner
* Agency Agent
* Builder
* Admin
* Super Admin

Test device widths:

* 320px
* 360px
* 390px
* 430px
* 768px
* 1366px

GLOBAL CHECKS:

1. No horizontal scroll.
2. No important text wrap.
3. Header does not break.
4. Mobile header shows logo + My Gujarat Property in one line.
5. City selector visible on mobile and desktop.
6. City change updates homepage feed without full page reload.
7. Login/Register hidden after login.
8. Correct role actions show.
9. Wrong role actions hide/block.
10. No fake data.
11. No fake metrics.
12. No fake property cards.
13. No fake verification badges.
14. No fake provider success.
15. No dead buttons.
16. Empty states guide action.
17. Error states explain what happened and next step.
18. Loading states are visible.
19. Back/touch/scroll/drawer behavior is app-like.

HOMEPAGE CHECK:

1. Open homepage as guest.
2. Check search-first layout.
3. Check city selector.
4. Change city.
5. Confirm feed refreshes without reload.
6. Check banner carousel.
7. Confirm no fake banner ad.
8. Check property sections:

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
9. Each section has View All.
10. If no data, section hides or shows real empty state.
11. Mobile carousel usable.

AUTH / REDIRECT CHECK:

1. Click Post Property as guest.
2. Login/Register opens.
3. Intent preserved.
4. Buyer clicking Post Property shows role request/upgrade.
5. Owner/Broker/Agency Owner/Builder can continue to allowed posting.
6. Agency Agent cannot post unless delegated.
7. Admin/Super Admin routes blocked for normal users.

PROPERTY IMAGE UPLOAD CHECK:

1. Open Post Property as eligible role.
2. Go to media upload step.
3. Confirm UI does not show maximum MB text.
4. Confirm UI shows user-friendly guidance.
5. Upload jpg image.
6. Confirm preview appears.
7. Confirm stored/processed image is WebP if implemented.
8. Upload png image.
9. Confirm compressed WebP output if implemented.
10. Upload webp image.
11. Confirm accepted and optimized.
12. Try unsupported format.
13. Confirm friendly error.
14. Try image that cannot process.
15. Confirm friendly processing error.
16. Confirm no raw storage/database error.
17. Set cover image.
18. Reorder images.
19. Remove image.
20. Replace image.
21. Confirm no fake upload success.
22. Confirm upload success only after storage/database record exists.

PROJECT MEDIA CHECK:

1. Login as Builder.
2. Open project posting.
3. Upload project gallery image.
4. Confirm WebP optimization if implemented.
5. Upload floor plan image if implemented.
6. Upload brochure PDF if implemented.
7. Confirm documents are not converted incorrectly.
8. Confirm private documents remain private.

PROPERTY POSTING FLOW CHECK:

1. First step asks listing purpose/type.
2. User does not see huge generic form.
3. Mobile flow is step-based.
4. Sticky Next button works.
5. Back button works.
6. Save Draft works.
7. Preview works.
8. Submit for approval works.
9. Pending property not public.
10. Approved active property appears publicly if approval enabled.
11. Wrong role blocked.
12. User cannot edit another user listing.

RESIDENTIAL FIELD CHECK:
Flat/Apartment:

1. BHK visible.
2. Bathroom visible.
3. Balcony visible.
4. Carpet/built-up/super area visible.
5. Floor/total floors visible.
6. Furnishing visible.
7. Parking visible.
8. Society/project visible.
9. Maintenance visible.
10. Land survey fields hidden.

House/Villa/Bungalow:

1. BHK visible.
2. Plot area if relevant visible.
3. Built-up area visible.
4. Floors visible.
5. Parking/garden/open space visible.
6. Facing/ownership visible.
7. Commercial frontage fields hidden unless relevant.

Studio:

1. Studio type visible.
2. Area/bathroom/furnishing visible.
3. BHK not forced.

Farm House:

1. Land area visible.
2. Built-up area visible.
3. Water/electricity/road access visible.
4. Taluka/village visible if rural.

COMMERCIAL FIELD CHECK:
Shop:

1. Commercial type visible.
2. Frontage visible.
3. Road width visible.
4. Main road/corner visible.
5. Washroom visible.
6. Parking visible.
7. Suitable business visible.
8. BHK hidden.

Office:

1. Area visible.
2. Seats/cabins if implemented visible.
3. Pantry/washroom visible.
4. Lift/parking/power backup visible.
5. BHK hidden.

Showroom:

1. Frontage visible.
2. Ceiling height visible if implemented.
3. Main road/parking visible.
4. BHK hidden.

Warehouse/Godown:

1. Covered area visible.
2. Ceiling height visible.
3. Loading/unloading visible.
4. Truck access/road width visible.
5. Power load visible.
6. BHK hidden.

Industrial Shed/Factory:

1. Plot area visible.
2. Built-up area visible.
3. Power load visible.
4. Shed height visible.
5. Road/truck access visible.
6. Zoning/industrial estate visible if implemented.
7. BHK hidden.

LAND / PLOT FIELD CHECK:
Residential Plot:

1. Plot area visible.
2. Area unit visible.
3. Road width visible.
4. Dimensions visible if implemented.
5. NA status visible.
6. Boundary visible.
7. BHK hidden.
8. Floor hidden.
9. Furnishing hidden.

Agricultural/Farm Land:

1. District visible.
2. Taluka visible.
3. Village visible.
4. Survey/block number if allowed visible.
5. Area in bigha/acre/hectare/guntha visible.
6. Irrigation/water source visible.
7. Electricity visible.
8. Road access visible.
9. Soil/crop if implemented visible.
10. BHK hidden.

Commercial/Industrial Land:

1. Zoning visible.
2. Road width visible.
3. Frontage visible.
4. Power/water visible.
5. BHK hidden.

PG / HOSTEL FIELD CHECK:

1. PG type visible.
2. Gender visible.
3. Sharing type visible.
4. Rent per bed/room visible.
5. Deposit visible.
6. Food included visible.
7. AC/non-AC visible.
8. Attached bathroom visible.
9. Wi-Fi/laundry/housekeeping if implemented visible.
10. Curfew/visitor rules visible.
11. Minimum stay visible.
12. Sale price hidden.
13. BHK not forced.

PROJECT / BUILDER FIELD CHECK:

1. Builder can open project posting.
2. Project type visible.
3. Project name visible.
4. Builder entity visible.
5. Project status visible.
6. Possession date visible.
7. RERA number visible if applicable.
8. RERA verified badge appears only after real verification.
9. Location visible.
10. Project land area visible.
11. Towers/blocks visible.
12. Total floors visible.
13. Total units visible.
14. Unit configurations visible.
15. Price range visible.
16. Area range visible.
17. Amenities visible.
18. Brochure upload works if implemented.
19. Floor plans work if implemented.
20. Project gallery works.
21. Project is not treated as simple single property.

UNIT CONFIGURATION CHECK:

1. Unit type visible.
2. BHK/commercial unit type visible.
3. Carpet/built-up/super area visible.
4. Price visible.
5. Floor plan visible.
6. Availability status visible.
7. Tower/block visible.
8. Sold/booked/hold status works if implemented.

SEARCH / FILTER SYNC CHECK:

1. Residential filters show BHK.
2. Rent filters show rent/deposit/available from.
3. Commercial filters show commercial fields.
4. Land filters show taluka/village/road/NA/zoning.
5. PG filters show gender/sharing/food.
6. Project filters show builder/project/RERA/unit/possession.
7. Irrelevant filters hidden.
8. Visible filters affect results.
9. Non-working filters hidden.

PROPERTY CARD / DETAIL CHECK:

1. Card is type-aware.
2. Residential card shows BHK/area/price.
3. Land card shows land area/unit/type.
4. Commercial card shows commercial type/area.
5. PG card shows rent/sharing/gender.
6. Project card shows project/builder/price range/unit types.
7. Source tag correct.
8. Status correct.
9. Verified badge only if real.
10. Hidden phone not exposed.

DASHBOARD / LEAD / STATUS CHECK:

1. All dashboards have filters.
2. Tables become cards on mobile.
3. Every row/card click opens detail.
4. Lead ID visible in dashboard/admin.
5. Property ID visible in dashboard/admin.
6. Lead status can update.
7. Lead date/time visible.
8. Lead source visible.
9. Alternate number badge works.
10. Notes/follow-up works if implemented.
11. Property status can update where allowed.
12. Status history records change.

30-DAY AVAILABILITY VERIFICATION CHECK:

1. Active listing has last_verified_at if implemented.
2. next_verification_due_at exists if implemented.
3. Due listing shows verification prompt.
4. User can confirm still available.
5. Admin setting/grace logic works if implemented.
6. If scheduled automation missing, mark as BLOCKED/PARTIAL in registry, not fake.

AGENCY CHECK:
Agency Owner:

1. Agents visible.
2. Assign lead works.
3. Reassign works if implemented.
4. Agent permissions visible.
5. Assignment history visible if implemented.

Agency Agent:

1. Assigned leads visible.
2. Assigned visits visible.
3. Agent cannot post property unless delegated.
4. Agent cannot see agency billing unless permission.
5. Agent cannot see all agency leads unless permission.
6. Agent actions are scoped.

ROLE PROFILE CHECK:

1. Buyer profile is buyer-specific.
2. Tenant profile is tenant-specific.
3. Owner profile shows owner data/properties/leads.
4. Broker profile shows broker fields.
5. Agency profile shows agency/team/logo.
6. Agency Agent profile shows assigned agency/permissions.
7. Builder profile shows company/projects/RERA fields.
8. Avatar/logo upload preview works.
9. Crop works or clearly disabled.
10. No fake profile image.

PUBLIC BUSINESS PROFILE CHECK:

1. Broker profile opens.
2. Agency profile opens.
3. Builder profile opens.
4. Real Estate Group profile opens if enabled.
5. Active listings show real data.
6. Verification badge only if real.
7. No fake rating/reviews/awards.

ADMIN CHECK:

1. Normal user cannot access admin.
2. Admin users list has filters.
3. User click opens full detail.
4. Property click opens full detail.
5. Lead click opens full detail.
6. Requirement/proposal/visit filters work.
7. Admin moderation works where allowed.
8. Admin cannot access Super Admin-only settings unless permission.

SUPER ADMIN CHECK:

1. Super Admin dashboard opens.
2. Platform overview visible.
3. Every card/list item click opens details.
4. Provider settings do not expose secrets.
5. Subscription/pricing controls exist or setup-required.
6. Plan/image limits exist if implemented.
7. Banner ad pricing/duration controls exist if enabled.
8. Missing usage/error data shows not-tracked/setup-required, not fake.

SECURITY / NO-FAKE CHECK:

1. Hidden phone not public.
2. Private docs not public.
3. Public reads only approved active public data.
4. Draft/pending/rejected not public.
5. Agent cannot see unrelated leads.
6. Service role key not client-side.
7. Dev OTP only development.
8. No fake payment success.
9. No fake provider success.
10. No fake WebP/upload success.

If anything fails:

1. Mark FAIL or PARTIAL.
2. Fix.
3. Retest.
4. Update Feature Registry.
5. Do not mark PASS until verified.

Output:

## MANUAL VERIFICATION REPORT

### Part Verified

PART 15B — UX Conversion + Property Type Fields + WebP Media QA

### Without Login Check

PASS / FAIL / BLOCKED
Details:

### With Login Check

PASS / FAIL / BLOCKED
Details:

### Homepage Conversion Check

PASS / FAIL / BLOCKED
Details:

### Header / City Selector Check

PASS / FAIL / BLOCKED
Details:

### Property Image Upload UI Check

PASS / FAIL / BLOCKED
Details:

### WebP Compression Check

PASS / FAIL / BLOCKED
Details:

### Property Posting Flow Check

PASS / FAIL / BLOCKED
Details:

### Property Type Field Check

PASS / FAIL / BLOCKED
Details:

### Project / Unit Field Check

PASS / FAIL / BLOCKED
Details:

### Search / Filter Sync Check

PASS / FAIL / BLOCKED
Details:

### Dashboard / Lead Pipeline Check

PASS / FAIL / BLOCKED
Details:

### Property Status / 30-Day Verification Check

PASS / FAIL / BLOCKED
Details:

### Agency Owner / Agency Agent Check

PASS / FAIL / BLOCKED
Details:

### Role-Based Profile Check

PASS / FAIL / BLOCKED
Details:

### Public Business Profile Check

PASS / FAIL / BLOCKED
Details:

### Admin / Super Admin Deep Detail Check

PASS / FAIL / BLOCKED
Details:

### Mobile UI Check

PASS / FAIL / BLOCKED
Details:

### Database / RLS / Security Check

PASS / FAIL / BLOCKED
Details:

### No-Fake UI / No-Fake Data Check

PASS / FAIL / BLOCKED
Details:

### Bugs Found

[List]

### Fixes Applied

[List]

### Retest Result

PASS / FAIL / BLOCKED

### Feature Registry Update

[List]

### Final Status

PASS / PARTIAL / FAIL / BLOCKED

NOTE: PLEASE DO NOT DELET FAKE USER, PROPERTY , DETAILES ECT IN DEVELOPMENT TIME