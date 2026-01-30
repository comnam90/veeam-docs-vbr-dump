---
title: "Restoring Entire Bucket or Container"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_data_recovery_restore_entire_bucket.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Restoring Entire Bucket or Container


You can restore an entire object storage bucket or container from the backup to a specific restore point. That can be helpful, for example, if your object storage data gets corrupted or unavailable and you need to restore the entire bucket or container to the original or other location.

|  |
| --- |
| Note |
| If the Archive recent object versions option is selected (the copy mode is enabled) at the [Archive Repository](os_backup_job_archive_repository.md) step of the object storage backup job wizard, you may restore an entire bucket or container from the archive repository. You can do that only for restore points that are stored in the archive repository and have the Copied label in backup properties. If this option is not selected (the copy mode is disabled), the restore of the entire bucket or container from the archive repository is not supported. |

Before you restore a bucket or container, [check prerequisites](restore_entire_bucket_byb.md). Then use the Bucket Restore wizard to restore the bucket or container.

1. [Launch the Bucket Restore wizard](restore_entire_bucket_launch.md).
2. [Select buckets or continers to restore](restore_entire_bucket_buckets.md).
3. [Specify a destination for the bucket or container restore](restore_entire_bucket_destination.md).
4. [Create a new bucket or container](restore_entire_bucket_new_bucket.md).
5. [Specify restore options](restore_entire_bucket_restore_options.md).
6. [Finish working with the wizard](restore_entire_bucket_summary.md).


