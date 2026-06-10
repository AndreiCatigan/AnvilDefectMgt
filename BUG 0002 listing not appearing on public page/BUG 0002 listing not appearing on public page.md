# Anvil v1.0 FirstPass Functional [Listing Creation]: Published listing visible in seller dashboard but absent from public listings page

## [Summary]
 When a seller successfully publishes a new food listing (e.g., "Fresh Sourdough Bread" under "Baked Goods" category), the listing is visible in the seller's management dashboard but does not appear on the public /listings page under any tab — including the "All" tab and the "Baked Goods" category tab. Instead, the page shows "No listings found".



## [Precondition]
  * Software version: Anvil Production Build v1.0 (Live Test Server)
  * Software configuration: User is logged in as a seller with listing permissions
  * Hardware specifications: Universal Desktop/Mobile Browsers (e.g., Google Chrome, Mozilla Firefox)
  * Network configuration: Active internet connection connected to the deployed application domain

## [Steps to reproduce]
  1. Log in as a seller with listing permissions.
  2. Navigate to the listing creation page.
  3. Enter valid details:
    - Title: "Fresh Sourdough Bread"
    - Category: "Baked Goods"
    - Price: 80
    - Quantity: 3
    - Expiration Date: 3 days in future
    - Storage: "Ambient (Room Temp)"
    - Location: "C. Arellano Street, Baybay, Leyte"
    - Plus Code: "7Q26MRH2+8J"
    - Image: Upload a valid image
  4. Click "Publish Listing".
  5. Verify redirection to `/listings` after success message.
  6. Observe the public listings page under the "All" tab.
  7. Click on the "Baked Goods" category tab.

## [Actual results]
  - The listing "Fresh Sourdough Bread" **does not appear** under the "All" tab (only existing older listings like Sardines, Rebisco, Juice are shown).
  - The listing **does not appear** under the "Baked Goods" tab — the page shows "No listings found in Baked Goods".
  - However, the listing **is visible** in the seller's management dashboard (Active tab) with status "Active" and quantity 3/3.

## [Expected results]
  - The newly published "Fresh Sourdough Bread" listing should appear under the **"All" tab** alongside existing listings.
  - The listing should also appear under the **"Baked Goods" category tab** with the price ₱80.

## [Additional information]
See attached screenshots:
- `seller_dashboard_showing_listing.png` — Listing visible in seller management
- `public_listings_all_tab.png` — Listing missing from All tab (only 4 old listings shown)
- `public_listings_baked_goods_tab.png` — Shows "No listings found in Baked Goods"

## [Is this Breakage?]
 Yes, see previous code tested

## [Severity: How does this problem impact the customer/user?]
6. Crash or hang cleared by restart / Severe GUI, usability, and accessibility issue — Core marketplace functionality (displaying listings) is broken; sellers cannot surface their items to buyers.  
## [Likelihood: How often will a customer/user use this feature/function?]
8. High — Every new listing created by any seller will fail to appear on the public page.

## [Repeatability: Is this problem easily reproducible?]
  10. 100% Reproducible

## [Impacted Test Cases]
  - LIST-0001: Add new food listing

## [Impact Sizing (in days)]
  Less than a day