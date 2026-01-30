---
title: "Step 4. Select Application Group"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_appgroup_hv.html"
last_updated: "11/22/2023"
product_version: "13.0.1.1071"
---

# Step 4. Select Application Group


Selecting application group is available only for SureBackup job working in Full recoverability testing mode.

At the Application Group step of the wizard, select an application group that you want to use for recovery verification.

You can select an application group or skip this step. If the application group is not selected, you must link at least one backup job to the SureBackup job at the [Linked Jobs](surebackup_job_joblink_hv.md) step of the wizard. In this case, when the SureBackup job starts, Veeam Backup & Replication will only run machines from the linked job in the virtual lab and verify these machines.

To select an application group:

1. From the Application group list, select an application group. The list contains all application groups that are created on the backup server.
2. In the Application group info list, refer to the Source Status column to make sure that backups and replicas for machines in the application group are created.
3. To leave machines from the application group running after the SureBackup job finishes, select the Keep the application group running after the job completes check box. With this option enabled, the lab will not be powered off when the SureBackup job completes, and you will be able to perform application item-level restore ([U-AIR](https://www.veeam.com/veeam_backup_12_uair_wizard_user_guide_pg.pdf)) and manually test machines started in the virtual lab.

![Step 4. Select Application Group](images/surebackup_job_app_group.webp)


