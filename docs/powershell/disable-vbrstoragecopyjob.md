---
title: "Disable-VBRStorageCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrstoragecopyjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disable-VBRStorageCopyJob


Short Description

Disables storage backup copy jobs.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRStorageCopyJob [-Job] <VBRStorageCopyJob[]> [-PassThru] [-Confirm] [-WhatIf] [<CommonParameters>] |

Detailed Description

This cmdlet disables storage backup copy jobs for HPE StoreOnce and Dell Data Domain repositories.

Run the [Enable-VBRStorageCopyJob](enable-vbrstoragecopyjob.md) cmdlet to enable storage backup copy jobs.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Job | Specifies an array of storage backup copy jobs. The cmdlet will disable these jobs. | Accepts the VBRStorageCopyJob[] object. To get this object, run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRStorageCopyJob object that contains settings of storage backup copy jobs.

Examples

Disabling Backup Copy Job for HPE StoreOnce Repository

This example shows how to disable the StoreOnce copy job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRStorageCopyJob -Name "StoreOnce copy job"  Disable-VBRStorageCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Disable-VBRStorageCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md)

Page updated 2026-07-21

