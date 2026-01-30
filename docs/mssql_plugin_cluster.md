---
title: "Support for SQL Server Failover Clusters"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_plugin_cluster.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Support for SQL Server Failover Clusters


Veeam Plug-In supports backup and restore of Microsoft SQL Server databases that operate as part of a failover cluster. Both Windows Server Failover Clusters with shared disks and Windows Server Failover Clusters with Cluster Shared Volumes (CSV) are supported.

To back up databases that operate as part of a failover cluster, do the following:

1. Install and configure Veeam Plug-In for Microsoft SQL Server on each node of the cluster. For more information, see [Installing Veeam Plug-In for Microsoft SQL Server](install_mssql.md) and [Configuring Veeam Plug-In for Microsoft SQL Server](configuring_mssql_plugin.md).
2. Configure backup settings in Veeam Plug-In on the active cluster node. For more information, see [Configuring Backup Settings](mssql_configure_backup.md).

On the passive node, the SQL instance that operates as part of the cluster is not displayed in the Veeam Plug-In UI.

1. Save backup settings as an SQL Agent job in Microsoft SQL Server Management Studio. For more information, see [Saving Backup Settings as SQL Agent Job](mssql_backup_script.md).

Veeam Plug-In for Microsoft SQL Server will start the backup job on the active cluster node.

To restore a database that operates as part of a failover cluster, you must start the restore process on the active cluster node. On the passive node, the backed-up SQL instance is not displayed in the Veeam Plug-In UI.


