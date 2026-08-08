---
title: "Replica Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_replication_chain.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Replica Chain


For every VM replica, Veeam Backup & Replication creates a replication chain that consists of restore points. Veeam Backup & Replication utilizes Proxmox VE snapshot capabilities to create and manage replica restore points.

Veeam Backup & Replication creates a restore point during every replication job session. During the first replication job session, Veeam Backup & Replication creates a copy of the original VM on the target host. During every subsequent replication job session, it adds a new snapshot to the replication chain for the VM replica. Original blocks of data that have changed since the last job run are written to the snapshot delta file, and the snapshot delta file acts as a restore point.

You can specify how many restore points you want to store in the replication chain. To do that, configure retention policy settings for the replication job. For more information, see [Configure Replication Settings](pve_replication_job_create_settings.md).

VM replica restore points are stored in a native Proxmox VE format next to replica virtual disk files, which allows Veeam Backup & Replication to accelerate failover operations. To fail over to the necessary point of the VM replica, Veeam Backup & Replication does not need to apply rollback files. Instead, it uses a native Proxmox VE mechanism of reverting to a snapshot.

|  |
| --- |
| Important |
| We recommend you against switching restore points for replicas and powering on replicas using Proxmox VE administration portal. This may disrupt further replication operations in Veeam Backup & Replication or cause loss of important data. Instead, use Veeam Backup & Replication to perform failover operations. For more information on how to fail over to a VM replica, see [Failover](pve_failover_run.md). |

Page updated 2026-07-31

