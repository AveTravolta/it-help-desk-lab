# 🖥️ Day 16 — File Shares & NTFS Permissions

## 🎯 Objective

The goal of Day 16 was to learn how Windows Server manages access to files and folders in a domain environment.

This lab focused on:

- Creating file share folders
- Understanding NTFS permissions
- Understanding Share Permissions
- Using Active Directory security groups
- Learning permission inheritance
- Understanding cumulative permissions
- Testing effective access

The goal was to understand how IT administrators control access to company resources.

---

# 🏢 Lab Environment

## Server

**DC01**

- Windows Server 2022
- Active Directory Domain Services
- Domain Controller
- File Share Host

## Client

**Client01**

- Windows 11
- Joined to the domain
- Used for permission testing

## Domain


sandoval.local


---

# 📁 File Share Folder Structure

Created a file share folder structure on DC01:


C:\File Shares

├── HR
├── IT
└── Sales


These folders were created to simulate department-based file storage in a company environment.

---

# 👥 Active Directory Security Groups

Created department-based security groups:


HR Staff
IT Staff
Sales Staff


Each group represents a department and will be used to manage folder access.

A major lesson from this lab was that permissions should be assigned to groups instead of individual users.

Instead of:


User → Folder Permission


A better approach is:


User
↓
Security Group
↓
Folder Permission


This makes managing access easier when employees join, leave, or change departments.

---

# 🔐 NTFS Permissions

## What Are NTFS Permissions?

NTFS permissions control what users can do with files and folders stored on an NTFS-formatted drive.

NTFS permissions are configured through:


Folder
→ Properties
→ Security


---

# NTFS Permission Levels Learned

## Read

Allows users to:

- View files and folders
- Open files
- Read file contents
- View file attributes

---

## Modify

Allows users to:

- Read files
- Edit files
- Create files
- Delete files

---

## Full Control

Allows users to:

- Modify files
- Change permissions
- Take ownership

---

# ➕ Cumulative Permissions

Learned that permissions from multiple groups can combine.

Example:

A user belongs to multiple groups:


Group A
→ Read

Group B
→ Modify


The user's effective permission becomes:


Modify


because permissions accumulate from all applicable group memberships.

---

# 🚫 Deny Permissions

Learned how Deny permissions work.

Deny permissions override Allow permissions.

Example:

Allow Modify
+
Deny Access

No Access


Because Deny can override normal permissions, it should be used carefully.

---

# ⚠️ Avoiding Deny Permissions

A best practice learned during this lab:

- Avoid using Deny unless necessary
- Use proper group organization
- Keep permissions simple and easy to troubleshoot

Poorly managed Deny permissions can create difficult access issues later.

---

# 🧬 Permission Inheritance

Learned how Windows uses inheritance to automatically apply permissions from parent folders to child folders.

Example:


C:\File Shares

    |
    |
   HR

    |
    |
  File.txt

Permissions can flow down through the folder structure.

---

# 🛑 Disabling Inheritance

Learned how to disable inheritance when a folder requires unique permissions.

Path:


Folder
→ Properties
→ Security
→ Advanced
→ Disable Inheritance


This allows administrators to manually configure permissions instead of using inherited settings.

---

# 🌐 Share Permissions

## What Are Share Permissions?

Share Permissions control access when users connect to a folder over the network.

Example network path:

`\\DC01\HR`

Share Permissions are configured through:

**Folder → Properties → Sharing → Advanced Sharing → Permissions**

Share Permissions determine what level of access a user has when accessing a folder remotely.

---

# 🔄 NTFS Permissions vs Share Permissions

NTFS Permissions and Share Permissions work together to determine a user's final access.

The most restrictive permission takes precedence.

## Example

### Share Permission

**IT Staff**

Permission:

`Read`

### NTFS Permission

**IT Staff**

Permission:

`Modify`

### Effective Permission

`Read Only`

Even though NTFS allows Modify access, the Share Permission limits the user's access to Read.

---

# 🧪 Permission Testing

Testing was performed from:

**Client01**

The goal was to verify how Share Permissions and NTFS Permissions combine when accessing resources over the network.

Example tested:

**Share Permission:**
`Read`

**NTFS Permission:**
`Modify`

Result:

- User could access the folder
- User could view files
- User could not modify files

The final access was limited by the more restrictive Share Permission.

---

# 🛠️ Troubleshooting Approach

When troubleshooting file access issues:

1. Check the user account
2. Check Active Directory group membership
3. Check Share Permissions
4. Check NTFS Permissions
5. Verify Effective Access

This process helps identify where permission issues are occurring.

---

# 🧠 Key Takeaways

## Active Directory

Manages:

- Users
- Groups
- Computer accounts

---

## Security Groups

Manage:

- Which users receive permissions
- Department-based access
- Resource access control

---

## NTFS Permissions

Control:

- What actions users can perform on files and folders
- Read access
- Modify access
- Full Control access

---

## Share Permissions

Control:

- Network access to shared folders
- Access when connecting through paths like:

`\\DC01\HR`

---

# 🎓 Skills Learned

- Windows Server File Shares
- Active Directory Security Groups
- NTFS Permissions
- Share Permissions
- Permission Inheritance
- Cumulative Permissions
- Deny Permissions
- File Access Troubleshooting

---

# 🚀 Lab Summary

Day 16 connected Active Directory security groups with real-world file access management.

The workflow learned:

`User → Active Directory Group → Share Permissions → NTFS Permissions → Effective Access`

This lab demonstrated how IT administrators manage and troubleshoot file access in Windows domain environments.
