# 🎫 Day 25 — ServiceNow + Help Desk Workflow

## 🎯 Overview

Today I added **ServiceNow** to my IT Help Desk lab and practiced working through realistic user incidents.

The focus was learning how ServiceNow fits into a Help Desk environment while using my existing Windows/Active Directory lab to perform the actual technical troubleshooting.

> **ServiceNow tracks and documents the work. The technical tools are used to perform the fix.**

---

## 🧰 Tools Used

- ServiceNow Personal Developer Instance
- VirtualBox
- Windows Server 2022
- Windows 11
- Active Directory Users and Computers (ADUC)
- DNS Manager
- Command Prompt

> **Lab Note:** My VirtualBox environment is completely isolated and is not connected to a real network.

---

## 🎫 Incident Management

I practiced creating and managing ServiceNow incidents, including:

- Creating incidents
- Categorizing tickets
- Setting impact and urgency
- Understanding automatic priority
- Updating ticket states
- Adding work notes
- Documenting troubleshooting
- Adding resolution notes
- Resolving and placing tickets on hold

---

## 🔐 Ticket 132 — Windows Login

Worked through a simulated Windows login issue involving an outdated password.

Practiced documenting the user's issue and resolution in ServiceNow.

---

## 🔒 Ticket 133 — Account Lockout

Worked through an Active Directory account lockout.

Using **ADUC**, I:

- Verified the account was locked
- Unlocked the account
- Reset the password
- Tested the user's authentication

I then documented the technical work in ServiceNow and resolved the incident.

---

## 📁 Ticket 134 — Shared Folder Access

Worked through a shared-folder access issue involving `CompanyShares`.

I compared a user who could access the share with the user experiencing the problem and performed troubleshooting involving:

- Active Directory authentication
- Group membership
- Share permissions
- NTFS permissions
- Network connectivity
- DNS/name resolution
- `ping`
- `nslookup`
- `net use`

A key troubleshooting discovery was that the affected user could access:

\\10.1.10.2\CompanyShares

but not

\\DC01\CompanyShares

This pointed toward a DNS/name-resolution issue rather than simply a permissions problem.

🧠 What I Learned

The biggest takeaway from Day 25 was understanding how ServiceNow and technical IT tools work together.

A typical Help Desk workflow looks like:

User reports problem
        ↓
Create ServiceNow ticket
        ↓
Troubleshoot using IT tools
        ↓
Fix the problem or identify the cause
        ↓
Document the work in ServiceNow
        ↓
Resolve or escalate the ticket

ServiceNow is much more than a ticketing system, but for an entry-level Help Desk role, incident management and ticket documentation are some of the most important areas to understand.

Day 25 Takeaway

Today connected my previous Active Directory, Windows Server, DNS, and file-sharing labs with a realistic Help Desk workflow.

The goal going forward is not just knowing how to use individual IT tools, but being able to:

Understand the user's problem → troubleshoot systematically → perform the appropriate fix → document the work professionally.
