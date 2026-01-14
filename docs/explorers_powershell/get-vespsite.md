---
title: "get-vespsite"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespsite.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns SharePoint sites.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* [For Veeam Backup & Replication] Get SharePoint sites from a backed-up SharePoint database.

|  |
| --- |
| Get-VESPSite [-Database] <VESPDatabase> [[-Name] <String[]>] [-Recurse] [<CommonParameters>] |

* [For Veeam Backup for Microsoft 365] Get SharePoint sites from a SharePoint organization.

|  |
| --- |
| Get-VESPSite [-Organization] <VESPOrganization> [[-Name] <String[]>] [-Recurse] [<CommonParameters>] |

* Get a SharePoint site from a parent site.

|  |
| --- |
| Get-VESPSite [-ParentSite] <VESPSite> [[-Name] <String[]>] [-Recurse] [<CommonParameters>] |

Detailed Description

This cmdlet returns SharePoint sites. You can get either parent items or child items of a SharePoint site.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a backed-up SharePoint database. The cmdlet will get SharePoint sites from the specified database.  Note: This parameter is available for backups of SharePoint created by Veeam Backup & Replication only. | Accepts the [VESPDatabase](vespdatabase.md) object. To get this object, run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of SharePoint site names. This cmdlet will return SharePoint sites with the specified names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |
| Recurse | Defines that the cmdlet will return all child items of the specified parent item.  Default: False | SwitchParameter | False | Named | False |
| Organization | Specifies a SharePoint organization. The cmdlet will return SharePoint items from this organization.  Note: This parameter is available for backups of SharePoint created by Veeam Backup for Microsoft 365 only. | Accepts the [VESPOrganization](vesporganization.md) object. To get this object, run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. | True | 0 | True (ByValue) |
| ParentSite | Specifies a name of a SharePoint parent site. The cmdlet will return only one sub-level child sites for this site. | Accepts the [VESPSite](vespsite.md) object. To get this object, run the Get-VESPSite cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPSite](vespsite.md)[] array that contains SharePoint sites.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting SharePoint Sites from SharePoint Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all SharePoint sites from the WSS\_Content.mdf SharePoint database.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  Get-VESPSite -Database $database |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPSite cmdlet. Set the $database variable as the Database parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SharePoint Child Sites from SharePoint Parent Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all child sites from the Teams parent site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $parentSite = Get-VESPSite -Database $database -Name "Teams"  Get-VESPSite -ParentSite $parentSite -Recurse |  Perform the following steps:   1. Get a parent SharePoint site:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPSite cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $parentSite variable.  1. Run the Get-VESPSite cmdlet. Set the $parentSite variable as the ParentSite parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting SharePoint Site from Microsoft Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the Team Site SharePoint site from the ABC SharePoint organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  Get-VESPSite -Organization $organization -Name "Team Site" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPSite cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting SharePoint Child Sites from SharePoint Parent Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get all child sites from the Team Site parent site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $parentSite = Get-VESPSite -Organization $organization -Name "Team Site"  Get-VESPSite -ParentSite $parentSite -Recurse |  Perform the following steps:   1. Get a parent SharePoint site:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPSite cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $parentSite variable.  1. Run the Get-VESPSite cmdlet. Set the $parentSite variable as the ParentSite parameter value. Provide the Recurse parameter. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPOrganization](get-vesporganization.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
