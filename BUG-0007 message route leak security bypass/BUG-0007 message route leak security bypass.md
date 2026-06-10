# Anvil v1.0 FirstPass Security [Auth]: Messenger route leaks broken 404 page to guest URLs instead of transaction redirect

## [Summary]
  When a buyer attempts to bypass transaction requirements by manually typing the messaging URL (`/messages?listingId=[id]`) into the browser's URL address bar for a listing with no active reservation history, the system fails to handle the request or execute a security redirect block. Instead of returning the user to `/listings` with an error message, the application fails to handle the route check and displays a standard 404 Error page.

## [Precondition]
  * Software version: Anvil Production Build v1.0 (Live Test Server)
  * Software configuration: Buyer is logged into an active account; browsing a public food listing that has no historical or active transaction record associated with their profile.
  * Hardware specifications: Universal Desktop/Mobile Browsers (e.g., Google Chrome, Mozilla Firefox)
  * Network configuration: Active internet connection connected to the deployed application domain.

## [Steps to reproduce]
  1. Log into the application using a valid buyer profile.
  2. Locate an active public food listing that your account has never reserved, interacted with, or purchased.
  3. Copy or document the unique ID parameter string belonging to that specific food listing.
  4. Manually type or force paste the parameter-bound link `/messages?listingId=[id]` onto the end of the base domain link string in the browser address bar (replacing `[id]` with the target listing value).
  5. Press Enter to submit the manual navigation request.

## [Actual results]
  The application fails to trigger the transaction binding security rule, leaving the interface in a broken state that displays a generic 404 error page without triggering a redirect or rendering user alert feedback.

## [Expected results]
  The route guard middleware must intercept the unverified chat channel call, verify that no active reservation link exists between the user and the listing ID, block access immediately, force a redirect back to the `/listings` index, and trigger an alert notice: "A transaction is required to message the seller."

## [Additional information]
  See attached screenshot `messenger_404_leak_screenshot.png` in this folder showing the unredirected 404 screen encountered when attempting to manipulate the parameter-bound messenger path directly.

## [Is this Breakage?]
  Yes, existing implementation transaction-bound route architecture is failing.

## [Severity: How does this problem impact the customer/user?]
  4. Serious functional error or flow disruption that hurts user navigation clarity.

## [Likelihood: How often will a customer/user use this feature/function?]
  3. Low-Medium, typically only attempted by advanced users trying to force open chat links.

## [Repeatability: Is this problem easily reproducible?]
  10. 100% Reproducible

## [Impacted Test Cases]
  MSG-0001

## [Impact Sizing (in days)]
  Less than a day