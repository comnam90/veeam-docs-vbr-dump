---
title: "New-VBRCDPPolicyRetentionOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcdppolicyretentionoptions.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCDPPolicyRetentionOptions


Short Description

Defines retention settings of CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRCDPPolicyRetentionOptions [-RPOFrequencyType <VBRCDPRPOIntervalType>] [-RPOFrequency <Int32>] [-BackupWindow <VBRBackupWindowOptions>] [-ShortTermRetentionIntervalType <VBRCDPRetentionIntervalType>] [-ShortTermRetentionInterval <Int32>] [-LongTermRetentionFrequency <Int32>] [-LongTermRetentionNumber <Int32>] [-LongTermRetentionFrequencyType <VBRCDPRetentionIntervalType>] [-ApplicationProcessingBackupWindow <VBRBackupWindowOptions>] [-HourlyOffset <Int32>] [-EnableRPOMarkAsWarning <Boolean>] [-MarkJobAsWarningThreshold <Int32>] [-MarkJobAsWarningIntervalType <VBRCDPRPOIntervalType>] [-EnableRPOMarkAsError <Boolean>] [-MarkJobAsErrorThreshold <Int32>] [-MarkJobAsErrorIntervalType <VBRCDPRPOIntervalType>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRCDPPolicyRetentionOptions object that defines the following setting of CDP policies:

* Recovery point objective (RPO) — a setting that defines the maximum allowed time of the data loss in case the production VM is down.
* Retention policy — a setting that defines the schedule for the short-term and long-term retention policies.
* RPO reports settings — a setting that defines when CDP policies are marked with the RPO warning or error.
* Schedule — a setting that defines when a CDP policy must create crash-consistent and application-consistent backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupWindow | Specifies a time interval within which a CDP policy is allowed to create a replicated state of the source VMs. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| ShortTermRetentionIntervalType | For a short-term retention policy.  Specifies a period during which Veeam Backup & Replication will store a replicated state of the source VMs on a target datastore. You can set the period in one of the following units of time:   * Minutes: Use this option to store a replicated state of the source VMs for last N minutes. * Hours: Use this option to store a replicated state of the source VMs for last N hours.   Default: Hours. | VBRCDPRetentionIntervalType | False | Named | False |
| ShortTermRetentionInterval | For short-term retention settings.  Specifies a number of minutes or hours to store a replicated state of the source VMs. The cmdlet will schedule a CDP policy to store a replicated state of the source VMs only for last N minutes or hours.  Default: 4 | Int | False | Named | False |
| LongTermRetentionFrequency | For long-term retention settings.  Specifies how often a CDP policy must create a long-term restore point. The cmdlet will schedule the CDP policy to create a restore point every N hours.  Default: 8. | Int | False | Named | False |
| ApplicationProcessingBackupWindow | Specifies a schedule that defines when a CDP policy must create crash-consistent and application-consistent backups. | Accepts the New-VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| EnableRPOMarkAsWarning | For RPO reports.  Enables RPO warning reports for a CDP policy. | Bool | False | Named | False |
| HourlyOffset | Used for adjusting the application processing backup window.  Specifies the number of minutes (1-59). The schedule will be shifted for the specified number of minutes.  For example, you schedule creation of crash-consistent restore points from 00:00 to 01:00, and set the offset value to 25. The schedule will be shifted forward, and the crash-consistent restore points will be created from 0:25 and to 01:25. | Int | False | Named | False |
| MarkJobAsWarningThreshold | For RPO reports.  Specifies an allowed time limit of the exceeded RPO. Veeam Backup & Replication will send a notification with a warning if this time limit is reached.  Default: 2. | Int | False | Named | False |
| MarkJobAsWarningIntervalType | For RPO reports.  Specifies a time interval of the exceeded RPO. You can set the period in one of the following units of time:   * Seconds: Use this option to get a warning notification after a time interval of the exceeded RPO reaches N seconds. * Minutes: Use this option to get a warning notification after a time interval of the exceeded RPO reaches N minutes.   Default: Seconds. | VBRCDPRPOIntervalType | False | Named | False |
| EnableRPOMarkAsError | For RPO reports.  Enables RPO error reports for a CDP policy. | Bool | False | Named | False |
| MarkJobAsErrorThreshold | For RPO reports.  Specifies an allowed time limit of the exceeded RPO. Veeam Backup & Replication will send notification with a warning if this time limit is reached.  Default: 3. | Int | False | Named | False |
| MarkJobAsErrorIntervalType | For RPO reports.  Specifies a time interval of the exceeded RPO. You can set the period in one of the following units of time:   * Seconds: Use this option to get an error notification after a time interval of the exceeded RPO reaches N seconds. * Minutes: Use this option to get an error notification after a time interval of the exceeded RPO reaches N minutes.   Default: Seconds. | VBRCDPRPOIntervalType | False | Named | False |
| RPOFrequencyType | Specifies RPO settings. The cmdlet will schedule the CDP policy to create a replicated state of the source VMs. You can set one of the following units of time:   * Minutes: Use this option to schedule a CDP policy to create a replicated state of the source VMs every N minutes. * Seconds: Use this option to schedule a CDP policy to create a replicated state of the source VMs every N seconds.   Default: Seconds. | VBRCDPRPOIntervalType | False | Named | False |
| RPOFrequency | Specifies a number of minutes or seconds for the RPO settings. The cmdlet will schedule the CDP policy to create a replicated state of the source VMs every N seconds or minutes.  Default: 15 | Int | False | Named | False |
| LongTermRetentionNumber | For long-term retention settings.  Specifies a number of days to keep a long-term restore point in a datastore. After this period is passed, Veeam Backup & Replication will delete a long-term restore point.  Default: 7. | Int32 | False | Named | False |
| LongTermRetentionFrequencyType | For long-term retention settings.  Specifies a period when a CDP policy must create long-term restore points. You can set the period in one of the following units of time:   * Minutes: Use this option to create a long-term restore point every N minutes. * Hours: Use this option to create a long-term restore point every N hours.   Default: Hours. | VBRCDPRetentionIntervalType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPPolicyRetentionOptions object that defines retention policy and schedule settings of CDP policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining RPO Settings for CDP Policy

|  |  |
| --- | --- |
| This example shows how to define the following RPO settings for a CDP policy:   * The cmdlet will create a replicated state of the source VMs during the following periods of time:  * From 22:00 to 22:59 on Friday * From 22:00 to 22:59 on Saturday  * RPO is set to 10 minutes.   |  | | --- | | $windowoptions = New-VBRBackupWindowOptions -FromDay Friday -FromHour 22 -ToDay Saturday -ToHour 22 -Enabled  New-VBRCDPPolicyRetentionOptions -RPOFrequencyType Minutes -RPOFrequency 10 -BackupWindow $windowoptions |  Perform the following steps:   1. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the FromDay, FromHour, ToDay, ToHour, Enabled parameter value. Save the result to the $windowoptions variable. 2. Run the New-VBRCDPPolicyRetentionOptions cmdlet. Specify the following settings:  * Set the Minutes option for the RPOFrequencyType parameter. * Specify the RPOFrequency parameter value. * Set the $windowoptions variable as the BackupWindow parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Short-Term Retention for CDP Policy

|  |  |
| --- | --- |
| This command schedules a CDP policy to keep only those VM replicated states that were created within last 2 hours.  |  | | --- | | New-VBRCDPPolicyRetentionOptions -ShortTermRetentionIntervalType Hours -ShortTermRetentionInterval 2 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Long-Term Retention for CDP Policy

|  |  |
| --- | --- |
| This command schedules a CDP policy to create a long-term restore points every 5 hours. Each restore point will be retained for 6 days.  |  | | --- | | New-VBRCDPPolicyRetentionOptions -LongTermRetentionFrequencyType Hours -LongTermRetentionFrequency 5 -LongTermRetentionNumber 6 | |

Related Commands

[New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)


