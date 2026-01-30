---
title: "Remove-VBRTapeMedium"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRTapeMedium


Short Description

Removes the selected tapes from tape catalog.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRTapeMedium -Medium <VBRTapeMedium[]> [-FromVault] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes the selected tapes and the data written to the tapes from the tape catalog and Veeam backup database.

|  |
| --- |
| ![Remove-VBRTapeMedium](images/icon_note.webp) Note: |
| Consider the following:   * You can remove only offline tapes. * You cannot remove protected tapes. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the tapes you want to remove. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| FromVault | Defines that the cmdlet will remove the tape from the vault.  Note that the tape will not be removed from the tape catalog. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Tape from the Tape Catalog and Backup Database

This example shows how to remove the tape SWOHC001 from the tape catalog and Veeam backup database.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name SWOHC001  Remove-VBRTapeMedium -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save it to the $tape variable.
2. Run the Remove-VBRTapeMedium cmdlet. Set the $tape variable as the Medium parameter value.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)


