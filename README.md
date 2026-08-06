# 🖥️ IT Help Desk / Cloud Admin Lab (Active Directory & Windows Server)

## Overview

This repository documents a hands-on IT support and systems administration lab designed to simulate a small business enterprise environment.

The goal of this project is to build practical experience with **Windows Server, Active Directory, DNS, DHCP, user administration, Group Policy, troubleshooting, and help desk ticket resolution** through realistic scenarios.

The lab environment uses **Windows Server Active Directory Domain Services (AD DS)** and a Windows client machine to practice common entry-level IT tasks performed by Help Desk Technicians and System Administrators.

---

## 🎯 Goals

- Build and manage a Windows Server domain environment
- Configure and administer Active Directory Domain Services (AD DS)
- Create and manage users, organizational units, and security groups
- Configure and troubleshoot DNS and DHCP services
- Manage and troubleshoot Group Policy Objects (GPOs)
- Practice real-world Help Desk troubleshooting scenarios
- Document issues using an IT ticket workflow:
  - Issue
  - Investigation
  - Root Cause
  - Resolution
  - Verification
- Develop foundational skills for Help Desk, Systems Administration, and Cloud Support roles

---

## Why This Project

This lab was created to bridge the gap between theoretical IT knowledge and practical experience by simulating common enterprise support scenarios.

The environment focuses on skills commonly used by Help Desk Technicians, Junior System Administrators, and Cloud Support professionals.

---

## 🧱 Lab Environment

- Virtualization: VirtualBox
- Domain Controller: DC01
- Client Machine: Client01 (Windows 11)
- Server OS: Windows Server
- Domain: sandoval.local

### Installed Roles:
- Active Directory Domain Services (AD DS)
- DNS Server
- DHCP Server

---

# 📅 Lab Progress

## Day 1 – Environment Setup

Completed:
- Installed VirtualBox
- Downloaded Windows Server ISO
- Created DC01 virtual machine
- Installed Windows Server OS

---

## Day 2 – Domain Controller & Active Directory Setup

Completed:
- Installed Active Directory Domain Services
- Promoted server to Domain Controller
- Created domain: sandoval.local
- Installed and configured DNS
- Verified domain functionality

---

## Day 3 – Active Directory Users + Groups (Help Desk Core)

Completed:
- Created Organizational Unit:
  - Employees

Created Active Directory users:
- Lennet Naranjo
- Robert Naranjo
- Pickles Pugsley
- Michael Sandoval

Created security groups:
- Management
- Pro Shop Staff
- Inventory Staff

Completed troubleshooting scenarios:
- Password reset
- Group membership correction

---

## Day 4 – Windows 11 Domain Join

Completed:
- Joined Client01 workstation to the sandoval.local domain
- Verified domain authentication
- Tested user logins

---

## Day 5 – DNS Configuration & Troubleshooting

Completed:
- Reviewed DNS fundamentals:
  - Name resolution
  - DNS role in Active Directory
  - Client DNS configuration

Completed troubleshooting scenario:
- Identified and corrected incorrect DNS configuration
- Verified client communication with Domain Controller

---

## Day 6 – Help Desk Ticket Simulation

Completed:
- Practiced real-world Help Desk ticket documentation
- Created and resolved simulated user issues:

Tickets completed:
- Account Lockout
- Password Reset
- Disabled User Account
- DNS Issue
- Group Membership Issue

Documented each ticket using:
- Issue
- Investigation
- Root Cause
- Resolution
- Verification

---

## Day 7 – Portfolio Documentation & Lab Review

Completed:

- Reviewed previous Active Directory configurations
- Verified:
  - Users
  - Security groups
  - Organizational Units
  - DNS configuration
  - Domain join functionality

Updated project documentation:

- Organized GitHub repository structure
- Added lab reflections
- Improved project presentation for portfolio use

---

## Day 8 – Password Reset & Account Lockout Troubleshooting

Completed:

- Reviewed Active Directory password management
- Configured and tested account lockout policies
- Practiced common Help Desk account issues

Completed troubleshooting scenarios:

- Locked user account
- Verified account lockout behavior
- Reset user passwords
- Unlocked user accounts
- Verified successful login after resolution

Documented troubleshooting workflow:

- Issue
- Investigation
- Root Cause
- Resolution
- Verification

---

## Day 9 – Group Policy Management

Completed:

- Created and configured Group Policy Objects (GPOs)
- Applied centralized user settings through Active Directory

Created policies:

- Wallpaper Policy
  - Applied desktop wallpaper settings to Golf Employees OU

- Control Panel Restriction Policy
  - Disabled Control Panel access for Inventory users

Completed troubleshooting scenario:

- Investigated GPO application failure
- Reviewed:
  - Organizational Unit placement
  - GPO links
  - Security Filtering
  - GPO permissions

