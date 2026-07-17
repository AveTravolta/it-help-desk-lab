# 🎫 Ticket #101 — DNS Failure

## 📌 Issue Summary

A user reported that after restarting **Client01**, they were unable to access company network resources.

The user received an error indicating that the computer could not locate a **logon server**, preventing normal domain authentication.

---

# 🔍 Investigation

## Initial Troubleshooting

The following troubleshooting steps were performed:

1. Connected to the **Client01** workstation.
2. Verified the network adapter was active and the computer had network connectivity.
3. Attempted to ping the Domain Controller to verify communication with the Active Directory server.

```powershell
ping DC01
```

4. Reviewed the workstation's network configuration:

```powershell
ipconfig /all
```

The investigation focused on verifying:

- IP address configuration
- Default gateway
- DNS server settings
- Domain connectivity

---

# 🧠 Root Cause

The Client01 workstation was configured with an incorrect preferred DNS server:

```
Preferred DNS Server: 8.8.8.8
```

The workstation was unable to properly locate Active Directory services because domain-joined computers rely on internal DNS hosted by the Domain Controller.

Active Directory services such as:

- Domain authentication
- Logon server discovery
- Group Policy processing
- Domain resource access

require the client computer to use the internal AD DNS server.

---

# 🛠️ Resolution

The DNS configuration on Client01 was corrected.

Updated DNS settings:

```
Preferred DNS Server: 10.1.10.2
```

The workstation was then refreshed:

```powershell
ipconfig /flushdns
```

DNS registration was renewed:

```powershell
ipconfig /registerdns
```

---

# ✅ Verification

The issue was verified by completing the following checks:

## Confirm DNS Configuration

```powershell
ipconfig /all
```

Confirmed:

- DNS server pointed to DC01
- Correct domain configuration was restored

## Test Domain Connectivity

Successfully tested communication with the Domain Controller:

```powershell
ping DC01
```

## Confirm Name Resolution

Verified the domain could resolve correctly:

```powershell
nslookup sandoval.local
```

The workstation was able to communicate with Active Directory services successfully.

---

# 🏁 Final Status

✅ DNS configuration restored  
✅ Client01 successfully communicated with DC01  
✅ Domain authentication restored  
✅ Network resources accessible again  

**Ticket Status: Resolved**
