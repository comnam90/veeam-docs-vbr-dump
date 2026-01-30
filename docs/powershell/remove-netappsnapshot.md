---
title: "Remove-NetAppSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-netappsnapshot.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-NetAppSnapshot


Short Description

Removes NetApp storage snapshots.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-NetAppSnapshot -Snapshot <CSanSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes a selected NetApp storage snapshot from your virtual infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the array of snapshots. The cmdlet will remove these snapshots. | Accepts the CSanSnapshot[] object. To get this object, run the [Get-NetAppSnapshot](get-netappsnapshot.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing NetApp Storage Snapshot

This example shows how to remove the NetApp storage snapshot.

|  |
| --- |
| $snapshot = Get-NetAppSnapshot -Name "vol1\_SS\_1"  Remove-NetAppSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Run the [Get-NetAppSnapshot](get-netappsnapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable.
2. Run the Remove-NetAppSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

[Get-NetAppSnapshot](get-netappsnapshot.md)


