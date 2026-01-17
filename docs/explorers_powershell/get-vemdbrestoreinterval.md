---
title: "Get-VEMDBRestoreInterval"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbrestoreinterval.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Get-VEMDBRestoreInterval


Short Description

Returns details on the available restore period for a backed-up MongoDB instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEMDBRestoreInterval [-Session] <VEMDBRestoreSession> [<CommonParameters>] |

Detailed Description

This cmdlet returns details on the available restore period for a backed-up MongoDB instance. You can use the output of this cmdlet to determine the required point-in-time state that you will specify in the [Start-VEMDBDataRestore](start-vemdbdatarestore.md) and [Start-VEMDBPublishJob](start-vemdbpublishjob.md) cmdlets.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a Veeam Explorer for MongoDB restore session. The cmdlet will return details on the available restore period for the MongoDB instance. | Accepts the [VEMDBRestoreSession](vemdbrestoresession.md) object. To get this object, run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBRestoreInterval](vemdbrestoreinterval.md) object that contains details on available restore period in the Veeam Explorer for MongoDB restore session.

Example

Getting Details on Available Restore Period for MongoDB Instance

This example shows how to get details on the available restore period for a MongoDB instance

|  |
| --- |
| $session = Get-VEMDBRestoreSession -SessionId "b7ced612-1259-4221-810b-f62c21b1c159"  Get-VEMDBRestoreInterval -Session $session |

Perform the following steps:

1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Specify the SessionId parameter value. Save the result to the $session variable.
2. Run the Get-VEMDBRestoreInterval cmdlet. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VEMDBRestoreSession](get-vemdbrestoresession.md)
* [Start-VEMDBDataRestore](start-vemdbdatarestore.md)
* [Start-VEMDBPublishJob](start-vemdbpublishjob.md)


