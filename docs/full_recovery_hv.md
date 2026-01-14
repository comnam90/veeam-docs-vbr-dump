---
title: "Entire VM Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/full_recovery_hv.html"
last_updated: "3/24/2025"
product_version: "13.0.1.1071"
---

# Entire VM Restore

In this article

With Veeam Backup & Replication, you can restore an entire VM from a backup file to the latest state or to a previous point in time if the original VM fails.

Entire VM restore requires that VM image is fully extracted to the production storage. Veeam Backup & Replication copies the VM data from the backup repository to the selected storage, registers the VM on the chosen Hyper-V host and, if necessary, powers it on.

A VM can be restored to its original location or to a new location. When you restore a VM to its original location, Veeam Backup & Replication powers off the original VM and deletes it before the restore. This type of restore ensures the quickest recovery and minimizes the number of mistakes which can be potentially caused by changes in VM settings. When you restore a VM to a new location, you can specify new VM settings such as the new VM name, the host and volume where the VM will reside and network properties. Veeam Backup & Replication will change the VM configuration file and store the VM data to the location of your choice.

When Veeam Backup & Replication restores VMs, it performs a cyclic redundancy check (CRC) for the TCP traffic going between the backup repository and backup proxy. This happens provided that the [multithreaded data transfer is enabled](enabling_multithreaded_transfer.md) in the network traffic settings. Veeam Backup & Replication calculates and compares checksums for data blocks going from the backup repository and data blocks received on the backup proxy. If the CRC check fails, Veeam Backup & Replication automatically re-sends data blocks without any impact on the restore job.

|  |
| --- |
| Note |
| If a VM has several VM disks, Veeam Backup & Replication restores VM disks in parallel. |

Related Topics

* [Quick Rollback](incremental_restore_hv.md)
* [Restoring Entire VM](performing_full_recovery_hv.md)

Page updated 3/24/2025

Page content applies to build 13.0.1.1071
