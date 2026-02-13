---
title: "Required Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_bu_job_settings.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Required Job Settings


The required job settings depend on whether you want to use an image-level backup created with native Veeam Backup & Replication functionality or an application backup created with Veeam Plug-In for Microsoft SQL Server.

Image-Level Backups

When you create backup jobs, replication jobs, and CDP policies, make sure to enable application-aware processing in the Veeam Backup & Replication console.

You can configure this setting at the Specify Guest Processing Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see [Specify Guest Processing Settings](backup_job_vss_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console.

Without application-aware processing, the created restore points will be crash-consistent only.

For more information about configuring transaction logs, see the Microsoft SQL Server Transaction Log Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see Microsoft SQL Server [Transaction Log Settings](backup_job_vss_sql_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console.

Veeam Explorer for Microsoft SQL Server allows you to explore crash-consistent restore points with heuristic analysis, which scans the restore point for application data. Note that application item restore from crash-consistent restore points is less reliable than restore from application-consistent restore points. Without application-aware processing, the restore point could contain unfinished database transactions or incomplete application files, which may affect data recovery.

Consider the following:

* For backups made with [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/data_protection.html) and [Veeam Plug-in for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/data_protection.html), application-aware processing is not supported.
* For VeeamZIP backups, application-aware processing is not supported. For more information, see [VeeamZIP](veeamzip.md).
* For storage snapshots, application-aware processing is automatically enabled. For more information, see [Application Item Restore from Storage Snapshots](restore_veeam_explorers_snapshots.md).

Backups Created with Veeam Plug-In for Microsoft SQL Server

You can create backups of Microsoft SQL Server databases using application backup policies managed by Veeam Backup & Replication and backup jobs managed by a standalone Veeam Plug-In for Microsoft SQL Server.

* To create an application backup policy managed by Veeam Backup & Replication, do the following:

1. Add the source Microsoft SQL Server machine to a protection group. For more information, see [Creating Protection Group for Individual Computers](protection_group_individual.md).
2. Create an application backup policy using the protection group. For more information, see [Creating](create_policy_create_microsoft_sql_server.md) Microsoft SQL Server [Backup Policy](create_policy_create_microsoft_sql_server.md).

* To create a backup job managed by a standalone Veeam Plug-In for Microsoft SQL Server, you can create a backup job with the plug-in backup wizard or with the command-line interface. For more information, see [Performing Backup](mssql_protection.md).

After the SQL plug-in backups are successfully created using one of these methods, you can use Veeam Plug-In for Microsoft SQL Server to restore your data.

Recovery Model

|  |
| --- |
| Note |
| To be able to restore your data as of a point in time or as of a state before undesired transactions, make sure the recovery model for the database is set to full or bulk-logged. |

The following table lists database logging models and applicable options in Veeam Backup & Replication.

| SQL DB Logging Model | Veeam Backup & Replication Options | | |
| --- | --- | --- | --- |
|  | Truncate logs | Do not truncate logs | Backup logs periodically |
| Simple | Databases are skipped from processing. | Applicable option. | Databases are skipped from processing.  Log files do not grow (and do not need to be backed up). |
| Full | Applicable option.  Veeam Backup & Replication performs "backup to NUL" for log files on guest. | Applicable but not recommended to use without native or 3rd party means of log truncation or backup – otherwise, logs will increase in size. | Applicable option. Log backup files (in the BAK format) are copied from the temporary folder on the Microsoft SQL Server machine to a backup repository. As soon as the data is copied to the target, BAK files are deleted from the source. |
| Bulk-logged | Applicable option.  Veeam Backup & Replication performs "backup to NUL" for log files on guest. | Applicable but not recommended to use without native or 3rd party means of log truncation or backup – otherwise, logs will increase in size. | Applicable option. Log backup files (in the BAK format) are copied from the temporary folder on the Microsoft SQL Server machine to a backup repository. As soon as the data is copied to the target, BAK files are deleted from the source. |


