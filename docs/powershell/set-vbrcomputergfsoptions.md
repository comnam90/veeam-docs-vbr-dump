---
title: "Set-VBRComputerGFSOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputergfsoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerGFSOptions


Short Description

Modifies GFS retention settings for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerGFSOptions -GFSOptions <VBRComputerGFSOptions> [-GFSWeeklyOptions <VBRComputerGFSWeeklyOptions>] [-GFSMonthlyOptions <VBRComputerGFSMonthlyOptions>] [-GFSYearlyOptions <VBRComputerGFSYearlyOptions>] [-EnableGFSWeeklyBackup] [-EnableGFSMonthlyBackup] [-EnableGFSYearlyBackup] [-ReadEntireRestorePoint]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies GFS retention settings that you can apply to Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| GFSOptions | Specifies GFS retention. The cmdlet will modify this policy. | VBRComputerGFSOptions | True | Named | True |
| GFSWeeklyOptions | Specifies settings of a weekly GFS retention policy. The cmdlet will define GFS retention with these settings. | Accepts the VBRComputerGFSWeeklyOptions object. To create this object, run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. | False | Named | False |
| GFSMonthlyOptions | Specifies settings of a monthly GFS retention policy. The cmdlet will define GFS retention with these settings. | Accepts the VBRComputerGFSMonthlyOptions object. To create this object, run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. | False | Named | False |
| GFSYearlyOptions | Specifies settings of a yearly GFS retention policy. The cmdlet will define GFS retention with these settings. | Accepts the VBRComputerGFSYearlyOptions object. To create this object, run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet. | False | Named | False |
| EnableGFSWeeklyBackup | Defines that the cmdlet will enable a weekly GFS retention policy. If you do not provide this parameter, the cmdlet will not change the settings of weekly GFS retention policy. | SwitchParameter | False | Named | False |
| EnableGFSMonthlyBackup | Defines that the cmdlet will enable a monthly GFS retention policy. If you do not provide this parameter, the cmdlet will not change the settings of a monthly GFS retention policy. | SwitchParameter | False | Named | False |
| EnableGFSYearlyBackup | Defines that the cmdlet will enable a yearly GFS retention policy. If you do not provide this parameter, the cmdlet will not change the settings of a yearly GFS retention policy. | SwitchParameter | False | Named | False |
| ReadEntireRestorePoint | Defines that the cmdlet will process the most recent restore point instead of waiting for the current backup file to become available. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSOptions object that contains settings of GFS retention for Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Monthly GFS Retention Policy

|  |  |
| --- | --- |
| This example shows how to modify the monthly retention policy settings to create backups on the last week of every month and keep them for 2 months.  |  | | --- | | $weekly = New-VBRComputerGFSWeeklyOptions -RetentionPeriod 3 -SelectedDay Wednesday  $options = New-VBRComputerGFSOptions -GFSWeeklyOptions $weekly  $monthly = New-VBRComputerGFSMonthlyOptions -RetentionPeriod 2 -SelectedWeek Last  Set-VBRComputerGFSOptions -GFSOptions $options -EnableGFSMonthlyBackup -GFSMonthlyOptions $monthly |  Perform the following steps:   1. Define the GFS Retention Policy:  1. Run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedDay parameter values. Save the result to the $weekly variable. 2. Run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. Set the $weekly variable as the GFSWeeklyOptions parameter value. Save the result to the $options variable.  1. Run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedWeek parameter values. Save the result to the $monthly variable. 2. Run the Set-VBRComputerGFSOptions cmdlet. Specify the following settings:  * Set the $options variable as the GFSOptions parameter value. * Provide the EnableGFSMonthlyBackup parameter. * Set the $monthly variable as the GFSMonthlyOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Yearly GFS Retention Policy

|  |  |
| --- | --- |
| This example shows how to modify the yearly retention policy settings to create backups on November and keep them for 2 years.  |  | | --- | | $weekly = New-VBRComputerGFSWeeklyOptions -RetentionPeriod 3 -SelectedDay Wednesday  $options = New-VBRComputerGFSOptions -GFSWeeklyOptions $weekly  $yearly = New-VBRComputerGFSYearlyOptions -RetentionPeriod 2 -SelectedMonth November  Set-VBRComputerGFSOptions -GFSOptions $options -EnableGFSYearlyBackup -GFSYearlyOptions $yearly |  Perform the following steps:   1. Define the GFS Retention Policy:  1. Run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedDay parameter values. Save the result to the $weekly variable. 2. Run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. Set the $weekly variable as the GFSWeeklyOptions parameter value. Save the result to the $options variable.  1. Run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedMonth parameter values. Save the result to the $yearly variable. 2. Run the Set-VBRComputerGFSOptions cmdlet. Specify the following settings:  * Set the $options variable as the GFSOptions parameter value. * Provide the EnableGFSYearlyBackup parameter. * Set the $yearly variable as the GFSYearlyOptions parameter value. |

Related Commands

* [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md)
* [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md)
* [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md)
* [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md)


