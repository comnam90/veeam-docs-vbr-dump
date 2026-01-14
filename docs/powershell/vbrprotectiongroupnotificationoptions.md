---
title: "VBRProtectionGroupNotificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrprotectiongroupnotificationoptions.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRProtectionGroupNotificationOptions

In this article

Contains notification options for protection groups.

Properties

| Property | Type | Description |
| --- | --- | --- |
| EnableAdditionalNotification | bool | Enables custom email notifications. |
| SendTime | TimeSpan | Time when notifications will be sent. |
| AdditionalAddress | string[] | Array of email addresses. |
| UseNotificationOptions | bool | Enables custom notification setting. |
| NotificationSubject | string | Email notifications subject. |
| NotifyOnSuccess | bool | Notifies if a job finishes successfully. |
| NotifyOnWarning | bool | Notifies if a job finishes with a warning. |
| NotifyOnError | bool | Notifies if a job finishes with an error. |

Related Commands

[New-VBRProtectionGroupNotificationOptions](new-vbrprotectiongroupnotificationoptions.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
