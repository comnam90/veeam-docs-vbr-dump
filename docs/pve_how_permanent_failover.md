---
title: "Permanent Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_how_permanent_failover.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Permanent Failover


Permanent failover is one of the ways to finalize failover. When you perform permanent failover, you permanently switch from the original VM to its replica. As a result of permanent failover, the VM replica stops acting as a replica and starts acting as the production VM.

The permanent failover operation is performed in the following way:

1. Veeam Backup & Replication removes snapshots (restore points) of the VM replica from the snapshot chain and deletes associated files from the storage.

Snaphot files that contained the original data changed while the VM replica was in the Failover state are deleted.

1. Veeam Backup & Replication removes the VM replica from the list of replicas in the Veeam Backup & Replication console.
2. To protect the VM replica from corruption after permanent failover is complete, Veeam Backup & Replication reconfigures the current replication job by adding the original VM to the list of exclusions. Note that other jobs are not modified automatically. When the replication job starts, the original VM is skipped from processing. As a result, no data is written to the working VM replica.

Related Topics

[Running Permanent Failover](pve_failover_permanent.md)

Page updated 2026-07-29

