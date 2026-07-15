## 🎯 Objective

The goal of this break/fix exercise was to simulate a DHCP failure and troubleshoot why a client machine was unable to receive a valid IP address.

This exercise focused on identifying DHCP issues, recognizing APIPA addresses, and restoring normal network connectivity.

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

# 💥 Issue Introduced

To simulate a DHCP outage, the active DHCP scope was intentionally deactivated.

Steps performed:

1. Opened the DHCP Management Console on DC01
2. Navigated to the active DHCP scope
3. Right-clicked the scope
4. Selected:

Deactivate

---

# 🔍 Troubleshooting Process

After deactivating the DHCP scope, troubleshooting was performed on Client01.

First, the current DHCP lease was released:

ipconfig /release

Then, Client01 attempted to request a new DHCP lease:

ipconfig /renew

The client was unable to obtain a valid IP address from the DHCP server.

---

# 🧪 Verification

Used the following command to inspect the client's network configuration:

ipconfig /all

The client received an APIPA address:

169.254.x.x

This confirmed:

- Client01 was unable to communicate with the DHCP server
- The DHCP scope was unavailable
- Windows automatically assigned an APIPA address because no DHCP lease was available

---

# 🛠️ Resolution

Returned to the DHCP Management Console on DC01.

Steps performed:

1. Located the DHCP scope
2. Reactivated the DHCP scope

Activate

After restoring the DHCP scope, returned to Client01 and requested a new lease:

ipconfig /renew

---

# ✅ Verification After Fix

Confirmed that Client01 successfully received a DHCP lease again.

Results:

IPv4 Address: 10.1.10.110

Verified:

- Client01 received a valid IP address from DHCP
- DHCP server was responding correctly
- Network configuration was restored

---

# 🧠 What I Learned

During this break/fix exercise I learned:

- How DHCP failures affect client connectivity
- How APIPA addresses indicate DHCP communication problems
- How to use ipconfig commands for troubleshooting
- How to verify whether a client has a valid DHCP lease
- How to restore DHCP functionality after a scope failure

---

# 🔧 Troubleshooting Commands Used

View network configuration:

ipconfig /all

Release current DHCP lease:

ipconfig /release

Request a new DHCP lease:

ipconfig /renew
