---
title: "stop-vesqlpluginrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqlpluginrestoresession.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active restore session started to explore and restore databases backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLPluginRestoreSession [-Session] <VESQLPluginRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore session initiated to explore and perform operations with databases backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| ![Stop-VESQLPluginRestoreSession](images/icon_note.webp) Note: |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VESQLPluginRestoreSession cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session for databases backed up with Veeam Plug-in for Microsoft SQL Server. The cmdlet will stop this session. | Accepts the [VESQLPluginRestoreSession](vesqlpluginrestoresession.md) object. To get this object, run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session for databases backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| $session = Get-VESQLPluginRestoreSession  Stop-VESQLPluginRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VESQLPluginRestoreSession cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

[Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md)

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
