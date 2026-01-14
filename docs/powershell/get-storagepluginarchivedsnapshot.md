---
title: "Get-StoragePluginArchivedSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-storagepluginarchivedsnapshot.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-StoragePluginArchivedSnapshot

In this article

Short Description

Returns archived snapshots of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-StoragePluginArchivedSnapshot [-Name <String[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns archived snapshots of Universal Storage API integrated systems. Archived snapshots are long-term snapshots offloaded to a 3rd party storage solution supported by a storage vendor.

If you do not specify any parameter, the cmdlet will return all archived snapshots that Veeam Backup & Replication detected during the latest rescan.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of the archived snapshot that you want to get. | String[] | False | Named | False |
| Volume | Specifies an array of storage volumes where you want to search for archived snapshots. | Accepts the CSanVolume[] object. To get this object, run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CSanArchivedSnapshot[] object that defines archived snapshot settings.

Examples

Getting Archived Snapshot by Name

This cmdlet returns the archived snapshot with the pdcqastg11:-pure14-AAB97A18587ghudDaPRSF-t5kbsdr1E name.

|  |
| --- |
| Get-StoragePluginArchivedSnapshot -Name pdcqastg11:-pure14-AAB97A18587ghudDaPRSF-t5kbsdr1E |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
