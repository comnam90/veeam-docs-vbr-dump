---
title: "Deploying Backup Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_deploying_appliance.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deploying Backup Appliance


Veeam Backup for Microsoft Azure is installed on an Azure VM that is created in a selected Azure subscription during the product installation. You can deploy Veeam Backup for Microsoft Azure from the Veeam Backup & Replication console only.

To deploy a new backup appliance from the Veeam Backup & Replication console, do the following:

1. [Launch the New Veeam Backup for Microsoft Azure appliance wizard](azure_deploying_appliance_wizard.md).
2. [Choose a deployment mode](azure_deploying_appliance_mode.md).
3. [Specify service account settings](azure_deploying_appliance_account.md).
4. [Specify an Azure subscription in which the appliance will be deployed](azure_deploying_appliance_subscription.md).
5. [Specify a name and description for the appliance](azure_deploying_appliance_vm.md).
6. [Specify the connection type](azure_deploying_appliance_connection_type.md).
7. [Specify network settings for the appliance](azure_deploying_network_resources.md).
8. [Specify credentials for the default user account](azure_deploying_guest_os_credentials.md).
9. [Wait for the appliance to be added to the backup infrastructure](azure_deploying_appliance_apply.md).
10. [Finish working with the wizard](azure_deploying_appliance_finish.md).

How Deployment Works

When deploying a backup appliance, Veeam Backup & Replication performs the following steps:

1. Deploys an Azure VM from the Ubuntu 22.04 LTS image.
2. Creates a temporary storage account in Microsoft Azure and uploads backup appliance installation packages and their dependencies to the account.

Alternatively, Veeam Backup & Replication can use a custom storage account with private access. For Veeam Backup & Replication to be able to do that, the account must belong to the resource group where the backup appliance will reside and must be assigned the Veeam backup for Azure deployment account Azure tag with an empty value. To learn how to apply tags to Azure resources, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources-portal#add-tags).

1. Installs the [required software components](azure_backup_appliances.md) on the Azure VM.
2. Creates a default service account on the backup appliance. This service account will then be used to perform data protection and recovery operations within the Azure subscription to which the backup appliance belongs. Out of the box, the account is already assigned all the required permissions listed in section [Service Account Permissions](azure_service_account_permissions.md).

You will be able to add other service accounts later, after the backup appliance installation. For more information, see [Managing Service Accounts](azure_service_accounts.md).

1. Removes the temporary storage account from Microsoft Azure.

Related Topics

[Connecting to Existing Appliances](azure_connecting_appliance_console.md)

Page updated 2026-07-01

