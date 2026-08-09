---
title: "Step 3. Specify Microsoft Azure Compute Account Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_adding_appliance_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Microsoft Azure Compute Account Settings


At the Account step of the wizard, select a Microsoft Azure compute account whose permissions will be used to connect the backup appliance.

For a Microsoft Azure compute account to be displayed in the Microsoft Azure compute account drop-down list, it must be added to the Cloud Credentials Manager as described in [Microsoft Azure Compute Accounts](restore_azure_acc_name.md). If you have not added the necessary credentials to the Cloud Credentials Manager beforehand, you can do it without closing the New Veeam Backup for Microsoft Azure Appliance wizard. To do that, click either the Manage accounts link or the Add button, and complete the Microsoft Azure Compute Account wizard.

For each newly created account, Veeam Backup & Replication creates a new Microsoft Entra application in your Microsoft Entra ID. The application is automatically assigned the Key Vault Crypto User, Owner and Storage Queue Data Contributor [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles). Note that the Owner role has a wide scope of permissions and capabilities. If you want the application to be assigned a limited list of permissions, create an application [manually in Microsoft Azure](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal). For more information on the required permissions that must be assigned to the Microsoft Entra application, see [Plug-In Permissions](azure_plugin_permissions.md).

|  |
| --- |
| Important |
| Microsoft Azure Stack Hub accounts are not supported. |

![Step 3. Specify Microsoft Azure Compute Account Settings](images/azure_connect_azure_appliance_account.webp)

Page updated 2026-06-26

