---
title: "Set-VBRProtectionGroupNotificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrprotectiongroupnotificationoptions.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Set-VBRProtectionGroupNotificationOptions

In this article

Short Description

Modifies notification options for protection groups.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRProtectionGroupNotificationOptions -NotificationOptions <VBRProtectionGroupNotificationOptions> [-EnableAdditionalNotification] [-SendTime <timespan>] [-AdditionalAddress <string[]>] [-UseNotificationOptions] [-NotificationSubject <string>] [-NotifyOnSuccess] [-NotifyOnWarning] [-NotifyOnError]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies notification options for protection groups.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| NotificationOptions | Specifies the notification options that you want to modify. | Accepts the [VBRProtectionGroupNotificationOptions](vbrprotectiongroupnotificationoptions.md) object. To get this object, run the [New-VBRProtectionGroupNotificationOptions](new-vbrprotectiongroupnotificationoptions.md) cmdlet. | True | Named | False |
| EnableAdditionalNotification | Enables custom custom email notifications for the protection group.  Default: Disabled.  Note: You must specify at least one email address to enable custom email notifications. Use the AdditionalAddress parameter to specify the email address. | SwitchParameter | False | Named | False |
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

Modifying Additional Notifications for Protection Groups

This example shows how to modify additional notifications for protection groups.

|  |
| --- |
| $options = New-VBRProtectionGroupNotificationOptions -EnableAdditionalNotification -AdditionalAddress admin@domain.com -SendTime 05:00  Set-VBRProtectionGroupNotificationOptions -NotificationOptions $options -EnableAdditionalNotification -UseNotificationOptions -NotifyOnError |

Perform the following steps:

1. Run the [New-VBRProtectionGroupNotificationOptions](new-vbrprotectiongroupnotificationoptions.md) cmdlet. Provide the EnableAdditionalNotification parameter. Specify the AdditionalAddress and SendTime parameter values. Save the result to the $options variable.
2. Run the Set-VBRProtectionGroupNotificationOptions cmdlet. Specify the following settings:

* Set the $options variable as the NotificationOptions parameter value.
* Provide the EnableAdditionalNotification parameter.
* Provide the UseNotificationOptions parameter.
* Provide the NotifyOnError parameter.

Related Commands

[New-VBRProtectionGroupNotificationOptions](new-vbrprotectiongroupnotificationoptions.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
