---
title: "Viewing Backup Policy Statistics"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/report_backup_policy_stats.html"
last_updated: "2/15/2026"
product_version: "13.0.1.1071"
---

# Viewing Backup Policy Statistics


You can view statistics about application backup policies configured in Veeam Backup & Replication. Veeam Backup & Replication displays statistics in the following way:

After the application backup policy session statistics becomes available in Veeam Backup & Replication, this statistics appears in the policy statistics window. The job session statistics becomes available in Veeam Backup & Replication on real-time basis.

|  |
| --- |
| TIP |
| In addition to backup policy statistics, Veeam Backup & Replication displays individual backup session statistics for each computer in the backup policy. You can view these statistics in the Last 24 Hours node of the Home view and in the History view of the Veeam backup console. |

To view application backup policy statistics:

1. Open the Home view.
2. In the inventory pane, click the Jobs node.
3. In the working area, select the necessary statistics:

* To get statistics for database data backup, double-click the necessary application backup policy. Alternatively, you can select the necessary application backup policy and click Statistics > Instance backup on the ribbon or right-click the backup policy and select Statistics > Instance backup.
* To get statistics for database logs backup, select the necessary application backup policy and click Statistics > Database logs backup on the ribbon or right-click the backup policy and select Statistics > Database logs backup.

[![Application Backup Policy Statistics](images/plugins_statistics_policy.webp)](images/plugins_statistics_policy.webp "Application Backup Policy Statistics")

Additional Options for Monitoring Microsoft SQL Server Application Backup Policies

When multiple objects in a database are backed up, you can use the search bar and status filters at the bottom of the statistics window to find specific object names. The search and filter options are also available in the job progress window. This functionality is available for application backup policies created with Veeam Plug-In for Microsoft SQL Server.

[![Application Backup Policy Statistics](images/plugins_statistics_policy_ms_sql.webp)](images/plugins_statistics_policy_ms_sql.webp "Application Backup Policy Statistics")


