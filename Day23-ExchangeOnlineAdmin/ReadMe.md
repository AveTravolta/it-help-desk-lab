# 📧 Day 23 — Exchange Online Administration

## 🎯 Objective

Learn the fundamentals of **Exchange Online administration** through the Microsoft Exchange Admin Center and Microsoft 365 Admin Center.

The focus was on managing mailboxes, email aliases, distribution lists, shared mailboxes, and mailbox permissions in a simulated Microsoft 365 environment.

---

## 📚 Learning Resources

### 🎥 Andy Malone MVP — Microsoft Exchange Online for Beginners

Completed a beginner-focused Exchange Online training video covering:

- Microsoft 365 Admin Center and Exchange Admin Center
- Creating users and mailboxes
- Licensing
- Exchange Admin Center navigation
- Group mailboxes
- Contact types
- Exchange administrative roles
- Mailbox management
- Exchange administration concepts

The video was used as an outside learning resource before completing the hands-on lab.

---

# 🧪 Hands-On Lab

## 📬 User Mailboxes

Explored user mailboxes through the Exchange Admin Center and reviewed how Exchange manages user email addresses and mailbox information.

Learned the distinction between:

- Microsoft 365 user/account administration
- Exchange mailbox administration
- Entra ID identity management

---

## 🏷️ Email Aliases

Configured and verified an additional email alias for a test user.

### Example

Primary mailbox address:

`KirkJ@MichaelSandoval.onmicrosoft.com`

Additional alias:

`KirkJames@MichaelSandoval.onmicrosoft.com`

Verified that the alias appeared in Exchange as an additional `smtp` address while the uppercase `SMTP` address remained the primary mailbox address.

Learned that multiple email addresses can point to the same mailbox.

---

## 👥 Distribution Lists

Created an **IT Support** distribution list and added test users as members.

Tested the distribution list by sending an email to the group's address.

### Result

The message was successfully distributed to the members' individual mailboxes.

This demonstrated that a distribution list functions as a centralized mailing address that distributes messages to its members.

---

## 📥 Shared Mailbox

Created an **IT Shared Mailbox**:

`ITSharedMailbox@MichaelSandoval.onmicrosoft.com`

Verified that Exchange identified the mailbox as:

**Recipient Type: SharedMailbox**

Configured mailbox delegation for a test user.

### Permissions practiced:

- **Full Access**
- **Send As**

Learned that these permissions serve different purposes:

**Full Access:**  
Allows a user to open and work with the shared mailbox.

**Send As:**  
Allows a user to send messages that appear to come directly from the shared mailbox.

---

## 🔐 Permission Testing

Tested shared mailbox permissions by changing access levels and observing the resulting behavior.

This demonstrated the difference between mailbox access and sending permissions.

A user may have **Send As** permission without having the ability to open and work inside the mailbox.

Full Access is required for normal mailbox access, while Send As controls the ability to send as the shared mailbox.

---

# 🧠 Key Concepts Learned

- Exchange Online provides cloud-based email and mailbox administration.
- User mailboxes belong to individual users.
- Email aliases provide additional addresses for the same mailbox.
- Distribution lists distribute messages to members' individual mailboxes.
- Shared mailboxes provide a common mailbox that multiple users can access.
- Full Access and Send As are separate mailbox permissions.
- Microsoft 365 Admin Center, Exchange Admin Center, and Entra ID have overlapping but different administrative responsibilities.
- Cloud administration changes may take time to propagate before appearing in Outlook.

---

# 🛠️ Help Desk Skills Practiced

Today's lab introduced several real-world Help Desk scenarios involving:

- User mailbox administration
- Email alias management
- Distribution list membership
- Shared mailbox access
- Mailbox permissions
- Send As permissions
- Basic Exchange troubleshooting
- Verifying configuration changes
- Troubleshooting cloud administration changes that do not immediately appear

---

# ✅ Day 23 Status

**Completed**

- ✅ Exchange Online fundamentals
- ✅ User mailbox exploration
- ✅ Email aliases
- ✅ Distribution lists
- ✅ Distribution list testing
- ✅ Shared mailbox creation
- ✅ Full Access permissions
- ✅ Send As permissions
- ✅ Mailbox permission troubleshooting
- ✅ Exchange Admin Center navigation
- ✅ Microsoft 365 Admin Center vs. Exchange Admin Center vs. Entra ID

---

## 🏆 Summary

Day 23 provided hands-on experience administering **Exchange Online** in a simulated Microsoft 365 environment.

The lab focused on understanding how organizations manage user mailboxes, aliases, distribution lists, shared mailboxes, and mailbox permissions while practicing basic troubleshooting and verification of cloud-based administrative changes.
