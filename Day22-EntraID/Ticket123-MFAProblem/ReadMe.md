## Ticket #123 – MFA Problem

### Issue

Sarah called me and stated “I can sign into Microsoft 365 with my password, but it is asking me for MFA and I can’t get past it.”

### Investigation

* Verified the employee Sarah Sherman by department and email address.
* Verified Sarah Sherman is still employed and that there were no account restrictions preventing access.
* Using Entra ID I found the User Sarah Sherman.
* Checked Sarah Sherman's authentication methods and found that there were no usable authentication methods registered.

### Resolution Steps

* Using Entra ID I generated a Temporary Access Pass (TAP) for Sarah Sherman.
* Provided the Temporary Access Pass to the user through an approved secure method.
* Provided Sarah with the secure registration instructions.
* Sarah used the Temporary Access Pass to register an authentication method for MFA.

### Root Cause

* Sarah Sherman did not have a usable authentication method registered on her account.

### Verification

* Sarah Sherman successfully registered an authentication method.
* Sarah Sherman confirmed that she was able to complete MFA authentication.
