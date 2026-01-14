---
title: "get-vepsqldatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqldatabase.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backed-up PostgreSQL databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLDatabase [-Session] <VEPSQLRestoreSession> [[-Name] <String[]>] [[-InstanceName] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up PostgreSQL databases.

After you get the backed-up PostgreSQL databases, you can use the [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) cmdlet to export the necessary databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return an array of databases within the specified restore session. | Accepts the [VEPSQLRestoreSession](vepsqlrestoresession.md) object. To get this object, run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names of PostgreSQL databases. The cmdlet will return an array of databases with the specified names. | String[] | False | 1 | False |
| InstanceName | Specifies an array of names of PostgreSQL instances. The cmdlet will return an array of databases located on the specified instances. | String[] | False | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabase](vepsqldatabase.md)[] array that contains backed-up PostgreSQL databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All PostgreSQL Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get an array of all PostgreSQL databases within the specified restore session.  |  | | --- | | $session = Get-VEPSQLRestoreSession  $database = Get-VEPSQLDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the second restore session in the array).   1. Run the Get-VEPSQLDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $database variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting PostgreSQL Databases With Specified Names

|  |  |
| --- | --- |
| This example shows how to get an array of PostgreSQL databases with the specified names.  |  | | --- | | $session = Get-VEPSQLRestoreSession  $dbnames = @("fiscal", "sales", "IT")  $database = Get-VEPSQLDatabase -Session $session[0] -Name $dbnames |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary PostgreSQL databases. 2. Run the Get-VEPSQLDatabase cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. Set the $dbnames variable as the Name parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All PostgreSQL Databases on Specified Instances

|  |  |
| --- | --- |
| This example shows how to get all PostgreSQL databases on specific instances.  |  | | --- | | $session = Get-VEPSQLRestoreSession  $instancenames = @("rhel01:5433", "rhel01:5434")  $database = Get-VEPSQLDatabase -Session $session[0] -InstanceName @instancenames |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $instancenames variable. Assign to this variable an array with the names of the necessary PostgreSQL instances. 2. Run the Get-VEPSQLDatabase cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. Set the $instancenames variable as the InstanceName parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |

Related Commands

[Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
