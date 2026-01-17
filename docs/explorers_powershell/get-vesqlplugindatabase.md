---
title: "Get-VESQLPluginDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlplugindatabase.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns databases backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPluginDatabase [-Session] <VESQLPluginRestoreSession> [-Name <String[]>] [-InstanceName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Microsoft SQL Server databases backed up with Veeam Plug-in for Microsoft SQL Server.

After you get the databases, you can use the following cmdlets:

* [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) — to get the available restore points for a specific database.
* [Start-VESQLPluginDatabaseRestore](start-vesqlplugindatabaserestore.md) — to restore your data.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return an array of databases within the specified restore session. | Accepts the [VESQLPluginRestoreSession](vesqlpluginrestoresession.md) object. To get this object, run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names for Microsoft SQL Server databases. The cmdlet will return an array of databases with the specified names.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| InstanceName | Specifies an array of names for Microsoft SQL Server instances. The cmdlet will return an array of databases located on the specified instances.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginDatabase](vesqlplugindatabase.md)[] object that contains an array of databases backed up by Veeam Plug-in for Microsoft SQL Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Microsoft SQL Server Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get a list of all Microsoft SQL Server databases within the specified restore session.  |  | | --- | | $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the second restore session in the array).   1. Run the Get-VESQLPluginDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $database variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft SQL Server Databases with Specified Name

|  |  |
| --- | --- |
| This example shows how to get all Microsoft SQL Server databases with the specified name.  |  | | --- | | $session = Get-VESQLPluginRestoreSession  Get-VESQLPluginDatabase -Session $session[0] -Name "SQLDatabase" |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VESQLPluginDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Microsoft SQL Server Databases with Specific Names Belonging to Specific Instances

|  |  |
| --- | --- |
| This example shows how to get all Microsoft SQL Server databases with specific names that belong to specific instances.  |  | | --- | | $session = Get-VESQLPluginRestoreSession  $databasenames = @("db1", "db2")  $instancenames = @("instance\_01", "instance\_02")  Get-VESQLPluginDatabase -Session $session[0] -Name @databasenames -InstanceName @instancenames |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $databasenames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server instances. 3. Run the Get-VESQLPluginDatabase cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value and specify the necessary restore session. * Set the $databasenames variable as the Name parameter value. * Set the $instancenames variable as the InstanceName parameter value.   Save the result to the $database variable to use it with other cmdlets. |

Related Commands

[Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
