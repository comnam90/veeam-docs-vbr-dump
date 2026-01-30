---
title: "Set-VBRBackupWindowOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrbackupwindowoptions.html"
last_updated: "3/13/2024"
product_version: "13.0.1.1071"
---

# Set-VBRBackupWindowOptions


Short Description

Modifies job backup window settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRBackupWindowOptions -Enabled -FromDay <DayOfWeek> -FromHour <Int32> -Options <VBRBackupWindowOptions> [-PassThru] -ToDay <DayOfWeek> -ToHour <Int32>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the job backup window settings. You can use it to extend the existing backup window or remove specific days and hours from it. To modify settings, you must specify new values for the necessary parameters.

|  |
| --- |
| ![Set-VBRBackupWindowOptions](images/icon_important.webp) Important! |
| To modify the backup windows settings, you must provide the PassThru parameter in your scripts. If you omit this parameter, the backup window settings will not be modified. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the backup window settings that you want to modify. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| FromDay | Specifies the day of the week on which the backup window opens. The cmdlet will extend the backup window with this day or will remove that day from the backup window.  Default: Sunday. | DayOfWeek | True | Named | False |
| FromHour | Specifies the hour on which the backup window opens. The cmdlet will add this hour to the existing backup window or will remove that hour from the backup window.  Default: 0. | Int32 | True | Named | False |
| ToDay | Specifies the day of the week on which the backup window ends. The cmdlet will extend the backup window with this day or will remove that day from the backup window.  Default: Saturday. | DayOfWeek | True | Named | False |
| ToHour | Specifies the hour on which the backup window ends. The cmdlet will add this hour to the existing backup window or will remove that hour from the backup window.  Default: 23. | Int32 | True | Named | False |
| Enabled | Defines that the cmdlet will extend the backup window or will remove specific days and hours from it.  If you set this parameter to the Enabled:$false value, the cmdlet will remove the specified time period from the backup window. | SwitchParameter | True | Named | False |
| PassThru | Defines that the command will return the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Object Output

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Specific Hours from Backup Window

|  |  |
| --- | --- |
| This example shows how to modify the job backup window settings. The cmdlet will specify the time when the backup job is not allowed to run.   * The [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet defines the following backup window settings: the job is allowed to run from 10:00 AM till 22.59 PM on Monday, Tuesday, Wednesday and Thursday. * The Set-VBRBackupWindowOptions cmdlet modifies these settings. The job is not allowed to run from 10.00 AM till 12.59 AM on Tuesday and Wednesday.   |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -FromHour 10 -ToDay Thursday -ToHour 22 -Enabled  $windowoptions = Set-VBRBackupWindowOptions -Options $windowoptions -FromDay Tuesday -FromHour 10 -ToDay Wednesday -ToHour 12 -Enabled:$false -PassThru  Set-VBRJobSchedule -Job $job -PeriodicallySchedule $windowoptions -Periodicaly -FullPeriod 6 -PeriodicallyKind Hours |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the following settings:  * Specify the FromDay parameter value. * Specify the FromHour parameter value. * Specify the ToDay parameter value. * Specify the ToHour parameter value. * Provide the Enabled parameter.   Save the result to the $windowoptions variable.   1. Run the Set-VBRBackupWindowOptions cmdlet. Specify the following settings:  * Set the $windowoptions variable as the Options parameter value. * Specify the FromDay parameter value. * Specify the FromHour parameter value. * Specify the ToDay parameter value. * Specify the ToHour parameter value. * Provide the $false value for the Enabled parameter. * Provide the PassThru parameter.   Save the result to the $windowoptions variable.   1. Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Set the $windowoptions variable as the PeriodicallySchedule parameter value. * Provide the Periodicaly parameter. * Specify the FullPeriod parameter value. * Set the Hours option for the PeriodicallyKind parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Extending Backup Window

|  |  |
| --- | --- |
| This example shows how to modify the job backup window settings. The cmdlet will extend the backup window to specify when the backup job is allowed to run.   * The [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet defines the following backup window settings: the job is allowed to run from 10:00 AM till 22.59 PM on Monday, Tuesday, Wednesday and Thursday. * The Set-VBRBackupWindowOptions cmdlet modifies these settings. The backup window is extended from 10.00 AM till 12.59 AM on Friday and Saturday.   |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -FromHour 10 -ToDay Thursday -ToHour 22 -Enabled  $windowoptions = Set-VBRBackupWindowOptions -Options $windowoptions -FromDay Friday -FromHour 10 -ToDay Saturday -ToHour 12 -Enabled -PassThru  Set-VBRJobSchedule -Job $job -Periodicaly -FullPeriod 6 -PeriodicallyKind Hours -PeriodicallySchedule $windowoptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the following settings:  * Specify the FromDay parameter value. * Specify the FromHour parameter value. * Specify the ToDay parameter value. * Specify the ToHour parameter value. * Provide the Enabled parameter.   Save the result to the $windowoptions variable.   1. Run the Set-VBRBackupWindowOptions cmdlet. Specify the following settings:  * Set the $windowoptions variable as the Options parameter value. * Specify the FromDay parameter value. * Specify the FromHour parameter value. * Specify the ToDay parameter value. * Specify the ToHour parameter value. * Provide the Enabled parameter. * Provide the PassThru parameter.   Save the result to the $windowoptions variable.   1. Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value.  * Provide the Periodicaly parameter. * Specify the FullPeriod parameter value.  * Set the Hours option for the PeriodicallyKind parameter.  * Set the $windowoptions variable as the PeriodicallySchedule parameter value. |

Related Commands

* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)
* [Set-VBRJobSchedule](set-vbrjobschedule.md)
* [Get-VBRJob](get-vbrjob.md)


