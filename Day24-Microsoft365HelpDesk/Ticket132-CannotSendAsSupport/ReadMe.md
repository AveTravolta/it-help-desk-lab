## Ticket #132 — I Can Access Support But Cannot Send as Support

### Issue

Sarah could access the IT Support shared mailbox but was unable to send messages as the Support mailbox.

### Investigation

- Verified that Sarah was a member of the IT Support shared mailbox
- Checked Sarah's existing mailbox permissions
- Confirmed that Sarah had read/manage access but did not have Send As permission

### Root Cause

Sarah did not have the Send As permission required to send email using the IT Support shared mailbox address.

### Resolution

- Added Send As permission for Sarah on the IT Support shared mailbox
- Had Sarah test sending an email as the Support mailbox

### Verification

- Sarah successfully sent a test email as the Support mailbox
- Confirmed that Send As permission was working correctly
- Issue resolved successfully
