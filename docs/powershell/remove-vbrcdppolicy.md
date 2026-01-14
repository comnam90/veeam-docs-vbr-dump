---
title: "Remove-VBRCDPPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcdppolicy.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCDPPolicy

In this article

Short Description

Removes CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCDPPolicy -Policy <VBRCDPPolicyBase[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies an array of the CDP policies that you want to remove. | Accepts the VBRCDPPolicyBase[] object. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing all Policies

This example shows how to remove all CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

|  |
| --- |
| $policy = Get-VBRCDPPolicy  Remove-VBRCDPPolicy -Policy $policy |

Perform the following steps:

1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Save the result to the $policy variable.
2. Run the Remove-VBRCDPPolicy cmdlet. Set the $policy variable as the Policy parameter value.

Related Commands

[Get-VBRCDPPolicy](get-vbrcdppolicy.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
