---
title: "Get-VBRSiteCollectionRestorePoint"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vbrsitecollectionrestorepoint.html"
last_updated: "3/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRSiteCollectionRestorePoint


Short Description

Returns restore points of backed-up machines with Microsoft SQL databases for the specified Microsoft SharePoint site collection.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSiteCollectionRestorePoint -SiteCollection <VBRSiteCollection> [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of backed-up machines with Microsoft SQL databases for the specified Microsoft SharePoint site collection.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SiteCollection | Specifies a site collection for Microsoft SharePoint. The cmdlet will return restore points of backed-up machines with Microsoft SQL databases for these site collections. | Accepts the [VBRSiteCollection](vbrsitecollection.md) object. To get this object, run the [Get-VBRSiteCollection](get-vbrsitecollection.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBRSiteCollectionRestorePoint](vbrsitecollectionrestorepoint.md)[] array that contains restore points of backed-up machines with Microsoft SQL databases for the specified SharePoint site collection.

Example

Getting All Restore Points of Machines with Microsoft SQL Databases for Microsoft SharePoint Site Collections

This example shows how to get all restore points of backed-up machines with Microsoft SQL databases for the SharePoint server SharePoint site collection.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -SharePoint -Name "SharePoint server"  $site = Get-VBRSiteCollection -RestorePoint $restorepoint  Get-VBRSiteCollectionRestorePoint -SiteCollection $site |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SharePoint parameter. Specify the Name parameter value. Save the result to the $restorepoint variable.
2. Run the [Get-VBRSiteCollection](get-vbrsitecollection.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $site variable.
3. Run the Get-VBRSiteCollectionRestorePoint cmdlet. Set the $site variable as the SiteCollection parameter value.

Related Commands

* [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)
* [Get-VBRSiteCollection](get-vbrsitecollection.md)


