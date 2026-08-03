---
title: "Compute Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_compute_accounts.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Compute Accounts


The Microsoft Azure Compute account is required to restore workloads to Microsoft Azure, add Azure archive storage and so on. For more information, see [Microsoft Azure Compute Accounts](restore_azure_accounts.md).

The following permissions are required for adding a Microsoft Azure Compute account.

Compute Accounts

| Microsoft Entra ID (formerly Azure Active Directory) Application | Permissions |
| New (select the Create a new account option at the [Subscription](restore_azure_acc_account.md) step of the wizard) | The Microsoft Entra ID user account where the application will be created must have the following permissions:   * To register applications. For this, you can assign the Global Administrator role to the user, or enable the Users can register applications option for the user in the Azure portal. For details, see [Microsoft Azure Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-how-applications-are-added). * To assign a role on the subscription level for the registered application. For this, you can use the Owner\* role or if the Owner role cannot be used, you can create a custom role with minimal permissions. To learn how to create a custom role, see [Creating Custom Role for Azure and Azure Stack Hub Accounts](azure_custom_role.md#hub_new).   \* — When you assign a privileged role, like Owner, using the Azure Portal, the default conditions can be added to this role assignment. With these default conditions, adding the Compute account will fail. To avoid this issue, select the Allow user to assign all roles (highly privileged) option. For more information on conditions, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal#delegate-condition). |
| Existing (select the Use the existing account option at the [Subscription](restore_azure_acc_account.md) step of the wizard) | The application must have the Contributor role for the selected subscription. If you restore workloads to Microsoft Azure Stack Hub and cannot use the Contributor role, you can create a custom role with minimal permissions. To learn how to create a custom role, see [Creating Custom Role for Azure and Azure Stack Hub Accounts](azure_custom_role.md#hub_ex). |

Page updated 2026-07-21

