---
title: "Data Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_restore_mssql_plugin.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Data Restore


With the configured Veeam Plug-In for Microsoft SQL Server, you can restore Microsoft SQL Server databases from Veeam Plug-In backups that reside on Veeam backup repositories.

Veeam Plug-In supports restore of entire databases to the original Microsoft SQL Server machine or to another server. You can specify a point in time to which you want to restore the database. This restore operation is based on backed up transaction logs. If there are no available backed up transaction logs, Veeam Plug-In restores the database to the time when the restore point was created. For details, see [Performing Restore](mssql_db_restore.md).

If you back up Microsoft SQL Server databases with Change Data Capture (CDC) enabled, and you want to preserve CDC configuration and metadata after restore, you must add the following parameter in the veeam\_config.xml file before you back up the database:

|  |
| --- |
| <PluginParameters RestoreWithKeepCdc="true" /> |

You can use the following tools to perform restore operations for Microsoft SQL Server databases:

* Restore with the Restore Database wizard.

Use the Restore Database wizard to restore Microsoft SQL Server databases based on Veeam Plug-In backups. For details, see [Restore with Restore Database Wizard](mssql_db_restore_ui.md).

* Restore with MSSQLRecoveryManager.exe tool in the command-line interface.

Use the MSSQLRecoveryManager.exe command-line tool to restore Microsoft SQL Server databases based on Veeam Plug-In backups. For details, see [Restore with Command-Line Interface](mssql_db_restore_cmd.md).

* Restore with Veeam Explorer for Microsoft SQL Server.

Use Veeam Explorer for Microsoft SQL Server to restore Microsoft SQL Server databases from the Veeam Backup & Replication console. For details, see [Restore with Veeam Explorer for Microsoft SQL Server](mssql_db_restore_vesql.md).


