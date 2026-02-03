---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_data_protection.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Performing Backup


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

In This Section

* [Creating Backup Jobs](pve_backup_job_create.md)
* [Editing Backup Job Settings](pve_backup_job_edit.md)
* [Starting and Stopping Backup Jobs](pve_backup_job_start.md)
* [Analyzing Performance Bottlenecks](pve_backup_job_bottlenecks.md)
* [Cloning Backup Jobs](pve_backup_job_clone.md)
* [Enabling and Disabling Backup Jobs](pve_backup_job_disable.md)
* [Deleting Backup Jobs](pve_backup_job_delete.md)
* [Creating Active Full Backups](pve_active_full_create.md)
* [Creating VeeamZIP Backups](pve_veeamzip_create.md)


