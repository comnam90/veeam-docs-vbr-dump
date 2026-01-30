---
title: "Quick Rollback"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failback_quick_rollback.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Quick Rollback


Quick rollback helps you significantly reduce the failback time. You can use quick rollback if you fail back from a replica to the source vApp in the original location.

During failback, Veeam Backup & Replication calculates differences between VM disks of the source vApp and disks of the replica. With the quick rollback option enabled, Veeam Backup & Replication compares only those disk sectors that have changed during the replica was in the Failover state instead of comparing entire disks. To get information about the changed disk sectors, Veeam Backup & Replication uses VMware vSphere Changed Block Tracking (CBT).

As a result of enabling quick rollback, difference calculation becomes much faster. After the differences are calculated, Veeam Backup & Replication performs failback in a regular way: transport changed blocks to the source vApp, powers off the replica and synchronizes the source vApp with the replica once again.

Requirements for Quick Rollback

To perform quick rollback, make sure that the following requirements are met:

* You fail back to the source vApp in the original location.
* Do not use quick rollback if the problem occurred at the vApp hardware level, storage level or due to a power loss.

Use quick rollback if you fail back to the source vApp that had a problem at the guest OS level — for example, there was an application error or a user accidentally deleted a file on the source VM guest OS.

* CBT must be enabled for the source vApp.

Limitations for Quick Rollback

During the first replication job session after failback with quick rollback, CBT on the source vApp is reset. Due to that Veeam Backup & Replication will read data of the entire vApp.


