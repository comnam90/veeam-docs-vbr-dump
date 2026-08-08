---
title: "Removing File Share Snapshots Created Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_fs_manual_snaphots.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing File Share Snapshots Created Manually


To remove all cloud-native snapshots created for a file share manually, follow the instructions provided in [Removing File Share Snapshots](azure_removing_fs_snapshots.md). If you want to remove a specific cloud-native snapshot created manually, do the following:

1. Navigate to Protected Data > Azure Files.
2. Select the check box next to the necessary file share, and click the link in the Restore Points column.
3. In the Available Restore Points window, select the necessary snapshot and click Remove Manual Snapshot.

[![Removing File Share Snapshots Created Manually](images/azure_removing_fs_manual_snapshots.webp)](images/azure_removing_fs_manual_snapshots.webp)

Related Topics

[Creating File Share Snapshots Manually](azure_creating_fs_snapshots_manually.md)

Page updated 2025-03-14

