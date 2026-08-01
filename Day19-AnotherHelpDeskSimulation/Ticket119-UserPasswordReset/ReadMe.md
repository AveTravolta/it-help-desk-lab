## Ticket #119 – User Password Reset

### Issue

User reported that they were unable to log in because they had forgotten their password.

### Investigation

* Verified the user's identity by confirming their department and manager
* Verified the correct user account
* Verified the user was attempting to log into the domain
* Checked the user's account status and confirmed the account was locked

### Root Cause

The user was unable to log in because they had forgotten their password, resulting in their account being locked out.

### Resolution

* Reset the user's password to a temporary password
* Unlocked the user's account
* Required the user to create a new password at their next login

### Verification

* Had the user log in using the temporary password
* Confirmed the user was prompted to create a new password
* Had the user log in again using the newly created password
* Confirmed the user could successfully access their domain account
