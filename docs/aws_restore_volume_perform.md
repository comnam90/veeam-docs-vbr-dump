---
title: "Performing Volume Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_volume_perform.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Volume Restore


In case a disaster strikes, you can restore corrupted EBS volumes of an EC2 instance from a cloud-native snapshot, snapshot replica or image-level backup. Veeam Plug-in for AWS allows you to restore EBS volumes to the original location or to a new location.

|  |
| --- |
| Notes |
| * Backup appliances do not attach restored EBS volumes to any EC2 instances — the volumes are placed to the specified location as standalone EBS volumes. * To restore an EC2 instance from a backup that is stored in an archive backup repository, you must retrieve the archived data first. You can either retrieve the archived data manually before you begin the restore operation, or launch the data retrieval process right from the Volume Restore wizard. To learn how to retrieve data manually, see [Retrieving EC2 Data From Archive](aws_data_retrieval.md). |

To restore EBS volumes of a protected EC2 instance, do the following:

1. [Launch the Volume Restore wizard](aws_restore_entire_launch.md).
2. [Select a restore point](aws_restore_volume_settings.md).
3. [Specify data retrieval settings for archived backups](aws_restore_volume_data_retrieval.md).
4. [Specify account settings for restore](aws_restore_volume_account.md).
5. [Choose a restore mode](aws_restore_volume_mode.md).
6. [Enable encryption for EBS volumes](aws_restore_volume_encryption.md).
7. [Specify the restored EBS volume name](aws_restore_volume_name.md).
8. [Specify a restore reason](aws_restore_volume_reason.md).
9. [Finish working with the wizard](aws_restore_volume_finish.md).

Page updated 2026-05-21

