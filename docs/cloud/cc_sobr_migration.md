---
title: "Migrating Tenant Data Between Performance Tier Extents"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_sobr_migration.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can migrate tenant data between performance extents within the same scale-out backup repository to balance storage resources, for example, after the SP adds a new extent to a scale-out backup repository. To perform this operation, the SP must use Veeam PowerShell cmdlets.

|  |
| --- |
| Note |
| If the source extent contains encrypted backups, Veeam Cloud Connect does not apply [Fast Clone](https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_block_cloning.html?ver=13) to these backups during migration between extents. |

To migrate tenant data between performance extents, follow these steps:

1. The SP specifies the source performance extent and the target performance extent for the operation, along with the tenant account whose data the SP wants to migrate. The migration process has no effect on other tenants.
2. The SP runs the Start-VBRCloudTenantBackupEvacuation cmdlet.

The cmdlet performs following steps:

1. Disables the tenant account.
2. Migrates following items from the source performance extent to the target performance extent:

* Tenant backups
* Subtenant backups
* Backup metadata files
* Backup files in the "recycle bin" used for insider protection
* Archive tier indexes for tenants running Veeam Backup & Replication version 11

Note that backup data offloaded to the capacity tier is not downloaded back to the performance tier during the migration process.

1. Enables the tenant account.

For detailed instructions, see the [Start-VBRCloudTenantBackupEvacuation](https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcloudtenantbackupevacuation.html?ver=13) section in the Veeam PowerShell Reference.

|  |
| --- |
| Note |
| Veeam Backup & Replication supports migration of tenant backups from a scale-out backup repository to a hardened (immutable) backup repository. For details, see [Switching from Linux Repository to Hardened Repository](cc_sobr_migration_linux.md). |

Related Topics

[Support for Scale-Out Backup Repository](cloud_connect_repository.md#sobr)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
