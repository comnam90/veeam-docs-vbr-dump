---
title: "Data Transfer"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_data_transfer.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Data Transfer


Veeam Backup & Replication allows you to transfer data to and from capacity extents, as well as [move data from capacity extents to archive extents](archive_data_transfer.md).

You can perform the following data transfer operations:

* Copy policy: the backups are copied to capacity extents automatically.
* Move policy: the inactive backup chains can be transferred to the capacity extents.
* Previously offloaded data can also be downloaded from the capacity tier back to the performance extents.

To manage data transfer to and from capacity extents, Veeam Backup & Replication uses system sessions.

The following types of backup files can be moved or copied to capacity extents:

* Regular backups (except transaction logs)

* Veeam backups for Amazon, Google and Microsoft Azure (using backup copy jobs)

* Backups created with Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Unix or Veeam Agent for Mac
* Backups created with Veeam Plug-Ins for Enterprise Applications (Oracle RMAN, SAP HANA, SAP on Oracle)
* Backups created with Veeam Plug-In for Nutanix AHV
* Backups created with Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization
* Backups created with VeeamZIP jobs
* Backups exported by Kasten policies
* Exported backup files
* Orphaned backups

|  |
| --- |
| Note |
| Consider the following:   * Imported backups can be copied or moved to capacity extents only [manually](moving_to_capacity_tier.md). * You can move only inactive backup chains to capacity extents. * If you use the [forever forward incremental backup](incremental_forever_backup.md) method to create your backups, Veeam Backup & Replication will ignore the move policy and will apply the copy policy since this backup method will always produce an active backup chain. If you want to make the backup chain inactive, you must create either a synthetic full or an active full backup. |

In This Section

* [Copying Backups to Capacity Tier](capacity_tier_copy.md)
* [Moving Backups to Capacity Tier](capacity_tier_move.md)
* [Manually Moving Backups to Capacity Tier](moving_to_capacity_tier.md)
* [Downloading Data from Capacity Tier](downloading_from_capacity_tier.md)
* [Viewing Capacity Tier Sessions Statistics](offload_session_results.md)


