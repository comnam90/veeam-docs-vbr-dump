---
title: "Temporary Restore Points"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_temporary_restore_points.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Temporary Restore Points


When running SLA-based backup policies, a backup appliance creates 2 types of temporary restore points — temporary snapshots and temporary backups.

Temporary Snapshots

To produce image-level backups according to backup schedules configured for SLA templates, the backup appliance takes temporary snapshots but then automatically removes them. The retention of these temporary snapshots depends on whether you enable the [changed block tracking (CBT) mechanism](azure_changed_block_tracking.md) for these templates:

* If CBT is enabled for an SLA template, the backup appliance keeps the latest temporary snapshot in the snapshot chain until the next backup session runs. In this case, the backup appliance processes only those data blocks that have changed since the previous snapshot was created. This allows you to increase the speed and efficiency of incremental backups but can incur additional costs of storing snapshots in Microsoft Azure.

* If CBT is disabled for an SLA template, the backup appliance removes the latest temporary snapshot from the snapshot chain during the next retention session at (as soon as Veeam Backup for Microsoft Azure finalizes the backup window in all protected Azure regions). In this case, the backup appliance processes not only those data blocks that have changed since the previous snapshot was created, but also all other data blocks of the snapshot. This allows you to reduce the cost of storing snapshots in Microsoft Azure but decreases the speed and efficiency of incremental backups.

That is, it is recommended that you take into account both backup schedules and your cost management strategy when choosing whether to enable CBT for SLA templates.

|  |
| --- |
| Important |
| Do not remove temporary snapshots from Microsoft Azure manually as Veeam Backup for Microsoft Azure will not be able to produce image-level backups. |

Temporary Backups

To build archive backup chains for Azure VMs protected by SLA-based backup policies, Veeam Backup for Microsoft Azure implements the same forever forward incremental backup method that applies to schedule-based backup policies. For more information, see [Archive Backup Chain](azure_archive_chain.md).

However, if Veeam Backup for Microsoft Azure fails to detect any full backups added to a backup chain on the same day when the archive session runs, it creates a temporary full backup that is then used to produce an archived backup in the target archive repository. After the archived backup is produced, Veeam Backup for Microsoft Azure automatically removes the temporary backup from the backup chain during the next retention session (as soon as Veeam Backup for Microsoft Azure finalizes the backup window in all protected regions).

Related Topics

[Adding SLA Templates](azure_sla_add.md)

Page updated 2026-07-01

