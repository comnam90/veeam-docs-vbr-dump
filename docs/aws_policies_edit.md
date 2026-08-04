---
title: "Editing Policy Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_policies_edit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Policy Settings


For each backup policy, you can modify settings configured while creating the policy:

1. Navigate to Policies.
2. Switch to the necessary tab and select the backup policy whose settings you want to edit.

1. Click Edit. The Edit Policy wizard will open.

1. Edit backup policy settings as described in sections [Creating EC2 Backup Policies](aws_policies_create.md), [Creating RDS Backup Policies](aws_policies_create_rds.md), [Creating DynamoDB Backup Policies](aws_policies_create_dynamo.md), [Creating Redshift Clusters Backup Policies](aws_perform_redshift_backup.md), [Creating Redshift Serverless Backup Policies](aws_perform_redshift_serverless_backup.md), [Creating EFS Backup Policies](aws_policies_create_efs.md) or [Creating FSx Backup Policies](aws_policies_create_fsx.md).

|  |
| --- |
| Tip |
| To protect additional resources by a configured backup policy, you can either edit the resource list in the backup policy settings, or add resources to the backup policy on the Resources tab. To learn how to add resources on the Resources tab, see [Adding Resources to Policy](aws_add_to_policy.md). |

[![Editing Backup Policy Settings](images/aws_policies_edit.webp)](images/aws_policies_edit.webp "Editing Backup Policy Settings")

Page updated 2026-05-21

