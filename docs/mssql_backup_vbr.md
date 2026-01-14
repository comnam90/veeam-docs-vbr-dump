---
title: "Managing Veeam Plug-In Backups in Veeam Backup & Replication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_backup_vbr.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Managing Veeam Plug-In Backups in Veeam Backup & Replication

In this article

In the Veeam Backup & Replication console, backups created by Veeam Plug-Ins are displayed in the Backups node of the Home view. In the working area, backups created by Veeam Plug-In for IBM Db2 are listed under the Microsoft SQL node.

For backups created by Veeam Plug-In for Microsoft SQL Server, consider the following:

* In the working area, backups created by Microsoft SQL Server are listed under the Microsoft SQL node.
* In the list of Microsoft SQL Server backups, Veeam Backup & Replication displays one backup for a standalone Microsoft SQL Server, Microsoft SQL Server failover cluster or Always On availability group. This backup contains all restore points created for different databases that reside on this server, cluster or availability group.

* Veeam Backup & Replication generates names for Microsoft SQL Server backups according to the following rules:

* For standalone Microsoft SQL Server, Veeam Backup & Replication generates the backup name based on name of Microsoft SQL Server.
* For Microsoft SQL Server that operates as part of a failover cluster or availability group, Veeam Backup & Replication generates the backup name based on the name of the cluster or name of the availability group.

You can use the Veeam Backup & Replication console to perform the following operations with Veeam Plug-In for Microsoft SQL Server backups:

* [Delete a backup from the backup repository](delete_backups_mssql.md)
* [Remove a backup from configuration](delete_backups_config_mssql.md)

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
