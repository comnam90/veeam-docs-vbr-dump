---
title: "Protecting DynamoDB Tables"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_overview_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting DynamoDB Tables


With Veeam Plug-in for AWS, you can perform the following operations to protect DynamoDB tables:

* Create cloud-native backups of DynamoDB tables and store them in any backup vault in the source AWS Region.

An Amazon DynamoDB backup captures the whole image of the DynamoDB table at a specific point of time. DynamoDB backups are taken using native [AWS capabilities](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CreateBackupAWS.html).

* Create backup copies of DynamoDB tables and store them in any AWS Region within the same AWS account.

By default, DynamoDB backups are stored only in the AWS Region where the processed resources reside. For enhanced data safety, you can instruct a backup appliance to create copies of these backups and store them in any other AWS Region within the same AWS account.

To protect DynamoDB tables, the backup appliance runs backup policies. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, how to retain restore points, and so on.

Veeam Plug-in for AWS does not install agent software inside instances to back up DynamoDB tables — it uses native AWS capabilities instead. During every backup session, the backup appliance creates a cloud-native backup for each table added to a backup policy. The cloud-native backup is further used to create a backup copy in another AWS Region. For more information on how DynamoDB table backup works, see [DynamoDB Backup](aws_backup_hiw_dynamo.md).

Supported DynamoDB Table Properties

Veeam Plug-in for AWS allows you to back up and restore the following table properties:

Supported DynamoDB Table Properties

| Property | Description | Ability to Change Property During Restore to New Location |
| Table name | Name of a DynamoDB table. | Yes |
| Partition key | First attribute of the primary key. | No |
| Sort key | Second attribute of the primary key. | No |
| Global secondary index (GSI) and local secondary index (LSI) | Additional indexes that provide efficient access to the table data. | No |
| Table class | Defines how often the table data is accessed. | Yes |
| Capacity mode | Defines how read/write operations are charged and managed. | Yes |
| Provisioned read/write capacity units | Read/write throughput for the table and its indexes. | Yes |
| Maximum throughput capacity | Maximum read/write throughput for the on-demand table. | No |
| Tags | Table identifiers. | No |
| Deletion protection | Defines whether the table is protected against accidental deletion. | Yes |
| Server-side encryption | Defines the key used for data-at-rest encryption. | Yes |
| Point-in-time recovery (PITR) | Defines whether the table data can be restored to any point in time during the last 35 days. | Yes |
| DynamoDB Time to Live (TTL) | Attribute name with a timestamp that determines when the table items are no longer needed. | No |

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support the following:   * CloudWatch alarms * Resource-based policies * DynamoDB global table feature * Adjusted provisioned throughput capacity provided by Amazon DynamoDB auto scaling * Item-level modifications captured by Amazon Kinesis Data Streams * Time-ordered sequences of item-level modifications captured by Amazon DynamoDB Streams * Restore of the configured CloudWatch Contributor Insights diagnostic tool |

How To Protect DynamoDB Tables

To create a DynamoDB policy, perform the following steps:

1. [Check limitations and prerequisites](aws_limitations.md#backup_dynamo).
2. [Specify IAM roles to access AWS services and resources](aws_accounts_iam_roles.md).
3. [[Optional] Configure global retention settings for obsolete session records](aws_retention_settings.md#sessions).
4. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](aws_email_settings.md).
5. [Complete the Add DynamoDB Policy wizard](aws_policies_create_dynamo.md).

Related Topics

[DynamoDB Restore](aws_restore_hiw_dynamodb.md)

Page updated 2026-05-15

