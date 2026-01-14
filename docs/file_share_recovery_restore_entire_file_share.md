---
title: "Restoring Entire File Share"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_recovery_restore_entire_file_share.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# Restoring Entire File Share

In this article

You can restore the entire file share from the backup to a specific restore point. That can be helpful, for example, if your file share device gets out of order and you need to restore the entire file share to the original or other location.

|  |
| --- |
| Note |
| If the Archive recent file versions option is selected (the copy mode is enabled) at the [Archive Repository](file_share_backup_job_archive_repo.md) step of the file backup job wizard, you may restore an entire file share from the archive repository. You can do that only for restore points that are stored in the archive repository and have the Copied label in backup properties.  If this option is not selected (the copy mode is disabled), the restore of the entire file share or even whole folders from the archive repository is not supported. |

Before you restore an entire file share, [check prerequisites](restore_entire_file_share_before_you_begin.md). Then use the File Restore wizard to restore files and folders of the file share.

1. [Launch the File Restore wizard](restore_entire_file_share_launch_wizard.md).
2. [Select an object to restore](restore_entire_file_share_backup.md).
3. [Specify a destination for the data restore](restore_entire_file_share_destination.md).
4. [Specify restore options](restore_entire_file_share_restore_options.md).
5. [Finish working with the wizard](restore_entire_file_share_summary.md).

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
