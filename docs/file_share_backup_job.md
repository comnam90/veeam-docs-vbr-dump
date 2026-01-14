---
title: "Creating File Backup Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_job.html"
last_updated: "11/14/2023"
product_version: "13.0.1.1071"
---

# Creating File Backup Jobs

In this article

To protect files and folders on the file share, configure a file backup job. The backup job defines how, where and when to back up data from the file share. One job can be used to protect one or more file shares. Jobs can be started manually or scheduled to run automatically at a specific time.

File backup jobs are used to protect the following sources of unstructured data:

* [File servers (Windows and Linux)](adding_managed_server_file_share.md)
* [File shares (NFS and SMB (CIFS)](adding_file_share.md)
* [Enterprise storage systems added as NAS filers](adding_nas_filer.md)

Before you create a file backup job, check [prerequisites](file_share_backup_job_before_you_begin.md).

To create a file backup job, use the New File Backup Job wizard:

1. [Launch the New File Share Backup wizard](file_share_backup_job_launch_wizard.md).
2. [Specify the job name and description](file_share_backup_job_name.md).
3. [Select files and folders to back up](file_share_backup_job_files_and_folders.md).
4. [Specify backup repository settings](file_share_backup_job_storage.md).
5. [Specify advanced backup settings](file_share_backup_job_advanced_settings.md).
6. [Specify archive repository settings](file_share_backup_job_archive_repo.md).
7. [Specify the secondary target repository](file_share_backup_job_secondary_target.md).
8. [Define the job schedule](file_share_backup_job_schedule.md).
9. [Finish working with the wizard](file_share_backup_job_summary.md).

Page updated 11/14/2023

Page content applies to build 13.0.1.1071
