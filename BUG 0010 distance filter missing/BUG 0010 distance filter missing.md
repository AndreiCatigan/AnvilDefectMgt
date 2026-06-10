# Anvil v1.0 FirstPass Functional [Search]: Distance proximity filter missing from listings page

## [Summary]
When a buyer navigates to the public listings page to browse available food items, there is no **distance proximity filter** available anywhere on the interface. Users cannot filter search results based on physical distance from their set location, making it impossible to find listings near them — especially for users in areas with multiple barangays or municipalities.

## [Precondition]
- **Software version:** Anvil v1.0 (Production build on https://anvil-eight.vercel.app)
- **Software configuration:** Buyer's location is set to Baybay (or any location)
- **Hardware specifications:** Universal Desktop/Mobile Browsers
- **Network configuration:** Active internet connection

## [Steps to reproduce]
1. Log in as a buyer (or guest) with location set to Baybay.
2. Navigate to the public `/listings` page.
3. Look for any distance-related filter, dropdown, slider, or input field.
4. Check the filter/sort bar, sidebar, or any advanced search options.

## [Actual results]
- The listings page displays category tabs (All, Baked Goods, Fruits & Vegetables, etc.) and a search bar for "Search surplus food..."
- **No distance filter** (e.g., "Within 5 km", "Within 10 km", "Within 100 km") is present anywhere on the page.
- There is no dropdown, slider, checkbox, or any UI element that allows filtering by proximity.
- Users cannot limit results to nearby listings only.

## [Expected results]
- A distance/proximity filter should be available on the listings page (e.g., dropdown with options: "Within 5 km", "Within 10 km", "Within 25 km", "Within 100 km").
- When "Within 5 km" is selected, only listings within 5 km of the buyer's location should be displayed.
- When "Within 100 km" is selected, listings within 100 km should be displayed.
- The filter should work in combination with category tabs and search keywords.

## [Additional information]
See attached screenshot:
- `listings_page_no_distance_filter.png` — Shows category tabs and search bar, but no distance filter control

**Note:** SRCH-0002 cannot be executed because the required UI component does not exist.

## [Is this Breakage?]
Yes, core search and filtering functionality is completely missing — the distance proximity filter required by SRCH-0002 is not implemented on the frontend, breaking the user's ability to find nearby food listings.

## [Severity]
6. Crash or hang cleared by restart / Severe GUI, usability, and accessibility issue — Critical missing feature that limits the app's core value proposition (connecting nearby surplus food givers and takers).

## [Likelihood]
8. High — Every user searching for listings will need to filter by distance to find relevant nearby items.

## [Repeatability]
10. 100% Reproducible

## [Impacted Test Cases]
- SRCH-0002: Filter by distance proximity (cannot be executed at all)

## [Impact Sizing (in days)]
Less than a day