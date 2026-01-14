---
title: "restore-veordatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-veordatabase.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restores a backed-up Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VEORDatabase [-Database] <VEORDatabase> [-Server <String>] [-OracleHome <String>] [-GlobalDatabaseName <String>] [-OracleSid <String>] [-WindowsCredentials <PSCredential>] [-OracleHomePassword <SecureString>] [-LinuxCredentials <VEORLinuxCredential>] [-SshPort <Int32>] [-ToDateTime <DateTime>] [-File <VEORDatabaseFile[]>] [-TargetPath <String[]>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet restores a backed-up Oracle database. You can restore an Oracle database to a Windows or a Linux machine.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database that the cmdlet will restore. | Accepts the [VEORDatabase](veordatabase.md) object. To get this object, run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. | True | 0 | True (ByValue) |
| LinuxCredentials | For restore to a Linux machine.  Specifies Linux credentials that the cmdlet will use to connect to a Linux machine. | Accepts the [VEORLinuxCredential](veorlinuxcredential.md) object. To get this object, run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. | True | Named | False |
| Server | For restore to another server.  Specifies DNS name or IP address of the target Oracle server to which the database will be restored.  Note: Do not provide this parameter if you want to restore to the original server. | String | False | Named | False |
| OracleHome | For restore to another location.  Specifies the target Oracle home path. The cmdlet will restore an Oracle database to the location specified in the Oracle home path.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| GlobalDatabaseName | For restore to another location.  Specifies the global database name. The cmdlet will restore an Oracle database with the specified name.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| OracleSid | For restore to another location.  Specifies target SID for an Oracle database.  The cmdlet will restore the database with the specified SID.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| WindowsCredentials | For restore to a Windows machine.  Specifies Windows credentials that the cmdlet will use to connect to a Windows machine. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| OracleHomePassword | For restoring Oracle Database 12c or later to a Windows machine.  Specifies Oracle home credentials that the cmdlet will use for starting Oracle Services on the guest OS.  Note that this parameter is required in case you use the following types of Oracle home User:   * Existing Windows user * New Windows user | SecureString | False | Named | False |
| ToDateTime | Specifies a point in time within the restore interval of an Oracle database.  The cmdlet will restore the database to the state of the specified point in time.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | Named | False |
| File | Specifies an array of Oracle database files. | Accepts the [VEORDatabaseFile](veordatabasefile.md)[] object. To get this object, run the [Get-VEORDatabaseFile](get-veordatabasefile.md) cmdlet. | False | Named | False |
| TargetPath | Specifies the target path array. The cmdlet will restore the Oracle database files to the locations specified in the array.  Note: You must assign a specific file path for each Oracle database file. | String[] | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing Oracle database with the database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| SshPort | For restore to a Linux machine.  Specifies the SSH port number that the cmdlet will use to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Latest State of Oracle Database to Same Server

|  |  |
| --- | --- |
| This example shows how to restore the latest state of an Oracle database to the original server.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  Restore-VEORDatabase -Database $database -Force |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the Restore-VEORDatabase cmdlet. Set the $database variable as the Database parameter value. Provide the Force parameter to overwrite the database on the original server with the restored database. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Oracle Database to Another Windows Server

|  |  |
| --- | --- |
| This example shows how to restore an Oracle database to another Windows machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  $windowscreds = Get-Credential  $orahomepass = Read-Host -Prompt "Enter your password" -AsSecureString  $pit = Get-Date -Date "2024-02-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  Restore-VEORDatabase -Database $database -WindowsCredentials $windowscreds -Server "winorcl01" -OracleHome "C:\app\Administrator\product\19.0.0.\dbhome\_1" -OracleHomePassword $orahomepass -GlobalDatabaseName "orcl\_res.tech.local" -OracleSid "orcl" -ToDateTime $pitutc |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the credentials that will be used for authenticating to the target Windows machine. Save the result to the $windowscreds variable. 3. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $orahomepass variable. 4. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state to which you want to restore your database. Save the result to the $pit variable. 5. Convert the $pit variable to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable.   Note that you can use the Get-VEORDatabaseRestoreInterval cmdlet to get the restore interval of the necessary database in UTC.   1. Run the Restore-VEORDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Set the $windowscreds variable as the WindowsCredentials parameter value. * Specify the Server parameter value. * Specify the OracleHome parameter value. * Set the $orahomepass variable as the OracleHomePassword parameter value. * Specify the GlobalDatabaseName parameter value. * Specify the OracleSid parameter value. * Set the $pitutc variable as the ToDateTime parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Oracle Database to Another Linux Server

|  |  |
| --- | --- |
| This example shows how to restore an Oracle database to another Linux machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEORLinuxCredential -Account "root" -Password $securepassword  $pit = Get-Date -Date "2024-02-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  Restore-VEORDatabase -Database $database -LinuxCredentials $linuxcreds -Server "linorcl01" -OracleHome "/u01/app/oracle/product/19.0.0/dbhome\_1/" -GlobalDatabaseName "orcl\_res.tech.local" -OracleSid "orcl" -ToDateTime $pitutc -SshPort 26 |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 3. Run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $linuxcreds variable. 4. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state to which you want to restore your database. Save the result to the $pit variable. 5. Convert the $pit variable to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable.   Note that you can use the Get-VEORDatabaseRestoreInterval cmdlet to get the restore interval of the necessary database in UTC.   1. Run the Restore-VEORDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Set the $linuxcreds variable as the LinuxCredentials parameter value. * Specify the Server parameter value. * Specify the OracleHome parameter value. * Specify the GlobalDatabaseName parameter value. * Specify the OracleSid parameter value. * Set the $pitutc variable as the ToDateTime parameter value. * Specify the SshPort parameter value. |

Related Commands

* [Get-VEORRestoreSession](get-veorrestoresession.md)
* [Get-VEORDatabase](get-veordatabase.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [New-VEORLinuxCredential](new-veorlinuxcredential.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
