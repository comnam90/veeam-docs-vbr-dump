---
title: "Start-VEPSQLDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqldatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VEPSQLDatabaseRestore


Short Description

Restores a backed-up PostgreSQL database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEPSQLDatabaseRestore [-Database] <VEPSQLDatabase> [[-DatabaseName] <String>] [[-ToPointInTimeUTC] <DateTime>] [-LinuxCredentials <VEPSQLLinuxCredential>] [-ServerName <String>] [-SshPort <Int32>] -PostgreSqlCredentials <VEPSQLInstanceCredentials> [-TargetPort <Int32>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet restores a backed-up PostgreSQL database to a Linux-based server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Database | Specifies a PostgreSQL database that you want to restore.  Note that this parameter accepts a single database only. | Accepts the [VEPSQLDatabase](vepsqldatabase.md) object. To get this object, run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| DatabaseName | Specifies a name for the restored PostgreSQL database on the target location. The database will be restored with the specified name. | String | False | 1 | True (ByValue) |
| ToPointInTimeUTC | Specifies the point in time in the UTC format within a restore interval of the PostgreSQL instance.  The cmdlet will restore the database to the state of the specified point in time.  If you do not use this parameter, the cmdlet will restore the database to the point in time when the restore point for which you started the restore session was created. | DateTime | False | 2 | True (ByValue) |
| LinuxCredentials | Specifies Linux credentials. The cmdlet will use these credentials to connect to the target PostgreSQL server. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) object. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | False | Named | True (ByValue) |
| PostgreSqlCredentials | Specifies PostgreSQL role credentials for authenticating to PostgreSQL on the target machine. | Accepts the [VEPSQLInstanceCredentials](vepsqlinstancecredentials.md) object. To get this object, run the [New-VEPSQLInstanceCredentials](new-vepsqlinstancecredentials.md) cmdlet. | True | Named | True (ByValue) |
| ServerName | For restore to another server.  Specifies DNS name or IP address of the target PostgreSQL server. The cmdlet will restore a PostgreSQL database to that server. | String | False | Named | False |
| SshPort | Specifies the SSH port number. The cmdlet will use this port to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |
| TargetPort | Specifies the port to connect to the target PostgreSQL instance. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will replace the target PostgreSQL database with the database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabaseRestore](vepsqldatabaserestore.md) object that contains information about the restore process for the PostgreSQL database.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring PostgreSQL Database to Latest State

|  |  |
| --- | --- |
| This example shows how to restore a backed-up PostgreSQL database to its latest state on the selected restore point. The restore operation will start with the following settings:   * The cmdlet will use PostgreSQL peer authentication credentials for the current Linux OS user. * The cmdlet will restore the database to the point in time when the restore point for which you started the restore session was created. * The cmdlet will restore the database to the original PostgreSQL server, with the original name.   |  | | --- | | $session = Get-VEPSQLRestoreSession  $database = Get-VEPSQLDatabase -Session $session[0] -Name "IT"  $creds = New-VEPSQLInstanceCredentials -UseLinuxUserForPeerAuthentication  $restore = Start-VEPSQLDatabaseRestore -Database $database -PostgreSqlCredentials $creds |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [New-VEPSQLInstanceCredentials](new-vepsqlinstancecredentials.md) cmdlet. Provide the UseLinuxUserForPeerAuthentication parameter to create credentials that use the current Linux OS user for PostgreSQL peer authentication. Save the result to the $creds variable. 3. Run the Start-VEPSQLDatabaseRestore cmdlet. Set the $database variable as the Database parameter value. Set the $creds variable as the PostgreSqlCredentials parameter value. Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring PostgreSQL Database to Point-in-Time State

|  |  |
| --- | --- |
| This example shows how to restore a backed-up PostgreSQL database to a point-in-time state on the selected restore point. The restore operation will start with the following settings:   * The cmdlet will use custom Linux credentials to connect to the target Linux machine. * The cmdlet will use SQL credentials for authenticating to PostgreSQL on the target server. * The cmdlet will restore the database to a point-in-time state on the selected restore point. * The cmdlet will restore the database to another PostgreSQL server.   |  | | --- | | $session = Get-VEPSQLRestoreSession  $database = Get-VEPSQLDatabase -Session $session[0] -Name "IT"  $time = Get-Date -Date "2026-06-24 13:00:00"  $timeutc = $time.ToUniversalTime()  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcredentials = New-VEPSQLLinuxCredential -Account "wells" -Password $securepassword -ElevateAccountToRoot  $sqlcred = Get-Credential  $postgresqlcredentials = New-VEPSQLInstanceCredentials -SQLCredentials $sqlcred  $restore = Start-VEPSQLDatabaseRestore -Database $database -DatabaseName "Inventory" -ToPointInTimeUTC $timeutc -ServerName srv01.tech.local -LinuxCredentials $linuxcredentials -PostgreSqlCredentials $postgresqlcredentials -SshPort 23 -TargetPort 5555 |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the point in time to which the database must be restored. Save the result to the $time variable. 3. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $timeutc variable. 4. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 5. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Provide the ElevateAccountToRoot parameter. Save the result to the $linuxcredentials variable. 6. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter PostgreSQL credentials that will be used for authenticating to PostgreSQL on the target server. Save the result to the $sqlcred variable. 7. Run the [New-VEPSQLInstanceCredentials](new-vepsqlinstancecredentials.md) cmdlet. Set the $sqlcred variable as the SQLCredentials parameter value. Save the result to the $postgresqlcredentials variable. 8. Run the Start-VEPSQLDatabaseRestore cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the DatabaseName parameter value. * Set the $timeutc variable as the ToPointInTimeUTC parameter value. * Specify the ServerName parameter value. * Set the $linuxcredentials variable as the LinuxCredentials parameter value. * Set the $postgresqlcredentials variable as the PostgreSqlCredentials parameter value. * Specify the SshPort parameter value. * Specify the TargetPort parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-VEPSQLDatabase](get-vepsqldatabase.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)

* [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md)
* [New-VEPSQLInstanceCredentials](new-vepsqlinstancecredentials.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 2026-06-25

