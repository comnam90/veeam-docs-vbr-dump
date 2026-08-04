---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup


With Veeam Plug-in for Microsoft Azure, you can protect data in the following ways:

* Create cloud-native snapshots of Azure VMs

A cloud-native snapshot includes point-in-time snapshots of virtual disks attached to the processed Azure VM. Snapshots of virtual disks are taken using [native Microsoft Azure capabilities](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/snapshot-copy-managed-disk).

* Create image-level backups of Azure VMs

In addition to cloud-native snapshots, you can protect your Azure VMs with image-level backups. An image-level backup captures the whole image of the processed Azure VM (including OS data, application data and so on) at a specific point in time. The backup is saved as multiple files to a repository in the [native Veeam format](azure_backup_chain_vm.md).

* Create backups of Azure SQL databases

A backup of an Azure SQL database captures the whole image of the processed database (including tables, constraints, indexes and actual data) at a specific point of time. The backup is saved as multiple files to a repository in the [native Veeam format](azure_backup_chain_sql.md).

* Create backups of Cosmos DB accounts

To back up Cosmos DB accounts, Veeam Backup for Microsoft Azure uses the native Microsoft Azure [continuous backup](https://learn.microsoft.com/en-us/azure/cosmos-db/continuous-backup-restore-introduction) feature.

For each processed Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account, you can also choose to store backups in a repository. A backup of a Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account stored in a repository includes user data contained in the database of this account. The backup is saved as a dump file to a repository in the [native Veeam format](azure_backup_chain_cosmos_db.md).

* Create cloud-native snapshots of Azure file shares

A cloud-native snapshot includes point-in-time snapshots of base files, metadata and files in the system properties of the processed Azure file share. Snapshots of these files are taken using [native Microsoft Azure capabilities](https://docs.microsoft.com/en-us/azure/storage/files/storage-snapshots-files).

|  |
| --- |
| Note |
| Consider that if you delete a file share from Microsoft Azure, the snapshots of this file share will be deleted as well. To protect your snapshots from accidental deletion, you can use the file share soft delete option. For more information on the soft delete option for Azure file shares, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-enable-soft-delete?tabs=azure-portal). |

* Create backups of your virtual network configuration

A virtual network configuration backup captures the whole image of a virtual network configuration of an Azure subscription (including multiple virtual network configuration settings and components) at a specific point in time. The virtual network configuration backup is stored in the backup appliance database.

|  |
| --- |
| Important |
| Veeam Plug-in for Microsoft Azure supports only the backup of the following virtual network configuration components: virtual networks, subnets, IP configurations, network security groups, route tables, network interfaces and virtual network peerings. |

To schedule data protection tasks to run automatically, create backup policies. You will be able to run the backup policies on demand and manually perform backup of Azure VMs, Azure SQL databases, Cosmos DB accounts and Azure file shares. To learn how to perform backup manually, see sections [Creating VM Snapshots Manually](azure_creating_vm_snapshots_manually.md), [Creating File Share Snapshots Manually](azure_creating_fs_snapshots_manually.md), [Creating SQL Backups Manually](azure_creating_sql_backups_manually.md) and [Creating Cosmos DB Backups Manually](azure_creating_cosmos_db_backups_manually.md).

|  |
| --- |
| Tip |
| You can perform advanced data protection operations with image-level backups from the Veeam Backup & Replication console. For more information, see [External Repository](external_repository.md). |

In This Section

* [Performing Backup Using Console](azure_performing_backup_console.md)
* [Performing Backup Using Web UI](azure_performing_backup_ui.md)

Page updated 2026-07-01

