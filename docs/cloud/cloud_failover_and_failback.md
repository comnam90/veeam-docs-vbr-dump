---
title: "Cloud Replica Failover and Failback"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_failover_and_failback.html"
last_updated: "11/8/2025"
product_version: "13.0.1.1071"
---


In this article

In case of software or hardware malfunction on the production site, a tenant can quickly recover a corrupted VM by failing over to its replica in the cloud. When you perform cloud failover, a replicated VM on the cloud host takes over the role of the original VM. A tenant can fail over to the latest state of a replica or to any of its good known restore points.

Veeam Cloud Connect Replication supports failover and failback operations for one VM and for several VMs. In case one or several hosts fail, you can use batch processing to restore operations with minimum downtime.

Depending on the scale of the disaster that affects the production site, a tenant can choose one of the following cloud failover scenarios:

* Full site failover — the whole production site becomes unavailable and all critical VMs that run interdependent applications fail over to their replicas on the cloud host.
* Partial site failover — one or several VMs become corrupted and fail over to their replicas on the cloud host.

In Veeam Backup & Replication, the actual failover is considered a temporary stage that should be further finalized. While the replica is in the Failover state, you can undo failover, perform failback or perform permanent failover.

|  |
| --- |
| Note |
| This and subsequent sections describe failover and failback aspects that are specific for Veeam Cloud Connect Replication. To get a detailed description of all failover and failback options supported in Veeam Backup & Replication, see the following sections in the Veeam Backup & Replication User Guide:   * [Failover and Failback for Replication](https://helpcenter.veeam.com/docs/backup/vsphere/failover_failback.html?ver=120) * [Failover and Failback for CDP](https://helpcenter.veeam.com/docs/backup/vsphere/cdp_failover_failback.html?ver=120) |

In This Section

* [Full Site Failover](cloud_connect_full_site_failover.md)
* [Partial Site Failover](cloud_connect_partial_site_failover.md)
* [Permanent Failover](cloud_connect_permanent_failover.md)
* [Failback](cloud_connect_failback.md)

Page updated 11/8/2025

Page content applies to build 13.0.1.1071
