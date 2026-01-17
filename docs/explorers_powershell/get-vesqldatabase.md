---
title: "Get-VESQLDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqldatabase.html"
last_updated: "7/2/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backed-up Microsoft SQL Server databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLDatabase [-Session] <IVESQLRestoreSession> [[-Name] <String[]>] [[-InstanceName] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Microsoft SQL Server databases.

After you get the backed-up Microsoft SQL Server databases, you can perform the following operations with these databases:

* [Publish-VESQLDatabase](publish-vesqldatabase.md)
* [Export-VESQLDatabase](export-vesqldatabase.md)
* [Restore-VESQLDatabase](restore-vesqldatabase.md)
* [Restore-VESQLIRDatabase](restore-vesqlirdatabase.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return an array of databases within the specified restore session. | Accepts the [VESQLRestoreSession](vesqlrestoresession.md) object. To get this object, run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names for Microsoft SQL Server databases. The cmdlet will return an array of databases with the specified names. | String[] | False | 1 | False |
| InstanceName | Specifies an array of names for Microsoft SQL Server instances. The cmdlet will return an array of databases located on the specified instances. | String[] | False | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabase](vesqldatabase.md)[] array that contains backed-up Microsoft SQL Server databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Microsoft SQL Server Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get a list of all Microsoft SQL Server databases within the specified restore session.  |  | | --- | | $session = Get-VESQLRestoreSession  Get-VESQLDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the second restore session in the array).   1. Run the Get-VESQLDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft SQL Server Databases with Specified Name

|  |  |
| --- | --- |
| This example shows how to get all Microsoft SQL Server databases with the specified name.  |  | | --- | | $session = Get-VESQLRestoreSession  Get-VESQLDatabase -Session $session[0] -Name "New SQL Database" |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VESQLDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Microsoft SQL Server Databases with Specific Names Belonging to Specific Instances

|  |  |
| --- | --- |
| This example shows how to get all Microsoft SQL Server databases with specific names that belong to specific instances.  |  | | --- | | $session = Get-VESQLRestoreSession  $databasenames = @("db1", "db2")  $instancenames = @("instance\_01", "instance\_02")  Get-VESQLDatabase -Session $session[0] -Name @databasenames -InstanceName @instancenames |  Perform the following steps:   1. Run the Get-VESQLRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $databasenames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server instances. 3. Run the Get-VESQLDatabase cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value and specify the necessary restore session. * Set the $databasenames variable as the Name parameter value. * Set the $instancenames variable as the InstanceName parameter value. |

Related Commands

[Get-VESQLRestoreSession](get-vesqlrestoresession.md)

Page updated 7/2/2025

Page content applies to build 13.0.1.1071
