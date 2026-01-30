---
title: "Remove-ThinkSystemSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-thinksystemsnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Remove-ThinkSystemSnapshot


Short Description

Removes ThinkSystem storage snapshots.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-ThinkSystemSnapshot -Snapshot <CSanSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes a selected ThinkSystem storage snapshot from your virtual infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the array of snapshots. The cmdlet will remove these snapshots. | Accepts the CSanSnapshot object. To create this object, run the [Get-ThinkSystemSnapshot](get-thinksystemsnapshot.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing ThinkSystem Storage Snapshot

This example shows how to remove the ThinkSystem storage snapshot.

|  |
| --- |
| $snapshot = Get-ThinkSystemSnapshot -Name "vol1\_SS\_1"  Remove-ThinkSystemSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Run the [Get-ThinkSystemSnapshot](get-thinksystemsnapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable.
2. Run the Remove-ThinkSystemSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

[Get-ThinkSystemSnapshot](get-thinksystemsnapshot.md)


