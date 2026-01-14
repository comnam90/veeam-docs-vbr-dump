---
title: "Quick Rollback"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/failback_quick_rollback_hv.html"
last_updated: "1/29/2025"
product_version: "13.0.1.1071"
---

# Quick Rollback

In this article

If you fail back from a VM replica to the source VM in the original location, you can instruct Veeam Backup & Replication to perform quick rollback. Quick rollback significantly reduces the failback time and has little impact on the production environment.

During failback with the quick rollback option enabled, Veeam Backup & Replication does not calculate digests for entire VM replica disks to get the difference between the source VM and VM replica. Instead, it queries CBT to get information about disk sectors that have changed, and calculates digests only for these disk sectors. As a result, digest calculation is performed much faster. After that, Veeam Backup & Replication performs failback in a regular way: transport changed blocks to the source VM, powers off the VM replica and synchronizes the source VM with the VM replica once again.

It is recommended that you use quick rollback if you fail back to the source VM after a problem that has occurred at the level of the guest OS of the VM replica — for example, there has been an application error or a user has accidentally deleted a file on the VM replica guest OS. Do not use quick rollback if the problem has occurred at the VM hardware level, storage level or due to a power loss.

Requirements for Quick Rollback

To perform quick rollback, make sure that the following requirements are met:

* You must perform failback to the source VM in the original location.
* The VM replica must be created with the Use changed block tracking data option enabled.

Limitations for Quick Rollback

The following limitations apply to quick rollback:

* After you fail back to the source VM with quick rollback, the CBT on the source VM is reset. During the subsequent replication job session, Veeam Backup & Replication will read data of the entire original VM.

* Quick rollback is not supported if the source VM is also replicated using Hyper-V native replication mechanisms.

Related Topics

[Performing Failback](performing_failback_hv.md)

Page updated 1/29/2025

Page content applies to build 13.0.1.1071
