---
title: "FSx Restore Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_fsx_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# FSx Restore Using Web UI


In case of a disaster, you can restore a FSx file system from a FSx backup or backup copy. Veeam Plug-in for AWS allows you to restore one or more file systems at a time, to the original location or to a new location. To learn how FSx restore works, see [FSx Restore](aws_restore_hiw_fsx.md).

|  |
| --- |
| Important |
| * Veeam Plug-in for AWS supports restoring FSx file systems only to the same AWS accounts to which the source file systems belong.  * Veeam Plug-in for AWS supports restoring only those FSx file system properties that are described in section [Protecting FSx File Systems](aws_overview_fsx.md#parameters).  * Veeam Plug-in for AWS supports restoring Amazon FSx for Windows File Server file systems. However, before you start a restore operation, it is recommended that you use the Amazon FSx Active Directory Validation tool to check the connection between the file systems that you plan to restore and the Microsoft Active Directories to which these file systems will be joined. To learn how to use the validation tool, see [AWS Documentation](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/aws-ad-integration-fsxW.html). * Veeam Plug-in for AWS does not support restoring Amazon FSx for Windows File Server file systems that use AWS Secrets Manager to store service account credentials when joined to a self-managed Microsoft Active Directory (AD). |

To restore a protected FSx file system, do the following:

1. [Launch the FSx Restore wizard](aws_restore_launch_fsx.md).
2. [Select a restore point](aws_restore_point_fsx.md).
3. [Specify account settings for restore](aws_restore_account_fsx.md).
4. [Choose a restore mode](aws_restore_mode_fsx.md).
5. [Enable encryption for the restored table](aws_restore_encryption_fsx.md).
6. [Configure file system settings](aws_restore_general_fsx.md).
7. [Configure network settings](aws_restore_capacity_network_efs.md).
8. [Specify a restore reason](aws_restore_reason_fsx.md).
9. [Finish working with the wizard](aws_restore_finish_fsx.md).

Page updated 2026-05-22

