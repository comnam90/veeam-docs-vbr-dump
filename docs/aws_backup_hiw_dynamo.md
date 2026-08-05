---
title: "DynamoDB Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_hiw_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Backup


A backup appliance performs DynamoDB backup in the following way:

1. The backup appliance uses the [AWS Backup service](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CreateBackupAWS.html) to create a cloud-native backup of the DynamoDB table, and saves this backup to the specified backup vault in the same AWS Region in which the source table resides.

The backup is assigned AWS tags upon creation. Keys and values of AWS tags contain encrypted metadata that helps the backup appliance identify the related table backup.

1. If you configure the DynamoDB backup policy to copy backup files to another AWS Region, the backup appliance copies the created backup to the target AWS Region in the same AWS account.

Related Topics

* [Backup Chain](aws_backup_chain_dynamo.md)
* [DynamoDB Backup Retention](aws_retention_backup_dynamo.md)

Page updated 2026-05-15

