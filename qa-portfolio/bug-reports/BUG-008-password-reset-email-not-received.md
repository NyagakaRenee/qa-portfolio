# BUG-008: Password reset email not received after submitting a reset request

| Field | Detail |
|---|---|
| **Bug ID** | BUG-008 |
| **Application** | Service Management App, Resident App |
| **Module / feature** | Authentication, Forgot Password |
| **Environment** | Android, staging |
| **Severity / Priority** | High / High |
| **Reported by** | Renee Nyagaka |
| **Date reported** | 27 July 2025 |
| **Related test case** | TC-008 |
| **Related requirement** | REQ-008 |
| **Status** | Assigned to developer (as recorded in the QA report) |

## Summary

A user who requests a password reset does not receive the reset email, so they cannot recover their account.

## Steps to reproduce

1. Launch the Resident App.
2. Tap **Forgot Password**.
3. Enter a registered email address.
4. Submit the password reset request.
5. Check the email inbox.

## Expected result

A password reset email containing a valid reset link arrives within a short time.

## Actual result

No email is received in the inbox.

## Impact

Users who forget their password cannot recover their account through the app, so they are locked out of the Resident App's features until the reset works. This is why it was rated High severity and High priority.

## Analysis

The app shows a confirmation message after the request (TC-007 passed), but TC-008 shows the email never arrives. This points to a failure after the request is accepted, most likely in the backend email trigger or the email delivery service, rather than in the app's form.

## Traceability

TC-008 → REQ-008 → BUG-008

It was one of the two key issues named in the final QA report, together with broken Terms and Conditions and Privacy Policy links.

## Evidence

Reproduction steps and supporting screenshots were recorded in the team defect log (Google Sheets).

## Suggested next checks

- Confirm the email service is triggered by checking the backend logs for the request.
- Check the spam folder and the delivery status in the email provider.
- Retest with more than one registered address.
