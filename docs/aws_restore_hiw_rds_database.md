---
title: "Database Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_rds_database.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Database Restore


To restore databases of Microsoft SQL Server and PostgreSQL DB instances from an image-level backup, a backup appliance performs the following steps:

1. [Applies only if you perform restore from an archived backup] Retrieves data from the archived restore point.
2. Deploys a worker instance in an AWS Region in which DB instance that will host the restored databases resides in an AWS account to which the instance belongs — that is, the production AWS account.

By default, the backup appliance selects the most appropriate network settings of AWS Regions in production accounts. However, you can add specific worker configurations. For more information on worker instances, see [Managing Worker Configurations](aws_worker_settings.md).

1. Creates 2 security groups that are associated with the target DB instance and worker instance to allow direct network traffic between the resources. The security group associated with the target instance allows inbound traffic through opened on the instance port only from the worker instance, whereas the security group associated with the worker instance allows outbound traffic through opened on the instance port only to the target instance.
2. [Applies only to Microsoft SQL Server DB instances] Reads data from the backup file stored in the target backup repository, transfers the data to a temporary Amazon S3 bucket in the same AWS Region in which the source DB instance resides and stores it in the native SQL Server backup format. Then, uses [native AWS capabilities](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/SQLServer.Procedural.Importing.Native.Using.html#SQLServer.Procedural.Importing.Native.Using.Restore) to restore the SQL Server databases to the specified DB instance.
3. [Applies only to PostgreSQL DB instances] Uses the worker instance to retrieve dumps, triggers and stored procedures from the backup file stored in the target backup repository. Then, uses PostgreSQL capabilities to restore the PostgreSQL databases to the specified DB instance.
4. [Applies only to Microsoft SQL Server DB instances] Removes the temporary Amazon S3 bucket from AWS if it is not currently used by any data recovery operation.
5. Removes the worker instance and 2 created security groups from AWS when the restore session completes.

To learn how to restore databases of a SQL Server DB instance from an image-level backup, see [RDS Restore](aws_rds_restore.md).

|  |
| --- |
| Note |
| Due to [AWS technical limitations](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-initialize.html), the next run of the backup policy protecting the source DB instance may take more time to complete in case the restore operation completes successfully, depending on the specified target AWS Region and target DB instance. For more information, see [Performing RDS Database Restore](aws_restore_rds_database_settings.md). |

Page updated 2026-05-15

