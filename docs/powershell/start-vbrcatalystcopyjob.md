---
title: "Start-VBRCatalystCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcatalystcopyjob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Start-VBRCatalystCopyJob

In this article

Short Description

Starts backup copy jobs for HPE StoreOnce repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRCatalystCopyJob -Job <VBRCatalystCopyJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet starts backup copy jobs for HPE StoreOnce repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of backup copy jobs for HPE StoreOnce repositories. The cmdlet will start these jobs. | Accepts the VBRCatalystCopyJob[] object. To get this object, run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of backup copy jobs for HPE StoreOnce repositories.

Examples

Starting Backup Copy Job for HPE StoreOnce Repository

This example shows how to start the StoreOnce copy job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRCatalystCopyJob -Name "StoreOnce copy job"  Start-VBRCatalystCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Start-VBRCatalystCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