Resolved issue:

- Corrected Security Filtering configuration
- Restored required Authenticated Users permissions
- Verified successful policy application using:

```cmd
gpupdate /force
gpresult /r
```

---

## Day 10 – DHCP Server Configuration & Troubleshooting

Completed:

- Installed and configured the DHCP Server role on Windows Server
- Authorized DHCP within Active Directory
- Created and configured a DHCP scope
- Configured DHCP options:
  - Default Gateway
  - DNS Server
  - Domain Name

Created DHCP scope:

- IP Range:
  - 10.1.10.100 - 10.1.10.200

Created DHCP exclusion range:

- 10.1.10.100 - 10.1.10.109

Verified DHCP functionality:

- Configured Client01 to obtain an IP address automatically
- Used `ipconfig /all` to verify DHCP lease information
- Confirmed Client01 successfully received:

  - IPv4 Address: 10.1.10.110
  - DHCP Server: 10.1.10.2
  - DNS Server: 10.1.10.2

Completed troubleshooting scenario:

- Simulated DHCP failure by deactivating the DHCP scope
- Released the client IP address using:

```cmd
ipconfig /release
```

- Attempted to renew the DHCP lease using:

```cmd
ipconfig /renew
```

- Verified Client01 received an APIPA address (`169.254.x.x`) due to DHCP unavailability

Resolved issue:

- Reactivated the DHCP scope
- Renewed the client lease
- Verified Client01 successfully received a valid DHCP address again

---

# Day 11 – Help Desk Troubleshooting Tickets

Completed:

- Simulated real-world user support incidents
- Investigated and resolved issues involving:
  - DNS
  - Active Directory accounts
  - Group Policy

Documented troubleshooting using:

- Issue
- Investigation
- Root Cause
- Resolution
- Verification

---

## Completed Tickets

### 🎫 Ticket #101 — DNS Failure

Scenario:

- User could not access network resources after restarting Client01
- User received an error related to locating a logon server

Troubleshooting completed:

- Verified client connectivity to DC01
- Reviewed network configuration using:

```cmd
ipconfig /all
```

Identified:

- Incorrect preferred DNS server configuration

Resolution:

- Restored Client01 DNS settings to use:

```text
10.1.10.2
```

Verification:

- Confirmed communication with DC01
- Verified DNS resolution using:

```cmd
nslookup sandoval.local
```

---

### 🎫 Ticket #102 — User Account Disabled

Scenario:

- User attempted to log into Client01
- User received an account disabled message

Troubleshooting completed:

- Opened Active Directory Users and Computers
- Located affected user account
- Confirmed account was disabled

Resolution:

- Enabled the user account
- Required password change after login verification

Verification:

- Confirmed successful authentication
- Confirmed user password change completed successfully

---

### 🎫 Ticket #103 — Group Policy Issue

Scenario:

- User noticed the system clock was missing from the Windows notification area

Troubleshooting completed:

- Verified the issue on Client01
- Reviewed local taskbar settings
- Generated Group Policy Results report:

```cmd
gpresult /h report.html
```

Identified applied GPO:

- Control Panel Restrictions

Identified policy:

```text
Remove the clock from the system notification area
```

Resolution:

- Updated the Group Policy Object
- Disabled the unwanted clock removal setting
- Forced policy refresh:

```cmd
gpupdate /force
```

Verification:

- User logged out and back into Client01
- Confirmed system clock was restored

---

---

# Day 12 – Help Desk Ticket Simulation & Documentation

Completed:

- Converted previous Active Directory troubleshooting tasks into professional Help Desk ticket documentation
- Practiced documenting incidents using a real-world support workflow:
  - Issue
  - Investigation
  - Root Cause
  - Resolution
  - Verification

Created and documented simulated user support tickets:

---

## 🎫 Ticket #104 — Password Reset Request

Scenario:

- User forgot their password and was unable to log into their workstation

Troubleshooting completed:

- Located user account in Active Directory Users and Computers (ADUC)
- Verified user identity:
  - Name
  - Department
  - Manager
- Confirmed account was not locked
- Confirmed account was not disabled

Resolution:

- Reset user password
- Enabled password change requirement at next login
- Verified successful authentication

---

## 🎫 Ticket #105 — Account Unlock Request

Scenario:

- User was unable to access their domain account after multiple failed login attempts

Troubleshooting completed:

- Located user account in Active Directory Users and Computers (ADUC)
- Verified user identity
- Confirmed account lockout status
- Confirmed account was enabled

Resolution:

- Unlocked user account
- Reset user password
- Required password change at next login
- Verified successful workstation login

---

## 🎫 Ticket #106 — Group Membership Issue

Scenario:

- User could not access Inventory Staff resources despite being the department manager

