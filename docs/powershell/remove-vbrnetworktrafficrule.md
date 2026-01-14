---
title: "Remove-VBRNetworkTrafficRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrnetworktrafficrule.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRNetworkTrafficRule

In this article

Short Description

Removes network traffic rules.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRNetworkTrafficRule -Rule <VBRNetworkTrafficRule[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes network traffic rules from the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Rule | Specifies an array of network traffic rules that you want to remove. | Accepts the [VBRNetworkTrafficRule](vbrnetworktrafficrule.md)[] object. To get this object, run the [Get-VBRNetworkTrafficRule](get-vbrnetworktrafficrule.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Network Traffic Rule

This example shows how to remove a network traffic rule from the backup infrastructure.

|  |
| --- |
| $rule = Get-VBRNetworkTrafficRule -Name "Rule #5"  Remove-VBRNetworkTrafficRule -Rule $rule |

Perform the following steps:

1. Run the [Get-VBRNetworkTrafficRule](get-vbrnetworktrafficrule.md) cmdlet. Specify the Name parameter value. Save the result to the $rule variable.
2. Run the Remove-VBRNetworkTrafficRule cmdlet. Set the $rule variable as the Rule parameter value.

Related Commands

[Get-VBRNetworkTrafficRule](get-vbrnetworktrafficrule.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
