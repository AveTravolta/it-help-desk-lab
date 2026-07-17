# 🎫 Ticket #102 — User Account Disabled

## 📌 Issue Summary

A user attempted to log into the **Client01** workstation but was unable to authenticate.

The user received a message indicating that their Active Directory account had been disabled.

---

# 🔍 Investigation

The following troubleshooting steps were performed:

1. Opened **Active Directory Users and Computers (ADUC)** on the Domain Controller.
2. Located the affected user's account.
3. Reviewed the account status and confirmed the account was disabled.

---

# 🧠 Root Cause

The user's Active Directory account had been disabled as part of the employee offboarding process after completion of a previous freelance assignment.

The account remained disabled when the user returned and attempted to access company resources.

---

# 🛠️ Resolution

The following actions were performed:

- Enabled the user's Active Directory account.
- Verified the account was active and able to authenticate.
- Required the user to change their password upon successful login to confirm account functionality.

---

# ✅ Verification

The issue was successfully resolved.

Verified:

- ✅ User was able to log into Client01 successfully.
- ✅ User was able to update their password.
- ✅ Active Directory authentication was restored.

---

# 🏁 Final Status

**Ticket Status: Resolved**
