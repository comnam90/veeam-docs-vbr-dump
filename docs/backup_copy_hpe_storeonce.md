---
title: "Creating Backup Copy Jobs for HPE StoreOnce Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_hpe_storeonce.html"
last_updated: "11/17/2025"
product_version: "13.0.1.1071"
---

# Creating Backup Copy Jobs for HPE StoreOnce Repositories

In this article

To copy backup files between HPE StoreOnce backup repositories, you must configure a backup copy job for HPE StoreOnce repositories.

Unlike other backup copy jobs, the backup copy job for HPE StoreOnce mirrors data from the source repository. This backup copy job copies backup files as they are stored in the source repository, without any transformation. To copy the backup files, Veeam Backup & Replication uses the HPE StoreOnce Catalyst Copy technology.

The backup copy job copies only backup files created by backup jobs and other backup copy jobs. The backup files must be of the following types:

* Backup files of VMware vSphere and Microsoft Hyper-V VMs created by Veeam Backup & Replication. Log backup files are not copied.
* Physical machine backup files created by [Veeam Agent backup jobs managed by the backup server](agents_job.md).
* Backup files of Nutanix AHV VMs created by Veeam Plug-In for Nutanix AHV.
* Backup files of oVirt VMs created by Veeam Backup for OLVM and RHV\*.
* Backups copied to an HPE StoreOnce repository by other backup copy jobs (regular backup copy jobs and backup copy jobs for HPE StoreOnce repositories).

\* - Available on Microsoft Windows-based backup server.

|  |
| --- |
| Important |
| Consider the following limitations:   * The backup copy job copies only backup files created by backup jobs. The backup jobs must be configured on the same backup server where you configure the backup copy job for HPE StoreOnce repositories. Backups created by jobs configured on other backup servers are not copied. * The backup copy jobs for HPE StoreOnce repositories do not copy imported backups. * To copy backups created by other backup copy jobs (regular backup copy jobs), you must enable the GFS retention for these backup copy jobs. For more information on how to enable the GFS retention, see [Specify Target Repository and Retention Settings](backup_copy_target.md). |

When the backup copy job for HPE StoreOnce runs for the first time, it copies all existing backup files. Then the backup copy job starts each time a new backup file appears in the source repository. In case of a removed backup file, the backup copy job waits 21 days since the backup file creation and after removes the backup file from the target repository. If 21 days have already passed at the moment of removal, the backup copy job removes the backup file immediately. You can change this day limit in the backup copy job settings. For more information, see [Maintenance Settings](bc_hpe_storeonce_maintenance_settings.md).

Before creating a job, [check prerequisites and limitations](backup_copy_hpe_storeonce_byb.md). Then use the New Backup Copy Job wizard to configure the backup copy job.

1. [Launch the New Backup Copy Job Wizard](backup_copy_hpe_storeonce_launch.md).
2. [Specify a Job Name and Description](backup_copy_hpe_storeonce_name.md).
3. [Select Source and Target Repositories](backup_copy_hpe_storeonce_source_and_target.md).
4. [Specify Advanced Settings](backup_copy_hpe_storeonce_settings.md).
5. [Define a Backup Copy Window](backup_copy_hpe_storeonce_schedule.md).
6. [Finish Working with the Wizard](backup_copy_hpe_storeonce_summary.md).

Related Topics

[HPE StoreOnce](deduplicating_appliance_storeonce.md)

Page updated 11/17/2025

Page content applies to build 13.0.1.1071
