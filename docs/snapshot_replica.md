---
title: "Snapshot Replica"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/snapshot_replica.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Snapshot Replica

In this article

To create snapshot replicas, Veeam Backup & Replication uses Hyper-V VM snapshot capabilities.

Snapshot replica in many respects is similar to forward incremental backup. During the first run of a replication job, Veeam Backup & Replication copies the VM running on the source Hyper-V host and creates its full replica on the target host. The replica is stored decompressed, in a native Hyper-V format.

All subsequent replication jobs are incremental. Veeam Backup & Replication copies only those data blocks that have changed since the last replication cycle. To keep track of changed data blocks for Hyper-V VMs, Veeam Backup & Replication uses its proprietary changed block tracking mechanism or resilient changed tracking (RCT). For more information, see [Changed Block Tracking](changed_block_tracking_hv.md).

For each new incremental run of the replication job, Veeam Backup & Replication triggers a regular snapshot of the replica. Blocks of data that have changed since the last job run are written to AVHD(X) files. Thus, the created replica snapshot acts as a new restore point.

As a result, for every replicated VM, Veeam Backup & Replication produces a full replica and a chain of snapshots, or restore points. The latest snapshot in the chain mirrors the state of the source VM. If the source VM fails for any reason, you can temporary or permanently fail over to the latest restore point or to an earlier point in time.

Veeam Backup & Replication creates and maintains the following types of replica files:

* Full VM replica (a set of VM configuration files and virtual disks).
* Replica restore points (VM snapshot files).
* Replica metadata (VBK file) that store VM replica digests. Veeam Backup & Replication uses this file to quickly detect changed blocks of data between two replica states. For more information, see [Changed Block Tracking](changed_block_tracking_hv.md).

The full VM replica along with its restore points is stored in a dedicated folder in the target datastore. Replica metadata files are stored in a backup repository.

|  |
| --- |
| Note |
| Virtual disks of snapshot VM replicas are always dynamically expand. |

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
