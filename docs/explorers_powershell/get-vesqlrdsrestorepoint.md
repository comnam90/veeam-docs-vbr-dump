---
title: "Get-VESQLRDSRestorePoint"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrdsrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLRDSRestorePoint


Short Description

Returns restore points for a backed-up Microsoft SQL Server database running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLRDSRestorePoint [-Database] <VESQLRDSDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns available restore points for a backed-up Microsoft SQL Server database running on Amazon RDS.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Database | Specifies a backed-up Microsoft SQL Server database running on Amazon RDS. | Accepts the [VESQLRDSDatabase](vesqlrdsdatabase.md) object. To get this object, run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSRestorePoint](vesqlrdsrestorepoint.md)[] object that contains an array of restore points for a backed-up Microsoft SQL Server database running on Amazon RDS.

Example

Getting All Restore Points for a Database

This command returns all restore points for a specific backed-up Microsoft SQL Server database running on Amazon RDS.

|  |
| --- |
| $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[0] -Name "location1"  $restorepoint = Get-VESQLRDSRestorePoint -Database $database |

Perform the following steps:

1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the first restore session in the array).

1. Run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Get-VESQLRDSRestorePoint cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable to use it with other cmdlets.

Related Commands

* [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md)
* [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md)

Page updated 2026-01-27

