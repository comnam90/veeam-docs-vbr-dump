---
title: "Get-VEHANASystem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanasystem.html"
last_updated: "1/3/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns information about a backed-up SAP HANA system.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEHANASystem [-Session] <VEHANARestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet returns information about a backed-up SAP HANA system. After you get the SAP HANA system, you can use the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet to get an array of the databases available on the system.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with SAP HANA databases. | Accepts the [VEHANARestoreSession](vehanarestoresession.md) object. To get this object, run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANASystem](vehanasystem.md) object that contains information about the specified SAP HANA system.

Example

Getting SAP HANA System

This example shows how to get the necessary SAP HANA system from the relevant restore session.

|  |
| --- |
| $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0] |

Perform the following steps:

1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the Get-VEHANASystem cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $system variable to be able to use it with other cmdlets.

Related Commands

[Get-VEHANARestoreSession](get-vehanarestoresession.md)

Page updated 1/3/2025

Page content applies to build 13.0.1.1071
