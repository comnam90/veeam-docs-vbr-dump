---
title: "Reset-VSBJobOptions (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vsbjoboptions.html"
last_updated: "2/26/2024"
product_version: "13.0.1.1071"
---

# Reset-VSBJobOptions (obsolete)


Short Description

Sets SureBackup job settings to default.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VSBJobOptions -Job <CSbJob> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet clears the custom settings of the specified SureBackup job and restores their default values.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the SureBackup job you want to edit. | Accepts the CSbJob object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Default Settings to Selected SureBackup Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to reset SureBackup Job 1 and SureBackup Job 2 SureBackup jobs to default settings.  |  | | --- | | Get-VSBJob -Name "SureBackup Job 1", "SureBackup Job 2" | Reset-VSBJobOptions |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Reset-VSBJobOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Default Settings to Selected SureBackup Jobs [Using Variable]

|  |  |
| --- | --- |
| This example shows how to reset SureBackup Job 1 and SureBackup Job 2 SureBackup jobs to default settings.  |  | | --- | | $SureJob = Get-VSBJob -Name "SureBackup Job 1", "SureBackup Job 2"  Reset-VSBJobOptions -Job $SureJob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. Save the result to the $SureJob variable. 2. Run the Reset-VSBJobOptions cmdlet. Set the $SureJob as the Job parameter value. |

Related Commands

[Get-VSBJob](get-vsbjob.md)


