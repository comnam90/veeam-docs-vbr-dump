---
title: "Restoring Entire File Share"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_recovery_restore_entire_file_share.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Entire File Share


You can restore the entire file share from the backup to a specific restore point. That can be helpful, for example, if your file share device gets out of order and you need to restore the entire file share to the original or other location.

|  |
| --- |
| Note |
| If the Archive recent file versions option is selected (the copy mode is enabled) at the [Archive Repository](file_share_backup_job_archive_repo.md) step of the file backup job wizard, you may restore an entire file share from the archive repository. You can do that only for restore points that are stored in the archive repository and have the Copied label in backup properties.  If this option is not selected (the copy mode is disabled), the restore of the entire file share or even whole folders from the archive repository is not supported. |

You can restore entire file share in one of the following ways:

* [Restore entire file share using console](restoring_entire_file_share_using_console.md).
* [Restore entire file share using web UI](restoring_entire_file_share_using_web_ui.md).

Page updated 2026-07-24

