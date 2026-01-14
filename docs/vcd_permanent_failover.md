---
title: "Permanent Failover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_permanent_failover.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Permanent Failover

In this article

Permanent failover is one of the ways to finalize failover. When you perform permanent failover, you permanently switch processes from the source vApp to its replica. As a result, the replica stops acting as a replica and starts acting as the production vApp.

The permanent failover operation is performed in the following way:

1. Veeam Backup & Replication removes restore points of the replica from the replication chain and deletes associated files from the datastore. Changes that were written to the delta disks are committed to the replica to bring the replica to the most recent state.
2. Veeam Backup & Replication removes the replica from the list of replicas in the Veeam Backup & Replication console and the replica becomes the production vApp.
3. To protect the replica from corruption after permanent failover is complete, Veeam Backup & Replication reconfigures the job or policy and adds the source vApp to the list of exclusions. When replication job starts, the source vApp is skipped from processing. As a result, no data is written to the working replica.

In This Section

* [Performing Permanent Failover](vcd_perform_permanent_failover.md)
* [Performing Permanent Failover Retry](vcd_perform_perm_failover_retry.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
