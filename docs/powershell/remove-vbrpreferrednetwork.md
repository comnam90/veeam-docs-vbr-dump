---
title: "Remove-VBRPreferredNetwork"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrpreferrednetwork.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRPreferredNetwork

In this article

Short Description

Removes preferred networks.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRPreferredNetwork -Network <VBRPreferredNetwork[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes an array of preferred networks created for the backup infrastructure. The cmdlet will remove all preferred networks added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Network | Specifies an array of preferred networks that you want to remove. | Accepts the [VBRPreferredNetwork](vbrpreferrednetwork.md)[] object. To get the object, run the [Get-VBRPreferredNetwork](get-vbrpreferrednetwork.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Preferred Network

This example shows how to remove preferred networks added to the backup infrastructure.

|  |
| --- |
| $network = Get-VBRPreferredNetwork  Remove-VBRNetworkTrafficRule -Network $network |

Perform the following steps:

1. Run the [Get-VBRPreferredNetwork](get-vbrpreferrednetwork.md) cmdlet. Save the result to the $network variable.
2. Run the Remove-VBRNetworkTrafficRule cmdlet. Set the $network variable as the Network parameter value.

Related Commands

[Get-VBRPreferredNetwork](get-vbrpreferrednetwork.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
