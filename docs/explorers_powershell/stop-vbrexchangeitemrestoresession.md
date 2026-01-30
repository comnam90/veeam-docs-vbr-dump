---
title: "Stop-VBRExchangeItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vbrexchangeitemrestoresession.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRExchangeItemRestoreSession


Short Description

Stops active restore sessions initiated to perform operations with backed-up Microsoft Exchange databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRExchangeItemRestoreSession [-Session] <VBRExchangeRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops active restore sessions initiated to perform operations with Microsoft Exchange databases.

|  |
| --- |
| Note |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VBRExchangeItemRestoreSession cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session for a Microsoft Exchange database that you want to stop. | Accepts the [VBRExchangeRestoreSession](vbrexchangerestoresession.md) object. To get this object, run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Specific Restore Session

This example shows how to stop a specific restore session initiated to perform operations with Microsoft Exchange databases.

|  |
| --- |
| $session = Get-VBRExchangeItemRestoreSession  Stop-VBRExchangeItemRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the fourth restore session in the array.

1. Run the Stop-VBRExchangeItemRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)


