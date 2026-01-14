---
title: "Remove-HP3Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-hp3storage.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Remove-HP3Storage

In this article

Short Description

Removes HPE 3PAR StoreServ storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Remove-HP3Storage -Storage <CHp3PARHost>  [<CommonParameters>] |

Detailed Description

This cmdlet removes the selected HPE 3PAR StoreServ storage from Veeam Backup & Replication.

The storage is not deleted from the server where it was created. When you remove a storage, you stop managing it in your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Storage | Specifies the storage you want to remove. | Accepts the CHp3PARHost object. To get this object, run the [Get-HP3Storage](get-hp3storage.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing HPE 3PAR StoreServ Storage

This example shows how to remove the HPE 3PAR StoreServ storage.

|  |
| --- |
| $storage = Get-HP3Storage -Name "HPE 3PAR StoreServe Storage"  Remove-HP3Storage -Storage $storage |

Perform the following steps:

1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Remove-HP3Storage cmdlet. Set the $storage variable as the Storage parameter value.

Related Commands

[Get-HP3Storage](get-hp3storage.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
