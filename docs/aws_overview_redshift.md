---
title: "Protecting Redshift Clusters"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_overview_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting Redshift Clusters


Veeam Plug-in for AWS allows you to create cloud-native backups of Redshift clusters and store them in any backup vault in the source AWS Region. An Amazon Redshift backup captures the whole image of the Redshift cluster at a specific point of time. Redshift backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-aws-backup.html).

To protect Redshift clusters, backup appliances run backup policies. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, how to retain restore points, and so on.

Veeam Plug-in for AWS does not install agent software inside instances to back up Redshift clusters — it uses native AWS capabilities instead. During every backup session, a backup appliance creates a cloud-native backup for each cluster added to a backup policy. For more information on how Redshift clusters backup works, see [Redshift Clusters Backup](aws_backup_hiw_redshift.md).

Supported Redshift Cluster Properties

Veeam Plug-in for AWS allows you to back up and restore the following cluster properties:

Supported Redshift Cluster Properties

| Property | Description | Ability to Change Property During Restore to New Location |
| Cluster ID | Unique identifier of the Redshift cluster. | Yes |
| Node type | Type of the nodes for the Redshift cluster. | Yes |
| Number of nodes | Total number of compute nodes for the Redshift cluster. | Yes |
| Associated IAM roles | List of IAM roles associated with the Redshift cluster. | Yes |
| Default role ARN | ARN of the default IAM role associated with the Redshift cluster. | Yes |
| Admin password | Defines whether the admin password is managed by AWS Secrets Manager. | No |
| Secret Manager KMS key ID | ID of the custom KMS key used to encrypt the secret. | Yes |
| VPC | VPC to which the Redshift cluster is connected. | Yes |
| Subnet group | Subnet group in which the Redshift cluster is launched. | Yes |
| Availability Zone | Availability Zone where the Redshift cluster resides. | Yes |
| Public access | Defines whether the Redshift cluster is accessible outside the VPC to which the cluster is connected. | Yes |
| Enhanced VPC routing | Defines whether network traffic is routed between the Redshift cluster and the data repositories through a Redshift-managed VPC endpoint. | No |
| Port | Port used to access the Redshift cluster. | Yes |
| Parameter group | Parameter group associated with the Redshift cluster. | Yes |
| Cluster relocation | Defines whether the Redshift cluster can be moved to another Availability Zone. | No |
| Encryption key | AWS KMS key that is used to encrypt the Redshift cluster data. | Yes |
| Tags | User-defined labels assigned to the Redshift cluster. | No |
| Backup and maintenance | Defines whether daily automatic backup is scheduled and whether a weekly maintenance window is configured for the Redshift cluster. | No |

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support the following:   * Multi-AZ deployment mode of Redshift clusters * HSM encryption scheme of Redshift clusters  * Elastic IP assigned to the network interfaces of Redshift clusters |

How To Protect Redshift Clusters

To create a Redshift policy, perform the following steps:

1. [Check limitations and prerequisites](aws_limitations.md#backup_redshift).
2. [Specify IAM roles to access AWS services and resources](aws_accounts_iam_roles.md).
3. [[Optional] Configure global retention settings for obsolete session records](aws_retention_settings.md#sessions).
4. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](aws_email_settings.md).
5. [Complete the Add Redshift Policy wizard](aws_policies_create_redshift.md).

Related Topics

[Redshift Restore](aws_restore_hiw_redshift.md)

Page updated 2026-05-15

