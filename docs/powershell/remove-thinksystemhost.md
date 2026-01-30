---
title: "Remove-ThinkSystemHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-thinksystemhost.html"
last_updated: "4/22/2024"
product_version: "13.0.1.1071"
---

# Remove-ThinkSystemHost


Short Description

Removes ThinkSystem storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-ThinkSystemHost -Host <CNaHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected ThinkSystem storage from Veeam Backup & Replication.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to remove. | Accepts the CNaHost object. To create this object, run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing ThinkSystem Storage System

This example shows how to remove a ThinkSystem storage system from Veeam Backup & Replication.

|  |
| --- |
| $storage = Get-ThinkSystemHost -Name "ThinkSystem Store 01"  Remove-ThinkSystemHost -Host $storage |

Perform the following steps:

1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-ThinkSystemHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-ThinkSystemHost](get-thinksystemhost.md)


