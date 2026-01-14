---
title: "Remove-StoragePluginArchivedSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-storagepluginarchivedsnapshot.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-StoragePluginArchivedSnapshot

In this article

Short Description

Removes archived snapshots of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-StoragePluginArchivedSnapshot -Snapshot <CSanArchivedSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet removes archived snapshots of Universal Storage API integrated systems. Archived snapshots are long-term snapshots offloaded to a 3rd party storage solution supported by a storage vendor.

|  |
| --- |
| Tip |
| To remove the retrieved version of the archived snapshot, use the [Remove-StoragePluginSnapshot](remove-storagepluginsnapshot.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the archived snapshot that you plan to remove. | Accepts the CSanArchivedSnapshot[] object. To get this object, run the [Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBaseSession object that defines the removal session.

Examples

Removing Snapshot

This example shows how to remove the archived snapshot that has the pdcqastg11:-pure14-AAB97A18587ghudDaPRSF-t5kbsdr1E name.

|  |
| --- |
| $snapshot = Get-StoragePluginArchivedSnapshot -Name pdcqastg11:-pure14-AAB97A18587ghudDaPRSF-t5kbsdr1E  Remove-StoragePluginArchivedSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Run the [Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable.
2. Run the Remove-StoragePluginArchivedSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

[Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
