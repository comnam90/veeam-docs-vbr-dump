---
title: "Step 7. Specify User Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_adding_appliance_credentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Specify User Credentials


At the Credentials step of the wizard, specify a user whose credentials Veeam Backup & Replication will use to connect to the backup appliance.

For a user to be displayed in the Credentials list, it must be added to the Credentials Manager as described in [Standard Accounts](credentials_manager_windows.md). If you have not added the necessary user to the Credentials Manager beforehand, you can do it without closing the New Veeam Backup for Microsoft Azure Appliance wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

|  |
| --- |
| Important |
| The specified user must have multi-factor authentication (MFA) disabled and the Portal Administrator role assigned. |

If you try to add to the backup infrastructure an appliance that runs a version of Veeam Backup for Microsoft Azure that is not compatible with the version of Veeam Backup & Replication, Veeam Backup & Replication will display a warning notifying that the appliance must be upgraded. To eliminate the warning, click Yes. Veeam Backup & Replication will automatically upgrade the appliance to the necessary version. Note that the Microsoft Azure compute account specified at [step 3](azure_adding_appliance_account.md) must have permissions required to upgrade the appliance. For more information, see [Plug-In Permissions](azure_plugin_permissions.md).

When you add a backup appliance to the backup infrastructure, Veeam Backup & Replication automatically verifies the TLS certificate installed on the appliance:

* If the certificate is trusted, Veeam Backup & Replication saves a thumbprint of the certificate in the configuration database. When Veeam Backup & Replication connects to the appliance, it uses the saved thumbprint to verify the appliance identity and to avoid the man-in-the-middle attack.
* If the certificate is not trusted, Veeam Backup & Replication does not save a thumbprint of the certificate in the configuration database. When Veeam Backup & Replication connects to the appliance, the appliance is shown in the Veeam Backup & Replication console as unavailable.

|  |
| --- |
| Important |
| * Do not change the role of a Veeam Backup for Microsoft Azure user whose credentials are used by Veeam Backup & Replication to connect to the backup appliance. * If you change the password of a Veeam Backup for Microsoft Azure user whose credentials are used by Veeam Backup & Replication to connect to the backup appliance, you must also change this user password in the Veeam Backup & Replication console as described in [Editing and Deleting Credentials Records](credentials_edit_delete.md). Otherwise, the connection will not be established. |

![Step 7. Specify User Credentials](images/azure_connect_azure_appliance_credentials.webp)

Page updated 2026-06-26