Troubleshooting completed:

- Reviewed user's Active Directory group memberships
- Compared current group memberships against expected department access requirements
- Identified missing Inventory Staff security group membership

Resolution:

- Added user to Inventory Staff security group
- Had user log out and sign back in to refresh security token and apply updated group membership

Verification:

- User confirmed access to required Inventory Staff resources

---

---

## Day 12 Skills Practiced

- Enterprise troubleshooting workflow
- DNS troubleshooting
- Active Directory authentication troubleshooting
- Group Policy verification
- Client/server communication testing
- Incident documentation
- Root cause analysis
- Help Desk escalation process

---

---

## Day 14 – PowerShell Basics

Completed:

- Introduced PowerShell as an administration tool for Windows environments
- Reviewed the difference between Command Prompt and PowerShell
- Practiced navigating the PowerShell environment
- Learned how PowerShell uses commands, parameters, and objects
- Began transitioning from GUI-based administration into command-line management

Practiced basic PowerShell commands:

```powershell
Get-Command
```

Used to discover available PowerShell commands.

```powershell
Get-Help
```

Used to learn command usage and available parameters.

```powershell
Get-Process
```

Used to view running processes on the system.

```powershell
Get-Service
```

Used to view Windows services and their current status.

Practiced filtering and displaying specific information:

```powershell
Get-Process | Select Name
```

Learned PowerShell pipeline concepts:

```text
Command output → Pipeline → Next command
```

Practiced using PowerShell to:

- Retrieve system information
- Search available commands
- View running services
- Understand object-based output
- Navigate administrative tasks without relying only on GUI tools

Skills practiced:

- PowerShell fundamentals
- Command discovery
- Help documentation usage
- Pipeline basics
- Windows administration through command line

---

## Day 15 – Active Directory PowerShell Administration

Completed:

- Learned how to manage Active Directory using PowerShell instead of relying only on Active Directory Users and Computers (ADUC)
- Reviewed the Active Directory PowerShell module
- Practiced retrieving, searching, filtering, modifying, and managing Active Directory user accounts
- Learned how PowerShell improves efficiency, reporting, and automation for system administrators

Verified the Active Directory PowerShell module:

```powershell
Get-Module ActiveDirectory -ListAvailable
```

Imported the Active Directory module:

```powershell
Import-Module ActiveDirectory
```

Explored available Active Directory commands:

```powershell
Get-Command -Module ActiveDirectory
```

Located user management commands:

```powershell
Get-Command *ADUser*
```

Practiced working with common Active Directory cmdlets:

- `Get-ADUser`
- `Set-ADUser`
- `New-ADUser`
- `Enable-ADAccount`
- `Disable-ADAccount`
- `Set-ADAccountPassword`

Attempted to use PowerShell help:

```powershell
Get-Help Get-ADUser
```

The lab environment did not have downloadable PowerShell help content installed because the server does not have internet access.

Used built-in syntax information instead:

```powershell
Get-Command Get-ADUser -Syntax
```

Practiced retrieving Active Directory users:

```powershell
Get-ADUser -Filter *
```

Displayed user names:

```powershell
Get-ADUser -Filter * | Select Name
```

Displayed usernames:

```powershell
Get-ADUser -Filter * | Select Name,SamAccountName
```

Retrieved a specific user:

```powershell
Get-ADUser -Identity username
```

Viewed additional Active Directory attributes:

```powershell
Get-ADUser -Identity username -Properties *
```

Learned that Active Directory user objects contain many attributes including:

- Username
- Department
- Office
- City
- Job Title
- Account Status
- Logon Information

Practiced filtering Active Directory users:

```powershell
Get-ADUser -Filter "Enabled -eq 'False'"
```

Learned PowerShell filtering structure:

```text
Property + Operator + Value
```

Examples:

```text
Enabled -eq 'True'
Department -eq 'IT'
City -eq 'Long Beach'
```

Modified Active Directory user attributes using:

```powershell
Set-ADUser
```

Used `-WhatIf` to preview changes before applying modifications:

```powershell
Set-ADUser username -City "Long Beach" -WhatIf
```

Modified user attributes including:

- City
- Office
- Department
- Job Title

Verified changes:

```powershell
Get-ADUser username -Properties *
```

Created a new Active Directory user account through PowerShell:

```powershell
New-ADUser -Name "PowerShell User" -GivenName "PowerShell" -Surname "User" -SamAccountName psuser -UserPrincipalName psuser@sandoval.local -AccountPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) -Enabled $true
```

Verified the account:

```powershell
Get-ADUser psuser
```

Practiced Active Directory account management:

Disabled an account:

```powershell
Disable-ADAccount psuser
```

Verified account status:

```powershell
Get-ADUser psuser -Properties Enabled
```

