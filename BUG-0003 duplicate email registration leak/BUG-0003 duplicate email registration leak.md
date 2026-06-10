# Anvil v1.0 FirstPass UI [Auth]: Registration accepts duplicate email instead of showing "Email already in use" error

## [Summary]
  When a user attempts to sign up with an email address that already exists in the database, the registration form fails to catch the duplicate entry or throw a validation error. Instead of remaining on the `/sign-up` page and displaying "Email already in use", the system triggers a false success state and moves to a verification screen stating "We sent a verification link to email@example.com."

## [Precondition]
  * Software version: Anvil Production Build v1.0 (Live Test Server)
  * Software configuration: User is logged out on the registration screen; an active account with the email "john.doe@example.com" already exists in the system database.
  * Hardware specifications: Universal Desktop/Mobile Browsers (e.g., Google Chrome, Safari)
  * Network configuration: Connected to the deployed app domain with database connectivity.

## [Steps to reproduce]
  1. Open the web browser and navigate directly to the registration page (`/sign-up`).
  2. Input data using the already registered email:
     - Name: Jane Doe
     - Email: john.doe@example.com
     - Password: Password456!
     - Location: Mahaplag, Leyte
  3. Click the "Create Account" or "Sign up free" submission button.

## [Actual results]
  The registration form submits successfully, moves the user away from the entry inputs, and displays a false verification screen text: "Check your email. We sent a verification link to john.doe@example.com. Click it to activate your account." No error banner appears.

## [Expected results]
  The submission should be blocked immediately. The application must display a clear validation error text stating "Email already in use," preserve the form inputs, and keep the user on the `/sign-up` page without sending false authentication prompts.

## [Additional information]
  See attached screenshot `verification_screen_leak.png` showing the application displaying the email verification screen for a pre-existing email identity instead of rejecting the submission.

## [Is this Breakage?]
  Yes, core account authentication constraints are being bypassed on the frontend layout.

## [Severity: How does this problem impact the customer/user?]
  4. Serious functional error or flow disruption that hurts user navigation clarity.

## [Likelihood: How often will a customer/user use this feature/function?]
  6. High, users frequently forget they have accounts and try to sign up again with the same email.

## [Repeatability: Is this problem easily reproducible?]
  10. 100% Reproducible

## [Impacted Test Cases]
  USER-0002

## [Impact Sizing (in days)]
  Less than a day