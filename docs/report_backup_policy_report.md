---
title: "Viewing Backup Policy Report"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/report_backup_policy_report.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---

# Viewing Backup Policy Report

In this article

You can generate a report with details about application backup job sessions performed on protected databases added to a backup policy. The report contains data on the latest backup job session initiated for the backup policy. To generate a report:

1. Open the Home view.
2. In the inventory pane, click the Jobs node.
3. In the working area, select the necessary report:

* To get report for database data backup, click Report > Instance backup on the ribbon or right-click the backup policy and select Report > Instance backup.
* To get report for database logs backup, click Report > Database logs backup on the ribbon or right-click the backup policy and select Report > Database logs backup.

The report contains data on the latest job session:

* Cumulative session statistics: details on the number of protected databases specified in the backup policy settings, the number of databases to which settings of the backup policy are applied, and the number of disconnected databases, details of the session performance, amount of read, processed and transferred data.
* Detailed statistics for every protected database processed within the session: processing duration details, backup data size, amount of read and transferred data, list of warnings and errors (if any).

|  |
| --- |
| TIP |
| You can also set up Veeam Backup & Replication to send reports automatically by email. To learn more, see [Enabling Email Reporting](report_email.md). |

[![View Backup Policy Report](images/policy_report.webp)](images/policy_report.webp "View Backup Policy Report")

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
