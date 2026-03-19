---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_data_protection.html"
last_updated: "3/10/2026"
product_version: "13.0.1.2067"
---

# Performing Backup


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

In This Section

* [Creating Backup Jobs](hpe_backup_job_create.md)
* [Cloning Backup Jobs](hpe_backup_job_clone.md)
* [Editing Backup Job Settings](hpe_backup_job_edit.md)
* [Starting and Stopping Backup Jobs](hpe_backup_job_start.md)
* [Retrying Jobs](hpe_retrying_jobs.md)
* [Analyzing Performance Bottlenecks](hpe_backup_job_bottlenecks.md)
* [Enabling and Disabling Backup Jobs](hpe_backup_job_disable.md)
* [Deleting Backup Jobs](hpe_backup_job_delete.md)
* [Creating Active Full Backups](hpe_active_full_create.md)
* [Creating VeeamZIP Backups](hpe_veeamzip_create.md)


