---
title: "Failover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_failover.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Failover

In this article

Failover is a process used when your primary node is unavailable due to an unexpected outage. During failover, Veeam Backup & Replication assigns the role of the primary node to the secondary node. The former primary node is no longer available, and the cluster consists of a single node. The replication of the database configuration is no longer possible until the failover is complete and the HA cluster acquires the secondary node. For the secondary node, you can either fix the former primary node and use it again in the same cluster, or you can configure a new HA cluster with a new node.

Failover Limitations

Before you perform a failover, consider the following limitations:

* Before you initiate a failover, ensure that the primary node is offline and will not revert to online status during the failover. Otherwise, it may lead to the split-brain scenarios.
* Kerberos authentication is not supported during failover to the secondary node. You must specify credentials in plain text.
* Veeam Backup & Replication does not support automatic failover of an HA cluster.

* If you initiate a failover while the secondary node is not synchronized with the primary node — for example, due to network issues — the secondary node database may lack information about the latest backup files created by the primary node. After the failover, you must rescan the backup repository to ensure the secondary node is updated with any backup files created while it was out of sync.
* To initiate a failover, you must use either the cluster virtual IP address or the IP address of the secondary node. You cannot initiate a failover using the cluster DNS name.

How Failover of High Availability Cluster Works

After you initiate a failover, Veeam Backup & Replication performs the following:

1. Veeam Backup & Replication updates the node database configuration.
2. Veeam Backup & Replication assigns the role of the primary node to the secondary node.
3. Veeam Backup & Replication assigns the cluster IP address to the secondary node.
4. Veeam Backup & Replication restores all processes necessary for the backup server operations.
5. Veeam Backup & Replication stops the PostgreSQL replication and synchronization between the nodes.
6. After the failover is completed, the HA cluster has only one node. The former primary node is no longer available.

Post-Failover Scenarios

After the failover completes, you can follow one of these scenarios to reconfigure the high availability cluster:

* Recover the former primary node. If you can recover the former primary node, you can use it as a secondary node of your high availability cluster. After you turn on this node, Veeam Backup & Replication will reconnect it to the cluster and convert it to the secondary node.
* Create a new cluster. If you are not able to recover the former primary node, you need to configure a new cluster:

1. [Decommission the HA cluster](high_availability_remove.md).
2. Configure a new secondary node with a new Veeam Software Appliance deployment.

Split Brain Resolution Algorithm

To prevent this split brain scenario, Veeam Backup & Replication uses the following algorithm:

1. The former primary node is back up and running.
2. The former primary node requests the update from the new primary node about its state.
3. The new primary node notifies that it has been assigned the role of primary node and informs the former primary node that it is now the secondary node.
4. Veeam Backup & Replication on the new secondary node updates the configuration and starts operating as the secondary node.

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
