---
title: "Remove-VBRCatalystCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcatalystcopyjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRCatalystCopyJob


Short Description

Removes backup copy jobs for HPE StoreOnce repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCatalystCopyJob -Job <VBRCatalystCopyJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup copy jobs for HPE StoreOnce repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of backup copy jobs for HPE StoreOnce repositories. The cmdlet will remove these jobs. | Accepts the VBRCatalystCopyJob[] object. To get this object, run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
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
| $job = Get-VBRCatalystCopyJob -Name "StoreOnce copy job"  Remove-VBRCatalystCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Remove-VBRCatalystCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md)


