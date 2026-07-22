# 🖥️ Day 15 — Active Directory PowerShell

## 📌 Overview

Today focused on managing **Active Directory through PowerShell instead of relying only on Active Directory Users and Computers (ADUC).**

The goal was to learn how administrators use PowerShell to query Active Directory objects, modify user attributes, create accounts, manage account status, and generate reports.

PowerShell allows IT professionals to automate repetitive tasks, manage larger environments, and perform administrative actions faster than using only the graphical interface.

---

# 🎯 Objectives

- Learn the Active Directory PowerShell module
- Understand common Active Directory cmdlets
- Retrieve user information using PowerShell
- Search and filter Active Directory users
- View additional user properties
- Modify user attributes
- Create user accounts
- Disable and enable accounts
- Reset passwords
- Export Active Directory information to CSV
- Practice a real-world Help Desk troubleshooting scenario

---

# 🧪 Lab Environment

**Domain:**

```
sandoval.local
```

**Server:**

```
DC01
```

**Tools Used:**

- Windows Server 2022
- Active Directory Domain Services
- PowerShell
- Active Directory PowerShell Module

---

# 📚 Learning Topics

## Active Directory PowerShell Module

Verified the Active Directory module was available.

```powershell
Get-Module ActiveDirectory -ListAvailable
```

Imported the module:

```powershell
Import-Module ActiveDirectory
```

---

# 🔎 Discovering Active Directory Commands

Used PowerShell to explore available Active Directory cmdlets.

List Active Directory commands:

```powershell
Get-Command -Module ActiveDirectory
```

Search for user-related commands:

```powershell
Get-Command *ADUser*
```

Examples discovered:

- `Get-ADUser`
- `New-ADUser`
- `Set-ADUser`
- `Enable-ADAccount`
- `Disable-ADAccount`
- `Set-ADAccountPassword`

---

# 📖 PowerShell Help and Syntax

Attempted to use:

```powershell
Get-Help Get-ADUser
```

The lab environment did not have downloadable PowerShell help content installed because the server does not have internet access.

Used built-in syntax information instead:

```powershell
Get-Command Get-ADUser -Syntax
```

This provided available parameters and command structure.

---

# 👥 Retrieving Active Directory Users

Retrieved all users:

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

---

# 🔍 Searching Users and Viewing Properties

Retrieved a specific user:

```powershell
Get-ADUser -Identity username
```

Viewed additional properties:

```powershell
Get-ADUser -Identity username -Properties *
```

Learned that Active Directory user objects contain many attributes including:

- Name
- SamAccountName
- Department
- Office
- City
- Enabled status
- Logon information
- Account details

---

# 🛠️ Modifying Active Directory Users

Practiced modifying user attributes using:

```powershell
Set-ADUser
```

Example:

```powershell
Set-ADUser username -City "Long Beach"
```

Used `-WhatIf` to preview changes before applying them:

```powershell
Set-ADUser username -City "Long Beach" -WhatIf
```

Used verification commands afterward:

```powershell
Get-ADUser username -Properties City
```

---

# 📝 User Modification Practice

The following scenarios were practiced as Active Directory administration exercises.

## Employee Promotion Example

Updated user attributes such as:

- Job title
- Department

Example:

```powershell
Set-ADUser username -Title "Senior IT Support Specialist" -Department "IT Support"
```

Verified:

```powershell
Get-ADUser username -Properties Title,Department
```

---

## Office Relocation Example

Updated office information:

- Office location
- City

Example:

```powershell
Set-ADUser username -Office "Long Beach" -City "Long Beach"
```

Verified:

```powershell
Get-ADUser username -Properties Office,City
```

---

# ➕ Creating a New Active Directory User

Created a new user account through PowerShell.

Example:

```powershell
New-ADUser -Name "PowerShell User" -GivenName "PowerShell" -Surname "User" -SamAccountName psuser -UserPrincipalName psuser@sandoval.local -AccountPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) -Enabled $true
```

