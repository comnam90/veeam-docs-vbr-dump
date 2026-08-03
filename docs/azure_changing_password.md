---
title: "Changing User Passwords"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_changing_password.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changing User Passwords


For backup appliance user accounts, you can change the password specified while creating the account.

|  |
| --- |
| Note |
| Consider the following:   * Passwords of accounts whose user identities were obtained from an identity provider cannot be changed by any user accounts, including their own. These passwords can only be changed on the identity provider side. * If your backup appliance is managed by a Veeam Backup & Replication server and you change the password of a user whose credentials Veeam Backup & Replication uses to connect to the backup appliance, you must also change this user password in the Veeam Backup & Replication console as described in [Editing and Deleting Credentials Records](credentials_edit_delete.md). Otherwise, the connection will not be established. |

To change the password, do the following:

1. Switch to the Configuration page.
2. Navigate to Accounts > Portal Users.
3. Select the user account and click Change Password.
4. In the Change Password window, enter the currently used password, enter and confirm a new password, and then click OK.

|  |
| --- |
| Tip |
| You can change a password of a user that is currently logged in as described in section [Changing Default Admin Password](azure_changing_default_admin_password.md). |

[![Changing User Passwords](images/azure_changing_password.webp)](images/azure_changing_password.webp "Changing User Passwords")

Page updated 2026-07-01

