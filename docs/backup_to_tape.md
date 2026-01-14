---
title: "Backup to Tape"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_to_tape.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Backup to Tape

In this article

The backup to tape job is a secondary backup as it additionally secures already backed up data allowing you to implement the ‘3-2-1’ backup approach (3 copies, 2 types of media, 1 offsite location). When a backup to tape job runs, it does not process source machines: it locates already existing backups and copies them from backup repository to tape. You can configure the backup to tape job to archive backups of specific primary jobs or to archive all backup within a specific repository.

The backup to tape job also allows you to implement the GFS (Grandfather-Father-Son) scheme and create yearly, quarterly, monthly, weekly and daily archives on tape.

In This Section

* [Before you Begin](tape_before_you_begin.md)
* [Backup to Tape](backup_to_tape_jobs.md)
* [GFS Backup to Tape](gfs_jobs.md)
* [Tenant Backup to Tape](tenant_backup_to_tape.md)
* [Linking Backup Jobs to Backup to Tape Jobs](linking_backup_to_backup_to_tape.md)
* [Viewing Backups on Tape](view_backups_on_tape.md)

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
