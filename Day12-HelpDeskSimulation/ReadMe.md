# 🖥️ Day 12 — Help Desk Ticket Simulation

## 📋 Overview

This lab simulated a real-world Help Desk support environment by documenting common user issues as professional IT support tickets.

The goal of this exercise was to practice:

- Troubleshooting user issues
- Following a structured ticket workflow
- Verifying user identity and account status
- Performing Active Directory account management
- Documenting investigation steps, root causes, resolutions, and verification
- Communicating technical solutions clearly

These tickets simulate common Tier 1 Help Desk scenarios within an Active Directory domain environment.

---

# 🎫 Ticket #104 — Password Reset Request

## 📋 Issue

A user reported they forgot their password and were unable to log into their workstation.

---

## 🔍 Investigation

Performed the following troubleshooting steps:

- Logged into the Domain Controller (**DC01**).
- Opened **Active Directory Users and Computers (ADUC)**.
- Located the affected user account.
- Verified the user's identity by confirming:
  - Name
  - Department
  - Manager
- Confirmed the user's account was not locked out.
- Confirmed the user's account was not disabled.

---

## 🧠 Root Cause

The user forgot their password and was unable to authenticate with their existing credentials.

---

## 🛠️ Resolution

Resolved the issue by performing the following actions:

- Reset the user's password to a temporary password (`Password123`).
- Enabled **User must change password at next logon**.
- Informed the user of the temporary password.

---

## ✅ Verification

Verified the issue was resolved by confirming:

- The user successfully logged into their workstation.
- The user was prompted to create a new password.
- Authentication completed successfully.

---

# 🎫 Ticket #105 — Account Unlock Request

## 📋 Issue

A user reported they were unable to access their domain account after multiple failed login attempts.

---

## 🔍 Investigation

Performed the following troubleshooting steps:

- Logged into the Domain Controller (**DC01**).
- Opened **Active Directory Users and Computers (ADUC)**.
- Located the affected user account.
- Verified the user's identity by confirming:
  - Name
  - Department
  - Manager
- Checked the account status.
- Confirmed the user's account was locked out.
- Confirmed the user's account was enabled and not disabled.

---

## 🧠 Root Cause

The user forgot their password and entered incorrect credentials multiple times, triggering the Active Directory account lockout policy.

---

## 🛠️ Resolution

Resolved the issue by performing the following actions:

- Unlocked the user's account in **Active Directory Users and Computers**.
- Reset the user's password to a temporary password (`Password123`).
- Enabled **User must change password at next logon**.
- Informed the user of the temporary password.

---

## ✅ Verification

Verified the issue was resolved by confirming:

- The user successfully logged into their workstation.
- The user was able to authenticate successfully.
- The account was no longer locked.

---

# 🎫 Ticket #106 — Group Membership Issue

## 📋 Issue

A user reported they were unable to access resources within the **Inventory Staff** group, even though they are the department manager.

---

## 🔍 Investigation

Performed the following troubleshooting steps:

- Logged into the Domain Controller (**DC01**).
- Opened **Active Directory Users and Computers (ADUC)**.
- Located the affected user account.
- Verified the user's identity by confirming:
  - Name
  - Department
  - Manager
- Reviewed the user's current Active Directory group memberships.
- Compared the user's current group memberships against the expected access requirements for their department role.
- Determined the user was missing the required Inventory Staff security group membership.

---

## 🧠 Root Cause

The user was correctly assigned to the **Management** group but was not a member of the **Inventory Staff** security group required for access to inventory resources.

---

## 🛠️ Resolution

Resolved the issue by performing the following actions:

- Added the user's account to the **Inventory Staff** security group.
- Had the user log out and sign back in to refresh their security token and apply the updated group membership.

---

## ✅ Verification

Verified the issue was resolved by confirming:

- The user successfully logged into their workstation.
- The user was able to access the required Inventory Staff resources.
- Updated group permissions were successfully applied.

---

# 🧰 Tools Used

- Windows Server 2022
- Windows 11 Client Machine
- Active Directory Users and Computers (ADUC)
- Domain Controller (DC01)
- Group Policy Management
- Active Directory Security Groups

---

# 🎯 Skills Demonstrated

- Help Desk Ticket Documentation
- Active Directory User Management
- Password Resets
- Account Lockout Troubleshooting
- Security Group Administration
- User Access Troubleshooting
- Identity and Access Management (IAM)
- Least Privilege Concepts
- User Authentication Troubleshooting
- Technical Documentation Practices

---

# 📝 Lab Summary

This exercise focused on transforming hands-on Active Directory administration tasks into realistic Help Desk support documentation.

The completed tickets demonstrate the ability to:

- Identify common user issues
- Investigate account and access problems
- Make appropriate Active Directory changes
- Verify successful resolution
- Document troubleshooting steps professionally

These scenarios represent common Tier 1 Help Desk responsibilities within a Windows Server Active Directory environment.
