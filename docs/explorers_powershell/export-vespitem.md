---
title: "Export-VESPItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-vespitem.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Exports SharePoint items.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export to the SharePoint document library.

|  |
| --- |
| Export-VESPItem [-DocumentLibrary] <VESPDocumentLibrary> -Path <String> [-Force] [<CommonParameters>] |

* Export to the SharePoint list.

|  |
| --- |
| Export-VESPItem [-List] <VESPList> -Path <String> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet exports SharePoint lists and document libraries.

|  |
| --- |
| Note |
| Consider the following:   * This cmdlet is available for backups created with Veeam Backup & Replication. * Before performing export operations, you must first start a restore session. For more information, see [Start-VBRSharePointItemRestoreSession](start-vbrsharepointitemrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DocumentLibrary | Specifies a SharePoint document library. This cmdlet will export the specified SharePoint document library. | Accepts the [VESPDocumentLibrary](vespdocumentlibrary.md) object. To get this object, run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a path to the export destination directory. | String | True | Named | True (ByValue) |
| Force | Defines that the cmdlet will create a folder in the specified directory and will overwrite the existing item with the same name.  Default: False | SwitchParameter | False | Named | False |
| List | Specifies a SharePoint list. This cmdlet will export the specified SharePoint list. | Accepts the [VESPList](vesplist.md) object. To get this object, run the [Get-VESPList](get-vesplist.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting SharePoint Document Library [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to export the SharePoint document library to the C:\ExportedDocLibrary folder.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $doclib = Get-VESPDocumentLibrary -Database $database -Name "Document\_Library"  Export-VESPItem -DocumentLibrary $doclib -Path "C:\ExportedDocLibrary" -Force |  Perform the following steps:   1. Get the SharePoint document library:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $doclib variable.  1. Run the Export-VESPItem cmdlet. Set the $doclib variable as the DocumentLibrary parameter value. Specify the Path parameter value. Provide the Force parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting SharePoint List [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to export the Calendar SharePoint list to the C:\ExportedLists folder.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SharePoint -Name "SharePoint server"  $session = Start-VBRSharePointItemRestoreSession -RestorePoint $restorePoint  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $site = Get-VESPSite -Database $database -Name "Home"  $list = Get-VESPList -Site $site -Name "Calendar"  Export-VESPItem -List $list -Path C:\ExportedLists -Force |  Perform the following steps:   1. Get the SharePoint list:  1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Specify the SharePoint parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the [Start-VBRSharePointItemRestoreSession](start-vbrsharepointitemrestoresession.md) cmdlet. Set the $restorePoint variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 4. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable. 5. Run the [Get-VESPList](get-vesplist.md) cmdlet. Set the $site variable as the Site parameter value. Specify the Name parameter value. Save the result to the $list variable.  1. Run the Export-VESPItem cmdlet. Set the $list variable as the List parameter value. Specify the Path parameter value. Provide the Force parameter. |

Related Commands

* [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)

* [Start-VBRSharePointItemRestoreSession](start-vbrsharepointitemrestoresession.md)
* [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPSite](get-vespsite.md)
* [Get-VESPList](get-vesplist.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
