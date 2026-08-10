---
title: "Step 7. Configure General Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_sla_notifications.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Configure General Settings


At the Settings step of the wizard, you can enable automatic retries and specify notification settings for the SLA-based backup policy policy.

Automatic Retry Settings

To instruct the backup appliance to run a policy session again if it fails on the first try, do the following:

1. In the Session retries section of the step, select the Automatic retry failed sessions check box.
2. In the field to the right of the check box, specify the maximum number of attempts to run the policy sessions. The time interval between retries is 600 seconds.

When retrying policy sessions, the backup appliance processes only those Azure VMs that failed to be backed up during the previous attempt.

Notification Settings

To instruct the backup appliance to send email notifications for the policy, do the following:

1. In the Notifications section of the step, set the Enable notifications toggle to On.

If you set the toggle to Off, the backup appliance will not send any notifications for this backup policy — regardless of the configured [global notification settings](azure_configuring_notification_settings.md).

1. In the Email field, specify an email address of a recipient. Use a semicolon to separate multiple recipient addresses.
2. Select the Report missed SLA and removed VMs only check box if you want Veeam Backup for Microsoft Azure to send email notifications only in case the backup policy fails to meet SLA target value, or if any Azure VMs added to the policy are [considered removed](azure_sla_calculation.md#removed_vms) from Microsoft Azure.
3. Use the Send reports setting to define whether you want Veeam Backup for Microsoft Azure to send email notifications immediately after it finalizes the backup window specified for the policy in all regions added to the policy and completes calculating SLA compliance ratio, or at a specific time after Veeam Backup for Microsoft Azure finalizes the backup window specified for the policy in all regions added to the policy and completes calculating SLA compliance ratio.

|  |
| --- |
| Note |
| If you specify the same email recipient in both backup policy notification and [global notification settings](azure_configuring_notification_settings.md), the backup appliance will override the configured global notification settings and will send each notification to this recipient only once to avoid notification duplicates. |

[![Adding Backup Policy](images/azure_vm_protection_notifications.webp)](images/azure_vm_protection_notifications.webp "Adding Backup Policy")

Page updated 2026-07-01

