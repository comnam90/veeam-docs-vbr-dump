---
title: "Instant Disk Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_disk_recovery.html"
last_updated: "8/8/2024"
product_version: "13.0.1.1071"
---

# Instant Disk Recovery

In this article

With Instant Disk Recovery, you can immediately restore VM disks from a backup file and publish them in the initial format. If you want to register disks as First Class Disks (FCD), see [Instant First Class Disk (FCD) Recovery](instant_disk_recovery_fcd.md). For the list of all disk recovery methods and their brief descriptions, see [Disk Recovery](disk_restores.md).

|  |
| --- |
| Note |
| You can also recover VMware vSphere VM disks directly from storage snapshots. |

Use Instant Disk Recovery if you need to:

* Recover VM disks, not an entire VM. Otherwise, use [Instant Recovery to VMware vSphere](instant_recovery.md).
* Recover VM disks and keep the target VM (to which you want to attach recovered disks) turned on. If the VM can be turned off, use [Virtual Disk Restore](virtual_drive_recovery.md).

The Instant Disk Recovery is a process that must be finalized. First, test the recovered disks and then decide whether to migrate them to the production environment or stop publishing the disks. To migrate the disks, Veeam Backup & Replication uses the [Quick Migration](quick_migration.md) mechanism. For more information on how to finalize Instant Disk Recovery, see [Finalizing Instant Disk Recovery](instant_disk_recovery_finalize.md).

How Instant Disk Recovery Works

Veeam Backup & Replication performs Instant Disk Recovery using [vPower technology](vpower_nfs_service.md). Veeam Backup & Replication performs the following steps to recover disks:

1. Checks whether the vPower NFS datastore is mounted to the ESXi host and contains VMDK files of the recovered disks.
2. [If you replace an existing disk] Unmounts and deletes the existing disk.
3. Connects the recovered disks to the target VM.
4. Initiates a creation of a protective snapshot for the target VM. If Instant Disk Recovery process fails, the protective snapshot guarantees no data loss.
5. Writes changes made to the recovered disks to redo logs on the vPower NFS server.

Related Topics

[Performing Instant First Class Disk (FCD) Recovery](performing_instant_fcd_recovery.md)

Page updated 8/8/2024

Page content applies to build 13.0.1.1071
