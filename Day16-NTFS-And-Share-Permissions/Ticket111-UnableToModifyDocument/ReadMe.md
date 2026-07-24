## Ticket #111 — User Unable to Modify HR Documents

### Issue

An IT user was able to access HR documents but was unable to modify or save changes to files.

---

### Investigation

* Reviewed NTFS permissions and confirmed the IT Staff group had **Modify** permissions.
* Reviewed Share Permissions and discovered the IT Staff group was limited to **Read** access.

---

### Root Cause

The user was receiving **Modify** permissions through NTFS permissions, but Share Permissions were restricting the user to **Read-only** access when accessing the folder through the network share.

---

### Resolution

* Updated Share Permissions from **Read** to **Change** for the IT Staff group.
* Verified that the user was able to modify HR documents successfully.

---

### Verification

* User logged back into the client machine.
* Attempted to modify the HR document.
* Confirmed the user could successfully edit and save changes.

