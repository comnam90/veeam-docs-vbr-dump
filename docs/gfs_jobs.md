---
title: "GFS Backup to Tape"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gfs_jobs.html"
last_updated: "3/7/2024"
product_version: "13.0.1.1071"
---

# GFS Backup to Tape


The GFS tape job creates yearly archive for source machines by the GFS (Grandfather-Father-Son) scheme. The GFS archive includes one yearly backup and several quarterly, monthly, weekly and daily backups.

You can create GFS backups for VMs and Veeam agent computers (physical machines) on tape.

The GFS tape job does not process source machines. The job uses backups created by machine-to-disk jobs.

|  |
| --- |
| Note |
| GFS backup to tape does not support unstructured data backup jobs or repositories storing unstructured data backups as a source. However, if the backup repository stores not only unstructured data backups, but also backups that can be processed by a GFS backup to tape job, you can add this repository to the GFS backup to tape job: unstructured data backups will be skipped from processing. |

GFS Media Sets

To distinguish between the backup cycles, the GFS media pool has 5 predefined media sets: yearly, quarterly, monthly, weekly and daily.

| Media Set | Restore Point Type |
| --- | --- |
| Yearly | Full backup or synthesized virtual full backup |
| Quarterly |
| Monthly |
| Weekly |
| Daily | As on disk (for details, see [How GFS Backup to Tape Works](gfs_to_tape_hiw.md)) |

Individual Media Sets Configuration

You can configure each media set individually. You can set retention period, appending data to tape or other settings for each media set separately.

For example, the weekly backups must be stored for 4 weeks, data is appended, tapes may be overwritten. The yearly backups must be never overwritten, each backup on an individual tape (or set of tapes), tapes must be moved to vault.

Manual Active Full

You can manually create a restore point for any media set at any time with the Active full option. Veeam Backup & Replication will copy or synthesize the most recent full backup possible for the selected period. The manual active full is not available for the Daily media set.

Schedule Overlap

If the schedule for backup periods overlap, only the backup for the eldest media set will be archived. The media sets have the following priority: Yearly, Quarterly, Monthly, Weekly, Daily. For example, if "the first Sunday of January" is the date for the monthly, the quarterly and the yearly backup, the GFS job will create only the yearly backup; the monthly and the quarterly backups will be skipped.

Related Topics

* [How GFS Backup to Tape Works](gfs_to_tape_hiw.md)
* [Creating GFS Tape Jobs](creating_gfs_tape_jobs.md)
* [Viewing Backups on Tape](view_backups_on_tape.md)


