---
title: "Data Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_backup_mssql_plugin.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Data Backup


Veeam Plug-In for Microsoft SQL Server uses native Microsoft SQL Server mechanisms to create application-level backups of Microsoft SQL Server data. You can use Veeam Plug-In to create backups of the following types:

* Full backup
* Differential backup
* Log backup
* Copy-only full backup
* Copy-only log backup

For more information about Microsoft SQL Server backup types, see [Microsoft Documentation](https://learn.microsoft.com/en-us/sql/relational-databases/backup-restore/backup-overview-sql-server?view=sql-server-ver16).

|  |
| --- |
| Important |
| For read-only databases, Veeam Plug-In for Microsoft SQL Server supports only full and copy-only full backups. Differential, log and copy-only log backups are not supported. |

To create backups of a specific type, you must configure backup settings for Veeam Plug-In and run the backup process. You can run the backup process manually, immediately after you configure backup settings, or you can define schedule according to which Veeam Plug-In will back up Microsoft SQL Server data automatically. For more information, see [Backup Settings and Process](#bsettings) and [Backup Schedule](#schedule).

After Veeam Plug-In for Microsoft SQL Server starts the backup process, Veeam Backup & Replication creates the backup job. You can use this job to monitor backup processes and generate backup job reports. You cannot start or edit Microsoft SQL Server backup jobs in the Veeam Backup & Replication console. You can manage backup operations on Microsoft SQL Server only. For details, see [Managing Backup Job in Veeam Backup & Replication](mssql_job_vbr.md).

To store backups, you can add and configure backup repositories to your Veeam Backup & Replication infrastructure. For details on supported backup repositories, see [Veeam Backup Repositories](repos_mssql.md).

Backup Settings

Veeam Plug-In backs up Microsoft SQL Server databases according to backup settings that you specify. You can specify what databases to back up, what type of backups you want to create, retention policy for database backups and processing settings for backed-up data.

To specify backup settings and start the backup process, you can use the following tools:

* Back Up Database wizard

Use the Back Up Database wizard to specify the backup settings for Veeam Plug-In backups of Microsoft SQL Server databases. You can use Microsoft SQL Server Management Studio or a third-party scheduling tool to define the schedule for database backup. For details, see [Configuring Backup Settings](mssql_configure_backup.md).

* MSSQLRecoveryManager.exe tool in the command-line interface

Use the MSSQLRecoveryManager.exe tool to specify backup settings to configure, perform and schedule all types of backups in the command-line interface. You can also use the backup settings to modify Veeam Plug-In for Microsoft SQL Server commands used in custom scripts. For details, see [Performing Backup with Command-Line Interface](mssql_configure_backup_cmd.md).

If you want to perform backups of different types periodically, you must configure backup settings and specify schedule for each backup type. For example, you can specify settings for full backup, settings for differential backup and settings for log backup, save each of these settings as a separate SQL Agent job, and create schedule for these SQL Agent jobs in Microsoft SQL Server Management Studio.

Backup Schedule

Veeam Plug-In for Microsoft SQL Server does not offer its own backup schedule mechanisms. Instead, Veeam Plug-In allows database administrators to use tools of their choice to configure flexible schedule for database backup. For example, you can use native Microsoft SQL Server schedule settings to configure flexible schedule for full, differential or log backups, or use an external scheduling tool.

Veeam Plug-In for Microsoft SQL Server offers two scenarios for backup scheduling:

* Scenario 1. You can configure backup schedule in Microsoft SQL Server. To do this, you must save Veeam Plug-In backup settings as an SQL Agent job. For more information, see [Saving Backup Settings as SQL Agent Job](mssql_backup_script.md).

After that, you will be able to configure job schedule in the properties of the SQL Agent job in Microsoft SQL Server Management Studio.

* Scenario 2. You can use a third-party scheduling tool to create periodic backups of Microsoft SQL Server data with Veeam Plug-In. To do this, you must configure Veeam Plug-In backup settings and obtain a command that will be used to start the backup process. For more information, see [Exporting Backup Settings to Custom Script](mssql_backup_agent_job.md).

After that, you will be able to use the resulting command in a custom backup script or with a scheduling tool of your choice.


