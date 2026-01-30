---
title: "Get-VESPDocumentLibrary"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespdocumentlibrary.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VESPDocumentLibrary


Short Description

Returns SharePoint document libraries.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a document library from a backed-up SharePoint database.

|  |
| --- |
| Get-VESPDocumentLibrary [-Database] <VESPDatabase> [[-Name] <String[]>] [<CommonParameters>] |

* Get a document library from a Microsoft organization.

|  |
| --- |
| Get-VESPDocumentLibrary [-Organization] <VESPOrganization> [[-Name] <String[]>] [<CommonParameters>] |

* Get a document library from a SharePoint site.

|  |
| --- |
| Get-VESPDocumentLibrary [-Site] <VESPSite> [[-Name] <String[]>] [-Recurse] [<CommonParameters>] |

Detailed Description

This cmdlet returns document libraries. You can search the SharePoint database, site or the whole organization to get a specific document library.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a backed-up SharePoint database. The cmdlet will return document libraries from the specified database. | Accepts the [VESPDatabase](vespdatabase.md) object. To get this object, run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of SharePoint document library names. This cmdlet will return an array of document libraries with the specified names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |
| Organization | Specifies an array of SharePoint organizations. The cmdlet will return document libraries from these organizations. | Accepts the [VESPOrganization](vesporganization.md)[] object. To get this object, run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. | True | 0 | True (ByValue) |
| Site | Specifies a name of the SharePoint site. This cmdlet will return a document library from the specified SharePoint site. | Accepts the [VESPSite](vespsite.md) object. To get this object, run the [Get-VESPSite](get-vespsite.md) cmdlet. | True | 0 | True (ByValue) |
| Recurse | Defines that the cmdlet will return all child items of the specified parent item.  Default: False | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPDocumentLibrary](vespdocumentlibrary.md)[] array that contains SharePoint document libraries.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting SharePoint Document Library from SharePoint Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all SharePoint document libraries from the WSS\_Content.mdf SharePoint database.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  Get-VESPDocumentLibrary -Database $database |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPDocumentLibrary cmdlet. Set the $database variable as the Database parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SharePoint Document Library from SharePoint Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get the Regulations document library from the Teams SharePoint site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name WSS\_Content.mdf  $site = Get-VESPSite -Database $database -Name "Teams"  Get-VESPDocumentLibrary -Site $site -Name "Regulations" |  Perform the following steps:   1. Get a SharePoint site:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable.  1. Run the Get-VESPDocumentLibrary cmdlet. Set the $site variable as the Site parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting SharePoint Document Library from Microsoft Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the Regulations document library from the ABC Microsoft organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  Get-VESPDocumentLibrary -Organization $organization -Name "Regulations" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPDocumentLibrary cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting SharePoint Document Library from SharePoint Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the Regulations document library from the Teams SharePoint site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $site = Get-VESPSite -Organization $organization -Name "Teams"  Get-VESPDocumentLibrary -Site $site -Name "Regulations" |  Perform the following steps:   1. Get a SharePoint site:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable.  1. Run the Get-VESPDocumentLibrary cmdlet. Set the $site variable as the Site parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPSite](get-vespsite.md)
* [Get-VESPOrganization](get-vesporganization.md)


