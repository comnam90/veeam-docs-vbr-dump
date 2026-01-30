---
title: "Stop-VEODRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veodrestoresession.html"
last_updated: "1/23/2025"
product_version: "13.0.1.1071"
---

# Stop-VEODRestoreSession


Short Description

Stops active restore sessions.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Stop-VEODRestoreSession [-Session] <VBOOneDriveItemRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet stops an active Veeam Explorer for Microsoft OneDrive for Business restore session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session that you want to stop. | Accepts the [VBOOneDriveItemRestoreSession](vboonedriveitemrestoresession.md) object. To get this object, run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session

This example shows how to stop a restore session for Veeam Explorer for Microsoft OneDrive for Business.

|  |
| --- |
| $session = Get-VEODRestoreSession  Stop-VEODRestoreSession -Session $session |

Perform the following steps:

1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the Stop-VEODRestoreSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VEODRestoreSession](get-veodrestoresession.md)


