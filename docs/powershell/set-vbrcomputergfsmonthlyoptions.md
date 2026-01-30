---
title: "Set-VBRComputerGFSMonthlyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputergfsmonthlyoptions.html"
last_updated: "12/23/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerGFSMonthlyOptions


Short Description

Modifies settings of the monthly GFS retention policy for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerGFSMonthlyOptions -Options <VBRComputerGFSMonthlyOptions> [-RetentionPeriod <Int32>] [-SelectedWeek <VBRWeekOfMonth>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the monthly GFS retention policy that you can apply to Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies a monthly GFS retention policy for Veeam Agent backup jobs. The cmdlet will modify this policy. | Accepts the VBRComputerGFSMonthlyOptions object. To create this object, run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. | True | Named | True |
| RetentionPeriod | Specifies the number of months to keep monthly full backups. | Int32 | False | Named | False |
| SelectedWeek | Specifies a week of a month when a monthly backup is created. You can specify either of the following weeks:   * First - the cmdlet will create the monthly backup in the first week of the month. * Second - the cmdlet will create the monthly backup in the second week of the month. * Third - the cmdlet will create the monthly backup in the third week of the month. * Fourth - the cmdlet will create the monthly backup in the fourth week of the month. * Last - the cmdlet will create the monthly backup in the last week of the month. | VBRWeekOfMonth | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSMonthlyOptions object that contains settings of a monthly GFS retention policy for Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Number of Months for GFS Retention Policy

|  |  |
| --- | --- |
| This example shows how to modify the settings of the monthly GFS retention policy and change a number of months to keep monthly backups.  With these settings applied, Veeam Backup & Replication will keep monthly backups for 5 months.  |  | | --- | | $options = New-VBRComputerGFSMonthlyOptions -RetentionPeriod 3 -SelectedWeek First  Set-VBRComputerGFSMonthlyOptions -Options $options -RetentionPeriod 5 |  Perform the following steps:   1. Run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedWeek parameter values. Save the result to the $options variable. 2. Run the Set-VBRComputerGFSMonthlyOptions cmdlet. Set the $options variable as the Options parameter value. Specify the RetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Day When Backup is Created

|  |  |
| --- | --- |
| This example shows how to modify the settings of the monthly GFS retention policy and change a week when a monthly backup is created.  With these settings applied, Veeam Backup & Replication will create monthly backups on the last week of a month.  |  | | --- | | $options = New-VBRComputerGFSMonthlyOptions -RetentionPeriod 3 -SelectedWeek First  Set-VBRComputerGFSMonthlyOptions -Options $options -SelectedWeek Last |  Perform the following steps:   1. Run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedWeek parameter values. Save the result to the $options variable. 2. Run the Set-VBRComputerGFSMonthlyOptions cmdlet. Set the $options variable as the Options parameter value. Set the Last option for the SelectedWeek parameter. |

Related Commands

[New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md)


