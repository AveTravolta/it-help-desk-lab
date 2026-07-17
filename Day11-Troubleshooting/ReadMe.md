# 🛠️ DAY 11 — Troubleshooting Lab Tickets

## 🎯 Objective

The goal of Day 11 was to simulate a real-world Help Desk troubleshooting environment by intentionally breaking common enterprise services and resolving the issues.

This troubleshooting day focused on identifying the root cause of user-impacting problems involving:

- 🌐 DNS
- 🔑 Active Directory User Accounts
- ⚙️ Group Policy

The goal was not only to fix the issues but to practice a structured troubleshooting process:

1. Identify the issue
2. Investigate the cause
3. Apply a resolution
4. Verify functionality

---

# 🎫 Ticket #101 — DNS Failure

## 📌 Issue Summary

A user reported that after restarting the **Client01** workstation, they were unable to access company network resources.

The user received an error indicating that the computer could not locate a **logon server**, preventing normal domain authentication.

---

# 🔍 Investigation

The following troubleshooting steps were performed:

1. Logged into the **Client01** workstation and verified the issue.

2. Checked network connectivity to ensure the workstation could communicate with the Domain Controller.

```powershell
ping DC01
```

3. Reviewed the workstation's network configuration:

```powershell
ipconfig /all
```

4. Verified:

- IP address configuration
- Default gateway
- DNS server settings
- Domain connectivity

---

# 🧠 Root Cause

The Client01 workstation was configured with an incorrect preferred DNS server.

Incorrect configuration:

```text
Preferred DNS Server: 8.8.8.8
```

Domain-joined computers rely on the internal DNS server hosted by the Domain Controller to locate Active Directory services.

Incorrect DNS configuration prevented Client01 from properly locating:

- Domain controllers
- Authentication services
- Domain resources
- Group Policy services

---

# 🛠️ Resolution

The DNS configuration was corrected.

Updated configuration:

```text
Preferred DNS Server: 10.1.10.2
```

The DNS cache was cleared:

```powershell
ipconfig /flushdns
```

DNS registration was refreshed:

```powershell
ipconfig /registerdns
```

---

# ✅ Verification

The issue was verified by:

- Confirming DNS settings with:

```powershell
ipconfig /all
```

- Successfully communicating with the Domain Controller:

```powershell
ping DC01
```

- Confirming domain name resolution:

```powershell
nslookup sandoval.local
```

Verified:

- ✅ DNS settings restored
- ✅ Client01 communicated with DC01
- ✅ Domain authentication restored

---

# 🎫 Ticket #102 — User Account Disabled

## 📌 Issue Summary

A user attempted to log into the **Client01** workstation but was unable to authenticate.

The user received a message indicating that their Active Directory account had been disabled.

---

# 🔍 Investigation

The following troubleshooting steps were performed:

1. Opened **Active Directory Users and Computers (ADUC)** on DC01.

2. Located the affected user's account.

3. Reviewed the account status and confirmed the account was disabled.

---

# 🧠 Root Cause

The user's Active Directory account had been disabled as part of the employee offboarding process after completion of a previous freelance assignment.

The account remained disabled when the user attempted to access company resources again.

---

# 🛠️ Resolution

The following actions were performed:

- Enabled the user's Active Directory account.
- Confirmed the account status was active.
- Required the user to change their password after successful login verification.

---

# ✅ Verification

The issue was verified by:

- Logging into Client01 successfully.
- Confirming the user could authenticate.
- Confirming the user could change their password.

Verified:

- ✅ User account enabled
- ✅ Authentication restored
- ✅ User access restored

---

# 🎫 Ticket #103 — Group Policy Issue

## 📌 Issue Summary

A user logged into the **Client01** workstation and noticed that the system clock was missing from the notification area on the Windows taskbar.

The computer was functioning normally, but the clock was no longer visible.

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
- Forced a Group Policy refresh:

```powershell
gpupdate /force
```

---

# ✅ Verification

The fix was verified by:

- Logging the user out of Client01.
- Having the user log back into the workstation.
- Confirming the system clock was restored.

Verified:

- ✅ GPO settings updated successfully
- ✅ User received the corrected policy
- ✅ System clock displayed normally

---

# 📚 Day 11 Lessons Learned

## 🌐 DNS Troubleshooting

Learned that DNS issues must be separated from general network connectivity issues.

A domain computer requires proper DNS configuration to locate Active Directory services.

Key lesson:

> If a computer cannot locate the Domain Controller, verify DNS settings before troubleshooting Active Directory.

---

## 📡 DHCP and APIPA Troubleshooting

While troubleshooting DNS, Client01 received an APIPA address:

```text
169.254.x.x
```

This indicated that the workstation was unable to obtain an IP address from DHCP.

Key lesson:

> A computer with a 169.254.x.x address has a network connectivity or DHCP problem before it has a DNS problem.

---

## 🔑 Active Directory User Management

Learned how Help Desk technicians handle common identity issues:

- Disabled user accounts
- User authentication failures
- Password verification

Key lesson:

> User access issues are often resolved through Active Directory account management.

---

## ⚙️ Group Policy Troubleshooting

Learned how to troubleshoot policies applied through Active Directory.

Important tools:

```powershell
gpresult /r
```

and:

```powershell
gpresult /h report.html
```

Key lesson:

> Client computers do not manage domain policies. They receive policies from Active Directory and can be checked using Group Policy reporting tools.

---

# 🏁 Day 11 Summary

Completed troubleshooting scenarios:

| Ticket | Category | Skills Practiced |
|---|---|---|
| #101 | DNS Failure | DNS troubleshooting, network validation, domain connectivity |
| #102 | Disabled User Account | Active Directory user management |
| #103 | Group Policy Issue | GPO troubleshooting and verification |

Day 11 expanded the lab from basic configuration into realistic enterprise troubleshooting workflows.
