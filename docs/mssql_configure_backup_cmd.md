---
title: "Performing Backup with Command-Line Interface"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_configure_backup_cmd.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Performing Backup with Command-Line Interface

In this article

You can perform backup of Microsoft SQL Server databases with Veeam Plug-In using the command-line interface.

To perform backup, do the following:

1. On Microsoft SQL Server, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
2. Run the MSSQLRecoveryManager.exe command with the required parameters. For more information, see [Backup Parameters](#options).

The following example shows a command to perform full backup of Microsoft SQL Server databases:

|  |
| --- |
| MSSQLRecoveryManager.exe --backup --d="IT" --d="Sales" --name="Database Backup" --description="Daily database backup" --type=full --parallelism=2 --instance="dlsql01\MSSQLSERVER" --retention=5 --use\_compression --check\_preferred |

|  |
| --- |
| TIP |
| You can also use the available backup parameters to modify Veeam Plug-In for Microsoft SQL Server commands used in custom scripts. For information, see [Exporting Backup Settings to Custom Script](mssql_backup_agent_job.md). |

Exit Codes

The MSSQLRecoveryManager.exe command can return the following exit codes:

* -1 — the service returns this code when the backup or restore process fails with an error.
* 0 — the service returns this code when the backup or restore process is successful.

Backup Parameters

You can specify the following parameters for backup of Microsoft SQL Server databases with the MSSQLRecoveryManager.exe command:

| Command | Description |
| --- | --- |
| --help | Shows the list of parameters for the MSSQLRecoveryManager.exe command. |
| --backup | Defines the backup operation. |
| --instance | Specifies the name of the SQL instance whose databases you want to back up.  The following values are possible:   * value is not specified — for default instance that resides on the standalone server * <hostname>\<instance\_name> — for named instance that resides on the standalone server * <cluster\_name> — for default instance that resides on the cluster node * <cluster\_name>\<instance\_name> — for named instance that resides on the cluster node   where:   * <hostname> — name of the host * <instance\_name> — name of the SQL instance * <cluster\_name> — name of the cluster |
| --d | Specifies the name of the database to back up.  This parameter is optional. If you do not use this parameter, Veeam Plug-In will back up all databases of the specified instance.  Alternatively, if you want to back up all databases of the instance except for the specified one, you can use the --ed parameter and specify the necessary database as its value. |
| --ed | Specifies the name of the database that must be excluded from the backup.  This parameter is optional. If you do not use this parameter, Veeam Plug-In will back up all databases of the specified instance.  Alternatively, if you want to back up a specific database, you can use the --d parameter and specify the necessary database as its value. |
| --name | Specifies the name for the backup set. |
| --description | Specifies the description for the backup set. |
| --type | Specifies the backup type. Possible values:   * full — full backup * diff — differential backup * log — log backup |
| --copy\_only | Defines the copy-only backup mode. You can use this parameter to create copy-only full backups or copy-only log backups of Microsoft SQL Server databases.  Keep in mind that differential backups cannot use the copy-only full backup as a starting point. To learn more, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/relational-databases/backup-restore/copy-only-backups-sql-server?view=sql-server-ver16). |
| --parallelism | Specifies the number of parallel data streams over which you want to back up Microsoft SQL Server data. For each backup stream, a separate VDI Device is started on Microsoft SQL Server. |
| --retention | Specifies the number of days to keep backups in the backup repository.  This parameter is optional. If you do not use this parameter, Veeam Plug-In will not apply the retention policy to the backup. |
| --check\_preferred | [For backup of Always On Availability Groups] Defines that Veeam Plug-In will check whether the availability replica is the preferred replica for backup. |
| --use\_compression | Defines that Veeam Backup & Replication mechanisms of data compression will be applied to the backup. To Veeam Plug-In for Microsoft SQL Server backups, the Optimal (ZSTD) compression level is applied. |

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
