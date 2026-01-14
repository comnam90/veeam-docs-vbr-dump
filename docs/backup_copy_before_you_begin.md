---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_before_you_begin.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a backup copy job, check the following prerequisites:

* Backup infrastructure components that will take part in the backup copy process must be added to the backup infrastructure. This include target backup repository to which backups must be copied. For more information on adding components, see [Backup Infrastructure Components](components.md).
* If you plan to use pre-job and post-job scripts, you must create scripts before you configure the backup copy job.

* [For Linux-based backup server] The following applies to pre-job and post-job scripts:

* Bash scripts must use Linux-style line ednings (LF).
* Only the .SH and .PS1 file extensions are supported.

* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

To upload scripts to the Linux backup server, in the Veeam Backup & Replication console, navigate to the Files node. Then, copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.

* If you plan to copy backups to an HPE StoreOnce repository, [check limitations and requirements](deduplicating_appliance_storeonce.md) for it.
* If you plan to copy Veeam Agents backups, see [Veeam Agent Backup](agent_backup_backup_copy.md) for limitations and requirements.
* If you plan to copy backups to an immutable repository, you must enable the GFS retention policy. For more information, see [Long-Term Retention Policy (GFS)](backup_copy_gfs.md).
* If you plan to use WAN accelerators, check that you use the Enterprise Plus edition of Veeam Backup & Replication and that target and source WAN accelerators are added to the backup infrastructure. For more information, see [Adding WAN Accelerators](wan_add.md).
* If you plan to migrate VMs between hosts in the cluster or SCVMM, you will not have to reconfigure jobs in Veeam Backup & Replication. Veeam Backup & Replication will automatically locate migrated VMs and continue processing them as usual. If you migrate VMs between standalone hosts that are not a part of one cluster or SCVMM server registered in Veeam Backup & Replication, you will have to reconfigure jobs to include the migrated VMs. After that, Veeam Backup & Replication will create full backups for these VMs. If you do not reconfigure the jobs, they will fail.
* If you delete the source backup job after creating the backup copy job, backup files will become orphaned. The orphaned backup files are displayed under the Backups > Disk (Orphaned) node. If the orphaned backup files were also stored in [capacity tier](capacity_tier.md) or [archive tier](archive_tier.md), they will also be displayed under the Backups > Object Storage (Orphaned) or Backups > Archive (Orphaned) nodes. The orphaned backup files can not be processed by any job.
* Even if Use per-machine backup files option is disabled in a repository that you are planning to use as the target, backup copy job will always create per-machine backup files in the backup repository.

Page updated 10/21/2025

Page content applies to build 13.0.1.1071
