---
title: "DynamoDB Restore Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_dynamo_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Restore Using Web UI


In case of a disaster, you can restore a DynamoDB table from a DynamoDB backup or backup copy. Veeam Plug-in for AWS allows you to restore one or more DynamoDB tables at a time, to the original location or to a new location. To learn how DynamoDB restore works, see [DynamoDB Restore](aws_restore_hiw_dynamodb.md).

|  |
| --- |
| Important |
| * Veeam Plug-in for AWS supports restoring DynamoDB tables only to the same AWS account where the source tables reside.  * Veeam Plug-in for AWS supports restoring only those DynamoDB table properties that are described in section [Protecting DynamoDB Tables](aws_overview_dynamo.md#table_parameters). * The [AWS Backup](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorksAWS.html) service does not support copying DynamoDB cloud-native backups stored in a cold storage tier to another AWS Region. These means that you will only be able to use these backups to restore tables to the same AWS Region in which the backups reside after being transitioned from a warm storage tier. |

To restore a protected DynamoDB table, do the following:

1. [Launch the DynamoDB Restore wizard](aws_restore_launch_dynamo.md).
2. [Select a restore point](aws_restore_point_dynamo.md).
3. [Specify account settings for restore](aws_restore_account_dynamo.md).
4. [Choose a restore mode](aws_restore_mode_dynamo.md).
5. [Enable encryption for the restored table](aws_restore_encryption_dynamo.md).
6. [Configure table settings](aws_restore_type_dynamo.md).
7. [Choose capacity mode for the restored table](aws_restore_capacity_mode_dynamo.md).
8. [Specify a restore reason](aws_restore_reason_dynamo.md).
9. [Finish working with the wizard](aws_restore_finish_dynamo.md).

Page updated 2026-05-22

