---
title: "Get-VEORDatabaseRestoreInterval"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veordatabaserestoreinterval.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns details on the available restore period for a backed-up Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORDatabaseRestoreInterval [-Database] <VEORDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns details on the available restore period for a backed-up Oracle database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a backed-up Oracle database. The cmdlet will return information on available restore period for the specified database. | Accepts the [VEORDatabase](veordatabase.md) object. To get this object, run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORDatabaseRestoreInterval](veordatabaserestoreinterval.md) object that contains details on the available restore period for a backed-up Oracle database.

Example

Getting Details on Available Restore Period for Backed-Up Oracle Database

This example shows how to get details on the available restore period for the specified Oracle database.

|  |
| --- |
| $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  Get-VEORDatabaseRestoreInterval -Database $database |

Perform the following steps:

1. Run the Get-VEORRestoreSession cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).

1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Get-VEORDatabaseRestoreInterval cmdlet. Set the $database variable as the Database parameter value.

Related Commands

[Get-VEORDatabase](get-veordatabase.md)

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
