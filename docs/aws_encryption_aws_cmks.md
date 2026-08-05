---
title: "AWS KMS Encryption"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_encryption_aws_cmks.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# AWS KMS Encryption


|  |
| --- |
| Note |
| Backup appliances do not use automatic AWS KMS key rotation for KMS keys, as well as AWS Secrets Manager for storing secrets. |

Veeam Plug-in for AWS allows you to back up, replicate and restore data of EC2 and RDS instance volumes encrypted with [AWS KMS keys](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html), as well as back up and restore EFS and FSx file systems, DynamoDB tables, Redshift clusters and Redshift Serverless namespaces encrypted with AWS KMS keys. Additionally, you can encrypt unencrypted data and change KMS keys used to encrypt data when performing the following operations:

* [Creating EC2 instance snapshot replicas](aws_add_policy_target_settings_replica.md).
* [Creating RDS instance snapshot replicas](aws_add_policy_target_settings_rds_replica.md).
* [Creating cloud-native snapshots of EC2 instances manually](aws_snapshot_manual.md).
* [Creating cloud-native snapshots of RDS instances manually](aws_snapshot_manual_rds.md).
* [Restoring entire EC2 instances to a new location](aws_restore_entire_encryption.md).
* [Restoring entire RDS instances to a new location](aws_restore_rds_encryption.md).
* [Restoring EC2 instance volumes to a new location](aws_restore_volume_encryption.md).
* [Restoring entire EFS file systems to a new location](aws_restore_entire_encryption_efs.md).
* [Restoring FSx file systems to a new location](aws_restore_encryption_fsx.md).
* [Restoring DynamoDB tables to a new location](aws_restore_encryption_dynamo.md).
* [Restoring Redshift clusters to the original location](aws_restore_encryption_redshift.md).
* [Restoring Redshift Serverless namespaces to a new namespace](aws_redshift_serverless_new_namespace.md).

Depending on the operation performed for an encrypted RDS instance or an EC2 instance that has encrypted EBS volumes, the IAM role that a backup appliance uses for the operation requires permissions to access various KMS keys:

* [Creating cloud-native snapshots](aws_encryption_aws_cmks_creating_snapshots.md)
* [Creating snapshot replicas](aws_encryption_aws_cmks_creating_replicas.md)
* [Restoring from cloud-native snapshots](aws_encryption_aws_cmks_restoring_from_snapshots.md)
* [Creating image-level backups](aws_encryption_aws_cmks_creating_backups.md)
* [Restoring from image-level backups](aws_encryption_aws_cmks_restoring_from_backups.md)

|  |
| --- |
| Important |
| If you back up, replicate or restore data of an unencrypted RDS instance or EC2 instance, and if you want to encrypt the backed-up or restored data, you must grant to the IAM role that the backup appliance uses to perform the operation permissions to access only the KMS key with which you want to encrypt the data. To learn how to grant to an IAM role permissions to use a KMS key, see [this Veeam KB article](https://www.veeam.com/kb3057#cmk). |

Page updated 2026-05-19

