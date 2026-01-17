---
title: "How High Availability Cluster Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_hiw.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# How High Availability Cluster Works

In this article

After you enable the High Availability option and assemble the HA cluster, Veeam Backup & Replication prepares the nodes to enable the data replication:

1. Starts the veeamhasvc.service service.
2. Assigns a virtual IP address of an HA cluster to the primary node.
3. Opens the necessary [ports](used_ports.md#copnfigurationdb) for the PostgreSQL database to communicate with the backup server.
4. Configures the secondary node:

* Removes data from the PostgreSQL database of the secondary node.
* Sets the PostgreSQL database to read-only mode.
* Stops all jobs and services except those necessary for the database replication and communication with the primary node.

1. Veeam Backup & Replication initiates the data synchronization of the configuration databases between the primary and secondary nodes.

Data Replication Algorithm

To synchronize data between the HA cluster nodes, Veeam Backup & Replication utilizes PostgreSQL database capabilities and leverages the database service that provides information on which node is primary and which node is secondary. Veeam Backup & Replication applies the streaming replication to synchronize the HA nodes: data is always written to the primary node, while the secondary node serves as a replica. The database service takes control of the primary and secondary node and initiates data synchronization between their databases.

1. PostgreSQL database service starts and constantly checks the PostgreSQL configuration.
2. PostgreSQL database service checks the HA cluster state and verifies that both HA nodes are available.
3. The High Availability maintenance job saves WAL logs on the primary node.
4. The High Availability maintenance job sends the following files to the secondary node.

* Configuration files used for registry-based settings.
* Configuration files used by the HA cluster to specify which data should be included or excluded from synchronization.

HA Cluster Alert Notification

If the secondary node in the HA cluster becomes unavailable for more than 10 minutes, the following notification mechanisms is used:

* Veeam Backup & Replication displays a notification in the notification bar.
* Veeam Backup & Replication sends an email alert to the email address that you specify in the [global email notification settings](general_email_notifications.md).

Once the secondary node is restored and operational, Veeam Backup & Replication sends a follow-up email notification to confirm that the cluster status is healthy.

High Availability Cluster Upgrade

To upgrade an HA cluster, Veeam Backup & Replication uses the [Veeam Updater service](update_appliances.md). The Veeam Updater service runs on both nodes. It uses the cluster IP address to communicate with the Veeam Identity Service and authorize against the Veeam Updater service on the secondary node. Veeam Backup & Replication starts upgrading the nodes from the primary node, and then synchronizes the updates with the secondary node. Automatic updates on the secondary node are disabled.

|  |
| --- |
| Important |
| Veeam Backup & Replication does not automatically install private fixes. You must do it manually using the Veeam Host Management console for every HA node. For more information, see [Installing Private Hotfixes](update_appliance_install_updates.md). |

To upgrade an HA cluster, Veeam Backup & Replication does the following:

1. Veeam Backup & Replication updates the primary node.
2. Veeam Backup & Replication gets updates installed on the primary node.
3. Veeam Backup & Replication gets all available updates from the secondary node and compares them with the updates installed on the primary node.
4. Veeam Backup & Replication creates a list of the updates that should be installed on the secondary node.
5. Veeam Backup & Replication sends a command to the secondary node to install the necessary updates.

Page updated 1/13/2026

Page content applies to build 13.0.1.1071
