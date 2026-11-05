# Resident App Test Cases (Executed)

These are the manual test cases I executed on the Resident App of a Service Management App during my QA attachment at Kiwami Tech (July 2025). Titles are tidied for readability, and test data is replaced with placeholders.

**Result: 18 executed, 17 passed, 1 failed.**

## Summary

| ID | Title | Type | Requirement | Status | Bug |
|---|---|---|---|---|---|
| TC-001 | Verify successful login with a valid email and password | Positive | REQ-002 | Passed | None |
| TC-002 | Verify navigation to the registration screen | Positive | REQ-006 | Passed | None |
| TC-003 | Verify an error message is displayed on invalid login | Negative | REQ-003 | Passed | None |
| TC-004 | Verify navigation to the forgot password screen | Positive | REQ-004 | Passed | None |
| TC-005 | Verify required fields are validated on the registration form | Negative | REQ-005 | Passed | None |
| TC-006 | Verify navigation from registration to login | Positive | REQ-006 | Passed | None |
| TC-007 | Verify password reset is accepted for a valid registered email | Positive | REQ-007 | Passed | None |
| TC-008 | Verify a password reset email is sent after a reset request | Positive | REQ-008 | **Failed** | BUG-008 |
| TC-009 | Verify user initials are displayed on the home screen after login | Positive | REQ-009 | Passed | None |
| TC-010 | Verify the notification count on the bell icon is correct | Positive | REQ-010 | Passed | None |
| TC-011 | Verify the notifications tab shows a summary of all notifications | Positive | REQ-011 | Passed | None |
| TC-012 | Verify a summary of recent deliveries is shown on the home screen | Positive | REQ-012 | Passed | None |
| TC-013 | Verify a summary of alerts is shown on the home screen | Positive | REQ-013 | Passed | None |
| TC-014 | Verify the welcome note shows the user's name on the home screen | Positive | REQ-014 | Passed | None |
| TC-015 | Verify the latest community updates are shown on the home screen | Positive | REQ-015 | Passed | None |
| TC-016 | Verify the quick action buttons are shown on the home screen | Positive | REQ-016 | Passed | None |
| TC-017 | Verify validation errors when logging in with empty fields | Negative | REQ-001 | Passed | None |
| TC-018 | Verify an error when password and confirmation do not match | Negative | REQ-005 | Passed | None |

## Selected test cases in detail

### TC-001: Verify successful login with a valid email and password

- **Precondition:** The resident has a valid registered account.
- **Steps:**
  1. Launch the Resident App.
  2. Go to the login screen.
  3. Enter a valid registered email.
  4. Enter the correct password.
  5. Tap **Login**.
- **Test data:** Email: `<registered email>`, Password: `<correct password>`
- **Expected:** The user is authenticated and redirected to the home screen.
- **Actual:** Login successful and the resident is redirected to the home screen.
- **Status:** Passed

### TC-003: Verify an error message is displayed on invalid login

- **Precondition:** The app is on the login screen.
- **Steps:**
  1. Launch the app.
  2. Enter an unregistered or invalid email.
  3. Enter an incorrect password.
  4. Tap **Login**.
- **Test data:** Email: `<unregistered email>`, Password: `<incorrect password>`
- **Expected:** The login attempt is denied and an error message is displayed.
- **Actual:** Error message displayed and login blocked.
- **Status:** Passed

### TC-007: Verify password reset is accepted for a valid registered email

- **Precondition:** The user is on the forgot password screen.
- **Steps:**
  1. Launch the Resident App.
  2. Enter a registered email address.
  3. Tap **Reset Password** or **Submit**.
- **Test data:** Email: `<registered email>`
- **Expected:** A confirmation message says the reset link was sent.
- **Actual:** Confirmation message displayed.
- **Status:** Passed

### TC-008: Verify a password reset email is sent after a reset request

- **Precondition:** A password reset was initiated.
- **Steps:**
  1. Launch the Resident App.
  2. Open the registered email inbox.
  3. Check for a password reset email from the app.
- **Test data:** Email: `<registered email>`
- **Expected:** An email arrives within a short time and includes a valid reset link.
- **Actual:** No email received.
- **Status:** **Failed**
- **Defect:** [BUG-008](../bug-reports/BUG-008-password-reset-email-not-received.md)

TC-007 passed and TC-008 failed on the same flow: the app confirms the request, but the email never arrives. That pattern points to a problem after the request is accepted, not in the form.

### TC-017: Verify validation errors when logging in with empty fields

- **Precondition:** The user is on the login screen.
- **Steps:**
  1. Launch the Resident App and continue past the splash page.
  2. Leave both email and password empty.
  3. Tap **Login**.
- **Test data:** None
- **Expected:** A validation error says that email and password are required.
- **Actual:** A validation error message is displayed.
- **Status:** Passed

### TC-018: Verify an error when password and confirmation do not match

- **Precondition:** The user is on the registration screen.
- **Steps:**
  1. Launch the Resident App and continue past the splash page.
  2. Fill in valid details but enter different values in password and confirm password.
  3. Tap **Register**.
- **Test data:** Password: `<password A>`, Confirm password: `<password B>` (different)
- **Expected:** An error says the passwords do not match.
- **Actual:** Error message displayed.
- **Status:** Passed
