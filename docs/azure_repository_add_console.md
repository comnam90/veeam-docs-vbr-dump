---
title: "Adding Backup Repositories Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repository_add_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Backup Repositories Using Console


Depending on whether you want to store backups in a short-term storage or a long-term storage, you can configure repositories of the following access tiers:

* Standard repositories

Use repositories of the Hot access tier to store data that you plan to access frequently, and repositories of the Cool access tier to store data that you plan to access infrequently. Backups stored in these repositories are shown under the External Repository node.

To store backups in a standard repository, first add it to the backup infrastructure and then enable Azure VM image-level backups, Azure SQL backups, Cosmos DB for PostgreSQL backups, Cosmos DB for MongoDB backups to a repository or virtual network configuration backup copy in the backup policy settings. For more information, see sections [Creating VM Backup Policies](azure_vm_backup_create.md), [Creating SQL Backup Policies](azure_sql_backup_create.md), [Creating Cosmos DB Backup Policies](azure_cosmos_db_backup_create.md) and [Editing Virtual Network Configuration Backup Policy](azure_vnet_backup_edit.md).

* Archive repositories

Use repositories of the Archive access tier to store data that you plan to access less than once a year. Backups stored in these repositories are shown under the External Repository (Archive) node.

To store backups in an archive repository, first add it to the backup infrastructure and then enable backup archiving for any backup policy that will store backups in this repository. For more information, see sections [Creating VM Backup Policies](azure_vm_backup_create.md), [Creating SQL Backup Policies](azure_sql_backup_create.md) and [Creating Cosmos DB Backup Policies](azure_cosmos_db_backup_create.md).

To learn how backup archiving works, see [Enabling Backup Archiving](azure_vm_backup_archiving.md).

|  |
| --- |
| Important |
| Note that you can perform a limited scope of operations with archive repositories from the Veeam Backup & Replication console:   * You cannot edit and rescan archive repositories. * You can only restore [entire Azure VMs](azure_entire_vm_restore_console.md) and [entire Azure SQL databases](azure_sql_restore_console.md) from backups stored in archive repositories. However, you can perform disk and file-level restore operations from these backups using the backup appliance Web UI. For more information, see sections [Performing Disk Restore](azure_performing_disk_restore.md) or [Performing File-Level Recovery](azure_performing_flr.md). |

For more information on access tiers for blob data, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview).

How to Add Backup Repositories

After you add a backup appliance to the backup infrastructure, you can configure repositories that will be used to store backups. To do that, use either of the following options:

* [Create new repositories](azure_repository_add_console_new.md).
* [Add existing repositories to the backup infrastructure](azure_repository_add_console_existing.md) if you have already configured them on the backup appliance.

Page updated 2026-07-28

