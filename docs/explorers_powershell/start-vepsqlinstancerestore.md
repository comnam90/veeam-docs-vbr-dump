---
title: "Start-VEPSQLInstanceRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqlinstancerestore.html"
last_updated: "4/8/2025"
product_version: "13.0.1.1071"
---

# Start-VEPSQLInstanceRestore


Short Description

Restores a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEPSQLInstanceRestore [-Instance] <VEPSQLInstance> [[-ToPointInTimeUTC] <DateTime>] [-LinuxCredentials <VEPSQLLinuxCredential>] [-ServerName <String>] [-DataDirectory <String>] [-PostRestoreAction <VEPSQLPostRestoreAction>] [-SshPort <Int32>] [-Force] [-TablespacePath <String[]>] [-Tablespace <VEPSQLTableSpace[]>] [-Port <Int32>] [<CommonParameters>] |

Detailed Description

This cmdlet restores a backed-up PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a PostgreSQL instance that the cmdlet will restore. | Accepts the [VEPSQLInstance](vepsqlinstance.md) object. To get this object, run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. | True | 0 | True (ByValue) |
| ToPointInTimeUTC | Specifies the point in time in the UTC format within a restore interval of the PostgreSQL instance.  The cmdlet will restore the instance to the state of the specified point in time.  If you do not use this parameter, the cmdlet will restore the instance to the point in time when the restore point for which you started the restore session was created. | DateTime | False | 1 | False |
| LinuxCredentials | Specifies Linux credentials. The cmdlet will use these credentials to connect to the target PostgreSQL server. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) object. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | False | Named | True (ByValue) |
| ServerName | Specifies DNS name or IP address of the target PostgreSQL server. The cmdlet will restore a PostgreSQL instance to that server. | String | False | Named | False |
| DataDirectory | Specifies a path to the data directory for the restored PostgreSQL instance. The cmdlet will restore the specified instance to the specified data directory. | String | False | Named | False |
| PostRestoreAction | Specifies the action with the restored PostgreSQL instance.   * Promote — use this option to start the instance after restore. The instance will operate in a regular way as a production instance. * Pause — use this option to start the instance after restore. The instance will operate but will not accept incoming TCP connections. This option is useful, for example, if you want to verify the state of the PostgreSQL database after restore. * Shutdown — use this option to restore the instance without starting the instance after the restore process is completed.   Default: Promote | VEPSQLPostRestoreAction | False | Named | False |
| SshPort | Specifies the SSH port number. The cmdlet will use that port to connect to the target PostgreSQL server.  Default: 22 | Int32 | False | Named | False |
| Force | Defines that the cmdlet will replace the target PostgreSQL instance with the instance from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| TablespacePath | Specifies an array of tablespace paths for the restored PostgreSQL instance. The cmdlet will restore PostgreSQL tablespaces to locations specified in this array.  Note: This parameter must be used together with the Tablespace parameter. | String[] | False | Named | False |
| Tablespace | Specifies an array of tablespace names for the restored PostgreSQL instance. The cmdlet will restore tablespaces specified in this array.  Note:   * For every PostgreSQL tablespace, you must assign a specific tablespace path. * This parameter must be used together with the TablespacePath parameter. | Accepts the [VEPSQLTableSpace](vepsqltablespace.md)[] object. To get this object, run the [Get-VEPSQLTablespace](get-vepsqltablespace.md) cmdlet. | False | Named | False |
| Port | Specifies the port to connect to the restored PostgreSQL instance. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstanceRestore](vepsqlinstancerestore.md) object that contains information about the restore process for the PostgreSQL instance.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring PostgreSQL Instance to Original Server

|  |  |
| --- | --- |
| This example shows how to restore a backed-up PostgreSQL instance to a target PostgreSQL server. The restore operation will start with the following settings:   * The cmdlet will restore the instance to the point in time when the restore point for which you started the restore session was created. * The cmdlet will restore the instance to the original PostgreSQL server.     |  | | --- | | $session = Get-VEPSQLRestoreSession  $instance = Get-VEPSQLInstance -Session $session[0] -DataDirectory /var/lib/pgsql/13/data  Start-VEPSQLInstanceRestore -Instance $instance |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value. Specify the DataDirectory parameter value. Save the result to the $instance variable. 2. Run the Start-VEPSQLInstanceRestore cmdlet. Set the $instance variable as the Instance parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring PostgreSQL Instance to Another Server

|  |  |
| --- | --- |
| This example shows how to restore a backed-up PostgreSQL instance to a target PostgreSQL server. The restore operation will start with the following settings:   * The cmdlet will restore the instance to a specific point in time. * The cmdlet will restore the instance to another PostgreSQL server. * The cmdlet will restore the instance to a specific data directory. * The cmdlet will restore tablespaces of the PostgreSQL instance to specific paths.   |  | | --- | | $session = Get-VEPSQLRestoreSession  $time = Get-Date -Date "2022-06-24 13:00:00"  $timeutc = $time.ToUniversalTime()  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $credentials = New-VEPSQLLinuxCredential -Account "postgres" -Password $securepassword -ElevateAccountToRoot  $instance = Get-VEPSQLInstance -Session $session[0] -DataDirectory /var/lib/pgsql/13/data  $tbsp = @("/ssd1/postgresql/data","/ssd2/postgresql/data2")  $tbsplist = Get-VEPSQLTablespace -Instance $instance  Start-VEPSQLInstanceRestore -Instance $instance -ToPointInTimeUTC $timeutc -ServerName srv01.tech.local -LinuxCredentials $credentials -DataDirectory /var/lib/pgsql/13/database -TablespacePath $tbsp -Tablespace $tbsplist -Port 5555 |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the point in time to which the instance must be restored. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $timeutc variable. 3. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 4. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Provide the ElevateAccountToRoot parameter. Save the result to the $credentials variable. 5. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value. Specify the DataDirectory parameter value. Save the result to the $instance variable. 6. Declare the $tbsp variable. Assign to this variable the array of tablespace paths for the restored PostgreSQL instance. 7. Run the [Get-VEPSQLTablespace](get-vepsqltablespace.md) cmdlet to get the list of tablespace names for the restored PostgreSQL instance. Set the $instance variable as the Instance parameter value. Save the result to the $tbsplist variable. 8. Run the Start-VEPSQLInstanceRestore cmdlet. Specify the following settings:  * Set the $instance variable as the Instance parameter value. * Set the $timeutc variable as the ToPointInTimeUTC parameter value. * Specify the ServerName parameter value. * Set the $credentials variable as the LinuxCredentials parameter value. * Specify the DataDirectory parameter value. * Set the $tbsp variable as the TablespacePath parameter value. * Set the $tbsplist variable as the Tablespace parameter value. * Specify the Port parameter value. |

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [Get-VEPSQLInstance](get-vepsqlinstance.md)
* [Get-VEPSQLTablespace](get-vepsqltablespace.md)

* [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md)


