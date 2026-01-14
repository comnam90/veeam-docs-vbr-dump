---
title: "get-vespitemattachment"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespitemattachment.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns attachments of the specified SharePoint item.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPItemAttachment [-Item] <VESPItem> [<CommonParameters>] |

Detailed Description

This cmdlet returns attachments of the specified SharePoint item.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies a SharePoint item. This cmdlet will return attachments of the specified item. | Accepts the [VESPItem](vespitem.md) object. To get this object, run the [Get-VESPItem](get-vespitem.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPItemAttachment](vespitemattachment.md)[] array that contains attachments added to the specified SharePoint item.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting SharePoint Item Attachments [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get attachments for the Documents SharePoint item.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $item = Get-VESPItem -Database $database -Query "Documents"  Get-VESPItemAttachment -Item $item |  Perform the following steps:   1. Get the SharePoint item:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. Save the result to the $item variable.  1. Run the Get-VESPItemAttachment cmdlet. Set the $item variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SharePoint Item Attachments [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get attachments for the Documents SharePoint item.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $item = Get-VESPItem -Organization $organization -Query "Documents"  Get-VESPItemAttachment -Item $item |  Perform the following steps:   1. Get the SharePoint item:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $item variable.  1. Run the Get-VESPItemAttachment cmdlet. Set the $item variable as the Item parameter value. |

Related Commands

* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VESPDatabase](get-vespdatabase.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPItem](get-vespitem.md)

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
