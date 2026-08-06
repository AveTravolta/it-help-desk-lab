# 🖥️ Day 21 — Microsoft 365 Administration & Help Desk

## 🎯 Objective

Learn the fundamentals of Microsoft 365 administration from a Help Desk perspective, including user management, licensing, applications and services, password resets, Microsoft 365 Groups, Teams, service health, and basic troubleshooting.

This lab used a real Microsoft 365 Business Standard trial tenant to practice administrative tasks and realistic Help Desk scenarios.

---

# 📚 What I Learned

## 🖥️ Microsoft 365 Admin Center

Learned how the Microsoft 365 Admin Center serves as the central administrative portal for managing an organization's Microsoft 365 environment.

Practiced navigating:

* Home
* Users
* Teams & Groups
* Billing
* Reports
* Settings
* Service Health

---

## 👤 User Management

Learned how to:

* Locate users through **Active Users**
* Review user account information
* Identify account status
* View assigned licenses
* Review assigned applications and services
* Create new Microsoft 365 users
* Understand the difference between standard users and administrator accounts

---

## 💳 Microsoft 365 Licensing

Learned that a Microsoft 365 license determines which Microsoft 365 products and services are available to a user.

Worked with:

**Microsoft 365 Business Standard**

Reviewed how licenses relate to services such as:

* Outlook / Exchange Online
* Microsoft Teams
* OneDrive
* Other Microsoft 365 applications and services

---

## 🔐 Password Management

Located the Microsoft 365 password reset workflow for users.

Learned that an administrator can:

* Generate a temporary password
* Require the user to change their password at their next sign-in
* Initiate a password reset from the user's Active Users profile

The password reset was reviewed as a training exercise without actually changing the test user's password.

---

## 👥 Microsoft 365 Groups & Teams

Learned the differences between several Microsoft 365 group types and collaboration tools.

### Microsoft 365 Groups

Can provide shared resources such as:

* Shared mailbox
* Shared calendar
* Shared document library
* Group membership
* Collaboration resources

### Microsoft Teams

Learned that Teams integrates with Microsoft 365 Groups and provides additional collaboration functionality such as:

* Teams
* Channels
* Chat
* Meetings
* Collaboration features

### Security Groups

Learned that Security Groups are commonly used to manage access and permissions to resources and can also be used for other identity and access management purposes.

### Distribution Lists

Learned that Distribution Lists are primarily used to distribute email messages to a group of recipients.

---

## 👑 Owners, Members & Administrators

Inspected an existing Microsoft 365 Group and identified the distinction between:

* **Owner** — manages the group and certain membership/settings
* **Member** — participates in the group's resources
* **Administrator** — has administrative permissions based on assigned Microsoft 365 administrator roles

Learned that being a group owner does not automatically make someone a Microsoft 365 administrator.

---

## 📊 Microsoft 365 Service Health

Learned how to use **Service Health** to determine whether Microsoft is experiencing an active service incident or advisory.

Used Service Health during a Teams troubleshooting scenario to verify that Microsoft Teams was operating normally.

This demonstrated the importance of checking for widespread service issues before troubleshooting an individual user's computer.

---

# 🎫 Help Desk Ticket #120 — User Cannot Access Microsoft Teams

## 📝 Issue

User **John Smith — Sales** reported:

> "I can't access Microsoft Teams. I was told I should have access."

## 🔎 Investigation

* Located John Smith through Active Users.
* Verified that his account was active.
* Verified that Microsoft 365 Business Standard was assigned.
* Reviewed Apps & Services.
* Confirmed Microsoft Teams was enabled.
* Checked Microsoft 365 Service Health.
* Confirmed Microsoft Teams was healthy with no active service issue.
* User reported that Teams opened briefly and then closed without displaying an error.
* Outlook and OneDrive were functioning normally.

## 🔧 Troubleshooting & Resolution

* Asked the user to access Teams through the Microsoft 365 web interface.
* Teams worked successfully through the web interface.
* This helped isolate the issue to the Teams desktop application rather than the user's Microsoft 365 account or the Teams service.
* Had the user restart their computer.
* Teams opened and functioned normally after the restart.

## 🧠 Root Cause

Temporary Teams desktop application/client issue.

The exact underlying cause could not be determined, but restarting the computer resolved the issue.

## ✅ Verification

* User successfully opened Teams after restarting the computer.
* User confirmed Teams was functioning normally.
* Ticket resolved and closed.

---

# 🎫 Help Desk Ticket #121 — New Employee Outlook & Teams Access

## 📝 Issue

**User:** Sarah Sherman — HR

Manager reported:

> "Sarah started today but cannot access Outlook or Microsoft Teams. She should have access."

## 🔎 Investigation

* Searched Microsoft 365 Admin Center → Users → Active Users.
* Confirmed that Sarah Sherman did not have an existing Microsoft 365 user account.

## 🔧 Resolution

* Created a new Microsoft 365 user account for Sarah Sherman.
* Assigned **Microsoft 365 Business Standard**.
* Enabled Microsoft Teams.
* Verified that the appropriate Microsoft 365 services were available.
* Confirmed Outlook / Exchange Online access was available.

## 🧠 Root Cause

Sarah's Microsoft 365 user account had not been provisioned, preventing her from accessing Microsoft 365 services.

## ✅ Verification

* Had Sarah sign in and verify access to Outlook.
* Had Sarah sign in and verify access to Microsoft Teams.
* Confirmed both services were accessible and functioning normally.

---

# 🧪 Skills Practiced

* Microsoft 365 Admin Center navigation
* Microsoft 365 tenant administration
* Active User management
* User account creation
* Microsoft 365 Business Standard licensing
* Application and service assignment
* Password reset workflow
* Microsoft 365 Group management
* Understanding Teams and Microsoft 365 Groups
* Security Groups vs. Distribution Lists
* Administrator roles
* Service Health investigation
* Cloud-side troubleshooting
* Desktop application troubleshooting
* Browser-based troubleshooting/isolation
* New employee provisioning
* Help Desk ticket documentation
* User communication
* Issue verification and resolution

---

# 🧠 Help Desk Troubleshooting Process

This lab reinforced a structured approach to troubleshooting Microsoft 365 issues:

**Identify the issue**
↓
**Investigate the user's account**
↓
**Verify licensing and services**
↓
**Check Microsoft Service Health**
↓
**Isolate the problem**
↓
**Troubleshoot**
↓
**Resolve**
↓
**Verify with the user**
↓
**Document the ticket**

---

# 📸 Lab Evidence

Screenshots were captured throughout the lab to document administrative actions and troubleshooting.

Evidence includes:

* Microsoft 365 Admin Center
* User account creation
* Microsoft Teams enabled for a user
* Microsoft Teams Service Health
* User/service configuration

Sensitive information such as passwords and other private tenant information should not be included in the public repository.

---

# 🎯 Key Takeaways

The biggest lesson from this lab was that Microsoft 365 Help Desk troubleshooting should not begin with assumptions.

A user saying:

> "Teams doesn't work."

doesn't immediately mean Teams is broken.

The technician should investigate:

**Account → License → Services → Service Health → Client → User Environment**

and use evidence to isolate the actual problem.

This lab provided hands-on experience administering Microsoft 365 users and services while practicing realistic Help Desk troubleshooting and documentation.
