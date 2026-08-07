---
title: "VPC Configuration Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_hiw_vpc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VPC Configuration Backup


A backup appliance performs VPC configuration backup in the following way:

1. Sends API requests to AWS to retrieve the VPC configuration data, and saves this data in the appliance configuration database.

To back up VPC configurations of AWS Regions added to backup policies, the backup appliance uses permissions of IAM roles specified either in the [organization settings](aws_organization_add_settings.md) or in the backup policy settings. The VPC configuration data is collected for the selected AWS Regions in the AWS accounts or AWS Organizations to which the specified IAM roles belong.

1. The backup appliance creates a configuration record for each pair of the AWS account and an AWS Region whose VPC configuration data is being backed up. Every time the VPC Configuration Backup policy runs, the backup appliance updates the record to create a new restore point for the VPC configurations. For more information, see [VPC Configuration Backup Chain](aws_backup_chain_vpc.md).

1. If you [enable additional backup copy](aws_vpc_policy_add_copy.md) for the VPC Configuration Backup policy, the backup appliance launches the Veeam Data Mover service on the backup appliance to copy restore points to the target backup repository, creating an individual folder for each AWS account whose VPC configuration data is protected by the policy.

Related Topics

* [Backup Chain](aws_backup_chain_vpc.md)
* [VPC Configuration Backup Retention](aws_retention_backup_vpc.md)

Page updated 2026-05-21

