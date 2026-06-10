# Anvil v1.0 FirstPass Functional [Validation]: Past expiration date accepted without error message

## [Summary]
When creating a new food listing, selecting an expiration date that is in the past (e.g., yesterday's date) does not trigger any validation error. The system accepts the past date and allows the user to proceed with publishing, which could lead to expired listings being created immediately.

## [Precondition]
- **Software version:** Anvil v1.0 (Production build on https://anvil-eight.vercel.app)
- **Software configuration:** Seller is logged in with listing permissions
- **Hardware specifications:** Universal Desktop/Mobile Browsers
- **Network configuration:** Active internet connection

## [Steps to reproduce]
1. Log in as a seller with listing permissions.
2. Navigate to the listing creation page.
3. Fill in Title: "Bananas"
4. Set Price: 20
5. Set Expiration Date: **Choose yesterday's date** (a date in the past)
6. Fill in other required fields with valid data (Category, Quantity, Storage, Location, Image).
7. Click "Publish Listing".

## [Actual results]
- The expiration date field accepts the past date without any validation error.
- No error message is displayed (e.g., "Expiration date cannot be in the past").
- The user can successfully publish the listing with an already-expired expiration date.

## [Expected results]
- Frontend validation should reject past expiration dates.
- An explicit error message should appear: **"Expiration date cannot be in the past."**
- The "Publish Listing" button should be blocked until a valid future date is selected.

## [Additional information]
See attached screenshot:
- `past_expiration_date_accepted.png` — Listing form showing yesterday's date with no validation error

## [Is this Breakage?]
Yes, core listing validation constraints are being bypassed on the frontend form.

## [Severity]
4. Crash or hang cleared by reload / Severe GUI, usability, and accessibility issue — Allows creation of already-expired listings, causing poor user experience and inventory confusion.

## [Likelihood]
6. Moderate — Users may accidentally select a past date, especially if typing manually.

## [Repeatability]
10. 100% Reproducible

## [Impacted Test Cases]
- LIST-0004: Listing validation checks (Scenario 1, Step 2)

## [Impact Sizing (in days)]
Less than a day