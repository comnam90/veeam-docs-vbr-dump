---
title: "Backup Chain"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_files.html"
last_updated: "7/19/2024"
product_version: "13.0.1.1071"
---

# Backup Chain

In this article

A backup chain is a sequence of backup files created by jobs. The backup chain provides the ability to recover data.

The backup chain consists of the first full backup file, incremental backup files, metadata files and some additional files. Full and incremental backup files correspond to restore points of the backed-up VM. You can think of restore points as "snapshots" of VM data at specific points in time. Restore points let you roll back VMs to the necessary state.

The type of backup files and how Veeam Backup & Replication orders them in the backup chain depend on the chosen backup method. For more information, see [Backup Methods](backup_methods.md).

The amount of backup chains for backed-up VMs depends on the chosen backup chain format. For more information, see [Backup Chain Formats](per_vm_backup_files.md).

Backup Files

Veeam Backup & Replication creates and maintains the following types of backup files:

* VBK — full backup files that store copies of full VM images.
* VIB or VRB — incremental backup files that store incremental changes of VM images.
* VBM — backup metadata files that store information about the backup job, VMs processed by the backup job, number and structure of backup files, restore points, and so on. Metadata files facilitate the import of backups, backup mapping and other operations.

In addition to these file types, Veeam Backup & Replication can create the following files in the backup repository:

* VSB — virtual synthetic backup files used to generate virtual full backups on tapes. For more information, see [Virtual Full Backup](virtual_full_backup.md).
* VLB, VSM and VLM — files that store Microsoft SQL Server transaction log data. For more information, see [Microsoft SQL Server Log Backup](sql_backup.md).
* VLB, VOM and VLM — files that store Oracle archived log data. For more information, see [Oracle Log Backup](oracle_backup.md).
* VLB, VPM and VLM — files that store PostgreSQL WAL files. For more information, see [PostgreSQL WAL Files Backup](postgresql_backup.md).

All backup files created by the backup job reside in a dedicated job folder in the backup repository. For example, if you create a backup job with the DC Backup name, Veeam Backup & Replication will create the DC Backup folder on the target backup repository and store all backup files produced with this job in this folder.

Rolling Back VMs

To roll back a VM to a specific point in time, you need a chain of backup files: a full backup file plus a set of incremental backup files dependent on this full backup file. If some file in the backup chain is missing, you will not be able to roll back to the necessary state. For this reason, you must not manually delete separate backup files from the backup repository. Instead, you must specify retention policy settings that will let you maintain the desired number of backup files in the backup repository.

In This Section

* [Backup Methods](backup_methods.md)
* [Backup Chain Formats](per_vm_backup_files.md)
* [Full Backup Methods](full_backup_methods.md)
* [Short-Term Retention Policy](retention_policy.md)
* [Long-Term Retention Policy (GFS)](gfs_retention_policy.md)
* [Background Retention](background_retention_job.md)

Page updated 7/19/2024

Page content applies to build 13.0.1.1071
