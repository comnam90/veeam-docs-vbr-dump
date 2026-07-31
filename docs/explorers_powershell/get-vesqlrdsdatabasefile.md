---
title: "Get-VESQLRDSDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrdsdatabasefile.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLRDSDatabaseFile


Short Description

Returns database files for a backed-up Microsoft SQL Server database running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLRDSDatabaseFile [-RestorePoint] <VESQLRDSRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of database files for a backed-up Microsoft SQL Server database running on Amazon RDS.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies a restore point for a Microsoft SQL Server database. The cmdlet will return an array of database files that are available on that restore point. | Accepts the [VESQLRDSRestorePoint](vesqlrdsrestorepoint.md) object. To get this object, run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSDatabaseFile](vesqlrdsdatabasefile.md)[] object that contains an array of database files for a backed-up Microsoft SQL Server database running on Amazon RDS.

Example

Getting List of Database Files for Microsoft SQL Server Database

This example shows how to get a list of database files for a backed-up Microsoft SQL Server database running on Amazon RDS.

|  |
| --- |
| $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[0] -Name "db1"  $restorepoint = Get-VESQLRDSRestorePoint -Database $database  $dbfiles = Get-VESQLRDSDatabaseFile -RestorePoint $restorepoint |

Perform the following steps:

1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the first restore session in the array).

1. Run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable.
3. Run the Get-VESQLRDSDatabaseFile cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $dbfiles variable to use it with other cmdlets.

Related Commands

* [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md)
* [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md)
* [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md)

Page updated 2026-01-28

