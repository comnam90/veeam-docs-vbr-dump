---
title: "Transformation Processes"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_transform_operations.html"
last_updated: "8/25/2023"
product_version: "13.0.1.1071"
---

# Transformation Processes

In this article

Veeam Backup & Replication can perform additional transformations in the target backup repository after the backup copying task or at the end of the backup copy interval. Transformation processes are the following:

* Backup chain transformation

When a new restore point is copied to the target backup repository, Veeam Backup & Replication checks the retention policy settings for the backup copy job. If the limit in restore points is exceeded, Veeam Backup & Replication does the following:

* If only short-term retention policy is enabled, Veeam Backup & Replication transforms the backup chain to make room for a new restore point. For more information, see [Short-Term Retention Policy](backup_copy_simple_retention.md).
* If long-term retention policy is enabled, Veeam Backup & Replication removes unnecessary restore points. Veeam Backup & Replication removes restore points in a way similar to the one described in section [Forward Incremental Backup Retention Policy](retention_incremental.md).

For more information on retention policies, see [Retention Policy for Backup Copy Jobs](backup_copy_retention.md).

After the transformation process, Veeam Backup & Replication can perform additional operations: remove data of deleted workloads from the backup chain and compact a full backup file.

* Removal of deleted items

In the backup copy job settings, you can specify after which period you want to delete data of deleted workloads from backups created by backup copy jobs. After the period ends, Veeam Backup & Replication checks the list of workloads included in the job and removes data of deleted workloads from the backup chain in the target backup repository. For more information on how data is deleted and which limitations apply, see [Deleted Items Retention](backup_copy_deleted_vms.md). For more information on how to configure the deleted items retention, see [Specifying Advanced Settings](backup_copy_settings_backup.md).

* Full backup file compact

In the backup copy job settings, you can select to periodically compact a full backup file to reduce its size and increase the speed of read and write operations. For more information, see [Compact of Full Backup File](backup_copy_compact_file.md).

|  |
| --- |
| Note |
| If backup copy job processes the per-machine backup files, transformation processes will be performed for each object individually. |

Page updated 8/25/2023

Page content applies to build 13.0.1.1071
