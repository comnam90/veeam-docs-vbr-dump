---
title: "get-vbrsharepointitemrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vbrsharepointitemrestoresession.html"
last_updated: "2/4/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active restore sessions started to perform operations with backed-up Microsoft SharePoint databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSharePointItemRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up Microsoft SharePoint databases.

|  |
| --- |
| Note |
| The cmdlet returns restore sessions initiated in the PowerShell console only. The cmdlet does not return restore sessions running in the Veeam Backup & Replication console. |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBRSharePointRestoreSession](vbrsharepointrestoresession.md)[] array that contains settings of restore sessions started to explore backed-up Microsoft SharePoint databases and to perform operations with these databases.

Example

Getting Restore Session

This example shows how to get a restore session started to perform operations with backed-up Microsoft SharePoint databases.

|  |
| --- |
| $session = Get-VBRSharePointItemRestoreSession  $session[0] |

Page updated 2/4/2025

Page content applies to build 13.0.1.1071
