---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_before_you_begin_web.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a backup copy job using web console, check the following prerequisites:

* Backup infrastructure components that will take part in the backup copy process must be added to the backup infrastructure. This include target backup repository to which backups must be copied. For more information on adding components, see [Backup Infrastructure Components](components.md).
* You can not create a backup copy job to copy backup files between HPE StoreOnce backup repositories. You can only select HPE StoreOnce backup repository as a target.
* You can not create application-level backup copy job.
* If you plan to copy backups to an HPE StoreOnce repository, [check limitations and requirements](deduplicating_appliance_storeonce.md) for it.
* If you plan to copy Veeam Agents backups, see [Veeam Agent Backup](agent_backup_backup_copy.md) for limitations and requirements.
* If you plan to copy backups to an immutable repository, you must enable the GFS retention policy. For more information, see [Long-Term Retention Policy (GFS)](backup_copy_gfs.md).
* If you plan to migrate VMs between hosts in the cluster or SCVMM, you will not have to reconfigure jobs in Veeam Backup & Replication. Veeam Backup & Replication will automatically locate migrated VMs and continue processing them as usual. If you migrate VMs between standalone hosts that are not a part of one cluster or SCVMM server registered in Veeam Backup & Replication, you will have to reconfigure jobs to include the migrated VMs. After that, Veeam Backup & Replication will create full backups for these VMs. If you do not reconfigure the jobs, they will fail.
* If you delete the source backup job after creating the backup copy job, backup files will become orphaned. The orphaned backup files can not be processed by any job.
* Even if Use per-machine backup files option is disabled in a repository that you are planning to use as the target, backup copy job will always create per-machine backup files in the backup repository.

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
