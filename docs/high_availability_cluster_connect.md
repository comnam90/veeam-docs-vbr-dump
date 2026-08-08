---
title: "Connecting to High Availability Cluster"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_cluster_connect.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Connecting to High Availability Cluster


Once you assemble an HA cluster, you can connect to it using the Veeam Backup & Replication console.

After the Veeam Backup & Replication establishes a connection with an HA cluster, it creates a local cache of the HA cluster nodes. On the next connection, the Veeam Backup & Replication console uses this cache to obtain the status of both nodes. This information is essential for performing switchover or failover operations, and it helps prevent a failover to the secondary node while the primary node is still running.

For a cross-subnet HA cluster, the console and supported browsers use the fast-failback name resolution to always connect to the active primary node, even after a switchover or failover.

To connect to an HA cluster, do the following:

1. Close the current session with the Veeam Backup & Replication console on the primary node.
2. Use the HA cluster IP address or the HA cluster DNS name to connect to an HA cluster using the Veeam Backup & Replication console. For a cross-subnet HA cluster, use the cluster DNS name.

Page updated 2026-07-17

