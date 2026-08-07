---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_db_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


You can restore Microsoft SQL Server databases from backups created with Veeam Plug-In. Veeam Plug-In supports restore of entire databases to the original Microsoft SQL Server machine or to another server.

You can restore a database to the same or different SQL instance. If you have backup of Microsoft SQL Server transaction logs, you can specify a point in time to which you want to restore the database. Otherwise, Veeam Plug-In will restore the database to the time when the restore point was created.

|  |
| --- |
| Important |
| It is recommended to create a full backup immediately after you restore a database. All subsequent log or differential backups of the restored database will be based on this full backup. This action helps prevent potential data loss. |

Before you perform database restore, consider the following:

* The backup job that created the backup must be present in Veeam Backup & Replication.

* To restore to another server, you must perform the restore operation on the target server, where you want to place the new database backup.
* To restore to another server under another user account, you can use on of the following options:

* Use the user account that either has the Backup Administrator, or both the Backup Operator and Restore Operator roles.
* Use the recovery token generated on the Veeam Backup & Replication side.

* To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067.

To learn more about options to restore to another server, see [Restore to Another Server](mssql_db_restore_another_server.md).

To restore Microsoft SQL Server databases, you can use the following tools:

* The Restore Database wizard. For details, see [Restore with Restore Database Wizard](mssql_db_restore_ui.md).
* The MSSQLRecoveryManager.exe command-line tool. For details, see [Restore with Command-Line Interface](mssql_db_restore_cmd.md).
* Veeam Explorer for Microsoft SQL Server. For details, see [Restore with Veeam Explorer for Microsoft SQL Server](mssql_db_restore_vesql.md).

Page updated 2026-07-30

