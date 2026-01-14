---
title: "High Availability (HA) Cluster"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_cluster.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# High Availability (HA) Cluster

In this article

The High Availability (HA) cluster is a solution that is designed to ensure continuous availability and minimize downtime of the backup server by clustering two backup servers. The HA cluster addresses the need for resilience and operational continuity of the Veeam Backup & Replication infrastructure. HA cluster guarantees continuous operation by replicating your backup server, ensuring uninterrupted service.

An HA cluster consists of two nodes with continuous replication between these nodes: the primary node handles all backup and replication tasks, while the secondary stands by to take over if needed. In case the primary node experiences downtime or you need to take it down for hardware maintenance, you can use one of the following operations to switch the role of the primary node to the secondary node:

* Switchover —  An operation that you may want to run when both HA nodes are in an operational state and synchronized with each other, but you need to perform operations that will require downtime for the primary node, such as hardware maintenance.
* Failover — An operation necessary when your primary node is not available due to an unexpected outage. In this case, you can perform a failover to promote the secondary node to the primary node role and resume working with the backup server without significant interruption.

In both scenarios, the secondary node is fully prepared to handle all the daily tasks typically managed by your primary node, ensuring that your backup server remains operational without any interruptions.

To prevent a split-brain scenario, Veeam Backup & Replication uses a built-in mechanism: the primary node always operates in the read-write mode, while the secondary HA node remains in the read-only mode.

After you install updates on the primary node using the [Veeam Updater](update_appliances.md), Veeam Backup & Replication will automatically update the secondary node, so you do not need to check and install updates on the secondary node manually.

In This Section

* [Considerations and Limitations](high_availability_limitations.md)
* [Infrastructure for High Availability Cluster](high_availability_infrastructure.md)
* [How High Availability Cluster Works](high_availability_hiw.md)
* [Assembling High Availability Cluster](high_availability_configuration.md)
* [Connecting to High Availability Cluster](high_availability_cluster_connect.md)
* [Switchover](high_availability_switchover.md)
* [Failover](high_availability_failover.md)
* [Managing High Availbility Cluster](high_availbilitu_cluster_management.md)

Page updated 11/12/2025

Page content applies to build 13.0.1.1071
