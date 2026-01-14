---
title: "New-VBRTapeMediaPoolRetentionPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrtapemediapoolretentionpolicy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRTapeMediaPoolRetentionPolicy

In this article

Short Description

Defines retention settings of a media pool.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRTapeMediaPoolRetentionPolicy [-Period <VBRTapeMediaPoolPeriod> {None | Days | Weeks | Months}] [-Type <VBRTapeMediaPoolRetentionType> {Never | Period | Cyclic}] [-Value <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRTapeMediaPoolRetentionPolicy](vbrtapemediapoolretentionpolicy.md) object. This object contains the retention settings of media pool.

Retention policy sets overwrite protection rules. The rules are set to media pool and are applied to all tapes belonging to this media pool. After the retention period ends, the tape is queued for overwriting.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the data retention type:   * Never: the data is never overwritten. This option sets a lifelong protection for tapes. * Period: the data is protected for an indicated period. Use the Period and the Value parameters to indicate the period settings. * Cyclic: the data is not protected. The tapes are overwritten according to the tape rotation settings. | [VBRTapeMediaPoolRetentionType](enums.md#VBRTapeMediaPoolRetentionType) | False | Named | False |
| Period | Specifies the data retention period. Use this parameter to indicate the time period for the Type parameter:   * None: data is not protected. Tapes are overwritten according to the tape rotation settings. * Days: indicates that the data retention period is measured in days. Use the Value parameter to indicate the number of days to protect the data. * Weeks: indicates that the data retention period is measured in  weeks. Use the Value parameter to indicate the number of weeks to protect the data. * Months: indicates that the data retention period is measured in months. Use the Value parameter to indicate the number of months to protect the data. | [VBRTapeMediaPoolPeriod](enums.md#VBRTapeMediaPooPeriod) | False | Named | False |
| Value | Sets the number of days, weeks or month to protect the data. You can enter value between 1 and 999. Use this parameter to indicate the value if you set the Period parameter to Days, Weeks or Months. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMediaPoolRetentionPolicy](vbrtapemediapoolretentionpolicy.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Retention Period Rule for Media Pool

|  |  |
| --- | --- |
| This command defines media pool retention rules and saves the result to the $newretention variable. The retention rules contain the following settings:   * The retention period is set to 14 days.  * The Type is set to Period, the Period is set to Days, and the Value is set to 14.   |  | | --- | | $newretention = New-VBRTapeMediaPoolRetentionPolicy -Type Period -Period Days -Value 14 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Switching Off Data Retention for Media Pool

|  |  |
| --- | --- |
| This command defines media pool retention rules and saves the result to the $noretention variable. The Type is set to Cyclic.  |  | | --- | | $noretention = New-VBRTapeMediaPoolRetentionPolicy -Type Cyclic | |

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
