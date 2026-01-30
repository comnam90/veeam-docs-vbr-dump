---
title: "Set-VBRCDPPolicyRetentionOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcdppolicyretentionoptions.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCDPPolicyRetentionOptions


Short Description

Modifies retention settings of CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCDPPolicyRetentionOptions -Options <VBRCDPPolicyRetentionOptions> [-RPOFrequencyType <VBRCDPRPOIntervalType>] [-RPOFrequency <Int32>] [-BackupWindow <VBRBackupWindowOptions>] [-ShortTermRetentionIntervalType <VBRCDPRetentionIntervalType>] [-ShortTermRetentionInterval <Int32>] [-LongTermRetentionFrequency <Int32>] [-LongTermRetentionNumber <Int32>] [-LongTermRetentionFrequencyType <VBRCDPRetentionIntervalType>] [-ApplicationProcessingBackupWindow <VBRBackupWindowOptions>] [-HourlyOffset <Int32>] [-EnableRPOMarkAsWarning <Boolean>] [-MarkJobAsWarningThreshold <Int32>] [-MarkJobAsWarningIntervalType <VBRCDPRPOIntervalType>] [-EnableRPOMarkAsError <Boolean>] [-MarkJobAsErrorThreshold <Int32>] [-MarkJobAsErrorIntervalType <VBRCDPRPOIntervalType>]  [<CommonParameters>] |

This cmdlet modifies retention setting of CDP policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies retention settings of CDP policies that you want to modify. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RPOFrequencyType | Specifies RPO settings. The cmdlet will schedule the CDP policy to create a replicated state of the source VMs. You can set one of the following units of time:   * Minutes: Use this option to schedule a CDP policy to create a replicated state of the source VMs every N minutes. * Seconds: Use this option to schedule a CDP policy to create a replicated state of the source VMs every N seconds.   Default: Seconds. | VBRCDPRPOIntervalType | False | Named | False |
| RPOFrequency | Specifies a number of minutes or seconds for the RPO settings. The cmdlet will schedule the CDP policy to create a replicated state of the source VMs every N seconds or minutes.  Default: 15. | Int | False | Named | False |
| BackupWindow | Specifies a time interval within which a CDP policy is allowed to create a replicated state of the source VMs. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| ShortTermRetentionIntervalType | For a short-term retention policy.  Specifies a period during which Veeam Backup & Replication will store a replicated state of the source VMs on a target datastore. You can set the period in one of the following units of time:   * Minutes: Use this option to store a replicated state of the source VMs for last N minutes. * Hours: Use this option to store a replicated state of the source VMs for last N hours.   Default: Hours. | VBRCDPRetentionIntervalType | False | Named | False |
| ShortTermRetentionInterval | For a short-term retention settings.  Specifies a number of minutes or hours to store a replicated state of the source VMs. The cmdlet will schedule a CDP policy to store a replicated state of the source VMs only for last N minutes or hours.  Default: 4. | Int | False | Named | False |
| LongTermRetentionFrequencyType | For a long-term retention settings.  Specifies a period when a CDP policy must create long-term restore points. You can set the period in one of the following units of time:   * Minutes: Use this option to create a long-term restore point every N minutes. * Hours: Use this option to create a long-term restore point every N hours.   Default: Hours. | VBRCDPRetentionIntervalType | False | Named | False |
| LongTermRetentionFrequency | For a long-term retention option.  Specifies how often a CDP policy must create a long-term restore point. The cmdlet will schedule the CDP policy to create a restore point every N hours.  Default: 8. | Int | False | Named | False |
| LongTermRetentionNumber | For long-term retention settings.  Specifies a number of days to keep a long-term restore point in a datastore. After this period is passed, Veeam Backup & Replication will delete a long-term restore point.  Default: 7. | Int32 | False | Named | False |
| ApplicationProcessingBackupWindow | Specifies a schedule that defines when a CDP policy must create crash-consistent and application-consistent backups. | Accepts the New-VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| EnableRPOMarkAsWarning | For RPO reports.  Enables RPO warning reports for a CDP policy. | Bool | False | Named | False |
| HourlyOffset | Used for adjusting the application processing backup window.  Specifies the number of minutes (1-59). The schedule will be shifted for the specified number of minutes.  For example, you schedule creation of crash-consistent restore points from 00:00 to 01:00, and set the offset value to 25. The schedule will be shifted forward, and the crash-consistent restore points will be created from 0:25 and to 01:25. | Int | False | Named | False |
| MarkJobAsWarningThreshold | For RPO reports.  Specifies an allowed time limit of the exceeded RPO. Veeam Backup & Replication will send notification with a warning if this time limit is reached.  Default: 2. | Int | False | Named | False |
| MarkJobAsWarningIntervalType | For RPO reports.  Specifies a time interval of the exceeded RPO. You can set the period in one of the following units of time:   * Seconds: Use this option to get a warning notification after a time interval of the exceeded RPO reaches N seconds. * Minutes: Use this option to get a warning notification after a time interval of the exceeded RPO reaches N minutes.   Default: Seconds. | VBRCDPRPOIntervalType | False | Named | False |
| EnableRPOMarkAsError | For RPO reports.  Enables RPO error reports for a CDP policy. | Bool | False | Named | False |
| MarkJobAsErrorThreshold | For RPO reports.  Specifies an allowed time limit of the exceeded RPO. Veeam Backup & Replication will send notification with a warning if this time limit is reached.  Default: 3. | Int | False | Named | False |
| MarkJobAsErrorIntervalType | For RPO reports.  Specifies a time interval of the exceeded RPO. You can set the period in one of the following units of time:   * Seconds: Use this option to get an error notification after a time interval of the exceeded RPO reaches N seconds. * Minutes: Use this option to get an error notification after a time interval of the exceeded RPO reaches N minutes.   Default: Seconds. | VBRCDPRPOIntervalType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPPolicyRetentionOptions object that defines retention policy and schedule settings of CDP policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Short-Term Retention for CDP Policy

|  |  |
| --- | --- |
| This example shows how to modify short-term retention for CDP policy to keep keep only those replicated states of the source VMs that were created within last 5 hours.  |  | | --- | | $options = New-VBRCDPPolicyRetentionOptions -ShortTermRetentionIntervalType Hours -ShortTermRetentionInterval 2  Set-VBRCDPPolicyRetentionOptions -Options $options -ShortTermRetentionInterval 5 |  Perform the following steps:   1. Run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. Specify the ShortTermRetentionIntervalType and ShortTermRetentionInterval parameters. Save the result to the $options variable. 2. Run the Set-VBRCDPPolicyRetentionOptions cmdlet. Set the $options variable as the Options parameter value. Specify the ShortTermRetentionInterval parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Long-Term Retention for CDP Policy

|  |  |
| --- | --- |
| This example shows how to modify long-term retention for CDP policy to create a long-term restore point every 9 hours.  |  | | --- | | $options = New-VBRCDPPolicyRetentionOptions -LongTermRetentionFrequencyType Hours -LongTermRetentionNumber 3  Set-VBRCDPPolicyRetentionOptions -Options $options -LongTermRetentionNumber 9 |  Perform the following steps:   1. Run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. Specify the LongTermRetentionFrequencyType and LongTermRetentionNumber parameters. Save the result to the $options variable. 2. Run the Set-VBRCDPPolicyRetentionOptions cmdlet. Set the $options variable as the Options parameter value. Specify the LongTermRetentionNumber parameter value. |

Related Commands

[New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md)


