---
title: "Creating GFS Tape Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/creating_gfs_tape_jobs.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Creating GFS Tape Jobs


To create a GFS archive on tape, you need to create a [GFS media pool](creating_gfs_media_pools.md) and target a backup to tape job to it. Technically, a GFS tape job is a variant of backup to tape job. When you select a GFS media pool as target, the job schedule automatically changes to the GFS mode. For details, see [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md).

As a source, you can use a backup job with any backup method: forever forward incremental, forward incremental or reverse incremental.

|  |
| --- |
| Note |
| If you use a job with enabled GFS retention as a source for a GFS tape job, the GFS tape job writes restore points to tapes according to its own schedule. The schedule of the source job is not taken into account. |

Related Topics

* [Creating GFS Media Pools](creating_gfs_media_pools.md)
* [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md)


