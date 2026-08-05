---
title: "Performing EC2 Instance Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_perform.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing EC2 Instance Restore


In case of a disaster, you can restore an entire EC2 instance from a cloud-native snapshot, snapshot replica or image-level backup. Veeam Plug-in for AWS allows you to restore one or more EC2 instances at a time, to the original location or to a new location.

|  |
| --- |
| Important |
| Before you start the restore operation, check the limitations and prerequisites described in section [Before You Begin](aws_restore_entire_before_you_begin.md). |

To restore a protected EC2 instance, do the following:

1. [Launch the Instance Restore wizard](aws_restore_entire_launch.md).
2. [Select a restore point](aws_restore_entire_settings.md).
3. [Specify data retrieval settings for archived backups](aws_restore_entire_data_retrieval.md).
4. [Specify account settings for restore](aws_restore_entire_account.md).
5. [Choose a restore mode](aws_restore_entire_mode.md).
6. [Enable encryption for EBS volumes](aws_restore_entire_encryption.md).
7. [Configure EC2 instance settings](aws_restore_entire_type.md).
8. [Configure network settings](aws_restore_entire_network.md).
9. [Specify a restore reason](aws_restore_entire_reason.md).
10. [Finish working with the wizard](aws_restore_entire_finish.md).

Page updated 2026-05-21

