---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_limitations.html"
last_updated: "2/6/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section lists considerations and limitations common for creating backup jobs.

Backup Infrastructure

* Backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and properly configured. These include ESXi hosts on which VMs are registered, backup proxy and backup repository.
* The backup repository must have enough free space to store created backup files. To receive alerts about low space in the backup repository, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).
* If you plan to map a backup job to a backup file that already exists in the backup repository, you must perform the rescan operations for this backup repository. Otherwise, Veeam Backup & Replication will not be able to recognize backup files in the backup repository. For more information, see [Rescanning Backup Repositories](rescanning_backup_repositories.md).

* If you plan to use a deduplicating storage appliance as a target for backup jobs, [check the limitations and requirements](deduplicating_storage_appliances.md) for the repository.

* If you plan to use the Backup from Storage Snapshots technology, check [Requirements and Limitations for Backup Proxies (Storage Systems)](storage_configure_proxy.md) section. Also, check other requirements in the guide.
* If you assign the role of a backup proxy to a VM, you should not add this VM to the list of processed VMs in a job that uses this backup proxy. Such configuration may result in degraded job performance. Veeam Backup & Replication will assign this backup proxy to process other VMs in the job first, and processing of this VM itself will be put on hold. Veeam Backup & Replication will report the following message in the job statistics: VM is a backup proxy, waiting for it to stop processing tasks. The job will start processing this VM only after the backup proxy deployed on the VM finishes its tasks.

Backup Source

Veeam Backup & Replication does not support protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).

Backup Job Configuration

* If you plan to configure a secondary destination for the backup job, you can create a backup copy job or backup to the tape job beforehand. While creating the backup copy or backup to tape job, you can leave the source empty and link the source to the job later. For more information, see [Creating Backup Copy Jobs for VMs and Physical Machines](backup_copy_create.md) and [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md).

* If you plan to perform maintenance operations with backup files periodically, consider the following limitations: [Health Check for Backup Files](backup_health_check.md#lim), [Retention Policy for Deleted Items](retention_deleted_vms.md#lim) and [Compact of Full Backup File](backup_compact_file.md#lim).

* If you plan to use pre-job and post-job scripts, you must create scripts before configuring the backup job.

* If you use tags to categorize virtual infrastructure objects, check the limitations for VM tags. For more information, see [VM Tags](vm_tags.md).
* If a job cannot be completed within the 21 days period, it will be stopped with the Failed status.
* If you plan to protect VMware Cloud Director objects, consider using the dedicated backup job. For more information, see [Backup for VMware Cloud Director](vcloud_director_backup.md).
* You cannot exclude VMs in the web UI. This option is available only in the Veeam Backup & Replication console.

Guest Processing

* If you plan to enable guest processing for the job, check [Guest Processing Requirements and Limitations](guest_processing.md#guest_req_limits).
* If you plan to use VM Guest OS File Indexing, you need enough disk space to store indexing data. For more information, see [Requirements and Limitations for VM Guest OS File Indexing](indexing.md#file_indexing_req_limits).

* If you plan to use pre-freeze and post-thaw scripts, you must create scripts before configuring the backup job.

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


