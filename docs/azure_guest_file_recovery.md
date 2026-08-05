---
title: "Performing Guest OS File Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_guest_file_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Guest OS File Restore


Veeam Backup & Replication allows you to use image-level backups to restore files and folders of various VM guest OS file systems from the Veeam Backup & Replication console. For more information, see [Guest OS File Restore](guest_file_recovery.md).

|  |
| --- |
| Important |
| * Guest OS file restore cannot be performed using backups that are stored in [Veeam Data Cloud storage vaults](azure_vdc_vaults.md). To perform this operation, use backups that are stored in standard backup repositories for which you have specified Microsoft Azure storage account credentials. To learn how to specify credentials for repositories, see sections [Creating New Repositories](azure_repository_console_storage_account.md) and [Connecting to Existing Appliances](azure_adding_appliance_repository.md). * Before you start the restore operation, check the limitations and prerequisites described in [Considerations and Limitations](vbr_flr_considerations_common.md). |

To restore guest OS files and folders, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository.
3. Expand the backup policy that protects an Azure VM whose files and folders you want to restore, select the necessary VM and click Restore Guest Files on the ribbon.

1. Complete the File Level Restore wizard as described in [Recovering Guest OS Files Using Console](performing_guest_restore.md).

|  |
| --- |
| Tips |
| * If the file system whose files and folders you want to restore is not included in the [list of supported systems](platform_support.md#guest-os-file-restore), you can restore them using the Instant Disk Recovery technology. For more information, see [Restore from Other File Systems](guest_restore_other.md). * You can also perform file-level recovery using the backup appliance Web UI. For more information, see [Performing File-Level Recovery](azure_performing_flr.md). |

[![Restore guest OS files](images/azure_restore_guest_os_files.webp)](images/azure_restore_guest_os_files.webp "Restore guest OS files")

Page updated 2026-07-01

