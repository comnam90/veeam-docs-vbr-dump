---
title: "Backup to Tape"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_rman_backup_to_tape.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup to Tape


If you want to store your Veeam Plug-In backups on tape, you can copy backups from a primary backup repository to a tape library by means of backup to tape jobs. From tape, you can later restore the backups to a backup repository for further database recovery operations.

Getting Started

Before you copy Veeam Plug-In backups to tape, you must complete the following preparation steps:

1. Add a tape server to your backup infrastructure. For details, see [Tape Servers](tape_servers.md).
2. Add media pools for full and incremental backups to your backup infrastructure. For details, see [Creating Media Pools](creating_custom_media_pools.md).
3. Create a Veeam Plug-In backup. Make sure that your Veeam Plug-In backups meet the requirements listed in section [Considerations and Limitations](#limitations).

After that, you can create a backup to tape job to make a copy of your database data in the tape library. For details, see [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md).

Considerations and Limitations

Before you copy Veeam Plug-In backups to tape, consider the following:

* Backups that you plan to copy to tape must be created with Veeam Plug-In version 12 or later.
* Veeam Backup & Replication supports the following tape libraries for Veeam Plug-In backups: Linear Tape-Open (LTO) and IBM 3592 (Jaguar). You can use physical libraries, standalone drives, virtual tape libraries, and partitions of physical or virtual tape libraries added to the Veeam backup infrastructure.
* Veeam Backup & Replication supports the following tape connections: direct connection over Fibre Channel (FC), Serial Attached SCSI (SAS) or SCSI, and remote connection over iSCSI or switched FC fabric.
* The GFS media pool is not supported for Veeam Plug-In backups.

How Backup to Tape Works

The backup to tape job consists of the following steps:

1. Veeam Backup & Replication will scan the source backup repository searching for Veeam Plug-In backups.

As a source for the backup to tape job, Veeam Backup & Replication can use any Veeam Plug-In backups created in standalone or managed mode, including backups produced by backup copy jobs.

1. Veeam Backup & Replication will generate the backup job metadata file (.VACM) and copy it to the tape library. This approach ensures that backup files stored on tape are not left without the central metadata even if the backup session fails.
2. After that, Veeam Backup & Replication will copy the backup data files (.VAB) and their backup metadata files (.VASM).

Veeam Backup & Replication will copy all closed backup files stored in the repository and skip backup files that are not yet closed. For details on when Veeam Plug-In for Oracle RMAN closes backup files, see [Reuse of Backup Files](rman_bfiles.md#bfiles_reuse).

Veeam Backup & Replication will copy backup files to tape at the database server level: one tape drive will write backup files of one server at a time. If your tape library has multiple tape drives and you set parallel processing in the media pool and application backup policy configurations, Veeam Backup & Replication will copy backup files of multiple servers in parallel — one server per tape drive. Backup files of the same server are never copied in parallel. This approach ensures that a single backup job metadata file is always created on tape.

Depending on the backup type, Veeam Backup & Replication will copy the Veeam Plug-In backup files to tape in the following way:

* In case of a full backup, Veeam Backup & Replication will copy all closed Veeam Plug-In backup files detected in the source repository and store them on tape.

* In case of an incremental backup, Veeam Backup & Replication will copy only those Veeam Plug-In backup files that were closed since the last full backup run and store them on tape.

With full and incremental backups on tape, you can create virtual full backups. In case of Veeam Plug-In backups, there are no synthetic operations during the virtual full creation: Veeam Backup & Replication copies all closed Veeam Plug-In backup files stored in the source backup repository and writes them to tape as a new full backup. If you want to create such backups, make sure that the export of virtual full backups is enabled even for backup chains with periodic fulls in the settings of the backup to tape job. To learn more, see [Choose Media Pool for Full Backups](backup_to_tape_pools.md).

How Restore from Tape Works

To restore a Veeam Plug-In backup from tape, you must perform 2 operations:

1. Restore the backup from tape to a disk-based backup repository.

* If you want to restore the content of the whole backup, restore it to a repository. For details, see [Restoring Backups from Tape to Repository](restoring_backups_from_tape.md). In this case, Veeam Backup & Replication restores the entire repository that was captured in the backup file. You cannot restore a specific Veeam Plug-In backup or a specific database.
* If you want to restore a specific Veeam Plug-In backup or database, you can restore individual backup files to a repository. For details, see [Restoring Files from Tape](restore_files_from_tapes.md).

|  |
| --- |
| Note |
| If a Veeam Plug-In backup is encrypted, the encryption keys are written to tape together with the backup. When you restore the backup, Veeam Backup & Replication decrypts it automatically if the Veeam Backup & Replication database contains a key with the same value and the same original ID. Otherwise, you must enter the original password. Re-encrypting a backup from the tape side is not supported. |

1. After you get the Veeam Plug-In backup in the disk-based backup repository, recover the database in the usual way.

For details, see [Database Recovery](oracle_db_restore.md).

Page updated 2026-07-10

