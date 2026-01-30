---
title: "Replication Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replication_chain_hv.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Replication Chain


For every VM replica, Veeam Backup & Replication creates a replication chain that consists of restore points. Veeam Backup & Replication utilizes Microsoft Hyper-V checkpoint capabilities to create and manage replica restore points.

Veeam Backup & Replication creates a restore point during every replication job session. During the first replication job session, Veeam Backup & Replication creates a copy of the source VM on the target host. During every subsequent replication job session, it adds a new checkpoint to the replication chain for the VM replica. Blocks of data that have changed since the last job run are written to the checkpoint differencing disk, and the checkpoint differencing disk acts as a restore point. You can view a replication chain created for a VM using Hyper-V Manager.

You can specify how many restore points you want to store in the replication chain. For this, configure retention policy settings for the replication job. For more information, see [Specify Replication Job Settings](replica_settings_hv.md).

VM replica restore points are stored in a native Microsoft Hyper-V format next to replica virtual disk files, which allows Veeam Backup & Replication to accelerate failover operations. To fail over to the necessary point of the VM replica, Veeam Backup & Replication does not need to apply rollback files. Instead, it uses a native Microsoft Hyper-V mechanism of applying the checkpoint.

|  |
| --- |
| Important |
| We recommend you against switching restore points for replicas and powering on replicas using Hyper-V Manager. This may disrupt further replication operations in Veeam Backup & Replication or cause loss of important data. Instead, use Veeam Backup & Replication to perform failover operations. For more information on how to fail over to a VM replica, see [Failover](failover_hv.md). |

[![Replication Chain](images/snapshot_chain_hv.webp)](images/snapshot_chain_hv.webp)


