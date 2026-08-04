---
title: "Remove-VBRStorageCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrstoragecopyjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Remove-VBRStorageCopyJob


Short Description

Removes storage backup copy jobs from the backup infrastructure.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRStorageCopyJob [-Job] <VBRStorageCopyJob[]> [-Confirm] [-WhatIf] [<CommonParameters>] |

Detailed Description

This cmdlet removes storage backup copy jobs for HPE StoreOnce and Dell Data Domain repositories from the backup infrastructure.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Job | Specifies an array of storage backup copy jobs. The cmdlet will remove these jobs from the backup infrastructure. | Accepts the VBRStorageCopyJob object. To get this object, run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Removing Backup Copy Job for HPE StoreOnce Repository

This example shows how to remove the StoreOnce copy job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRStorageCopyJob -Name "StoreOnce copy job"  Remove-VBRStorageCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Remove-VBRStorageCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md)

Page updated 2026-07-21

