---
title: "Creating Replica Seeds for CDP"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_creating_replica_seed.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Replica Seeds for CDP


To use replica seeding in a CDP policy, you must have backups of replicated workloads in a backup repository in the disaster recovery (DR) site. These backups are known as replica seeds. For more information on seeding and when to use it, see [Replica Seeding](uni_cdp_seeding.md).

If you do not have replica seeds in the DR site, do the following:

1. Use Veeam Agent for Linux or Veeam Agent for Microsoft Windows to create a backup of workloads that you plan to replicate. For more information, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md). As the target repository for this job, select a backup repository in the production site. Then run the job or policy.

If you already have backups containing the necessary workloads, there is no need to configure and run a new backup job. For seeding, you can use any existing backups created by Veeam Agent for Linux or Veeam Agent for Microsoft Windows. The backup must include VBK and VBM files. If you have a full backup and a chain of forward increments, you can use VIB files together with the VBK and VBM files. In this case, Veeam Backup & Replication will restore workloads from the seed to the latest available restore point.

1. Copy the backup from the backup repository in the production site to a backup repository in the DR site.

You can move the backup using a [file copy job](file_copy.md) or any other appropriate method, for example, copy the backup to a removable storage device, ship the device to the DR site and copy backups to the backup repository in the DR site.

If you do not have a backup repository in the DR site, you need to create the repository as described in section [Backup Repositories](backup_repository.md).

|  |
| --- |
| Important |
| You cannot copy backups to a scale-out backup repository in the DR site. |

1. After the backup is copied to the backup repository in the DR site, perform rescan of this backup repository as described in section [Rescanning Backup Repositories](rescanning_backup_repositories.md). Otherwise, Veeam Backup & Replication will not be able to detect the copied backup.

Page updated 2026-05-20

