---
title: "Remove-NetAppHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-netapphost.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-NetAppHost


Short Description

Removes NetApp storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-NetAppHost -Host <CNaHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected NetApp storage from Veeam Backup & Replication.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to remove. | Accepts the CNaHost object. To get this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing NetApp Storage

This example shows how to remove a NetApp storage from Veeam Backup & Replication.

|  |
| --- |
| $storage = Get-NetAppHost -Name "NetApp Store 01"  Remove-NetAppHost -Host $storage |

Perform the following steps:

1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-NetAppHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-NetAppHost](get-netapphost.md)


