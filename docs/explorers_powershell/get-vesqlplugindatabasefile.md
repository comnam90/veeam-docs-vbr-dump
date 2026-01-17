---
title: "Get-VESQLPluginDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlplugindatabasefile.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VESQLPluginDatabaseFile


Short Description

Returns database files for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPluginDatabaseFile [-RestorePoint] <VESQLPluginRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of database files for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point for a Microsoft SQL Server database. The cmdlet will return an array of database files that are available on that restore point. | Accepts the [VESQLPluginRestorePoint](vesqlpluginrestorepoint.md) object. To get this object, run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginDatabaseFile](vesqlplugindatabasefile.md)[] object that contains an array of database files for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Example

Getting List of Database Files for Microsoft SQL Server Database

This example shows how to get a list of database files for a database backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "db1"  $restorepoint = Get-VESQLPluginRestorePoint -Database $database  $dbfiles = Get-VESQLPluginDatabaseFile -RestorePoint $restorepoint |

Perform the following steps:

1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).

1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable.
3. Run the Get-VESQLPluginDatabaseFile cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $dbfiles variable to use it with other cmdlets.

Related Commands

* [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md)
* [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md)
* [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md)


