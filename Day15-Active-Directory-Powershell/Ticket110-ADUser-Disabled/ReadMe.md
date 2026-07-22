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
