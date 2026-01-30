---
title: "Set-VBRJobAdvancedNotificationOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobadvancednotificationoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobAdvancedNotificationOptions


Short Description

Customizes job notification settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobAdvancedNotificationOptions [-EmailNotification <Boolean>] [-EmailNotificationAddresses <string>] -Job <CBackupJob[]> [-SnmpNotification <Boolean>]  [<CommonParameters>] |

Detailed Description

This cmdlet sets notification options for the selected job.

You can set SNMP and email notifications on job run results.

|  |
| --- |
| ![Set-VBRJobAdvancedNotificationOptions](images/icon_important.webp) Important! |
| Veeam Backup & Replication will send email notifications and SNMP notifications only in case these options are set up in the Veeam Backup & Replication general settings. Note that you cannot enable email notifications and SNMP notifications with Veeam PowerShell.  For more information on configuring notification, see the [Specifying Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/email_notification_settings.html?ver=13) section of the User Guide.  For more information on configuring SNMP notifications, see the [Specifying SNMP Settings](https://helpcenter.veeam.com/docs/vbr/userguide/snmp_settings.html?ver=13) section of the User Guide. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will modify notification options of these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| SnmpNotification | Defines whether the job will send the SNMP notification. You need to have the SNMP notification pre-configured. | Bool | False | Named | False |
| EmailNotification | Defines whether the job will send notifications to email address(es). Use the EmailNotificationAddresses parameter to specify the addresses. | Bool | False | Named | False |
| EmailNotificationAddresses | Specifies the email address(es) to use for email notification. You can write multiple addresses separated by semicolon. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting SNMP and Email Notifications for Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set SNMP and email notifications for the backup job named Backup Job 01.  |  | | --- | | Get-VBRJob -Name "Backup Job 01" | Set-VBRJobAdvancedNotificationOptions -SnmpNotification $True -EmailNotification $True -EmailNotificationAddresses "administrator@veeam.com" |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedNotificationOptions cmdlet. Specify the following settings:  * Provide the $True value for the SnmpNotification parameter. * Provide the $True value for the EmailNotification parameter. * Specify the EmailNotificationAddresses parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Turning off Previously Set Email Notification for Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to turn off the previously set email notification for the backup job named Backup Job 01.  |  | | --- | | Get-VBRJob -Name "Backup Job 01" | Set-VBRJobAdvancedNotificationOptions -EmailNotification $False |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedNotificationOptions cmdlet. Provide the $False value for the EmailNotification parameter. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


