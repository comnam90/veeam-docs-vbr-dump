---
title: "Configuring Job Notification Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/job_email_notifications.html"
last_updated: "3/20/2025"
product_version: "13.0.1.1071"
---

# Configuring Job Notification Settings


To configure job notification settings:

1. Open advanced settings of the job.
2. On the Notifications tab, select the Send email notifications to the following recipients check box.
3. In the field under the Send email notifications to the following recipients check box, enter an email address to which a notification must be sent. You can enter several email addresses separated with a semicolon.

|  |
| --- |
| Important |
| If you specify the same email recipient in both job notification and global notification settings, Veeam Backup & Replication will send the job notification only. |

1. You can choose to use global notification settings for the job or specify custom notification settings.

* To receive a typical notification for the job, select Use global notification settings. In this case, Veeam Backup & Replication will apply to the job global email notification settings specified for the backup server. For more information, see [Configuring Global Email Notification Settings](general_email_notifications.md).
* To configure a custom notification for the job, select Use custom notification settings and specify notification settings as required.

1. If you want to save this set of settings as the default one, click Save as default. When you create a new job, the saved settings will be offered as the default. This also applies to all users added to the backup server.

![Configuring Job Notification Settings](images/vm_backup_job_settings_notification.webp)


