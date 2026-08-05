---
title: "Changing User Passwords"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_accounts_vba_users_password.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changing User Passwords


For user accounts of the backup appliance, you can change the password specified while creating the account:

|  |
| --- |
| Important |
| * You cannot change the password for a user account whose user identity was obtained from an identity provider.  * If your backup appliance is managed by a Veeam Backup & Replication server and you change the password of a user whose credentials Veeam Backup & Replication uses to connect to the backup appliance, you must also change this user password in the Veeam Backup & Replication console as described in section [Editing and Deleting Credentials Records](credentials_edit_delete.md). Otherwise, the connection will not be established. |

1. Switch to the Configuration page.

1. Navigate to Accounts > Portal Users.

1. Select the user account and click Change Password.

1. In the Change Password window, enter the currently used password, enter and confirm a new password, and then click Change.

[![Changing User Password](images/aws_users_change_password.webp)](images/aws_users_change_password.webp "Changing User Password")

Page updated 2026-05-21

