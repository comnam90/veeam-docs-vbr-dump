---
title: "Logs and Support"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_mssql_logs.html"
last_updated: "3/14/2024"
product_version: "13.0.1.1071"
---

# Logs and Support

In this article

If you have any questions or issues with Veeam Plug-In for Microsoft SQL Server or Veeam Backup & Replication, you can search for a resolution on [Veeam R&D Forums](https://forums.veeam.com/) or submit a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, we recommend that you attach logs files related to Veeam Plug-In operations.

To export Veeam Plug-In logs, do the following:

1. On the computer with Microsoft SQL Server, navigate to the %PROGRAMDATA%\Veeam\Backup\MSSQLPluginLogs directory and copy the contents of the directory.

|  |
| --- |
| Tip |
| Besides Veeam Plug-In logs, Customer Support may need additional information from the computer with Veeam Plug-In. For example, Microsoft Windows event logs or SQL Server error logs. You can run a special PowerShell script to collect all the required information. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4438). |

1. On the Veeam Backup & Replication server, navigate to the %PROGRAMDATA%\Veeam\Backup\Plugin directory and copy logs of the required backup or restore process.

Page updated 3/14/2024

Page content applies to build 13.0.1.1071
