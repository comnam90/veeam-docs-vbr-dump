---
title: "Creating Storage Copy Jobs Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_copy_create.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Storage Copy Jobs Using Console


To copy backups between HPE StoreOnce and Dell Data Domain storage systems, you must configure a storage copy job.

Unlike other backup copy jobs, the storage copy job for HPE StoreOnce and Dell Data Domain mirrors data from the source repository. This storage copy job copies backup files as they are stored in the source repository, without any transformation. To copy backup files, Veeam Backup & Replication uses the HPE StoreOnce Catalyst Copy and the Data Domain Boost (DD Boost) technologies.

The storage copy job copies only backup files created by backup jobs and other backup copy jobs. The backup files must be of the following types:

* Backup files of VMware vSphere and Microsoft Hyper-V VMs created by Veeam Backup & Replication. Log backup files are not copied.
* Physical machine backup files created by [Veeam Agent backup jobs managed by the backup server](agents_job.md).
* Backup files of Nutanix AHV created by Veeam Plug-In for Nutanix AHV.
* Backup files of oVirt created by Veeam Plug-In for oVirt KVM\*.
* Backup files of Proxmox VE created by Veeam Plug-In for Proxmox VE.
* Backup files of Scale Computing HyperCore created by Veeam Plug-in for Scale Computing HyperCore.
* Backup files of XenServer created by Veeam Plug-in for Xen.
* Backup files of HPE Morpheus VM Essentials created by Veeam Plug-In for HPE Morpheus VM Essentials.
* Backups copied to HPE StoreOnce or Dell Data Domain repository by other backup copy jobs (regular backup copy jobs and storage copy jobs).

\* - Available on Microsoft Windows-based backup server.

|  |
| --- |
| Important |
| Consider the following limitations:   * The backup jobs must be configured on the same backup server where you configure the storage copy job. Backups created by jobs configured on other backup servers are not copied. * You can not copy orphaned or imported backups using the storage copy job. * To copy backups created by other backup copy jobs (regular backup copy jobs), you must enable the GFS retention for these backup copy jobs. For more information on how to enable the GFS retention, see [Specify Target Repository and Retention Settings](backup_copy_target.md). |

When the storage copy job runs for the first time, it copies all existing backup files. Then the storage copy job starts each time a new backup file appears in the source repository. In case of a removed backup file, the storage copy job waits 21 days since the backup file was copied to the target repository and then removes it. If 21 days have already passed at the moment of removal, the storage copy job removes the backup file immediately. You can change this day limit in the storage copy job settings. For more information, see [Maintenance Settings](storage_copy_maintenance_settings.md).

Before creating a job, [check prerequisites and limitations](storage_copy_byb.md). Then use the New Storage Copy Job wizard to configure the storage copy job.

1. [Launch the New Storage Copy Job Wizard](storage_copy_launch.md).
2. [Specify a Job Name and Description](storage_copy_name.md).
3. [Select Source and Target Repositories](storage_copy_source_and_target.md).
4. [Specify Advanced Settings](storage_copy_settings.md).
5. [Define a Backup Copy Window](storage_copy_schedule.md).
6. [Finish Working with the Wizard](storage_copy_summary.md).

Related Topics

[HPE StoreOnce](deduplicating_appliance_storeonce.md)

[Dell Data Domain](dell_dd.md)

Page updated 2026-07-30

