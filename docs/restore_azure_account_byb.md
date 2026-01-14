---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_account_byb.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you add a Microsoft Azure Compute account to Veeam Backup & Replication, check the following prerequisites:

* If you plan to use a new Microsoft Entra ID (formerly Azure Active Directory) application to access Microsoft Azure (at the [Account Type](restore_azure_acc_account.md) step), consider the following:

* Make sure that you already have a user account in Microsoft Entra ID. This account must have privileges listed in section [Permissions](required_permissions.md#azure_compute).

* If you have multiple tenants associated with the Microsoft Entra user account that you plan to use to create a new application, Veeam Backup & Replication will create the application in the home tenant of the account. As a result, the application will have access only to the subscriptions of the home tenant, as well as the Azure Compute account will. If you want to use another tenant and its subscriptions, follow the instructions in [this Veeam KB article](https://www.veeam.com/kb4108).

* The created Microsoft Entra application is assigned the Contributor, Key Vault Crypto User, Storage Blob Data Contributor and Storage Queue Data Contributor role privileges for the subscriptions for which the following conditions are met:

* The subscriptions are linked to the home tenant of the Microsoft Entra user.
* The Microsoft Entra user has access to these subscriptions and can assign roles on the subscription level for the registered application.

You can limit the subscriptions to which Veeam Backup & Replication assigns the privileges as described in [this Veeam KB article](https://www.veeam.com/kb4406). For more information on roles, see [Microsoft Azure Docs](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-built-in-roles#owner).

* If you plan to use an existing Microsoft Entra ID (formerly Azure Active Directory) application to access Microsoft Azure (at the [Account Type](restore_azure_acc_account.md) step), consider the following:

* Make sure that you already have a Microsoft Entra application. For more information on how to create it, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#register-an-application-with-azure-ad-and-create-a-service-principal). Note that you do not need to configure redirect URI.
* The Microsoft Entra application must have privileges listed in section [Permissions](required_permissions.md#azure_compute).
* Only subscriptions that belong to the selected tenant will be added.

* [If you plan to restore Linux workloads using [helper appliances](restore_azure_acc_lin.md)] Veeam Backup & Replication uses its built-in credentials record to work with all helper appliances. For security reasons, we recommended that you change a password for this account before you set up the helper appliances. Changing credentials is required only once. For more information, see [Changing Credentials for Helper Appliances](restore_azure_credentials.md).
* On the backup server, you must set the correct time according to the timezone where the backup server is located. Otherwise, you may not be able to add a Microsoft Azure user account to Veeam Backup & Replication.

* When the internet access is possible only through HTTP/HTTPS proxy, you must configure the proxy settings for the Local System account or account under which the Veeam Backup Service is running. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/configure-proxy-internet).

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
