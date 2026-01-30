---
title: "Step 3. Select Workloads to Process"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_vms.html"
last_updated: "8/31/2025"
product_version: "13.0.1.1071"
---

# Step 3. Select Workloads to Process


At the Objects step of the wizard, select workloads whose restore points you want to copy to the target backup repository:

1. Click Add.
2. Select a type of a source from which you want to copy restore points:

* From jobs. You will see existing backup jobs. Veeam Backup & Replication will copy restore points created by the selected jobs.

You can use another backup copy job as a source to process VMware, Cloud Director, and Hyper-V workloads, including workloads located on backup repositories with rotated drives.

[For the periodic copy mode] If multiple jobs process one workload, Veeam Backup & Replication copies only restore points created by the first job in the Objects to process list.

* From repositories. You will see all backup repositories in the backup infrastructure. Veeam Backup & Replication will copy restore points stored on the selected backup repositories.

If you select repositories as sources, and target new jobs to the repositories in future, Veeam Backup & Replication will update backup copy job settings automatically to include these jobs to be copied.

* From backups. You will browse for workloads in existing backups. Veeam Backup & Replication will search for restore points of the selected workloads in all backups of backup jobs created on the external repositories and will copy the most recent restore points. You can limit the search scope by selecting only specific backup policies for the backup copy job.

This source is only available for backup copy jobs that process backups of Amazon EC2 instances, Microsoft Azure and Google Cloud.

|  |
| --- |
| Note |
| You can use From backups source only if you have an external repository added to the backup infrastructure and have at least one backup file stored in it. |

1. In the Select window, select the necessary sources or workloads.
2. Click Ok.
3. [For the immediate copy mode] If you have configured processing of transaction log backups in the source backup jobs, and want to copy these log backups to the target repository, select the Include database transaction log backups check box.

As an alternative, you can create a backup copy job with an empty source — that is, do not add any workloads at this step of the wizard. In this case, you need to configure a secondary destination for the source backup job and link it to the created backup copy job. For more information, see [Linking Backup Jobs to Backup Copy Jobs](linking_backup_to_copy.md).

Limitations for Workload Selection

If you use tags to categorize virtual infrastructure objects, check limitations for VM tags. For more information, see [VM Tags](vm_tags.md).

![Step 3. Select Workloads to Process](images/backup_copy_workloads_immediate.webp)

Related Topics

[Restore Point Selection](backup_copy_select_point.md)


