---
title: "VM Snapshot Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_snapshot_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Snapshot Retention


Depending on the data protection scenario, the backup appliance retains cloud-native snapshots as follows:

* In days/months/years — for snapshots produced by SLA-based backup policies.

Restore points can be kept in a snapshot chain only for the period of time defined in snapshot scheduling settings as described in section [Adding SLA Templates](azure_sla_snapshot_settings.md). If the backup appliance detects that a restore point is older than the specified time limit, it removes this restore point from the snapshot chain.

* In restore points — for snapshots produced by schedule-based backup policies.

A snapshot chain can contain only the allowed number of restore points defined in backup scheduling settings as described in section [Creating VM Backup Policies](azure_vm_backup_policy_schedule.md). If the backup appliance detects that the number of restore points in the snapshot chain exceeds the retention limit, it removes the earliest restore point from the chain.

Due to the CBT mechanism limitations, the backup appliance permanently retains in the snapshot chain 2 cloud-native snapshots of each processed Azure VM; these snapshots are then used to create image-level backups. To learn how the CBT mechanism works, see [Changed Block Tracking](azure_changed_block_tracking.md).

For more information on the snapshot deletion process, see [Microsoft Docs](https://azure.microsoft.com/en-us/blog/announcing-general-availability-of-incremental-snapshots-of-managed-disks/).

[![VM Snapshot Retention](images/azure_snapshot_retention.webp)](images/azure_snapshot_retention.webp)

|  |
| --- |
| Notes |
| * Consider that Veeam Backup for Microsoft Azure does not apply retention policy settings to cloud-native snapshots created manually. To learn how to remove these snapshots, see [Managing VM Data](azure_removing_vm_backups_and_snapshots.md). * Due to Microsoft Azure limitations, retention of [locked Azure VM snapshots](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json) is not supported. As a workaround, you can instruct Veeam Backup for Microsoft Azure to store snapshots in an unlocked resource group as described in [Creating SLA-Based VM Backup Policies](azure_vm_sla_tags_snapshot_location.md#location). |

Page updated 2026-07-01

