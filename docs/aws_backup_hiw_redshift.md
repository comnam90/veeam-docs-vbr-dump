---
title: "Redshift Clusters Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_hiw_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Clusters Backup


A backup appliance performs Redshift clusters backup in the following way:

1. The backup appliance uses the [AWS Backup service](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-aws-backup.html) to create a cloud-native backup of the Redshift cluster and saves this backup to the specified backup vault in the same AWS Region in which the source cluster resides.
2. The backup is assigned AWS tags upon creation. Keys and values of AWS tags contain encrypted metadata that helps backup appliance identify the related cluster backup.

Related Topics

* [Backup Chain](aws_backup_chain_redshift.md)
* [Redshift Backup Retention](aws_retention_backup_redshift.md)

Page updated 2026-05-15

