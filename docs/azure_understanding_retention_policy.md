---
title: "Retention Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_understanding_retention_policy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retention Policies


Cloud-native snapshots and image-level backups are not kept forever — they are removed according to retention policy settings specified while creating the policies.

Depending on the data protection scenario, retention policies can be specified:

* In restore points — for cloud-native snapshots produced by schedule-based backup policies.

The snapshot chain can contain only the allowed number of restore points. If the number of allowed restore points is exceeded, backup appliances remove the earliest restore point from the snapshot chain. For more information, see [VM Snapshot Retention](azure_vm_snapshot_retention.md) and [File Share Snapshot Retention](azure_file_share_snapshot_retention.md).

* In days/months/years — for image-level backups and archived backups as well as for cloud-native snapshots produced by SLA-based backup policies.

Restore points in the backup chain (either regular or archive) can be stored in the backup repository only for the allowed period of time. If a restore point is older than the specified time limit, backup appliances remove it from the backup chain. For more information, see sections [VM Backup Retention](azure_vm_backup_retention.md), [SQL Backup Retention](azure_sql_backup_retention.md) and [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md).

|  |
| --- |
| Note |
| * When configuring schedule-based backup policy scheduling, consider that backup appliances run retention sessions for schedule-based backup policies at 12:00 AM by default, according to the time zone set on the backup appliance. If you schedule these policies to execute at 12:00 AM, the policies and the retention tasks will be queued.  * If you disable any configured backup schedule in a schedule-based backup policy and run the policy, this does not affect retention settings of already created restore points — their expiration dates will still be determined by the previously applied retention policy. * If you change the retention period configured for any backup schedule in a schedule-based backup policy, this will affect expiration dates of already created restore points — their expiration dates will be determined by the newly applied retention policy. |

You can also define a specific retention time limit that will apply to all cloud-native snapshots stored in the configuration database and backup repositories. For more information, see [Configuring Global Retention Settings](azure_configuring_global_retention.md).

Related Topics

* [Creating VM Backup Policies](azure_vm_backup_create.md)
* [Creating SQL Backup Policies](azure_sql_backup_create.md)
* [Creating Cosmos DB Backup Policies](azure_cosmos_db_backup_create.md)
* [Creating Azure Files Backup Policies](azure_fs_backup_create.md)

Page updated 2026-07-01

