---
title: "Managing Backed-Up Data Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_managing_backups_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Backed-Up Data Using Web UI


Veeam Backup for Microsoft Azure stores information on all protected Azure resources in the configuration database. Even if a resource is no longer protected by any configured backup policy and even if the resource no longer exists in Microsoft Azure, information on the backed-up data will not be deleted from the database until Veeam Backup for Microsoft Azure automatically removes all restore points associated with this resource according to the retention settings saved in the backup metadata. You can also remove the restore points manually on the Protected Data page.

|  |
| --- |
| Note |
| Backup appliances do not include restore points created manually in backup and snapshot chains, and do not apply the configured retention policy settings to these restore points. This means that the restore points are kept in your Microsoft Azure environment unless you remove them manually, as described in sections [Removing VM Backups and Snapshots](azure_removing_vm_backups_and_snapshots.md), [Removing SQL Backups](azure_removing_sql_backups.md), [Removing Cosmos DB Backups](azure_removing_cosmos_db_backups.md), [Removing File Share Snapshots](azure_removing_fs_snapshots.md) and [Removing Virtual Network Configuration Backups](azure_removing_vnet_backups.md). |

In This Section

* [Azure VM Data](azure_managing_vm_data.md)
* [Azure SQL Data](azure_managing_sql_data.md)
* [Cosmos DB Data](azure_managing_cosmos_db_data.md)
* [Azure Files Data](azure_managing_azure_files.md)
* [Virtual Network Configuration Data](azure_managing_vnet_data.md)

Page updated 2026-07-01

