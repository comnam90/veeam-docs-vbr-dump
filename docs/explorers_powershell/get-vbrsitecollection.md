---
title: "Get-VBRSiteCollection"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vbrsitecollection.html"
last_updated: "3/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRSiteCollection


Short Description

Returns site collections for Microsoft SharePoint.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSiteCollection -RestorePoint <VBRApplicationRestorePoint[]> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of site collections for Microsoft SharePoint.

|  |
| --- |
| Note |
| This cmdlet is available for backups created with Veeam Backup & Replication. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies restore points. The cmdlet will get Microsoft SharePoint site collections from the specified restore points. | Accepts the [VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13)[] object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [IVBRSiteCollection](vbrsitecollection.md)[] object that contains an array of site collections for Microsoft SharePoint.

Example

Getting All Microsoft SharePoint Site Collections

This example shows how to get all Microsoft SharePoint site collections from a restore point.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -SharePoint -Name "SharePoint server"  Get-VBRSiteCollection -RestorePoint $restorepoint |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SharePoint parameter. Specify the Name parameter value. Save the result to the $restorepoint variable.
2. Run the Get-VBRSiteCollection cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.

Related Commands

[Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)


