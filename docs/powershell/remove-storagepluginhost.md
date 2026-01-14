---
title: "Remove-StoragePluginHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-storagepluginhost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Remove-StoragePluginHost

In this article

Short Description

Removes Universal Storage API integrated systems from Veeam Backup & Replication console.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Remove-StoragePluginHost -Host <CPublicPluginHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected storage from Veeam Backup & Replication console.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to remove. | Accepts the CPublicPluginHost object. To get the object, run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Selected Storage

This example shows how to remove a selected storage from Veeam Backup & Replication console.

|  |
| --- |
| $storage = Get-StoragePluginHost -Name "IBM Spectrum"  Remove-StoragePluginHost -Host $storage |

Perform the following steps:

1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-StoragePluginHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-StoragePluginHost](get-storagepluginhost.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
