## Ticket #116 – Printer Offline

### Issue

User reported that the Sales Printer showed as “offline” and they were unable to print.

### Investigation

* Verified the user
* Verified the user account was enabled
* Verified the user was logged into the domain
* Confirmed the user was a member of the Sales Staff group
* Checked the permissions assigned to the Sales Staff group on the Sales Printer

### Root Cause

The user was a member of the Sales Staff group, but the group was not granted the appropriate **Print** permission on the Sales Printer.

### Resolution

* Coordinated with Sales Staff management to confirm that the Sales Staff group should have Print permission on the Sales Printer
* Granted the Sales Staff group **Print** permission on the Sales Printer

### Verification

* Had the user log out and log back into Client01
* Confirmed the Sales Printer was accessible to the user
* Submitted a test print job successfully
* Confirmed the user had the appropriate Print permission on the Sales Printer
