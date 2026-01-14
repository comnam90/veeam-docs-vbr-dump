---
title: "get-vesqldatabasefile"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqldatabasefile.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns full file names for a backed-up Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLDatabaseFile [-Database] <VESQLDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of full file names for a backed-up Microsoft SQL Server database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database. The cmdlet will return an array of full file names for the specified database. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabaseFile](vesqldatabasefile.md)[] array that contains full file names for the backed-up Microsoft SQL database.

Example

Getting List of Full File Names for Backed-Up Microsoft SQL Server Database

This example shows how to get a list of full file names for a backed-up Microsoft SQL Server database.

|  |
| --- |
| $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "db1"  Get-VESQLDatabaseFile -Database $database |

Perform the following steps:

1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).

1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Get-VESQLDatabaseFile cmdlet. Set the $database variable as the Database parameter value.

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
