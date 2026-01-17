---
title: "Stop-VEORRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veorrestoresession.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active restore session initiated to perform operations with Oracle databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEORRestoreSession [-Session] <VEORRestoreSession> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore session initiated to perform operations with Oracle databases.

|  |
| --- |
| Note |
| * The cmdlet stops restore sessions initiated in the PowerShell console only. * Restore sessions will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VEORRestoreSession cmdlet. * If the restore session you want to stop contains ongoing publishing operations, you will be prompted to unpublish all databases still published in the session. To avoid this interactive prompt, unpublish the databases using the [Unpublish-VEORDatabase](unpublish-veordatabase.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an Oracle restore session that you want to stop. | Accepts the [VEORRestoreSession](veorrestoresession.md) object. To get this object, run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Oracle Restore Session

This example shows how to stop a restore session initiated to perform operations with Oracle databases.

|  |
| --- |
| $session = Get-VEORRestoreSession  Stop-VEORRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Stop-VEORRestoreSession cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

[Get-VEORRestoreSession](get-veorrestoresession.md)

Page updated 1/7/2025

Page content applies to build 13.0.1.1071
