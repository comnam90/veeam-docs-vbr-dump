---
title: "Active Full Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_active_full_backup.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Active Full Backup


In some cases, you need to regularly create a full backup. For example, your corporate backup policy may require that you create a full backup on weekend and run incremental backup on work days. To let you conform to these requirements, Veeam Plug-in for Scale Computing HyperCore allows you to create active full backups (either manually or automatically according to a specific schedule).

When creating an active full backup, Veeam Plug-in for Scale Computing HyperCore starts a new backup chain for the VM. All further created incremental backups use the latest active full backup file as a new starting point. The old full backup file from the old backup chain remains on disk until it is automatically deleted according to the retention policy.

![Active Full Backup](images/sch_active_full_backup.webp)

The active full backup session starts at the same time when the backup job is scheduled. For example, if you schedule the backup job to run at 12:00 AM Sunday through Friday, and schedule active full backup to be created on Saturday, Veeam Plug-in for Scale Computing HyperCore will start a backup job session that will produce an active full backup at 12:00 AM on Saturday.

If the backup job is not scheduled to run automatically or is disabled, Veeam Plug-in for Scale Computing HyperCore will not perform active full backup. If a regular backup session and an active full backup session are scheduled on the same day, Veeam Plug-in for Scale Computing HyperCore will produce an active full backup — an incremental backup that should have been created by the regular backup session will not be added to the backup chain. However, if you run the backup job again on the same day manually, Veeam Plug-in for Scale Computing HyperCore will perform incremental backup in a regular manner.


