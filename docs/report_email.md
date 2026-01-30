---
title: "Enabling Email Reporting"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/report_email.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Enabling Email Reporting


You can set up Veeam Backup & Replication to send reports automatically by email. To do this, you must enable and configure global email notification settings in Veeam Backup & Replication. For details, see [Configuring Global Email Notification Settings](general_email_notifications.md).

In addition, you can enable and configure custom notification settings for a specific protection group or application backup policy. This may be useful if you want to change subject, notification rules or list of recipients for some reports.

Rescan Job Report

By default, after you enable and configure global email notification settings in Veeam Backup & Replication, Veeam Backup & Replication sends rescan job reports at 10:00 PM daily. Veeam Backup & Replication sends a separate report for every protection group that you configured. The report contains cumulative statistics for rescan job sessions performed within the last 24-hour period.

You can specify custom notification settings for a specific protection group. To learn more, see [Advanced Settings](protection_group_advanced.md).

Backup Policy Report

You can specify custom notification settings for a specific backup policy. To learn more, see the following sections:

* [Notification Settings](policy_oracle_rman_advanced_notifications.md) for Veeam Plug-In for Oracle RMAN
* [Notification Settings](policy_sap_hana_advanced_notifications.md) for Veeam Plug-In for SAP HANA
* [Notification Settings](policy_sap_oracle_advanced_notifications.md) for Veeam Plug-In for SAP on Oracle


