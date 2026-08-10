---
title: "Performing EFS Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_perform_efs_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing EFS Backup


One backup policy can be used to process one or more EFS file systems either within one AWS account or within an entire AWS Organization. The scope of data that you can protect in an AWS account is limited by permissions of an IAM role that is specified in the backup policy settings, whereas the scope of data that you can protect in an AWS Organization is limited by permissions of an IAM role that is specified in the organization settings.

To schedule data protection tasks to run automatically, [create backup policies](aws_policies_create_efs.md). For each protected EFS systems, you can also [take a backup manually](aws_backup_manual_efs.md) when needed.

|  |
| --- |
| Important |
| * Veeam Plug-in for AWS supports creating cloud-native backups for EFS file systems only to the same AWS accounts to which the source file systems belong.  * Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.  * Indexing of the backed up EFS file systems is not supported in the Free edition of backup appliances. For more information on license editions, see [Licensing](aws_licensing.md).  * Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued. |

Page updated 2026-05-21

