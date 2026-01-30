---
title: "Stop-VBOTeamsItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vboteamsitemrestoresession.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Stop-VBOTeamsItemRestoreSession


Short Description

Stops active restore sessions initiated to perform operations with backed-up Microsoft Teams items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Stop-VBOTeamsItemRestoreSession [-Session] <ITeamsRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops active restore sessions initiated to perform operations with backed-up Microsoft Teams objects.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session that you want to stop. | Accepts the [ITeamsRestoreSession](vboteamsrestoresession.md) object. To get this object, run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session initiated to perform operations with backed-up Microsoft Teams objects.

|  |
| --- |
| $session = Get-VBOTeamsItemRestoreSession  Stop-VBOTeamsItemRestoreSession -Session $session[3] |

Perform the following steps:

1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the fourth restore session in the array.

1. Run the Stop-VBOTeamsItemRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)


