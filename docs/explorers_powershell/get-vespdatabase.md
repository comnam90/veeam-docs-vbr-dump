---
title: "Get-VESPDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespdatabase.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backed-up Microsoft SharePoint databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPDatabase [-Session] <VBRSharePointRestoreSession> [[-Name] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Microsoft SharePoint databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session started to perform operations with Microsoft SharePoint databases.  The cmdlet will return an array of Microsoft SharePoint databases that are available for restore within this session. | Accepts the [VBRSharePointRestoreSession](vbrsharepointrestoresession.md) object. To get this object, run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names for Microsoft SharePoint databases. The cmdlet will return an array of Microsoft SharePoint databases with those names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPDatabase](vespdatabase.md)[] array that contains backed-up Microsoft SharePoint databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Microsoft SharePoint Databases

|  |  |
| --- | --- |
| This example shows how to get a list of Microsoft SharePoint databases.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  Get-VESPDatabase -Session $session |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the Get-VESPDatabase cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft SharePoint Database by Name

|  |  |
| --- | --- |
| This example shows how to get the DocArchive06\_AuditorDB.mdf Microsoft SharePoint database.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  Get-VESPDatabase -Session $session -Name "DocArchive06\_AuditorDB.mdf" |  Perform the following steps:   1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the Get-VESPDatabase cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
