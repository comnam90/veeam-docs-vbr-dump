---
title: "Retention Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retention Policies


Cloud-native snapshots, snapshot replicas and image-level backups created by backup policies are not kept forever — they are removed according to retention policy settings specified while creating the policies.

Depending on the data protection scenario, retention policy can be specified:

* In restore points — for cloud-native snapshots and snapshot replicas by schedule-based backup policies.

The snapshot chain can contain only the allowed number of restore points. If the number of allowed restore points is exceeded, backup appliances remove the earliest restore point from the snapshot chain. For more information, see [EC2 Backup Retention](aws_retention_backup.md) and [RDS Backup Retention](aws_retention_backup_rds.md).

* In days/months/years — for image-level backups and archived backups, as well as for cloud-native snapshots and snapshot replicas produced by SLA-based backup policies.

Restore points in the backup chain (either standard or archive) can be stored in the backup repository for the allowed period of time. If a restore point is older than the specified time limit, backup appliances remove it from the backup chain. For more information, see sections [EC2 Snapshot Retention](aws_retention_snapshots.md), [EC2 Backup Retention](aws_retention_backup.md), [RDS Backup Retention](aws_retention_backup_rds.md), [Redshift Backup Retention](aws_retention_backup_redshift.md), [DynamoDB Backup Retention](aws_retention_backup_dynamo.md), [EFS Backup Retention](aws_retention_backup_efs.md), [FSx Backup Retention](aws_retention_backup_fsx.md) and [VPC Configuration Backup Retention](aws_retention_backup_vpc.md).

You can also specify global retention settings for obsolete snapshots and replicas. For more information, see [Configuring Global Retention Settings](aws_retention_settings.md#snapshots).

|  |
| --- |
| Notes |
| * When configuring policy scheduling, consider that backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on the backup appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued. * If your backup appliance is managed by a Veeam Backup & Replication server, the backup server becomes the owner of the backup repositories. As a result, Veeam Backup & Replication will prioritize retention settings configured for the backup server over retention settings configured for backup policies. For more information on how Veeam Backup & Replication handles retention policies, see [Managing Retention Policy](external_repository_retention.md). |

Related Topics

* [Creating EC2 Backup Policies](aws_add_policy_schedule_retention.md)
* [Creating RDS Backup Policies](aws_add_policy_schedule_retention_rds.md)
* [Creating Redshift Clusters Backup Policies](aws_add_policy_schedule_retention_redshift.md)
* [Creating Redshift Serverless Backup Policies](aws_add_policy_schedule_retention_redshift_serverless.md)
* [Creating DynamoDB Backup Policies](aws_add_policy_schedule_retention_dynamo.md)
* [Creating EFS Backup Policies](aws_add_policy_schedule_retention_efs.md)
* [Creating FSx Backup Policies](aws_add_policy_schedule_retention_fsx.md)
* [Editing VPC Configuration Backup Policy](aws_vpc_policy_retention.md)

Page updated 2026-05-22

