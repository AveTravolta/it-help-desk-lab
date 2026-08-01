## Ticket #118 – Wrong Permissions

### Issue

User from the Sales Staff group could access the Sales folder but could not modify files.

### Investigation

* Verified the user
* Verified the user was logged into the domain
* Confirmed the user was a member of the Sales Staff group
* Checked the NTFS permissions assigned to the Sales Staff group on the Sales folder
* Checked the Share permissions assigned to the Sales Staff group on the Sales share

### Root Cause

The user was a member of the Sales Staff group, which had **NTFS Modify** permission on the Sales folder. However, the Sales Staff group only had **Read** Share permission, which prevented the user from modifying files through the shared folder.

### Resolution

* Changed the Share permission for the Sales Staff group from **Read** to **Change**

### Verification

* Had the user log out and log back into Client01
* Confirmed the user could access the Sales shared folder
* Confirmed the user could create a new text file
* Confirmed the user could modify and save files within the Sales shared folder
