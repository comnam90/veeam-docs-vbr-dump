---
title: "Get-VESPDocumentVersion"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespdocumentversion.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VESPDocumentVersion


Short Description

Returns other versions of a SharePoint document.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPDocumentVersion [-Document] <VESPDocument> [<CommonParameters>] |

Detailed Description

This cmdlet returns other versions of a SharePoint document.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Document | Specifies a SharePoint document. This cmdlet will return other versions of this SharePoint document. | Accepts the [VESPDocument](vespdocument.md) object. To get this object, run the [Get-VESPDocument](get-vespdocument.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns a [VESPDocument](vespdocument.md)[] array that contains other versions of the specified SharePoint document.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Version of SharePoint Document from Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a version of the reports.txt document from the Teams site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $site = Get-VESPSite -Database $database -Name "Teams"  $document = Get-VESPDocument -Site $site -Query "reports.txt"  Get-VESPDocumentVersion -Document $document |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. Save the result to the $document variable. 5. Run the Get-VESPDocumentVersion cmdlet. Set the $document variable as the Document parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Version of SharePoint Document from Document Library [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a version of the reports.txt document from the Regulations SharePoint document library.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $documentLibrary = Get-VESPDocumentLibrary -Database $database -Name "Regulations"  $document = Get-VESPDocument -DocumentLibrary $documentLibrary -Query "reports.txt"  Get-VESPDocumentVersion -Document $document |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable. 4. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Query parameter value. Save the result to the $document variable. 5. Run the Get-VESPDocumentVersion cmdlet. Set the $document variable as the Document parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Version of SharePoint Document from Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a version of the reports.txt document from the Teams site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $site = Get-VESPSite -Organization $organization -Name "Team Site"  $document = Get-VESPDocument -Site $site -Query "reports.txt"  Get-VESPDocumentVersion -Document $document |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable.  1. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable. 2. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. Save the result to the $document variable. 3. Run the Get-VESPDocumentVersion cmdlet. Set the $document variable as the Document parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Version of SharePoint Document from Document Library [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a version of the reports.txt document from the Regulations SharePoint document library.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $documentLibrary = Get-VESPDocumentLibrary -Organization $organization -Name "Regulations"  $document = Get-VESPDocument -DocumentLibrary $documentLibrary -Query "report.txt"  Get-VESPDocumentVersion -Document $document |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable.  1. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable. 2. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Query parameter value. Save the result to the $document variable. 3. Run the Get-VESPDocumentVersion cmdlet. Set the $document variable as the Document parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Version of SharePoint Document from Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a version of the reports.txt document from the ABC SharePoint organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $document = Get-VESPDocument -Organization $organization -Query "report.txt"  Get-VESPDocumentVersion -Document $document |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $document variable. 4. Run the Get-VESPDocumentVersion cmdlet. Set the $document variable as the Document parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPSite](get-vespsite.md)
* [Get-VESPDocument](get-vespdocument.md)


