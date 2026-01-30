---
title: "Creating Backup Jobs for Cloud Director VMs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_perform_backup.html"
last_updated: "6/10/2025"
product_version: "13.0.1.1071"
---

# Creating Backup Jobs for Cloud Director VMs


The process of creating a VMware Cloud Director backup job is practically the same as for a [VMware vSphere backup job](backup_job.md). The VMware Cloud Director backup job aggregates main settings for the backup task and defines when, what, how and where to back up VMware Cloud Director VMs.

Considerations and Limitations

Consider the following:

* Veeam Backup & Replication supports the VMware Cloud Director multisite deployment. To back up vApps and VMs, you must [add all Cloud Director servers](adding_vcloud_director.md) to Veeam Backup & Replication separately.
* We recommend adding VMs of one vApp into one Cloud Director backup job. Splitting VMs into different jobs can cause additional load on the system during backup and restore. This can happen because Veeam Backup & Replication must handle multiple vApp metadata copies.
* The limitation of concurrent tasks applies in the same way as for backup jobs. Veeam Backup & Replication ignores vApps. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md).
* If you run a VMware Cloud Director backup job for the vApp, the job is considered to finish with the Success status and the complete restore point for the vApp is created only if all VMs in the vApp are successfully backed up. If any VM in the job fails, the restore point for the vApp will be in the incomplete status, and you will not be able to restore the whole vApp from such a restore point. However, you will be able to perform restore to the original vApp for VMs that were partially or successfully backed up and whose data is available in the incomplete restore point. Veeam Backup & Replication will restore all data that is available for such VMs in the backup.

Creating Cloud Director Backup Job

To create a VMware Cloud Director backup job, do the following:

1. Open the Home view.
2. In the inventory pane, right-click Jobs and select Backup > Virtual Machine > VMware Cloud Director.
3. Complete the wizard as described in [Creating Backup Jobs (VMware vSphere)](backup_job.md).

At the Virtual Machines step of the wizard, select which Cloud Director instances you want to protect.

|  |
| --- |
| Note |
| Veeam Backup & Replication shows restore points of a VM that is no longer processed, for example, excluded from the job or deleted, as long as incremental backup files with this VM exist in the active backup chain. After Veeam Backup & Replication deletes the files according to the [retention policy](retention_policy.md), it also hides the VM restore points from the list of restore points created by this backup job. Although the full backup file with the VM may still exist, restore from this file into the VMware Cloud Director is not supported. |

[![Create job for VMware Cloud Director](images/vcloud_backup.webp)](images/vcloud_backup.webp "Create job for VMware Cloud Director")


