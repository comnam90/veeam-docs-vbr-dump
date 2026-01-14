---
title: "New-VBRTapeMediaSetCreationPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrtapemediasetcreationpolicy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRTapeMediaSetCreationPolicy

In this article

Short Description

Defines a set of rules for creating media sets.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRTapeMediaSetCreationPolicy [-DailyOptions <VBRDailyOptions>] [-Type <VBRTapeMediaSetCreationPolicyType> {Never | Always | Daily | Monthly}]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRTapeMediaSetCreationPolicy](vbrtapemediasetcreationpolicy.md) object. This object contains the set of rules for creating media sets. You can apply these settings when configuring media sets.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DailyOptions | Specifies the schedule settings you want to apply to the media set.  Default: Selected Days, 18 hours, Saturday. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| Type | Specifies the type of policy for creating media sets:   * Never: new media sets are not created. All data archived to tape is written to the same media set. * Always: new media set is created for each tape job session. * Daily: new media set is created on particular days. Use the DailyOptions parameter to set days on which you want the media sets to be created. * Monthly: not supported.   Default: Never. | [VBRTapeMediaSetCreationPolicyType](enums.md#VBRTapeMediaSetCreationPolicyType) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMediaSetCreationPolicy](vbrtapemediasetcreationpolicy.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Media Set Creation Rules - New Media Set for Every Backup Session

|  |  |
| --- | --- |
| This command defines media set creation rules. A new media set will be created for every backup session.  |  | | --- | | New-VBRTapeMediaSetCreationPolicy -Type Always | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Media Set Creation Rules - New Media Set Every Sunday

|  |  |
| --- | --- |
| This example shows how to define media set creation rules. This cmdlet will create a new media set every Sunday at 22:00.  |  | | --- | | $dailyoptions = New-VBRDailyOptions -DayOfWeek Sunday -Period 22:00 -Type SelectedDays  New-VBRTapeMediaSetCreationPolicy -DailyOptions $dailyoptions -Type Daily |  Perform the following steps:   1. Run the New-VBRDailyOptions cmdlet. Specify the DayOfWeek, Period and the Type parameter values. Save the result to the $dailyoptions variable. 2. Run the New-VBRTapeMediaSetCreationPolicy cmdlet. Set the $dailyoptions variable as the DailyOptions parameter value. Set the Daily option for the Type parameter. |

Related Commands

[New-VBRDailyOptions](new-vbrdailyoptions.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
