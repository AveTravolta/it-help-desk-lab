# 🖥️ Day 17 — Shared Folders & Network Shares

## 📖 Overview

Today focused on creating and managing **Windows Network Shares** in a Windows Server Active Directory environment.

The goal of this lab was to understand how organizations share files across a network, configure Share and NTFS permissions, verify user access from a domain-joined client, and troubleshoot permission-related issues.

This lab builds directly on the previous day's NTFS Permissions lab by demonstrating how users access shared resources over the network and how Share Permissions interact with NTFS Permissions.

---

# 🎯 Objectives

- Create a network shared folder on Windows Server
- Configure Share Permissions
- Configure NTFS Permissions
- Understand the difference between local folders and shared folders
- Access shared folders from a domain-joined client computer
- Verify user permissions using different Active Directory accounts
- Troubleshoot and resolve permission-related issues

---

# 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Server | DC01 |
| Client | CLIENT01 |
| Operating System | Windows Server 2022 |
| Client OS | Windows 11 |
| Domain | sandoval.local |

---

# 🛠️ Lab Tasks Completed

## 1. Created a Company Shared Folder

Created the following folder on **DC01**:

```text
C:\CompanyShares
```

Configured the folder as a Windows Network Share so it could be accessed by domain users from another computer on the network.

---

## 2. Configured NTFS Permissions

Disabled permission inheritance and converted inherited permissions into explicit permissions for easier management.

Configured the following NTFS permissions:

| Security Group | Permission |
|---------------|------------|
| HR Staff | Read |
| Sales Staff | Read |
| IT Staff | Modify |

This configuration allows HR and Sales users to view files while restricting modification privileges to the IT department.

---

## 3. Configured Share Permissions

Configured the shared folder with the following Share Permission:

| Group | Permission |
|------|------------|
| Domain Users | Change |

This allows authenticated domain users to connect to the shared folder while NTFS permissions determine the user's effective level of access.

---

## 4. Accessed the Share from CLIENT01

Logged into **CLIENT01** using different Active Directory user accounts and connected to the shared folder using its Universal Naming Convention (UNC) path.

Example:

```text
\\DC01\CompanyShares
```

Verified that the shared folder was accessible across the network.

---

## 5. Verified User Permissions

### HR Staff

Confirmed that an HR user could:

- View folders
- Open files
- Browse subfolders

Confirmed the HR user **could not**:

- Create files
- Modify files
- Delete files

This verified that the Read permission was functioning correctly.

---

### IT Staff

Logged in using an IT user account.

Verified the IT user could:

- Open files
- Create new files
- Modify existing files
- Save changes successfully

Created a test text document to confirm Modify permissions were working as expected.

---

## 6. Permission Troubleshooting

Performed additional testing by intentionally modifying permissions to simulate a real-world support scenario.

Verified that incorrect permissions prevented expected access and restored the correct permissions to resolve the issue.

This demonstrated the importance of validating both Share Permissions and NTFS Permissions when troubleshooting file access problems.

---

# 📚 Key Concepts Learned

During this lab I learned:

- How Windows Network Shares work
- The purpose of Share Permissions
- The purpose of NTFS Permissions
- How Share and NTFS permissions work together
- Why the most restrictive permission becomes the effective permission
- How to access shared folders using a UNC path
- How to verify user access from a client computer
- Basic permission troubleshooting techniques

---

# 🔍 Share Permissions vs NTFS Permissions

## Share Permissions

Share Permissions determine what users are allowed to do when accessing a folder over the network.

Common permissions include:

- Read
- Change
- Full Control

---

## NTFS Permissions

NTFS Permissions determine what users can do within the folder itself.

Common permissions include:

- Read
- Modify
- Full Control

---

## Effective Permissions

Windows evaluates both Share Permissions and NTFS Permissions.

The **most restrictive permission** becomes the user's effective permission.

Example:

| Share Permission | NTFS Permission | Effective Permission |
|-----------------|-----------------|----------------------|
| Change | Read | Read |
| Full Control | Modify | Modify |

---

# 💼 Real-World Relevance

Shared folders are used in nearly every business environment to centralize files and allow employees to collaborate securely.

Help Desk and Desktop Support technicians frequently receive requests involving:

- Access Denied errors
- Missing shared folders
- Incorrect file permissions
- Requests for department folder access
- Permission changes for new employees

Understanding how Share Permissions and NTFS Permissions interact is an essential skill for IT Support, Desktop Support, and System Administration roles.

---

# 📸 Screenshots

Include screenshots of:

- CompanyShares folder
- Shared Folder Properties
- Share Permissions
- NTFS Security Permissions
- HR user accessing the shared folder
- IT user creating a test file
- Successful access from CLIENT01
- Permission troubleshooting

---

# ✅ Skills Gained

After completing this lab, I can:

- Create Windows Network Shares
- Configure Share Permissions
- Configure NTFS Permissions
- Manage access using Active Directory security groups
- Access shared folders from a domain-joined client
- Verify user permissions
- Troubleshoot and resolve file access issues
- Explain how Share Permissions and NTFS Permissions work together
