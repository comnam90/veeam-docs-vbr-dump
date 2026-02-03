---
title: "Editing Backup Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_edit.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Editing Backup Job Settings


For each backup job, you can modify settings configured while creating the job.

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, right-click the job and select Edit.

Alternatively, select the necessary job and click Edit on the ribbon.

1. Complete the Edit Job wizard:

1. To provide a new name and description for the job, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_general_settings.md) (step 2).
2. To edit the backup scope, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_assign_vms.md) (step 3).
3. To change the backup repository where backups are stored, to configure backup job retention settings, to schedule active and synthetic full backups, to configure health checks and email notifications, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_destination.md) (step 4).
4. To modify settings for application-aware processing of VMs included into the backup scope, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_guest_processing.md) (step 5).
5. To modify the job schedule and configure automatic retry settings, follow the instructions provided in section [Creating Backup Jobs](pve_backup_job_create_schedule.md) (step 6).
6. At the Summary step of the wizard, review configuration information and click Finish.

[![Editing Backup Job Settings](images/pve_backup_job_edit.webp)](images/pve_backup_job_edit.webp "Editing Backup Job Settings")


