---
title: "Protecting FSx File Systems"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_overview_fsx.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting FSx File Systems


With Veeam Plug-in for AWS, you can perform the following operations to protect FSx file systems:

* Create cloud-native backups of FSx file systems and store them in any backup vault in the source AWS Region.

An Amazon FSx file system backup captures the whole image of the FSx file system (including file system configuration, files, directories and so on) at a specific point of time. FSx backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html#supported-resources).

* Create backup copies of FSx file systems and store them in AWS Regions within the same AWS account.

By default, FSx backups are stored only in the AWS Region where the processed resources reside. For enhanced data safety, you can instruct backup appliances to create copies of these backups and store them in any other [default AWS Region](https://docs.aws.amazon.com/controltower/latest/userguide/opt-in-region-considerations.html) (that is, an AWS Region activated by default for your AWS account) within the same AWS account.

To protect FSx file systems, backup appliances run backup policies. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, how to retain restore points, and so on.

Veeam Plug-in for AWS does not install agent software inside instances to back up FSx file systems — it uses native AWS capabilities instead. During every backup session, a backup appliance creates a cloud-native backup for each file system added to a backup policy. The cloud-native backup is further used to create a backup copy in another AWS Region.

Supported FSx File System Properties

Veeam Plug-in for AWS allows you to back up and restore the following file system properties:

Supported FSx File System Properties

| Property | Description | Ability to Change Property During Restore to New Location |
| File system name | Name of an FSx file system. | Yes |
| Deployment type | Deployment type of the FSx file system. | No |
| Storage type | Storage type of the FSx file system. | No |
| Storage capacity | Storage capacity of the FSx file system. | No |
| Throughput capacity  [Applies only to FSx for Windows File Server and FSx for OpenZFS file systems] | Sustained speed at which file servers hosting the FSx file system can process data. | No |
| Throughput per unit of storage [Applies only to FSx for Lustre file systems with the Persistent deployment type] | Read/write throughput for each 1 TiB of provisioned storage, in MB/s/TiB. | No |
| IOPS | Maximum number of input/output operations per second that the FSx file system can process. | No |
| Provisioned Metadata IOPS [Applies only to FSx for Lustre file systems] | Maximum rate of metadata operations supported by the FSx file system. | No |
| Volume properties [Applies only to FSx for OpenZFS file systems] | Properties of the FSx file system configured to manage its root volume storage. | No |
| Provisioned SSD IOPS [Applies only to FSx for Windows File Server file systems] | Additional IOPS provisioned to the FSx file system. | No |
| Data compression type [Applies only to FSx for Lustre file systems] | Defines whether the FSx file system data is compressed. | No |
| Windows authentication [Applies only to FSx for Windows File Server file systems] | Type of an Microsoft Active Directory to which the FSx file system is joined. | No |
| Active Directory domain name [Applies only to FSx for Windows File Server file systems] | Domain name of the Microsoft AD to which the FSx file system is joined. | Yes |
| DNS server IP addresses [Applies only to FSx for Windows File Server file systems] | IPv4 addresses of DNS servers configured for the domain. | Yes |
| Service account user name [Applies only to FSx for Windows File Server file systems] | Name of a service account that has access to the FSx file system. | Yes |
| Organizational unit [Applies only to FSx for Windows File Server file systems] | Path name of an organizational unit in which the FSx file system is connected. | Yes |
| System administrators group [Applies only to FSx for Windows File Server file systems] | Name of an Active Directory group that has privileges to manage the FSx file system. | Yes |
| DNS Aliases [Applies only to FSx for Windows File Server file systems] | Additional names that are used to access FSx file system data. | No |
| Root squash configuration [Applies only to FSx for Lustre file systems] | Additional layer of access control configured for the FSx file system. | No |
| Elastic Fabric Adapter (EFA) [Applies only to FSx for Lustre file systems] | EFA is a high-performance network interface to increase the performance of the FSx file system. | No |
| Tags | File systems identifiers. | No |
| VPC | VPC to which the FSx file system is connected. | Yes |
| Subnet | Subnet in which the elastic network interface of the FSx file system resides. | Yes |
| Preferred and standby subnet [Applies only to FSx for Windows File Server and FSx for OpenZFS file systems file systems] | Subnets in which the network interfaces of the primary and standby file servers reside. | Yes |
| Security groups | Security groups associated with the FSx file system. | Yes |
| Route tables [Applies only to FSx for OpenZFS file systems file systems] | Route tables associated with the subnet of the VPC to which the FSx file system is connected. | Yes |
| Encryption key | AWS KMS key that is used to encrypt the FSx file system data. | Yes |
| Backup and maintenance | Defines whether daily automatic backup is scheduled and whether a weekly maintenance window is configured for the FSx file system. | No |

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support restore of the following items:   * [For FSx for OpenZFS file systems] Copy tags to snapshots from the root volume and copy tags to backups settings * [For FSx for OpenZFS file systems with the Multi-AZ deployment type] Configured endpoint IP address ranges  * [For FSx for Windows File Server file systems] Copy tags to backups setting, file access auditing configurations and associated DNS aliases  * [For Amazon FSx for Lustre file systems] Copy tags to backups setting, CloudWatch logging configurations, and exceptions to root squash settings |

Required Ports

If you plan to protect FSx file systems, make sure that security groups associated with these file systems allow access to the following ports:

Required Ports

| File System Type | Protocol | Ports | Notes |
| Amazon FSx for Windows File Server | UPD | 53, 88, 123, 389, 464 | Requires inbound and outbound access. |
| TCP | 53, 88, 135, 389, 445, 464, 636, 3268, 3269, 5985, 9389, 49152-65535 |
| Amazon FSx for Lustre | TCP | 988, 1018-1023 | Requires inbound access. For more information on file system access control, see [AWS Documentation](https://docs.aws.amazon.com/fsx/latest/LustreGuide/limit-access-security-groups.html). |
| Amazon FSx for OpenZFS | TCP, UDP | 111, 2049, 20001-20003 | Requires inbound access. |

To learn how to authorize access to security groups, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html).

How To Protect FSx File Systems

To create an FSx backup policy, perform the following steps:

1. [Check limitations and prerequisites](aws_limitations.md#backup_fsx).
2. [Specify IAM roles to access AWS services and resources](aws_accounts_iam_roles.md).
3. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](aws_email_settings.md).
4. [Complete the Add FSx Policy wizard](aws_policies_create_fsx.md).

Related Topics

[FSx Restore](aws_restore_hiw_fsx.md)

Page updated 2026-05-22

