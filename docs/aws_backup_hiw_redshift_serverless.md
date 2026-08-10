---
title: "Redshift Serverless Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_hiw_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Serverless Backup


A backup appliance performs Redshift Serverless backup in the following way:

1. The backup appliance uses the [Amazon Redshift Serverless service](https://docs.aws.amazon.com/redshift/latest/mgmt/serverless-snapshots-recovery-points.html) to create a cloud-native backup of the Redshift Serverless namespace, and saves this backup in the same AWS Region in which the source namespace resides.
2. The backup is assigned AWS tags upon creation. Keys and values of AWS tags contain encrypted metadata that helps the backup appliance identify the related namespace backup.

Related Topics

* [Backup Chain](aws_backup_chain_redshift_serverless.md)
* [Redshift Serverless Backup Retention](aws_retention_backup_redshift_serverless.md)

Page updated 2026-05-15

