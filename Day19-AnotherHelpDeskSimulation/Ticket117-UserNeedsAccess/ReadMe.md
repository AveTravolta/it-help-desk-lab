## Ticket #117 – User Needs Access

### Issue

User from the HR Staff group requested Modify access to the Sales shared folder.

### Investigation

* Verified the user
* Verified the user was logged into the domain
* Confirmed the user was a member of the HR Staff group
* Checked the user's existing permissions to the Sales folder
* Confirmed management approved the user's request for Sales folder access
* Verified that the user only needed access to the Sales folder occasionally

### Root Cause

The user was a member of the HR Staff group, which did not have access to the Sales folder. Since the user only required occasional Modify access, adding them to the Sales Staff group would have provided unnecessary access beyond their requirements.

### Resolution

* Created a new security group named `HRtoSales` for approved HR users who require occasional access to the Sales folder
* Added John Smith to the `HRtoSales` group
* Granted the `HRtoSales` group the appropriate **NTFS Modify** permission on the Sales folder
* Granted the `HRtoSales` group the appropriate **Share Change** permission on the Sales share

### Verification

* Had the user log out and log back into Client01
* Confirmed the user could access the Sales shared folder
* Confirmed the user could create a new text file in the Sales folder
* Confirmed the user had the required Modify access
