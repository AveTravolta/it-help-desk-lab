# 🖥️ Day 19 — Week 3 Help Desk Shift

## 📋 Overview

Day 19 simulated a real-world **Level 1 Help Desk shift** using the Windows Server and Active Directory lab environment built throughout Week 3.

Instead of introducing a large amount of new technology, the focus was on applying previously learned skills to realistic Help Desk scenarios.

The day focused on:

* 🔎 Troubleshooting before making changes
* 👥 Active Directory user and group management
* 🔐 NTFS and Share permissions
* 🖨️ Printer permissions and troubleshooting
* 📁 Shared folder access
* 🛡️ Least privilege
* 🧩 Security group-based access
* 🔑 Password resets and account lockouts
* 📝 Professional ticket documentation
* ✅ Verifying that fixes actually worked

---

# 🎯 Objectives

By the end of Day 19, the goal was to demonstrate the ability to:

* Investigate common Level 1 Help Desk issues
* Identify the root cause before applying a fix
* Troubleshoot Active Directory user access
* Troubleshoot Share and NTFS permissions
* Use security groups instead of assigning permissions directly to users
* Apply least-privilege principles
* Troubleshoot printer access
* Reset passwords and unlock user accounts
* Verify successful resolutions
* Document Help Desk tickets professionally

---

# 🖥️ Lab Environment

| Component          | Configuration                    |
| ------------------ | -------------------------------- |
| Domain             | `sandoval.local`                 |
| Domain Controller  | `DC01`                           |
| Client             | `Client01`                       |
| Server OS          | Windows Server 2022              |
| Client OS          | Windows 11                       |
| Directory Services | Active Directory Domain Services |
| DNS                | Windows DNS Server               |
| DHCP               | Windows DHCP Server              |
| Virtualization     | VirtualBox                       |

---

# 📚 Week 3 Review

Day 19 began with a review of the concepts covered during Days 14–18.

## 🔹 Day 14 — PowerShell Basics

Reviewed PowerShell commands used for Windows administration and troubleshooting.

Commands reviewed included:

```powershell
Get-Help
Get-Command
Get-Service
Get-Process
Get-ChildItem
Get-Location
Set-Location
```

The review reinforced how PowerShell can be used to investigate Windows systems and perform administrative tasks without relying exclusively on graphical tools.

---

## 🔹 Day 15 — Active Directory with PowerShell

Reviewed using PowerShell to manage and investigate Active Directory.

Commands reviewed included:

```powershell
Get-ADUser
Set-ADUser
Get-ADGroup
Search-ADAccount
Export-Csv
```

Example:

```powershell
Get-ADUser -Filter "Enabled -eq 'False'"
```

The review reinforced using PowerShell to search, filter, modify, and report on Active Directory objects.

---

## 🔹 Day 16 — File Shares & NTFS Permissions

Reviewed:

* NTFS permissions
* Share permissions
* Security groups
* Permission inheritance
* Least privilege
* Effective access
* Read permissions
* Modify permissions
* Deny permissions

A major concept reinforced was that **Share and NTFS permissions work together to determine effective access**.

Permissions were assigned through security groups rather than directly to individual users whenever possible.

---

## 🔹 Day 17 — Shared Folders & Network Shares

Reviewed troubleshooting for shared folder access.

The lab environment included department-based folders such as:

```text
C:\CompanyShares
├── HR
├── IT
├── Sales
└── Finance
```

Access was managed using Active Directory security groups.

The troubleshooting process involved checking:

1. User account
2. Account status
3. Domain authentication
4. Group membership
5. Share permissions
6. NTFS permissions
7. Effective access

---

## 🔹 Day 18 — Print Services & Network Drives

Reviewed printer and mapped network drive administration.

Topics included:

* Printer sharing
* Printer permissions
* Print queues
* Print Spooler
* Printer drivers
* Network printer access
* UNC paths
* Mapped network drives
* Group Policy Drive Mapping
* `gpupdate`
* Create vs. Update drive mappings
* Logoff/logon verification

Example network drive:

```text
H:
\\DC01\HR
```

---

# 🎫 Help Desk Ticket Queue

Day 19 consisted of five simulated Level 1 Help Desk tickets.

| Ticket   | Issue                       | Primary Skills                        |
| -------- | --------------------------- | ------------------------------------- |
| 🎫 #115  | Cannot Modify Shared Folder | NTFS Permissions                      |
| 🖨️ #116 | Printer Offline             | Printer Permissions                   |
| 👤 #117  | User Needs Access           | Security Groups / Least Privilege     |
| 🔐 #118  | Wrong Permissions           | Share + NTFS Permissions              |
| 🔑 #119  | Password Reset              | Active Directory / Account Management |

---

# 🎫 Ticket #115 — Cannot Modify Shared Folder

