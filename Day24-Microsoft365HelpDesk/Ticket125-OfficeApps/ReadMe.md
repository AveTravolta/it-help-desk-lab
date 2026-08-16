## Ticket #125 — I Don't Have Office Apps

### Issue

User reported that they did not have access to the Microsoft Office applications.

### Investigation

- Checked Mike Johnson's Microsoft 365 account
- Verified that Mike had a Microsoft 365 Business Standard license assigned
- Checked the license service settings and found that Office for the Web and Microsoft 365 Apps were not enabled

### Root Cause

The Microsoft 365 Business Standard license was assigned, but the Office for the Web and Microsoft 365 Apps services were not enabled for the user.

### Resolution

- Enabled Office for the Web
- Enabled Microsoft 365 Apps
- Had Mike log out of Microsoft 365 and log back in

### Verification

- Mike logged back into Microsoft 365
- Confirmed that the Office applications were now available
- Issue resolved successfully
