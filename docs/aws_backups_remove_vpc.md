---
title: "Removing VPC Configuration Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_vpc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing VPC Configuration Backups


The backup appliance applies the [configured retention policy settings](aws_vpc_policy_retention.md) to automatically remove VPC configuration backups and backup copies created by the VPC Configuration Backup policy. If necessary, you can also remove these backups manually — from the appliance configuration database or from the repository. Keep in mind, that:

* If a backup is removed from the repository but still exists in the appliance configuration database, you will be able to use this backup to restore the VPC configuration data.
* If a backup is removed from the appliance configuration database but still exists in the repository, you will be able to use this backup to restore the VPC configuration data — but you will first have re-add the backup repository to the backup appliance as described in section [Adding Backup Repositories Using Web UI](aws_repositories_add_ui.md).

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > VPC.
2. Select the configuration record for which you want to remove the backed-up data.

Each configuration record contains a whole set of all virtual network configuration backups created for an AWS account and an AWS Region. Note that you cannot remove individual virtual network configuration items or specific backups.

1. Click Remove and select either of the following options:

* Backups — to remove all VPC configuration backups for the selected configuration record from the backup appliance database.
* Backup Copies — to remove all VPC configuration backups of all AWS Regions within selected AWS account from the backup repository specified in the [target settings](aws_vpc_policy_add_copy.md) of the VPC Configuration Backup policy.

[![Removing VPC Configuration Backups](images/aws_vpc_backup_remove.webp)](images/aws_vpc_backup_remove.webp "Removing VPC Configuration Backups")

Page updated 2026-05-21

