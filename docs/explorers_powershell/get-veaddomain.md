---
title: "get-veaddomain"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veaddomain.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns a backed-up Active Directory domain.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEADDomain [-Session] <IVEADRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet will return a backed-up Active Directory domain.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return a backed-up Active Directory domain within the specified restore session. | Accepts the IVEADRestoreSession or [VEADRestoreSession](veadrestoresession.md) object. To get this object, run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADDomain](veaddomain.md) object that contains a backed-up Active Directory domain.

Example

Getting Active Directory Domain Within Specified Restore Session

This example shows how to get an Active Directory domain within the specified restore session.

|  |
| --- |
| $session = Get-VEADRestoreSession  Get-VEADDomain -Session $session[3] |

Perform the following steps:

1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).

1. Run the Get-VEADDomain cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session.

Related Commands

[Get-VEADRestoreSession](get-veadrestoresession.md)

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
