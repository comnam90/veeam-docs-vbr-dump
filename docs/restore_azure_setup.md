---
title: "Configuring Components and Accounts for Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_setup.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---

# Configuring Components and Accounts for Restore


Before you restore workloads, you must first add an account to be used for restore and then configure the required components:

1. [Add a Microsoft Azure Compute account](restore_azure_accounts.md).

This account must have specific built-in Azure roles (the roles are listed in the sections about adding the accounts). If you do not want to use built-in roles, you can create a custom role with granular permissions. For more information, see [Creating Custom Role for Azure Account](azure_custom_role.md).

1. [For restore of Linux workloads] [Configure helper appliances in Microsoft Azure](restore_azure_linux.md).

|  |
| --- |
| Note |
| [If you have not changed default credentials for helper appliance] Before you configure the helper appliances, we recommend you to change the default credentials used during the helper appliance deployment. For more information on how to do this, see [Changing Credentials for Helper Appliances](restore_azure_credentials.md). |

1. [For restore process speed-up] [Configure an Azure restore proxy appliance](restore_azure_proxy.md).

|  |
| --- |
| Note |
| If you use Veeam Backup for Microsoft Azure and plan to restore VMs from restore points that were created using the appliance, you do not need to configure the helper appliance and Azure restore proxy appliance (former Azure proxy). Also, restore to Microsoft Azure works as described in the [Performing VM Restore](https://helpcenter.veeam.com/docs/vbazure/guide/vm_restore_entire_hiw.html?ver=8.1) section in Veeam Backup for Microsoft Azure User Guide. |


