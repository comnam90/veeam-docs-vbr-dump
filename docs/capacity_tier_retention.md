---
title: "Retention Policy"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_retention.html"
last_updated: "6/4/2025"
product_version: "13.0.1.1071"
---

# Retention Policy

In this article

Retention policy defines the number of restore points to keep on your performance extents and capacity extents. You can manage retention policies to remove obsolete restore points both from the performance extents and the capacity tier. For more information on how to configure retention policy, see the Specify Backup Storage Settings section for [VMware vSphere backup jobs](backup_job_storage_vm.md) and [Microsoft Hyper-V backup jobs.](backup_job_storage_hv.md)

The restore points that fall under the retention policy will be removed both from the performance and capacity extents in the following manner:

* An earliest restore point will be removed from the backup chain on the associated extent.
* Data blocks that correspond to the restore point that is being removed will be purged from the capacity extent upon the next offload or copy session.

Make sure that the capacity extent has not been put into the Maintenance mode, as this mode prevents synchronization of the state of the backup chain in the performance tier with that of the capacity tier.

For more information about the move and copy offload sessions, see [Moving Backups to Capacity Tier](capacity_tier_move.md) and [Copying Backups to Capacity Tier](capacity_tier_copy.md).

* Immutable blocks of data is removed after the immutability period is over.

When a retention policy encounters immutable copied/moved blocks of data, it removes such blocks from the associated backup files that are located on the performance extents only, informing Veeam Backup & Replication that these blocks no longer exist and must be removed from the capacity tier once mutable.

For more information about immutability, see [Immutability for Scale-Out Backup Repositories](immutability_sobr.md).

Related Topics

* [Short-Term Retention Policy](retention_policy.md)
* [Switching to Maintenance Mode](sobr_maintenance.md)

Page updated 6/4/2025

Page content applies to build 13.0.1.1071
