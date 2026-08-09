---
title: "Notification Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_advanced_notify_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Notification Settings


You can specify notification settings for Veeam Agent backup jobs configured in Veeam Backup & Replication. To specify notification settings:

1. At the Storage step of the wizard, click Change default advanced settings and open the Notifications tab.
2. Turn on the Send SNMP notifications for this job toggle if you want to receive SNMP traps when the job completes successfully.

SNMP traps will be sent if you specify global SNMP settings in Veeam Backup & Replication and configure software on recipient's machine to receive SNMP traps. For more information, see [Specifying SNMP Settings](snmp_settings.md).

1. Turn on the Send email notifications to the following recipients toggle if you want to receive notifications about the job completion status by email. In the field below, specify a recipient’s email address. You can enter several addresses separated by a semicolon.

Email notifications will be sent if you configure global email notification settings in Veeam Backup & Replication. For more information, see [Configuring Global Email Notification Settings](general_email_notifications.md).

1. Choose to use global notification settings or specify custom notification settings.

* To receive a typical notification for the job, select Use global notification settings. In this case, Veeam Backup & Replication will apply to the job global email notification settings specified for the backup server.
* To configure a custom notification for the job, select Use custom notification settings specified below. You can specify the following notification settings:

* In the Subject field, specify a notification subject. You can use the following variables in the subject: %Time% (completion time), %JobName%, %JobResult%, %ObjectCount% (number of machines in the job) and %Issues% (number of machines in the job that have been processed with the Warning or Failed status).
* Select the Notify on success, Notify on warning or Notify on error check boxes to receive email notification if the job completes successfully, completes with a warning or fails.
* Select the Suppress notifications until the last retry check box to receive a notification about the final job status. If you do not enable this option, Veeam Backup & Replication will send one notification per every job retry.

[![Specify Notification Settings for Veeam Agent Backup Job](images/agent_job_settings_notify_web.webp)](images/agent_job_settings_notify_web.webp "Specify Notification Settings for Veeam Agent Backup Job")

Page updated 2026-07-15

