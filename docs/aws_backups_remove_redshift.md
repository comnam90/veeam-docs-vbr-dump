---
title: "Removing Redshift Clusters Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Redshift Clusters Backups


the backup appliance applies the [configured retention policy settings](aws_add_policy_schedule_retention_redshift.md) to automatically remove Redshift backups created by backup policies. If necessary, you can also remove the backed-up data manually.

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > Databases > Redshift.
2. Select Redshift cluster whose data you want to remove.
3. Click Remove and select either of the following options:

* Backups — to remove Redshift backups created for the selected cluster by backup policies.
* Manual Backups — to remove Redshift backups created for the selected cluster manually.

If you want to remove only specific manual backup, follow the instructions provided in section [Removing Redshift Backups Created Manually](aws_backups_remove_individual_redshift.md).

* All — to remove all backups created for the selected clusters both by backup policies and manually.

[![Removing Redshift Backups](images/aws_remove_backups_redshift.webp)](images/aws_remove_backups_redshift.webp "Removing Redshift Backups")

Page updated 2026-05-21

