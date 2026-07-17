# 🎫 Ticket #104 — Password Reset Request

## 📋 Issue

A user reported they had forgotten their password and were unable to log in to their domain-joined workstation.

---

## 🔍 Investigation

Performed the following troubleshooting steps:

- Logged into the Domain Controller (DC01).
- Opened **Active Directory Users and Computers (ADUC)**.
- Located the affected user account.
- Verified the user's identity by confirming:
  - Name
  - Department
  - Manager
- Confirmed the account was **not locked out**.
- Confirmed the account was **enabled**.
- Determined the issue was not related to account lockout or a disabled account.

---

## 🧠 Root Cause

The user had forgotten their domain password and was unable to authenticate.

---

## 🛠️ Resolution

Resolved the issue by performing the following actions:

- Reset the user's password to a temporary password (`Password123`).
- Selected **User must change password at next logon**.
- Informed the user of the temporary password.

---

## ✅ Verification

Verified the issue was resolved by confirming:

- The user successfully logged into their workstation.
- The user was prompted to create a new password upon signing in.
- Authentication completed successfully using the new credentials.

---

## 🧰 Tools Used

- Windows Server 2022
- Active Directory Users and Computers (ADUC)
- Domain Controller (DC01)

---

## 🎯 Skills Demonstrated

- Active Directory User Administration
- Password Management
- Identity Verification
- Tier 1 Help Desk Troubleshooting
- User Account Management
- Ticket Documentation
