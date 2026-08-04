---
title: "Creating Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_create_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Backup Jobs


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

To create a backup job, you can either use the [Veeam Plug-in for Proxmox VE web console](pve_backup_web.md) or the [Veeam Backup & Replication console](pve_backup_console.md). To create a backup job using the Veeam Plug-in for Proxmox VE web console, do the following:

1. [Check prerequisites and limitations](pve_backup_job_create_prerequisites_web.md).
2. [Launch the Add Job wizard](pve_backup_job_create_launch_web.md).
3. [Configure general settings](pve_backup_job_create_general_settings_web.md).
4. [Select resources to back up](pve_backup_job_create_assign_vms_web.md).
5. [Configure backup target settings](pve_backup_job_create_destination_web.md).
6. [Enable guest processing](pve_backup_job_create_guest_processing_web.md).
7. [Create a schedule for the backup job](pve_backup_job_create_schedule_web.md).
8. [Finish working with the wizard](pve_backup_job_create_summary_web.md).

Page updated 2026-07-01

