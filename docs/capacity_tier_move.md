---
title: "Moving Backups to Capacity Tier"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_move.html"
last_updated: "12/29/2025"
product_version: "13.0.1.1071"
---

# Moving Backups to Capacity Tier

In this article

To collect backup files that belong to inactive backup chains from the performance extents and move them to the capacity tier, Veeam Backup & Replication uses an offload session which is executed automatically every 4 hours.

To enable data movement, make sure to select the Move backups to object storage as they age out of the operational restores window option, as described in the [Add Capacity Tier](new_capacity_tier.md) section.

A complete name of each offload session is built up of the scale-out backup repository name plus the Offload postfix. That is, if your scale-out backup repository name is Amazon, the offload session name will be Amazon Offload.

The offload session manages the following:

* [Validation Process](#vp)
* [Data Transfer](#dt)

Validation Process

Before your data can safely be moved to the capacity tier, Veeam Backup & Replication performs the following mandatory verifications and required actions:

* Verifies whether data that is about to be moved belongs to an inactive backup chain.

For more information, see [Backup Chain Detection](capacity_tier_inactive_backup_chain.md).

* Verifies whether performance extents are available and have not been put into the Maintenance mode.

|  |
| --- |
| Important |
| Veeam Backup & Replication does not offload data from Linux-based performance extents that have internet access through HTTP(S) proxy. All Linux-based performance extents configured in your scale-out backup repository must have direct access to the internet. |

* Verifies whether the capacity extents have not been put into the Maintenance or the Sealed mode.

For more information, see [Switching to Maintenance Mode](sobr_maintenance.md) and [Switching to Sealed Mode](sobr_seal.md).

* Verifies whether configuration parameters that define how and when inactive backup chains must be moved to capacity extents are met.

Such parameters are configured as described in section [Add Capacity Tier](new_capacity_tier.md).

* Synchronizes the backup chain state between the performance and capacity extents to maintain retention policies.

For more information, see [Retention Policy](capacity_tier_retention.md).

Data Transfer

After the validation process is complete, the SOBR Offload session collects backup files that have passed verification. Such verified backup files are collected from all the performance extents added to a scale-out backup repository.

The performance extent A has an inactive backup chain consisting of one VBK file and three VIB files, that is, 4 restore points in total. Each of these files comprises metadata and the actual blocks of data. During the offload session, Veeam Backup & Replication will collect the actual blocks of data from all the backup files (VBK and VIB) and offload these blocks to the object storage repository.

Each offloaded block may be of different size, which is defined during configuring storage optimization. The offloaded blocks are placed to the blocks directory in your capacity extents.

Such approach will be applied to all inactive backup chains that satisfy validation criteria.

After offload is complete, the new Capacity Tier node appears in the Home view, under the Backups node and shows backups that have been moved to capacity extents.

|  |
| --- |
| Note |
| The offload is not performed during prohibited hours specified in the scale-out backup repository backup window configuration. You can configure the backup window at the [Add Capacity Tier](new_capacity_tier.md) step of the New Scale-out Backup Repository wizard. |

Offload Session Statistics

The offload session results are saved to the configuration database and available for viewing, as described in section [Viewing Offload Session Results](capacity_tier_offload_results.md).

Related Topics

* [Copying Backups to Capacity Tier](capacity_tier_copy.md)
* [Enabling Traffic Throttling](setting_network_traffic_throttling.md)
* [Storage Settings](backup_job_advanced_storage_vm.md) (vSphere)
* [Storage Settings](backup_job_advanced_storage_hv.md) (Hyper-V)
* [Capacity Extent Structure](object_storage_repository_structure.md)

Page updated 12/29/2025

Page content applies to build 13.0.1.1071
