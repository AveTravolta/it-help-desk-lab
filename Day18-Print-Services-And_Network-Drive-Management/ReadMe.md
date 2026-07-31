# 🖥️ Day 18 — Print Services & Network Drive Management

## 🎯 Overview

Today focused on managing shared business resources in a Windows Server Active Directory environment.

The goal was to simulate common Help Desk and Junior System Administrator responsibilities, including:

- Windows Print Server management
- Shared printer creation
- Printer permissions
- Printer troubleshooting
- Network share access
- Group Policy mapped drive deployment
- Reviewing PowerShell administration concepts

The lab environment:

```
DC01
Windows Server 2022
Domain: sandoval.local

Client01
Windows 11
Domain Joined
```

---

# 🖨️ Part 1 — Windows Print Services

## 📚 Concepts Learned

Reviewed how organizations manage printers using a centralized Windows Print Server.

Instead of every user manually installing printers, companies can host printers from a central server and deploy them to users.

Example:

```
User Computer
      |
      |
   Network
      |
      |
 Windows Print Server
      |
      |
 Shared Printer
```

---

# ⚙️ Print Server Configuration

Installed and reviewed:

```
Print and Document Services
```

Configured a shared printer on:

```
DC01
```

Created:

```
HR-Printer
```

Verified the printer could be accessed from:

```
Client01
```

Users were able to connect to the shared printer through:

```
\\DC01\HR-Printer
```

---

# 👥 Printer Permissions

Reviewed printer permissions:

| Permission | Description |
|---|---|
| Print | Allows users to print |
| Manage Documents | Allows users to manage print jobs |
| Manage Printer | Allows users to modify printer settings |

Example permission model:

```
HR Staff
    |
    └── Print

IT Staff
    |
    └── Manage Printer
```

---

# 🎫 Ticket #113 — Printer Offline

## Issue

User reported:

> "I cannot print. The printer says offline."

---

## Investigation

Reviewed common printer offline troubleshooting steps:

- Verified printer availability
- Checked printer status
- Reviewed Print Spooler service
- Reviewed possible communication issues between the client and printer

Checked Print Spooler service using:

```powershell
Get-Service Spooler
```

The Print Spooler service was verified as running.

---

## Resolution

Reviewed restarting the Print Spooler service as a common troubleshooting step.

Command reviewed:

```powershell
Restart-Service Spooler
```

Also reviewed pausing/resuming print operations and checking printer status.

---

## Verification

Confirmed the printer was accessible from the client machine.

---

# 🎫 Ticket #114 — Printer Queue Problems

## Issue

User reported:

> "My documents are stuck printing."

---

## Investigation

Reviewed printer queue troubleshooting:

Checked for:

- Stuck print jobs
- Failed documents
- Print Spooler issues

Reviewed the print queue through Windows printer management tools.

---

## Resolution

Reviewed clearing print queues by restarting the Print Spooler service and removing stuck spool files.

Commands reviewed:

Stop Print Spooler:

```powershell
Stop-Service Spooler
```

Clear print queue files:

```
C:\Windows\System32\spool\PRINTERS
```

Start Print Spooler:

```powershell
Start-Service Spooler
```

---

# 📁 Part 2 — Network Drives & File Server Management

## 🎯 Objective

Learn how businesses provide employees access to shared company files.

Topics covered:

- File server structure
- Shared folders
- UNC paths
- Network drive mapping
- Group Policy drive deployment
- User-based access control

---

# 🗄️ File Server Structure

Reviewed company file server organization:

```
DC01

C:\CompanyShares

├── HR
├── IT
├── Sales
└── Finance
```

Reviewed how users normally access files through network shares instead of browsing server folders directly.

Example:

Server folder:

```
C:\CompanyShares\IT
```

Shared network path:

```
\\DC01\IT
```

Mapped drive:

```
I:
```

---

# 🔐 Permissions Review

Reviewed best practices for file permissions:

❌ Avoid assigning permissions directly to users

✅ Assign permissions through security groups

Example:

```
IT Staff
    |
    └── Modify Access

HR Staff
    |
    └── Modify Access
```

---

# 🌐 Group Policy Drive Mapping

Created and tested a Group Policy Object:

```
IT Drive Mapping
```

Configured:

```
User Configuration
        |
        └── Preferences
              |
              └── Windows Settings
                    |
                    └── Drive Maps
```

Created mapped drive:

```
I: → \\DC01\IT
```

Tested deployment from:

```
Client01
```

Verified users could access the mapped network drive.

---

# 🔧 Group Policy Troubleshooting Practice

Reviewed troubleshooting steps for mapped drives:

1. Verify user account
2. Verify group membership
3. Verify GPO linking
4. Verify security filtering
5. Verify network share availability
6. Verify permissions

Commands reviewed:

Force Group Policy Update:

```cmd
gpupdate /force
```

View applied Group Policies:

```cmd
gpresult /r
```

---

# 🧠 PowerShell Administration Review

Reviewed previously learned PowerShell administration commands.

Commands reviewed:

View services:

```powershell
Get-Service
```

Find commands:

```powershell
Get-Command
```

View command help:

```powershell
Get-Help
```

Navigate directories:

```powershell
Get-Location

Set-Location
```

---

# 💼 Skills Practiced

By completing Day 18, I practiced:

✅ Windows Print Server administration  
✅ Shared printer configuration  
✅ Printer permissions  
✅ Printer troubleshooting  
✅ Print queue troubleshooting  
✅ File server organization  
✅ Network shares  
✅ UNC paths  
✅ Group Policy drive mapping  
✅ User and group based access control  
✅ PowerShell administration basics  

---

# 📝 Real Help Desk Scenarios Simulated

This lab simulated tickets such as:

🎫 "I cannot print to the office printer."

🎫 "The printer is showing offline."

🎫 "My print jobs are stuck."

🎫 "My department drive disappeared."

🎫 "I need access to a shared folder."

---

# ⭐ Day 18 Summary

Today I gained hands-on experience managing shared Windows resources in an Active Directory environment.

I practiced configuring shared printers, troubleshooting printer issues, deploying mapped network drives through Group Policy, and managing file server resources.

These tasks simulate responsibilities commonly handled by:

- Help Desk Technicians
- Desktop Support Technicians
- Junior System Administrators
