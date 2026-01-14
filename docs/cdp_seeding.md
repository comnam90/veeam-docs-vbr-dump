---
title: "Replica Seeding and Mapping"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_seeding.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# Replica Seeding and Mapping

In this article

Replica seeding and mapping are technologies that help reduce the amount of traffic sent over a network. With these technologies, Veeam Backup & Replication does not have to transfer all of VM data from the source host to the target host across the sites during the initial synchronization. For more information on the initial synchronization, see [How CDP Works](cdp_hiw.md#data).

You can use seeding and mapping in the following scenarios:

* Seeding

Configure replica seeding if, in a backup repository located in the disaster recovery (DR) site, you have backups of VMs that you plan to replicate. During replication, Veeam Backup & Replication will restore VMs from these backups and will synchronize the state of the restored VMs with the latest state of the source VMs. Then Veeam Backup & Replication will use these restored VMs as replicas.

For more information on how to create backups that can be used as "seeds" for replica, see [Creating Replica Seeds for CDP](creating_replica_seed.md).

* Mapping

Configure replica mapping if, on the host in the DR site, you have ready-to-use copies of the source VMs. These can be regular or restored VMs, or replicas created by other CDP policies. Veeam Backup & Replication will synchronize the state of these ready-to-use VMs with the latest state of the source VMs and will use these VMs as replicas.

You can also configure both replica seeding and replica mapping in the same CDP policy. For example, if a policy includes 2 VMs, you can use seeding for one VM and map the other VM to an existing VM.

|  |
| --- |
| Important |
| If seeding or mapping is enabled in a policy, all VMs in the policy must be covered with seeding or mapping. If a VM neither has a seed, nor is mapped to an existing VM, it will be skipped from processing. |

Algorithm for Seeding

Replica seeding includes the following steps:

1. As a preparatory step for replica seeding, you need to create a backup of a VM that you plan to replicate. For more information on how to create a backup that will be used as a "seed" for replica, see [Creating Replica Seeds for CDP](creating_replica_seed.md).
2. When you create a CDP policy, you should point it to a backup repository in the DR site. During the initial synchronization, Veeam Backup & Replication accesses the backup repository where the replica seed is located, and restores the VM from the backup. The restored VM is registered on the target host in the DR site. Files of the restored VM are placed to the location you specify as the replica destination datastore.

Virtual disks of a replica restored from the backup preserve their format (that is, if the source VM used thin provisioned disks, virtual disks of the replica are restored as thin provisioned).

1. Veeam Backup & Replication synchronizes the restored VM with the latest state of the source VM.

After successful synchronization, in the Home view in the Veeam Backup & Replication console, under Replicas node you will see a replica with two restore points. One point will contain the state of the VM from the backup file; the other point will contain the latest state of the source VM you want to replicate.

1. During incremental synchronization, Veeam Backup & Replication transfers only incremental changes in a regular manner.

![Replica Seeding and Mapping](images/cdp_seeding.webp)

Replica seeding dramatically reduces traffic sent over WAN or slow connections because Veeam Backup & Replication does not send the full contents of the VM image. Instead, it transmits only differential data blocks.

Algorithm for Mapping

Replication to a mapped VM is performed in the following way:

1. The first step differs depending on which VM you have selected for mapping:

* If you have selected a regular or restored VM, Veeam Backup & Replication calculates the differences between the source and mapped VM.

Note that you cannot select a regular or restored VM for [CDP with Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_cdp.html?ver=13).

* If you have selected a CDP replica, Veeam Backup & Replication imports all restore points of this replica and then calculates the differences between the source and mapped VM. Note that if disk sizes of the source and mapped VM differ, Veeam Backup & Replication will delete all restore points of the mapped VM.

1. To synchronize the state of the mapped VM with the state of the source VM, Veeam Backup & Replication sends the calculated changes to the mapped VM.

The first and second steps take place during the initial synchronization.

1. During the incremental synchronization, Veeam Backup & Replication transfers only incremental changes in a regular manner.

After the successful initial synchronization, in the Home view of Veeam Backup & Replication, under Replicas node you will see a replica with restore points. If you have selected for mapping a regular VM or snapshot replica, you will see two restore points: one restore point will contain the latest state of the mapped VM, the other will contain the state of the source VM. If you have selected a CDP replica, you will see all restore points of the mapped VM plus one restore point that will contain the state of the source VM.

![Replica Seeding and Mapping](images/vmware_replica_mapping.webp)

Related Topics

[Configure Seeding and Mapping](cdp_policy_seeding_mapping.md)

Page updated 10/22/2025

Page content applies to build 13.0.1.1071
