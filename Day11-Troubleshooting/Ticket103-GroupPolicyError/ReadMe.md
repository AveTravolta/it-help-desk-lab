# 🎫 Ticket #103 — Group Policy Issue

## 📌 Issue Summary

A user logged into the **Client01** workstation and noticed that the system clock was missing from the notification area on the Windows taskbar.

The user reported that the computer was functioning normally, but the clock was no longer visible.

---

# 🔍 Investigation

The following troubleshooting steps were performed:

1. Logged into the **Client01** workstation and verified the reported issue.

2. Reviewed Windows taskbar settings to confirm the clock was not disabled through a local user setting.

3. Determined that the issue was likely related to a domain-level configuration because Client01 is managed through Active Directory.

4. Generated a Group Policy Results report:

```powershell
gpresult /h report.html
```

5. Reviewed the applied Group Policy Objects and identified that the user was receiving the **Control Panel Restrictions** GPO.

6. Reviewed the GPO settings and identified the following policy:

```text
Remove the clock from the system notification area
```

---

# 🧠 Root Cause

The user's account was receiving a Group Policy Object that had the following setting enabled:

```text
Remove the clock from the system notification area
```

Because the policy was applied through Active Directory, the setting overrode the normal Windows taskbar behavior on Client01.

---

# 🛠️ Resolution

The following actions were performed:

- Reviewed the purpose of the existing GPO settings.
- Confirmed that removing the system clock was not an intended configuration.
- Modified the Group Policy Object to disable the clock removal setting.
- Forced a Group Policy refresh on Client01:

```powershell
gpupdate /force
```

---

# ✅ Verification

The fix was verified by:

- Logging the user out of Client01.
- Having the user log back into the workstation.
- Confirming the system clock was restored to the Windows notification area.

Verified:

- ✅ GPO settings updated successfully
- ✅ User received the corrected policy
- ✅ System clock displayed normally again

---

# 🏁 Final Status

**Ticket Status: Resolved**
