---
title: "Set-VBRComputerGFSWeeklyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputergfsweeklyoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerGFSWeeklyOptions


Short Description

Modifies settings of the weekly GFS retention policy for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerGFSWeeklyOptions -Options <VBRComputerGFSWeeklyOptions> [-RetentionPeriod <Int32>] [-SelectedDay <DayOfWeek>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the weekly GFS retention policy that you can apply to Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies a weekly GFS retention policy for Veeam Agent backup jobs. The cmdlet will modify this policy. | Accepts the VBRComputerGFSWeeklyOptions object. To create this object, run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. | True | Named | True |
| RetentionPeriod | Specifies the number of weeks to keep weekly full backups. | Int32 | False | Named | False |
| SelectedDay | Specifies a day of week when a weekly backup is created. You can specify either of the following day of a week:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSWeeklyOptions object that contains settings of the weekly GFS retention policy for Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Number of Weeks for GFS Retention Policy

|  |  |
| --- | --- |
| This example shows how to modify the weekly GFS retention policy settings. With these settings applied, Veeam Backup & Replication will keep weekly backups for 5 days.  |  | | --- | | $options = New-VBRComputerGFSWeeklyOptions -RetentionPeriod 3 -SelectedDay Wednesday  Set-VBRComputerGFSWeeklyOptions -Options $options -RetentionPeriod 5 |  Perform the following steps:   1. Run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedDay parameter values. Save the result to the $options variable. 2. Run the Set-VBRComputerGFSWeeklyOptions cmdlet. Set the $options variable as the Options parameter value. Specify the RetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Day When Backup is Created

|  |  |
| --- | --- |
| This example shows how to modify the weekly GFS retention policy settings and change a day of a week when a weekly backup is created. With these settings applied, Veeam Backup & Replication will create weekly backups on Tuesday.  |  | | --- | | $options = New-VBRComputerGFSWeeklyOptions -RetentionPeriod 3 -SelectedDay Wednesday  Set-VBRComputerGFSWeeklyOptions -Options $options -SelectedDay Tuesday |  Perform the following steps:   1. Run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedDay parameter values. Save the result to the $options variable. 2. Run the Set-VBRComputerGFSWeeklyOptions cmdlet. Set the $options variable as the Options parameter value. Set the Tuesday option for the SelectedDay parameter. |

Related Commands

[New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md)


