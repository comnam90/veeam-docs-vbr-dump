---
title: "get-vesqlpublisheddatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlpublisheddatabase.html"
last_updated: "7/2/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns published Microsoft SQL Server databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPublishedDatabase [-Session] <IVESQLRestoreSession> [[-Name] <String[]>] [-ServerName <String[]>] [-InstanceName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of published Microsoft SQL databases.

|  |
| --- |
| Note |
| The cmdlet returns Microsoft SQL databases published in the PowerShell console only. The cmdlet does not return Microsoft SQL databases published in the Veeam Backup & Replication console. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will return information about a Microsoft SQL database added to the specified restore session. | Accepts the [VESQLRestoreSession](vesqlrestoresession.md) object. To get this object, run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names for Microsoft SQL databases. The cmdlet will return information about databases with the specified names. | String[] | False | 1 | False |
| ServerName | Specifies an array of target server names (as DNS names or IP addresses). The cmdlet will get Microsoft SQL databases that are published to these servers. | String[] | False | Named | False |
| InstanceName | Specifies an array of target instance names. The cmdlet will get Microsoft SQL databases that are published to these instances. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPublishedDatabase](vesqlpublisheddatabase.md)[] array that contains published Microsoft SQL databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Published Microsoft SQL Server Databases

|  |  |
| --- | --- |
| This example shows how to get an array of all published Microsoft SQL Server databases within a restore session.  |  | | --- | | $session = Get-VESQLRestoreSession  Get-VESQLPublishedDatabase -Session $session[0] |  Perform the following steps:   1. Run the Get-VESQLRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VESQLPublishedDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Published Microsoft SQL Server Databases with Specific Names Belonging to Specific Instances

|  |  |
| --- | --- |
| This example shows how to get an array of published Microsoft SQL Server databases with specific names belonging to specific instances on the backup file.  |  | | --- | | $session = Get-VESQLRestoreSession  $dbnames = @("db1", "db2")  $instancenames = @("instance\_01", "instance\_02")  $database = Get-VESQLPublishedDatabase -Session $session[0] -Name $dbnames -InstanceName $instancenames |  Perform the following steps:   1. Run the Get-VESQLRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the Microsoft SQL Server instances that you want to query. 3. Run the Get-VESQLPublishedDatabase cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value and select the necessary restore session. * Set the $dbnames variable as the Name parameter value. * Set the $instancenames variable as the InstanceName parameter value.   Save the result to the $database variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Microsoft SQL Server Databases Published on Specific Servers

|  |  |
| --- | --- |
| This example shows how to get an array of all Microsoft SQL Server databases published on the specified servers.  |  | | --- | | $session = Get-VESQLRestoreSession  $servernames = @("dlsql01", "dlsql02")  $database = Get-VESQLPublishedDatabase -Session $session[0] -ServerName $servernames |  Perform the following steps:   1. Run the Get-VESQLRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $servernames variable. Assign to this variable an array with the names of the necessary servers with Microsoft SQL Server. 2. Run the Get-VESQLPublishedDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Set the $servernames variable as the ServerName parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |

Related Commands

[Get-VESQLRestoreSession](get-vesqlrestoresession.md)

Page updated 7/2/2025

Page content applies to build 13.0.1.1071
