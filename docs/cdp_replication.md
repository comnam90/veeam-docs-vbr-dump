---
title: "Continuous Data Protection (CDP) for VMware vSphere"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_replication.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# Continuous Data Protection (CDP) for VMware vSphere


Continuous data protection (CDP) is a technology that helps you protect mission-critical VMware virtual machines when data loss for seconds or minutes is unacceptable. CDP also provides minimum recovery time objective (RTO) in case a disaster strikes because CDP replicas are in a ready-to-start state.

Data Replication

First, CDP creates replicas and, then, keeps these replicas up to date.

CDP constantly replicates I/O operations performed on VMs. To read and process I/O operations in transit between the protected VMs and their underlying datastore, CDP uses vSphere APIs for I/O filtering (VAIO) that gives an option not to create snapshots. Because CDP is always on and does not create snapshots, it allows reaching a lower recovery point objective (RPO) compared to the [snapshot-based replication](replication.md) — near-zero RPO which means almost no data loss.

Data of I/O operations is stored on the target datastore and relates to short-term restore points. The short-term restore points allow you to recover a VM to a state back to seconds or minutes ago (depending on the RPO that you specify) in case a disaster strikes. Information about short-term restore points is maintained in a special journal. This journal stores records about short-term restore points for a maximum of 168 hours (7 days). If you want to recover a VM to an older state, Veeam Backup & Replication allows you to create additional restore points that contain a VM state back to hours or days ago. Such restore points are called long-term restore points.

To facilitate replication over slow connections, Veeam Backup & Replication optimizes traffic transmission. It filters out unnecessary data blocks such as duplicate data blocks, zero data blocks and compresses replica traffic.

To replicate a VM, you need to [configure required backup infrastructure components](cdp_infrastructure.md) and [create a CDP policy](cdp_policy_create.md).

Data Recovery

To recover a VM to a short-term or long-term restore point, you need to fail over to its replica.

When you fail over to a replica, the replica takes over the role of the source VM. After your source VM is repaired, you can fail back to it and transfer all changes that occurred to replica to the source VM. If your source VM cannot be repaired, you can perform permanent failover, that is, permanently switch from the source VM to the VM replica and use this replica as the source VM. For more information, see [Failover and Failback for CDP](cdp_failover_failback.md).

Related Topics

* [CDP for VMware Cloud Director](vcloud_director_cdp.md)
* [Continuous Data Protection (CDP) with Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_cdp.html?ver=13)

In This Section

* [Requirements and Limitations](cdp_requirements.md)
* [Backup Infrastructure for CDP](cdp_infrastructure.md)
* [How CDP Works](cdp_hiw.md)


