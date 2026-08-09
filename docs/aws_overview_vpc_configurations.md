---
title: "Protecting VPC Configurations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_overview_vpc_configurations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting VPC Configurations


To protect Amazon VPC configurations, Veeam Plug-in for AWS retrieves configuration data through API and saves this data to the appliance configuration database. You can also instruct backup appliances to store copies of VPC configuration backups in backup repositories. For more information on how VPC configuration backup works, see [VPC Configuration Backup](aws_backup_hiw_vpc.md).

How To Protect VPC Configurations

To configure the VPC configuration backup policy settings, perform the following steps:

1. [Check limitations and prerequisites](aws_limitations.md#backup).
2. [Specify IAM role or add custom IAM roles to access AWS services and resources](aws_accounts_iam_roles.md).
3. [Add backup repositories to save additional VPC configuration backup copies](aws_repositories.md).
4. [[Optional] Configure global retention settings for obsolete session records](aws_retention_settings.md#sessions).
5. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](aws_email_settings.md).
6. [Complete the VPC Configuration Backup wizard](aws_policies_edit_vpc.md).

Related Topics

* [Exporting VPC Configuration](aws_exporting_vpc_configuration.md)
* [VPC Configuration Restore](aws_restore_hiw_vpc.md)

Page updated 2026-05-21

