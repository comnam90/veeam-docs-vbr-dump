---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


When you plan to deploy and configure backup appliances, keep in mind the following limitations and considerations.

Deployment

When deploying backup appliances, consider the following:

* Backup appliances are supported only in AWS Global, AWS China and AWS GovCloud (US) Regions.
* You can deploy backup appliances within a single Availability Zone only.
* To ensure successful deployment and installation of backup appliances, customers are encouraged to make sure they are operating within AWS service quotas. For more information, see [AWS Documentation](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html).

Licensing

If the Paid license is not installed, backup appliances will operate in the Free edition allowing you to protect up to 10 instances free of charge. For more information, see [Licensing](aws_licensing.md).

Hardware

The minimum recommended EC2 instance type for the backup appliance is t3.medium, and the supported AMI architecture is x86\_64. For the list of all existing instance types, see [AWS Documentation](https://aws.amazon.com/ec2/instance-types/).

Software

To access backup appliance Web UI, use Microsoft Edge (latest version), Mozilla Firefox (latest version) or Google Chrome (latest version). Internet Explorer is not supported.

Security Certificates

Backup appliances supports certificates only in the .PFX and .P12 formats.

Backup Repositories

When managing backup repositories, consider the following:

* Veeam Plug-in for AWS supports storing image-level backups only in the S3 Standard, S3 Standard-IA, S3 Glacier Flexible Retrieval and S3 Glacier Deep Archive storage classes. The S3 One Zone-IA storage class is not supported.

When you add a backup repository of the S3 Glacier Flexible Retrieval or S3 Glacier Deep Archive storage class, the backup appliance does not create any S3 Glacier vaults in your AWS environment — it assigns the selected storage class to backups stored in the repository. That is why these backups remain in Amazon S3 and cannot be accessed directly through the Amazon S3 Glacier service.

* Amazon S3 buckets with S3 Object Lock and S3 Versioning enabled can be used only for creating backup repositories with enabled immutability settings.

If you enable S3 Object Lock for a bucket that is already used as a target location for image-level backups, the backup appliance will not be able to continue creating backups and storing them in an existing backup repository.

* Veeam Plug-in for AWS does not support changing immutability settings for existing repositories specified in backup policies. However, you can change immutability settings for the newly created bucket in the AWS Management Console after creating the bucket, and then specify this bucket as the target location for image-level backups when creating a new repository with immutability enabled.

* Veeam Plug-in for AWS does not support changing Amazon S3 buckets, folders and storage classes for backup repositories that are already added to backup appliances.
* Veeam Plug-in for AWS does not support Amazon S3 buckets that use server-side encryption with AWS KMS keys (SSE-KMS).

* If you plan to use [AWS Key Management Service (KMS) keys](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html) to encrypt backup repositories, note that Veeam Plug-in for AWS supports symmetric KMS keys only.

If you use a KMS key to encrypt a repository, do not disable or delete this key. Otherwise, the backup appliance will not be able to encrypt and decrypt data stored in the repository.

* After you create a repository with encryption enabled, you will not be able to disable encryption for this repository. However, you will still be able to change the encryption settings as described in section [Editing Backup Repository Settings](aws_repositories_edit.md).

* Backup repositories must not be managed by multiple backup appliances simultaneously. Retention sessions running on different backup appliances may corrupt backups stored in the repositories, which may result in unpredictable data loss.
* Veeam Plug-in for AWS preserves all backup files previously stored in Amazon S3 buckets that are no longer used as backup repositories.

If you no longer need the backed-up data, either delete it as described in sections [Removing EC2 Backups and Snapshots](aws_backups_remove.md), [Removing RDS Backups and Snapshots](aws_snapshots_remove_rds.md) and [Removing VPC Configuration Backups](aws_backups_remove_vpc.md) before you remove the repositories from the backup appliance, or [use the AWS Management Console](aws_uninstall.md#removeData) to delete the data if the repositories have already been removed.

Storage Vaults

When managing storage vaults, consider the following:

* Veeam Plug-in for AWS does not support adding storage vaults located in AWS China Regions or AWS GovCloud (US) Regions.
* Veeam Plug-in for AWS supports storing image-level backups only in storage vaults with the S3 Standard-IA storage class assigned. The S3 Standard, S3 Glacier Flexible Retrieval and S3 Glacier Deep Archive storage classes are not supported.

AWS Organizations

When performing data protection operations with resources within AWS Organizations, consider the following:

* Veeam Plug-in for AWS does not support taking manual snapshots and backups using IAM roles specified in the [organization settings](aws_organization_add_settings.md).
* Veeam Plug-in for AWS does not support cloud-native snapshot replication of EC2 instances and RDS resources using IAM roles specified in the organization settings.
* Veeam Plug-in for AWS does not support managing backup repositories using IAM roles specified in the organization settings.

EC2 Backup

When protecting EC2 instances, consider the following:

* Veeam Plug-in for AWS prioritizes SLA-based backup policies over schedule-based backup policies. If an EC2 instance is included into both a schedule-based and an SLA-based backup policy, it will be processed by the SLA-based backup policy only.

* Veeam Plug-in for AWS protects only EC2 instances that run in VPCs. EC2-Classic instances are not supported. For more information, see [this Veeam KB article](https://www.veeam.com/kb3147).

When the backup appliance backs up EC2 instances with IPv6 addresses assigned, it does not save the addresses. That is why when you restore these instances, IP addresses are assigned according to the settings specified in AWS for the subnet to which the restored instances will be connected.

* Backup appliances may fail to create image-level backups of EC2 instances with [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes) if the AMIs that were used to deploy the instances do not support the type of worker instances deployed for the backup operation. To work around the issue, modify the worker profile to choose another instance type, as described in section [Managing Worker Profiles](aws_worker_profiles.md).

* [Applies only to image-level backups and file-level recovery from cloud-native snapshots] Veeam Plug-in for AWS does not support creating image-level backups and restoring EC2 instances with [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes) that have vendor restrictions preventing root EBS volumes from being attached to worker instances as secondary volumes. To learn how EC2 backup is performed, see [Protecting EC2 Instances](aws_backup_hiw_ec2.md).

* Veeam Plug-in for AWS does not support creating cloud-native snapshots and image-level backups for arm64-based EC2 instances if these instances were deployed from AMIs containing [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes).

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.
* Since backup appliances run retention sessions for SLA-based backup policies as soon as they finalize the data protection window in all protected regions, it is recommended that you estimate how long it may take for the appliance to complete a retention session first, and then configure a backup window. Otherwise, the backup appliance will not be able to run retention sessions, and obsolete data will not be removed from the appliance configuration database and backup repositories.

RDS Backup

When protecting RDS resources, consider the following:

* Veeam Plug-in for AWS supports creating image-level backups for Microsoft SQL Server and PostgreSQL DB instances only. However, the size of each database hosted on a protected Microsoft SQL Server DB instance must not exceed 5 TiB.

For the list of supported PostgreSQL versions, see [Protecting RDS Resources](aws_overview_rds.md#applications).

* For backup appliances to be able to create image-level backups for PostgreSQL DB instances, make sure that [security groups associated with worker instances](aws_worker_add_config_prod.md#region) allow outbound HTTPS traffic from the worker instances through port 443 to download a certificate bundle for establishing SSL/TLS connections. For more information on certificate bundles for AWS Regions, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html#UsingWithRDS.SSL.RegionCertificates).
* Veeam Plug-in for AWS does not support creating cloud-native snapshots for PostgreSQL DB clusters with Multi-AZ DB cluster deployment and IBM Db2 DB instances.
* Veeam Plug-in for AWS does not support creating cloud-native snapshots for Aurora PostgreSQL Limitless Database clusters.
* Veeam Plug-in for AWS does not support creating image-level backups for Microsoft SQL Server DB instances that host system databases only.
* Veeam Plug-in for AWS does not support creating image-level backups for Aurora PostgreSQL clusters.
* Veeam Plug-in for AWS does not support creating archived backups for Microsoft SQL Server DB instances.

* [Applies only if you plan to back up Microsoft SQL Server DB instances] The SQLSERVER\_BACKUP\_RESTORE option must be added to the option group that is applied to each processed DB instance.

The IAM role that is associated with the SQLSERVER\_BACKUP\_RESTORE option must have the permissions required to access temporary Amazon S3 buckets. The IAM role must also have a trust relationship and a permissions policy attached to allow the Amazon RDS service to assume the role. For more information on the backup and restore option, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.SQLServer.Options.BackupRestore.html#Appendix.SQLServer.Options.BackupRestore.Add).

* [Applies only if you plan to back up Microsoft SQL Server DB instances] If you plan to enable the [private network deployment](aws_enable_private_network_deployment.md) functionality, Veeam Plug-in for AWS must be able to connect to the public s3..amazonaws.com endpoint to access temporary Amazon S3 buckets. Otherwise, backup policies processing DB instances will fail to produce image-level backups. For more information on the temporary buckets, see [Performing RDS Backup](aws_backup_hiw_rds.md).

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

Redshift Clusters Backup

When protecting Redshift clusters, consider the following:

* Veeam Plug-in for AWS supports backup of only those Redshift cluster properties that are described in section [Protecting Redshift Clusters](aws_overview_redshift.md#parameters).
* Veeam Plug-in for AWS supports creating cloud-native backups for Redshift clusters only to the same AWS accounts to which the source clusters belong and the same AWS Region where the source clusters reside.
* For backup appliances to be able to create cloud-native backups of Redshift clusters, you must enable the Opt-in service for the Redshift resource type in the AWS Backup settings. Otherwise, Veeam Plug-in for AWS will automatically enable the service for each AWS Region specified in the backup policy settings in your AWS account while performing backup operations. For more information on considerations for using AWS Backup with Amazon Redshift, see [AWS Documentation](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-aws-backup.html#managing-aws-backup-considerations).
* Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

Redshift Serverless Backup

When protecting Redshift Serverless namespaces, consider the following:

* Veeam Plug-in for AWS supports backup of only those Redshift Serverless properties that are described in section [Protecting Redshift Serverless](aws_overview_redshift_serverless.md#properties).

* Veeam Plug-in for AWS supports creating cloud-native backups for Redshift Serverless namespaces only to the same AWS accounts to which the source namespaces belong and the same AWS Region where the source namespaces reside.

* Make sure that workgroups are associated with Redshift Serverless namespaces that you plan to protect. Otherwise, the backup operation may fail to complete successfully.
* Due to technical limitations, Veeam Plug-in for AWS does not estimate the cost of creating and maintaining cloud-native backups of Redshift Serverless namespaces.

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

DynamoDB Backup

When protecting DynamoDB tables, consider the following:

* Veeam Plug-in for AWS supports backup of only those DynamoDB table properties that are described in section [Protecting DynamoDB Tables](aws_overview_dynamo.md#table_parameters).

* Veeam Plug-in for AWS supports creating cloud-native backups for DynamoDB tables only to the same AWS accounts to which the source tables belong.
* For backup appliances to be able to create cloud-native backups for DynamoDB tables, you must configure the AWS Backup settings to enable both the Opt-in service and the advanced features for Amazon DynamoDB backups. Otherwise, Veeam Plug-in for AWS will automatically enable these settings for each AWS Region specified in the backup policy settings in your AWS account while performing backup operations. For more information on advanced DynamoDB backup, see [AWS Documentation](https://docs.aws.amazon.com/aws-backup/latest/devguide/advanced-ddb-backup.html).

* Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.

* Veeam Plug-in for AWS uses the [AWS Backup](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorksAWS.html) service to create DynamoDB backups and backup copies. The [DynamoDB backup](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorks.html) service is not supported.

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

EFS Backup

When protecting EFS file systems, consider the following:

* Veeam Plug-in for AWS supports creating cloud-native backups for EFS file systems only to the same AWS accounts to which the source file systems belong.

* Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.

* Indexing of the backed up EFS file systems is not supported in the Free edition of Veeam Plug-in for AWS. For more information on license editions, see [Licensing](aws_licensing.md).

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

FSx Backup

When protecting FSx file systems, consider the following:

* Veeam Plug-in for AWS supports backup of only those FSx file system properties that are described in section [Protecting FSx File Systems](aws_overview_fsx.md#parameters).

* Veeam Plug-in for AWS supports creating cloud-native backups for FSx file systems only to the same AWS accounts to which the source file systems belong.
* For backup appliances to be able to create cloud-native backups for FSx file systems, you must enable the Opt-in service for the FSx resource type in the AWS Backup settings. Otherwise, Veeam Plug-in for AWS will automatically enable the service for each AWS Region specified in the backup policy settings in your AWS account while performing backup operations.

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for NetApp ONTAP file systems. However, you can back up Amazon FSx for NetApp ONTAP file systems using the Veeam Backup & Replication console. For more information, see [Unstructured Data Backup](unstructured_data_backup.md).
* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for Windows File Server file systems that use AWS Secrets Manager to store service account credentials when joined to a self-managed Microsoft Active Directory (AD).

* Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for Lustre file systems with the [Scratch deployment type](https://docs.aws.amazon.com/fsx/latest/LustreGuide/using-fsx-lustre.html?icmpid=docs_fsx_console#scratch-file-system).

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for Lustre with the [data repository association](https://docs.aws.amazon.com/fsx/latest/LustreGuide/fsx-data-repositories.html).

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for OpenZFS with the [Intelligent-Tiering storage class](https://docs.aws.amazon.com/fsx/latest/OpenZFSGuide/performance-intelligent-tiering.html).

* Veeam Plug-in for AWS uses the [AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html) service to create FSx backups and backup copies. The AWS Backup service does not support creating backup copies of FSx backups stored in [Opt-in Regions](https://docs.aws.amazon.com/controltower/latest/userguide/opt-in-region-considerations.html).

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

VPC Backup

When protecting VPC configurations, consider the following:

* Veeam Plug-in for AWS does not support creating backups for the following VPC configuration components: VPC Traffic Mirroring, AWS Network Firewall, Route 53 Resolver DNS Firewall, AWS Verified Access, VPC Flow Logs, carrier gateways, customer IP pools, transit gateway policy tables, or core networks in route tables.

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

EC2 Restore

When restoring EC2 instances, consider the following:

* Veeam Plug-in for AWS supports file-level recovery for FAT, FAT32, NTFS, ext2, ext3, ext4, XFS and Btrfs file systems only. For EC2 instances running Microsoft Windows OSes, Veeam Plug-in for AWS supports file-level recovery for basic volumes only.

* Veeam Plug-in for AWS does not support restoring files and folders stored on volumes with Windows-native [Data Deduplication](https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/overview) enabled.

* If you restore multiple EC2 instances that have the same EBS volume attached, Veeam Plug-in for AWS creates a separate volume for each instance and enables the Multi-Attach option for all volumes. After the restore operation completes, you can manually delete extra EBS volumes in the AWS Management Console and attach the necessary volume to the instances.

For more information on Amazon EBS Multi-Attach, see [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes-multi.html).

* [Applies only if you plan to restore EC2 instances to a new location or with different settings] Veeam Plug-in for AWS restores EC2 instances with a single network interface and assigns a new primary private IP address to each instance.

* [Applies only if you plan to restore EC2 instances to the original location] Veeam Plug-in for AWS restores the instance and all network interfaces that were attached to the source EC2 instance. However, there are limitations regarding Elastic IP and private IP addresses. For more information, see [Performing EC2 Instance Restore](aws_restore_entire_before_you_begin.md#limitation_ec2_rto).

* [Applies only if you plan to restore EC2 instances to the original location] If [stop protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-stop-protection.html) or [termination protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html#Using_ChangingDisableAPITermination) is enabled on an EC2 instance, Veeam Plug-in for AWS will not be able to restore the instance and will raise an error notifying that you must disable stop protection or termination protection on the source instance.
* [Applies only if you plan to restore EC2 instances to the original location] Veeam Plug-in for AWS does not support restoring EC2 instances if the source instances with termination protection and stop protection enabled still exist in AWS.

* Veeam Plug-in for AWS does not support restore of IPv6 addresses, tags of Elastic IP addresses or prefixes assigned to Amazon EC2 network interfaces attached to EC2 instances.

RDS Restore

When restoring RDS resources, consider the following:

* When restoring Aurora DB clusters that are part of an Amazon Aurora global database, Veeam Plug-in for AWS restores only the primary clusters in the primary AWS Region. Secondary clusters must be created manually in the AWS Management Console after the restore operation completes.

For more information on Amazon Aurora Global Database feature, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html).

* When restoring Aurora DB clusters to a new location, Veeam Plug-in for AWS creates only primary DB instances in the restored clusters. Additional writer DB instances (for Aurora multi-master clusters) or Aurora Replicas (for Aurora DB clusters with single-master replication) must be added manually in the AWS Management Console after the restore operation completes.

To learn how to add DB instances to Amazon Aurora DB clusters, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-replicas-adding.html).

* Veeam Plug-in for AWS does not support restoring RDS resources to the original location if the IAM role specified for the restore operation belongs to an AWS account that differs from the AWS account to which the source resources belong.
* Veeam Plug-in for AWS does not support restoring RDS resources to the original location if deletion protection is enabled for the source resource.

* [Applies only if you restore databases of Microsoft SQL Server and PostgreSQL DB instances from image-level backups] Keep in mind the following:

* The database account that you specify for the restore operation will become the owner of all restored databases.
* Veeam Plug-in for AWS does not support restoring original database accounts, including their predefined roles and access privileges. Therefore, you will have to manually recreate these accounts on the restored databases and reassign their privileges after the restore process completes.

* [Applies only if you restore databases of Microsoft SQL Server DB instances from image-level backups] Keep in mind the following:

* The target DB instance must be set to the same time zone as the source DB instance. Otherwise, your applications may encounter data consistency issues.
* The target DB instance must run the same or a later engine version as the source DB instance. Otherwise, the restore operation will fail to complete successfully.
* Veeam Plug-in for AWS does not support restoring databases that contain the FILESTREAM file group.
* Veeam Plug-in for AWS does not support restoring databases of DB instances that have a zero backup retention period to DB instances that have a nonzero retention period due to the incompatibility in database recovery models. This is the expected behavior caused by [AWS technical limitations](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.SQLServer.CommonDBATasks.DatabaseRecovery.html).

Redshift Restore

When restoring Redshift clusters, consider the following:

* Veeam Plug-in for AWS supports restoring Amazon Redshift clusters only to the same AWS accounts to which the source clusters belong and the same AWS Region where the source clusters reside.
* Veeam Plug-in for AWS supports restoring only those Redshift cluster properties that are described in section [Protecting Redshift Clusters](aws_overview_redshift.md#properties).

* Veeam Plug-in for AWS does not support restoring Amazon Redshift clusters with the Multi-AZ deployment. These clusters will be restored as clusters with the Single-AZ deployment.

Redshift Serverless Restore

When restoring Redshift Serverless namespaces, consider the following:

* Veeam Plug-in for AWS supports restoring Amazon Redshift Serverless namespaces only to the same AWS accounts to which the source namespaces belong and the same AWS Region where the source namespaces reside.
* Veeam Plug-in for AWS supports restoring only those Redshift Serverless namespace properties listed in section [Protecting Redshift Serverless](aws_overview_redshift_serverless.md#properties).
* Veeam Plug-in for AWS does not support restoring Amazon Redshift Serverless namespaces to provisioned clusters.
* Veeam Plug-in for AWS does not support restoring tables of Amazon Redshift Serverless namespaces.

DynamoDB Restore

When restoring DynamoDB tables, consider the following:

* Veeam Plug-in for AWS supports restoring DynamoDB tables only to the same AWS account to which the source tables belong.
* Veeam Plug-in for AWS supports restoring only those DynamoDB table properties that are described in section [Protecting DynamoDB Tables](aws_overview_dynamo.md#table_parameters).

* The [AWS Backup](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorksAWS.html) service does not support copying DynamoDB cloud-native backups stored in a cold storage tier to another AWS Region. This means that you will only be able to use these backups to restore tables to the same AWS Region in which the backups reside after being transitioned from a warm storage tier.

* You can change the Time to Live (TTL) setting for DynamoDB tables only an hour after the restore operation completes.

EFS Restore

When restoring EFS file systems, consider the following:

* Veeam Plug-in for AWS supports restoring EFS file systems only to the same AWS account to which the source file systems belong.

FSx Restore

When restoring FSx file systems, consider the following:

* Veeam Plug-in for AWS supports restoring FSx file systems only to the same AWS accounts to which the source file systems belong.

* Veeam Plug-in for AWS supports restoring only those FSx file system properties that are described in section [Protecting FSx File Systems](aws_overview_fsx.md#table_parameters).

* Veeam Plug-in for AWS does not support restoring Amazon FSx for Windows File Server file systems that use AWS Secrets Manager to store service account credentials when joined to a self-managed Microsoft Active Directory (AD).

VPC Restore

When restoring VPC configurations, consider the following:

* Veeam Plug-in for AWS does not support restoring entire VPC configurations to a new location for the following VPC configuration items: Client VPN endpoints, customer gateways or load balancer listeners that use authentication certificates or specific components of route tables (core networks, routes to local gateways, network interfaces, instances or carrier gateways).
* Veeam Plug-in for AWS does not support restoring specific VPC configuration items to a new location.

SureBackup

Starting from backup appliance version 10, the SureBackup functionality is supported for backup appliances managed by Veeam Backup & Replication servers. However, this functionality is limited at the moment — you can perform backup verification and content scan only. Also, consider that since SureBackup performs backup integrity check and extensive content analysis, it requires additional data to be read from AWS, which may incur an increase in the associated costs.

For more information on SureBackup, see [Recovery Verification](surebackup_hiw.md).

Page updated 2026-06-29

