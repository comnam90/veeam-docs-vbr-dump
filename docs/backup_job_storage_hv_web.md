---
title: "Step 5. Specify Backup Storage Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_storage_hv_web.html"
last_updated: "9/18/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Backup Storage Settings

In this article

At the Storage step of the wizard, select backup infrastructure components for the job — backup proxy and backup repository, and define backup storage settings:

1. Click Choose next to the Backup proxy field to select a backup proxy.

+ If you choose the On-host backup mode, the source Microsoft Hyper‑V host will perform the source host and backup proxy roles. In this mode, Veeam Data Mover runs directly on the source host, which helps streamline data retrieval operations but puts an additional load on the host.

If the job processes a VM whose disks are located on the CSV and the Microsoft CSV Software Shadow Copy Provider is used for snapshot creation, the Microsoft Hyper-V host owning the CSV will be used as the on-host backup proxy.

+ If you choose the Off-host backup mode, Veeam Data Mover will be started on a dedicated off-host backup proxy. In this mode, all backup processing operations are shifted to the off-host backup proxy from the source host.

By default, if the off-host backup mode is selected for the job but no off-host backup proxies are available when the job starts, Veeam Backup & Replication will automatically fail over to the on-host backup mode. To disable failover, clear the Failover to on-host backup mode if no suitable off-host proxies available check box. If you disable this option, you must check off-host backup proxies before the job starts. The job will not be able to start if off-host backup proxies are not available or are not configured correctly.

To perform off-host backup, Veeam Backup & Replication analyzes the current load on off-host backup proxies and proxy settings (such as the number of allowed tasks and connectivity to the source volumes) to select an appropriate off-host backup proxy for the job. You can also explicitly point out what off-host backup proxies the job must use. To do this, select the Use the following backup proxy servers only check box and choose one or several off-host backup proxies from the list. It is recommended that you select at least two off-host backup proxies to ensure that the backup job starts if one of the backup proxies fails or loses its connectivity to the source volumes.

1. From the Backup repository list, select a backup repository where the created backup files must be stored. When you select a backup repository, Veeam Backup & Replication automatically checks how much free space is available in the backup repository.

|  |
| --- |
| Note |
| Consider the following:   * If you change the repository after the job has already run, Veeam Backup & Replication suggests you move the existing backups to the new repository. If you want to move the backups, check the limitations and considerations in [Backup Move](backup_moving_hv.md). * If you select an object storage repository or a scale-out backup repository which performance tier consists of object storage repositories, Veeam Backup & Replication will not provide the amount of free space in this repository since its capacity is constantly expanding. |

1. In the Retention Policy field, specify retention policy settings for restore points.

To keep all restore points created during the last N days, specify the number of days. When the specified number is exceeded, the earliest restore point is removed from the backup chain or merged with the next closest restore point. For more information, see [Short-Term Retention Policy](retention_policy.md).

|  |
| --- |
| Note |
| If you enable the [GFS retention](gfs_retention_policy_hv.md), the short-term retention policy will not be able to delete and merge the GFS backup files. Thus, the backup chain will have more restore points than specified in the short-term retention policy. |

[![Click to zoom in](images/hv_backup_job_storage_web.webp)](images/hv_backup_job_storage_web.webp "Click to zoom in")

Page updated 9/18/2025

Page content applies to build 13.0.1.1071
