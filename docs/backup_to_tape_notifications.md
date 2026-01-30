---
title: "Notifications Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_to_tape_notifications.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Notifications Settings


At the Notifications tab, you can specify notification settings for the backup to tape job.

At the Options step of the wizard, click Advanced. Then select the Notifications tab.

Select the Send email notifications to the following recipients check box if you want to receive notifications about tape job status. In the field below, specify a recipient’s email address. You can enter several addresses separated by a semicolon.

|  |
| --- |
| Important |
| To receive notifications about tape jobs status, you must enable general email notifications in Veeam Backup & Replication. For more information, see [Specifying Email Notification Settings](email_notification_settings.md). |

You can choose between the following options:

* Use global notification settings: Veeam Backup & Replication will notify you according to global email notification settings specified for the Veeam backup server.
* Use custom notification settings specified below: you can specify notification settings for tape jobs.

In the Subject field, specify a notification subject. You can use the following variables in the subject:

+ %Time%: the time when the tape job finished.
+ %JobName%: the name of the tape job.
+ %TapeCount%: the number of tapes used for the tape job session.
+ %JobResult%: the job result.
+ %VmCount%: the number of machines in the job.
+ %Issues%: the number of machines in the job processed with Warning or Failed status.

Select the occasions on which you want to receive email notifications:

* Notify on success: Veeam Backup & Replication will notify you if the tape job finishes successfully.
* Notify on warning: Veeam Backup & Replication will notify you if the tape job finishes with a warning.
* Notify on error: Veeam Backup & Replication will notify you if the tape job fails.
* Notify when waiting for tape: Veeam Backup & Replication will notify you if the tape job cannot start because there are no available tapes.

![Notifications Settings](images/files_to_tape_advanced_notify.webp)

|  |
| --- |
| Tip |
| After you specify necessary settings for the tape job, you can save them as default settings. To do this, click Save as Default at the bottom left corner of the Advanced Settings window. When you create a new backup to tape job, Veeam Backup & Replication will automatically apply the default settings to the new job. |