Re-enabled the account:

```powershell
Enable-ADAccount psuser
```

Verified:

```powershell
Get-ADUser psuser -Properties Enabled
```

Reset user passwords using PowerShell:

```powershell
Set-ADAccountPassword psuser -Reset -NewPassword (ConvertTo-SecureString "NewPassword123!" -AsPlainText -Force)
```

Created Active Directory reports by filtering users and exporting results to CSV:

```powershell
Get-ADUser -Filter "Enabled -eq 'False'" | Select Name,SamAccountName,Enabled | Export-Csv C:\UsersDisabled.csv -NoTypeInformation
```

This demonstrated a common administrative workflow:

- Retrieve Active Directory objects
- Filter based on object properties
- Select relevant information
- Export results for reporting

---

## 🎫 Ticket #110 — User Unable to Log In

Scenario:

- User **Max Homa** reported being unable to log into their workstation
- The workstation indicated that the user's Active Directory account was disabled

Troubleshooting completed:

- Verified the user's identity in Active Directory
- Reviewed user properties using PowerShell ISE
- Confirmed the account was disabled

Checked account status:

```powershell
Get-ADUser maxhoma -Properties Enabled
```

Root Cause:

- User account was accidentally disabled during account cleanup

Resolution:

Enabled the user account using PowerShell:

```powershell
Enable-ADAccount maxhoma
```

Verification:

```powershell
Get-ADUser maxhoma -Properties Enabled
```

Confirmed:

- Account status changed to enabled
- User access was restored successfully

---

## Day 15 Skills Practiced

- Active Directory PowerShell administration
- User account management
- Searching and filtering Active Directory objects
- User attribute modification
- Account lifecycle management
- Password management
- CSV reporting
- PowerShell pipeline usage
- Help Desk troubleshooting workflow

---

## Day 16 – File Shares & NTFS Permissions

Completed:

- Learned how Windows Server manages file access using NTFS Permissions and Share Permissions
- Created department-based file share folders:
  - HR
  - IT
  - Sales
- Created and used Active Directory security groups:
  - HR Staff
  - IT Staff
  - Sales Staff
- Practiced assigning permissions through security groups instead of individual users
- Learned how permissions are inherited and how inheritance can be disabled
- Tested how NTFS Permissions and Share Permissions combine to determine effective access

Covered NTFS Permission concepts:

- Read
- Modify
- Full Control
- Permission inheritance
- Cumulative permissions
- Deny permissions

Covered Share Permission concepts:

- Creating network shares
- Configuring Share Permissions
- Understanding Share Permissions vs NTFS Permissions
- Determining effective permissions

Completed troubleshooting scenario:

- User had Modify permissions through NTFS
- User was restricted to Read access through Share Permissions
- Identified Share Permissions as the limiting factor
- Updated Share Permissions and verified the user could modify files successfully

Documented troubleshooting workflow:

- Issue
- Investigation
- Root Cause
- Resolution
- Verification

---

## Day 16 Skills Practiced

- Windows Server File Shares
- NTFS Permissions
- Share Permissions
- Active Directory Security Groups
- File and Folder Access Management
- Permission Inheritance
- Effective Access Troubleshooting
- User Access Troubleshooting

---

## Day 17 – Shared Folders & Network Shares

### Completed:

Created a centralized network share to simulate a company file server

Configured the following shared folder:

CompanyShares

Reviewed the purpose of Windows Network Shares and how organizations centrally store files for users across a network

Configured Share Permissions for Domain Users

Disabled NTFS permission inheritance and converted inherited permissions into explicit permissions

Assigned NTFS permissions using Active Directory security groups:

- HR Staff – Read
- Sales Staff – Read
- IT Staff – Modify

Verified user access by connecting to the shared folder from Client01 using its UNC path

Tested access using multiple Active Directory user accounts

Confirmed:

- HR users could browse folders and open files
- HR users could not create, modify, or delete files
- IT users could create, edit, save, and delete files as expected

Completed troubleshooting scenario:

Simulated a file access issue by removing the IT Staff group's NTFS permissions

Investigated:

- Share Permissions
- NTFS Permissions
- Active Directory group membership
- Effective user access

Resolved issue:

Restored the IT Staff group's Modify permissions

Verified successful access by:

- Logging back into Client01
- Opening the network share
- Creating and editing a test text file

---

# Day 18 – Print Services & Network Drive Management

## Completed:

Learned how Windows Server manages centralized printing services in an Active Directory environment

Reviewed Windows Print Server concepts:

- Print Server role
- Shared printers
- Printer permissions
- Printer deployment
- Print queue management
- Print Spooler troubleshooting

Configured and tested a shared printer environment:

Created a shared printer on DC01:

```
HR-Printer
```

