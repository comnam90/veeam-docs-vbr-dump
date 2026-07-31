---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup


With Veeam Plug-in for AWS, you can protect data in the following ways:

* Create cloud-native snapshots of EC2 instances and RDS resources

A cloud-native snapshot of a EC2 instance includes point-in-time snapshots of EBS volumes attached to the processed instance. Snapshots of EBS volumes (also referred to as EBS snapshots) are taken using native [AWS capabilities](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html).

A cloud-native snapshot of a DB instance includes a storage volume snapshot of the instance. Snapshots of DB instances (also referred to as DB snapshots) are taken using native [AWS capabilities](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateSnapshot.html).

A cloud-native snapshot of an Aurora DB cluster includes a storage volume snapshot of the cluster that backs up the entire cluster and not just individual databases. Snapshots of Aurora DB clusters (also referred to as DB cluster snapshots) are taken using native [AWS capabilities](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_CreateSnapshotCluster.html).

* Replicate cloud-native snapshots to a remote site

By default, cloud-native snapshots are stored only in the AWS Region where the processed instance resides. For enhanced data safety, you can instruct a backup appliance to create copies of cloud-native snapshots and store them in any other AWS Region within any AWS account. You can also combine the snapshot replication functionality with various [data recovery options](aws_recovery.md) to migrate instance data between AWS Regions and AWS accounts.

* Create image-level backups of EC2 instances and RDS resources

In addition to cloud-native snapshots, you can protect your EC2 and DB instances with image-level backups.

An image-level backup of an EC2 instance captures the whole image of the processed instance (including instance configuration, OS data, application data and so on) at a specific point in time. The backup is saved to a backup repository in the native Veeam format.

An image-level backup of a DB instance captures the Microsoft SQL Server or PostgreSQL databases of the processed instance. The backup is saved to a backup repository in the native Veeam format.

* Create backups of your Redshift clusters

An Amazon Redshift backup captures the whole image of the Redshift cluster at a specific point of time. Redshift backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CreateBackupAWS.html).

Redshift clusters backups are stored only in the AWS Region where the processed clusters reside.

* Create backups of your Redshift Serverless namespaces

An Amazon Redshift Serverless backup captures the data of the processed Redshift Serverless namespace at a specific point of time. Redshift Serverless backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/redshift/latest/mgmt/serverless-snapshots-recovery-points.html).

Redshift Serverless backups are stored only in the AWS Region where the processed namespaces reside.

* Create backups and backup copies of your DynamoDB tables

An Amazon DynamoDB backup captures the whole image of the DynamoDB table at a specific point of time. DynamoDB backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CreateBackupAWS.html).

By default, DynamoDB backups are stored only in the AWS Region where the processed tables reside. For enhanced data safety, you can instruct a backup appliance to create copies of these backups and store them in any other AWS Region within the same AWS account.

* Create backups and backup copies of your EFS and FSx file systems

An Amazon EFS and FSx file system backup captures the whole image of the EFS and FSx file system (including file system configuration, files, directories and so on) at a specific point of time. EFS and FSx backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/efs/latest/ug/awsbackup.html).

By default, EFS and FSx backups are stored only in the AWS Region where the processed resources reside. For enhanced data safety, you can instruct a backup appliance to create copies of these backups and store them in other AWS Regions within the same AWS account. For EFS file systems, you can also combine the backup copy functionality with various [data recovery options](aws_efs_restore_ui.md) to migrate file system data between AWS Regions.

* Create backups of your VPC configuration

An Amazon VPC configuration backup captures the whole image of a VPC configuration of an AWS account (including multiple VPC configuration settings and components) at a specific point in time. By default, the VPC configuration backup is stored in the backup appliance database. For enhanced data safety, you can instruct a backup appliance to create copies of Amazon VPC configuration backups and store them in a backup repository.

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support backup of the following VPC configuration components: VPC Traffic Mirroring, AWS Network Firewall, Route 53 Resolver DNS Firewall, AWS Verified Access, VPC Flow Logs, carrier gateways, customer IP pools, transit gateway policy tables, or core networks in route tables. |

To schedule data protection tasks to run automatically, create backup policies. You will be able to [run the backup policies on demand](aws_policies_start_stop.md) and manually perform backup of EC2 instances, RDS resources, DynamoDB tables, Redshift clusters, Redshift Serverless namespaces, EFS and FSx file systems. To learn how to perform backup manually, see sections [Creating EC2 Snapshots Manually](aws_snapshot_manual.md), [Creating RDS Snapshots Manually](aws_snapshot_manual_rds.md), [Creating DynamoDB Backups Manually](aws_backup_manual_dynamo.md), [Creating Redshift Backups Manually](aws_backup_manual_redshift.md), [Creating EFS Backups Manually](aws_backup_manual_efs.md), [Creating FSx Backups Manually](aws_backup_manual_fsx.md).

|  |
| --- |
| Tip |
| You can perform advanced data protection operations with image-level backups from the Veeam Backup & Replication console. For more information, see [External Repository](external_repository.md). |

In This Section

* [Performing Backup Using Console](aws_performing_backup_console.md)
* [Performing Backup Using Web UI](aws_performing_backup_web_ui.md)

Page updated 2026-05-21

