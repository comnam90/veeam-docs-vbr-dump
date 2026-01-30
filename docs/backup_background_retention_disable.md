---
title: "Disabling Background Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_background_retention_disable.html"
last_updated: "3/4/2025"
product_version: "13.0.1.1071"
---

# Disabling Background Retention


You can manually disable [background retention](background_retention_job.md), which is launched every 24 hours at 00:30. You can enable disabled background retention at any time.

If you turn off background retention, you will receive a daily email report reminding you that it is disabled. Veeam Backup & Replication will send these reports only after you have enabled and configured email notifications, as described in the section [Configuring Global Email Notification Settings](general_email_notifications.md).

If background retention is turned off while backup jobs are still enabled, auxiliary data cannot be cleaned from object storage repositories. This can decrease backup job performance over time.

To disable background retention:

1. Open the Home view.
2. In the inventory pane, right-click the Backups node.
3. Select Disable retention or click Disable Retention on the ribbon.

To enable disabled background retention, select the Backups node and click Disable Retention on the ribbon again. Alternatively, you can right-click the Backups node and select Disable retention.

[![Disable background retention](images/background_retention_disable.webp)](images/background_retention_disable.webp "Disable background retention")

Related Links

* [Background Retention](background_retention_job.md)
* [Launching Background Retention](backup_background_retention_launch.md)


