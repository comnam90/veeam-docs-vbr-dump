---
title: "Removing Redshift Clusters Backups Created Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_individual_redshift.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing Redshift Clusters Backups Created Manually


To remove all backups created for a Redshift cluster manually, follow the instructions provided in the
[Removing Redshift Backups](aws_backups_remove_redshift.md)
section. If you want to remove a specific Redshift backup created manually, do the following:

1. Navigate to
   Protected Data
    >
   Databases
    >
   Redshift
   .
2. Select the necessary cluster, and click the link in the
   Restore Points
    column.
3. In the
   Available Restore Points
    window, select a backup that you want to remove, and click
   Remove Manual Backup
   .

[![Removing Redshift Backups Created Manually](images/aws_remove_manual_points_redshift.webp)](images/aws_remove_manual_points_redshift.webp "Removing Redshift Backups Created Manually")

Related Topics

* [Creating Redshift Backups Manually](aws_backup_manual_redshift.md)
* [Removing Redshift Backups](aws_backups_remove_redshift.md)

Page updated 2025-09-26

