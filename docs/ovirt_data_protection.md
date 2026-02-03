---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_data_protection.html"
last_updated: "1/30/2026"
product_version: "13.0.1.1071"
---

# Performing Backup


To produce backups of oVirt VMs, Veeam Plug-in for oVirt KVM runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

You can instruct the Veeam Plug-in for oVirt KVM to run jobs automatically according to a specified schedule or start them manually.

In This Section

* [Creating Backup Jobs](ovirt_backup_job_create.md)
* [Editing Backup Job Settings](ovirt_editing_jobs.md)
* [Starting and Stopping Backup Jobs](ovirt_start_job.md)
* [Analyzing Performance Bottlenecks](ovirt_bottlenecks.md)
* [Cloning Backup Jobs](ovirt_cloning_jobs.md)
* [Enabling and Disabling Backup Jobs](ovirt_disable_jobs.md)
* [Deleting Backup Jobs](ovirt_delete_jobs.md)
* [Creating Active Full Backups](ovirt_crearting_active_full_backup.md)
* [Creating VeeamZIP Backups](ovirt_veeamzip_backup_create.md)


