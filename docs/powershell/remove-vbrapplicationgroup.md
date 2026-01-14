---
title: "Remove-VBRApplicationGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrapplicationgroup.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRApplicationGroup

In this article

Short Description

Removes application groups from the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRApplicationGroup -ApplicationGroup <VBRApplicationGroup> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes application groups from the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ApplicationGroup | Specifies an application group. The cmdlet will remove this application group the Veeam Backup & Replication infrastructure. | Accepts the VBRApplicationGroup object. To get this object, run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParamter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Application Groups

This example shows how to remove an application group from the Veeam Backup & Replication infrastructure.

|  |
| --- |
| $group = Get-VBRApplicationGroup -Name "Exchange Application Group"  Remove-VBRApplicationGroup -ApplicationGroup $group |

Perform the following steps:

1. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the Remove-VBRApplicationGroup cmdlet. Set the $group variable as the ApplicationGroup parameter value.

Related Commands

[Get-VBRApplicationGroup](get-vbrapplicationgroup.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
