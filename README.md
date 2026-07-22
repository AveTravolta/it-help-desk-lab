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
- Windows client/server administration

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

---

## Help Desk Skills

- Ticket documentation
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

This project represents a transition from foundational IT knowledge into practical Help Desk, Systems Administration, and Cloud Support skills.
