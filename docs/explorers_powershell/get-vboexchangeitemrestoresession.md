---
title: "Get-VBOExchangeItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vboexchangeitemrestoresession.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active restore sessions started to perform operations with backed-up Microsoft Exchange items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBOExchangeItemRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up Microsoft Exchange items.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOExchangeRestoreSession](vboexchangerestoresession.md)[] array that contains restore sessions started to perform operations with backed-up Microsoft Exchange items.

Example

Getting Restore Sessions

This command returns all active restore sessions started to perform operations with backed-up Microsoft Exchange items.

|  |
| --- |
| Get-VBOExchangeItemRestoreSession |

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
