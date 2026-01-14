---
title: "Enable-VBRProtectionGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrprotectiongroup.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRProtectionGroup

In this article

Short Description

Enables automatic discovery for the protection group computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRProtectionGroup -ProtectionGroup <VBRProtectionGroup[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet enables automatic discovery for selected protection groups. Automatic discovery is performed per discovery schedule configured for the protection group.

Run the [Disable-VBRProtectionGroup](disable-vbrprotectiongroup.md) cmdlet to disable automatic discovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ProtectionGroup | Specifies the array of protection groups. The cmdlet will enable automatic discovery for these protection groups. | Accepts the [VBRProtectionGroup[]](vbrprotectiongroup.md) object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Automatic Discovery for Computers of Protection Group

This example shows how to enable automatic discovery for the computers of the protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "East Computers"  Enable-VBRProtectionGroup -ProtectionGroup $group |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the Enable-VBRProtectionGroup cmdlet. Set the $group variable as the ProtectionGroup parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Disable-VBRProtectionGroup](disable-vbrprotectiongroup.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
