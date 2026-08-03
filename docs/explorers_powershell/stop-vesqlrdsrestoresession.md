---
title: "Stop-VESQLRDSRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqlrdsrestoresession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VESQLRDSRestoreSession


Short Description

Stops an active restore session started to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLRDSRestoreSession [-Session] <VESQLRDSRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore session initiated to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

|  |
| --- |
| Note: |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VESQLRDSRestoreSession cmdlet. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Session | Specifies a restore session for backed-up Microsoft SQL Server databases running on Amazon RDS. The cmdlet will stop this session. | Accepts the [VESQLRDSRestoreSession](vesqlrdsrestoresession.md) object. To get this object, run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session for backed-up Microsoft SQL Server databases running on Amazon RDS.

|  |
| --- |
| $session = Get-VESQLRDSRestoreSession  Stop-VESQLRDSRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).

1. Run the Stop-VESQLRDSRestoreSession cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

[Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md)

Page updated 2026-01-27

