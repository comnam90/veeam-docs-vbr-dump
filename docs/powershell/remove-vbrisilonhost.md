---
title: "Remove-VBRIsilonHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrisilonhost.html"
last_updated: "2/19/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRIsilonHost


Short Description

Removes Dell PowerScale (formerly Isilon) storage systems from Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRIsilonHost -Host <CIsilonHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected Dell PowerScale storage from Veeam Backup & Replication.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CIsilonHost object. To create this object, run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Dell PowerScale Storage

This example shows how to remove the Dell PowerScale storage.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  Remove-VNXHost -Host $storage |

Perform the following steps:

1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-VBRIsilonHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-VBRIsilonHost](get-vbrisilonhost.md)


