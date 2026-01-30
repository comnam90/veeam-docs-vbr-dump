---
title: "Support for Always On Availability Groups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_plugin_aon.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Support for Always On Availability Groups


Veeam Plug-In supports backup and restore of Microsoft SQL Server databases that operate as part of an Always On availability group.

The following types of availability groups are supported:

* Always On Availability Groups
* Always On Clusterless Availability Groups

Backup of Always On Availability Groups

To back up databases that operate as part of an Always On availability group, do the following:

1. Install and configure Veeam Plug-In for Microsoft SQL Server on each node of the cluster that runs Always On Availability Groups. For more information, see [Installing Veeam Plug-In for Microsoft SQL Server](install_mssql.md) and [Configuring Veeam Plug-In for Microsoft SQL Server](configuring_mssql_plugin.md).
2. Configure backup settings in Veeam Plug-In on each node and save backup settings as SQL Agent jobs in Microsoft SQL Server Management Studio. For more information, see [Configuring Backup Settings](mssql_configure_backup.md) and [Saving Backup Settings as SQL Agent Job](mssql_backup_script.md).
3. In Microsoft SQL Server Management Studio on each node, configure the same schedule settings for SQL Agent jobs so that database backup will start at the same time on each node.

Veeam Plug-In for Microsoft SQL Server performs backup of Always On Availability Groups in the following way:

1. When the SQL Agent job starts, Veeam Plug-In checks backup preferences specified in the properties of the Always On availability group.
2. If the node on which the SQL Agent job is running is the preferred node for backup, Veeam Plug-In performs backup. Otherwise, the backup process stops.

Consider the following:

* Veeam Plug-In does not check backup preferences of the Always On availability group if you start the backup process manually from the Veeam Plug-In UI.
* On secondary replicas, only full copy-only backup and log backup are supported. Differential backup is not supported.
* Veeam Plug-In does not add a restored database to an Always On availability group. You must perform this operation manually after the restore process is completed. For details, see [Restore of Always On Availability Groups](#aon_restore).

Restore of Always On Availability Groups

To restore a database that operates as part of an Always On availability group, complete the following steps:

1. Restore the database on the primary replica. During the restore process, Veeam Plug-In will remove the original database from the availability group and delete it from Microsoft SQL Server.
2. Perform log backup for the restored database.
3. Remove the original database from the secondary replica.
4. Add the restored database to the availability group.


