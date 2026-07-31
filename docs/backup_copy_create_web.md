---
title: "Creating Backup Copy Jobs for VMs and Physical Machines Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_create_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Backup Copy Jobs for VMs and Physical Machines Using Web UI


To copy backups to a secondary location, you must configure a backup copy job. The backup copy job defines how, where and when to copy backups. One backup copy job can be used to process one or multiple machines. Machines included in the job are processed in parallel. If a machine included in the backup copy job has multiple disks, disks are processed sequentially, one after another.

Before you create a job, [check prerequisites](backup_copy_before_you_begin_web.md). Then use the Veeam Backup & Replication web console to configure the backup copy job.

1. [Launch New Backup Copy Job wizard](backup_copy_launch_web.md).
2. [Specify job name and copy mode](backup_copy_name_web.md).
3. [Select workloads to process](backup_copy_vms_web.md).
4. [Specify target repository and retention settings](backup_copy_target_web.md).
5. [Step 5. Specify Advanced Settings](backup_copy_settings_web.md).
6. [Define backup copy window](backup_copy_schedule_web.md).
7. [Finish working with wizard](backup_copy_finish_web.md).

Page updated 2026-07-27

