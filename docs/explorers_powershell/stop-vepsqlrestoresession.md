---
title: "Stop-VEPSQLRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vepsqlrestoresession.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---

# Stop-VEPSQLRestoreSession


Short Description

Stops an active restore session initiated to perform operations with PostgreSQL instances.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEPSQLRestoreSession [-Session] <VEPSQLRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops active restore sessions initiated to perform operations with PostgreSQL instances.

|  |
| --- |
| Note |
| * The cmdlet will unpublish all PostgreSQL instances published in the restore session. * The cmdlet stops restore sessions initiated in the PowerShell console only. * Active restore sessions will not stop automatically if you close the PowerShell console. To stop a restore session, you must run the Stop-VEPSQLRestoreSession cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an PostgreSQL restore session that you want to stop. | Accepts the [VEPSQLRestoreSession](vepsqlrestoresession.md) object. To get this object, run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session initiated to perform operations with PostgreSQL instances.

|  |
| --- |
| $session = Get-VEPSQLRestoreSession  Stop-VEPSQLRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VEPSQLRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Start-VEPSQLRestoreSession](start-vepsqlrestoresession.md)


