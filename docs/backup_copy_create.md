---
title: "Creating Backup Copy Jobs for VMs and Physical Machines Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_create.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Backup Copy Jobs for VMs and Physical Machines Using Console


To copy backups to a secondary location, you must configure a backup copy job. The backup copy job defines how, where and when to copy backups. One backup copy job can be used to process one or multiple machines. Machines included in the job are processed in parallel. If a machine included in the backup copy job has multiple disks, disks are processed sequentially, one after another.

|  |
| --- |
| Note |
| If you want to copy backups between HPE StoreOnce repositories, follow the instructions listed in section [Creating Backup Copy Jobs for HPE StoreOnce Repositories](storage_copy_create.md).  If you want to copy file share backups, follow the instructions listed in section [Creating File Backup Jobs](file_share_backup_job.md). |

Before you create a job, [check prerequisites](backup_copy_before_you_begin.md). Then use the New Backup Copy Job wizard to configure the backup copy job.

1. [Launch the New Backup Copy Job wizard](backup_copy_launch.md).
2. [Specify a job name and copy mode](backup_copy_name.md).
3. [Select workloads to process](backup_copy_vms.md).
4. [Exclude objects from the backup copy job](backup_copy_exclude.md).
5. [Specify a target repository and retention settings](backup_copy_target.md).
6. [Map a backup file](backup_copy_mapping_file_job.md).
7. [Specify advanced settings](backup_copy_settings.md).
8. [Specify data path settings](backup_copy_wan.md).
9. [Define a backup copy window](backup_copy_schedule.md).
10. [Finish working with the wizard](backup_copy_finish.md).

Page updated 2026-07-30

