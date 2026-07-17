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

## 🧰 Tools Used

- Windows Server 2022
- Active Directory Users and Computers (ADUC)
- Domain Controller (DC01)

---

## 🎯 Skills Demonstrated

- Active Directory Group Management
- Security Group Administration
- User Access Troubleshooting
- Least Privilege Concepts
- Identity and Access Management (IAM)
- Help Desk Ticket Resolution
- Technical Documentation
