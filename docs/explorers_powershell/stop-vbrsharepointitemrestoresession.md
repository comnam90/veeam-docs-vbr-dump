---
title: "stop-vbrsharepointitemrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vbrsharepointitemrestoresession.html"
last_updated: "7/9/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops active restore sessions initiated to perform operations with SharePoint databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRSharePointItemRestoreSession [-Session] <SharePointRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops active restore sessions for Microsoft SharePoint initiated to perform operations with Microsoft SharePoint databases.

|  |
| --- |
| Note |
| * You can stop restore sessions that are created by means of PowerShell only. * The cmdlet will stop sessions that are initiated within the same PowerShell session only. * Restore sessions will not stop automatically if you close the PowerShell console without stopping the restore session first. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session that you want to stop. | Accepts the [VBRSharePointRestoreSession](vbrsharepointrestoresession.md) object. To get this object, run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session for Veeam Explorer for Microsoft SharePoint.

|  |
| --- |
| $session = Get-VBRSharePointItemRestoreSession  Stop-VBRSharePointItemRestoreSession -Session $session |

Perform the following steps:

1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the Stop-VBRSharePointItemRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)

Page updated 7/9/2025

Page content applies to build 13.0.1.1071
