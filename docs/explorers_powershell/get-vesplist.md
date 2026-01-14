---
title: "get-vesplist"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesplist.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns SharePoint lists.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* [For Veeam Backup & Replication] Get lists from a backed-up SharePoint database.

|  |
| --- |
| Get-VESPList [-Database] <VESPDatabase> [[-Name] <String[]>] [<CommonParameters>] |

* [For Veeam Backup for Microsoft 365] Get lists from the Microsoft organization.

|  |
| --- |
| Get-VESPList [-Organization] <VESPOrganization> [[-Name] <String[]>] [<CommonParameters>] |

* Get lists from the SharePoint site.

|  |
| --- |
| Get-VESPList [-Site] <VESPSite> [[-Name] <String[]>] [-Recurse] [<CommonParameters>] |

Detailed Description

This cmdlet returns SharePoint lists.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a SharePoint database. The cmdlet will return SharePoint lists from this database. | Accepts the [VESPDatabase](vespdatabase.md) object. To get this object, run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of SharePoint list names. This cmdlet will return SharePoint lists with the specified names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |
| Organization | Specifies a SharePoint organization. The cmdlet will return SharePoint lists from this organization. | Accepts the [VESPOrganization](vesporganization.md) object. To get this object, run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. | True | 0 | True (ByValue) |
| Site | Specifies a name of the SharePoint site. This cmdlet will return SharePoint lists from the specified SharePoint site. | Accepts the [VESPSite](vespsite.md) object. To get this object, run the [Get-VESPSite](get-vespsite.md) cmdlet. | True | 0 | True (ByValue) |
| Recurse | Defines that the cmdlet will return all child items of the specified parent item.  Default: False | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPList](vesplist.md)[] array that contains SharePoint document libraries.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting SharePoint Lists from Backed-Up SharePoint Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all SharePoint lists from the WSS\_Content.mdf backed-up SharePoint database.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  Get-VESPList -Database $database |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPList cmdlet. Set the $database variable as the Database parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SharePoint List from SharePoint Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get the Color names SharePoint list from the Teams SharePoint site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $site = Get-VESPSite -Database $database -Name "Teams"  Get-VESPList -Site $site -Name "Color names" |  Perform the following steps:   1. Get a SharePoint site:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable.  1. Run the Get-VESPList cmdlet. Set the $site variable as the Site parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting SharePoint List from Microsoft Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the Color names SharePoint list from the ABC SharePoint organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  Get-VESPList -Organization $organization -Name "Color names" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPList cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting SharePoint List from SharePoint Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the Color SharePoint list from the Team Site SharePoint site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $site = Get-VESPSite -Organization $organization -Name "Teams"  Get-VESPList -Site $site -Name "Color names" |  Perform the following steps:   1. Get a parent SharePoint site:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable.  1. Run the Get-VESPList cmdlet. Set the $site variable as the Site parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPSite](get-vespsite.md)
* [Get-VESPOrganization](get-vesporganization.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
