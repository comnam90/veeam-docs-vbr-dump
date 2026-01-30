---
title: "Notification Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_advanced_notify_hv_web.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Notification Settings


To specify notification settings for the backup job:

1. At the Storage step of the wizard, click Advanced job settings.
2. Click the Notifications tab.
3. Select the Send SNMP notifications for this job check box if you want to receive SNMP traps when the job completes successfully.

SNMP traps will be sent if you specify global SNMP settings in Veeam Backup & Replication and configure software on the recipient's machine to receive SNMP traps. For more information, see [Specifying SNMP Settings](snmp_settings.md).

1. Select the Send email notifications to the following recipients check box if you want to receive notifications about the job completion status by email. In the field under the check box, specify the recipient’s email address. You can enter several addresses separated by a semicolon.

Email notifications will be sent if you configure global email notification settings in Veeam Backup & Replication. For more information, see [Configuring Global Email Notification Settings](general_email_notifications.md).

1. You can choose to use global notification settings or specify custom notification settings.

+ To receive a typical notification for the job, select Use global notification settings. In this case, Veeam Backup & Replication will apply to the job global email notification settings specified for the backup server. For more information, see [Configuring Global Email Notification Settings](general_email_notifications.md).
+ To configure a custom notification for the job, select Use custom notification settings specified below check box. You can specify the following notification settings:

1. In the Subject field, specify a notification subject. You can use the following variables in the subject: %Time% (completion time), %JobName%, %JobResult%, %VmCount% (number of VMs in the job) and %Issues% (number of VMs in the job that have been processed with the Warning or Failed status).

1. Select the Notify on success, Notify on warning and Notify on error check boxes to receive email notification if the job completes successfully, fails, or completes with a warning.

1. Select the Suppress notifications until the last retry check box to receive a notification about the final job status. If you do not enable this option, Veeam Backup & Replication will send one notification per every job retry.

[![Click to zoom in](images/hv_backup_job_settings_notify_web.webp)](images/hv_backup_job_settings_notify_web.webp "Click to zoom in")


