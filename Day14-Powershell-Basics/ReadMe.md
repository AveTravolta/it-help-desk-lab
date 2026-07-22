# 🖥️ Day 14 – PowerShell Basics for IT Administrators

## Overview

Day 14 introduced the fundamentals of **Windows PowerShell** from an IT administration perspective. The objective was to become comfortable using PowerShell as a command-line management tool rather than relying solely on the Windows graphical interface.

Rather than focusing on scripting, this lab emphasized discovering commands, navigating the file system, viewing system information, managing Windows services, and understanding how PowerShell assists with day-to-day Help Desk and Systems Administration tasks.

The lab was completed using **Windows PowerShell 5.1** on the **DC01 Windows Server 2022** virtual machine.

---

# 📚 Microsoft Learn

Completed the introductory **Get Started with Windows PowerShell** learning path.

Topics covered included:

- What Windows PowerShell is
- Why PowerShell is used by IT professionals
- Cmdlets and the Verb-Noun naming convention
- PowerShell execution policies
- Windows PowerShell ISE
- Checking the installed PowerShell version
- Basic PowerShell concepts

---

# 🛠️ PowerShell Commands Practiced

## Viewing PowerShell Version

```powershell
$PSVersionTable
```

Verified the installed version of Windows PowerShell.

---

## Discovering Commands

```powershell
Get-Command
```

Displayed every available PowerShell command installed on the system.

Also searched for commands related to services, processes, and networking.

```powershell
Get-Command *service*

Get-Command *process*

Get-Command *network*

Get-Command *net*
```

This demonstrated how administrators discover commands instead of memorizing every cmdlet.

---

## Using the Help System

```powershell
Get-Help Get-Service
```

Used PowerShell's built-in documentation to learn how cmdlets function.

Attempted:

```powershell
Get-Help Get-Service -Examples
```

However, examples were unavailable because the local help files had not been downloaded.

---

## Viewing Windows Services

```powershell
Get-Service
```

Displayed every Windows service and its current status.

Filtered services using the pipeline:

```powershell
Get-Service | Where-Object Status -eq "Running"
```

```powershell
Get-Service | Where-Object Status -eq "Stopped"
```

This introduced the concept of using the PowerShell pipeline (`|`) to pass objects between commands.

---

## Viewing Running Processes

```powershell
Get-Process
```

Displayed all currently running processes on the server.

Also practiced exporting command output:

```powershell
Get-Process >> C:\Users\Administrator\Desktop\Process.txt
```

This appended the process list to a text file located on the Administrator Desktop, demonstrating PowerShell output redirection for documentation and reporting.

---

## Navigating the File System

Displayed the current directory:

```powershell
Get-Location
```

Listed files and folders:

```powershell
Get-ChildItem
```

Changed directories:

```powershell
Set-Location C:\
```

```powershell
Set-Location C:\Users
```

These commands provided basic command-line navigation similar to using Windows File Explorer.

---

# 🔧 Break / Fix Exercise

A basic Windows service troubleshooting exercise was performed using the **Print Spooler** service.

Checked the service status:

```powershell
Get-Service spooler
```

Stopped the service:

```powershell
Stop-Service spooler
```

Verified the service had stopped:

```powershell
Get-Service spooler
```

Restarted the service:

```powershell
Start-Service spooler
```

Confirmed the service was running again:

```powershell
Get-Service spooler
```

This simulated a common Help Desk troubleshooting task where restarting a Windows service can resolve application issues.

---

# ⚠️ Troubleshooting

While exploring PowerShell's built-in help system, the following command was tested:

```powershell
Get-Help Get-Service -Examples
```

The examples section was unavailable because the local PowerShell help files had not been downloaded.

An attempt was made to update the help files using:

```powershell
Update-Help
```

However, the lab's **DC01** virtual machine does not currently have external internet connectivity, preventing PowerShell from downloading the latest help content from Microsoft.

The lab continued using the available built-in help documentation.

---

# 🎯 Skills Learned

- Navigated Windows PowerShell using common cmdlets
- Learned the PowerShell Verb-Noun command structure
- Used `Get-Command` to discover available cmdlets
- Used `Get-Help` to view command documentation
- Viewed and filtered Windows services
- Viewed running processes
- Navigated the Windows file system using PowerShell
- Used the PowerShell pipeline to filter command output
- Exported command output to a text file using output redirection
- Performed a basic Windows service troubleshooting exercise
- Documented a real-world PowerShell troubleshooting scenario involving offline help files

---

# 💡 Key Takeaways

PowerShell is a powerful administration tool used throughout Windows environments. While graphical interfaces remain useful, PowerShell provides administrators with faster methods of gathering information, troubleshooting systems, managing services, and automating repetitive tasks.

This lab focused on learning the core PowerShell commands commonly used by Help Desk Technicians and Junior Systems Administrators before progressing into scripting and automation in future labs.
