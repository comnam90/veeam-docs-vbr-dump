---
title: "Removing FSx Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_fsx.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing FSx Backups


The backup appliance applies the [configured retention policy settings](aws_add_policy_schedule_retention_fsx.md) to automatically remove FSx file system backups and backup copies created by backup policies. If necessary, you can also remove the backed-up data manually.

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > File Systems > FSx.
2. Select FSx file systems whose data you want to remove.
3. Click Remove and select either of the following options:

* Backups — to remove FSx backups created for the selected file systems by backup policies.
* Backup Copies — to remove backup copies created for the selected file systems by backup policies.
* Manual Backups — to remove FSx backups created for the selected file systems manually.

If you want to remove only specific manual backup, follow the instructions provided in section [Removing FSx Backups Created Manually](aws_backups_remove_individual_fsx.md).

* All — to remove all backups and backup copies created for the selected file systems both by backup policies and manually.

[![Removing FSx Backups](images/aws_remove_backups_fsx.webp)](images/aws_remove_backups_fsx.webp "Removing FSx Backups")

Page updated 2026-05-21

