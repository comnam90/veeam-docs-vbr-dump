---
title: "New-VBRHealthCheckOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhealthcheckoptions.html"
last_updated: "12/4/2024"
product_version: "13.0.1.1071"
---

# New-VBRHealthCheckOptions


Short Description

Defines the health check schedule options.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHealthCheckOptions [-Enable] [-ScheduleType {Weekly | Monthly}] [-SelectedDays {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayNumber {First | Second | Third | Fourth | Last | OnDay}] [-DayOfWeek {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayOfMonth <string>] [-SelectedMonths {January | February | March | April | May | June | July | August | September | October | November | December}] [-WeeklyPeriod <timespan>] [-MonthlyPeriod <timespan>] [-EnableFullHealthCheck]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRHealthCheckOptions object that defines backup files health check schedule options.

|  |
| --- |
| Important |
| You cannot apply the New-VBRHealthCheckOptions cmdlet to a backup job. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DayNumber | For the monthly health check of backup files.  Specifies the day of the month when the job performs backup files health check. Parameter accepts the following values:   * First: the job will perform the health check on the first specified day of the week for the selected months. * Second: the job will perform the health check on the second specified day of the week for the selected months. * Third: the job will perform the health check on the third specified day of the week for the selected months. * Fourth: the job will perform the health check on the fourth specified day of the week for the selected months. * Last: the job will perform the health check on the last specified day of the week for the selected months. * OnDay: the job will perform the health check on the selected day of the month. Use the DayOfMonth parameter to set the day. | VBRDayNumberInMonth | False | Named | False |
| DayOfMonth | For the monthly health check of backup files.  Specifies the day of the month, when the job performs backup files health check. | String | False | Named | False |
| DayOfWeek | For the monthly health check of backup files.  Specifies the day of the week when the job performs the health check. Parameter accepts the following values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday   Default: Saturday. | DayofWeek | False | Named | False |
| Enable | Defines that the job will perform the light health check of backup files. | SwitchParameter | False | Named | False |
| EnableFullHealthCheck | Defines that the job will perform the full health check of backup files. | SwitchParameter | False | Named | False |
| MonthlyPeriod | For the monthly health check of backup files.  Specifies the job start time. | Timespan | False | Named | False |
| ScheduleType | Specifies the type of the health check job schedule. Parameter accepts the following values:   * Monthly: the job will run on selected days of the month. * Weekly: the job will run on selected days of the week. | VBRHealthCheckScheduleType | False | Named | False |
| SelectedDays | For the weekly health check of backup files.  Specifies the day of the week when the job will perform the health check of backup files. | DayOfWeek[] | False | Named | False |
| SelectedMonths | For the monthly health check of backup files.  Specifies the month when the job will perform the health check of backup files. | VBRMonth[] | False | Named | False |
| WeeklyPeriod | For the weekly health check of backup files.  Specifies the job start time. | Timespan | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHealthCheckOptions object that defines backup files health check schedule options.

Examples

Defining Backup Files Health Check Schedule Options

This command defines the following health check schedule options:

* The job will perform the light health check.
* The job runs weekly on Sunday at 18:00.

|  |
| --- |
| New-VBRHealthCheckOptions -Enable -ScheduleType Weekly -SelectedDays Sunday -WeeklyPeriod 18:00 |


