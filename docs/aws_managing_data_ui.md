---
title: "Managing Backed-Up Data Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_managing_data_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Backed-Up Data Using Web UI


Information on all protected AWS resources is stored in the configuration database of backup appliances. Even if a resource is no longer protected by any configured backup policy and even if the resource no longer exists in AWS, information on the backed-up data will not be deleted from the database until backup appliances automatically remove all restore points associated with this resource according to the retention settings saved in the backup metadata. You can also remove the restore points manually on the Protected Data page.

|  |
| --- |
| Note |
| Backup appliances do not include restore points created manually in backup and snapshot chains, and do not apply the configured retention policy settings to these restore points. This means that the restore points are kept in your AWS environment unless you remove them manually, as described in sections [Removing EC2 Snapshots Created Manually](aws_backups_remove_manual_snapshots.md), [Removing RDS Snapshots Created Manually](aws_snapshots_remove_individual_rds.md), [Removing DynamoDB Backups Created Manually](aws_backups_remove_individual_dynamo.md), [Removing Redshift Backups Created Manually](aws_backups_remove_individual_redshift.md), [Removing Redshift Serverless Backups Created Manually](aws_backups_remove_individual_redshift_serverless.md), [Removing EFS Backups Created Manually](aws_backups_remove_individual_efs.md) and [Removing FSx Backups Created Manually](aws_backups_remove_individual_fsx.md). |

In This Section

* [EC2 Data](aws_backups_view_ec2.md)
* [RDS Data](aws_backups_view_rds.md)
* [DynamoDB Data](aws_backups_view_dynamo.md)
* [Redshift Clusters Data](aws_backups_view_redshift.md)
* [Redshift Serverless Data](aws_backups_view_redshift_serverless.md)
* [EFS Data](aws_backups_view_efs.md)
* [FSx Data](aws_backups_view_fsx.md)
* [VPC Configuration Data](aws_backups_view_vpc.md)

Page updated 2026-05-21

