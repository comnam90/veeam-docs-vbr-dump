---
title: "Remove-NimbleHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-nimblehost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Remove-NimbleHost


Short Description

Removes HPE Nimble storage systems from Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-NimbleHost -Host <CNimbleHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected HPE Nimble storage from Veeam Backup & Replication.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to remove. | Accepts the CNimbleHost object. To get this object, run the [Get-NimbleHost](get-nimblehost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing HPE Nimble Storage

This example shows how to remove an HPE Nimble storage from Veeam Backup & Replication.

|  |
| --- |
| $storage = Get-NimbleHost -Name "HPE Nimble-FC"  Remove-NimbleHost -Host $storage |

Perform the following steps:

1. Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-NimbleHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-NimbleHost](get-nimblehost.md)


