---
title: "DynamoDB Backup Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_retention_backup_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Backup Retention


For DynamoDB backups, the backup appliance retains restore points for the period of time specified in [backup scheduling settings](aws_add_policy_schedule_retention_dynamo.md).

During every successful backup session, the backup appliance creates a restore point and saves the date, time and applied retention settings in the restore point metadata. If the appliance detects that the period of time for which the restore point was stored exceeds the period specified in the retention settings, it automatically removes the restore point from the DynamoDB chain. You can also remove unnecessary DynamoDB backups manually as described in section [Removing DynamoDB Backups](aws_backups_remove_dynamo.md).

[![DynamoDB Backup Retention](images/aws_dynamo_backup_retention.webp)](images/aws_dynamo_backup_retention.webp "DynamoDB Backup Retention")

|  |
| --- |
| Note |
| Backup appliances do not apply retention policy to DynamoDB backups created manually. To learn how to remove them, see [Removing DynamoDB Backups Created Manually](aws_backups_remove_individual_dynamo.md). |

Page updated 2026-05-15

