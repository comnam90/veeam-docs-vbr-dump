---
title: "Restore-VEORRMANDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-veorrmandatabase.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restores an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VEORRMANDatabase [-Database] <VEORRMANDatabase> [-ChannelsNumber <Int32>] [-Server <String>] [-OracleSid <String>] [-OracleHome <String>] [-GlobalDatabaseName <String>] [-ChangeDbId] [-Restore] [-Recover] [-RestoreAndRecover] [-WindowsCredentials <PSCredential>] [-OracleHomePassword <SecureString>] [-SysUserPassword <SecureString>] [-LinuxCredentials <VEORLinuxCredential>] [-SshPort <Int32>] [-ToCurrentPointInTime] [-UntilTime <DateTime>] [-UntilScn <BigInteger>] [-UntilSeq <BigInteger>] [-File <VEORDatabaseFile[]>] [-TargetPath <String[]>] [-SuppressResetLog] [-Force] [-ManualChannelsAllocation] [<CommonParameters>] |

Detailed Description

This cmdlet restores an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database. The cmdlet will start a restore of the specified database. | Accepts the [VEORRMANDatabase](veorrmandatabase.md) object. To get this object, run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Server | For restore to another server.  Specifies DNS name or IP address of the target server to which the cmdlet will restore an Oracle database.  Note: Do not provide this parameter if you want to restore to the original server. | String | False | Named | False |
| OracleSid | For restore to another location.  Specifies a new SID for an Oracle database. The cmdlet will restore the database with the specified SID.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| OracleHome | For restore to another location.  Specifies the target Oracle home path. The cmdlet will restore an Oracle database to the location specified in the Oracle home path.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| GlobalDatabaseName | For restore to another location.  Specifies the global database name. The cmdlet will restore an Oracle database with the specified name.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| LinuxCredentials | For restore to a Linux machine.  Specifies Linux credentials that the cmdlet will use to connect to a Linux machine. | Accepts the [VEORLinuxCredential](veorlinuxcredential.md) object. To get this object, run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. | False | Named | False |
| WindowsCredentials | For restore to a Windows machine.  Specifies Windows credentials that the cmdlet will use to connect to a Windows machine. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| SysUserPassword | For restore with database authentication.  Specifies the password for the SYS user of the target database.  Note: This parameter is required when OS authentication to Oracle databases is disabled on the target server. | SecureString | False | Named | False |
| OracleHomePassword | For restoring Oracle Database 12c or later on Windows server.  Specifies Oracle home credentials that the cmdlet will use for starting Oracle Services on the guest OS.  Note: This parameter is required in case you use the following types of Oracle home User:   * Existing Windows user. * New Windows user. | SecureString | False | Named | False |
| Recover | Defines that the cmdlet will restore the Oracle database to the latest available state. | SwitchParameter | False | Named | False |
| Restore | Defines that the cmdlet will restore the data files from a specific point in time without applying log files. | SwitchParameter | False | Named | False |
| RestoreAndRecover | Defines that the cmdlet will restore the data files from a specific point in time and will apply log files. | SwitchParameter | False | Named | False |
| ToCurrentPointInTime | Defines that the cmdlet will restore the data from the latest available point in time. | SwitchParameter | False | Named | False |
| UntilScn | Specifies the System Change Number (SCN). The cmdlet will restore the database from a consistent point. | BigInteger | False | Named | False |
| UntilSeq | Specifies the sequence from which the cmdlet will restore the database. | BigInteger | False | Named | False |
| UntilTime | Specifies the date and time from which the cmdlet will restore the database. | DateTime | False | Named | False |
| ChangeDbId | For restore to another location.  Defines that the cmdlet will generate a new database ID.  If you omit this parameter, the database will be restored with the current ID.  Note: The command will not run if you use this parameter together with the SuppressResetLog parameter. | SwitchParameter | False | Named | False |
| File | Specifies an array of Oracle database files. | Accepts the [VEORRMANDatabaseFile](veorrmandatabasefile.md)[] object. To get this object, run the [Get-VEORRMANDatabaseFile](get-veorrmandatabasefile.md) cmdlet. | False | Named | False |
| ChannelsNumber | Specifies the number of channels used to restore Oracle databases.  By default, the cmdlet will use the default channel configuration, specified in the Veeam Plug-in for Oracle RMAN settings. | Int32 | False | Named | False |
| SuppressResetLog | Defines that Veeam Plug-in for Oracle RMAN will not run the ALTER DATABASE OPEN RESETLOG command after recovery or restore operations.  Note: Do not provide this parameter if you run the script with the following parameters:   * OracleHome * OracleSid * GlobalDatabaseName * ChangeDBID | SwitchParameter | False | Named | False |
| SshPort | For restore to a Linux machine.  Specifies the SSH port number that the cmdlet will use to connect to the Linux machine. | Int32 | False | Named | False |
| TargetPath | Specifies the target path array. The cmdlet will restore the Oracle database files to the locations specified in the array.  Note: You must assign a specific file path for each Oracle database file. | String[] | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing Oracle database with the database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| ManualChannelsAllocation | This parameter is deprecated. Use the ChannelsNumber parameter instead. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Oracle Database to Another Location

