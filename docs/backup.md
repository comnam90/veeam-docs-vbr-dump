---
title: "Backup for VMware vSphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Backup for VMware vSphere

In this article

Veeam Backup & Replication produces image-level backups of VMs. It treats VMs as objects, not as a set of files. When you back up VMs, Veeam Backup & Replication copies a VM image as a whole at a block level. Image-level backups can be used for different types of restore, including Instant Recovery, entire VM restore, VM file recovery, file-level recovery, and so on.

The backup technology is typically used for VMs with lower RTOs. When the primary VM fails, you need some time to restore VM data from a compressed and deduplicated backup file.

In This Section

* [About Backup](about_backup.md)
* [Creating Backup Jobs](backup_job.md)
* [Encrypting Backup Jobs](encrypting_backup_jobs.md)
* [Performing Active Full Backup](performing_active_full_backup.md)
* [Quick Backup](quick_backup.md)
* [Importing Backups Manually](importing_backups.md)
* [Managing Backups](managing_backups.md)
* [Managing Backup Jobs](managing_jobs.md)
* [Reporting](reporting.md)

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
