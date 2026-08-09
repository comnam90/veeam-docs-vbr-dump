---
title: "Step 2. Select AWS Regions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_vpc_policy_regions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select AWS Regions


At the Regions step of the wizard, select AWS Regions whose VPC configuration you want to back up.

The backup appliance allows you to automatically collect and back up VPC configuration data for all AWS Regions selected for EC2, RDS, DynamoDB, Redshift Clusters, Redshift Serverless, EFS and FSx backup policies. To do that, [enable automatic protection](aws_vpc_policy_regions_automatic.md) for AWS Regions. To retrieve VPC configurations of all automatically protected AWS Regions, the backup appliance will use the permissions of IAM roles specified either in the [organization settings](aws_organization_add_settings.md) (if you back up resources within an AWS Organization), or in the backup policy settings (if you back up resources belonging to an AWS account).

You can also configure the VPC Configuration Backup policy to protect configuration data for AWS Regions that are not specified in the settings of any backup policy, or choose another IAM role whose permissions the backup appliance will use to collect the VPC configuration data of the automatically protected AWS Regions. To do that, [manually add AWS Regions](aws_vpc_policy_regions_manual.md) to the VPC Backup policy and configure backup settings for them.

Page updated 2026-05-21

