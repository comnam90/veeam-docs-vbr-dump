---
title: "Instant First Class Disk (FCD) Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_disk_recovery_fcd.html"
last_updated: "5/31/2023"
product_version: "13.0.1.1071"
---

# Instant First Class Disk (FCD) Recovery

In this article

With Instant First Class Disk (FCD) Recovery, you can immediately restore VM disks from a backup file and register them as FCDs. If you want to recover disks in their initial format, see [Instant Disk Recovery](instant_disk_recovery.md). For the list of all disk recovery methods and their brief descriptions, see [Disk Recovery](disk_restores.md).

The Instant FCD Recovery is a process that must be finalized. You must migrate FCDs to the production environment or stop publishing them. To migrate the disks, Veeam Backup & Replication uses the [Quick Migration](quick_migration.md) mechanism. For more information on how to finalize Instant FCD Recovery, see [Finalizing Instant FCD Recovery](instant_fcd_recovery_finalize.md).

How Instant FCD Recovery Works

Veeam Backup & Replication performs the following steps to recover disks:

1. Initiates a recover session.
2. Connects to a target VMware cluster and mounts vPower NFS datastore to all ESXi hosts added to the target VMware cluster.
3. Mounts recovered disks and publishes them to the target vPower NFS datastore.
4. Registers the published disks as FCDs to the target vPower NFS datastore.

Veeam Backup & Replication performs Instant FCD Recovery using [vPower technology](vpower_nfs_service.md).

|  |
| --- |
| Note |
| Consider the following:   * If you specify the custom datastore to keep the redo logs, information on the FCD snapshots will be stored in the instant recovery session logs. * Veeam Backup & Replication does not remove the mounted vPower NFS datastore from a VMware cluster. |

Related Topics

[Performing Instant FCD Recovery](performing_instant_fcd_recovery.md)

Page updated 5/31/2023

Page content applies to build 13.0.1.1071
