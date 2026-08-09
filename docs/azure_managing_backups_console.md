---
title: "Managing Backed-Up Data Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_managing_backups_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Backed-Up Data Using Console


To view and manage backed-up data, navigate to the Backups node of the Home view. The node displays information on all restore points created by backup appliances.

|  |
| --- |
| Note |
| You cannot remove created image-level backups and snapshots from the Veeam Backup & Replication console. To remove restore points of Azure VMs, Azure SQL databases, Cosmos DB accounts, Azure file shares and Azure virtual network configurations, open the backup [appliance Web UI](azure_accessing_vb_console.md) and follow the instructions provided in section [Managing Backed-Up Data Using Web UI](azure_managing_backups_ui.md). |

When you expand the Backups node in the working area, you can see the following icons:

Managing Backed-Up Data Using Console

| Icon | Protected Workload |
| ![Managing Backed-Up Data Using Console](images/azure_icon_vm.webp "Icon for Azure VM") | Indicates that the protected workload is an Azure VM. |
| ![Managing Backed-Up Data Using Console](images/azure_icon_sql.webp "Icon for databases") | Indicates that the protected workload is an Azure SQL database. |
| ![Managing Backed-Up Data Using Console](images/azure_icon_cosmos_db.webp "Icon for Cosmos DB") | Indicates that the protected workload is a Cosmos DB account. |
| ![Managing Backed-Up Data Using Console](images/azure_icon_file_share.webp "Icon for file shares") | Indicates that the protected workload is an Azure file share. |
| ![Managing Backed-Up Data Using Console](images/azure_icon_vnet.webp "Icon for virtual network configuration") | Indicates that the protected workload is a virtual network configuration. |

The Backups node contains 4 subnodes:

* The Snapshots subnode displays information on cloud-native snapshots of the protected Azure VMs, Azure file shares and Azure virtual network configurations and cloud-native backups of the protected Cosmos DB accounts:

* <appliance\_name> nodes show snapshots created manually on the backup appliance and snapshots imported to the appliance from Azure regions specified in the backup policy settings.
* <backup\_policy\_name> nodes show snapshots and cloud-native backups created by the backup policy.

To learn how backup appliances create cloud-native snapshots of Azure VMs, Azure file shares and Azure virtual network configurations, see sections [Protecting Azure VMs](azure_snapshot_chain_vm.md), [Protecting Azure Files](azure_snapshot_chain_fs.md) and [Protecting Virtual Network Configurations](azure_backup_chain_vnet.md). To learn how backup appliances create cloud-native backups of Cosmos DB accounts, see section [Protecting Cosmos DB Accounts](azure_how_cosmos_db_backup_works.md).

* The External Repository subnode displays information on backups of the protected Azure VMs, Azure SQL databases and Cosmos DB accounts that are stored in standard repositories.

To learn how backup appliances create image-level backups of the Azure VMs and backups of Azure SQL databases and Cosmos DB accounts, see sections [Protecting Azure VMs](azure_backup_chain_vm.md), [Protecting Azure SQL Databases](azure_how_sql_backup_works.md) and [Protecting Cosmos DB Accounts](azure_how_cosmos_db_backup_works.md#repository).

|  |
| --- |
| Note |
| If a backup chain was originally encrypted and then got decrypted by Veeam Backup & Replication, the backup chain will be marked with the Key icon. |

* The External Repository (Encrypted) subnode displays information on encrypted image-level backups of Azure VMs that are stored in standard repositories and that have not been decrypted yet, which means either that you have not specified the decryption password or that the specified password is invalid.

To learn how to decrypt backups, see [Decrypting Backups](#decrypt_image_level_backups).

* The External Repository (Archive) subnode displays information on backups of the protected Azure VMs, Azure SQL databases and Cosmos DB accounts that are stored in archive repositories.

To learn how backup appliances create archive backups, see section [Archive Backup Chain](azure_archive_chain.md).

[![Manage backed-up data](images/azure_manage_backed_up_data.webp)](images/azure_manage_backed_up_data.webp "Manage backed-up data")

Decrypting Backups

Veeam Backup & Replication automatically decrypts backup files stored in repositories either using passwords that you specify when adding these repositories to the backup infrastructure or using Azure Key Vault cryptographic keys automatically detected by Veeam Backup & Replication. If you do not specify decryption passwords or Veeam Backup & Replication does not have permissions to access cryptographic keys, the backup files remain encrypted.

* To decrypt backup files encrypted using a cryptographic key, make sure that the service account specified when [creating a new repository](azure_repository_console_service_account.md) or [adding an existing repository](azure_adding_appliance_account.md) to the backup infrastructure is assigned permissions required to access Azure Key Vault cryptographic keys. For more information on the required permissions, see [Plug-In Permissions](azure_plugin_permissions.md#azure_acc).
* To decrypt backup files encrypted using a password, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository (Encrypted).
3. Expand the backup policy that protects an Azure VM whose image-level backups you want to decrypt, select the backup chain that belongs to the VM and click Specify Password on the ribbon.

Alternatively, you can right-click the necessary backup chain and select Specify password.

|  |
| --- |
| Tip |
| To decrypt all backups created by a backup policy, right-click the policy and select Specify Password. |

1. In the Specify Password window, enter a password that was used to encrypt the data stored in the target repository.

[![Backup decryption](images/azure_decrypt_backup.webp)](images/azure_decrypt_backup.webp "Backup decryption")

Page updated 2026-07-01

