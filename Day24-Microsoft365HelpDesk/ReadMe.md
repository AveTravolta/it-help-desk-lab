# Day 24 – Microsoft 365 Help Desk Shift

## Overview

Day 24 focused on applying Microsoft 365 administration and Entra ID knowledge in a simulated Help Desk environment.

The goal was to practice handling common Microsoft 365 support requests involving user accounts, passwords, licensing, application access, security groups, shared mailboxes, and mailbox permissions.

This day built directly on the administration skills learned during Days 21–23.

---

## Skills Practiced

- Microsoft 365 user administration
- Microsoft Entra ID user management
- Password resets
- Account lockout and sign-in troubleshooting
- Microsoft 365 license assignment
- Microsoft 365 application access
- Security group membership
- Shared mailbox access
- Shared mailbox permissions
- Send As permissions
- User verification
- Account status investigation
- Help Desk ticket documentation
- User access troubleshooting
- Basic Microsoft 365 troubleshooting workflow

---

## Help Desk Workflow

For each ticket, I followed a basic troubleshooting and resolution process:

1. Identify the user's issue
2. Verify the user's account
3. Investigate account status, licenses, groups, or permissions
4. Determine the root cause
5. Make the required administrative change
6. Have the user test the solution when appropriate
7. Document the resolution and verification

This helped simulate how Microsoft 365 issues could be handled in an entry-level IT Help Desk or Microsoft 365 support environment.

---

# Tickets Completed

## Ticket #120 — User Cannot Access Teams

### Issue

User reported being unable to access Microsoft Teams.

### Actions

- Checked the user's Microsoft 365 license
- Confirmed the appropriate license was assigned
- Checked Microsoft service health
- Confirmed there was no active Microsoft service issue affecting Teams

### Resolution

Verified that the user's licensing and Microsoft service availability were normal and continued troubleshooting from the user-access side.

---

## Ticket #122 — Password Reset

### Issue

User was unable to access their account because of a password issue.

### Actions

- Located the user account in Microsoft Entra ID
- Verified the user
- Reset the user's password
- Provided the temporary password
- Had the user sign in with the new credentials

### Resolution

Password was successfully reset and the user regained account access.

---

## Ticket #123 — Account Unlock

### Issue

User reported being unable to sign in because their account was locked.

### Actions

- Located the user's account
- Investigated the account status
- Confirmed the account was locked
- Unlocked the account
- Had the user attempt to sign in again

### Resolution

Account was unlocked and access was restored.

---

## Ticket #124 — Assign License and Group Membership

### Issue

Mike Johnson required Microsoft 365 access and appropriate group membership.

### Actions

- Located Mike Johnson's account
- Checked existing group membership
- Confirmed that Mike did not have the required group membership
- Assigned the Microsoft 365 Business Standard license
- Added Mike to the appropriate group

### Resolution

Mike was licensed and added to the required group.

---

## Ticket #125 — I Don't Have Office Apps

### Issue

Mike Johnson had a Microsoft 365 Business Standard license but could not access the Office applications.

### Investigation

- Verified that Mike had the Microsoft 365 Business Standard license
- Checked the services included with the license
- Found that Office for the Web and Microsoft 365 Apps were not enabled

### Resolution

- Enabled Office for the Web
- Enabled Microsoft 365 Apps
- Had Mike log out and back into Microsoft 365

### Verification

Mike successfully logged back in and confirmed that the Office applications were available.

---

## Ticket #126 — I'm Locked Out

### Issue

David Brown reported that he was unable to access his account.

### Investigation

- Checked David Brown's account
- Found that the account was disabled
- Investigated sign-in failures
- Found no relevant failed sign-in events
- Contacted David's supervisor to verify that the account should be restored

### Resolution

- Removed the sign-in block
- Re-enabled David Brown's account

### Verification

David's account was restored and available for sign-in.

---

## Ticket #127 — I Forgot My Password

### Issue

Emily reported that she could not access her account because she forgot her password.

### Investigation

- Located Emily's account
- Verified her identity
- Checked for account restrictions or blocked access
- Confirmed that there were no account restrictions
- Confirmed that Emily had forgotten her password

### Resolution

Reset Emily's Microsoft 365 password.

### Verification

Emily was able to use the new password to access her account.

---

## Ticket #128 — Add Me to IT Support

### Issue

John requested access to IT Support resources.

### Investigation

- Verified that John needed access to the Oslo Support Project
- Confirmed that the project was represented by a security group
- Checked the group's membership
- Confirmed John was not currently a member
- Verified that Michael was the group owner
- Confirmed that membership would provide access to the IT Support shared mailbox
- Confirmed the requested access with Michael

### Resolution

Added John to the Oslo Support Project security group.

### Verification

Confirmed that John was now a member of the group and would receive the associated shared mailbox access.

---

## Ticket #129 — I Need to Be in the HR Group

### Issue

Sarah needed access to the HR shared mailbox.

### Investigation

- Checked Sarah's HR group membership
- Confirmed that Sarah was not a member
- Determined that membership in the HR group was required for access to the shared mailbox

### Resolution

Added Sarah to the HR group.

### Verification

Confirmed that Sarah's group membership provided access to the HR shared mailbox.

---

## Ticket #130 — New Employee Needs Mailbox

### Issue

A new employee needed Microsoft 365 access and a mailbox.

### Investigation

- Verified that the employee was new
- Confirmed that the employee required Microsoft 365 services
- Determined that the employee needed a license and application access

