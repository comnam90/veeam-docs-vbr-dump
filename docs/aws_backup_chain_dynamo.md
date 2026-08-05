---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_chain_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Chain


During every backup session, the backup appliance creates a new cloud-native backup for each DynamoDB table added to the backup policy. To create the backup, the appliance uses the [AWS Backup service](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html). A sequence of cloud-native backups created during a set of backup sessions makes up a backup chain.

[![DynamoDB Backup Chain](images/aws_dynamo_backup_chain.webp)](images/aws_dynamo_backup_chain.webp "DynamoDB Backup Chain")

Each DynamoDB backup in the backup chain contains encrypted metadata. Metadata stores information about the protected table, the backup policy that created the backup, and the date, time and applied retention settings. The backup appliance uses metadata to identify outdated backups, to load the configuration of source tables during recovery operations, and so on.

|  |
| --- |
| Notes |
| * Due to [AWS Backup service limitations](https://docs.aws.amazon.com/aws-backup/latest/devguide/backup-feature-availability.html#features-by-resource), during every backup session,the backup appliance creates a full backup in the regular backup chain. * DynamoDB backups created manually are not included into the DynamoDB backup chain. Therefore, these backups are not removed automatically according to retention policy settings. To learn how to remove them, see [Removing DynamoDB Backups Created Manually](aws_backups_remove_individual_dynamo.md). |

DynamoDB backups act as independent restore points for backed-up tables. If you remove any backup, it will not break the DynamoDB backup chain — you will still be able to roll back table data to any existing restore point. The period of time during which DynamoDB backups are kept in the DynamoDB backup chain is defined by retention policy settings. For more information, see [DynamoDB Backup Retention](aws_retention_backup_dynamo.md).

DynamoDB Backup Copy Chain

If you enable backup copying for a backup policy, the backup appliance will make a copy of the initially created full DynamoDB backup and save it to the target AWS Region specified in the backup policy settings. In the target AWS Region, backup copies created during a set of backup sessions make up a backup copy chain.

The backup appliance creates and maintains a DynamoDB backup copy chain in the same way as a regular DynamoDB backup chain — during every backup copy session the backup appliance creates a full backup in the backup copy chain.

Page updated 2026-05-15

