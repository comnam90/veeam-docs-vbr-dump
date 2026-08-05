---
title: "Performing RDS Instance Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_performing_rds_resource_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing RDS Instance Restore


In case of a disaster, you can restore a DB instance or an Aurora DB cluster from a cloud-native snapshot or snapshot replica. Veeam Plug-in for AWS allows you to restore one or more RDS resources at a time, to the original location or to a new location.

|  |
| --- |
| Important |
| * When restoring Aurora DB clusters that are part of an Amazon Aurora global database, backup appliances restore only the primary clusters in the primary AWS Region. Secondary clusters must be created manually in the AWS Management Console after the restore operation completes.   For more information on Amazon Aurora Global Database feature, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html).   * When restoring Aurora DB clusters to a new location, backup appliances create only primary DB instances in the restored clusters. Additional writer DB instances (for Aurora multi-master clusters) or Aurora Replicas (for Aurora DB clusters with single-master replication) must be added manually in the AWS Management Console after the restore operation completes.   To learn how to add DB instances to Amazon Aurora DB clusters, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-replicas-adding.html).   * Veeam Plug-in for AWS does not support restoring RDS resources to the original location if the IAM role specified for the restore operation belongs to an AWS account that differs from the AWS account to which the source resources belong. * Veeam Plug-in for AWS does not support restoring RDS resources to the original location if deletion protection is enabled for the source resource. |

To restore a protected RDS resource, do the following:

1. [Launch the RDS Restore wizard](aws_restore_rds_launch.md).
2. [Select a restore point](aws_restore_rds_point.md).
3. [Specify account settings for restore](aws_restore_rds_account.md).
4. [Choose a restore mode](aws_restore_rds_mode.md).
5. [Enable encryption](aws_restore_rds_encryption.md).
6. [Configure RDS resource settings](aws_restore_rds_settings.md).
7. [Configure network settings](aws_restore_rds_network.md).
8. [Specify a restore reason](aws_restore_rds_reason.md).
9. [Finish working with the wizard](aws_restore_rds_finish.md).

Page updated 2026-05-22

