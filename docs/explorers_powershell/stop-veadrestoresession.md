---
title: "Stop-VEADRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veadrestoresession.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Stop-VEADRestoreSession


Short Description

Stops an active restore session initiated to perform operations with Microsoft Active Directory databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEADRestoreSession [-Session] <IVEADRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops active restore sessions initiated to perform operations with Microsoft Active Directory databases.

|  |
| --- |
| Note |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VEADRestoreSession cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with Microsoft Active Directory databases. The cmdlet will stop this session. | Accepts the IVEADRestoreSession object. To get this object, run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session initiated to perform operations with a Microsoft Active Directory database.

|  |
| --- |
| $session = Get-VEADRestoreSession  Stop-VEADRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VEADRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VEADRestoreSession](get-veadrestoresession.md)


