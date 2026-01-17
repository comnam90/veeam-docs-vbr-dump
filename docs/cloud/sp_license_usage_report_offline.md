---
title: "Manual License Usage Reporting"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/sp_license_usage_report_offline.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

When license auto update is disabled for the Veeam Cloud Connect license or Rental Veeam Backup & Replication license, Veeam Backup & Replication performs license usage reporting in the following way:

1. On the first day of the new month (at 12:00 AM GMT), Veeam Backup & Replication generates a report based on the current license usage. The report is saved to the Reports subfolder in the log folder on the Veeam backup server. The default path to the folder is %ProgramData%\Veeam\Backup\Reports.

If the SP configured email notification settings, Veeam Backup & Replication will also send the report to an email address specified there. To learn more, see the [Configuring Global Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/general_email_notifications.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| Consider the following:   * [For the Rental Veeam Backup & Replication license] If the backup server is connected to Veeam Backup Enterprise Manager that is deployed on a dedicated server, the report is saved to the log folder on the Veeam Backup Enterprise Manager server. The default path to the folder is %ProgramData%\Veeam\Backup\Reports. * You can change the default path to the log folder with a registry key. For more information, contact [Veeam Customer Support](https://www.veeam.com/support.html). After you change the default path, license usage reports will be saved to the new path.  * If the SP uses Veeam Service Provider Console to manage the Veeam backup infrastructure, they collect license usage reports in Veeam Service Provider Console. For more information, see [Veeam Rental Licensing and Usage Reporting Guide](https://helpcenter.veeam.com/docs/vcsp/refguide/about.html). |

1. Veeam Backup & Replication informs the SP about the generated report with the notification window in the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| If the SP uses Veeam Service Provider Console to manage the Veeam backup infrastructure, the notification window in the Veeam Backup & Replication console on the first day of the month will not be displayed. |

1. The SP can review, adjust if necessary and save the report locally for future submission. To learn more, see [Managing License Usage Reports](sp_license_usage_manage.md).

|  |
| --- |
| Important |
| In case of manual reporting, Veeam Backup & Replication does not automatically send monthly license usage reports. The SP must send the report to Veeam before the day defined by the agreement with Veeam or the Aggregator (if any is involved). The default day is the tenth day of the month. |

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
