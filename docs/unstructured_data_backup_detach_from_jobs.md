---
title: "Detaching Unstructured Data Backups from Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup_detach_from_jobs.html"
last_updated: "6/24/2025"
product_version: "13.0.1.1071"
---

# Detaching Unstructured Data Backups from Jobs

In this article

If you want to detach backups from a job, you can use the Detach from job operation.

The detached backup files remain in the backup repository and the Veeam Backup & Replication console. Veeam Backup & Replication shows the detached backups in the [inventory pane](vbr_ui.md) under the Disk (Orphaned) or Object Storage (Orphaned) node. These backups are retained according to the retention policy.

To detach backups from a job:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), select the Backups node.
3. In the working area, right-click the necessary backup and select Detach from job. Alternatively, click Delete from > Job on the ribbon.

Page updated 6/24/2025

Page content applies to build 13.0.1.1071
