---
title: "Protecting Redshift Serverless"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_overview_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting Redshift Serverless


Veeam Plug-in for AWS allows you to create cloud-native backups of Redshift Serverless namespaces and store them in the source AWS Region. An Amazon Redshift Serverless backup captures the data of the processed Redshift Serverless namespace and its associated workgroup at a specific point of time. Redshift Serverless backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/redshift/latest/mgmt/serverless-snapshots-recovery-points.html).

To protect Redshift Serverless namespaces, backup appliances run backup policies. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, when to start the backup process, how to retain restore points, and so on. During every backup session, a backup appliance creates a cloud-native backup for each namespace added to a backup policy. For more information on how Redshift Serverless namespaces backup works, see [Redshift Serverless Backup](aws_backup_hiw_redshift_serverless.md).

Veeam Plug-in for AWS does not install agent software inside instances to back up Redshift Serverless namespaces — it uses native AWS capabilities instead. During every backup session, the backup appliance creates a cloud-native backup for each namespace added to a backup policy. For more information on how Redshift Serverless namespaces backup works, see [Redshift Serverless Backup](aws_backup_hiw_redshift_serverless.md).

Supported Redshift Serverless Properties

Veeam Plug-in for AWS allows you to back up and restore the following Redshift Serverless properties:

Supported Redshift Serverless Properties

| Property | Description | Ability to Change Property During Restore to New Location |
| Namespace name | Name of a Redshift Serverless namespace. | Yes |
| Workgroup name | Name of a workgroup associated with the Redshift Serverless namespace. | Yes |
| Base capacity and maximum capacity | Basic and maximum amount of compute resources allocated to the workgroup. | Yes |
| Associated IAM roles | List of IAM roles associated with the Redshift Serverless namespace. | Yes |
| Default role ARN | ARN of the default IAM role associated with the Redshift Serverless namespace. | Yes |
| Admin password | Defines whether the admin password is managed by AWS Secrets Manager. | * Yes (if the admin password is entered manually or generated automatically by Amazon Redshift) * No (if the admin password is managed by AWS Secrets Manager) |
| Secret Manager KMS key ID | ID of the custom KMS key used to encrypt the secret. | Yes |
| VPC | VPC where the Redshift Serverless namespace is deployed. | Yes |
| Subnets | Subnet associated with the Redshift Serverless namespace. | Yes |
| Security group | Security groups associated with the Redshift Serverless namespace. | Yes |
| Public access | Defines whether the Redshift Serverless namespace is accessible outside the VPC in which the namespace is deployed. | Yes |
| Enhanced VPC routing | Defines whether network traffic is routed between the Redshift Serverless namespace and the data repositories through a Redshift-managed VPC endpoint. | No |
| Database name | Name of the initial database in the Redshift Serverless environment. | No |
| Database port | Port used to access the Redshift Serverless namespace. | Yes |
| Encryption key | AWS KMS key that is used to encrypt the Redshift Serverless namespace data. | Yes |
| Tags | User-defined labels assigned to the Redshift Serverless namespace. | No |

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support the following:   * Audit logging for Amazon Redshift Serverless * Configured resource policies, automatically optimized price-performance targets, backup copy settings and Redshift-managed VPC endpoints  * Elastic IP assigned to the network interfaces of Redshift Serverless namespaces |

How To Protect Redshift Serverless

To create a Redshift Serverless policy, perform the following steps:

1. [Check limitations and prerequisites](aws_limitations.md#backup_redshift_serverless).
2. [Specify IAM roles to access AWS services and resources](aws_accounts_iam_roles.md).
3. [[Optional] Configure global retention settings for obsolete session records](aws_retention_settings.md#sessions).
4. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](aws_email_settings.md).
5. [Complete the Add Redshift Serverless Policy wizard](aws_policies_create_redshift_serverless.md).

Related Topics

[Redshift Serverless Restore](aws_restore_hiw_redshift_serverless.md)

Page updated 2026-05-15