## Issue

User was able to access the Sales shared folder but could not modify files.

## Investigation

* Verified the user
* Verified the account was enabled
* Verified the user was logged into the domain
* Confirmed the user was a member of the Sales Staff group
* Checked the permissions assigned to the Sales Staff group
* Investigated the NTFS permissions on the Sales folder

## Root Cause

The Sales Staff group was not granted the appropriate **NTFS Modify permission** on the Sales folder.

## Resolution

* Confirmed that Sales Staff should have Modify access
* Granted the Sales Staff group **Modify** NTFS permissions on the Sales folder

## Verification

* Had the user log out and log back into Client01
* Confirmed the user could access the Sales shared folder
* Confirmed the user could create a new file
* Confirmed the user could modify files

---

# 🖨️ Ticket #116 — Printer Offline

## Issue

User reported that the Sales Printer showed as “offline” and they were unable to print.

## Investigation

* Verified the user
* Verified the user account was enabled
* Verified the user was logged into the domain
* Confirmed the user was a member of the Sales Staff group
* Checked the permissions assigned to the Sales Staff group on the Sales Printer

## Root Cause

The Sales Staff group did not have the appropriate **Print permission** on the Sales Printer.

## Resolution

* Confirmed with Sales Staff management that the group should have Print permission
* Granted the Sales Staff group **Print** permission on the Sales Printer

## Verification

* Had the user log out and log back into Client01
* Confirmed the Sales Printer was accessible to the user
* Submitted a test print job successfully
* Confirmed the user had the appropriate Print permission

> **Lab Note:** The lab does not contain a physical printer, so physical printing could not be verified. The test confirmed that the user could access the shared printer and submit a print job.

---

# 👤 Ticket #117 — User Needs Access

## Issue

An HR Staff user requested Modify access to the Sales shared folder.

## Investigation

* Verified the user
* Verified the user was logged into the domain
* Confirmed the user was a member of the HR Staff group
* Checked the user's existing permissions to the Sales folder
* Confirmed management approved the user's request for Sales folder access
* Verified that the user only needed access to the Sales folder occasionally

## Root Cause

The user was a member of the HR Staff group, which did not have access to the Sales folder.

Adding the user directly to the Sales Staff group would have provided unnecessary access beyond their requirements.

## Resolution

A dedicated security group was created to provide controlled access:

```text
HRtoSales
```

The following changes were made:

* Created the `HRtoSales` security group
* Added John Smith to the `HRtoSales` group
* Granted `HRtoSales` **NTFS Modify** permission on the Sales folder
* Granted `HRtoSales` appropriate **Share Change** permission on the Sales share

This provided the user with the required access without granting unnecessary Sales Staff permissions.

## Verification

* Had the user log out and log back into Client01
* Confirmed the user could access the Sales shared folder
* Confirmed the user could create a new text file
* Confirmed the user had the required Modify access

---

# 🔐 Ticket #118 — Wrong Permissions

## Issue

User from the Sales Staff group could access the Sales folder but could not modify files.

## Investigation

* Verified the user
* Verified the user was logged into the domain
* Confirmed the user was a member of the Sales Staff group
* Checked the NTFS permissions assigned to Sales Staff on the Sales folder
* Checked the Share permissions assigned to Sales Staff on the Sales share

## Root Cause

The Sales Staff group had **NTFS Modify** permission on the Sales folder.

However, the Share permission was only configured as **Read**, which restricted the user's effective access when accessing the folder through the network share.

## Resolution

Changed the Sales Staff Share permission from:

```text
Read
```

to:

```text
Change
```

The NTFS Modify permission remained in place.

## Verification

* Had the user log out and log back into Client01
* Confirmed the user could access the Sales shared folder
* Confirmed the user could create a new text file
* Confirmed the user could modify and save files

---

# 🔑 Ticket #119 — User Password Reset

## Issue

User reported that they were unable to log in because they had forgotten their password.

## Investigation

* Verified the user's identity by confirming their department and manager
* Verified the correct user account
* Verified the user was attempting to log into the domain
* Checked the user's account status
* Confirmed the account was locked

## Root Cause

The user was unable to log in because they had forgotten their password, resulting in their account becoming locked out.

## Resolution

* Reset the user's password to a temporary password
* Unlocked the user's account
* Required the user to create a new password at their next login

## Verification

* Had the user log in using the temporary password
* Confirmed the user was prompted to create a new password
* Had the user log in again using the newly created password
* Confirmed the user could successfully access their domain account

---

# 🧠 Key Lessons Learned

## 🔐 Share vs. NTFS Permissions

A user's effective access to a shared folder can be affected by both:

```text
Share Permissions
        +
NTFS Permissions
        ↓
Effective Access
```

For example:

```text
Share → Read
NTFS → Modify

Effective Network Access → Read
```

