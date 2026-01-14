---
title: "Set-VBRFullBackupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrfullbackupoptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Set-VBRFullBackupOptions

In this article

Short Description

Modifies active full backup schedule settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRFullBackupOptions -Options <VBRFullBackupOptions> [-Enable] [-ScheduleType <VBRFullBackupScheduleType> {Weekly | Monthly}] [-SelectedDays <DayOfWeek[]> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayNumber <VBRDayNumberInMonth> {First | Second | Third | Fourth | Last | OnDay}] [-DayOfWeek <DayOfWeek> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayOfMonth <string>] [-SelectedMonths <VBRMonth[]> {January | February | March | April | May | June | July | August | September |October | November | December}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies schedule settings that you can apply to Veeam Agent backup jobs. You can modify settings for the following types of schedules:

* HealthCheck schedules
* Compact full backup schedules
* Active full backup schedules

* Synthetic full backup schedules

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the active full backup schedule that you want to modify. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | True | Named | True (ByValue) |
| Enable | Enables the option for the Veeam Agent backup job to create active full backups. | SwitchParameter | False | Named | False |
| ScheduleType | Specifies the type of active full backup schedule.   * Monthly: the job will create an active full on selected days of the month. * Weekly: the job will create an active full on selected days of the week. | VBRFullBackupScheduleType | False | Named | False |
| SelectedDays | For weekly full backups.  Specifies the day of the week when active full backups will be created. | DayOfWeek[] | False | Named | False |
| DayNumber | For monthly backups.  Specifies the day of the month when active full backups will be created (for example, Saturday):   * First: the job will create an active full backup on the first specified day of the week for the selected months. * Second: the job will create an active full backup on the second specified day of the week for the selected months. * Third: the job will create an active full backup on the third specified day of the week for the selected months. * Fourth: the job will create an active full backup on the fourth specified day of the week for the selected months. * Last: the job will create an active full backup on the last specified day of the week for the selected months. * OnDay: the job will create an active full backup on the selected day of the month. Use the DayOfMonth parameter to set the day. | VBRDayNumberInMonth | False | Named | False |
| DayOfWeek | For monthly backups.  Specifies the day of the week, when the job creates active full backups.   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek | False | Named | False |
| DayOfMonth | For monthly backups with the OnDay option.  Specifies the day of the month, when the job creates active full backups.  For example, on the 3rd day of November. | String | False | Named | False |
| SelectedMonths | Specifies the months, when the job creates active full backups.   * January * February * March * April * May * June * July * August * September * October * November * December | VBRMonth[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRFullBackupOptions object that contains schedule settings for backup jobs.

Examples

Modifying Active Full Backup Schedule from Weekly to Monthly

This example shows how to modify an active full backup schedule settings from weekly to monthly.

|  |
| --- |
| $activefull = New-VBRFullBackupOptions -Enable -ScheduleType Weekly -SelectedDays Sunday, Wednesday  Set-VBRFullBackupOptions -Options $activefull -Enable -ScheduleType Monthly -SelectedMonths January, March, June, October -DayNumber OnDay -DayOfMonth 3 |

Perform the following steps:

1. Run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. Provide the Enable parameter. Specify the ScheduleType and SelectedDays parameter values. Save the result to the $activefull variable.
2. Run the Set-VBRFullBackupOptions cmdlet. Specify the following settings:

* Set the $activefull variable as the Options parameter value.
* Provide the Enable parameter.
* Set the Monthly option for the ScheduleType parameter.
* Specify the SelectedMonths parameter value.
* Set the OnDay option for the DayNumber parameter.
* Specify the DayOfMonth parameter value.

Related Commands

[New-VBRFullBackupOptions](new-vbrfullbackupoptions.md)

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