Verified users could access the shared printer from Client01 using the network printer path:

```
\\DC01\HR-Printer
```

Reviewed printer permission concepts:

- Print
- Manage Documents
- Manage Printer

Practiced assigning printer access based on user roles and security groups

---

## 🎫 Ticket #113 — Printer Offline

### Scenario:

User reported they were unable to print because the office printer appeared offline.

### Troubleshooting completed:

Investigated common printer connectivity issues:

- Verified printer availability
- Reviewed printer status
- Checked Print Spooler service
- Reviewed printer communication troubleshooting steps

Verified Print Spooler status:

```powershell
Get-Service Spooler
```

### Resolution:

Reviewed Print Spooler troubleshooting procedures:

```powershell
Restart-Service Spooler
```

Verified printer availability after troubleshooting.

---

# 🎫 Ticket #114 — Printer Queue Problems

## Scenario:

User reported:

"Documents are stuck printing."

## Troubleshooting completed:

Investigated:

- Stuck print jobs
- Failed documents
- Print queue issues
- Print Spooler problems

Reviewed print queue cleanup process:

Stop Print Spooler:

```powershell
Stop-Service Spooler
```

Remove stuck print jobs:

```
C:\Windows\System32\spool\PRINTERS
```

Start Print Spooler:

```powershell
Start-Service Spooler
```

Verified the print queue was cleared and printing functionality was restored.

---

# 🌐 Network Drive Mapping & Group Policy

Learned how organizations provide employees access to department resources using mapped network drives.

Reviewed:

- UNC paths
- Network shares
- Drive letters
- Group Policy Preferences
- User-based drive deployment

Example:

Server folder:

```
C:\CompanyShares\IT
```

Network share:

```
\\DC01\IT
```

Mapped drive:

```
I:
```

Created and tested a Group Policy Object:

```
IT Drive Mapping
```

Configured:

```
User Configuration
    |
    └── Preferences
          |
          └── Windows Settings
                |
                └── Drive Maps
```

Created mapped drive:

```
I: → \\DC01\IT
```

Tested deployment from Client01.

Verified:

- User could access the mapped drive
- Network share permissions were working
- Group Policy successfully deployed the resource

---

# Group Policy Troubleshooting Practice

Practiced troubleshooting mapped drive deployment issues.

Reviewed:

- GPO linking
- Security Filtering
- User group membership
- Group Policy processing
- Drive mapping actions

Commands used:

Force Group Policy update:

```cmd
gpupdate /force
```

Review applied policies:

```cmd
gpresult /r
```

Generated Group Policy reports:

```cmd
gpresult /h report.html
```

---

# Day 18 Skills Practiced

Windows Print Server Administration

Shared printer configuration

Printer permission management

Printer troubleshooting

Print queue troubleshooting

Print Spooler administration

Windows Network Shares

UNC path navigation

Mapped network drives

Group Policy Preferences

Drive deployment through Group Policy

User resource access troubleshooting

Security group-based resource access

PowerShell service management

Help Desk ticket troubleshooting workflow

---

# Day 19 – Week 3 Help Desk Shift

Completed:

* Simulated a full Level 1 Help Desk shift
* Reviewed PowerShell, Active Directory, file shares, NTFS permissions, Share permissions, printers, and network resources
* Practiced investigating issues before making changes
* Practiced identifying root causes and determining appropriate resolutions
* Applied least-privilege principles and security group-based access
* Documented and resolved five simulated Help Desk tickets

---

## 🎫 Ticket #115 — Cannot Modify Shared Folder

### Scenario:

User could access the Sales shared folder but could not modify files.

### Troubleshooting completed:

* Verified the user and account status
* Confirmed the user was logged into the domain
* Confirmed Sales Staff group membership
* Reviewed the Sales folder NTFS permissions
* Identified that Sales Staff did not have the appropriate NTFS Modify permission

### Resolution:

* Granted the Sales Staff group **Modify** NTFS permission on the Sales folder

### Verification:

* User logged out and back into Client01
* Confirmed access to the Sales shared folder
* Confirmed the user could create and modify files

---

## 🖨️ Ticket #116 — Printer Offline

### Scenario:

User reported that the Sales Printer showed as offline and they were unable to print.

### Troubleshooting completed:

* Verified the user and account status
* Confirmed the user was logged into the domain
* Confirmed Sales Staff group membership
* Reviewed Sales Printer permissions
* Identified that Sales Staff did not have the appropriate **Print** permission

### Resolution:

* Granted the Sales Staff group **Print** permission on the Sales Printer

### Verification:

* User logged out and back into Client01
* Confirmed the Sales Printer was accessible
* Successfully submitted a test print job
* Confirmed the appropriate Print permission was applied

> **Lab Note:** The lab does not contain a physical printer, so physical printing could not be verified. The test confirmed that the user could access the shared printer and submit a print job.

