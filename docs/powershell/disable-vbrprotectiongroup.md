---
title: "Disable-VBRProtectionGroup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrprotectiongroup.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRProtectionGroup


Short Description

Disables automatic discovery for the protection group computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRProtectionGroup -ProtectionGroup <VBRProtectionGroup[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables automatic discovery for the computers of selected protection groups.

Run the [Enable-VBRProtectionGroup](enable-vbrprotectiongroup.md) cmdlet to enable automatic discovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ProtectionGroup | Specifies the array of protection groups. The cmdlet will disable automatic discovery for the computers of these protection groups. | Accepts the [VBRProtectionGroup[]](vbrprotectiongroup.md) object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Automatic Discovery for Computers of Protection Group

This example shows how to disable automatic discovery for the computers of a protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "East Computers"  Disable-VBRProtectionGroup -ProtectionGroup $group |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the Disable-VBRProtectionGroup cmdlet. Set the $group variable as the ProtectionGroup parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Enable-VBRProtectionGroup](enable-vbrprotectiongroup.md)


