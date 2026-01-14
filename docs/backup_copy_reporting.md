---
title: "Reporting"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_reporting.html"
last_updated: "11/22/2023"
product_version: "13.0.1.1071"
---

# Reporting

In this article

The process of performing reporting operations for backup copy jobs is the same as described in the [Backup: Reporting](reporting.md) section. However, the process differs for immediate backup copy jobs created in Veeam Backup & Replication 11 the following way:

* [Viewing real-time statistics](realtime_statistics.md)

You can view real-time statistics for the whole job if you select the job in the working area of the Jobs node. The whole job report shows general information about the job itself and child jobs — tasks that copy backup jobs [added as sources](backup_copy_vms.md) to the backup copy job. You can also view real-time statistics for an individual child job if you select the child job in the working area of the Last 24 Hours or Running node. This statistics shows detailed information about the selected child job including the processed VMs.

* [Viewing job session results](session_results.md)

You select and view session results for a child job.

* [Viewing job reports](session_report.md#job)

The job report shows results for the last job run and does not provide details on child jobs. If you want to get reports once a child job finishes, configure notifications. For more information, see [Notification Settings](backup_copy_settings_notification.md).

* [Viewing session reports](session_report.md#session)

You can view session reports only if you configured notifications for a job. In this case, you get reports once a child job finishes. For more information, see [Notification Settings](backup_copy_settings_notification.md).

Page updated 11/22/2023

Page content applies to build 13.0.1.1071
