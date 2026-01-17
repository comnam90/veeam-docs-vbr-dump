---
title: "Get-VEORDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veordatabasefile.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VEORDatabaseFile


Short Description

Returns full file names for a backed-up Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORDatabaseFile [-Database] <VEORDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of full file names for a backed-up Oracle database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database. The cmdlet will return an array of full file names for the specified database. | Accepts the [VEORDatabase](veordatabase.md) object. To get this object, run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORDatabaseFile](veordatabasefile.md)[] array that contains database files of the specified Oracle database.

Example

Getting List of Full File Names For Backed-Up Oracle Database

This example shows how to get a list of full file names for a backed-up Oracle database.

|  |
| --- |
| $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  Get-VEORDatabaseFile -Database $database |

Perform the following steps:

1. Run the Get-VEORRestoreSession cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).

1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Get-VEORDatabaseFile cmdlet. Set the $database variable as the Database parameter value.

Related Commands

[Get-VEORDatabase](get-veordatabase.md)


