---
title: "Restore with Command-Line Interface"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_db_restore_cmd.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Restore with Command-Line Interface


You can restore backup of Microsoft SQL Server databases with Veeam Plug-In using the MSSQLRecoveryManager.exe command-line tool.

If you want to restore databases from a Veeam Plug-In backup on another server, launch the wizard on the target server, where you want to place the new database backup.

To perform restore with the command-line interface, do the following:

1. On Microsoft SQL Server, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
2. Run the MSSQLRecoveryManager.exe command with the required parameters. For more information, see [Configuration Parameters](#options).

For example, to restore a Microsoft SQL Server database, use the following command:

|  |
| --- |
| MSSQLRecoveryManager.exe --restore --src\_server="srv16" --src\_instance="MSSQLSERVER" --src\_database="IT" --src\_backup="srv16 SQL Backup (Backup Vol 01)" --date="2022-08-17 09:03:49" --dst\_instance="MSSQLSERVER" --dst\_database="IT\_restored" --recovery\_state="recovery" --f="'IT'::'DC:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\IT.mdf'" --f="'IT\_log'::C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\IT\_log.ldf'" |

Exit Codes

The MSSQLRecoveryManager.exe command can return the following exit codes:

* -1 — the service returns this code when the backup or restore process fails with an error.
* 0 — the service returns this code when the backup or restore process is successful.

Restore Parameters

You can specify the following parameters for database restore with the MSSQLRecoveryManager.exe command:

| Command | Description |
| --- | --- |
| --help | Shows the list of parameters for the MSSQLRecoveryManager.exe command. |
| --restore | Defines the restore operation. |
| --src\_server | Specifies the name of the original server that contained the backed-up database. |
| --src\_instance | Specifies the name of the original SQL instance that contained the backed-up database. |
| --src\_cluster | Specifies the name of the original Microsoft SQL Server cluster that contained the backed-up database. |
| --src\_aon | Specifies the name of the original Always On availability group that contained the backed-up database. |
| --src\_database | Specifies the name of the database that you want to restore. |
| --src\_backup | Specifies the name of the Veeam Backup & Replication job that created the backup of the database you want to restore. |
| --src\_backup\_id | Specifies the unique identifier of the Veeam Backup & Replication job that created the backup of the database you want to restore.  If the unique identifier of the backup is not specified, you can use the name of the backup.  Keep in mind that if you specify both or neither the --src\_backup and --src\_backup\_id parameters when you initiate a restore script, the restore operation will fail. |
| --point\_in\_time | Specifies the point in time to which you want to restore the database.  This parameter is optional. If you do not use this parameter, Veeam Plug-In will restore the database to the time when the latest restore point was created. |
| --point\_in\_time\_utc | Specifies the point in time to which you want to restore the database using Coordinated Universal Time (UTC).  This parameter is optional. If you do not use this parameter, Veeam Plug-In will restore the database to the time when the latest restore point was created. |
| --dst\_instance | Specifies the name of the target SQL instance.  The following values are possible:   * value is not specified — for default instance that resides on the standalone server * <hostname>\<instance\_name> — for named instance that resides on the standalone server * <cluster\_name> — for default instance that resides on the cluster node * <cluster\_name>\<instance\_name> — for named instance that resides on the cluster node   where:   * <hostname> — name of the host * <instance\_name> — name of the SQL instance * <cluster\_name> — name of the cluster |
| --dst\_database | Specifies the name of the restored database.  This parameter is optional. If you do not use this parameter, Veeam Plug-In will restore the database with its original name.  If you restore the database with its original name to the original location, the original database will be overwritten. |
| --recovery\_state | Specifies the recovery state. Possible values:   * recovery. Rolls back (undo) any uncommitted changes. * norecovery. Skips the undo phase so that uncommitted or incomplete transactions are held open. This allows further restore stages to carry on from the restore point. When applying this option, the database will be in the norecovery state and inaccessible to users. * standby. The database will be in the standby state and therefore available for read operations. You can also provide a standby file with uncommitted transactions. |
| --standby\_file\_path | Specifies the path to a standby file with uncommitted transactions. |
| --f | Specifies the rules for database file mapping. Provide mapping rules in the following format: --f="'<DisplayName>'::'<TargetFileLocation>'".  For example: --f="'DB'::'D:\SQLServer\Data\DB.mdf'".  This parameter is optional. If you do not use this parameter, Veeam Plug-In will place database files to the same location and with the same name as for the original database. |
| --quick\_recovery | Applies differential and log backup to the existing database.  This parameter is optional. If you do not use this parameter, Veeam Plug-In will restore an entire database and then applies differential or log backup to the restored database. For details, see [Step 3. Specify Point in Time](mssql_db_restore_pit.md#quick). |


