---
title: "How GFS Backup to Tape Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gfs_to_tape_hiw.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# How GFS Backup to Tape Works


To create a GFS archive, Veeam Backup & Replication performs the following operations:

1. The GFS job starts according to the GFS job schedule and checks which media set is scheduled for today.
2. For GFS jobs with the Daily media set disabled, if some elder media sets are scheduled today:

* If the source job creates a full backup, the GFS job copies it.
* If the source job creates an incremental backup, the GFS job synthesizes a virtual full backup.

If the source job created several restore points, the tape job will copy only the first one.

1. For GFS jobs with the Daily media set enabled:

* If today some elder media sets are also scheduled, for example, the weekly media set, the GFS job archives the first restore point to the Weekly media set:

* If the source job creates a full backup, the GFS job copies it.
* If the source job creates an incremental backup, the GFS job synthesizes a virtual full backup.

* If there is more than 1 restore point on disk available, the GFS job copies the rest of them to the Daily media set.
* If only the Daily media set is due today, the GFS job copies all available restore points to the Daily media set.

1. The GFS job waits for the source backup to appear on the disk or for the source job to start till the end of the day. If the source job starts during the day, the GFS job waits till the source job finishes and copies the created backup to tapes. If the source backup doesn't appear or the source job does not start till midnight:

* [For Daily media set] The GFS job stops at midnight. It starts again next day according to the configured schedule.
* [For Weekly, Monthly, Quarterly and Yearly media sets] The GFS job copies the most recent restore point since the last GFS job run and stops. It starts again according to the configured schedule.

|  |
| --- |
| Important |
| The GFS job copies only new restore points. If the source job did not create a new point after the last GFS job run, the GFS job will not copy anything to tape. For example, if you want weekly backups in the tape GFS archive, make sure that the source job runs at least once a week. |

Consider the following:

* No restore point will be archived to the Daily media set when the daily backup overlaps elder media sets dates, and only one source restore point is available.
* No restore point will be archived to the Daily media set if the daily backup is delayed and starts the next day when some elder media sets are also scheduled. For example, a daily backup scheduled for Friday is delayed until Saturday because the source restore point is locked. It overlaps with the Weekly media set scheduled on Saturday. The GFS job archives the next restore point to the Weekly media set and skips the delayed daily backup.
* Incremental restore points in the Daily media set are linked to a full restore point in any media set. For example, a full restore point from the Weekly media set is used. If there is no full restore point that can be used for linking the daily increments, the tape job will create a virtual full backup and put it to the Daily media set.
* When you link a source job to a GFS job, the GFS job does not copy old restore points. The GFS job will copy only the restore point created on the day when the GFS job was linked to the source job or new restore points created later.
* If the restore point is available but locked (for example, if the source job is a backup copy job), the GFS job will wait for this restore point to become available for up to 7 days. If the restore point is still locked after 7 days, the GFS job will use the most recent restore point that is not locked.

If you do not want to wait, you can instruct the tape job to copy the most recent restore point instead of waiting. To do this, select the Process the most recent restore point instead of waiting check box in the settings of the tape job. For more details, see [Advanced Settings for GFS Tape Job](advanced_advanced_gfs.md).

* If you stop the tape job manually, it will start again the next day at the time scheduled.
* If you use the Daily media set, after creating or enabling a tape job it will be started within an hour even if the scheduled start time has already passed.
* If there is a technical problem, for example, the tape library is offline, or the backup server is down, the GFS job will not run. When the problem is fixed, the GFS job will archive one most recent missed full backup for each media set.
* If the GFS tape job was disabled manually for some period, it will skip all backups for this period after it is resumed.
* If the GFS job failed for some reason, it will try to restart every hour for 24 hours.

* If a job is unable to complete within a period of 21 days, it will be stopped with the Failed status.