### Resolution

- Assigned the required Microsoft 365 license
- Enabled the required applications
- Provided a temporary password
- Had the employee sign in

### Verification

The employee successfully signed into Microsoft 365 and received access to the required applications and mailbox.

---

## Ticket #131 — Add Me to IT Support

### Issue

Sarah requested access to the IT Support shared mailbox.

### Investigation

- Checked Sarah's IT Support group membership
- Confirmed that Sarah was already a member of IT Support
- Verified that Sarah already had access to the Support shared mailbox

### Resolution

No additional configuration was required.

### Verification

Confirmed that Sarah was already properly configured for IT Support group and shared mailbox access.

---

## Ticket #132 — I Can Access Support But Cannot Send as Support

### Issue

Sarah could access the IT Support shared mailbox but could not send messages as the Support mailbox.

### Investigation

- Verified Sarah's membership in the IT Support shared mailbox
- Checked her existing mailbox permissions
- Confirmed that she had read/manage access
- Determined that she did not have Send As permission

### Resolution

- Added Send As permission for Sarah
- Had Sarah test sending an email as the Support mailbox

### Verification

Sarah successfully sent a test message as the Support mailbox.

---

# Microsoft 365 Administration Skills Demonstrated

During this Help Desk shift, I worked with several common Microsoft 365 administrative tasks:

### User Accounts

- Locate and verify users
- Check account status
- Enable and disable accounts
- Remove sign-in blocks
- Reset passwords
- Investigate account access issues

### Licensing

- Check assigned licenses
- Assign Microsoft 365 Business Standard
- Verify application services included with a license
- Enable Microsoft 365 Apps
- Enable Office for the Web

### Groups

- Review group membership
- Add users to security groups
- Use group membership to provide access to resources
- Verify group ownership

### Shared Mailboxes

- Verify shared mailbox access
- Troubleshoot shared mailbox access
- Understand group-based access to shared resources
- Configure Send As permissions
- Test Send As functionality

---

# Key Troubleshooting Lessons

## License Assignment Does Not Always Mean Application Access

A user can have a Microsoft 365 license assigned but still have individual services disabled.

For example, Mike Johnson had a Microsoft 365 Business Standard license but did not have Office for the Web or Microsoft 365 Apps enabled.

This reinforced the importance of checking both:

- The assigned license
- The individual services enabled within the license

---

## Account Status Matters

When troubleshooting sign-in problems, I learned to check more than just the user's password.

Important account checks include:

- Is the account enabled?
- Is sign-in blocked?
- Is the account locked?
- Are there account restrictions?
- Are there failed sign-in events?
- Does the user simply need a password reset?

---

## Group Membership Can Control Resource Access

Several tickets demonstrated how security groups can be used to control access to resources.

Instead of granting individual permissions to every user, users can be placed into the appropriate security group.

This allows group membership to control access to resources such as shared mailboxes.

---

## Shared Mailbox Access and Send As Are Different

A user can have access to a shared mailbox without necessarily being able to send email as that mailbox.

This was demonstrated in Ticket #132.

Sarah already had access to the Support shared mailbox, but she did not have the **Send As** permission.

After Send As was assigned, she was able to successfully send a test message as the Support mailbox.

---

# Tickets Not Completed

## Ticket #121 — New Employee Needs Outlook & Teams

This ticket was intentionally skipped for the current lab session.

The functionality overlapped with the Microsoft 365 account provisioning and application access tasks already practiced in other tickets.

Additional tickets were also not created after Ticket #132 because the remaining scenarios would have become increasingly redundant with the Microsoft 365 administration tasks already demonstrated.

---

# Day 24 Takeaways

Day 24 brought together the Microsoft 365 administration skills learned throughout Week 4 and applied them in a simulated Help Desk environment.

I practiced troubleshooting real-world scenarios involving:

- User account access
- Passwords
- Account lockouts
- Microsoft 365 licensing
- Office application access
- Security groups
- Shared mailboxes
- Mailbox permissions
- Send As permissions
- New employee provisioning

The biggest takeaway was learning to approach Microsoft 365 support issues systematically rather than immediately changing settings.

**Verify → Investigate → Identify Root Cause → Resolve → Verify**

This workflow will be used as a foundation for future Help Desk, Microsoft 365, Entra ID, and cloud administration work.

---

# Week 4 Progress

### Completed

- Day 21 — Microsoft 365 Admin Center
- Day 22 — Microsoft Entra ID
- Day 23 — Exchange Online
- Day 24 — Microsoft 365 Help Desk Shift

### Week 4 Skills

- Microsoft 365 Administration
- Microsoft Entra ID
- Exchange Online
- User Administration
- Password Management
- License Management
- Security Groups
- Shared Mailboxes
- Mailbox Permissions
- Help Desk Troubleshooting

---

## Lab Environment

- **Virtualization:** VirtualBox
- **On-Premises Server:** Windows Server 2022
- **Client:** Windows 11
- **Active Directory Domain:** sandoval.local
- **Cloud Identity:** Microsoft Entra ID
- **Cloud Platform:** Microsoft 365
- **License:** Microsoft 365 Business Standard

---

## Next Steps

Continue building Microsoft 365 and cloud administration experience before moving into the next section of the IT learning roadmap.

The goal is to continue connecting the on-premises Active Directory experience from earlier days with Microsoft Entra ID and Microsoft 365 cloud administration.

**Lab Status: Active**
