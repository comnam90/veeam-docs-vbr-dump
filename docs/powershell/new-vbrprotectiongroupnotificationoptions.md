---
title: "New-VBRProtectionGroupNotificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrprotectiongroupnotificationoptions.html"
last_updated: "8/6/2025"
product_version: "13.0.1.1071"
---

# New-VBRProtectionGroupNotificationOptions

In this article

Short Description

Creates notification options for protection groups.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRProtectionGroupNotificationOptions [-EnableAdditionalNotification] [-SendTime <timespan>] [-AdditionalAddress <string[]>] [-UseNotificationOptions] [-NotificationSubject <string>] [-NotifyOnSuccess] [-NotifyOnWarning] [-NotifyOnError]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRProtectionGroupNotificationOptions](vbrprotectiongroupnotificationoptions.md) object. This object contains notification options for protection groups.

|  |
| --- |
| Important |
| Email notification can be configured for the protection groups only in case the global email notifications are enabled. Note that you cannot enable the global email notifications with Veeam PowerShell. To learn more about notification settings, see the [Specifying Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/email_notification_settings.html?ver=13) section in the Veeam Backup & Replication User Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EnableAdditionalNotification | Enables custom email notifications for the protection group.  Default: Disabled.  Note: You must specify at least one email address to enable custom email notifications. Use the AdditionalAddress parameter to specify the email address. | SwitchParameter | False | Named | False |
| SendTime | Specifies the time when notifications will be sent. | Timespan | False | Named | False |
| AdditionalAddress | Specifies an array of email addresses. Veeam Backup & Replication will send notifications to this email address. | String[] | False | Named | False |
| UseNotificationOptions | Enables custom notification setting.  Use the following parameters to set the custom settings:   * NotifyOnSuccess * NotifyOnWarning * NotifyOnError   Default: Disabled. | SwitchParameter | False | Named | False |
| NotificationSubject | Specifies the subject for the email notifications. | String | False | Named | False |
| NotifyOnSuccess | Defines that an email will be sent if the job finishes successfully. | SwitchParameter | False | Named | False |
| NotifyOnWarning | Defines that an email will be sent if the job finishes with warning. | SwitchParameter | False | Named | False |
| NotifyOnError | Defines that an email will be sent if the job finishes with error. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroupNotificationOptions](vbrprotectiongroupnotificationoptions.md)

Examples

Creating Notification Options for Protection Group

The example shows how to create notifications options for the protection group. Veeam Backup & Replication will send notifications at 5:00 PM. Save the result to the $options variable to use it when you create a protection group and to get it in case you need to modify notification options.

|  |
| --- |
| $options = New-VBRProtectionGroupNotificationOptions -EnableAdditionalNotification -AdditionalAddress admin@domain.com -SendTime 05:00 |

Page updated 8/6/2025

Page content applies to build 13.0.1.1071
