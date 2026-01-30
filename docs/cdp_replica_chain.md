---
title: "CDP Replication Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_replica_chain.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# CDP Replication Chain


A replication chain is a sequence of files that allows you to roll back a replica to a specific point in time during failover. Veeam Backup & Replication creates replication chains for each disk of a workload added to a CDP policy.

The replication chain contains short-term and long-term restore points. Short-term restore points allow you to roll back replica data to a state created seconds or minutes ago, while long-term restore points — to a state created hours or days ago. Short-term restore points are always crash-consistent, long-term restore points can be crash-consistent or application-consistent depending on how long-term restore points are configured in CDP policy settings.

The replication chain is stored on the target datastore in the <replica\_VM\_name> folder. The replication chain consists of the files of the following types (only the key file types are listed):

* VMX — the configuration file of the replica.

The replication chain contains one .vmx file, other files from the list are created per virtual disk.

* VMDK — virtual disk files that store contents of replica hard disk drives.

On the datastore, you can see files under the following names:

* <disk\_name>.vmdk — files that store full copies of virtual disks, that is, store base disk data. These files are created during the initial synchronization and relate to the very first long-term restore point. This restore point is crash-consistent.
* <disk\_name>-<index>.vmdk — files that store incremental changes made to virtual disks, that is, store delta disk data. Delta disk files relate to long-term restore points. These files are created according to the long-term schedule configured in CDP policy settings. The files remain unchanged till they are retained by long-term retention.
* <disk\_name>-<index>.tlog.vmdk — transaction log files that store incremental changes made to virtual disks during RPO set in CDP policy settings. These files relate to short-term restore points that are created once in RPO set in CDP policy settings. One transaction log file stores data for multiple short-term restore points.

A new transaction log file is created in the following cases:

* When a transaction log file reaches 512 GB.
* When a long-term restore point is created.
* When the short-term retention is reached. For example, if you set short-term retention to 1 hour, a new transaction log file will be created every hour.
* After failback commit.

There can be some other quite rare cases connected with policy settings or technical processes.

* <disk\_name>.ctlog.vmdk — file that stores data of outdated transaction logs, that is, stores compacted transaction logs. This compacted transaction log file is required during short-term retention. The compacted transaction log file is created when the earliest transaction log file in the chain reaches the short-term retention, that is, when all short term restore points stored in this file reach short-term retention. There is only one compacted transaction log file in the replication chain.
* <disk\_name>.bset.vmdk — file that contains metadata for the compacted transaction log file.
* <disk\_name>-<index>.unused.tlog.vmdk — unused transaction log file that will be reused later.
* <disk\_name>-interim.vmdk — files for protective virtual disks. Changes made to virtual disks will be written in these files when you perform failover.
* <disk\_name>.ds.vmdk — files that contain information about digests. These digests are used to recognize modified disk blocks.

|  |
| --- |
| Note |
| Although VMDK files look like VMware snapshot files, they are not real snapshots. These files are created by the I/O filter installed on the target host. |

* VMFD — files that contains metadata for disks.
* META — files that contain metadata for transaction log files.

To roll back a replica to a specific point in time, the chain of files created for the replica must contain files with data for the base disk (<disk\_name>.vmdk) and a set of files that contain incremental changes for disks (<disk-name>-<index>.vmdk + .tlog.vmdk). If any file in the replication chain is missing, you will not be able to roll back to the necessary state. For this reason, you must not delete files from the datastore manually. Instead, you must specify retention policy settings that will let you maintain the desired number of files.

For more information on retention policies and how to configure them, see [Retention Policies](cdp_retention.md).


