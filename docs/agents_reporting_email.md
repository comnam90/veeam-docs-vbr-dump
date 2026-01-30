---
title: "Enabling Email Reporting"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_reporting_email.html"
last_updated: "8/5/2025"
product_version: "13.0.1.1071"
---

# Enabling Email Reporting


You can set up Veeam Backup & Replication to send reports automatically by email. To do this, you must enable and configure global email notification settings in Veeam Backup & Replication. To learn more, see [Configuring Global Email Notification Settings](general_email_notifications.md).

In addition, you can enable and configure custom notification settings for a specific protection group, Veeam Agent backup job or backup policy. This may be useful if you want to change subject, notification rules or list of recipients for some reports.

Rescan Job Report

By default, after you enable and configure global email notification settings in Veeam Backup & Replication, Veeam Backup & Replication sends rescan job reports at 10:00 PM daily. Veeam Backup & Replication sends a separate report for every protection group that you configured. The report contains cumulative statistics for rescan job sessions performed within the last 24-hour period.

You can specify custom notification settings for a specific protection group. To learn more, see [Notification Settings](agents_protection_group_advanced_notify.md).

Veeam Agent Backup Job Report

By default, after you enable and configure global email notification settings in Veeam Backup & Replication, Veeam Backup & Replication sends an email notification after every backup job session completes.

You can specify custom notification settings for a specific Veeam Agent backup job. To learn more, see the following sections:

* [Notification Settings for Veeam Agent Backup Job](agent_job_advanced_notify.md) (for Microsoft Windows computers)
* [Notification Settings for Veeam Agent Backup Job](agent_advanced_notifiy_linux.md) (for Linux computers)

Backup Policy Report

By default, after you enable and configure global email notification settings in Veeam Backup & Replication, Veeam Backup & Replication sends backup policy reports at 10:00 AM daily. Veeam Backup & Replication sends a separate report for every backup policy that you configured. The report contains cumulative statistics for backup job sessions performed for the last 24-hour period on computers to which the backup policy is applied.

You can specify custom notification settings for a specific backup policy. To learn more, see the following sections:

* [Notification Settings for Backup Policy](agent_policy_advanced_notify.md) (for Microsoft Windows computers)
* [Notification Settings for Backup Policy](agent_policy_advanced_notify.md) (for Linux computers)
* [Notification Settings for Backup Policy](agent_policy_advanced_notify_unix.md) (for Unix computers)
* [Notification Settings for Backup Policy](agent_policy_advanced_notify_mac.md) (for macOS computers)


