---
title: "Oracle RMAN Incremental Merge"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_rman_incremental_merge_overview.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Oracle RMAN Incremental Merge


Oracle RMAN Incremental Merge is a backup strategy that combines forever-incremental backup with quick database recovery. Oracle RMAN creates an image copy of the database, then regularly creates incremental backups and merges them into this copy. The image copy is always up to date and ready for use. To recover the database, you switch it to the image copy. Oracle RMAN only updates the control file and does not copy any data back to the production storage, so the database returns to operation within minutes regardless of the database size.

To create and merge incremental backups, you must use an application backup repository. Veeam Backup & Replication will create immutable snapshots of this repository and turn them into restore points. Using these restore points, you can revert the image copy to an earlier state and quickly recover the database to a required point in time. For more information, see [Application Backup Repositories](application_backup_repository.md).

Getting Started

To back up an Oracle database using Oracle RMAN Incremental Merge, you must perform the following operations:

1. On the Veeam Backup & Replication server, do the following:

1. Add an application backup repository to the Veeam Backup & Replication backup infrastructure. When you create the repository, allow access to the NFS share for the Oracle server and configure the snapshot schedule. For more information, see [Adding Application Backup Repositories](abr_repository_add.md).
2. Mount the NFS share configured of the application backup repository on the Oracle server.

1. On the Oracle server, do the following:

1. Create an image copy of the database with a level 0 incremental backup. The backup must include the archived redo logs, control file, and SPFILE.
2. Start creating regular level 1 incremental backups. During each run, Oracle RMAN will back up data blocks changed since the previous run and merge the incremental backup into the image copy.

|  |
| --- |
| Note |
| Veeam Backup & Replication does not orchestrate the backup process on the Oracle server side. You must schedule the backup scripts on the Oracle server, for example, using Oracle Scheduler. |

For more information, see [Oracle RMAN Incremental Backup and Merge](plugins_rman_incremental_merge.md).

In case of a disaster, you can recover the database using the image copy and application backup repository snapshots. For more information, see [Restore from Application Backup Repository](plugins_rman_restore_abr.md).

Considerations and Limitation

Before you configure Oracle RMAN Incremental Merge, consider the following:

* Veeam Backup & Replication cannot verify the consistency of the image copy and other Oracle backup files in a snapshot in the application backup repository. For example, if you did not back up the control file and SPFILE to the NFS share before the snapshot was created, Veeam Backup & Replication does not report any error, but you cannot restore the database from this snapshot. Similarly, Veeam Backup & Replication does not indicate which control file and SPFILE backups on the share match the image copy in a snapshot. When you restore the database, you must identify the matching files yourself.
* Make sure that the snapshot captures the image copy after the latest incremental backup is merged. A snapshot created while the backup script is running or before the incremental backup is merged produces an inconsistent restore point.
* Store the image copy of one Oracle database per application backup repository. In case of instant recovery operation, Veeam Backup & Replication rolls back the entire NFS share and affects all data stored in the application backup repository. For more information on the recovery of the application backup repository, see [Performing Instant Application Backup Repository Recovery](performing_abr_recovery.md).
* Access to the backup files depends on the access settings of the application backup repository:

* If you access the NFS share by host/IP address permission without Kerberos authentication, all OS users of the Oracle server have read and write permissions on the share and can access the backup files. As a result, you can run the backup scripts under any OS account.
* If you use Kerberos authentication to access the NFS share, only accounts that are granted read and write access in the repository settings can create and modify files on the share. Make sure that the OS user that owns the Oracle instance has a valid Kerberos ticket for such an account. Otherwise, Oracle RMAN cannot create backup files on the share.

Keep in mind that after you revert the repository to a snapshot or change the access permissions in the repository settings, the owner of the files and folders that already exist on the share may change, and the execute permission, which is required to open folders, is added to all folders. However, the accounts granted access in the repository settings keep their access to the files through ACLs.

Page updated 2026-07-24

