---
title: "Publish-StoragePluginArchivedSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/publish-storagepluginarchivedsnapshot.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Publish-StoragePluginArchivedSnapshot

In this article

Short Description

Retrieves and restores an archived snapshot.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Publish-StoragePluginArchivedSnapshot -Snapshot <CSanArchivedSnapshot> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet retrieves an archived snapshot and restores it to the storage system. An archived snapshots is a long-term snapshot offloaded to a 3rd party storage solution supported by a storage vendor.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the archived snapshot. The cmdlet will retrieve this archived snapshot and restore it to the storage system. | Accepts the CSanArchivedSnapshot object. To get this object, run the [Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md) cmdlet. | True | Named | False |
| Force | Defines that the cmdlet will retrieve and restore this archived snapshot without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBaseSession object that defines the restore session.

Examples

Retrieving and Restoring Data from Archived Snapshot

This example shows how to retrieve and restore the archived snapshot that has the pdcqastg11:-pure14-AAB97A18587ghudDaPRSF-t5kbsdr1E name.

|  |
| --- |
| $snapshot = Get-StoragePluginArchivedSnapshot -Name pdcqastg11:-pure14-AAB97A18587ghudDaPRSF-t5kbsdr1E  Publish-StoragePluginArchivedSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Run the [Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable.
2. Run the Publish-StoragePluginArchivedSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

[Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