Verified the account:

```powershell
Get-ADUser psuser
```

---

# 🚫 Managing Account Status

Disabled a user account:

```powershell
Disable-ADAccount psuser
```

Checked account status:

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

---

# 🔑 Password Management

Reset a user's password:

```powershell
Set-ADAccountPassword psuser -Reset -NewPassword (ConvertTo-SecureString "NewPassword123!" -AsPlainText -Force)
```

---

# 📊 Exporting Active Directory Reports

Created a report of disabled user accounts.

Command:

```powershell
Get-ADUser -Filter "Enabled -eq 'False'" | Select Name,SamAccountName,Enabled | Export-Csv C:\UsersDisabled.csv -NoTypeInformation
```

This demonstrated a common administrative workflow:

1. Retrieve objects
2. Filter based on properties
3. Select useful information
4. Export results for reporting

---

# 🎫 Ticket #110 — User Unable to Log In

## Issue

User **Max Homa** reported that he was unable to log in to his workstation. The system indicated that his Active Directory account was disabled.

---

## Investigation

- Confirmed the identity of the user by locating the **Max Homa** Active Directory account.
- Reviewed the user's account properties using PowerShell ISE.
- Verified that the account status showed as disabled.

Command used:

```powershell
Get-ADUser maxhoma -Properties Enabled
```

---

## Root Cause

A coworker accidentally disabled the **Max Homa** Active Directory account while performing user account cleanup.

---

## Resolution

Enabled the user's Active Directory account using PowerShell.

Command used:

```powershell
Enable-ADAccount maxhoma
```

---

## Verification

Confirmed that the account was successfully enabled by checking the user's Active Directory properties.

Command used:

```powershell
Get-ADUser maxhoma -Properties Enabled
```

The account status was verified as enabled, allowing the user to log in again.

---

## Outcome

User account access was restored successfully. The issue was resolved by identifying the disabled account, correcting the account status, and verifying the change through Active Directory PowerShell.

---

# 🧠 PowerShell Concepts Learned

## Get

Used to retrieve information:

```powershell
Get-ADUser
```

## Set

Used to modify existing objects:

```powershell
Set-ADUser
```

## New

Used to create new objects:

```powershell
New-ADUser
```

## Enable / Disable

Used to change account status:

```powershell
Enable-ADAccount
```

```powershell
Disable-ADAccount
```

---

# ⚖️ GUI vs PowerShell Comparison

## Active Directory Users and Computers (GUI)

Advantages:

- Easier for beginners
- Visual navigation
- Good for occasional changes

Disadvantages:

- Slower for repetitive tasks
- Difficult to automate
- Less efficient for large environments

---

## PowerShell

Advantages:

- Faster administration
- Automation capabilities
- Handles large numbers of accounts
- Better reporting options
- Commonly used by system administrators

Disadvantages:

- Requires learning syntax
- Mistakes can affect many objects if not tested

---

# 🧠 Lessons Learned

- Active Directory objects contain many attributes beyond what is visible in the GUI.
- PowerShell allows administrators to manage users more efficiently.
- Filtering is based on object properties and comparisons.
- The pipeline (`|`) allows commands to pass information between steps.
- `Get-ADUser` is used to retrieve user information.
- `Set-ADUser` modifies existing user attributes.
- CSV exports are useful for audits and reporting.
- Real IT troubleshooting involves identifying the problem, making the smallest required change, and verifying the result.

---

# 📸 Screenshots Included

Screenshots documented:

- Active Directory PowerShell module
- Available AD cmdlets
- User searches
- User properties
- User modifications
- User creation
- Account enable/disable actions
- Password reset
- CSV exports
- Ticket #110 resolution

---

# ✅ Day 15 Completed

Skills practiced:

✔ Active Directory PowerShell  
✔ User management  
✔ Filtering and searching  
✔ User attribute modification  
✔ Account lifecycle management  
✔ Password management  
✔ CSV reporting  
✔ Help Desk troubleshooting workflow
