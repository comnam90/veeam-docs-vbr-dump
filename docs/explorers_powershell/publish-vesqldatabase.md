---
title: "publish-vesqldatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/publish-vesqldatabase.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Publishes a backed-up Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Publish-VESQLDatabase [-Database] <VESQLDatabase> [-DatabaseName <String>] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-UseSQLAuthentication] [-SqlCredentials <PSCredential>] [-GuestCredentials <PSCredential>] [-ToPointInTime <DateTime>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet allows you to publish a backed-up Microsoft SQL Server database to a target server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database that you want to publish. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| ServerName | Specifies DNS name or IP address of the target server. The cmdlet will publish a Microsoft SQL Server database to that server. | String | True | Named | False |
| DatabaseName | Specifies a new name for a Microsoft SQL Server database. The cmdlet will publish the existing database with this name. | String | False | Named | False |
| InstanceName | Specifies the name of the target instance. The cmdlet will publish the Microsoft SQL Server database to that instance. | String | False | Named | False |
| Port | Specifies a port number. The cmdlet will use this port to connect to the target machine with Microsoft SQL Server. | Int32 | False | Named | False |
| SqlCredentials | Specifies the credentials for authenticating to Microsoft SQL Server on the target machine.  Note: If you do not specify SQL credentials, the cmdlet will use the current account credentials. If these credentials do not work, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the target machine.  Note: If you omit this parameter, the cmdlet will use the credentials specified in the SQLCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the target server. If these credentials do not work, the cmdlet will use the credentials specified in the backup job.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS on the target server.  * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ToPointInTime | Specifies a point in time within the restore interval of a Microsoft SQL Server database.  The cmdlet will publish the database to the state of the specified point in time.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing database with the database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPublishedDatabase](vesqlpublisheddatabase.md) object that contains a published Microsoft SQL Server database.

Example

Publishing Microsoft SQL Server Database to Specific Server

This example shows how to publish a Microsoft SQL Server database to a specific server. This example uses the current account credentials to log in to the guest OS and Microsoft SQL Server on the target machine.

|  |
| --- |
| $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  Publish-VESQLDatabase -Database $database -ServerName "TargetServer" |

Perform the following steps:

1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Publish-VESQLDatabase cmdlet. Specify the following settings:

* Set the $database variable as the Database parameter value.
* Specify the ServerName parameter value.

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)

Page updated 3/5/2025

Page content applies to build 13.0.1.1071
