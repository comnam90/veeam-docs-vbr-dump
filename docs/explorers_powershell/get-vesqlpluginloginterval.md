---
title: "Get-VESQLPluginLogInterval"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlpluginloginterval.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Get-VESQLPluginLogInterval


Short Description

Returns details on the available restore period for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPluginLogInterval [-RestorePoint] <VESQLPluginRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet returns details on the available restore period within a restore point of a database backed up with Veeam Plug-in for Microsoft SQL Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies restore point of a database backed up with Veeam Plug-in for Microsoft SQL Server. The cmdlet will return details on the available restore period within the restore point. | Accepts the [VESQLPluginRestorePoint](vesqlpluginrestorepoint.md) object. To get this object, run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginLogInterval](vesqlpluginloginterval.md) object that contains details on the available restore period for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Example

Getting Details on Available Restore Period for Microsoft SQL Server Database

This example shows how to get details on an available restore period for a database backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "SQLDatabase"  $restorepoint = Get-VESQLPluginRestorePoint -Database $database  Get-VESQLPluginLogInterval -RestorePoint $restorepoint |

Perform the following steps:

1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).

1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable.
3. Run the Get-VESQLPluginLogInterval cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.

Related Commands

* [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md)
* [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md)
* [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md)


