---
title: "Permanent Failover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_permanent_failover.html"
last_updated: "3/19/2025"
product_version: "13.0.1.1071"
---

# Permanent Failover

In this article

Permanent failover is one of the ways to finalize failover. When you perform permanent failover, you permanently switch processes from the source VM to its replica. As a result of permanent failover, the VM replica stops acting as a replica and starts acting as the production VM.

The permanent failover operation is performed in the following way:

1. Veeam Backup & Replication powers off the replica.
2. Veeam Backup & Replication removes short-term and long-term restore points of the replica from the replication chain and deletes associated files from the datastore. Changes that were written to the protective virtual disks (<disk\_name>-interim.vmdk) are committed to the replica to bring the replica to the most recent state.
3. Veeam Backup & Replication removes the replica from the list of replicas in the Veeam Backup & Replication console.
4. To protect the replica from corruption after permanent failover is complete, Veeam Backup & Replication reconfigures the current CDP policy by adding the source VM to the list of exclusions. Note that other policies and jobs are not modified automatically. When the CDP policy starts, the source VM is skipped from processing. As a result, no data is written to the working VM replica.

Related Topics

[Performing Permanent Failover](cdp_performing_perm_failover.md)

Page updated 3/19/2025

Page content applies to build 13.0.1.1071
