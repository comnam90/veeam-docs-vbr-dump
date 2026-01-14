---
title: "Viewing Backup Policy Statistics"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_report_backup_job_stats.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Viewing Backup Policy Statistics

In this article

You can view statistics about application backup policies configured in Veeam Backup & Replication. Veeam Backup & Replication displays statistics in the following way:

After the application backup policy session statistics becomes available in Veeam Backup & Replication, this statistics appears in the policy statistics window. The policy session statistics becomes available in Veeam Backup & Replication on real-time basis.

|  |
| --- |
| TIP |
| In addition to backup policy statistics, Veeam Backup & Replication displays log backup statistics for each replica in the backup policy. You can view these statistics in the Last 24 Hours node of the Home view and in the History view of the Veeam backup console. |

To view application backup policy statistics:

1. Open the Home view.
2. In the inventory pane, click the Jobs node.
3. In the working area, select the necessary statistics:

* To get statistics for data backup, double-click the necessary application backup policy. Alternatively, you can select the necessary application backup policy and click Statistics > Instance backup on the ribbon or right-click the backup policy and select Statistics > Instance backup.
* To get statistics for oplog backup, select the necessary application backup policy and click Statistics > MongoDB oplog backup on the ribbon or right-click the backup policy and select Statistics > MongoDB oplog backup.

[![View Backup Statistics](images/mongo_policy_statistics.webp)](images/mongo_policy_statistics.webp "View Backup Statistics")

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
