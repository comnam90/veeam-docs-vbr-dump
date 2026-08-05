---
title: "Removing Redshift Serverless Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Redshift Serverless Backups


The backup appliance applies the [configured retention policy settings](aws_add_policy_schedule_retention_redshift_serverless.md) to automatically remove cloud-native backups created by backup policies. If necessary, you can also remove the backed-up data manually.

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > Databases > Redshift Serverless.
2. Select Redshift Serverless namespace whose data you want to remove.
3. Click Remove and select either of the following options:

* Backups — to remove cloud-native backups created for the selected Redshift Serverless namespace by backup policies.
* Manual Backups — to remove cloud-native backups created for the selected Redshift Serverless namespace manually.

If you want to remove only specific manual cloud-native backups, follow the instructions provided in section [Removing Redshift Serverless Backups Created Manually](aws_backups_remove_individual_redshift_serverless.md).

* All — to remove all cloud-native backups created for the selected Redshift Serverless namespaces both by backup policies and manually.

[![Removing Redshift Serverless Snapshots](images/aws_remove_backups_redshift_serverless.webp)](images/aws_remove_backups_redshift_serverless.webp "Removing Redshift Serverless Snapshots")

Page updated 2026-05-21

