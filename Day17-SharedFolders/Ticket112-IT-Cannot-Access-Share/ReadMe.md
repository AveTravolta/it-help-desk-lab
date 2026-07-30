## Ticket #112 — IT Cannot Access Shared Folder

### Issue

An IT staff member reported they were unable to access the **CompanyShares** network share from **CLIENT01**. The user received an **Access Denied** message when attempting to open the shared folder.

### Investigation

- Logged into CLIENT01 using the IT user account
- Verified the shared folder was reachable over the network
- Confirmed the issue occurred only when attempting to access the shared folder
- Reviewed Share Permissions on the CompanyShares folder
- Reviewed NTFS Security permissions on the shared folder
- Verified the IT user was a member of the **IT Staff** security group

### Root Cause

The **IT Staff** group had been removed from the NTFS permissions on the shared folder, preventing the user from accessing the files despite having Share Permissions.

### Resolution

- Added the **IT Staff** security group back to the NTFS permissions
- Assigned the **Modify** permission to the IT Staff group
- Verified Share Permissions remained configured correctly
- Applied the updated permissions

### Verification

- Logged back into CLIENT01 as the IT user
- Successfully accessed the **CompanyShares** network share
- Created a test text file to verify write access
- Edited and saved the file successfully
- Confirmed the issue was resolved
