---
title: "Entire VM Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/full_recovery.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---

# Entire VM Restore

In this article

With Veeam Backup & Replication, you can restore an entire VM from a backup file to the latest state or to a previous point in time if the original VM fails.

When you restore an entire VM, Veeam Backup & Replication extracts the VM image from a backup to the production storage.Then Veeam Backup & Replication pulls the VM data from the backup repository to the selected storage, registers the VM on the chosen ESXi host and, if necessary, powers it on.

Entire VM restore enables full disk I/O performance while Instant Recovery provides a “temporary spare” for a VM as the vPower NFS throughput is limited.

How Entire VM Restore Works

A VM can be restored to its original location or to a new location. When you restore a VM to its original location, Veeam Backup & Replication powers off the original VM and restores only those disks that are included in the backup file. All other disks remain unchanged.

When you restore a VM to a new location, you can specify new VM settings such as the new VM name, the host and datastore where the VM will reside, disk format (thin or thick provisioned) and network properties. Veeam Backup & Replication will change the VM configuration file and store the VM data to the location of your choice.

To perform entire VM restore, Veeam Backup & Replication uses one of the following transport modes:

* If the backup proxy is connected directly to the SAN fabric or has access to NFS datastores, Veeam Backup & Replication uses the Direct storage access transport mode. Veeam Data Movers, which are deployed on the backup repository and backup proxy, retrieve VM data from the backup file and put it directly to the necessary datastore.

|  |
| --- |
| Important |
| Veeam Backup & Replication can restore only thick VM disks using the [Direct SAN access](direct_san_access.md) transport mode. For thin VM disks restore, Veeam Backup & Replication will use the [Direct NFS access](data_restore_in_direct_nfs_acc.md), [Virtual appliance](virtual_appliance.md) or [Network](network_mode.md) transport modes. Alternatively, you can instruct Veeam Backup & Replication to restore VM disks as thick. |

* If the backup proxy is virtualized and resides on the ESXi host to which the VM must be restored, Veeam Backup & Replication uses the Virtual appliance transport mode. The Virtual appliance mode utilizes VMware ESXi capabilities of HotAdding disks to the VM and thus eliminates the need to transfer the backup data across the network. Veeam Data Movers deployed on the backup repository and backup proxy retrieve VM data from the backup file and put it directly to the necessary datastore through the ESXi I/O stack.
* If the Direct storage access and Virtual appliance transport modes cannot be used, Veeam Backup & Replication uses the Network transport mode.

When Veeam Backup & Replication restores VMs, it performs a cyclic redundancy check (CRC) for the TCP traffic going between Veeam Data Movers installed on the backup repository and backup proxy. This happens provided that the [multithreaded data transfer is enabled](enabling_multithreaded_transfer.md) in the network traffic settings. Veeam Backup & Replication calculates and compares checksums for data blocks going from the source Veeam Data Mover and data blocks received on the target Veeam Data Mover. If the CRC check fails, Veeam Backup & Replication automatically re-sends data blocks without any impact on the restore job.

|  |
| --- |
| Note |
| If a VM has several VM disks, Veeam Backup & Replication restores VM disks in parallel. |

Related Topics

* [Quick Rollback](incremental_restore.md)
* [Storage Policies](storage_profile_restore.md)
* [Transport Modes](transport_modes.md)
* [Restoring Entire VM](performing_full_recovery.md)

Page updated 3/5/2025

Page content applies to build 13.0.1.1071
