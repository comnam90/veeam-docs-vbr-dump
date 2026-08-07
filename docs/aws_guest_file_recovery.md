---
title: "Performing Guest OS File Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_guest_file_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Guest OS File Restore


Veeam Backup & Replication allows you to use image-level backups to restore files and folders of various EC2 guest OS file systems from the Veeam Backup & Replication console. For more information, see section [Guest OS File Restore](guest_file_recovery.md).

|  |
| --- |
| Important |
| * Guest OS File Restore can be performed only using backup files stored in standard backup repositories for which you have specified access keys of an IAM user whose permissions are used to access the repository. To learn how to specify credentials for repositories, see sections [Creating New Repositories](aws_add_s3_account.md) and [Connecting to Existing Appliances](aws_connect_appliance_repo.md). * Before you start the restore operation, check the limitations and prerequisites described in section [Considerations and Limitations](vbr_flr_considerations_common.md). |

To restore guest OS files and folders, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository.
3. Expand the backup policy that protects an EC2 instance whose files and folders you want to restore, select the necessary instance and click Restore Guest Files on the ribbon.
4. Complete the File Level Restore wizard as described in section [Recovering Guest OS Files Using Console](performing_guest_restore.md).

|  |
| --- |
| Tips |
| * If the file system whose files and folders you want to restore is not included in the [list of supported systems](platform_support.md), you can restore them using the Instant Disk Recovery technology. For more information, see [Restore from Other File Systems](guest_restore_other.md).  * You can also perform file-level recovery using the backup appliance Web UI. To learn how to recover files and folders to a local machine using file-level recovery browser, see [Performing File-Level Recovery](aws_restore_item_perform.md). |

[![Restore guest OS files](images/aws_guest_os_win.webp)](images/aws_guest_os_win.webp "Restore guest OS files")

Page updated 2026-07-17

