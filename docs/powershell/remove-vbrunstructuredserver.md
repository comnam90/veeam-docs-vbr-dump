---
title: "Remove-VBRUnstructuredServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrunstructuredserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRUnstructuredServer

In this article

Short Description

Removes unstructured data sources from the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRUnstructuredServer -Server <VBRUnstructuredServer[]> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet removes unstructured data sources from the inventory.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an array of unstructured data sources. The cmdlet will remove these unstructured data sources from the inventory. | Accepts the VBRUnstructuredServer[] object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing all Unstructured Data Sources

|  |  |
| --- | --- |
| This example shows how to remove all unstructured data sources from the inventory.  |  | | --- | | $server = Get-VBRUnstructuredServer  Remove-VBRUnstructuredServer -Server $server |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Save the result to the $server variable. 2. Run the Remove-VBRUnstructuredServer cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Certain Unstructured Data Sources from Inventory

|  |  |
| --- | --- |
| This example shows how to remove the \\WinSRV2049\Documents file share from the inventory. The cmdlet will display a prompt that asks if the user is sure that he wants to continue.  |  | | --- | | $fileshare = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  Remove-VBRUnstructuredServer -Server $fileshare -Confirm |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $fileshare variable. 2. Run the Remove-VBRUnstructuredServer cmdlet. Set the $fileshare variable as the Server parameter value. Provide the Confirm parameter. |

Related Commands

[Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
