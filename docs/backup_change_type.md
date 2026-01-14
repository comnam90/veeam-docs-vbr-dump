---
title: "Upgrading Backup Chain Formats"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_change_type.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Upgrading Backup Chain Formats

In this article

Veeam Backup & Replication supports the following ways to store backup files: per-machine backup with separate metadata files, per-machine backup with single metadata file and single-file backup. For more information, see [Backup Chain Formats](per_vm_backup_files.md).

Changing the Use per-machine backup files option for existing backup repositories or [moving backups](move_backup.md) to other repositories does not change the backup chain format. To change the format, follow the instructions in this section.

|  |
| --- |
| Note |
| Consider the following:   * Change the backup chain format only for backups created successfully. * Before changing the backup chain format, Veeam Backup & Replication disables the job to which the backups belong. After the change, the job stays disabled. You need to enable it manually. * You must disable the log backup jobs manually before changing the format. * You can stop an upgrade session only for the backups for which the session has not started. If the session has started, Veeam Backup & Replication continues the upgrade to avoid backup corruption. * [For backups stored on repositories with immutability enabled] You can upgrade backups from per-machine backup with single metadata file to per-machine backup with separate metadata files. Other upgrades are not possible. * You cannot upgrade the backup chain format for backups stored on repositories with rotated drives. |

Per-Machine Backup with Single Metadata File to Per-Machine with Separate Metadata Files

To change the backup chain format from per-machine with single metadata file to per-machine with separate metadata files, use the upgrade functionality:

1. Open the Home view.
2. In the inventory pane, select the Backups node.
3. In the working area, select the necessary jobs. Note that the selected jobs must be targeted to the same repository.
4. Right-click one of the selected jobs and click Upgrade backup chain format. Alternatively, click Upgrade Backup Chain Format on the ribbon.

Veeam Backup & Replication will generate new metadata files for the existing backups. After the upgrade, the job will continue the backup chain and create per-machine backups with separate metadata files.

Other Formats

To change the backup chain format, you must detach the existing backup chain from the job and then target the job to the required repository:

1. Detach backups from the job for whose backups you want to change the backup chain format. For more information, see [Detaching Backups from Jobs](detach_backup.md).
2. To create backup files of the required backup chain format, launch the job. The job will create active full backups.

|  |
| --- |
| Note |
| If the job has a backup to tape job configured as a [secondary target](vmware_backup_secondary_target.md), the backup to tape job will archive a full backup during its next scheduled run. |

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
