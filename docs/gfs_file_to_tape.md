---
title: "GFS File and Object Storage Backup to Tape"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gfs_file_to_tape.html"
last_updated: "10/2/2025"
product_version: "13.0.1.1071"
---

# GFS File and Object Storage Backup to Tape


The GFS tape job allows you to archive files, folders and object storage data by the Grandfather-Father-Son (GFS) scheme. The GFS archive includes one yearly backup and several quarterly, monthly, weekly and daily backups.

You can create GFS backups for files, folders and objects from the following storage devices and object storage services:

* Windows servers, including physical boxes.
* Linux servers, including physical boxes.
* NAS devices (by specifying the path to the SMB (CIFS) or NFS file share) and SMB file shares organized into DFS.

* S3 Compatible Object storage
* Amazon S3
* Microsoft Azure Blob Storage

|  |
| --- |
| Note |
| [NDMP server backup](ndmp_servers_backup_to_tape.md) does not support GFS. |

GFS Media Sets

To distinguish between the backup cycles, the GFS media pool has 5 predefined media sets: yearly, quarterly, monthly, weekly and daily.

| Media Set | Restore Point Type |
| --- | --- |
| Yearly | Full backup |
| Quarterly |
| Monthly |
| Weekly |
| Daily | Incremental (for details, see [How GFS File and Object Storage Backup to Tape Works](gfs_file_to_tape_hiw.md)) |

Individual Media Sets Configuration

You can configure each media set individually. You can set the retention period, appending data to tape or other settings for each media set separately.

For example, the weekly backups must be stored for 4 weeks, data is not appended, tapes may be overwritten. The yearly backups must be stored for 10 years, each backup on an individual tape (or set of tapes), tapes must be moved to vault.

Manual Active Full

You can manually create a restore point for any media set at any time with the Active full option. The manual active full is not available for the Daily media set.

Schedule Overlap

If the schedules for backup periods overlap, only the backup for the eldest media set will be archived. The media sets have the following priority: Yearly, Quarterly, Monthly, Weekly, Daily. For example, if "the first Sunday of January" is the date for the monthly, the quarterly and the yearly backup, the GFS job will create only the yearly backup; the monthly and the quarterly backups will be skipped.

Related Topics

* [File Backup to Tape](file_to_tape_jobs.md)
* [Object Storage Backup to Tape](object_to_tape_jobs.md)


