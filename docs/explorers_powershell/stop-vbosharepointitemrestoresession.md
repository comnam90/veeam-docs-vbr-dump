---
title: "Stop-VBOSharePointItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vbosharepointitemrestoresession.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops active restore sessions initiated to perform operations with SharePoint items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBOSharePointItemRestoreSession [-Session] <VBOSharePointRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops active restore sessions for Veeam Explorer for Microsoft SharePoint.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session that you want to stop. | Accepts the [VBOSharePointRestoreSession](vbosharepointrestoresession.md) object. To get this object, run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session for Veeam Explorer for Microsoft SharePoint.

|  |
| --- |
| $session = Get-VBOSharePointItemRestoreSession  Stop-VBOSharePointItemRestoreSession -Session $session |

Perform the following steps:

1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the Stop-VBOSharePointItemRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
