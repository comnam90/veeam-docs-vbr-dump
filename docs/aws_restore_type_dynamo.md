---
title: "Step 6. Configure Table Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_type_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Configure Table Settings


[This step applies only if you have selected the Restore to new location, or with different settings option at the Restore Mode step of the wizard]

At the Settings step of the wizard, you can specify a new name for the restored table. To do that, select the table and click Rename.

You can also choose a class for the restored table, decide whether you want to protect the table from accidental deletion, and enable point-in-time recovery to prevent accidental writes and to ensure restore to any point in time during the last 35 days. To specify the configuration settings, select the table and click Edit.

|  |
| --- |
| Note |
| By default, the AWS Backup service restores tables with the Standard table class only. To restore a table with the Standard-IA table class, the backup appliance updates the table class of the restored table. Keep in mind that you can change table classes no more than two times during a 30-day period.  For more information on considerations and limitations when choosing a table class, see [AWS Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithTables.tableclasses.html). |

For more information on deletion protection, see [AWS Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithTables.Basics.html#WorkingWithTables.Basics.DeletionProtection). For more information on point-in-time recovery, see [AWS Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery_Howitworks.html).

[![Restoring DynamoDB Tables](images/aws_restore_general_settings_dynamodb.webp)](images/aws_restore_general_settings_dynamodb.webp "Restoring DynamoDB Tables")

Page updated 2026-05-22

