---
title: "Remove-VBRLocation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrlocation.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRLocation


Short Description

Removes geographic locations from Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRLocation -Location <VBRLocation[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes geographic locations from the Veeam Backup & Replication database.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Location | Specifies the array of locations you want to remove. | Accepts the VBRLocation[] object. To get this object, run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Selected Geographic Location

|  |  |
| --- | --- |
| This example shows how to remove a selected geographic location from Veeam Backup & Replication.  |  | | --- | | $location = Get-VBRLocation -Name "Sacramento"  Remove-VBRLocation -Location $location |  Perform the following steps:   1. Run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. Specify the Name parameter value. Save the result to the $location variable. 2. Run the Remove-VBRLocation cmdlet. Set the $location variable as the Location parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Several Geographic Locations

|  |  |
| --- | --- |
| This example shows how to remove several geographic locations from Veeam Backup & Replication.  |  | | --- | | $locations = Get-VBRLocation -Name North\*  Remove-VBRLocation -Location $locations |  Perform the following steps:   1. Run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. Specify the Name parameter value. Save the result to the $locations variable. 2. Run the Remove-VBRLocation cmdlet. Set the $locations variable as the Location parameter value. |

Related Commands

[Get-VBRLocation](get-vbrlocation.md)


