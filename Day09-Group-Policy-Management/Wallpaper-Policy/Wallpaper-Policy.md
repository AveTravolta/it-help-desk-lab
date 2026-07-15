## Overview

Created a Group Policy Object (GPO) to centrally manage desktop wallpaper settings for domain users.

This simulated a common enterprise task where administrators control user desktop configurations through Active Directory Group Policy.

---

# 🎯 Objective

Create and apply a wallpaper policy to users inside the Golf Employees Organizational Unit (OU).

---

# 🛠️ Implementation

## Created Wallpaper Policy GPO

Created a new Group Policy Object:

**Wallpaper Policy**

The policy was linked to the:

**Golf Employees Organizational Unit (OU)**

---

## Configured Desktop Wallpaper Settings

Navigated to:

**User Configuration → Policies → Administrative Templates → Desktop → Desktop → Desktop Wallpaper**

Configured the following:

- Enabled the Desktop Wallpaper policy
- Selected a wallpaper image stored on the client machine
- Applied the wallpaper setting to domain users

---

## Testing

Verified the policy by logging into a domain user account on the client machine.

Forced Group Policy update:

```cmd
gpupdate /force
```

Confirmed the wallpaper policy applied successfully.

---

# 📚 Skills Practiced

- Creating Group Policy Objects
- Linking GPOs to Organizational Units
- Configuring User Configuration policies
- Testing Group Policy changes
- Managing user desktop settings
