---
title: "Creating Backup Copy Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup_copy.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Creating Backup Copy Job

In this article

The main backup purpose is to protect your data against disasters and virtual or physical machine failures. However, having just one backup does not provide the necessary level of safety. The primary backup may get destroyed together with production data, and you will have no backups from which you can restore data.

To build a successful data protection and disaster recovery plan, it is recommended that you follow the 3-2-1 rule:

* 3: You must have at least three copies of your data: the original production data and two backups.
* 2: You must use at least two different types of media to store the copies of your data, for example, local disk and cloud.
* 1: You must keep at least one backup off-site, for example, in the cloud or in a remote site.

Thus, you must have at least two backups and they must be in different locations. If a disaster takes out your production data and local backup, you can still recover from your off-site backup.

To help you adopt the 3-2-1 rule, Veeam Backup & Replication offers backup copy capabilities. Backup copy allows you to create several instances of the same backup data in different locations, whether on-site or off-site. Backup copies have the same format as those created by backup jobs and you can recover your data from them when you need it.

Backup copy is a job-driven process. Veeam Backup & Replication fully automates the backup copy process and lets you specify retention settings to maintain the desired number of restore points, as well as full backups for archival purposes.

Before creating a job, [check prerequisites](mongo_backup_copy_prerequisites.md). Then use the New Backup Copy Job wizard to configure a backup copy job.

1. [Launch Backup Copy Job wizard](mongo_backup_copy_launch.md).
2. [Specify a job name and description](mongo_backup_copy_name.md).
3. [Select backups to process](mongo_backup_copy_backups.md).
4. [Define backup copy target](mongo_backup_copy_target.md).
5. [Map a backup file](mongo_backup_copy_mapping.md).
6. [Specify advanced settings](mongo_backup_copy_advanced.md).
7. [Specify data path settings](mongo_backup_copy_data_path.md).
8. [Define backup copy schedule](mongo_backup_copy_schedule.md).
9. [Finish working with the wizard](mongo_backup_copy_summary.md).

Page updated 8/25/2025

Page content applies to build 13.0.1.1071
