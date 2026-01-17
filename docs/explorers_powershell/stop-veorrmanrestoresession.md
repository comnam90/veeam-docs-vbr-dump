---
title: "Stop-VEORRMANRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veorrmanrestoresession.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active restore session started to explore Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEORRMANRestoreSession [-Session] <VEORRMANRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore sessions started to explore Oracle databases that have been backed up with Veeam Plug-in for Oracle RMAN.

|  |
| --- |
| Note |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VEORRMANRestoreSession cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with Oracle databases backed up with Veeam Plug-in for Oracle RMAN. The cmdlet will stop the specified restore session. | Accepts the [VEORRMANRestoreSession](veorrmanrestoresession.md) object. To get this object, run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session of an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

|  |
| --- |
| $session = Get-VEORRMANRestoreSession  Stop-VEORRMANRestoreSession -Session $session |

Perform the following steps:

1. Run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VEORRMANRestoreSession cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

[Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
