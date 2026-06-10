# Anvil v1.0 FirstPass Functional [Listing Edit]: Edited listing remains invisible on public listings page

## [Summary]
When a seller edits an active listing (e.g., "Fresh Sourdough Bread") to update Price (80 → 60), Quantity (3 → 2), and Description, the changes are successfully saved in the backend and reflected in the seller's management dashboard. However, the listing **still cannot be seen on the public `/listings` page** under any tab (All, Baked Goods, etc.) — because the underlying visibility issue documented in BUG-0002 remains unresolved.

## [Precondition]
- **Software version:** Anvil v1.0 (Production build on https://anvil-eight.vercel.app)
- **Software configuration:** Seller is logged in with an active listing "Fresh Sourdough Bread"
- **Hardware specifications:** Universal Desktop/Mobile Browsers (Chrome, Firefox, Safari)
- **Network configuration:** Active internet connection to the deployed application

## [Steps to reproduce]
1. Log in as a seller with an active listing "Fresh Sourdough Bread" (Price: 80, Quantity: 3).
2. Navigate to `/listings/manage` and locate "Fresh Sourdough Bread".
3. Click "Edit" button.
4. Modify the listing values:
   - Price: 60
   - Quantity: 2
   - Description: "Fresh bread, price reduced for quick pickup!"
5. Click "Update Listing".
6. Observe the success message confirming the update.
7. Navigate to the public `/listings` page as a buyer or guest.
8. Check the "All" tab and the "Baked Goods" category tab.

## [Actual results]
- The edit operation returns a success message and the seller dashboard shows the updated values (₱60, quantity 2).
- However, the listing **does not appear** on the public `/listings` page at all — not under "All" tab, not under "Baked Goods" tab.
- The page only displays older existing listings (Sardines, Rebisco, Juice, etc.).
- Since the listing is invisible, buyers cannot see the updated price or quantity anyway.

## [Expected results]
- The edited listing should appear on the public `/listings` page under the "All" tab and the "Baked Goods" category tab.
- The listing detail page should display the updated price (₱60), updated quantity (2), and modified description.
- Buyers should be able to see the updated listing immediately after edit.

## [Additional information]
See attached screenshots:
- `seller_dashboard_showing_listing_edited.png` — Listing visible in seller management
- `public_listings_all_tab.png` — Listing missing from All tab (only 4 old listings shown)
- `public_listings_baked_goods_tab.png` — Shows "No listings found in Baked Goods"

## [Is this Breakage?]
Yes, see previous code tested — this is the same root issue as BUG-0002


## [Severity]
6. Crash or hang cleared by restart / Severe GUI, usability, and accessibility issue — Core marketplace functionality is broken; sellers cannot surface any listings (original or edited) to buyers.

## [Likelihood]
8. High — Every listing created or edited by any seller will never appear on the public page.

## [Repeatability]
10. 100% Reproducible

## [Impacted Test Cases]
- LIST-0001: Add new food listing
- LIST-0002: Edit food listing details

## [Impact Sizing (in days)]
Less than a day