---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_dynamo_policy_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you protect DynamoDB tables, consider the following:

* Veeam Plug-in for AWS supports backup of only those DynamoDB table properties that are described in section [Protecting DynamoDB Tables](aws_overview_dynamo.md#table_parameters).

* Veeam Plug-in for AWS supports creating cloud-native backups for DynamoDB tables only to the same AWS accounts to which the source tables belong.
* For backup appliances to be able to create cloud-native backups for DynamoDB tables, you must configure the AWS Backup settings to enable both the Opt-in service and the advanced features for Amazon DynamoDB backups. Otherwise, backup appliances will automatically enable these settings for each AWS Region specified in the backup policy settings in your AWS account while performing backup operations. For more information on advanced DynamoDB backup, see [AWS Documentation](https://docs.aws.amazon.com/aws-backup/latest/devguide/advanced-ddb-backup.html).

* Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.

* Backup appliances use the [AWS Backup](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorksAWS.html) service to create DynamoDB backups and backup copies. The [DynamoDB backup](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorks.html) service is not supported.

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

Page updated 2026-05-21

