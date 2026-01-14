---
title: "Remove-VNXHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vnxhost.html"
last_updated: "12/11/2025"
product_version: "13.0.1.1071"
---

# Remove-VNXHost

In this article

Short Description

Removes Dell VNX storage systems from Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Remove-VNXHost -Host <CVnxHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes the selected Dell VNX storage from the Veeam Backup & Replication infrastructure.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage system you want to remove. | Accepts the CVnxHost object. To get this object, run the [Get-VNXHost](get-vnxhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Dell VNX Storage

This example shows how to remove the Dell VNX storage.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  Remove-VNXHost -Host $storage |

Perform the following steps:

1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-VNXHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-VNXHost](get-vnxhost.md)

Page updated 12/11/2025

Page content applies to build 13.0.1.1071
