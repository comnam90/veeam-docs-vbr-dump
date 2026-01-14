---
title: "Viewing SQL Server Transaction Log Backup Report"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_reporting_logs_report.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Viewing SQL Server Transaction Log Backup Report

In this article

If you configure a backup job or backup policy to back up Microsoft SQL Server transaction logs, you can generate a report with details about the SQL Server transaction log backup job session performed on protected computers. For more information about backup of Microsoft SQL Server transaction logs, see [Microsoft SQL Server Transaction Log Settings](agent_job_vss_sql.md).

To generate the SQL Server transaction log backup report, do the following:

1. Open the Home view.
2. In the inventory pane, click the Jobs node.
3. In the working area, select the necessary backup job or backup policy and click Report > SQL Server log backup on the ribbon. Alternatively, you can right-click the backup job or backup policy and select Report > SQL Server log backup.

The report contains data on the latest SQL Server transaction log backup job session:

* Cumulative session statistics: number of processed databases, details on session performance, size of backed-up data, compression ratio, backup job session status.
* Detailed statistics for every computer processed within the session: session performance, amount of read and transferred data, list of warnings and errors (if any).
* Statistics for processed SQL databases: processing duration details, number of processed databases, amount of read and transferred data, list of warnings and errors (if any).

|  |
| --- |
| TIP |
| [For Veeam Agent backup jobs] If you set up Veeam Backup & Replication to send reports automatically by email, SQL Server transaction log backup reports is sent to the specified email address after each transaction log backup job session. For more information about email notifications, see [Enabling Email Reporting](agents_reporting_email.md). |

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
