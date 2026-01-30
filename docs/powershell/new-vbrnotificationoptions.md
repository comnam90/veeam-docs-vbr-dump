---
title: "New-VBRNotificationOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnotificationoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRNotificationOptions


Short Description

Creates new job notification options.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRNotificationOptions [-AdditionalAddress <String[]>] [-EnableAdditionalNotification] [-EnableDailyNotification] [-EnableSnmpNotification] [-NotificationSubject <String>] [-NotifyOnError] [-NotifyOnLastRetryOnly] [-NotifyOnSuccess] [-NotifyOnWarning] [-NotifyWhenWaitingForTape] [-SendTime <TimeSpan>] [-UseNotificationOptions]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRNotificationOptions](vbrnotificationoptions.md) object. This object contains email notification settings for backup or replication jobs. You can use this object later to apply these settings to a job.

|  |
| --- |
| Important |
| Email notification can be configured for jobs only in case that the global email notifications are enabled. Note that you cannot enable the global email notifications with Veeam PowerShell. For more information, see the [Configuring Global Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/general_email_notifications.html?ver=13) section of the Veeam Backup & Replication User Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EnableAdditionalNotification | Enables the email notification. You can set it to True (enabled) or False (disabled). | SwitchParameter | False | Named | False |
| AdditionalAddress | Specifies the email address for job notifications. | String | False | Named | False |
| UseNotificationOptions | Defines that the notifications must use custom or global settings. You can set it to True (custom settings) or False (global settings).  Use the following parameters to set the custom settings:   * NotifyOnSuccess * NotifyOnWarning * NotifyOnError * NotifyOnLastRetryOnly | SwitchParameter | False | Named | False |
| NotificationSubject | Specifies the subject of the email notifications. | String | False | Named | False |
| NotifyOnSuccess | Defines that the cmdlet will send the email if the job finished successfully.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnWarning | Defines that the cmdlet will send the email if the job finished with warning.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnError | Defines that the cmdlet will send the email if the job finished with error.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnLastRetryOnly | Defines that the cmdlet will send the email about the final job status. If you do not enable this option, Veeam Backup & Replication will send one notification per every job retry.  Default: True.  Note:   * This parameter is not available for backup policies that Veeam Agent backup jobs use to back up computers. * To disable this parameter, set the value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableSnmpNotification | Defines that the SNMP traps will be sent when the job completes successfully.  Note: This parameter is not available for the following types of jobs:   * Backup policies that Veeam Agent backup jobs use to back up computers. * Veeam Agent backup jobs. | SwitchParameter | False | Named | False |
| NotifyWhenWaitingForTape | Defines that the cmdlet will send the email if the tape job cannot start because there are no available tapes.  Note: This parameter is not available for the following types of jobs:   * Backup policies that Veeam Agent backup jobs use to back up computers. * Veaam Agent backup jobs. | SwitchParameter | False | Named | False |
| EnableDailyNotification | Defines that the cmdlet will send email notification daily.  Use the SendTime parameter to specify the time when the cmdlet must send the email notification. | SwitchParameter | False | Named | False |
| SendTime | Specifies the time when the cmdlet must send the email notification. | TimeSpan | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNotificationOptions](vbrnotificationoptions.md)

Examples

Creating Notification Options for Backup Job

This command creates notification options for the backup job. Veeam Backup & Replication will send notifications about the job warning and when the job completes successfully.

|  |
| --- |
| New-VBRNotificationOptions -EnableAdditionalNotification -AdditionalAddress admin@domain.com -UseNotificationOptions -NotifyOnSuccess -NotifyOnWarning |


