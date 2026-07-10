# Week 1 Reflection — IT Help Desk / Cloud Admin Lab

## Overview

During the first week of this lab, I built and documented a Windows Server Active Directory environment designed to simulate a small business IT support environment.

The goal was to move beyond simply learning concepts and practice the actual workflow used by Help Desk Technicians and System Administrators: building infrastructure, managing users, troubleshooting issues, and documenting solutions.

---

# What I Built

During Week 1, I created:

- A Windows Server Domain Controller (`DC01`)
- An Active Directory domain (`sandoval.local`)
- A Windows 11 domain-joined client machine (`Client01`)
- Active Directory users, organizational units, and security groups
- DNS configuration for domain communication
- A simulated Help Desk ticket environment

The lab now represents a small business network where users can authenticate, access resources, and experience common IT support issues.

---

# Skills Practiced

## Active Directory Administration

I practiced:

- Installing and configuring Active Directory Domain Services
- Creating and managing user accounts
- Creating organizational units
- Managing security groups
- Modifying user access and permissions
- Troubleshooting account-related issues

---

## Windows Server Administration

I practiced:

- Creating and managing a Domain Controller
- Installing server roles
- Understanding the relationship between Active Directory and DNS
- Managing domain services

---

## DNS Troubleshooting

I learned how important DNS is in an Active Directory environment.

I practiced:

- Understanding name resolution
- Checking client DNS configuration
- Using `nslookup` to verify DNS communication
- Troubleshooting domain connectivity issues

---

## Help Desk Troubleshooting

One of the biggest lessons from this week was learning how to approach technical issues using a structured troubleshooting process.

Each ticket followed:

```
Issue
↓
Investigation
↓
Root Cause
↓
Resolution
↓
Verification
```

I simulated common workplace tickets including:

- Account lockouts
- Password resets
- Disabled user accounts
- DNS issues
- Group membership problems

---

# Challenges Faced

One of the biggest challenges during this lab was understanding how the different components work together.

At the beginning, Active Directory, DNS, domain controllers, and client machines felt like separate technologies.

After building the environment, I developed a better understanding of how they depend on each other:

- Active Directory manages identities
- DNS allows systems to locate domain services
- Domain Controllers authenticate users
- Client machines rely on these services to function correctly

Troubleshooting issues helped reinforce these relationships.

---

# Biggest Takeaways

The biggest takeaway from Week 1 was that IT support is not just about fixing individual problems.

A good technician needs to:

- Understand the environment
- Ask the right questions
- Identify the root cause
- Apply the correct fix
- Verify the solution
- Document the process

Documentation is just as important as the technical solution because it allows problems to be repeated, reviewed, and improved.

---

# Career Connection

This lab helped bridge the gap between my software development background and my goal of moving into IT Support, Systems Administration, and eventually Cloud Administration.

The skills practiced in this environment are foundational technologies used in many enterprise environments:

- Active Directory
- Windows Server
- DNS
- User management
- Troubleshooting
- Technical documentation

Future goals for this lab include expanding into:

- Group Policy
- PowerShell automation
- File permissions
- Microsoft 365 administration
- Azure cloud services
- Cloud identity management

---

# Week 1 Summary

Week 1 transformed this project from a simple technical exercise into a documented IT support simulation.

I built the environment, created users, joined clients, configured services, resolved issues, and documented the troubleshooting process.

The next phase will focus on expanding the environment and building additional system administration and cloud-focused skills.
