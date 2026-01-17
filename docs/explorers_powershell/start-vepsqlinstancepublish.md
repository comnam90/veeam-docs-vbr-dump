---
title: "Start-VEPSQLInstancePublish"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqlinstancepublish.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Publishes a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEPSQLInstancePublish [-Instance] <VEPSQLInstance> [[-ToPointInTimeUTC] <DateTime>] -LinuxCredentials <VEPSQLLinuxCredential> [-ServerName <String>] [-SshPort <Int32>] [-Force] [-Port <Int32>] [<CommonParameters>] |

Detailed Description

This cmdlet publishes a backed-up PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a PostgreSQL instance that the cmdlet will publish. | Accepts the [VEPSQLInstance](vepsqlinstance.md) object. To get this object, run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. | True | 0 | True (ByValue) |
| ToPointInTimeUTC | Specifies a point in time in the UTC format within the restore interval of the PostgreSQL instance.  The cmdlet will publish the instance to the state of the specified point in time. | DateTime | False | 1 | False |
| LinuxCredentials | Specifies Linux credentials that the cmdlet will use to connect to the Linux machine. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) object. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | True | Named | True (ByValue) |
| ServerName | Specifies DNS name or IP address of the target PostgreSQL server. The cmdlet will publish a PostgreSQL instance to that server. | String | False | Named | False |
| SshPort | Specifies the SSH port number. The cmdlet will use this port to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |
| Force | Defines that the cmdlet will replace the target PostgreSQL instance with the instance from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| Port | Specifies the port to connect to the published PostgreSQL instance. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstancePublish](vepsqlinstancepublish.md)[] array that contains information about the publishing process for the PostgreSQL instance.

Example

Publishing PostgreSQL Instance

This example shows how to publish backed-up PostgreSQL instance to a machine with PostgreSQL.

|  |
| --- |
| $session = Get-VEPSQLRestoreSession  $instance = Get-VEPSQLInstance -Session $session[0]  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEPSQLLinuxCredential -Account "root" -Password $securepassword  Start-VEPSQLInstancePublish -Instance $instance -LinuxCredentials $linuxcreds |

Perform the following steps:

1. Get the restore session:

1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $instance variable.

1. Get Linux credentials:

1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable.
2. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value.

1. Run the Start-VEPSQLInstancePublish cmdlet. Specify the following settings:

* Set the $instance variable as the Instance parameter value.
* Set the $linuxcreds variable as the LinuxCredentials parameter value.

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-VEPSQLInstance](get-vepsqlinstance.md)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md)

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
