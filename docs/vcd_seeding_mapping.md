---
title: "vApp Replica Seeding and Mapping"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_seeding_mapping.html"
last_updated: "7/18/2024"
product_version: "13.0.1.1071"
---

# vApp Replica Seeding and Mapping


Replica seeding and mapping are technologies that help reduce the amount of traffic sent over the network. With these technologies, Veeam Backup & Replication does not have to transfer all of vApp data from the source host to the target host across the sites during the initial synchronization.

You can use seeding and mapping in the following scenarios:

* Seeding

Configure replica seeding if, in a backup repository located in the disaster recovery (DR) site, you have backups of vApps that you plan to protect. During replication, Veeam Backup & Replication will restore image of VMs that are added to vApps from these backups and will synchronize the state of the restored vApps with the latest state of the source vApps. Then Veeam Backup & Replication will use these restored vApps as replicas.

For more information on how to create backups that can be used as "seeds" for replica, see [Creating vApp Replica Seeds](vcd_replica_create_seed.md).

* Mapping

Configure replica mapping if, on the host in the DR site, you have ready-to-use copies of the source vApps. These can be restored vApps or replicas. Veeam Backup & Replication will synchronize the state of these ready-to-use vApps with the latest state of the source vApps and will use these vApps as replicas.

You can also configure both replica seeding and replica mapping in the same job. For example, if a job includes 2 vApps, you can use seeding for one vApp and map the other vApp to an existing vApp.

|  |
| --- |
| Important |
| If seeding or mapping is enabled in a job, all vApps in the job must be covered with seeding or mapping. If a vApp neither has a seed, nor is mapped to an existing vApp, it will be skipped from processing. |

Algorithm for Seeding

Replica seeding includes the following steps:

1. As a preparatory step for replica seeding, you need to create a backup of a vApp that you plan to protect. For more information on how to create a backup that will be used as a "seed" for replica, see [Creating vApp Replica Seeds](vcd_replica_create_seed.md).
2. When you create a replication job, you should point it to a backup repository in the DR site. During the initial synchronization, Veeam Backup & Replication accesses the backup repository where the replica seed is located, and restores the image of VMs that are added to vApp from the backup. The restored vApp is registered on the target host in the DR site. Files of the restored vApp are placed to the location you specify as the replica destination datastore.

Virtual disks of a replica restored from the backup preserve their format (that is, if the source VM used thin provisioned disks, virtual disks of the replica are restored as thin provisioned).

1. Veeam Backup & Replication synchronizes the restored vApp with the latest state of the source vApp.

After successful synchronization, in the Home view in the Veeam Backup & Replication console, under Replicas node you will see a vApp replica with two restore points. One point will contain the state of the vApp from the backup file; the other point will contain the latest state of the source vApp you want to replicate.

1. During incremental synchronization, Veeam Backup & Replication transfers only incremental changes in a regular manner.

Replica seeding dramatically reduces traffic sent over WAN or slow connections because Veeam Backup & Replication does not send the full contents of the vApp. Instead, it transmits only differential data blocks.

Algorithm for Mapping

Replication to a mapped vApp is performed in the following way:

1. The first step differs depending on which vApp you have selected for mapping:

* If you have selected a regular vApp, Veeam Backup & Replication calculates the differences between the source and mapped vApp.
* If you have selected a snapshot replica, Veeam Backup & Replication deletes all restore points and delta disks and then calculates the differences between the source and mapped vApp.
* If you have selected a CDP replica, Veeam Backup & Replication imports all restore points of this replica and then calculates the differences between the source and mapped vApp. Note that if disk sizes of the source and mapped vApp differ, Veeam Backup & Replication will delete all restore points of the mapped vApp.

1. To synchronize the state of the mapped vApp with the state of the source vApp, Veeam Backup & Replication sends the calculated changes to the mapped vApp.

The first and second steps take place during the initial synchronization.

1. During the incremental synchronization, Veeam Backup & Replication transfers only incremental changes in a regular manner.

After the successful initial synchronization, in the Home view of Veeam Backup & Replication, under Replicas node you will see a replica with restore points. If you have selected for mapping a regular vApp or snapshot replica, you will see two restore points: one restore point will contain the latest state of the mapped vApp, the other will contain the state of the source vApp. If you have selected a CDP replica, you will see all restore points of the mapped vApp plus one restore point that will contain the state of the source vApp.

Related Topics

* [Configure Seeding and Mapping in Cloud Director Replication](vcd_seeding_and_mapping.md)
* [Configure Seeding and Mapping in Cloud Director CDP](vcd_cdp_policy_seeding_mapping.md)


