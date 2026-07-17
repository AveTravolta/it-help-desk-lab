# 🎫 Ticket #105 — Account Unlock Request

## 📋 Issue

A user reported that they were unable to access their domain account after multiple failed login attempts.

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
- Checked the account status and confirmed the account was **locked out**.
- Confirmed the account was **enabled** and not disabled.
- Determined the issue was related to account lockout rather than an inactive account.

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
- The user was prompted to create a new password.
- Authentication completed successfully.

---

## 🧰 Tools Used

- Windows Server 2022
- Active Directory Users and Computers (ADUC)
- Domain Controller (DC01)

---

## 🎯 Skills Demonstrated

- Active Directory Account Management
- Account Lockout Troubleshooting
- Password Resets
- User Authentication Troubleshooting
- Help Desk Ticket Resolution
- Documentation Practices
