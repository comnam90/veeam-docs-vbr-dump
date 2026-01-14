---
title: "Remove-HyperFlexHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-hyperflexhost.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-HyperFlexHost

In this article

Short Description

Removes Cisco HyperFlex storage systems from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-HyperFlexHost -Host <CCiscoHxHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes Cisco HyperFlex storage from the backup infrastructure.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to remove. | Accepts the CCiscoHxHost object. To create this object, run the [Get-HyperFlexHost](get-hyperflexhost.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Cisco HyperFlex Storage

This example shows how to remove the HX Storage Cisco HyperFlex storage.

|  |
| --- |
| $storage = Get-HyperFlexHost -Name "HX Storage"  Remove-HyperFlexHost -Host $storage |

Perform the following steps:

1. Run the [Get-HyperFlexHost](get-hyperflexhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-HyperFlexHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-HyperFlexHost](get-hyperflexhost.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
