---
title: "Get-VESPItemVersion"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespitemversion.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VESPItemVersion


Short Description

Returns other versions of a SharePoint item.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPItemVersion [-Item] <VESPItem> [<CommonParameters>] |

Detailed Description

This cmdlet returns other versions of a SharePoint item.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies a SharePoint item. This cmdlet will return other versions of this SharePoint item. | Accepts the [VESPItem](vespitem.md) object. To get this object, run the [Get-VESPItem](get-vespitem.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns a [VESPItem](vespitem.md)[] array that contains other versions of the specified SharePoint item.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Version of SharePoint Item from SharePoint List [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a version of a SharePoint item from the Color names SharePoint list.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $list = Get-VESPList -Database $database -Name "Color names"  $item = Get-VESPItem -List $list -Query "red"  Get-VESPItemVersion -Item $item |  Perform the following steps:   1. Get SharePoint list:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPList](get-vesplist.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $list variable.  1. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $list variable as the List parameter value. Specify the Query parameter value. Save the result to the $item variable. 2. Run the Get-VESPItemVersion cmdlet. Set the $item variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Version of SharePoint Item from SharePoint Site [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a version of a SharePoint item from the Teams SharePoint site.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $site = Get-VESPSite -Database $database -Name "Teams"  $item = Get-VESPItem -Site $site -Query "ABC"  Get-VESPItemVersion -Item $item |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. Save the result to the $item variable. 5. Run the Get-VESPItemVersion cmdlet. Set the $item variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Version of SharePoint Item from SharePoint List [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a version of a SharePoint item from the ABC One SharePoint list.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $list = Get-VESPList -Organization $organization -Name "ABC One"  $item = Get-VESPItem -List $list -Query "abc"  Get-VESPItemVersion -Item $item |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPList](get-vesplist.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $list variable. 4. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $list variable as the List parameter value. Specify the Query parameter value. Save the result to the $item variable. 5. Run the Get-VESPItemVersion cmdlet. Set the $item variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Version of SharePoint Item from Microsoft Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a version of a SharePoint item from the ABC organization.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $item = Get-VESPItem -Organization $organization -Query "abc"  Get-VESPItemVersion -Item $item |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $item variable. 4. Run the Get-VESPItemVersion cmdlet. Set the $item variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Version of SharePoint Item from SharePoint Site [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get a version of a SharePoint item from the Teams SharePoint site.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $site = Get-VESPSite -Organization $organization -Name "Teams"  $item = Get-VESPItem -Site $site -Query "ABC"  Get-VESPItemVersion -Item $item |  Perform the following steps:   1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPSite](get-vespsite.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $site variable. 4. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $site variable as the Site parameter value. Specify the Query parameter value. Save the result to the $item variable. 5. Run the Get-VESPItemVersion cmdlet. Set the $item variable as the Item parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPList](get-vesplist.md)
* [Get-VESPSite](get-vespsite.md)

* [Get-VESPItem](get-vespitem.md)


