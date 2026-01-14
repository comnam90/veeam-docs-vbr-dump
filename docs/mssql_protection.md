---
title: "Performing Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_protection.html"
last_updated: "2/12/2025"
product_version: "13.0.1.1071"
---

# Performing Backup

In this article

After you [configure Veeam Plug-In settings](configuring_mssql_plugin.md), you can use Veeam Plug-In to back up Microsoft SQL Server databases. Veeam Plug-In uses native Microsoft SQL Server mechanisms to create application-level backups of Microsoft SQL Server data.

Veeam Plug-In backs up Microsoft SQL Server databases according to backup settings that you specify. You can specify what databases to back up, the type of database backups you want to create, retention policy for database backups and processing settings for backed-up data. In addition, you can use Microsoft SQL Server Management Studio or a third-party scheduling tool to define schedule for database backup.

|  |
| --- |
| Note |
| Backups created by Veeam Plug-Ins cannot be used as a source for file to tape or backup to tape jobs. |

In This Section

* [Configuring Backup Settings](mssql_configure_backup.md)
* [Saving Backup Settings as SQL Agent Job](mssql_backup_script.md)
* [Exporting Backup Settings to Custom Script](mssql_backup_agent_job.md)
* [Performing Backup with Command-Line Interface](mssql_configure_backup_cmd.md)
* [Managing Backup Job in Veeam Backup & Replication](mssql_job_vbr.md)
* [Managing Backups in Veeam Backup & Replication](mssql_backup_vbr.md)

Page updated 2/12/2025

Page content applies to build 13.0.1.1071