---

## 👤 Ticket #117 — User Needs Access

### Scenario:

An HR Staff user requested Modify access to the Sales shared folder.

### Troubleshooting completed:

* Verified the user
* Confirmed the user was logged into the domain
* Confirmed HR Staff group membership
* Reviewed the user's existing Sales folder permissions
* Confirmed management approval for Sales folder access
* Determined the user only required occasional access

### Resolution:

Created a dedicated security group:

```text
HRtoSales
```

Configured access using group-based permissions:

* Added John Smith to `HRtoSales`
* Granted `HRtoSales` **NTFS Modify** permission on the Sales folder
* Granted `HRtoSales` appropriate **Share Change** permission

This avoided granting the user unnecessary access through the broader Sales Staff group.

### Verification:

* User logged out and back into Client01
* Confirmed access to the Sales shared folder
* Confirmed the user could create a new text file
* Confirmed the user had the required Modify access

---

## 🔐 Ticket #118 — Wrong Permissions

### Scenario:

User from the Sales Staff group could access the Sales folder but could not modify files.

### Troubleshooting completed:

* Verified the user
* Confirmed domain login
* Confirmed Sales Staff group membership
* Checked NTFS permissions
* Checked Share permissions
* Determined that NTFS allowed Modify access while Share permissions only allowed Read access

### Resolution:

Changed the Sales Staff Share permission from:

```text
Read
```

to:

```text
Change
```

The existing NTFS Modify permission remained in place.

### Verification:

* User logged out and back into Client01
* Confirmed access to the Sales shared folder
* Confirmed the user could create a new text file
* Confirmed the user could modify and save files

---

## 🔑 Ticket #119 — User Password Reset

### Scenario:

User reported being unable to log in because they had forgotten their password.

### Troubleshooting completed:

* Verified the user's identity using department and manager information
* Verified the correct user account
* Confirmed the user was attempting to log into the domain
* Checked account status
* Confirmed the account was locked

### Resolution:

* Reset the user's password to a temporary password
* Unlocked the user's account
* Required the user to create a new password at next login

### Verification:

* User logged in using the temporary password
* Confirmed the user was prompted to create a new password
* User logged in again using the newly created password
* Confirmed successful access to the domain account

---

## Day 19 Help Desk Skills Practiced

* Investigating issues before making changes
* Root cause identification
* NTFS permission troubleshooting
* Share permission troubleshooting
* Security group-based access management
* Least-privilege access
* Printer permission troubleshooting
* Active Directory account troubleshooting
* Password resets
* Account unlocks
* Professional Help Desk ticket documentation
* Resolution verification

---

# Day 21 – Microsoft 365 Administration & Help Desk

Completed:

* Introduced Microsoft 365 cloud administration through the Microsoft 365 Admin Center
* Learned how Microsoft 365 is administered through a centralized cloud-based management portal
* Explored the Microsoft 365 Admin Center dashboard and navigation
* Reviewed how administrators manage users, licenses, applications, groups, and service health
* Created and managed Microsoft 365 user accounts
* Assigned Microsoft 365 Business Standard licenses
* Reviewed individual user account details and available administrative actions
* Reviewed Microsoft 365 applications and services assigned to users
* Practiced managing Microsoft Teams access
* Reviewed Microsoft 365 service health for troubleshooting cloud service issues
* Practiced distinguishing between a user account issue, license/service issue, application issue, and Microsoft service outage
* Reviewed Microsoft 365 Groups and their relationship to Teams
* Learned the distinction between Microsoft 365 Groups, Microsoft Teams, Security Groups, and Distribution Lists
* Reviewed Microsoft 365 administrator roles and the concept of delegated administrative access
* Reviewed user templates and how they can simplify account provisioning
* Practiced applying a structured Help Desk troubleshooting workflow to cloud-based services

---

## 👤 Microsoft 365 User Administration

Practiced creating a new Microsoft 365 user account and configuring basic access.

Reviewed:

* User creation
* Display name
* Username
* Email address
* Department
* Job title
* Account status
* Password configuration
* Password reset options
* Require password change at next sign-in
* Assigned licenses
* Assigned applications and services

---

## 💳 Microsoft 365 Licensing

Worked with a Microsoft 365 Business Standard license.

Reviewed:

* Microsoft 365 Business licensing
* License assignment
* Available services within a license
* Application/service enablement
* How licensing affects user access

Verified that users could be assigned services including:

* Microsoft Teams
* Outlook / Exchange Online
* OneDrive
* Microsoft 365 applications

---

## 👥 Microsoft 365 Groups & Access Management

Reviewed the purpose and differences between Microsoft 365 group types.

Learned that **Microsoft 365 Groups** can provide shared resources such as:

