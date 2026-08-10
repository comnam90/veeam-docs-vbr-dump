---
title: "Step 5. Specify Email Notification Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_vpc_policy_notification.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Email Notification Settings


At the Settings step of the wizard, you can specify email notification settings for the VPC Backup policy.

|  |
| --- |
| Note |
| If you want to receive daily reports and email notifications on the VPC Configuration Backup policy results, you must configure [global notification settings](aws_email_settings.md) first. |

To instruct the backup appliance to send email notifications for the backup policy, do the following:

1. In the Notifications section, set the Receive daily report toggle to On.

1. In the Email field, specify an email address of a recipient.

Use a semicolon to separate multiple recipient addresses. Do not use spaces after semicolons between the specified email addresses.

1. Use the Notify on list to choose whether you want the backup appliance to send email notifications in case the backup policy completes successfully, completes with warnings or completes with errors.

|  |
| --- |
| Note |
| If you specify the same email recipient in both backup policy notification and [global notification settings](aws_email_settings.md), the backup appliance will override the configured global notification settings and will send each notification to this recipient only once to avoid notification duplicates. |

[![Editing VPC Configuration Backup Policy](images/aws_vpc_policy_notifications.webp)](images/aws_vpc_policy_notifications.webp "Editing VPC Configuration Backup Policy")

Page updated 2026-05-21

