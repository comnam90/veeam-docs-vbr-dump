---
title: "Before you Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entraid_before_you_begin.html"
last_updated: "12/11/2024"
product_version: "13.0.1.1071"
---

# Before you Begin


Before you add a Microsoft Azure storage account with Microsoft Entra authorization to Veeam Backup & Replication, check the following prerequisites:

* If you plan to use a new Microsoft Entra application to access storage account (at the [Account Type](entraid_access.md) step), consider the following:

* Make sure that you already have a user account in Microsoft Entra ID. This account must have privileges listed in the [Permissions](required_permissions.md#entraid) section.

* If you have multiple tenants associated with the Microsoft Entra user account that you plan to use to create a new application, Veeam Backup & Replication will create the application in the home tenant of the account. As a result, the application will have access only to the subscriptions of the home tenant, as well as the Azure Compute account will. If you want to use another tenant and its subscriptions, follow the instructions in [this Veeam KB article](https://www.veeam.com/kb4108).

* The created Microsoft Entra application is assigned with the following roles for a storage account which name was entered at the [Name step of the wizard](entraid_name.md):

* Storage Account Contributor
* Storage Blob Data Contributor
* Storage Blob Data Owner

For more information on roles, see [Microsoft Azure Docs](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-built-in-roles#owner).

You can limit the subscriptions to which Veeam Backup & Replication assigns the privileges as described in [this Veeam KB article](https://www.veeam.com/kb4406).

* If you plan to use an existing Microsoft Entra application to access storage account (at the [Account Type](entraid_access.md) step), consider the following:

* Create a Microsoft Entra application beforehand. For more information on how to create it, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#register-an-application-with-azure-ad-and-create-a-service-principal). Note that you do not need to configure redirect URI.
* The Microsoft Entra application must have several role privileges assigned on a storage account. For more information, see [Permissions](required_permissions.md#entraid).
* Only storage accounts from subscriptions that belong to the applications tenant can be used.

* On the backup server, you must set the correct time according to the timezone where the backup server is located. Otherwise, you may not be able to add a Microsoft Entra user account to Veeam Backup & Replication.

* When the internet access is possible only through HTTP/HTTPS proxy, you must configure the proxy settings for the Local System account or account under which the Veeam Backup Service is running. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/configure-proxy-internet).