* Shared mailbox
* Shared calendar
* Shared document library
* Group conversations
* Shared collaboration resources

Reviewed the relationship between Microsoft 365 Groups and Microsoft Teams.

Learned that Teams can add additional collaboration capabilities to a Microsoft 365 Group, including:

* Teams channels
* Team-based collaboration
* Meetings
* Chat
* Additional Teams functionality

Reviewed other group types:

### Security Groups

Used primarily to assign permissions and control access to resources.

### Distribution Lists

Used primarily for sending email communications to a defined group of recipients.

### Microsoft 365 Groups

Designed around collaboration and shared Microsoft 365 resources.

### Microsoft Teams

Provides collaboration capabilities built around Microsoft 365 Groups and adds Teams-specific functionality.

Also reviewed:

* Group owners
* Group members
* Group membership
* Team ownership
* Team membership

---

## 🏢 Microsoft 365 Administrator Roles

Reviewed the concept of administrative roles within Microsoft 365.

Learned that administrators can be assigned specific roles based on their responsibilities rather than automatically receiving unrestricted administrative access.

Reviewed the importance of:

* Role-based administration
* Least privilege
* Limiting administrative access to what is required for a user's job responsibilities

---

## 🏥 Microsoft 365 Service Health

Practiced using Microsoft 365 Service Health as part of a troubleshooting workflow.

Used the following troubleshooting process:

```text
User reports issue
        ↓
Verify user's account
        ↓
Verify license
        ↓
Verify required application/service
        ↓
Check Microsoft 365 Service Health
        ↓
Determine whether issue is user-side or service-side
        ↓
Troubleshoot / Resolve
        ↓
Verify functionality
        ↓
Document ticket
```

Learned that checking service health can prevent unnecessary troubleshooting when Microsoft is experiencing a widespread service issue.

---

# 🎫 Ticket #120 — User Cannot Access Microsoft Teams

## Scenario

John Smith reported:

> "I can't access Microsoft Teams. I was told I should have access."

## Investigation

* Located John Smith in Microsoft 365 Admin Center
* Verified the user's Microsoft 365 license
* Reviewed Apps and Services assigned to the account
* Confirmed Microsoft Teams was enabled
* Asked the user what occurred when attempting to open Teams
* User reported Teams opened briefly and then closed without displaying an error
* Confirmed other Microsoft 365 applications such as Outlook and OneDrive were functioning
* Checked Microsoft 365 Service Health
* Confirmed Microsoft Teams was reporting as healthy

## Resolution

* Had the user attempt to access Teams through the Microsoft 365 website
* Had the user restart their computer
* User successfully accessed Microsoft Teams after restarting

## Root Cause

* Local Teams application/session issue requiring a workstation restart

## Verification

* User successfully opened Microsoft Teams
* Confirmed Teams was functioning normally after restart

---

# 🎫 Ticket #121 — New Employee Outlook & Teams Access

## Scenario

Sarah Sherman reported:

> "Sarah started today but cannot access Outlook or Microsoft Teams. She should have access."

## Investigation

* Searched Microsoft 365 Active Users for Sarah Sherman
* Determined that the new employee did not have an existing Microsoft 365 account

## Resolution

* Created a new Microsoft 365 user account for Sarah Sherman
* Assigned the Microsoft 365 Business Standard license
* Granted access to Microsoft Teams

## Root Cause

* New employee account had not yet been created in Microsoft 365

## Verification

* Confirmed Sarah's account was successfully created
* Confirmed the Microsoft 365 license was assigned
* Confirmed Microsoft Teams was enabled for the user

## Day 21 Skills Practiced

* Microsoft 365 Admin Center navigation
* Microsoft 365 user administration
* Cloud-based user provisioning
* Microsoft 365 Business Standard licensing
* Application and service management
* Microsoft Teams administration
* Microsoft 365 Groups
* Security Groups
* Distribution Lists
* User password management
* Password reset workflows
* Microsoft 365 administrator roles
* Role-based access concepts
* Service Health investigation
* Cloud application troubleshooting
* New employee provisioning
* Help Desk ticket documentation
* Cloud-based troubleshooting methodology
* Issue → Investigation → Root Cause → Resolution → Verification workflow

---

# 🧠 Skills Practiced

## Active Directory

- Active Directory Domain Services (AD DS)
- User account management
- User creation and modification
- Security groups
- Organizational Units (OUs)
- Group Policy Objects (GPOs)
- Password resets
- Account lockout troubleshooting
- Disabled account troubleshooting
- Domain authentication troubleshooting
- Group membership troubleshooting
- User access management
- Active Directory attribute management
- Security group-based access management
- File access management
- User permissions troubleshooting

---

## PowerShell Administration

