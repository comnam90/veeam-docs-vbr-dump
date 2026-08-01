---
title: "Removing EC2 Snapshots Created Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_remove_manual_snapshots.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing EC2 Snapshots Created Manually


To remove all cloud-native snapshots created for an EC2 instance manually, follow the instructions provided in the
[Removing EC2 Backups and Snapshots](aws_backups_remove.md)
section. If you want to remove a specific snapshot created manually, do the following:

1. Navigate to
   Protected Data
    >
   EC2
   .
2. Select the necessary instance, and click the link in the
   Restore Points
    column.
3. In the
   Available Restore Points
    window, select a snapshot that you want to remove, and click
   Remove Manual Snapshot
   .

[![Removing EC2 Snapshots Created Manually](images/aws_snapshot_manual_remove_select.webp)](images/aws_snapshot_manual_remove_select.webp "Removing EC2 Snapshots Created Manually")

Related Topics

* [Creating EC2 Snapshots Manually](aws_snapshot_manual.md)
* [Removing EC2 Backups and Snapshots](aws_backups_remove.md)

Page updated 2025-09-16

