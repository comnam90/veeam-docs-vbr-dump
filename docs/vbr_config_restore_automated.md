---
title: "Automating Configuration Database Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_restore_automated.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Automating Configuration Database Restore


If you want to automate the process of the configuration database restore, you can do it using the Veeam.Backup.Configuration.UnattandedRestore.exe file.

Limitations and Considerations

Before you start the restore process, check the [prerequisites](restore_vbr_before_you_begin.md).

Restoring Configuration Database

To restore Veeam Backup & Replication configuration database using the Veeam.Backup.Configuration.UnattendedRestore.exe file, perform the following steps:

1. [Generate Configuration File](#step1).
2. [Specify Restore Settings](#step2).
3. [Restore Configuration Database](#step3).

Step 1. Generate Configuration File

To generate the configuration file, do the following:

1. Open the command prompt.
2. Change the directory to the directory where the Veeam.Backup.Configuration.UnattendedRestore.exe file is stored. By default, C:\Program Files\Veeam\Backup and Replication\Backup.

|  |
| --- |
| cd "C:\Program Files\Veeam\Backup and Replication\Backup" |

1. Use the following command to generate the configuration file. In the generate parameter, specify the path where the configuration file will be saved.

|  |
| --- |
| Veeam.Backup.Configuration.UnattendedRestore.exe /generate:C:\backup\unattended.xml |

Alternatively, you can complete the [configuration restore wizard](vbr_config_restore.md) and click Export answer file on the [Summary](vbr_config_summary.md) step of the wizard. In this case, the configuration file will contain parameters you specified during the restore process.

Step 2. Specify Restore Settings

After you execute the command, the configuration file will be generated with default preferences by the path you specified. You can manually edit the file to specify the necessary parameters.

Step 3. Restore Configuration Database

To restore the configuration database, do the following:

1. Open the command prompt.
2. Change the directory to the directory where the Veeam.Backup.Configuration.UnattendedRestore.exe file is stored. By default, C:\Program Files\Veeam\Backup and Replication\Backup.

|  |
| --- |
| cd "C:\Program Files\Veeam\Backup and Replication\Backup" |

1. Use the following command to restore the configuration file. In the file parameter, specify the path where the configuration file is stored.

|  |
| --- |
| Veeam.Backup.Configuration.UnattendedRestore.exe /file:C:\backup\unattended.xml |

Veeam Backup & Replication will use the preferences specified in the unattended.xml file to perform the configuration database restore.

The path to the log file is %ProgramData%\Veeam\Backup\Utils\Util.VeeamBackupConfiguration.UnattendedRestore.log.

Configuration File Parameters

| Parameter | Description | Required |
| --- | --- | --- |
| MODE | Specifies the restore mode.  Supported values: restore or migrate.  Note: For the configuration database restore, specify the restore mode. | Yes |
| CONFIGURATION\_FILE | Specifies a full path to the configuration backup file.  Supported values:   * For local backup files: C:\Backup\VeeamConfigBackup\VM\VM\_2022-12-04\_13-01-38.bco. * For network backup files: \\VM\Backups\VM\_2022-12-04\_13-01-38.bco. * For repository backup files: VeeamConfigBackup\VM\VM\_2022-12-04\_13-01-38.bco. | Yes |
| REPOSITORY\_NAME | Specifies Veeam Backup & Replication repository name where the configuration backup file is stored. If you do not specify this parameter, empty name will be used.  Supported values: String. | No |
| BACKUP\_PASSWORD | Specifies the password to decrypt the configuration backup file.  Supported values: String. | No |
| NETWORK\_USER | Specifies the user account for the network share.  Supported values: domain\username. | No |
| NETWORK\_PASSWORD | Specifies the password for the network share.  Supported values: String. | No |
| SQLSERVER\_ENGINE | Specifies the database engine.  Supported values: mssql or postgresql.  Default: postgresql. | No |
| DATABASE\_SERVER | Specifies the database server and instance on which the configuration database will be deployed.  Supported values:   * Microsoft SQL Server: MSSQLSERVER\DBINSTANCE:PORT. * PostgreSQL Server: POSTGRESQLSERVER:PORT. | Yes |
| SQLSERVER\_DATABASE | Specifies the name for the configuration database.  Supported values: String.  Default: VeeamBackup. | No |
| SQLSERVER\_AUTHENTICATION | Specifies the authentication mode to connect to the database server where the Veeam Backup & Replication configuration database will be deployed.  Supported values:   * Windows authentication: 0. * SQL native authentication: 1.   Default: 0. | No |
| VBR\_SQLSERVER\_USERNAME | Specifies a LoginID to connect to the SQL server in the native authentication mode  Supported values: String.  Note: The parameter is required if the SQLSERVER\_AUTHENTICATION parameter value is 1. | No |
| VBR\_SQLSERVER\_PASSWORD | Specifies a password to connect to the SQL server in the native authentication mode.  Supported values: String.  Note: The parameter is required if you specify the VBR\_SQLSERVER\_USERNAME parameter. | No |
| PG\_DUMP\_PATH | Specifies a path to the pg\_dump.exe file.  Supported values: String. | No |
| RESTORE\_BACKUPS | Defines that Veeam Backup & Replication will restore backup and replica restore points catalog.  Supported values:   * No: 0. * Yes: 1.   Default: 1. | No |
| RESTORE\_SESSIONS | Defines that Veeam Backup & Replication will restore sessions history.  Supported values:   * No: 0. * Yes: 1.   Default: 0. | No |
| ENABLE\_POWERSHELL\_POLICY | Defines that PowerShell execution policy will be set to work for SCVMM.  Supported values:   * No: 0. * Yes: 1.   Default: 1. | No |
| BACKUP\_EXISTING\_DATABASE | Defines that the current database will be backed up.  Supported values:   * No: 0. * Yes: 1.   Default: 0. | No |
| SERVICES\_AUTOSTART | Defines that Veeam Backup & Replication will start automatically after the migration.  Supported values:   * No: 0. * Yes: 1.   Default: 1. | No |
| CREATE\_NEW\_DATABASE | Defines that the new database will be created if it does not exist.  Supported values:   * No: 0. * Yes: 1.   Default: 1. | No |
| USE\_EXISTING\_DATABASE | Defines that Veeam Backup & Replication will use an existing database if it is not empty.  Supported values:   * No: 0. * Yes: 1.   Default: 0. | No |
| USE\_LOCKED\_DATABASE | Defines that Veeam Backup & Replication will use an existing database owned by another backup server.  Supported values:   * No: 0. * Yes: 1.   Default: 1. | No |
| OVERWRITE\_EXISTING\_DATABASE | Defines that the new database will overwrite the existing one.  Supported values:   * No: 0. * Yes: 1.   Default: 0. | No |
| STOP\_PROCESSES | Defines that Veeam Backup & Replication will terminate all running backup server processes.  Supported values:   * No: 0. * Yes: 1.   Default: 0. | No |
| SWITCH\_TO\_RESTORE\_MODE | Defines that the configuration restore will switch to the restore mode if enabled backup jobs are found.  Supported values:   * No: 0. * Yes: 1. * Cancel: 2.   Default: 2. | No |
| RETRY\_COUNT | Specifies the amount of retries that configuration restore should perform.  Supported values: Int32.  Default: 3. | No |
| ACCEPT\_FOUND\_DATABASE\_ISSUES | Defines that the configuration restore will proceed if database issues are found.  Supported values:   * No: 0. * Yes: 1.   Default: 0. | No |
| CREDENTIALS | Specify this parameter if you want to update stored passwords during the configuration restore. If you do not specify this parameter, passwords will not be updated  Supported values: user=password;{hint}. | No |
| PRIVATE\_KEYS | Specify this parameter if you want to update stored private keys during the configuration restore. If you do not specify this parameter, private keys will not be updated.  Supported values: user=privatekey;password;{hint}. | No |
| HOSTS | Forces target server components upgrade if necessary. If you do not specify this parameter, all hosts will be upgraded.  Note: If you specify only several hosts out of all hosts in your backup infrastructure, only these hosts will be upgraded. Do not specify this parameter if you want to upgrade all hosts.  Supported values: DNS name\IP address. | No |


