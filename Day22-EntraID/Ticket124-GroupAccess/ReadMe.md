## Ticket #124 – Group Access

### Issue

Mike Johnson called me and stated “I was moved to the IT department, but I can't access the resources my coworkers can.”

### Investigation

* Verified the employee Mike Johnson by department and email address.
* Verified Mike Johnson is still employed and that there were no account restrictions preventing access.
* Using Entra ID I found the User Mike Johnson.
* Checked Mike Johnson's group memberships and found that he was not a member of any groups.
* Checked Mike Johnson's licenses and found that he did not have a Microsoft 365 license assigned.

### Resolution Steps

* Assigned Mike Johnson the same Microsoft 365 license used by the other users in the environment.
* Created a Security Group named **IT-HelpDesk**.
* Added Mike Johnson as a member of the **IT-HelpDesk** group.
* Verified that Mike Johnson was a member of the IT-HelpDesk group and had the appropriate Microsoft 365 license assigned.

### Root Cause

* Mike Johnson was not a member of an appropriate IT group and did not have a Microsoft 365 license assigned to his account.

### Verification

* Mike Johnson's Microsoft 365 license was successfully assigned.
* Mike Johnson was successfully added to the IT-HelpDesk group.
* User account and group membership were verified in Microsoft Entra ID.
