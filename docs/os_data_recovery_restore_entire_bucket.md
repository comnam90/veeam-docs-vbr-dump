---
title: "Restoring Entire Bucket or Container"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_data_recovery_restore_entire_bucket.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Entire Bucket or Container


You can restore an entire object storage bucket or container from the backup to a specific restore point. That can be helpful, for example, if your object storage data gets corrupted or unavailable and you need to restore the entire bucket or container to the original or other location.

|  |
| --- |
| Note |
| If the Archive recent object versions option is selected (the copy mode is enabled) at the [Archive Repository](os_backup_job_archive_repository.md) step of the object storage backup job wizard, you may restore an entire bucket or container from the archive repository. You can do that only for restore points that are stored in the archive repository and have the Copied label in backup properties. If this option is not selected (the copy mode is disabled), the restore of the entire bucket or container from the archive repository is not supported. |

You can restore an entire object storage bucket in one of the following ways:

* [Restore entire bucket or container using console](os_data_recovery_restore_entire_bucket_console.md).
* [Restore entire bucket or container using web UI](os_data_recovery_restore_entire_bucket_webd.md).

Page updated 2026-07-25

