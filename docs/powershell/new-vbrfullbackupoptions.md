---
title: "New-VBRFullBackupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfullbackupoptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRFullBackupOptions

In this article

Short Description

Creates active full backup schedule settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFullBackupOptions [-Enable] [-ScheduleType <VBRFullBackupScheduleType> {Weekly | Monthly}] [-SelectedDays <DayOfWeek[]> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayNumber <VBRDayNumberInMonth> {First | Second | Third | Fourth | Last | OnDay}] [-DayOfWeek <DayOfWeek> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayOfMonth <string>] [-SelectedMonths <VBRMonth[]> {January | February | March | April | May | June | July | August | September | October | November | December}]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRFullBackupOptions object. This object contains active full backup schedule settings that you can apply to Veeam Agent backup jobs. You can use this object to set up the following types of schedules for backup jobs:

* HealthCheck schedules
* Compact full backup schedules
* Active full backup schedules
* Synthetic full backup schedules

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Enable | Enables the option for the backup job to create active full backups. | SwitchParameter | False | Named | False |
| ScheduleType | Specifies the active full backups schedule type.   * Monthly: the job will create an active full on selected days of the month. * Weekly: the job will create an active full on selected days of the week. | VBRFullBackupScheduleType | False | Named | False |
| SelectedDays | For weekly backups.  Specifies the day of the week when the job creates active full backups.  Default: Saturday. | DayOfWeek[] | False | Named | False |
| DayNumber | For monthly backups.  Specifies the day of the month when the job creates active full backups.   * First: the job will create an active full backup on the first specified day of the week for the selected months. * Second: the job will create an active full backup on the second specified day of the week for the selected months. * Third: the job will create an active full backup on the third specified day of the week for the selected months. * Fourth: the job will create an active full backup on the fourth specified day of the week for the selected months. * Last: the job will create an active full backup on the last specified day of the week for the selected months. * OnDay: the job will create an active full backup on the selected day of the month. Use the DayOfMonth parameter to set the day. | VBRDayNumberInMonth | False | Named | False |
| DayOfWeek | For monthly backups.  Specifies the day of the week, when the job creates active full backups.   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday   Default: Saturday. | DayOfWeek | False | Named | False |
| DayOfMonth | For monthly backups with the OnDay option.  Specifies the day of the month, when the job creates active full backups.  For example, on the 3rd day of November. | String | False | Named | False |
| SelectedMonths | Specifies the months, when the job creates active full backups.   * January * February * March * April * May * June * July * August * September * October * November * December   Default: all months are selected. | VBRMonth[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRFullBackupOptions object that contains schedule settings for backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Schedule for Weekly Active Full Backups

|  |  |
| --- | --- |
| This command sets a schedule to create active full backups weekly. The job with these settings applied will create active full backups on Sundays and Wednesdays.  |  | | --- | | New-VBRFullBackupOptions -Enable -ScheduleType Weekly -SelectedDays Sunday, Wednesday | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Schedule for Monthly Active Full Backups

|  |  |
| --- | --- |
| This command sets a schedule to create active full backups monthly. The job with these settings applied will create active full backups on the 15th of January, April and September.  |  | | --- | | New-VBRFullBackupOptions -Enable -ScheduleType Monthly -DayNumber OnDay -DayOfMonth 15 -SelectedMonths January, April, September | |

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
