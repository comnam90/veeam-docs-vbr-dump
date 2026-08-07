---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_data_protection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

In This Section

* [Creating Backup Jobs](xen_backup_job_create.md)
* [Editing Backup Job Settings](xen_backup_job_edit.md)
* [Starting and Stopping Backup Jobs](xen_backup_job_start.md)
* [Analyzing Performance Bottlenecks](xen_backup_job_bottlenecks.md)
* [Cloning Backup Jobs](xen_backup_job_clone.md)
* [Enabling and Disabling Backup Jobs](xen_backup_job_disable.md)
* [Deleting Backup Jobs](xen_backup_job_delete.md)
* [Creating Active Full Backups](xen_active_full_create.md)
* [Creating VeeamZIP Backups](xen_veeamzip_create.md)

Page updated 2026-01-21

