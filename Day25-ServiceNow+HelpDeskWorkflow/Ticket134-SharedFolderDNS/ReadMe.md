# 📁 Ticket 134 — Shared Folder Access / DNS Troubleshooting

**Incident:** INC-TICKET-003  
**Category:** Software  
**Channel:** Phone  
**Priority:** 4 - Low  
**State:** On Hold

---

## 📝 User Issue

John Smith reported being unable to access the company's shared folder.

The initial symptom was that John could not access:

```text
\\DC01\CompanyShares
```

Kenny Rogers, another domain user, was able to access the share.

---

## 🔍 Troubleshooting

### 1. Verified John's Account

John Smith was confirmed to be logged into the domain as:

```text
sandoval\john
```

His relevant Active Directory group memberships were:

- HR Staff
- HRtoSales

---

### 2. Checked Network Connectivity

CLIENT01 was able to successfully communicate with DC01.

```text
Ping DC01
4 packets received
0 packets lost
```

Basic network connectivity was therefore working.

---

### 3. Checked Existing Network Connections

The following command was used:

```cmd
net use
```

No existing network connections were listed.

---

### 4. Checked Folder Permissions

The `IT` folder under:

```text
C:\CompanyShares\IT
```

contained the following permission entries:

- IT Staff
- HR Staff
- Sales Staff
- HRtoSales
- Administrator

Relevant permissions included:

- HR Staff — Read & Execute
- HRtoSales — Modify

No permission changes were made during troubleshooting.

---

### 5. Compared Hostname vs. IP Access

John was unable to access:

```text
\\DC01\CompanyShares
```

However, John was successfully able to access:

```text
\\10.1.10.2\CompanyShares
```

This was an important troubleshooting result.

The share itself was working and John's account was capable of accessing it.

---

### 6. DNS Troubleshooting

DNS queries for DC01 repeatedly timed out.

The following tests were performed:

```cmd
nslookup DC01
```

and:

```cmd
nslookup DC01 10.1.10.2
```

Both resulted in DNS timeouts.

The DNS Server service on DC01 was confirmed to be running.

DNS Manager was also checked and confirmed to be listening on all IP addresses.

---

## 🎯 Findings

The evidence indicated that the underlying problem was **DNS/name resolution** rather than the CompanyShares permissions.

John could access the share using the server's IP address:

```text
\\10.1.10.2\CompanyShares
```

but could not access it using the hostname:

```text
\\DC01\CompanyShares
```

This isolated the problem to hostname resolution/DNS.

---

## ⏸️ Ticket Status

The incident was placed **On Hold** because the underlying DNS issue had been identified but not repaired during this lab session.

No unnecessary permission changes were made to resolve the user's issue.

---

## 💡 What I Learned

This ticket demonstrated the importance of isolating a problem before changing permissions or account settings.

The troubleshooting process was:

**User reports problem**  
→ Verify account  
→ Verify connectivity  
→ Check existing connections  
→ Check permissions  
→ Test hostname  
→ Test IP address  
→ Identify DNS/name-resolution issue  
→ Document findings

The IP-vs-hostname test was particularly useful because it demonstrated that the network share itself was functioning.

---

## 🛠️ Tools Used

- ServiceNow
- Windows Server 2022
- Windows 11
- Active Directory Users and Computers
- DNS Manager
- Command Prompt
- `ping`
- `ipconfig`
- `nslookup`
- `net use`
