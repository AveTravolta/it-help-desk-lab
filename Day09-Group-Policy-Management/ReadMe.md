## Overview

Completed hands-on practice with Windows Server Group Policy Objects (GPOs).

The goal of this lab was to learn how administrators centrally manage user settings across a domain environment.

---

# 🎯 Objectives

- Create and configure Group Policy Objects
- Apply policies to Organizational Units
- Manage user desktop settings
- Restrict access to Windows settings
- Troubleshoot Group Policy application issues

---

# 🛠️ Completed Tasks

## Wallpaper Policy

Created a Group Policy Object to manage desktop wallpaper settings.

Completed:

- Created Wallpaper Policy GPO
- Linked policy to Golf Employees OU
- Configured Desktop Wallpaper settings
- Tested policy application on domain users

---

## Control Panel Restriction Policy

Created a Group Policy Object to restrict access to Control Panel and Windows Settings.

Completed:

- Created Inventory Organizational Unit
- Moved test user into Inventory OU
- Created Control Panel restriction policy
- Applied policy using Group Policy Management

---

# 🔧 Break/Fix Scenario

Encountered an issue where Group Policy Objects existed and were linked but were not applying correctly.

Troubleshooting included:

- Reviewing OU placement
- Checking GPO links
- Reviewing Security Filtering
- Verifying GPO permissions
- Running:
```cmd
- gpupdate /force
- and
- gpresult /r ```
- Resolved the issue by restoring required Authenticated Users permissions. 

# Skills Learned

## Active Directory
Organizational Units
Security Groups vs OUs
User policy targeting

## Group Policy
Creating GPOs
Linking GPOs
User Configuration policies
Security Filtering
Troubleshooting GPO failures

## Administration Tools
Active Directory Users and Computers
Group Policy Management Console
Command-line troubleshooting