- PowerShell fundamentals
- Active Directory PowerShell module
- Command discovery and syntax usage
- Object filtering
- Pipeline usage
- User retrieval with `Get-ADUser`
- User modification with `Set-ADUser`
- User creation with `New-ADUser`
- Account enable/disable management
- Password management
- CSV reporting and data export
- Command-line administration workflows
- Windows service management using PowerShell
- Service status verification
- Restarting administrative services

---

## Windows Administration

- Windows Server configuration
- Active Directory Domain Services (AD DS)
- DNS Server management
- DHCP Server configuration
- Group Policy Management
- User Configuration policies
- Desktop configuration management
- User restrictions
- Policy troubleshooting
- Client policy verification
- Windows client/server 
- Windows Server File Shares
- NTFS and Share Permission management
- File and folder security administration
- Windows Network Shares
- Shared folder administration
- Share permission configuration
- Permission inheritance management
- Print Server management
- Windows Print Services
- Shared printer configuration
- Printer permissions
- Print queue administration
- Print Spooler troubleshooting
- Group Policy Preferences
- Mapped drive deployment

---

## Networking

- DNS troubleshooting
- DHCP configuration
- DHCP scopes and leases
- Client/server communication
- Name resolution testing
- IP configuration troubleshooting
- APIPA troubleshooting
- Network service verification
- Basic network troubleshooting methodology
- UNC path navigation
- Network share connectivity
- Network drive deployment
- UNC path management
- Department resource access
- Mapped drive administration

---

## Microsoft 365 Administration

Microsoft 365 Admin Center
Microsoft 365 cloud administration
Microsoft 365 user administration
Microsoft 365 user provisioning
Microsoft 365 Business Standard licensing
License assignment and verification
Microsoft 365 application/service management
Microsoft Teams administration
Microsoft 365 Service Health
Microsoft 365 account troubleshooting
Microsoft 365 password management
Microsoft 365 password reset workflows
Microsoft 365 user account status
Microsoft 365 Groups
Security Groups
Distribution Lists
Group ownership and membership
Microsoft 365 administrator roles
Role-based access concepts
Least-privilege administrative access
New employee account provisioning
Cloud application troubleshooting
Cloud / Cloud Support Skills
Cloud-based user administration
SaaS administration concepts
Microsoft 365 cloud services
Cloud application access troubleshooting
Cloud service health monitoring
License-based service access
Cloud identity and access concepts
User provisioning and account lifecycle management
Cloud-based Help Desk troubleshooting
Differentiating user-side issues from service-side outages
Cloud service troubleshooting methodology

--

## Help Desk Skills

- Ticket documentation
- Microsoft 365 user administration
- Microsoft 365 license troubleshooting
- Troubleshooting methodology
- Root cause analysis
- Incident response
- Verification procedures
- Identity and access troubleshooting
- User account troubleshooting
- Security group administration
- User support workflows
- Escalation processes
- Technical documentation
- Incident lifecycle management
- File access troubleshooting
- Permission troubleshooting
- User resource access issues
- Shared folder troubleshooting
- Network share access verification
- Access Denied troubleshooting
- Printer troubleshooting
- Printer connectivity troubleshooting
- Print queue troubleshooting
- User resource access issues
- Mapped drive troubleshooting
- Group Policy troubleshooting

---

# 📂 Repository Structure

Each lab day includes:

- Main README documentation
- Configuration screenshots
- Troubleshooting notes
- Realistic Help Desk ticket scenarios
- Ticket documentation containing:
  - Issue
  - Investigation
  - Root Cause
  - Resolution
  - Verification

---

# 🚀 Future Lab Expansion

Planned additions:

- Microsoft Entra ID (Azure Active Directory)
- Azure Virtual Machines
- Azure networking fundamentals
- Microsoft 365 administration
- PowerShell automation
- Cloud identity management
- Backup and recovery testing
- Additional Help Desk ticket simulations
- System Administrator level troubleshooting scenarios
- Cloud administration workflows

---

# 📌 Project Summary

This lab demonstrates practical experience building, managing, and supporting a small enterprise Windows environment.

Through hands-on scenarios, I have practiced:

- Building and maintaining an Active Directory domain
- Managing Windows Server roles and services
- Supporting Windows client machines
- Troubleshooting DNS, DHCP, and authentication issues
- Managing users, groups, and permissions
- Administering Active Directory through PowerShell
- Creating reports and automating administrative tasks
- Resolving user issues through professional Help Desk workflows
- Documenting incidents using real-world troubleshooting methodology
- Creating and managing Windows Network Shares
- Configuring Share and NTFS permissions
- Verifying user access to shared resources
- Troubleshooting file share and permission issues

This project represents a transition from foundational IT knowledge into practical Help Desk, Systems Administration, and Cloud Support skills.
