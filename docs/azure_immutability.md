---
title: "Immutability"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_immutability.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Immutability


Veeam Plug-in for Microsoft Azure allows you to protect VM, SQL, Cosmos DB for PostgreSQL, Cosmos DB for MongoDB and virtual network configuration data stored in backup repositories from deletion by making the data temporarily immutable. To do that, the backup appliance uses [Immutable storage for Azure Blob Storage](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview) — once imposed, Immutable storage prevents objects from being deleted or overwritten for a specific immutability period. The immutability period is set based on the retention policy configured in the backup policy settings.

|  |
| --- |
| Note |
| To reduce the number of requests sent to immutable repositories during VM, SQL, Cosmos DB and virtual network configuration backup operations, the backup appliance leverages the [Block Generation mechanism](azure_block_generation.md). |

Considerations and Limitations

Before you start creating immutable backups, keep in mind the following limitations:

* You cannot manually remove immutable data from immutable repositories using the backup appliance Web UI, as described in sections [Removing VM Backups and Snapshots](azure_removing_vm_backups_and_snapshots.md), [Removing SQL Backups](azure_removing_sql_backups.md), [Removing Cosmos DB Backups](azure_removing_cosmos_db_backups.md) and [Removing Virtual Network Configuration Backups](azure_removing_vnet_backups.md) — until the immutability period is over.
* You can neither remove data from Microsoft Azure using any cloud service provider tools nor request the technical support department to do it for you — none of the protected objects can be overwritten or deleted by any user, including the Global Administrator in your Microsoft Entra ID.

How To Create Immutable Backups

To protect backups created with Veeam Plug-in for Microsoft Azure from deletion by making them temporarily immutable, perform the following steps:

1. [Add a backup repository with immutability enabled](azure_repository_add_ui.md#enable_efs_indexing).
2. Create a backup policy and specify the repository with immutability enabled as the target location for image-level backups. For more information, see sections [Creating VM Backup Policies](azure_vm_backup_create.md), [Creating SQL Backup Policies](azure_sql_backup_create.md), [Creating Cosmos DB Backup Policies](azure_cosmos_db_backup_create.md) and [Editing Virtual Network Configuration Backup Policy](azure_vnet_backup_edit.md).

Page updated 2026-07-01

