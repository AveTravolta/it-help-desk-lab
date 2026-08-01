# Week 3 Reflection — IT Help Desk / Cloud Admin Lab

## Overview

During Week 3 of this lab, I moved beyond basic Active Directory administration and began working with more advanced Windows Server and Help Desk administration tasks.

The focus of this week was learning how to manage Windows environments more efficiently, troubleshoot resource access issues, and apply permissions in a way that reflects real-world IT support practices.

I worked with:

* PowerShell
* Active Directory administration
* NTFS permissions
* Share permissions
* File shares
* Security groups
* Printer services
* Network drives
* Group Policy
* Help Desk ticket workflows

The week ended with a simulated Level 1 Help Desk shift where I applied these skills to realistic user support scenarios.

---

# What I Built & Configured

During Week 3, I expanded the existing Windows Server environment by creating and managing:

* PowerShell-based Active Directory administration workflows
* Department-based file shares
* NTFS permissions
* Share permissions
* Security groups for resource access
* Shared printers
* Printer permissions
* Network drive mappings
* Group Policy-based drive deployment
* Additional Help Desk ticket scenarios

The lab environment now more closely resembles a small business Windows environment where users have different levels of access to shared company resources.

---

# Skills Practiced

## PowerShell Administration

One of the biggest areas of growth this week was learning how PowerShell can be used to administer Windows and Active Directory environments.

I practiced:

* Navigating PowerShell
* Discovering commands
* Using PowerShell help and syntax information
* Working with the PowerShell pipeline
* Managing Windows services
* Retrieving Active Directory users
* Filtering Active Directory accounts
* Modifying user attributes
* Creating Active Directory users
* Enabling and disabling accounts
* Resetting passwords
* Exporting Active Directory information to CSV

Commands practiced included:

```powershell
Get-Command
Get-Help
Get-Service
Get-Process
Get-ChildItem
Get-Location
Set-Location
Get-ADUser
Set-ADUser
New-ADUser
Enable-ADAccount
Disable-ADAccount
Set-ADAccountPassword
Search-ADAccount
Export-Csv
```

This helped me understand how administrators can use PowerShell to perform repetitive tasks more efficiently and create reports that would be difficult to produce manually through a GUI.

---

# Active Directory Administration

I expanded my Active Directory administration skills by working with user accounts and security groups through PowerShell.

I practiced:

* Searching for users
* Filtering users based on account properties
* Checking account status
* Creating user accounts
* Modifying user information
* Enabling and disabling accounts
* Resetting passwords
* Unlocking accounts
* Managing group membership
* Exporting account information

I also completed a simulated Help Desk ticket involving a disabled Active Directory account.

This helped reinforce the connection between Active Directory administration and real-world user support.

---

# File Shares & NTFS Permissions

Another major focus of Week 3 was learning how Windows manages access to shared files and folders.

I created department-based file shares and worked with:

* HR
* IT
* Sales
* Finance

I practiced assigning access through security groups rather than individual users.

I also worked with NTFS permissions including:

* Read
* Modify
* Full Control
* Permission inheritance
* Explicit permissions
* Deny permissions

One of the most important lessons was understanding that permissions need to be evaluated in the context of the user's group memberships and the resource being accessed.

---

# Share Permissions vs. NTFS Permissions

Week 3 helped me better understand the difference between Share Permissions and NTFS Permissions.

I learned that both permission layers can affect a user's effective access when accessing a resource through a network share.

For example:

```text
Share Permission → Read
NTFS Permission  → Modify

Effective Network Access → Read
```

I applied this knowledge directly while troubleshooting Help Desk tickets.

This became especially important during Ticket #118, where the user had NTFS Modify permissions but was still unable to modify files because their Share permission was limited to Read.

---

# Least Privilege & Security Groups

One of the most valuable lessons from Week 3 was learning that simply giving a user access is not always the correct solution.

During Ticket #117, an HR employee required occasional Modify access to the Sales folder.

Instead of adding the user directly to the Sales Staff group, I created a dedicated security group:

```text
HRtoSales
```

The user was then added to that group, and the group was granted the appropriate permissions.

This created a structure like:

```text
HR User
   ↓
HRtoSales
   ↓
Sales Folder
   ↓
Modify
```

This reinforced several important IT administration principles:

* Use security groups to manage access
* Avoid assigning permissions directly to users
* Follow least-privilege principles
* Give users only the access required for their job
* Make access easier to manage and revoke

---

# Printer Administration

I also expanded the lab into Windows printer administration.

I practiced:

* Creating shared printers
* Sharing printers from the server
* Configuring printer permissions
* Assigning Print permissions to security groups
* Troubleshooting printer access
* Understanding printer-related Help Desk tickets

