---
title: "Remove-VBRFiler"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrfiler.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRFiler


Short Description

Removes an enterprise NAS system added to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRFiler -Filer <VBRFiler[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes an enterprise NAS system from the inventory.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Filer | Specifies an enterprise NAS system that you want to remove from the inventory. | Accepts the VBRFiler[] object. To create this object, run the [Get-VBRFiler](get-vbrfiler.md) cmdlet. | True | Named | True(ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Enterprise NAS System

This cmdlet removes an enterprise NAS system from the inventory.

|  |
| --- |
| $filer = Get-VBRFiler -Name "ontap-2"  Remove-VBRFiler -Filer $filer |

Perform the following steps:

1. Run the [Get-VBRFiler](get-vbrfiler.md) cmdlet. Specify the Name parameter value. Save the result to the $filer variable.
2. Run the Remove-VBRFiler cmdlet. Set the $filer variable as the Filer parameter value.

Related Commands

[Get-VBRFiler](get-vbrfiler.md)


