---
title: "Set-VBRNotificationOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnotificationoptions.html"
last_updated: "4/18/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNotificationOptions


Short Description

Modifies job notification settings.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNotificationOptions [-AdditionalAddress <String[]>] [-EnableAdditionalNotification] [-EnableDailyNotification] [-EnableSnmpNotification] -NotificationOptions <VBRNotificationOptions> [-NotificationSubject <String>] [-NotifyOnError] [-NotifyOnLastRetryOnly] [-NotifyOnSuccess] [-NotifyOnWarning] [-NotifyWhenWaitingForTape] [-SendTime <TimeSpan>] [-UseNotificationOptions]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies notification settings for backup or replication jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| NotificationOptions | Specifies notification settings that you want to modify. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To get this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | True | Named | False |
| EnableAdditionalNotification | Enables the email notification option. | SwitchParameter | False | Named | False |
| AdditionalAddress | Specifies the email address for job notifications. | String[] | False | Named | False |
| UseNotificationOptions | Defines that the cmdlet will use custom or global settings. You can set it to True (custom settings) or False (global settings).  Use the following parameters to set the custom settings:   * NotifyOnSuccess * NotifyOnWarning * NotifyOnError * NotifyOnLastRetryOnly | SwitchParameter | False | Named | False |
| NotificationSubject | Specifies the subject of the email notifications. | String | False | Named | False |
| NotifyOnSuccess | Defines that the cmdlet will send the email when the job finished successfully.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnWarning | Defines that the cmdlet will send the email when the job finished with a warning.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnError | Defines that the cmdlet will send the email when the job finished with an error.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnLastRetryOnly | Defines that the cmdlet will send the email about the final job status. If you do not enable this option, Veeam Backup & Replication will send one notification per every job retry.  Default: True.  Note:   * This parameter is not available for backup policies that Veeam Agent backup jobs use to back up computers. * To disable this parameter, set the value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableSnmpNotification | Defines that the cmdlet will send the SNMP traps when the job completes successfully.  Note: This parameter is not available for the following types of jobs:   * Backup policies that Veeam Agent backup jobs use to back up computers. * Veeam Agent backup jobs. | SwitchParameter | False | Named | False |
| NotifyWhenWaitingForTape | Defines that the cmdlet will send the email if the tape job cannot start because there are no available tapes.  Note: This parameter is not available for the following types of jobs:   * Backup policies that Veeam Agent backup jobs use to back up computers. * Veaam Agent backup jobs. | SwitchParameter | False | Named | False |
| EnableDailyNotification | Defines that the cmdlet will send email notification daily.  Use the SendTime parameter to specify the time when the cmdlet must send the email notification. | SwitchParameter | False | Named | False |
| SendTime | Specifies the time when the cmdlet must send the email notification. | TimeSpan | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNotificationOptions](vbrnotificationoptions.md) object that contains job notification options.

Examples

Modifying Notification Settings for Backup Job

This example shows how to modify notification settings for the backup job. Veeam Backup & Replication will send a notification when the backup job completes with the error, warning or when it completes successfully.

|  |
| --- |
| $notifications = New-VBRNotificationOptions -EnableAdditionalNotification -AdditionalAddress "admin@domain.com" -UseNotificationOptions -NotifyOnSuccess -NotifyOnWarning  Set-VBRNotificationOptions -NotificationOptions $notifications -EnableAdditionalNotification -UseNotificationOptions -NotifyOnError |

Perform the following steps:

1. Run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. Specify the following settings:

* Provide the EnableAdditionalNofitication parameter.
* Specify the AdditionalAddress parameter value.
* Provide the UseNotificationOptions parameter.
* Provide the NotifyOnSuccess parameter.
* Provide the NotifyOnWarning parameter.

Save the result to the $notifications variable.

1. Run the Set-VBRNotificationOptions cmdlet. Specify the following settings:

* Set the $notifications variable as the NotificationOptions parameter value.
* Provide the EnableAdditionalNotification parameter.
* Provide the UseNotificationOptions parameter.
* Provide the NotifyOnError parameter.

Related Commands

[New-VBRNotificationOptions](new-vbrnotificationoptions.md)


