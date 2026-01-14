---
title: "Universal CDP to VMware vSphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/universal_cdp.html"
last_updated: "12/12/2025"
product_version: "13.0.1.1071"
---

# Universal CDP to VMware vSphere

In this article

Universal continuous data protection (CDP) is a technology that helps you protect mission-critical workloads when data loss for seconds or minutes is unacceptable. Workloads of various types, such as virtual, physical or cloud machines can be replicated to VMware vSphere cluster or host. CDP provides minimum recovery time objective (RTO) in case a disaster strikes because CDP replicas are in a ready-to-start state.

Data Replication

First, universal CDP creates replicas and, then, keeps these replicas up to date.

CDP constantly replicates I/O operations performed on workloads. To read and process data transmitted between the kernel and volumes, Veeam Backup & Replication uses two components: Veeam CDP Agent Service and Veeam CDP Volume Filter Driver. These components allow protection of various workloads compared to CDP for vSphere that protects only virtual machines. Universal CDP also allows reaching a lower recovery point objective (RPO) compared to the [snapshot-based replication](replication.md) — near-zero RPO which means almost no data loss.

Workloads can be replicated to a vSphere host or cluster. Data of I/O operations is stored on the target datastore and relates to short-term restore points. The short-term restore points allow you to recover a VM to a state back to seconds or minutes ago (depending on the RPO that you specify) in case a disaster strikes. Information about short-term restore points is maintained in a special journal. This journal stores records about short-term restore points for a maximum of 168 hours (7 days). If you want to recover a workload to an older state, Veeam Backup & Replication allows you to create additional restore points that contain a workload state back to hours or days ago. Such restore points are called long-term restore points.

To facilitate replication over slow connections, Veeam Backup & Replication optimizes traffic transmission. It filters out unnecessary data blocks such as duplicate data blocks, zero data blocks and compresses replica traffic.

To replicate a workload, you need to [configure required backup infrastructure components](uni_cdp_infrastructure.md) and [create a CDP policy](uni_cdp_policy_create.md).

Data Recovery

To recover a workload to a short-term or long-term restore point, you need to fail over to its replica.

When you fail over to a replica, the replica takes over the role of the source workload. You can shift all the operations from the source workload to the replica or recover a production VM from the replica in another location and shift all the processes to it. For more information, see [Failover and Failback for Universal CDP](uni_cdp_failover_failback.md).

Related Topics

* [Continuous Data Protection (CDP) with Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_cdp.html?ver=13)

In This Section

* [Backup Infrastructure for Universal CDP](uni_cdp_infrastructure.md)
* [Considerations and Limitations](uni_cdp_considerations.md)

Page updated 12/12/2025

Page content applies to build 13.0.1.1071
