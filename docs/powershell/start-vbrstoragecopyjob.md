---
title: "Start-VBRStorageCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrstoragecopyjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRStorageCopyJob


Short Description

Starts storage backup copy jobs.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRStorageCopyJob [-Job] <VBRStorageCopyJob[]> [<CommonParameters>] |

Detailed Description

This cmdlet starts storage backup copy jobs for HPE StoreOnce and Dell Data Domain repositories.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Job | Specifies an array of storage backup copy jobs. The cmdlet will start these jobs. | Accepts the VBRStorageCopyJob[] object. To get this object, run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRStorageCopyJob object that contains settings of storage backup copy jobs.

Examples

Starting Backup Copy Job for HPE StoreOnce Repository

This example shows how to start the StoreOnce Copy Job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRStorageCopyJob -Name "StoreOnce Copy Job"  Start-VBRStorageCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Start-VBRStorageCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md)

Page updated 2026-07-21

