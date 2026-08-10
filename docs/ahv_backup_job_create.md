---
title: "Creating Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_backup_job_create.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Backup Jobs


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

To create a backup job, you can either use the [Veeam Plug-in for Nutanix AHV web console](ahv_backup_web.md) or the [Veeam Backup & Replication console](ahv_backup_console.md). To create a backup job using the Veeam Backup & Replication console, do the following:

1. [Check prerequisites and limitations](ahv_backup_job_prerequisites.md).
2. [Launch the Add Job wizard](ahv_backup_job_vbr_launch_wizard.md).
3. [Configure general settings](ahv_backup_job_vbr_general_settings.md).
4. [Select resources to back up](ahv_backup_job_vbr_assign_vms.md).
5. [Configure backup target settings](ahv_backup_job_vbr_destination.md).
6. [Enable guest processing](ahv_backup_job_vbr_guest_processing.md).
7. [Create a schedule for the backup job](ahv_backup_job_vbr_schedule.md).
8. [Finish working with the wizard](ahv_backup_job_vbr_review.md).

Page updated 2026-03-20

