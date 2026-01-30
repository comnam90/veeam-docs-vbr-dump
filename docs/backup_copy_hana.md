---
title: "Creating Backup Copy Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_hana.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Creating Backup Copy Job


Veeam Backup & Replication offers the backup copy functionality that allows you to create several instances of the same backup in different locations, whether onsite or offsite. Backup copies have the same format as those created by backup jobs and you can recover your data from them when you need it.

Veeam Backup & Replication fully automates the backup copy process and lets you specify retention settings to maintain the desired number of restore points, as well as full backups for archival purposes. Backup copy is a job-driven process. When enabled, the backup copy job for Veeam Plug-In backups runs continuously. For details on how it works, see [Backup Copy](backup_copy.md).

You can configure a job and start it immediately or save the job to start it later.

Before creating a job, [check prerequisites](backup_copy_prerequisites_hana.md). Then use the New Backup Copy Job wizard to configure a backup copy job.

1. [Launch Backup Copy Job wizard](backup_copy_launch_hana.md).
2. [Specify a job name and description](backup_copy_name_hana.md).
3. [Select backups to process](backup_copy_backups_hana.md).
4. [Define backup copy target](backup_copy_target_hana.md).
5. [Specify advanced settings](backup_copy_advanced_hana.md).
6. [Define backup copy schedule](backup_copy_schedule_hana.md).
7. [Finish working with the wizard](backup_copy_summary_hana.md).


