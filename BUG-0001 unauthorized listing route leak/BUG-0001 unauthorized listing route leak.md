# Anvil v1.0 FirstPass Security [Auth]: Route leak allows guests to access broken 404 listing page instead of sign-in redirect

## [Summary]
  When an unauthenticated guest user attempts to access the protected layout route `/listings/new` directly through the browser's URL address bar, the system fails to execute an authentication check redirect. Instead of pointing the user to `/sign-in` with an alert message, the application breaks execution and displays a standard 404 Error page.

## [Precondition]
  * Software version: Anvil Production Build v1.0 (Live Test Server)
  * Software configuration: User is entirely logged out / operating as a guest session
  * Hardware specifications: Universal Desktop/Mobile Browsers (e.g., Google Chrome, Mozilla Firefox)
  * Network configuration: Active internet connection connected to the deployed application domain

## [Steps to reproduce]
  1. Open a fresh browser window in incognito mode to clear active session tokens.
  2. Direct the browser interface URL link field to the application's base deployment address.
  3. Ensure that the session states show no profile or user context is logged into the client framework.
  4. Manually type or copy `/listings/new` onto the end of the base domain link string in the browser address bar.
  5. Press Enter to submit the navigational call.

## [Actual results]
  The application fails to trigger an authentication check mechanism, leaving the user on the route space while rendering a generic 404 page error without redirection flags or user alert feedback panels.

## [Expected results]
  The security middleware engine must intercept the unauthorized route declaration, reject access to the template layout container, force a redirect script back to the `/sign-in` screen, and show a clear error toast: "Authentication required to list food items."

## [Additional information]
  See attached screenshot `404_error_screenshot.png` in this folder documenting the application route mismatch context rendering an unredirected 404 screen when a guest enters the target link space.

## [Is this Breakage?]
  Yes, existing implementation security block is failing.

## [Severity: How does this problem impact the customer/user?]
  4. Serious functional error or flow disruption that hurts user navigation clarity.

## [Likelihood: How often will a customer/user use this feature/function?]
  4. Medium, common method for users to manually bookmark or share listing forms.

## [Repeatability: Is this problem easily reproducible?]
  10. 100% Reproducible

## [Impacted Test Cases]
  SEC-0001

## [Impact Sizing (in days)]
  Less than a day