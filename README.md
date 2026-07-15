# 🖥️ IT Help Desk / Cloud Admin Lab (Active Directory & Windows Server)

## Overview

This repository documents a hands-on IT support and systems administration lab designed to simulate a small business enterprise environment.

The goal of this project is to build practical experience with **Windows Server, Active Directory, DNS, user administration, troubleshooting, and help desk ticket resolution** through realistic scenarios.

The lab environment uses **Windows Server Active Directory Domain Services (AD DS)** and a Windows client machine to practice common entry-level IT tasks performed by Help Desk Technicians and System Administrators.

---

## 🎯 Goals

- Build and manage a Windows Server domain environment
- Configure and administer Active Directory Domain Services (AD DS)
- Create and manage users, organizational units, and security groups
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

# 🧠 Skills Practiced

## Active Directory
- User account management
- Security groups
- Organizational Units
- Group Policy Objects (GPOs)
- Password resets
- Account lockout troubleshooting
- Account troubleshooting

## Windows Administration
- Group Policy Management
- User Configuration policies
- Desktop configuration management
- User restrictions
- Policy troubleshooting

## Networking
- DNS troubleshooting
- Client/server communication
- Name resolution testing

## Help Desk Skills
- Ticket documentation
- Troubleshooting methodology
- Root cause analysis
- Verification procedures
- User support workflows

---

# 📂 Repository Structure


