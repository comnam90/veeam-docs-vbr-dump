---
title: "Performing DynamoDB Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_perform_dynamo_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing DynamoDB Backup


One backup policy can be used to process one or more DynamoDB tables either within one AWS account or within an entire AWS Organization. The scope of data that you can protect in an AWS account is limited by permissions of an IAM role that is specified in the backup policy settings, whereas the scope of data that you can protect in an AWS Organization is limited by permissions of an IAM role that is specified in the organization settings.

To schedule data protection tasks to run automatically,
[create backup policies](aws_policies_create_dynamo.md)
. For each protected DynamoDB table, you can also
[take a backup manually](aws_backup_manual_dynamo.md)
when needed.

|  |
| --- |
| Important |
| Before you create a DynamoDB backup policy, check the limitations and prerequisites described in section  [Before You Begin](aws_add_dynamo_policy_byb.md) . |

Page updated 2026-03-18

