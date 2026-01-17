---
title: "Get-VESQLPluginRestorePoint"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlpluginrestorepoint.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VESQLPluginRestorePoint


Short Description

Returns restore points for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPluginRestorePoint [-Database] <VESQLPluginDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns available restore points for a database backed up with Veeam Plug-in for Microsoft SQL Server.

After you get the restore points, you can use the following cmdlets:

* [Get-VESQLPluginLogInterval](get-vesqlpluginloginterval.md) — to see the available restore period within a restore point.
* [Get-VESQLPluginDatabaseFile](get-vesqlplugindatabasefile.md) — to get the available database files on a restore point.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a database backed up with Veeam Plug-in for Microsoft SQL Server. | Accepts the [VESQLPluginDatabase](vesqlplugindatabase.md) object. To get this object, run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginRestorePoint](vesqlpluginrestorepoint.md)[] object that contains an array of restore points for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Example

Getting All Restore Points for a Database

This command returns all restore points for specific database backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "location1"  $restorepoint = Get-VESQLPluginRestorePoint -Database $database |

Perform the following steps:

1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).

1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Get-VESQLPluginRestorePoint cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable to use it with other cmdlets.

Related Commands

* [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md)
* [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md)


