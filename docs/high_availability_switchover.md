---
title: "Switchover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_switchover.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Switchover

In this article

A switchover is a process used when both nodes are in an operational state and synchronized with each other, but you need to perform tasks that require primary node downtime, such as hardware maintenance. When you initiate a switchover, Veeam Backup & Replication assigns the role of the primary node to the secondary node. The replication of the database configuration flows to the former primary node. After the maintenance, you can revert to the primary node or use it as a new secondary.

Switchover Limitations

Before you perform a switchover, consider the following limitations:

* It is crucial to prevent any scenario where either the primary or secondary node becomes offline (for example, due to power loss or network connectivity issues) during the switchover process. If either node becomes and remains offline for the entire duration of the switchover, the HA cluster will be unable to recover. If this happens, contact [Veeam Customer Support](https://www.veeam.com/support.html).
* Veeam Backup & Replication does not support an automatic switchover of an HA cluster.
* During a switchover, Veeam Backup & Replication stops all jobs and services.

* [Instant Recovery to Hyper-V] Make sure you [finalize the Instant Recovery session](ir_finalize_hv.md) to Hyper-V before you start a switchover. During a switchover, Veeam Backup & Replication stops the Instant Recovery session. After that, the VM that Veeam Backup & Replication creates on the Hyper-V datastore and its snapshot are deleted. Once you connect to a cluster, Veeam Backup & Replication will start an Instant Recovery session again.

How Switchover Works

After you initiate a switchover, Veeam Backup & Replication performs the following:

1. Removes the HA cluster IP from the primary node.
2. Rewrites information about what host is a primary node in the database.
3. Sets the database on the former primary node to read-only mode.
4. Restarts services on both HA nodes.
5. Assigns an HA cluster cluster IP address to a new primary node.

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
