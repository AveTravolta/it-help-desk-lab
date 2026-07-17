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

# Day 12 – Advanced Troubleshooting & Incident Response

Completed:

- Performed a full Help Desk troubleshooting simulation
- Practiced diagnosing enterprise issues from a user-impact perspective
- Used a structured troubleshooting methodology:

  - Identify the issue
  - Gather information
  - Determine root cause
  - Apply a fix
  - Verify resolution
  - Document the incident

---

## 🎫 Ticket #104 — DNS Misconfiguration Troubleshooting

Scenario:

- Client01 was unable to properly communicate with Active Directory services

Troubleshooting completed:

- Reviewed network configuration using:

```cmd
ipconfig /all
```

- Verified DNS settings
- Tested Domain Controller connectivity:

```cmd
ping dc01
```

- Tested name resolution:

```cmd
nslookup sandoval.local
```

Identified:

- Client01 DNS configuration was pointing to an incorrect DNS server

Root Cause:

- Client workstation was unable to locate Active Directory services because DNS was not pointing to the Domain Controller DNS server

Resolution:

- Corrected Client01 DNS configuration
- Restored DNS settings to:

```text
10.1.10.2
```

Verification:

- Confirmed successful communication with DC01
- Confirmed DNS resolution restored

---

## 🎫 Ticket #105 — Group Policy Troubleshooting

Scenario:

- User reported that a company policy was not applying correctly

Troubleshooting completed:

- Verified user and computer placement within Active Directory
- Reviewed Group Policy links
- Checked applied policies using:

```cmd
gpresult /r
```

- Forced Group Policy refresh:

```cmd
gpupdate /force
```

Identified:

- Policy was not applying due to incorrect configuration

Root Cause:

- Group Policy configuration prevented the intended setting from being applied

Resolution:

- Corrected GPO configuration
- Verified proper policy targeting

Verification:

- Confirmed policy applied successfully on Client01

---

## 🎫 Ticket #106 — Active Directory Login Troubleshooting

Scenario:

- User was unable to authenticate to the domain

Troubleshooting completed:

- Verified account status in Active Directory Users and Computers
- Checked:
  - Account enabled status
  - Password status
  - Group membership
  - Domain connectivity

Resolution:

- Corrected account configuration issue
- Verified user authentication

Verification:

- User successfully logged into Client01 using domain credentials

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

# 🧠 Skills Practiced

## Active Directory

- User account management
- Security groups
- Organizational Units (OUs)
- Group Policy Objects (GPOs)
- Password resets
- Account lockout troubleshooting
- Disabled account troubleshooting
- Domain authentication troubleshooting

---

## Windows Administration

- Windows Server configuration
- Active Directory Domain Services (AD DS)
- Group Policy Management
- User Configuration policies
- Desktop configuration management
- User restrictions
- Policy troubleshooting
- Client policy verification

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

---

## Help Desk Skills

- Ticket documentation
- Troubleshooting methodology
- Root cause analysis
- Incident response
- Verification procedures
- User support workflows
- Escalation processes
- Technical documentation

---

# 📂 Repository Structure

---

# 🚀 Future Lab Expansion

Planned additions:

- Azure Active Directory / Microsoft Entra ID
- Azure Virtual Machines
- Cloud networking fundamentals
- Microsoft 365 administration
- PowerShell automation
- Backup and recovery testing
- Additional Help Desk ticket simulations
- System Administrator level troubleshooting scenarios

---

# 📌 Project Summary

This lab demonstrates practical experience building and supporting a small enterprise Windows environment.

Through hands-on scenarios, I have practiced:

- Managing Active Directory environments
- Supporting Windows clients
- Troubleshooting DNS and DHCP issues
- Managing Group Policy
- Resolving user access issues
- Documenting incidents using professional Help Desk workflows

This project represents a transition from foundational IT knowledge into real-world Help Desk, Systems Administration, and Cloud Support skills.
