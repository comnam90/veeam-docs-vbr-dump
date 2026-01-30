---
title: "Save-VESPItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/save-vespitem.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Save-VESPItem


Short Description

Saves SharePoint items.

Applies to

Veeam Backup for Microsoft 365, Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Save a SharePoint document library.

|  |
| --- |
| Save-VESPItem [-DocumentLibrary] <VESPDocumentLibrary> [-Path] <String> [-AsZip] [-Force] [<CommonParameters>] |

* Save a specific SharePoint document.

|  |
| --- |
| Save-VESPItem [-Document] <VESPDocument[]> [-Path] <String> [-AsZip] [-Force] [<CommonParameters>] |

* Save a SharePoint attached item.

|  |
| --- |
| Save-VESPItem [-ItemAttachment] <VESPItemAttachment[]> [-Path] <String> [-AsZip] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet saves SharePoint items such as document libraries, documents and attached items.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DocumentLibrary | Specifies a SharePoint document library that you want to save. | Accepts the [VESPDocumentLibrary](vespdocumentlibrary.md) object. To get this object, run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a path to the specified item. | String | True | 1 | True (ByValue) |
| AsZip | Defines that the cmdlet will save the specified item as a ZIP archive.  Default: False | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will create a folder in the specified directory.  Default: False | SwitchParameter | False | Named | False |
| Document | Specifies an array of SharePoint documents that you want to save. | Accepts the [VESPDocument](vespdocument.md)[] object. To get this object, run the [Get-VESPDocument](get-vespdocument.md) cmdlet. | True | 0 | True (ByValue) |
| ItemAttachment | Specifies an array of SharePoint item attachments that you want to save. | Accepts the [VESPItemAttachment](vespitemattachment.md)[]object. To get this object, run the [Get-VESPItemAttachment](get-vespitemattachment.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Saving SharePoint Document Library [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to save the Regulations document library to the C:\save path.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $documentLibrary = Get-VESPDocumentLibrary -Database $database -Name "Regulations"  Save-VESPItem -DocumentLibrary $documentLibrary -Path "C:\save" |  Perform the following steps:   1. Get the SharePoint document library:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable.  1. Run the Save-VESPItem cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Saving SharePoint Document [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to save the reports.txt document to the C:\save path.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $document = Get-VESPDocument -Database $database -Query "reports.txt"  Save-VESPItem -Document $document -Path "C:\save" |  Perform the following steps:   1. Get the SharePoint document:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. Save the result to the $document variable.  1. Run the Save-VESPItem cmdlet. Set the $document variable as the Document parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Saving SharePoint Item Attachment [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to save attachments for the Documents item to the C:\save path.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $item = Get-VESPItem -Database $database -Query "Reports"  $attachment = Get-VESPItemAttachment -Item $item  Save-VESPItem -ItemAttachment $attachment -Path "C:\save" |  Perform the following steps:   1. Get the SharePoint item:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. Save the result to the $item variable. 4. Run the [Get-VESPItemAttachment](get-vespitemattachment.md) cmdlet. Set the $item variable as the Item parameter value. Save the result to the $attachment variable.  1. Run the Save-VESPItem cmdlet. Set the $attachment variable as the ItemAttachment parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Saving SharePoint Document Library [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to save the Regulations document library to the C:\save path.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $documentLibrary = Get-VESPDocumentLibrary -Organization $organization -Name "Regulations"  Save-VESPItem -DocumentLibrary $documentLibrary -Path "C:\save" |  Perform the following steps:   1. Get the SharePoint document library:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable.  1. Run the Save-VESPItem cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Saving SharePoint Document Library from Specific Backup Job [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to save the Regulations document library created by a specific backup job to the ZIP archive file.  |  | | --- | | $session = Start-VBOSharePointItemRestoreSession -Job $Job -LatestState  $organization = Get-VESPOrganization -Session $session  $site = Get-VESPSite -Organization $organization -Name "Site"  $documentLibrary = Get-VESPDocumentLibrary -Site $site -Name "Regulations"  Save-VESPItem -DocumentLibrary $documentLibrary -Path "C:\Save\archive.zip" -AsZip |  Perform the following steps:   1. Get the SharePoint document library:  1. Run the [Start-VBOSharePointItemRestoreSession](start-vbosharepointitemrestoresession.md) cmdlet. Specify the Job parameter value. Provide the LatestState parameter. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $organization variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $site variable as the Site parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable.  1. Run the Save-VESPItem cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the Path parameter value. Provide the AsZip parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Saving SharePoint Document [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to save the reports.txt document to the C:\save path.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $document = Get-VESPDocument -Organization $organization -Query "reports.txt"  Save-VESPItem -Document $document -Path "C:\save" |  Perform the following steps:   1. Get the SharePoint document:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $document variable.  1. Run the Save-VESPItem cmdlet. Set the $document variable as the Document parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Saving SharePoint Item Attachment [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to save attachments to the reports.txt item to the C:\save path.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $item = Get-VESPItem -Organization $organization -Query "reports.txt"  $attachment = Get-VESPItemAttachment -Item $item  Save-VESPItem -ItemAttachment $attachment -Path "C:\save" |  Perform the following steps:   1. Get the SharePoint item:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $item variable. 4. Run the [Get-VESPItemAttachment](get-vespitemattachment.md) cmdlet. Set the $item variable as the Item parameter value. Save the result to the $attachment variable.  1. Run the Save-VESPItem cmdlet. Set the $attachment variable as the ItemAttachment parameter value. Specify the Path parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md)
* [Get-VESPDocument](get-vespdocument.md)
* [Get-VESPItem](get-vespitem.md)
* [Get-VESPItemAttachment](get-vespitemattachment.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)


