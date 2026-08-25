# 🔒 ServiceNow Ticket 02 — Account Lockout

**Incident:** INC0010002  
**Category:** Password Reset  
**Channel:** Phone  
**Priority:** 4 - Low  
**State:** Resolved

---

## 📝 User Issue

User reported being unable to log into their Windows workstation and receiving an account locked message.

The user was unsure why the account had been locked and confirmed that the issue was not related to a requested password reset.

---

## 🔍 Troubleshooting

The issue was investigated using the Windows Server Active Directory environment.

### Active Directory troubleshooting

- Located the user's account in Active Directory Users and Computers (ADUC).
- Verified that the account was locked.
- Unlocked the user's account.
- Reset the user's password.
- Tested authentication after making the changes.

---

## 🔧 Resolution

The user's Active Directory account was unlocked and the password was reset.

The user was able to successfully authenticate after the changes.

**Resolution Code:** Solved (Permanently)

### Resolution Notes

> Account was locked in Active Directory. Account was unlocked and password was reset. User successfully authenticated after the changes.

---

## 💡 What I Learned

This ticket demonstrated how a ServiceNow incident can be used to track an actual technical fix performed in another system.

### Workflow

**ServiceNow**
→ Document user issue

**ADUC**
→ Investigate account  
→ Unlock account  
→ Reset password

**ServiceNow**
→ Document work performed  
→ Resolve incident

This reinforced the distinction between the ticketing system and the tools used to perform the actual technical work.
