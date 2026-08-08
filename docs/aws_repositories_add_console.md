---
title: "Adding Backup Repositories Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_repositories_add_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Backup Repositories Using Console


Depending on whether you want to store backups in a high-performance, high-cost and short-term storage, or a secure, low-cost and long-term storage, you can configure repositories of the following storage classes:

* Standard repositories

Use repositories of the S3 Standard storage class to store data that you plan to access frequently, and the S3 Standard-IA storage class to store data that you plan to access infrequently. Backups stored in these repositories are shown under the External Repository node.

To store backups in a standard repository, first add it to the backup infrastructure and then enable image-level backups, VPC backup copy or EFS indexing in the backup policy settings. For more information, see sections [Creating EC2 Backup Policies](aws_policies_create.md), [Creating RDS Backup Policies](aws_policies_create_rds.md), [Editing VPC Configuration Backup Policy](aws_policies_edit_vpc.md) and [Creating EFS Backup Policies](aws_policies_create_efs.md).

* [Applies only to EC2 and RDS backups] Archive repositories

Use repositories of the S3 Glacier Flexible Retrieval storage class to store data that you plan to access infrequently, and the S3 Glacier Deep Archive storage class to store data that you plan to access once or twice a year. Backups stored in these repositories are shown under the External Repository (Archive) node.

To store backups in an archive repository, first add it to the backup infrastructure and then enable backup archiving for any backup policy that will store backups in this repository. For more information, see [Creating EC2 Backup Policies](aws_policies_create.md).

To learn how backup archiving works, see [Enabling Backup Archiving](aws_backup_archiving.md).

|  |
| --- |
| Important |
| Note that you can perform a limited scope of operations with archive repositories from the Veeam Backup & Replication console:   * You cannot edit and rescan archive repositories. * You can only restore [entire EC2 instances](aws_restoring_to_amazon.md) from backups stored in archive repositories. However, you can perform volume-level and file-level recovery operations from these backups using the backup appliance Web UI. For more information, see sections [Performing Volume-Level Restore](aws_restore_volume_perform.md) or [Performing File-Level Recovery](aws_restore_item_perform.md). * You can restore specific databases of PostgreSQL DB instances using the backup appliance Web UI only. For more information, see [Restoring RDS Databases](aws_rds_database_restore.md). |

For more information on Amazon S3 storage classes, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html).

How to Add Backup Repositories

After you add a backup appliance to the backup infrastructure, you can configure repositories that will be used to store backups. To do that, use either of the following options:

* [Create new repositories](aws_add_s3_repository.md).
* [Add existing repositories to the backup infrastructure](aws_connecting_existing_repository.md) if you have already configured them on the backup appliance.

Page updated 2026-07-13

