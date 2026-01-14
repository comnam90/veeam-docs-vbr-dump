---
title: "Creating vApp Replica Seeds"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_replica_create_seed.html"
last_updated: "7/18/2024"
product_version: "13.0.1.1071"
---

# Creating vApp Replica Seeds

In this article

To use seeding, you must have backups of replicated vApps in a backup repository in the disaster recovery (DR) site. These backups are known as replica seeds. For more information on seeding and when to use it, see [vApp Seeding and Mapping](vcd_seeding_mapping.md).

If you do not have replica seeds in the DR site, do the following:

1. Create a backup of vApps that you plan to replicate as described in section [Creating Backup Jobs](backup_job.md). As the target repository for this job, select a backup repository in the production site. Then run the job.

If you already have backups containing the necessary vApps, there is no need to configure and run a new backup job. For seeding, you can use any existing backups created by Veeam Backup & Replication. The backup must include VBK and VBM files. If you have a full backup and a chain of forward increments, you can use VIB files together with the VBK and VBM files. In this case, Veeam Backup & Replication will restore vApps from the seed to the latest available restore point.

1. Copy the backup from the backup repository in the production site to a backup repository in the DR site.

You can move the backup using a [file copy job](file_copy.md) or any other appropriate method, for example, copy the backup to a removable storage device, ship the device to the DR site and copy backups to the backup repository in the DR site.

If you do not have a backup repository in the DR site, you need to create the repository as described in section [Backup Repositories](backup_repository.md).

|  |
| --- |
| Important |
| You cannot copy backups to a scale-out backup repository in the DR site. |

1. After the backup is copied to the backup repository in the DR site, perform rescan of this backup repository as described in section [Rescanning Backup Repositories](rescanning_backup_repositories.md). Otherwise, Veeam Backup & Replication will not be able to detect the copied backup.

Page updated 7/18/2024

Page content applies to build 13.0.1.1071
