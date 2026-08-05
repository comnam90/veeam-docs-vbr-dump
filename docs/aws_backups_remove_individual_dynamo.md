---
title: "Removing DynamoDB Backups Created Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_individual_dynamo.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing DynamoDB Backups Created Manually


To remove all backups created for a DynamoDB table manually, follow the instructions provided in the
[Removing DynamoDB Backups](aws_backups_remove_dynamo.md)
section. If you want to remove a specific DynamoDB backup created manually, do the following:

1. Navigate to
   Protected Data
    >
   Databases
    >
   DynamoDB
   .
2. Select the necessary table, and click the link in the
   Restore Points
    column.
3. In the
   Available Restore Points
    window, select a backup that you want to remove, and click
   Remove Manual Backup
   .

[![Removing DynamoDB Backups Created Manually](images/aws_remove_manual_points_dynamo.webp)](images/aws_remove_manual_points_dynamo.webp "Removing DynamoDB Backups Created Manually")

Related Topics

* [Creating DynamoDB Backups Manually](aws_backup_manual_dynamo.md)
* [Removing DynamoDB Backups](aws_backups_remove_dynamo.md)

Page updated 2025-09-26

