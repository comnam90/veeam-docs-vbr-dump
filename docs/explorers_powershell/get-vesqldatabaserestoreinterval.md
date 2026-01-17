---
title: "Get-VESQLDatabaseRestoreInterval"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqldatabaserestoreinterval.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns details on the available restore period for a backed-up Microsoft SQL database.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLDatabaseRestoreInterval [-Database] <VESQLDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns details on the available restore period for a backed-up Microsoft SQL Server database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a backed-up Microsoft SQL Server database. The cmdlet will return details on the available restore period for the specified database. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabaseRestoreInterval](vesqldatabaserestoreinterval.md) object that contains details on available restore period for the backed-up Microsoft SQL database.

Example

Getting Details on Available Restore Period for Backed-Up Microsoft SQL Database

This example shows how to get details on an available restore period for a backed-up Microsoft SQL database.

|  |
| --- |
| $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  Get-VESQLDatabaseRestoreInterval -Database $database |

Perform the following steps:

1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
3. Run the Get-VESQLDatabaseRestoreInterval cmdlet. Set the $database variable as the Database parameter value.

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
