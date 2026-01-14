---
title: "stop-vesqlrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqlrestoresession.html"
last_updated: "7/2/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active restore session initiated to perform operations with Microsoft SQL Server databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLRestoreSession [-Session] <IVESQLRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore session initiated to perform operations with Microsoft SQL Server databases.

|  |
| --- |
| Note |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VESQLRestoreSession cmdlet.  * If the restore session you want to stop contains ongoing publishing operations, you will be prompted to unpublish all databases still published in the session. To avoid this interactive prompt, unpublish the databases using the [Unpublish-VESQLDatabase](unpublish-vesqldatabase.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with Microsoft SQL Server databases. The cmdlet will stop this session. | Accepts the [VESQLRestoreSession](vesqlrestoresession.md) object. To get this object, run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session initiated to perform operations with Microsoft SQL Server databases.

|  |
| --- |
| $session = Get-VESQLRestoreSession  Stop-VESQLRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VESQLRestoreSession cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

[Get-VESQLRestoreSession](get-vesqlrestoresession.md)

Page updated 7/2/2025

Page content applies to build 13.0.1.1071