This was demonstrated directly during Ticket #118.

---

## 👥 Group-Based Permissions

Permissions should generally be assigned to **security groups**, rather than directly to individual users.

Example:

```text
User
 ↓
Security Group
 ↓
Resource
```

This makes access easier to manage and revoke.

---

## 🛡️ Least Privilege

Ticket #117 demonstrated that simply adding a user to an existing department group isn't always the best solution.

Instead of:

```text
HR User
   ↓
Sales Staff
   ↓
Full Sales Staff Access
```

a dedicated group was created:

```text
HR User
   ↓
HRtoSales
   ↓
Limited Approved Access
   ↓
Sales Folder
```

This allowed the user to receive only the access required for their job responsibilities.

---

## 🖨️ Printer Permissions

Users require appropriate printer permissions to submit print jobs to shared printers.

The Sales Staff group was given:

```text
Print
```

rather than unnecessary administrative permissions such as:

```text
Manage Printers
Manage Documents
```

This reinforced the principle of least privilege.

---

## 🔑 Account Lockouts & Password Resets

Password-related tickets require more than simply changing a password.

The technician should:

1. Verify the user's identity
2. Verify the correct account
3. Check account status
4. Check for account lockout
5. Reset the password if appropriate
6. Unlock the account if necessary
7. Verify successful login

---

# 🧪 Troubleshooting Methodology

Day 19 reinforced the following Help Desk troubleshooting process:

```text
USER REPORTS PROBLEM
        ↓
GATHER INFORMATION
        ↓
VERIFY USER / ACCOUNT
        ↓
INVESTIGATE
        ↓
FORM A HYPOTHESIS
        ↓
TEST
        ↓
IDENTIFY ROOT CAUSE
        ↓
APPLY FIX
        ↓
VERIFY
        ↓
DOCUMENT
        ↓
ESCALATE IF NECESSARY
```

The focus was on **investigating before making changes** rather than immediately applying a suspected fix.

---

# 📸 Lab Evidence

Screenshots from Day 19 can include:

* Active Directory user and group membership
* `Sales Staff` security group
* `HRtoSales` security group
* Sales folder NTFS permissions
* Sales folder Share permissions
* Sales Printer configuration
* Sales Printer permissions
* Successful Sales folder access
* Successful file creation/modification
* PowerShell AD administration
* Password reset/account management

---

# 🛠️ Technologies & Tools Practiced

* Windows Server 2022
* Windows 11
* Active Directory Domain Services
* Active Directory Users and Computers
* PowerShell
* NTFS Permissions
* Share Permissions
* Security Groups
* File Shares
* UNC Paths
* Printer Sharing
* Printer Permissions
* Print Spooler
* Group Policy
* Mapped Network Drives
* Windows Help Desk Troubleshooting

---

# 📈 Skills Demonstrated

By completing Day 19, I demonstrated practical experience with:

* ✅ Active Directory account troubleshooting
* ✅ Security group management
* ✅ Group-based permissions
* ✅ NTFS permission troubleshooting
* ✅ Share permission troubleshooting
* ✅ Effective access troubleshooting
* ✅ Least-privilege access design
* ✅ Shared folder troubleshooting
* ✅ Printer permission troubleshooting
* ✅ Password resets
* ✅ Account unlocks
* ✅ PowerShell administration
* ✅ Help Desk ticket investigation
* ✅ Root-cause identification
* ✅ Resolution verification
* ✅ Professional ticket documentation

---

# 🏆 Day 19 Completion

### Learning & Review

* [x] Reviewed PowerShell fundamentals
* [x] Reviewed Active Directory PowerShell
* [x] Reviewed NTFS and Share permissions
* [x] Reviewed shared folder troubleshooting
* [x] Reviewed printer administration
* [x] Reviewed mapped network drives

### Help Desk Tickets

* [x] Ticket #115 — Cannot Modify Shared Folder
* [x] Ticket #116 — Printer Offline
* [x] Ticket #117 — User Needs Access
* [x] Ticket #118 — Wrong Permissions
* [x] Ticket #119 — User Password Reset

### Documentation

* [x] Investigated each ticket before making changes
* [x] Identified root causes
* [x] Applied appropriate resolutions
* [x] Verified fixes
* [x] Documented each ticket professionally

---

# 🎯 Day 19 Takeaway

Day 19 focused on transitioning from **learning individual technologies** to applying them as a Help Desk technician.

The primary lesson was that effective IT support isn't simply about knowing which button to click.

A technician needs to:

> **Investigate the problem, understand the environment, identify the root cause, apply the least-invasive appropriate fix, verify the result, and document the work.**

This lab provided hands-on practice troubleshooting **Active Directory, permissions, shared folders, printers, user access, and account issues** in a simulated enterprise environment.
