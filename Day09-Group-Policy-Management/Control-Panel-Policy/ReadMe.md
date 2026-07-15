# 🖥️ Day 9 — Control Panel Restriction Policy

## Overview

Created a Group Policy Object (GPO) to restrict access to Control Panel and Windows Settings for users in the Inventory Organizational Unit (OU).

This simulated an enterprise environment where administrators restrict user access to system configuration settings.

---

# 🎯 Objective

Prevent Inventory users from accessing Control Panel and PC Settings.

---

# 🛠️ Implementation

## Created Inventory Organizational Unit

Created a new Organizational Unit:

**Inventory OU**

Moved the test user:

**Pickles Pugsley**

into the Inventory OU.

---

## Created Control Panel Disable Policy

Created a new Group Policy Object:

**Control Panel Disable Policy**

The policy was linked to the Inventory Organizational Unit (OU).

---

## Configured Control Panel Restriction

Navigated to:

**User Configuration → Policies → Administrative Templates → Control Panel**

Enabled:

**Prohibit access to Control Panel and PC Settings**

---

## Testing

Forced a Group Policy update:

```cmd
gpupdate /force
```

Logged in as the Inventory user and verified:

- Control Panel access was blocked
- Windows Settings access was restricted

---

# 📚 Skills Practiced

- Creating Organizational Units
- Linking GPOs to specific OUs
- Applying user restrictions
- Testing domain policies
- Understanding GPO scope
