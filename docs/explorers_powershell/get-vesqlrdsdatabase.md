---
title: "Get-VESQLRDSDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrdsdatabase.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLRDSDatabase


Short Description

Returns backed-up Microsoft SQL Server databases running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLRDSDatabase [-Session] <VESQLRDSRestoreSession> [-Name <String[]>] [-InstanceName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Microsoft SQL Server databases running on Amazon RDS.

After you get the databases, you can use the following cmdlets:

* [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) — to get the available restore points for a specific database.
* [Start-VESQLRDSDatabaseRestore](start-vesqlrdsdatabaserestore.md) — to restore your data.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Session | Specifies an active restore session. The cmdlet will return an array of databases within the specified restore session. | Accepts the [VESQLRDSRestoreSession](vesqlrdsrestoresession.md) object. To get this object, run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names for Microsoft SQL Server databases. The cmdlet will return an array of databases with the specified names.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| InstanceName | Specifies an array of names for Microsoft SQL Server instances. The cmdlet will return an array of databases located on the specified instances.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSDatabase](vesqlrdsdatabase.md)[] object that contains an array of backed-up Microsoft SQL Server databases running on Amazon RDS.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Microsoft SQL Server Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get a list of all Microsoft SQL Server databases within the specified restore session.  |  | | --- | | $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the second restore session in the array).   1. Run the Get-VESQLRDSDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $database variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft SQL Server Databases with Specified Name

|  |  |
| --- | --- |
| This example shows how to get all Microsoft SQL Server databases with the specified name.  |  | | --- | | $session = Get-VESQLRDSRestoreSession  Get-VESQLRDSDatabase -Session $session[0] -Name "SQLDatabase" |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the Get-VESQLRDSDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Microsoft SQL Server Databases with Specific Names Belonging to Specific Instances

|  |  |
| --- | --- |
| This example shows how to get all Microsoft SQL Server databases with specific names that belong to specific instances.  |  | | --- | | $session = Get-VESQLRDSRestoreSession  $databasenames = @("db1", "db2")  $instancenames = @("instance\_01", "instance\_02")  Get-VESQLRDSDatabase -Session $session[0] -Name $databasenames -InstanceName $instancenames |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Declare the $databasenames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server instances. 3. Run the Get-VESQLRDSDatabase cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value and specify the necessary restore session. * Set the $databasenames variable as the Name parameter value. * Set the $instancenames variable as the InstanceName parameter value.   Save the result to the $database variable to use it with other cmdlets. |

Related Commands

[Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md)

Page updated 2026-01-27

