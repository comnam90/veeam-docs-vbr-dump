---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_data_protection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

In This Section

* [Creating Backup Jobs](uh_backup_job_create.md)
* [Cloning Backup Jobs](uh_backup_job_clone.md)
* [Editing Backup Job Settings](uh_backup_job_edit.md)
* [Starting and Stopping Backup Jobs](uh_backup_job_start.md)
* [Retrying Jobs](uh_retrying_jobs.md)
* [Analyzing Performance Bottlenecks](uh_backup_job_bottlenecks.md)
* [Enabling and Disabling Backup Jobs](uh_backup_job_disable.md)
* [Deleting Backup Jobs](uh_backup_job_delete.md)
* [Creating Active Full Backups](uh_active_full_create.md)
* [Creating VeeamZIP Backups](uh_veeamzip_create.md)

Page updated 2026-03-10

