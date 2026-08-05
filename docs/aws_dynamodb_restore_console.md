---
title: "DynamoDB Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_dynamodb_restore_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Restore Using Console


You can recover corrupted DynamoDB tables in the backup appliance Web UI only. However, you can launch the DynamoDB Table Restore wizard directly from the Veeam Backup & Replication console to start the restore operation:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the backup policy that protects the DynamoDB tables you want to recover, select the necessary table and click Amazon DynamoDB on the ribbon.

Alternatively, you can right-click the selected table and click Restore to Amazon DynamoDB.

|  |
| --- |
| Important |
| You cannot restore multiple DynamoDB tables from the Veeam Backup & Replication console. |

Veeam Backup & Replication will open the DynamoDB Table Restore wizard in a web browser. Complete the wizard as described in section [DynamoDB Restore Using Web UI](aws_restore_point_dynamo.md).

[![Restore to Amazon DynamoDB](images/aws_restore_dynamodb.webp)](images/aws_restore_dynamodb.webp "Restore to Amazon DynamoDB")

Page updated 2026-07-20