|  |  |
| --- | --- |
| This example shows how to restore an Oracle database backed up with Veeam Plug-in for Oracle RMAN to the OracleSrv2049 server with the following settings:   * The cmdlet will restore the database to the latest available state on the backup file.  * The database will be assigned the ORCL Oracle SID. * The database will be assigned the orcl global database name. * The database will be restored to the E:\app\administrator\product\19.3.0\dbhome\_1 Oracle home path. * The cmdlet will generate a new database ID.  * The cmdlet will restore the database to another Linux server.  * The cmdlet will use operating system authentication to connect to the Oracle database.     |  | | --- | | $backup = Get-VEORRMANBackup -Name "Oracle RMAN\*"  $session = Start-VEORRMANRestoreSession -Backup $backup  $database = Get-VEORRMANDatabase -Session $session -Name "orcl"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $credentials = New-VEORLinuxCredential -Account "root" -Password $securepassword  Restore-VEORRMANDatabase -Database $database -Server "OracleSrv2049" -LinuxCredentials $credentials -OracleSid ORCL -OracleHome "E:\app\administrator\product\19.3.0\dbhome\_1" -GlobalDatabaseName orcl -ChangeDbId -ToCurrentpointInTime -Recover |  Perform the following steps:   1. Run the [Get-VEORRMANBackup](get-veorrmanbackup.md) cmdlet. Specify the Name parameter value. Use the wildcard \* character to get all backups whose names begin with "Oracle RMAN". Save the result to the $backup variable. 2. Run the [Start-VEORRMANRestoreSession](start-veorrmanrestoresession.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $session variable. 3. Run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter the password that will be used to connect to the target server and the Oracle database. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $credentials variable. 3. Run the Restore-VEORRMANDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Server parameter value. * Set the $credentials variable as the LinuxCredentials parameter value. * Specify the OracleSid parameter value. * Specify the OracleHome parameter value. * Specify the GlobalDatabaseName parameter value. * Provide the ChangeDbId parameter. * Provide the ToCurrentpointInTime parameter. * Provide the Recover parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Oracle Database to Linux Server to the Latest Available State

|  |  |
| --- | --- |
| This example shows how to restore an Oracle database backed up with Veeam Plug-in for Oracle RMAN with the following settings:   * The cmdlet will restore the database to the latest available state on the backup file. * The cmdlet will restore the database to the original Linux server.  * The cmdlet will use operating system authentication to connect to the Oracle database.     |  | | --- | | $backup = Get-VEORRMANBackup -Name "Oracle RMAN\*"  $session = Start-VEORRMANRestoreSession -backup $backup  $database = Get-VEORRMANDatabase -Session $session -Name "orcl"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $credentials = New-VEORLinuxCredential -Account "root" -Password $securepassword  Restore-VEORRMANDatabase -Database $database -LinuxCredentials $credentials -ToCurrentPointInTime -Recover |  Perform the following steps:   1. Run the [Get-VEORRMANBackup](get-veorrmanbackup.md) cmdlet. Specify the Name parameter value. Use the wildcard \* character to get all backups whose names begin with "Oracle RMAN". Save the result to the $backup variable. 2. Run the [Start-VEORRMANRestoreSession](start-veorrmanrestoresession.md) cmdlet. Set the $backup variable as the Backup parameter value. 3. Run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target server and the Oracle database. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $credentials variable. 3. Run the Restore-VEORRMANDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Set the $credentials variable as the LinuxCredentials parameter value. * Provide the ToCurrentPointInTime parameter. * Provide the Recover parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Oracle Database to Windows Server with Database Authentication

|  |  |
| --- | --- |
| This example shows how to restore an Oracle database backed up with Veeam Plug-in for Oracle RMAN with the following settings:   * The cmdlet will restore the database to a specific point-in-time state on the backup file. * The cmdlet will restore the database to the original Windows server.  * The cmdlet will use database authentication to connect to the Oracle database. * The cmdlet will use 4 channels for restoring data. * The cmdlet will skip the OPEN RESETLOGS operation and keep the database in the mount state after restore.     |  | | --- | | $session = Get-VEORRMANRestoreSession  $database = Get-VEORRMANDatabase -Session $session[0] -Name "orcl"  $pit = Get-Date -Date "2024-10-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  $oscredentials = Get-Credential  $syspassword = Read-Host -Prompt "Enter password" -AsSecureString  Restore-VEORRMANDatabase -Database $database -WindowsCredentials $oscredentials -SysUserPassword $syspassword -RestoreAndRecover -UntilTime $pitutc -ChannelsNumber 4 -SuppressResetLog |  Perform the following steps:   1. Run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the point in time to which the database must be restored. Save the result to the $pit variable. 3. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the guest OS on the target server. Save the result to the $oscredentials variable. 5. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials for the SYS user that will be used to connect to the target Oracle Database. Define the AsSecureString parameter. Save the result to the $syspassword variable. 6. Run the Restore-VEORRMANDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Set the $oscredentials variable as the WindowsCredentials parameter value. * Set the $syspassword variable as the SysUserPassword parameter value. * Provide the RestoreAndRecover parameter. * Set the $pitutc variable as the UntilTime parameter value. * Specify the ChannelsNumber parameter value. * Provide the SuppressResetLog parameter. |

Related Commands

* [Get-VEORRMANBackup](get-veorrmanbackup.md)
* [Start-VEORRMANRestoreSession](start-veorrmanrestoresession.md)
* [Get-VEORRMANDatabase](get-veorrmandatabase.md)
* [New-VEORLinuxCredential](new-veorlinuxcredential.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
