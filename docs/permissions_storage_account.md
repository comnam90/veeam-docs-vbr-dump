---
title: "Storage Accounts (Entra ID)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_storage_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Storage Accounts (Entra ID)


The Microsoft Azure storage account with Microsoft Entra ID authorization is required to add Azure Blob storage, Azure archive storage, and so on. For more information, see [Microsoft Azure Storage Accounts (Entra ID)](azure_entra_id.md).

The following permissions are required for the existing Microsoft Azure storage account with Microsoft Entra ID authorization.

Storage Accounts (Entra ID)

| Microsoft Entra ID (formerly Azure Active Directory) Application | Permissions |
| New (select the Create a new account option at the [Account Type](entraid_access.md) step of the wizard) | When adding a Microsoft Azure Stack Hub Compute account, the Microsoft Entra ID user account where the Microsoft Entra ID application will be created must have the following permissions:   * To register applications. For this, you can assign the Global Administrator privileges to the user or enable the Users can register applications option for the user in the Azure portal. For details, see [Microsoft Azure Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-how-applications-are-added). * To assign a role on the subscription level for the registered application. For this, you can use the Owner role or if the Owner role cannot be used, you can create a custom role with minimal permissions. To learn how to create a custom role, see [Creating Custom Role for Azure and Azure Stack Hub Accounts](azure_custom_role.md#hub_new). |
| Existing (select the Use the existing account option at the [Account Type](entraid_access.md) step of the wizard) | The application must have the following role privileges for the selected storage account:   * Storage Account Contributor * Storage Blob Data Contributor * Storage Blob Data Owner   For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles). |

Page updated 2026-07-21

