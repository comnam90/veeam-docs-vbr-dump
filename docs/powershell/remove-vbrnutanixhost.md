---
title: "Remove-VBRNutanixHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrnutanixhost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRNutanixHost


Short Description

Removes Nutanix Files storage systems from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRNutanixHost -Host <CNutanixHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a Nutanix Files storage system from the backup infrastructure. Note that the storage itself is not removed.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage system that you want to remove. | Accepts the CNutanixHost object. To create this object, run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Modifying Port Number of Nutanix Files Storage Systems

This example shows how to modify the port number of Nutanix Files Storage Systems.

|  |
| --- |
| $host = Get-VBRNutanixHost -Name "Nutanix Files\_host"  Remove-VBRNutanixHost -Host $host |

Perform the following steps:

1. Run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable.
2. Run the Remove-VBRNutanixHost cmdlet. Set the $host variable as the Host parameter value.

Related Commands

[Get-VBRNutanixHost](get-vbrnutanixhost.md)


