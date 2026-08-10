---
title: "DynamoDB Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_dynamodb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Restore


|  |
| --- |
| Important |
| You can restore a DynamoDB table only to the same AWS account to which the source table belongs. |

To restore a DynamoDB table from a backup, a backup appliance performs the following steps using native [AWS capabilities](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Restore.TutorialAWS.html):

1. Creates a table in the specified location.
2. Restores backed-up data (items and attributes) to the restored table.
3. Modifies the configuration setting values of the created DynamoDB table.

To learn how to restore a DynamoDB table from a DynamoDB backup or a backup copy, see [DynamoDB Restore](aws_dynamo_restore.md).

Page updated 2026-05-15

