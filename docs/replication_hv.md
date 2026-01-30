---
title: "Replication for Microsoft Hyper-V"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replication_hv.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Replication for Microsoft Hyper-V


Replication is a technology that helps you protect mission-critical Microsoft Hyper-V virtual machines. When you replicate a VM, Veeam Backup & Replication creates an exact copy of the VM in the native Microsoft Hyper-V format on the target host. Veeam Backup & Replication maintains this copy in sync with the source VM. Replication provides minimum recovery time objective (RTO) in case a disaster strikes because VM replicas are in a ready-to-start state.

Data Replication

To replicate VMs, Veeam Backup & Replication leverages Microsoft VSS snapshot and checkpoint capabilities. When you replicate a VM, Veeam Backup & Replication instructs Microsoft Hyper-V to create a cohesive point-in-time copy of a VM. Veeam Backup & Replication uses this point-in-time copy as a source of data for replication.

During the first replication cycle, Veeam Backup & Replication copies data of the source VM running on the source host, and creates its full replica on the target host. Unlike backup files, replica virtual disks are stored decompressed in their native format. All subsequent replication cycles are incremental. Veeam Backup & Replication copies only those data blocks that have changed since the last replication job session. To keep track of changed data blocks, Veeam Backup & Replication uses different approaches. For more information, see [Changed Block Tracking](changed_block_tracking_hv.md).

Veeam Backup & Replication lets you perform on-site replication for high availability scenarios and remote (off-site) replication for disaster recovery scenarios. To facilitate replication over the WAN or slow connections, Veeam Backup & Replication optimizes traffic transmission. It filters out unnecessary data blocks such as duplicate data blocks, zero data blocks, blocks of swap files and blocks of excluded VM guest OS files, and compresses replica traffic. Veeam Backup & Replication also allows you to use [WAN accelerators](wan_accelerator.md) and apply [network throttling rules](setting_network_traffic_throttling.md) to prevent replication jobs from consuming the entire network bandwidth.

To replicate a VM, you need to [configure required backup infrastructure components](replication_components_hv.md) and [create a replication job](replica_job_hv.md).

Recovery

If a disaster strikes and the production VM stops working properly, you can fail over to its replica.

When you fail over to a replica, the replica takes over the role of the source VM. After your source VM is repaired, you can fail back to it and transfer all changes that occurred to replica to the source VM. If your source VM cannot be repaired, you can perform permanent failover, that is, permanently switch from the source VM to the VM replica and use this replica as the source VM. For more information, see [Failover and Failback for Replication](failover_failback_hv.md).

In This Section

* [Considerations and Limitations](replica_limitations_hv.md)
* [Backup Infrastructure for Replication](replication_components_hv.md)
* [How Replication Works](replication_process_hv.md)

* [Creating Replication Jobs](replica_job_hv.md)
* [Creating Replica Seeds](replica_create_seed_hv.md)
* [Managing Replicas](manage_replicas_hv.md)
* [Managing Replication Jobs](managing_replication_jobs_hv.md)
* [Failover and Failback for Replication](failover_failback_hv.md)


