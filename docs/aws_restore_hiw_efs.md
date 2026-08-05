---
title: "EFS Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_efs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# EFS Restore


Veeam Plug-in for AWS offers the following restore options:

* File system restore — restores an entire Amazon EFS file system from an EFS backup or a backup copy. You can restore one or more Amazon EFS file systems at a time, to the original location or to a new location.
* File-level recovery — recovers individual files and folders stored in a file system from an EFS backup or backup copy. You can restore files and folders to the original file system or to another file system.

You can restore EFS file system data to the most recent state or to any available restore point.

|  |
| --- |
| Important |
| You can restore an EFS file system only to the same AWS account to which the source file system belongs. |

How File System Restore Works

To restore an EFS file system from a backup, a backup appliance performs the following steps using native [AWS capabilities](https://docs.aws.amazon.com/efs/latest/ug/awsbackup.html#restoring-backup-efs):

1. Creates a file system in the specified location.
2. Modifies the configuration setting values of the created EFS file system.
3. Creates a recovery EFS directory in the root directory of the selected file system and restores backed-up files and folders to the created directory.

To learn how to restore an entire Amazon EFS file system from an EFS backup or a backup copy, see [EFS Restore](aws_efs_restore.md).

How EFS File-Level Recovery Works

To recover files and folders of a backed-up file system using specific file paths, the backup appliance sends an API request to AWS to restore the specified files to the selected file system.

To recover files and folders of a backed-up file system using specific file paths, the backup appliance performs the following steps:

1. On the backup appliance, restores the EFS index associated with the specified restore point.
2. Launches the file-level recovery browser.

The file-level recovery browser displays the file system tree of the backed-up EFS file system. In the browser, you select the necessary files and folders to restore.

1. Creates a new EFS directory aws-backup-restore\_<datetime> in the root directory of the selected file system and restores the specified backed-up files and folders to the created directory.

To learn how to restore individual files and folders stored in a file system from an EFS backup or backup copy, see [EFS Restore](aws_efs_restore.md).

Page updated 2026-05-22

