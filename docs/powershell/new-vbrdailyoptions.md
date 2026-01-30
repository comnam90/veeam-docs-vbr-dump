---
title: "New-VBRDailyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrdailyoptions.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRDailyOptions


Short Description

Creates new job daily schedule settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRDailyOptions [-DayOfWeek <DayOfWeek[]>] [-Period <TimeSpan>] [-Type <VBRDailyOptionsType>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRDailyOptions](vbrdailyoptions.md) object. This object contains job daily schedule settings. You can use this object to set job schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the job schedule type:   * Everyday: the job will run every day. * WeekDays: the job will run Monday to Friday. * SelectedDays: the job will run on selected days. Use the DaysOfWeek parameter to set the days. | VBRDailyOptionsType | False | Named | False |
| DayOfWeek | Specifies the day of week when the job will run.  Default: Saturday. | DayOfWeek[] | False | Named | False |
| Period | Specifies the time when the job will start.  Default: 18:00. | TimeSpan | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDailyOptions](vbrdailyoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Schedule for Every Friday

|  |  |
| --- | --- |
| This example shows how to create schedule with the following settings: every Friday at 23:00.  |  | | --- | | $fridayoptions = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00 |  Perform the following steps:   1. Run the New-VBRDailyOptions cmdlet. Specify the DayOfWeek parameter value. Specify the Period parameter value. 2. Save the result to the $fridayoptions variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Schedule for Everyday

|  |  |
| --- | --- |
| This example shows how to create schedule with the following settings: everyday at 20:00.  |  | | --- | | $everydayoptions = New-VBRDailyOptions -Type Everyday -Period 20:00 |  Perform the following steps:   1. Run the New-VBRDailyOptions cmdlet. Specify the Type parameter value. Specify the Period parameter value. 2. Save the result to the $everydayoptions variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Schedule for Weekends

|  |  |
| --- | --- |
| This example shows how to create schedule with the following settings: on weekends at 18:00.  |  | | --- | | $weekendoptions = New-VBRDailyOptions -DayOfWeek Saturday, Sunday -Type SelectedDays |  Perform the following steps:   1. Run the New-VBRDailyOptions cmdlet. Specify the DayOfWeek parameter value. Specify the Type parameter value. 2. Save the result to the $weekendoptions variable. |


