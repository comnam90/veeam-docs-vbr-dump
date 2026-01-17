---
title: "Stop-VEMDBRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vemdbrestoresession.html"
last_updated: "1/3/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active restore session started to perform restore operations with backed-up MongoDB data.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEMDBRestoreSession [-Session] <VEMDBRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore session initiated to perform operations with backed-up MongoDB data.

|  |
| --- |
| Note |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VEMDBRestoreSession cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with MongoDB data. The cmdlet will stop this session. | Accepts the [VEMDBRestoreSession](vemdbrestoresession.md) object. To get this object, run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session initiated to perform restore operations with MongoDB data.

|  |
| --- |
| $session = Get-VEMDBRestoreSession  Stop-VEMDBRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VEMDBRestoreSession cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

* [Start-VEMDBRestoreSession](start-vemdbrestoresession.md)
* [Get-VEMDBRestoreSession](get-vemdbrestoresession.md)

Page updated 1/3/2025

Page content applies to build 13.0.1.1071
