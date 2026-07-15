## 🎯 Objective

The goal of this lab was to install and configure a **DHCP Server** role on Windows Server and verify that client machines could automatically receive IP addresses from the DHCP server.

This lab focused on learning how DHCP works in an Active Directory environment, including scopes, exclusions, leases, and client verification.

---

# 🏢 Lab Environment

**Domain Controller:**
- Server Name: DC01
- Operating System: Windows Server 2022
- Domain: sandoval.local

**Client Machine:**
- Client Name: Client01
- Operating System: Windows 11
- Joined to: sandoval.local

---

# 🛠️ DHCP Configuration

## Installed DHCP Role

Installed the DHCP Server role through:

Server Manager → Add Roles and Features → DHCP Server

After installation, DHCP was authorized within Active Directory.

---

# 🌐 DHCP Scope Configuration

Created a DHCP scope for the existing lab network.

## Scope Details

**Scope Name:**

sandoval.local DHCP Scope

**IP Address Range:**

Start: 10.1.10.100  
End: 10.1.10.200

**Subnet Mask:**

255.0.0.0

**Prefix Length:**

/8

---

# 🚫 DHCP Exclusion Range

Created an exclusion range to reserve addresses from being automatically assigned.

10.1.10.100 - 10.1.10.109

This allows those addresses to remain available for potential static assignments.

---

# ⚙️ Scope Options

Configured DHCP options:

## Default Gateway

10.1.10.1

## DNS Server

10.1.10.2

## Domain Name

sandoval.local

---

# 💻 Client Verification

Configured Client01 to obtain an IP address automatically.

Used:

ipconfig /all

Verified that Client01 successfully received a DHCP lease.

## Results

Client01 received:

IPv4 Address: 10.1.10.110

Verified:

- DHCP Enabled: Yes
- DHCP Server: 10.1.10.2
- DNS Server: 10.1.10.2

---

# 🧠 What I Learned

During this lab I learned:

- How to install the DHCP Server role on Windows Server
- How DHCP scopes control automatic IP assignment
- How exclusions reserve IP addresses
- How DHCP works with Active Directory environments
- How to verify DHCP leases using command-line tools
- How client machines receive network configuration automatically

---

# 🔧 Tools Used

- Windows Server Manager
- DHCP Management Console
- Command Prompt
- ipconfig /all
- ipconfig /release
- ipconfig /renew
