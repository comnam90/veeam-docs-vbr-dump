---
title: "Step 5. Select Backup Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_mode_linux.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Step 5. Select Backup Mode


At the Backup Mode step of the wizard, select the mode in which you want to create a backup.

1. In the Backup mode section, select the backup mode. You can select one of the following options:

* Entire computer — select this option if you want to create a backup of the entire computer image. When you restore data from such backup, you will be able to recover the entire computer image as well as data on specific computer volumes: files, directories, application data and so on. With this option selected, you will pass to the [Storage](agent_job_target_set_linux.md) step of the wizard.
* Volume level backup — select this option if you want to create a backup of specific computer volumes, for example, the system volume. When you restore data from such backup, you will be able to recover data located on these volumes only: files, directories, application data and so on. With this option selected, you will pass to the [Objects](agent_job_volumes_linux.md) step of the wizard.
* File level backup — select this option if you want to create a backup of individual directories on your computer. With this option selected, you will pass to the [Objects](agent_job_folders_linux.md) step of the wizard.

If necessary, you can edit the backup mode settings after you create the backup job.

1. [For file-level backup] If you want to perform backup in the snapshot-less mode, select the Backup directly from live file system check box. With this option selected, Veeam Agent for Linux will not create a snapshot of a backed-up volume during backup. This allows Veeam Agent to back up data residing in file systems that are not supported for snapshot-based backup with Veeam Agent for Linux. To learn more, see the [Snapshot-Less File-Level Backup](https://helpcenter.veeam.com/docs/agentforlinux/userguide/file_backup_snapshotless.html?ver=13) section in the Veeam Agent for Linux User Guide.

|  |
| --- |
| TIP |
| File-level backup is typically slower than volume-level backup. Depending on the performance capabilities of your computer and backup environment, the difference between file-level and volume-level backup job performance may increase significantly. If you plan to back up all folders with files on a specific volume or back up large amount of data, it is recommended that you configure volume-level backup instead of file-level backup. |

![Step 5. Select Backup Mode](images/agent_job_mode_linux.webp)


