---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_limitations_hv.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and limitations common for creating backup jobs.

Backup Infrastructure

* Check requirements and limitations in the [VMs](platform_support.md#vms) section in [Supported Platforms, Applications and Workloads](platform_support.md).

* Backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and properly configured. These include Microsoft Hyper-V hosts on which VMs are located and a backup repository. If you want to perform backup in the off-host backup mode, the off-host backup proxy must also be added to the backup infrastructure and properly configured.
* The backup repository must have enough free space to store created backup files. To receive alerts about low space in the backup repository, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).
* If you plan to map a backup job to a backup file that already exists in the backup repository, you must perform the rescan operations for this backup repository. Otherwise, Veeam Backup & Replication will not be able to recognize backup files in the backup repository. For more information, see [Rescanning Backup Repositories](rescanning_backup_repositories.md).

* If you plan to use a deduplicating storage appliance as a target for backup jobs, [check the limitations and requirements](deduplicating_storage_appliances.md) for the repository.

* If Microsoft Hyper-V Server 2016 or later is added along with hosts of lower versions to the same cluster, Veeam Backup & Replication will not use new mechanisms (for example, online backup with checkpoints and RCT for change block tracking) for VMs in this cluster. The new mechanisms will be used only after you perform the following actions:

+ Upgrade all nodes in the cluster to Microsoft Hyper-V Server 2016 or later.
+ Upgrade the cluster functional level.
+ Upgrade VM configuration version to 8.x.

Backup Source

* Veeam Backup & Replication does not support protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* [For VMs with VHDX disks] If you plan to perform a live VHDX resizing operation (either shrink or expand), see [this Veeam KB article](https://www.veeam.com/kb2450).

Backup Job Configuration

* If you plan to configure a secondary destination for the backup job, you can create a backup copy job or backup to the tape job beforehand. The backup copy job or backup to tape job can have an empty source; that is, it cannot be linked to any backup job. For more information, see [Creating Backup Copy Jobs for VMs and Physical Machines](backup_copy_create.md) and [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md).

* If you plan to perform maintenance operations with backup files periodically, consider the following limitations: [Health Check for Backup Files](backup_health_check_hv.md#lim), [Retention Policy for Deleted VMs](retention_deleted_vms_hv.md#lim), and [Compact of Full Backup File](backup_compact_file_hv.md#lim).

* If you plan to use pre-job and post-job scripts, you must create scripts before you configure the backup job.

* If you plan to migrate VMs between hosts in the cluster or SCVMM, you will not have to reconfigure jobs in Veeam Backup & Replication. Veeam Backup & Replication will automatically locate migrated VMs and continue processing them as usual. If you migrate VMs between standalone hosts that are not a part of one cluster or SCVMM server registered in Veeam Backup & Replication, you will have to reconfigure jobs to include the migrated VMs. After that, Veeam Backup & Replication will create full backups for these VMs. If you do not reconfigure the jobs, they will fail.

Guest Processing

* If you plan to enable guest processing for the job, check [Guest Processing Requirements and Limitations](guest_processing_hv.md#guest_req_limits).
* Dynamic disks and FAT/FAT32 disks can be backed up only with disabled application-aware processing.

* If you plan to use VM Guest OS File Indexing, you need enough disk space to store indexing data. For more information, see [Requirements and Limitations for VM Guest OS File Indexing](indexing_hv.md).

* If you plan to use pre-freeze and post-thaw scripts, you must create scripts before you configure the backup job.

Scripts

The following applies to [pre-job and post-job scripts:](backup_job_advanced_scripts_vm.md#script_settings) created on Linux-based backup server:

* Bash scripts must use Linux-style line endings (LF).
* Only the .SH and .PS1 file extensions are supported.
* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

Before you configure script settings, you must create and upload scripts to the Linux backup server:

1. In the Veeam Backup & Replication console, navigate to the Files node.
2. Copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.

When scripts are uploaded correctly, permissions are set automatically. You do not have to edit them.

Page updated 12/3/2025

Page content applies to build 13.0.1.1071
