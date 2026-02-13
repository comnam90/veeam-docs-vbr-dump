---
title: "Creating Custom Role for Azure Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_custom_role.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Creating Custom Role for Azure Account


Granular permissions differ depending on whether you create an Azure Stack Hub account, or Azure Compute account using a new Microsoft Entra ID (formerly Azure Active Directory) application, or Azure Compute account using an existing Microsoft Entra application.

|  |
| --- |
| Note |
| This section describes permissions required for Veeam Backup & Replication to perform tasks. If you need to perform other tasks, for example create virtual networks, add the required permissions for those tasks manually.  Instead of granular permissions, you can use built-in roles. For more information, see [Permissions](required_permissions.md#azure_compute). |

Permissions for Azure Compute Account (Existing Application)

If you plan to add an Azure Compute account using an existing Microsoft Entra ID (formerly Azure Active Directory) application (select the Use the existing account option at the [Access Type](restore_azure_acc_account.md) step of the wizard), and you do not want to use built-in Azure roles, you can create a custom role with granular permissions:

1. In the Azure Portal, go to subscription properties and open Access control (IAM).
2. Create a custom role from a JSON file as described in [Microsoft Docs](https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles-portal#step-6-json). Use the following JSON. In the assignableScopes field, specify your subscription ID.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)JSON — Permissions for Existing Application

|  |  |
| --- | --- |
| |  | | --- | | {     "properties": {         "roleName": "VBR Azure Compute Account 13.x",         "description": "Permissions needed for an application for an Azure Compute Account",         "assignableScopes": [             "/subscriptions/your\_subscription\_ID\_here"         ],         "permissions": [             {                 "actions": [                     "Microsoft.Storage/storageAccounts/listkeys/action",                     "Microsoft.Storage/storageAccounts/read",                     "Microsoft.Storage/storageAccounts/write",                     "Microsoft.Storage/storageAccounts/delete",                     "Microsoft.Storage/storageAccounts/queueServices/queues/delete",                     "Microsoft.Storage/storageAccounts/queueServices/queues/read",                     "Microsoft.Storage/storageAccounts/queueServices/queues/write",                                 "Microsoft.Storage/storageAccounts/blobServices/containers/read",                     "Microsoft.Storage/storageAccounts/blobServices/containers/write",                     "Microsoft.Storage/storageAccounts/blobServices/containers/delete",                     "Microsoft.Storage/storageAccounts/blobServices/generateUserDelegationKey/action",                       "Microsoft.Network/locations/checkDnsNameAvailability/read",                     "Microsoft.Network/virtualNetworks/read",                     "Microsoft.Network/virtualNetworks/write",                     "Microsoft.Network/virtualNetworks/delete",                     "Microsoft.Network/virtualNetworks/subnets/join/action",                     "Microsoft.Network/virtualNetworks/subnets/read",                     "Microsoft.Network/virtualNetworks/subnets/write",                     "Microsoft.Network/virtualNetworks/subnets/delete",                     "Microsoft.Network/publicIPAddresses/read",                     "Microsoft.Network/publicIPAddresses/write",                     "Microsoft.Network/publicIPAddresses/delete",                     "Microsoft.Network/publicIPAddresses/join/action",                     "Microsoft.Network/networkInterfaces/read",                     "Microsoft.Network/networkInterfaces/write",                     "Microsoft.Network/networkInterfaces/delete",                     "Microsoft.Network/networkInterfaces/join/action",                     "Microsoft.Network/networkSecurityGroups/read",                     "Microsoft.Network/networkSecurityGroups/write",                     "Microsoft.Network/networkSecurityGroups/delete",                     "Microsoft.Network/networkSecurityGroups/join/action",                       "Microsoft.Compute/locations/vmSizes/read",                     "Microsoft.Compute/locations/usages/read",                     "Microsoft.Compute/virtualMachines/read",                     "Microsoft.Compute/virtualMachines/write",                     "Microsoft.Compute/virtualMachines/delete",                     "Microsoft.Compute/virtualMachines/start/action",                     "Microsoft.Compute/virtualMachines/restart/action",                     "Microsoft.Compute/virtualMachines/deallocate/action",                     "Microsoft.Compute/virtualMachines/powerOff/action",                     "Microsoft.Compute/virtualMachines/retrieveBootDiagnosticsData/action",                     "Microsoft.Compute/virtualMachines/instanceView/read",                     "Microsoft.Compute/virtualMachines/extensions/read",                     "Microsoft.Compute/virtualMachines/extensions/write",                     "Microsoft.Compute/virtualMachines/convertToManagedDisks/action",                     "Microsoft.Compute/virtualMachines/runCommands/read",                     "Microsoft.Compute/virtualMachines/runCommands/write",                     "Microsoft.Compute/virtualMachines/runCommands/delete",                     "Microsoft.Compute/virtualMachines/generalize/action",                     "Microsoft.Compute/virtualMachines/capture/action",                     "Microsoft.Compute/disks/read",                     "Microsoft.Compute/disks/write",                     "Microsoft.Compute/disks/beginGetAccess/action",                     "Microsoft.Compute/disks/delete",                     "Microsoft.Compute/disks/endGetAccess/action",                     "Microsoft.Compute/galleries/read",                     "Microsoft.Compute/galleries/write",                     "Microsoft.Compute/galleries/delete",                     "Microsoft.Compute/galleries/images/read",                     "Microsoft.Compute/galleries/images/write",                     "Microsoft.Compute/galleries/images/delete",                     "Microsoft.Compute/galleries/images/versions/read",                     "Microsoft.Compute/galleries/images/versions/write",                     "Microsoft.Compute/galleries/images/versions/delete",                       "Microsoft.Resources/checkResourceName/action",                     "Microsoft.Resources/subscriptions/resourceGroups/read",                     "Microsoft.Resources/subscriptions/resourceGroups/write",                     "Microsoft.Resources/subscriptions/locations/read",                       "Microsoft.MarketplaceOrdering/offerTypes/publishers/offers/plans/agreements/read",                     "Microsoft.MarketplaceOrdering/offerTypes/publishers/offers/plans/agreements/write",                                                            "Microsoft.ManagedIdentity/userAssignedIdentities/read",                     "Microsoft.ManagedIdentity/userAssignedIdentities/write",                     "Microsoft.ManagedIdentity/userAssignedIdentities/delete",                     "Microsoft.ManagedIdentity/userAssignedIdentities/assign/action",                     "Microsoft.ManagedIdentity/userAssignedIdentities/listAssociatedResources/action",                       "Microsoft.Authorization/roleAssignments/write",                     "Microsoft.Authorization/roleAssignments/delete"                                     ],                 "notActions": [],                 "dataActions": [                     "Microsoft.KeyVault/vaults/keys/encrypt/action",                     "Microsoft.KeyVault/vaults/keys/decrypt/action",                     "Microsoft.KeyVault/vaults/keys/read",                       "Microsoft.Storage/storageAccounts/queueServices/queues/messages/delete",                     "Microsoft.Storage/storageAccounts/queueServices/queues/messages/read",                     "Microsoft.Storage/storageAccounts/queueServices/queues/messages/write",                     "Microsoft.Storage/storageAccounts/queueServices/queues/messages/process/action",                     "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read",                     "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/write",                     "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/delete",                     "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/add/action",                     "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/move/action"                   ],                 "notDataActions": []             }         ]     }  } | |

1. Assign the created role to the required Microsoft Entra application. For details, see the [Manage access to Azure resources using RBAC and the Azure portal](https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal) section in the RBAC for Azure resources documentation.

|  |
| --- |
| Note |
| When you assign the role, consider the following:   * To find the custom role you created, click Privileged administrator roles on the Role tab. * On the Conditions tab, select the Allow user to assign all roles except privileged administrator roles Owner, UAA, RBAC option. |

1. At the [Account Type](restore_azure_acc_account.md) step of the Microsoft Azure Compute Account wizard, select Use existing account.
2. At the [Subscription](restore_azure_acc_account_existing.md) step of the wizard, specify the Azure Microsoft Entra application with the assigned role.

|  |
| --- |
| Important |
| If you use granular permissions and upgraded Veeam Backup & Replication to version 13.0.1, you need to create a new custom role with updated permissions to use the Instant Recovery to Azure functionality. |

Permissions for Azure Compute Account (New Application)

If you plan to add an Azure Compute account using a new Microsoft Entra ID (formerly Azure Active Directory) application (select the Create a new account option at the [Subscription](restore_azure_acc_account.md) step of the wizard), and you do not want to use built-in Azure roles, you can create a custom role with granular permissions:

1. In the Azure Portal, go to subscription properties and open Access control (IAM).
2. Create a custom role from a JSON file as described in [Microsoft Docs](https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles-portal#step-6-json). Use the following JSON. In the assignableScopes field, specify your subscription ID.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)JSON — Permissions for New Application

|  |  |
| --- | --- |
| |  | | --- | | {     "properties": {         "roleName": "Veeam Register Azure Compute Account using new Microsoft Entra application",         "description": "Permissions needed for a user to add an Azure Compute Account based on new Microsoft Entra application",         "assignableScopes": [             "/subscriptions/00000000-0000-0000-0000-000000000000"         ],         "permissions": [             {                 "actions": [                     "Microsoft.Authorization/roleDefinitions/read",                     "Microsoft.Authorization/roleAssignments/read",                     "Microsoft.Authorization/roleAssignments/write"                 ],                 "notActions": [],                 "dataActions": [],                 "notDataActions": []             }         ]     }  } | |

1. Assign the created role to the required Microsoft Entra user. For details, see the [Manage access to Azure resources using RBAC and the Azure portal](https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal) section in the RBAC for Azure resources documentation.
2. At the [Account Type](restore_azure_acc_account.md) step of the Microsoft Azure Compute Account wizard, select Create a new account.
3. At the Subscription step, configure the account as described in section [Creating New Entra ID Application](restore_azure_acc_account_new.md). On the Microsoft Azure device authentication page, specify a Microsoft Entra user account with the assigned role.

|  |
| --- |
| Note |
| The described permissions are required for assigning a role on the subscription level for the registered application. Also, privileges to register applications are required. For more information, see [Permissions](required_permissions.md#azure_compute). |


