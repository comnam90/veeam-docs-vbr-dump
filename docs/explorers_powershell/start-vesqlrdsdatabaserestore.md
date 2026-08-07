---
title: "Start-VESQLRDSDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqlrdsdatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VESQLRDSDatabaseRestore


Short Description

Restores a backed-up Microsoft SQL Server database running on Amazon RDS to an on-premise Microsoft SQL Server machine.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VESQLRDSDatabaseRestore [-RestorePoint] <VESQLRDSRestorePoint> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-TargetFolder <String>] [-File <VESQLDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet restores a backed-up Microsoft SQL Server database running on Amazon RDS to an on-premise Microsoft SQL Server machine.

You can stop the restore process with the [Stop-VESQLRDSDatabaseRestore](stop-vesqlrdsdatabaserestore.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies a restore point as of which the cmdlet will restore the database. | Accepts the [VESQLRDSRestorePoint](vesqlrdsrestorepoint.md) object. To get this object, run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. | True | 0 | True (ByValue) |
| DatabaseName | For restore to another location.  Specifies a name for the restored Microsoft SQL Server database on the target location. The database will be restored with the specified name. | String | False | Named | False |
| File | Specifies an array of file names for a Microsoft SQL Server database. | Accepts the [VESQLDatabaseFile](vesqldatabasefile.md)[] object. To get this object, run the [Get-VESQLRDSDatabaseFile](get-vesqlrdsdatabasefile.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will overwrite an existing Microsoft SQL Server database with a database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the target machine. If these credentials do not work, the cmdlet will use the credentials specified in the backup job.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| InstanceName | For restore to another location.  Specifies the name of the target instance. The cmdlet will restore the Microsoft SQL Server database to the specified target instance. | String | False | Named | False |
| Port | Specifies a port number that will be used to connect to the target Microsoft SQL Server machine. | Int32 | False | Named | False |
| RecoveryState | Specifies the recovery option.   * Recovery — use this option to leave a Microsoft SQL Server database in the ready to use state. With this option, you will not be able to restore additional transaction logs. * NoRecovery — use this option to leave a Microsoft SQL Server database in the non-operational state and to avoid rolling back uncommitted transactions. Use this option to restore transaction logs that are backed up with a third-party tool. * StandBy — use this option to leave the Microsoft SQL Server database in the read-only mode. It allows you to undo uncommitted transactions. The undo actions are saved in a standby file so that the recovery effects can be reversed.   Default: Recovery | RestoreMode | False | Named | False |
| ServerName | Specifies DNS name or IP address of the target server. The cmdlet will restore a Microsoft SQL Server database to the specified target server. | String | True | Named | False |
| SqlCredentials | Specifies SQL credentials for authenticating to Microsoft SQL Server on the target machine.  Note: If you do not specify SQL credentials, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| StandbyFilePath | For the StandBy recovery option.  Specifies a location for the standby file with the uncommitted transactions. | String | False | Named | False |
| TargetPath | Specifies a target path array. The cmdlet will restore Microsoft SQL Server database files to the locations specified in the target path array.  Note that you must assign a specific file path for every Microsoft SQL Server database file. | String[] | False | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the target machine. If you do not provide additional credentials, the cmdlet will use SQL credentials from the backup job and guest credentials from the protection group.  Note: If you omit this parameter, the cmdlet will use credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. | SwitchParameter | False | Named | False |
| TargetFolder | For restore of SQL Server database files to specific location.  Specifies a folder on the target machine. The cmdlet will restore all database files to that folder.  Note: This parameter is not available if you use the TargetPath parameter. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSDatabaseRestore](vesqlrdsdatabaserestore.md) object that contains details on the restore job for a backed-up Microsoft SQL Server database running on Amazon RDS.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Microsoft SQL Server Database to Latest State

|  |  |
| --- | --- |
| This example shows how to restore a backed-up Microsoft SQL Server database running on Amazon RDS to the latest state on the backup file. The restore operation will run with the following settings:   * The cmdlet will restore the database files to another server (dlsql02). * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server. * The cmdlet will use the guest credentials for authenticating to the guest OS.   |  | | --- | | $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[0] -Name "db1"  $restorepoint = Get-VESQLRDSRestorePoint -Database $database  $sqlcreds = Get-Credential  $oscreds = Get-Credential  $restore = Start-VESQLRDSDatabaseRestore -RestorePoint $restorepoint -ServerName "dlsql02" -UseSqlAuthentication -SqlCredentials $sqlcreds -GuestCredentials $oscreds |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to Microsoft SQL Server. Save the result to the $sqlcreds variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter guest credentials that will be used for authenticating to the guest OS. Save the result to the $oscreds variable. 5. Run the Start-VESQLRDSDatabaseRestore cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the ServerName parameter value. * Provide the UseSqlAuthentication parameter.  * Set the $sqlcreds variable as the SqlCredentials parameter value. * Set the $oscreds variable as the GuestCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Microsoft SQL Server Database to Specific Folder

|  |  |
| --- | --- |
| This example shows how to restore a backed-up Microsoft SQL Server databases running on Amazon RDS to a specific folder. SQL credentials are used for authenticating to the guest OS and Microsoft SQL Server.  |  | | --- | | $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[0] -Name "db1"  $restorepoint = Get-VESQLRDSRestorePoint -Database $database  $creds = Get-Credential  $restore = Start-VESQLRDSDatabaseRestore -RestorePoint $restorepoint -ServerName "SQLServer" -TargetPath "C:\SQL\Restore" -SqlCredentials $creds |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to the guest OS and Microsoft SQL Server. Save the result to the $creds variable. 4. Run the Start-VESQLRDSDatabaseRestore cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the ServerName parameter value. * Specify the TargetPath parameter value. * Set the $creds variable as the SqlCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Microsoft SQL Server Database Files to Specific Path Array

|  |  |
| --- | --- |
| This example shows how to restore database files to the specified array of paths. The restore job will run with the following options:   * The cmdlet will restore the File1.mdf file to the C:\SQLDBfile1\new\_file.mdf location. * The cmdlet will restore the File2.ldf file to the C:\SQLDBfile2\new\_file.ldf location. * The cmdlet will restore the database files as of the selected restore point. * The cmdlet will restore the database files to another server (dlsql02). * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server. * The cmdlet will use the guest credentials for authenticating to the guest OS.   |  | | --- | | $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[0] -Name "SQLDatabase"  $restorepoint = Get-VESQLRDSRestorePoint -Database $database  $files = Get-VESQLRDSDatabaseFile -RestorePoint $restorepoint  $path = @("C:\SQLDBfile1\new\_file.mdf","C:\SQLDBfile2\new\_file.ldf")  $sqlcreds = Get-Credential  $oscreds = Get-Credential  $restore = Start-VESQLRDSDatabaseRestore -RestorePoint $restorepoint -ServerName "dlsql02" -File $files -TargetPath $path -UseSqlAuthentication -SqlCredentials $sqlcreds -GuestCredentials $oscreds |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $database variable. 2. Run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-VESQLRDSDatabaseFile](get-vesqlrdsdatabasefile.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $files variable. 4. Declare the $path variable. Assign to this variable an array of paths for every database file that you want to restore. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to Microsoft SQL Server. Save the result to the $sqlcreds variable. 6. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter guest credentials that will be used for authenticating to the guest OS. Save the result to the $oscreds variable. 7. Run the Start-VESQLRDSDatabaseRestore cmdlet. Specify the following settings:  * Specify the ServerName parameter value. * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $files variable as the File parameter value. * Set the $path variable as the TargetPath parameter value. * Provide the UseSqlAuthentication parameter. * Set the $sqlcreds variable as the SqlCredentials parameter value. * Set the $oscreds variable as the GuestCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Microsoft SQL Server Database to Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to restore a backed-up Microsoft SQL Server database running on Amazon RDS as of a specific restore point. The restore job will run with the following options:   * The cmdlet will restore the database to the dlsql02 server. * The cmdlet will use the NoRecovery restore option. * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server and the guest OS.   |  | | --- | | $session = Get-VESQLRDSRestoreSession  $database = Get-VESQLRDSDatabase -Session $session[0] -Name "db1"  $restorepoint = Get-VESQLRDSRestorePoint -Database $database  $creds = Get-Credential  $restore = Start-VESQLRDSDatabaseRestore -RestorePoint $restorepoint -ServerName "dlsql02" -RecoveryState NoRecovery -SqlCredentials $creds |  Perform the following steps:   1. Run the [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable.   The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In this example, it is the third restore point in the array.   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the guest OS and Microsoft SQL Server on the target server. Save the result to the $creds variable.  1. Run the Start-VESQLRDSDatabaseRestore cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the ServerName parameter value. * Set the NoRecovery property as the RecoveryState parameter value. * Set the $creds variable as the SqlCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md)
* [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md)
* [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-VESQLRDSDatabaseFile](get-vesqlrdsdatabasefile.md)

Page updated 2026-04-10

