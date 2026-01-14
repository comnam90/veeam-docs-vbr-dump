---
title: "VBRNotificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnotificationoptions.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRNotificationOptions

In this article

Contains job notification options.

Properties

| Property | Type | Description |
| --- | --- | --- |
| EnableAdditionalNotification | bool | Indicates if the email notification is enabled (TRUE) or not (FALSE). |
| AdditionalAddress | string[] | The email address for notification. |
| UseNotificationOptions | bool | Indicates that the notifications must use custom settings (TRUE) or global settings (FALSE). Custom settings are:   * NotifyOnSuccess * NotifyOnWarning * NotifyOnError * NotifyOnLastRetryOnly |
| NotificationSubject | string | The subject that must be used for creating the notification email. |
| NotifyOnSuccess | bool | Indicates if the email is sent if the job finished successfully (TRUE) or not (FALSE). |
| NotifyOnWarning | bool | Indicates if the email is sent if the job finished with warning (TRUE) or not (FALSE). |
| NotifyOnError | bool | Indicates if the email is sent if the job finished with error (TRUE) or not (FALSE). |
| NotifyOnLastRetryOnly | bool | Indicates if the email is sent if the last retry of the job started (TRUE) or not (FALSE). |

Related Commands

[New-VBRNotificationOptions](new-vbrnotificationoptions.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
