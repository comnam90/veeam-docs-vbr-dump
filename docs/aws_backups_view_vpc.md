---
title: "VPC Configuration Data"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_view_vpc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VPC Configuration Data


After the VPC Configuration Backup policy successfully creates a restore point for the VPC configuration of an AWS Region within an AWS account, the configuration record is automatically added to the resource list on the Protected Data page.

For each protected AWS Region within the AWS account, the backup appliance creates a configuration record in the database with the following set of properties:

* AWS Account — the AWS account whose IAM role was used to collect VPC configuration data.

* Organization — the name of the AWS Organization whose AWS account was used to collect VPC configuration data.

* Region — the AWS Region whose VPC configuration data is backed up.
* Latest Backup — the date and time of the latest created restore point.
* Latest Changes — the summary of changes in the VPC configuration in comparison with the previous restore point.
* Restore Points — the total number of restore points created for the VPC configuration.

On the Protected Data page, you can perform the following actions:

* Compare the attributes of the current VPC configuration with the attributes stored in a backup. For more information, see [Comparing VPC Configuration Backups](aws_backups_compare_vpc.md).
* Export the backed-up VPC configuration data to an AWS CloudFormation template. For more information, see [Exporting VPC Configuration](aws_export_vpc.md).
* Remove restore points if you no longer need them. For more information, see [Removing VPC Configuration Backups](aws_backups_remove_vpc.md).

* Restore data of backed-up VPC configurations. For more information, see [VPC Configuration Restore Using Web UI](aws_vpc_restore_ui.md).

[![Managing Backed-Up VPC Configuration Data](images/aws_vpc_config_details.webp)](images/aws_vpc_config_details.webp "Managing Backed-Up VPC Configuration Data")

Page updated 2026-05-21

