---
title: "Step 7. Choose Capacity Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_capacity_mode_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Choose Capacity Mode


[Applies only if you have selected the Restore to new location, or with different settings option at the Restore Mode step of the wizard]

At the Capacity step of the wizard, you can change the capacity mode and configure provisioned capacity settings for the restored table. To do that, select the table and click Edit.

|  |
| --- |
| Note |
| You can change the capacity mode only once within 24 hours. For more information on table capacity modes, see [AWS Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CostOptimization_TableCapacityMode.html). |

If you have selected the Provisioned capacity mode option, specify the value of the capacity units in the Read capacity and Write capacity fields. For more information on considerations and limitations when decreasing throughput for provisioned tables, see [AWS Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ServiceQuotas.html#default-limits-throughput).

[![Restoring DynamoDB Tables](images/aws_restore_capacity_mode_dynamodb.webp)](images/aws_restore_capacity_mode_dynamodb.webp "Restoring DynamoDB Tables")

Page updated 2026-05-22

