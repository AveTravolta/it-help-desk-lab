## Ticket #115 – Cannot Modify Shared Folder

### Issue

User started Client01 and logged on. They were able to access the Sales shared folder but could not modify files.

### Investigation

* Verified the user
* Verified the account was enabled
* Verified the user was logged into the domain
* Confirmed the user was a member of the Sales Staff group
* Checked the permissions assigned to the Sales Staff group

### Root Cause

The user was a member of the Sales Staff group, but the group was not granted the appropriate **NTFS Modify permission** on the Sales folder.

### Resolution

* Coordinated with Sales Staff management to confirm that the Sales Staff group should have Modify permissions
* Granted the Sales Staff group **Modify** NTFS permissions on the Sales folder

### Verification

* Had the user log out and log back in
* Confirmed the user could access the Sales shared folder
* Confirmed the user could successfully create a new file
