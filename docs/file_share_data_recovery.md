---
title: "File Share Data Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_data_recovery.html"
last_updated: "7/21/2023"
product_version: "13.0.1.1071"
---

# File Share Data Recovery

In this article

You can restore data previously backed up with file backup jobs. You can restore the following data:

* SMB file share files and folders
* NFS file share files and folders
* Files and folders of a managed Microsoft Windows server
* Files and folders of a managed Linux server

Veeam Backup & Replication offers several recovery options for different recovery scenarios:

* [Instant file share recovery](instant_nas_recovery.md) allows you to publish a point-in-time file share state to instantly access all protected files.

* [Restore of the entire file share](file_share_recovery_restore_entire_file_share.md) allows you to recover all files and folders of the file share to one of the restore points.
* [Rollback to a point in time](file_share_recovery_roll_back_to_point_in_time.md) allows you to restore only changed files to one of the restore points.
* [Restore of files and folders](file_share_recovery_restore_files_folders.md) allows you to select files and folders to restore to one of the restore points.
* [Restore of files from an archive repository](restore_files_from_archive.md) allows you to select archived files to restore to one of the restore points.

Page updated 7/21/2023

Page content applies to build 13.0.1.1071
