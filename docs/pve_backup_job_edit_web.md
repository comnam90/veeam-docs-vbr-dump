---
title: "Editing Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_edit_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Job Settings


For each job, you can modify settings configured while creating the job:

1. Navigate to Jobs.
2. Select the job.

You can select the job for editing even when it is running.

1. Click Edit:

* To provide a new name and description for the job, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_general_settings_web.md) (step 2).
* To edit the backup scope, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_assign_vms_web.md) (step 3).
* To change the backup repository where backups are stored, to configure backup job retention settings, to schedule active and synthetic full backups, to configure health checks and email notifications, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_destination_web.md) (step 4).
* To modify settings for application-aware processing of VMs included into the backup scope, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_guest_processing_web.md) (step 5).
* To modify the job schedule and configure automatic retry settings, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_schedule_web.md) (step 6).
* At the Summary step of the wizard, review configuration information and click Finish.

[![Editing Job Settings](images/pve_job_edit_web.webp)](images/pve_job_edit_web.webp "Editing Job Settings")

Page updated 2026-07-27

