---
title: "Redshift Serverless Restore Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_redshift_serverless_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Serverless Restore Using Web UI


In case of a disaster, you can restore a Redshift Serverless namespace from a cloud-native backup. Veeam Plug-in for AWS allows you to restore only one Redshift Serverless namespace at a time to the original, any existing or a new namespace. To learn how Redshift Serverless restore works, see [Redshift Serverless Restore](aws_restore_hiw_redshift_serverless.md).

|  |
| --- |
| Important |
| * Veeam Plug-in for AWS supports restoring Redshift Serverless namespaces only to the same AWS accounts to which the source namespaces belong and to the same AWS Region where the source namespaces reside.  * Veeam Plug-in for AWS supports restoring only those Redshift Serverless namespace properties listed in section [Protecting Redshift Serverless](aws_overview_redshift_serverless.md#properties).  * Veeam Plug-in for AWS does not support restoring Amazon Redshift Serverless namespaces to provisioned clusters. * Veeam Plug-in for AWS does not support restoring tables of Amazon Redshift Serverless namespaces. |

To restore a protected Redshift Serverless namespace, do the following:

1. [Launch the Redshift Serverless Restore wizard](aws_restore_launch_redshift_serverless.md).
2. [Select a restore point](aws_restore_point_redshift_serverless.md).
3. [Specify account settings for restore](aws_restore_account_redshift_serverless.md).
4. [Choose a restore mode](aws_restore_mode_redshift_serverless.md).
5. [Configure workgroup settings](aws_restore_redshift_serverless_workgroup.md).
6. [Configure namespace settings](aws_restore_redshift_serverless_namespace.md).
7. [Specify a restore reason](aws_restore_reason_redshift_serverless.md).
8. [Finish working with the wizard](aws_restore_finish_redshift_serverless.md).

Page updated 2026-05-22

