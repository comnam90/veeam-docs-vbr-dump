---
title: "Get-VESPDocument"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespdocument.html"
last_updated: "5/6/2025"
product_version: "13.0.1.1071"
---

# Get-VESPDocument


Short Description

Returns SharePoint documents.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get documents from a specified SharePoint document library.

|  |
| --- |
| Get-VESPDocument [-DocumentLibrary] <VESPDocumentLibrary> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get child documents of a specified SharePoint document.

|  |
| --- |
| Get-VESPDocument [-ParentDocument] <VESPDocument> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get documents from a specified SharePoint database.

|  |
| --- |
| Get-VESPDocument [-Database] <VESPDatabase[]> [-Query <String>] [<CommonParameters>] |

* Get documents from a specified SharePoint organization.

|  |
| --- |
| Get-VESPDocument [-Organization] <VESPOrganization[]> [-Query <String>] [<CommonParameters>] |

* Get documents from a specified SharePoint site.

|  |
| --- |
| Get-VESPDocument [-Site] <VESPSite> [-Query <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns SharePoint documents.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DocumentLibrary | Specifies a document library. This cmdlet will return SharePoint documents from the specified document library. | Accepts the [VESPDocumentLibrary](vespdocumentlibrary.md) object. To get this object, run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. | True | 0 | True (ByValue) |
| Query | Specifies a query string for item search. The cmdlet will return items that match the search query from the specified database, organization, site, list or item.  For more information, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. | String | False | Named | False |
| Recurse | Defines that the cmdlet will return all child items of the specified parent item.  Default: False | SwitchParameter | False | Named | False |
| ParentDocument | Specifies a parent document. The cmdlet will return child documents of this parent document. | Accepts the [VESPDocument](vespdocument.md) object. To get this object, run the Get-VESPDocument cmdlet. | True | 0 | True (ByValue) |
| Database | Specifies an array of SharePoint databases. This cmdlet will return SharePoint documents from these databases.  Note: This parameter is available for SharePoint databases backed up by Veeam Backup & Replication. | Accepts the [VESPDatabase](vespdatabase.md)[] object. To get this object, run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Organization | Specifies an array of SharePoint organizations. The cmdlet will return SharePoint documents from these organizations. | Accepts the [VESPOrganization](vesporganization.md)[] object. To get this object, run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. | True | 0 | True (ByValue) |
| Site | Specifies a SharePoint site. This cmdlet will return SharePoint documents from this SharePoint site. | Accepts the [VESPSite](vespsite.md) object. To get this object, run the [Get-VESPSite](get-vespsite.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPDocument](vespdocument.md) array that contains SharePoint documents.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting SharePoint Document from Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get the reports.txt document from the Teams site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $site = Get-VESPSite -Database $database -Name "Teams"  Get-VESPDocument -Site $site -Query "reports.txt" |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the Get-VESPDocument cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SharePoint Document from Document Library [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a document with a name reports.txt from the Regulations SharePoint document library.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $documentLibrary = Get-VESPDocumentLibrary -Database $database -Name "Regulations"  Get-VESPDocument -DocumentLibrary $documentLibrary -Query "reports.txt" |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable. 4. Run the Get-VESPDocument cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Child Documents from SharePoint Document [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get child documents for the reports.txt SharePoint document.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPdatabase -Session $session -Name "WSS\_Content.mdf"  $documentLibrary = Get-VESPDocumentLibrary -Database $database -Name "Regulations"  $parentDocument = Get-VESPDocument -DocumentLibrary $documentLibrary -Query "reports.txt"  Get-VESPDocument -ParentDocument $parentDocument -Recurse |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable. 4. Run the Get-VESPDocument cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Query parameter value. Save the result to the $parentDocument variable. 5. Run the Get-VESPDocument cmdlet. Set the $parentDocument variable as the ParentDocument parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Documents from SharePoint Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all SharePoint documents from the WSS\_Content.mdf SharePoint database.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  Get-VESPDocument -Database $database |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPDocument cmdlet. Set the $database variable as the Database parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting SharePoint Document from Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the reports.txt document from the Teams site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $site = Get-VESPSite -Organization $organization -Name "Team Site"  Get-VESPDocument -Site $site -Query "reports.txt" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable.  1. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable. 2. Run the Get-VESPDocument cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting SharePoint Document from Document Library [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the report.txt document from the Regulations document library.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $documentLibrary = Get-VESPDocumentLibrary -Organization $organization -Name "Regulations"  Get-VESPDocument -DocumentLibrary $documentLibrary -Query "report.txt" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable.  1. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable. 2. Run the Get-VESPDocument cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Getting Child Documents from SharePoint Document [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get child documents for the reports.txt SharePoint document.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $documentLibrary = Get-VESPDocumentLibrary -Organization $organization -Name "Documents"  $parentDocument = Get-VESPDocument -DocumentLibrary $documentLibrary -Query "reports.txt"  Get-VESPDocument -ParentDocument $parentDocument -Recurse |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet, Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable.  1. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable.  1. Run the Get-VESPDocument cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Query parameter value. Save the result to the $parentDocument variable.  1. Run the Get-VESPDocument cmdlet. Set the $parentDocument variable as the ParentDocument parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 8. Getting Documents from SharePoint Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the reports.txt document from the ABC SharePoint organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  Get-VESPDocument -Organization $organization -Query "report.txt" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPDocument cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 9. Getting Documents from SharePoint Database [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get all SharePoint documents from the WSS\_Content.mdf SharePoint database.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  Get-VESPDocument -Database $database |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPDocument cmdlet. Set the $database variable as the Database parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)

* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPSite](get-vespsite.md)


