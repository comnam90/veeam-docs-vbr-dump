---
title: "Get-VESPItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespitem.html"
last_updated: "5/6/2025"
product_version: "13.0.1.1071"
---

# Get-VESPItem


Short Description

Returns SharePoint items.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get items from a SharePoint list.

|  |
| --- |
| Get-VESPItem [-List] <VESPList> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get items from a parent item.

|  |
| --- |
| Get-VESPItem [-ParentItem] <VESPItem> [-Query <String>] [-Recurse] [<CommonParameters>] |

* [For Veeam Backup & Replication] Get items from a SharePoint database.

|  |
| --- |
| Get-VESPItem [-Database] <VESPDatabase[]> [-Query <String>] [<CommonParameters>] |

* [For Veeam Backup for Microsoft 365] Get items from a SharePoint organization.

|  |
| --- |
| Get-VESPItem [-Organization] <VESPOrganization[]> [-Query <String>] [<CommonParameters>] |

* Get items from a SharePoint site.

|  |
| --- |
| Get-VESPItem [-Site] <VESPSite> [-Query <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns SharePoint items. You can get either parent and\or child items from the following backed-up sources:

* Microsoft organization
* SharePoint site
* SharePoint list

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| List | Specifies a SharePoint list. This cmdlet will return SharePoint items from this list. | Accepts the [VESPList](vesplist.md) object. To get this object, run the [Get-VESPList](get-vesplist.md) cmdlet. | True | 0 | True (ByValue) |
| Query | Specifies a query string for item search. The cmdlet will return items that match the search query from the specified database, organization, site, list or item.  For more information, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. | String | False | Named | False |
| Recurse | Defines that the cmdlet will return all child items of the specified parent item.  Default: False | SwitchParameter | False | Named | False |
| ParentItem | Specifies a parent item. The cmdlet will return only one sub-level child items for this item. | Accepts the [VESPItem](vespitem.md) object. To get this object, run the Get-VESPItem cmdlet. | True | 0 | True (ByValue) |
| Database | Specifies an array of SharePoint databases. The cmdlet will get items from these databases.  Note: This parameter is available for SharePoint databases backed up by Veeam Backup & Replication. | Accepts the [VESPDatabase](vespdatabase.md)[] object. To get this object, run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Organization | Specifies an array of SharePoint organizations. The cmdlet will return SharePoint items from these organizations. | Accepts the [VESPOrganization](vesporganization.md)[] object. To get this object, run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. | True | 0 | True (ByValue) |
| Site | Specifies a name of the SharePoint site. This cmdlet will return SharePoint items from the specified SharePoint site. | Accepts the [VESPSite](vespsite.md) object. To get this object, run the [Get-VESPSite](get-vespsite.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPItem](vespitem.md) object that contains SharePoint items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting SharePoint Items from SharePoint List [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a SharePoint item from the Color names SharePoint list.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $list = Get-VESPList -Database $database -Name "Color names"  Get-VESPItem -List $list -Query "new" |  Perform the following steps:   1. Get SharePoint list:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPList](get-vesplist.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $list variable.  1. Run the Get-VESPItem cmdlet. Set the $list variable as the List parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SharePoint Child Items from SharePoint Parent Item [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get the child items for the Reports SharePoint parent item.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $parentItem = Get-VESPItem -Database $database -Query "Reports"  Get-VESPItem -ParentItem $parentItem -Recurse |  Perform the following steps:   1. Get SharePoint item:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPItem cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. Save the result to the $parentItem variable.  1. Run the Get-VESPItem cmdlet. Set the $parentItem variable as the ParentItem parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting SharePoint Items from SharePoint Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all SharePoint items from the WSS\_Content.mdf database.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  Get-VESPItem -Database $database |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VESPItem cmdlet. Set the $database variable as the Database parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting SharePoint Items from SharePoint Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get an item from the Teams SharePoint site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $site = Get-VESPSite -Database $database -Name "Teams"  Get-VESPItem -Site $site -Query "new" |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the Get-VESPItem cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting SharePoint Items from SharePoint List [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a SharePoint item from the ABC One SharePoint list.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $list = Get-VESPList -Organization $organization -Name "ABC One"  Get-VESPItem -List $list -Query "new" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPList](get-vesplist.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $list variable. 4. Run the Get-VESPItem cmdlet. Set the $list variable as the List parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting SharePoint Child Items from SharePoint Parent Item [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get child items for the Reports item.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $parentItem = Get-VESPItem -Organization $organization -Query "Reports"  Get-VESPItem -ParentItem $parentItem -Recurse |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPItem cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $parentItem variable. 4. Run the Get-VESPItem cmdlet. Set the $parentItem variable as the ParentItem parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Getting SharePoint Items from Microsoft Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a SharePoint item from the ABC organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  Get-VESPItem -Organization $organization -Query "new" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the Get-VESPItem cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 8. Getting SharePoint Items from SharePoint Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a SharePoint item from the Teams SharePoint site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $site = Get-VESPSite -Organization $organization -Name "Teams"  Get-VESPItem -Site $site -Query "new" |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the Get-VESPItem cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPList](get-vesplist.md)
* [Get-VESPSite](get-vespsite.md)


