---
title: "Enable-VBRStorageCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrstoragecopyjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Enable-VBRStorageCopyJob


Short Description

Enables storage backup copy jobs.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRStorageCopyJob [-Job] <VBRStorageCopyJob[]> [-PassThru] [<CommonParameters>] |

Detailed Description

This cmdlet enables backup copy jobs for HPE StoreOnce and Dell Data Domain repositories.

Run the [Disable-VBRStorageCopyJob](disable-vbrstoragecopyjob.md) cmdlet to disable backup copy jobs for HPE StoreOnce and Dell Data Domain repositories.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Job | Specifies an array of storage backup copy jobs. The cmdlet will enable these jobs. | Accepts the VBRStorageCopyJob[] object. To get this object, run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of storage backup copy jobs.

Examples

Enabling Backup Copy Job for HPE StoreOnce Repository

This example shows how to enable the StoreOnce copy job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRStorageCopyJob -Name "StoreOnce copy job"  Enable-VBRStorageCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Enable-VBRStorageCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md)

Page updated 2026-07-21

