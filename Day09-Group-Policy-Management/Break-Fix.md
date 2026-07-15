## Issue

A Group Policy Object (GPO) was created and linked successfully, but the policy was not applying to the intended users.

The Wallpaper Policy and Control Panel Disable Policy appeared in Group Policy Management, but users were not receiving the expected settings.

Symptoms:

- GPO appeared in Group Policy Management
- Policy settings were not applying
- Group Policy Results showed:

```
None (Unknown reason)
```

---

# 🔍 Troubleshooting

Investigated the following:

- Verified GPO links in Group Policy Management
- Confirmed users were located in the correct Organizational Units (OUs)
- Reviewed Security Filtering settings
- Checked GPO permissions
- Verified Authenticated Users permissions

Forced Group Policy refresh:

```cmd
gpupdate /force
```

Verified applied policies:

```cmd
gpresult /r
```

---

# 🛠️ Root Cause

The GPO Security Filtering configuration was incorrect.

The:

**Authenticated Users**

permission was removed without properly replacing the required permissions.

This prevented users from reading and applying the Group Policy Object.

---

# ✅ Resolution

Restored:

**Authenticated Users**

to the GPO Security Filtering section.

After correcting permissions:

- Wallpaper Policy applied successfully
- Control Panel restriction applied successfully
- Users received the intended settings

---

# 📚 Lessons Learned

- GPO linking and GPO permissions are separate concepts
- Security Filtering controls who can apply a GPO
- Removing Authenticated Users requires proper replacement permissions
- Organizational Units determine GPO scope
- `gpupdate /force` and `gpresult /r` are important troubleshooting tools
