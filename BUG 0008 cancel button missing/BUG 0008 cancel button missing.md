# Anvil v1.0 FirstPass Functional [Listing Cancel]: Cancel/Deactivate button missing from listings management table

## [Summary]
When a seller navigates to `/listings/manage` to manage their active food listings, there is no **"Cancel / Deactivate Listing"** button available for any listing. Sellers are unable to deactivate or remove their listings from the marketplace, leaving them with no control over which items remain visible to buyers.

## [Precondition]
- **Software version:** Anvil v1.0 (Production build on https://anvil-eight.vercel.app)
- **Software configuration:** Seller is logged in and has active food listings
- **Hardware specifications:** Universal Desktop/Mobile Browsers
- **Network configuration:** Active internet connection

## [Steps to reproduce]
1. Log in as a seller with active food listings (e.g., "Banana" or "Fresh Sourdough Bread").
2. Navigate to `/listings/manage`.
3. Observe the listings management table.
4. Look for a "Cancel", "Deactivate", or "Delete" button/option for any listing.

## [Actual results]
- The `/listings/manage` table displays columns for: TITLE, STATUS, PRICE, QTY, PICKUP, and an "Edit" button.
- **No "Cancel / Deactivate Listing" button** is present anywhere in the table row.
- There is no alternative method (e.g., dropdown menu, three dots, trash icon) to deactivate or remove a listing.
- Sellers can only "Edit" listings, but cannot cancel or deactivate them.

## [Expected results]
- Each listing row in `/listings/manage` should have a **"Cancel / Deactivate Listing"** button or equivalent action (e.g., trash icon, "Deactivate" link).
- Clicking the button should trigger a confirmation pop-up modal.
- After confirmation, the listing status should be set to Inactive/Deactivated.
- The listing should be removed from the management table and no longer visible to buyers.

## [Additional information]
See attached screenshot:
- `listings_manage_table.png` — Shows management table with columns: TITLE, STATUS, PRICE, QTY, PICKUP, and only "Edit" — no cancel/deactivate button

**Note:** The "Edit" button is present and functional, but there is no way to deactivate or cancel a listing.

## [Is this Breakage?]
Yes, core listing management functionality is completely missing — sellers have no means to deactivate or cancel their listings, violating the requirement that sellers should be able to remove unwanted items from the marketplace.

## [Severity]
6. Crash or hang cleared by restart / Severe GUI, usability, and accessibility issue — Sellers cannot control their inventory; stale or unwanted listings remain visible indefinitely.

## [Likelihood]
8. High — Every seller with active listings will need to deactivate or cancel items at some point.

## [Repeatability]
10. 100% Reproducible

## [Impacted Test Cases]
- LIST-0003: Cancel food listing (cannot be executed at all)

## [Impact Sizing (in days)]
Less than a day