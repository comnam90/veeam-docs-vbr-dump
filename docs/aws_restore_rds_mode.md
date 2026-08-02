---
title: "Step 4. Choose Restore Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds_mode.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Choose Restore Mode


At the Restore Mode step of the wizard, choose whether you want to restore the selected RDS resources to the original or to a custom location. If you select the Restore to new location, or with different settings option, specify the target AWS Region where the restored DB instances and Aurora DB clusters will operate.

Considerations and Limitations

When you restore RDS resources, consider the following:

* When restoring Aurora DB clusters that are part of an Amazon Aurora global database, the backup appliance restores only the primary clusters in the primary AWS Region. Secondary clusters must be created manually in the AWS Management Console after the restore operation completes.

For more information on Amazon Aurora Global Database feature, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html).

* When restoring Aurora DB clusters to a new location, the backup appliance creates only primary DB instances in the restored clusters. Additional writer DB instances (for Aurora multi-master clusters) or Aurora Replicas (for Aurora DB clusters with single-master replication) must be added manually in the AWS Management Console after the restore operation completes.

To learn how to add DB instances to Amazon Aurora DB clusters, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-replicas-adding.html).

* Veeam Plug-in for AWS does not support restoring RDS resources to the original location if the IAM role specified for the restore operation belongs to an AWS account that differs from the AWS account to which the source resources belong.
* Veeam Plug-in for AWS does not support restoring RDS resources to the original location if deletion protection is enabled for the source resource.

[![Restoring RDS Resources](images/aws_rds_restore_mode.webp)](images/aws_rds_restore_mode.webp "Restoring RDS Resources")

Page updated 2026-05-22