I learned that printer access can also be controlled through security groups and that users should generally receive only the permissions necessary to perform their job.

Because the lab does not contain a physical printer, printer testing was limited to the Windows configuration, shared printer access, permissions, and print job submission.

---

# Network Drives & Group Policy

I practiced configuring network resources that users can access through mapped drives.

I worked with:

* UNC paths
* Network shares
* Drive letters
* Group Policy Preferences
* Drive mapping
* User-based resource deployment

For example:

```text
H:
\\DC01\HR
```

I also practiced troubleshooting drive mapping problems involving:

* Group Policy
* Security filtering
* User group membership
* Drive mapping actions
* `gpupdate`
* User logoff/logon

This helped connect the concepts of **Active Directory groups, Group Policy, and file server resources**.

---

# Help Desk Troubleshooting

The final part of Week 3 was a simulated Help Desk shift.

Instead of simply following instructions, I had to investigate problems and determine the appropriate resolution.

The tickets completed were:

### 🎫 Ticket #115 — Cannot Modify Shared Folder

Identified an NTFS permission issue and corrected the Sales Staff group's Modify permissions.

### 🖨️ Ticket #116 — Printer Offline

Identified an issue with Sales Staff printer permissions and corrected the group's Print permission.

### 👤 Ticket #117 — User Needs Access

Created the `HRtoSales` security group to provide an HR user with limited, approved access to the Sales folder.

### 🔐 Ticket #118 — Wrong Permissions

Identified that NTFS allowed Modify access while Share permissions only allowed Read access.

Corrected the Share permission from Read to Change.

### 🔑 Ticket #119 — User Password Reset

Verified the user's identity, investigated the account status, reset the password, unlocked the account, and verified successful authentication.

---

# Challenges Faced

One of the biggest challenges this week was understanding how multiple permission systems interact.

At first, it can be easy to look at a user's NTFS permissions and assume that those permissions completely determine access.

Working through the lab demonstrated that this isn't always the case.

I had to consider:

```text
User
 ↓
Group Membership
 ↓
Share Permissions
 ↓
NTFS Permissions
 ↓
Effective Access
```

I also encountered situations where something appeared correctly configured but still didn't work.

For example, during Ticket #117, the `HRtoSales` group had the correct NTFS permissions but could not initially access the Sales share because the Share permissions had not been configured for the new group.

This reinforced the importance of checking the **entire access path** instead of assuming that one permission setting tells the whole story.

---

# Biggest Takeaways

The biggest lesson from Week 3 was learning to **investigate before making changes**.

Instead of immediately changing something because a user reports a problem, I practiced asking:

* Who is the user?
* What are they trying to access?
* What access should they have?
* What access do they currently have?
* What groups are they members of?
* What permissions are assigned?
* Where is the restriction occurring?
* What is the root cause?
* What is the least-privileged solution?
* How can I verify the fix?

This changed the way I approached Help Desk tickets.

The goal isn't simply to make the error disappear.

The goal is to understand **why the problem happened**, fix the underlying issue, and verify that the user has the appropriate access afterward.

---

# Documentation & Ticket Management

Week 3 also strengthened my ability to document technical work professionally.

Each Help Desk ticket followed the same workflow:

```text
Issue
↓
Investigation
↓
Root Cause
↓
Resolution
↓
Verification
```

This made the tickets easier to understand and created a record of:

* What the user reported
* What was investigated
* What caused the problem
* What was changed
* How the resolution was verified

I learned that good documentation is an important part of IT support because another technician should be able to understand what happened without having to repeat the entire investigation.

---

# Career Connection

Week 3 helped bridge the gap between basic Help Desk knowledge and more advanced Systems Administration concepts.

The skills practiced this week are directly relevant to entry-level IT roles involving:

* Help Desk Support
* Desktop Support
* IT Support
* Systems Administration
* Windows Administration
* Identity and Access Management
* Cloud Support

The biggest improvement was becoming more comfortable thinking about IT problems from the perspective of **access, identity, permissions, and troubleshooting methodology** rather than simply following a set of instructions.

---

# Week 3 Summary

Week 3 represented a significant progression in this project.

I moved from primarily managing individual Active Directory objects into managing **how users interact with shared enterprise resources**.

I practiced:

* PowerShell administration
* Active Directory management
* Security group management
* NTFS permissions
* Share permissions
* File shares
* Printer permissions
* Network drives
* Group Policy
* Least-privilege access
* Help Desk troubleshooting
* Professional ticket documentation

Most importantly, I began approaching problems more like an IT support technician:

> **Investigate first. Identify the root cause. Apply the appropriate fix. Verify the result. Document the work.**

The next phase of the lab will continue building on these Windows and Help Desk fundamentals while moving toward **Systems Administration and Cloud Administration**.
