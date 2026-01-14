---
title: "New-VBRMonthlyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmonthlyoptions.html"
last_updated: "10/9/2024"
product_version: "13.0.1.1071"
---

# New-VBRMonthlyOptions

In this article

Short Description

Creates a new [VBRMonthlyOptions](vbrmonthlyoptions.md) object.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMonthlyOptions [-DayNumberInMonth <VBRDayNumberInMonth>] [-DayOfMonth <String>] [-DayOfWeek <DayOfWeek>] [-Months <VBRMonth[]>] [-Period <TimeSpan>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRMonhtlyOptions](vbrmonthlyoptions.md) object. This object contains the monthly schedule job settings. You can use this object to set job schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Period | Specifies the time when the job will start.  Default: 22:00. | TimeSpan | False | Named | False |
| DayNumberInMonth | Specifies the number of day in month (for example, Saturday):   * First: the job will run on the first (Saturday) of the selected months. * Second: the job will run on the second (Saturday) of the selected months. * Third: the job will run on the third (Saturday) of the selected months. * Fourth: the job will run on the fourth (Saturday) of the selected months. * Last: the job will run on the last (Saturday) of the selected months. * OnDay: the job will run on the selected day of the selected months. Use the DayOfMonth parameter to specify the day.   Default: Fourth. | VBRDayNumberInMonth | False | Named | False |
| DayOfWeek | Specifies the week day for the DayNumberInMonth parameter.  Default: Saturday. | DayOfWeek | False | Named | False |
| DayOfMonth | Specifies the day in month: 1-31, Last. | String | False | Named | False |
| Months | Specifies the months on which the job will run:   * January * February * March * April * May * June * July * August * September * October * November * December   Default: all months. | VBRMonth[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRMonthlyOptions](vbrmonthlyoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Schedule with Specific Day and Time

|  |  |
| --- | --- |
| This command creates the schedule for a job to run at 23:00 on the second Wednesday every month.  |  | | --- | | New-VBRMonthlyOptions -DayNumberInMonth Second -DayOfWeek Wednesday -Period 23:00 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Schedule to Run at 10:00 on Last Sunday of January and July

|  |  |
| --- | --- |
| This command creates the schedule for a job to run at 10:00 on the last Sunday of January and July.  |  | | --- | | New-VBRMonthlyOptions -DayNumberInMonth Last -DayOfWeek Sunday -Period 10:00 -Months January, July | |

Page updated 10/9/2024

Page content applies to build 13.0.1.1071
