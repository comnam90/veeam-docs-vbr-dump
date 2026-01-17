---
title: "Start-VESQLPluginDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqlplugindatabaserestore.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restores a database backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore a database to the original server as of the latest state on the backup file.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-File <VESQLPluginDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-Force] [<CommonParameters>] |

* Restore a database to the original server as of a particular restore point.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -RestorePoint <VESQLPluginRestorePoint> [-File <VESQLPluginDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-Force] [<CommonParameters>] |

* Restore a database to the original server as of a particular point-in-time state.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -ToPointInTimeUtc <DateTime> [-File <VESQLPluginDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-Force]  [<CommonParameters>] |

* Restore a database to another server as of the latest state on the backup file.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-File <VESQLPluginDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-Force] [<CommonParameters>] |

* Restore a database to another server as of a particular restore point.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -RestorePoint <VESQLPluginRestorePoint> [-File <VESQLPluginDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-Force] [<CommonParameters>] |

* Restore a database to another server as of a particular point-in-time state.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -ToPointInTimeUtc <DateTime> [-File <VESQLPluginDatabaseFile[]>] [-TargetPath <String[]>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-Force] [<CommonParameters>] |

* Restore a database to the original server as of the latest state on the backup file, using quick recovery.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-QuickRecovery] [-Force] [<CommonParameters>] |

* Restore a database to the original server as of a particular restore point, using quick recovery.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -RestorePoint <VESQLPluginRestorePoint> [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-QuickRecovery] [-Force] [<CommonParameters>] |

* Restore a database to the original server as of a particular point-in-time state, using quick recovery.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -ToPointInTimeUtc <DateTime> [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-QuickRecovery] [-Force] [<CommonParameters>] |

* Restore a database to another server as of the latest state on the backup file, using quick recovery.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-QuickRecovery] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-Force] [<CommonParameters>] |

* Restore a database to another server as of a particular restore point, using quick recovery.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -RestorePoint <VESQLPluginRestorePoint> [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-QuickRecovery] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-Force] [<CommonParameters>] |

* Restore a database to another server as of a particular point-in-time state, using quick recovery.

|  |
| --- |
| Start-VESQLPluginDatabaseRestore [-Database] <VESQLPluginDatabase> [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] -ToPointInTimeUtc <DateTime> [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [-QuickRecovery] -ServerName <String> [-InstanceName <String>] [-Port <Int32>] [-DatabaseName <String>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet restores a database backed up with Veeam Plug-in for Microsoft SQL Server. You can restore a Microsoft SQL database to the original location or to another location. You can stop the restore process with the [Stop-VESQLPluginDatabaseRestore](stop-vesqlplugindatabaserestore.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database that you want to restore. | Accepts the [VESQLPluginDatabase](vesqlplugindatabase.md) object. To get this object, run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. | True | 0 | True (ByValue) |
| DatabaseName | For restore to another location.  Specifies a name for the restored Microsoft SQL Server database on the target location. The database will be restored with the specified name. | String | False | Named | False |
| File | Specifies an array of file names for a Microsoft SQL database. | Accepts the [VESQLPluginDatabaseFile](vesqlplugindatabasefile.md)[] object. To get this object, run the [Get-VESQLPluginDatabaseFile](get-vesqlplugindatabasefile.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will overwrite an existing Microsoft SQL database with a Microsoft SQL database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the target machine. If these credentials do not work, the cmdlet will use the credentials specified in the backup job.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| QuickRecovery | Defines that the cmdlet will use incremental restore or quick recovery. The cmdlet applies differential or log backups to an existing database, removing the need to restore the entire database.  Consider the following:   * If you use this parameter, do not specify the TargetPath parameter. * The target database must have the NoRecovery or StandBy state. | SwitchParameter | True | Named | False |
| InstanceName | For restore to another location.  Specifies the name of the target instance. The cmdlet will restore the Microsoft SQL Server database to the specified target instance. | String | False | Named | False |
| Port | For restore to another location.  Specifies a port number that will be used to connect to the target Microsoft SQL Server machine. | Int32 | False | Named | False |
| RecoveryState | Specifies the recovery option.   * Recovery — use this option to leave a Microsoft SQL database in the ready to use state. With this option, you will not be able to restore additional transaction logs. * NoRecovery — use this option to leave a Microsoft SQL database in the non-operational state and to avoid rolling back uncommitted transactions. Use this option to restore transaction logs that are backed up with a third-party tool. * StandBy — use this option to leave the Microsoft SQL database in the read-only mode. It allows you to undo uncommitted transactions. The undo actions are saved in a standby file so that the recovery effects can be reversed.   Default: Recovery | RestoreMode | False | Named | False |
| RestorePoint | Specifies a restore point as of which the cmdlet will restore the database.  Note: Do not specify this parameter if you use the ToPointInTimeUtc parameter. | Accepts the [VESQLPluginRestorePoint](vesqlpluginrestorepoint.md) object. To get this object, run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. | True | Named | False |
| ServerName | For restore to another location.  Specifies DNS name or IP address of a Microsoft SQL target server. The cmdlet will restore a Microsoft SQL database to the specified target server. | String | True | Named | False |
| SqlCredentials | Specifies SQL credentials for authenticating to Microsoft SQL Server on the target machine.  Note: If you do not specify SQL credentials, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| StandbyFilePath | For the StandBy recovery option.  Specifies a location for the standby file with the uncommitted transactions. | String | False | Named | False |
| TargetPath | Specifies a target path array. The cmdlet will restore Microsoft SQL database files to the locations specified in the target path array.  Consider the following:   * You must assign a specific file path for every Microsoft SQL database file. * Do not specify this parameter if you use the QuickRecovery parameter.   This parameter accepts wildcard characters. | String[] | False | Named | False |
| ToPointInTimeUtc | Specifies a point in time in UTC within the restore interval of a Microsoft SQL database. The cmdlet will restore the database to the state of the specified point in time.  Note: Do not specify this parameter if you use the RestorePoint parameter. | DateTime | True | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the target machine. If you do not provide additional credentials, the cmdlet will use SQL credentials from the backup job and guest credentials from the protection group.  Note: If you omit this parameter, the cmdlet will use credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginRestore](vesqlpluginrestore.md) object that contains details on the restore job for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Microsoft SQL Server Database to Original Location

|  |  |
| --- | --- |
| This example shows how to restore a database backed up with Veeam Plug-in for Microsoft SQL Server to the original location. The restore operation will run with the following settings:   * The cmdlet will use the credentials of the user that is running the PowerShell session. * If these credentials do not work, the cmdlet will use the backup job credentials to connect to the guest OS and to Microsoft SQL Server. * The database will be restored to the latest state on the backup file.     |  | | --- | | $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "db1"  $restore = VESQLPluginDatabaseRestore -Database $database |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the Start-VESQLPluginDatabaseRestore cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Microsoft SQL Server Database to Specific Folder

|  |  |
| --- | --- |
| This example shows how to restore a database backed up with Veeam Plug-in for Microsoft SQL Server to a specific folder. SQL credentials are used for authenticating to the guest OS and Microsoft SQL Server.  |  | | --- | | $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "db1"  $creds = Get-Credential  $restore = Start-VESQLPluginDatabaseRestore -Database $database -ServerName "SQLServer" -TargetPath "C:\SQL\Restore" -SqlCredentials $creds |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to the guest OS and Microsoft SQL Server. Save the result to the $creds variable. 3. Run the Start-VESQLPluginDatabaseRestore cmdlet. Specify the following settings:  * Set the $database variable as the Database value. * Specify the ServerName parameter value. * Specify the TargetPath parameter value. * Set the $creds variable as the SqlCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Microsoft SQL Server Database Files to Specific Path Array

|  |  |
| --- | --- |
| This example shows how to restore database files backed up with Veeam Plug-in for Microsoft SQL Server to the specified array of paths. The restore job will run with the following options:   * The cmdlet will restore the File1.mdf file to the C:\SQLDBfile1\new\_file.mdf location. * The cmdlet will restore the File2.ldf file to the C:\SQLDBfile2\new\_file.ldf location. * The cmdlet will restore the database files as of the latest state of the selected restore point. * The cmdlet will restore the database files to another server (dlsql02). * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server. * The cmdlet will use the guest credentials for authenticating to the guest OS.   |  | | --- | | $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "SQLDatabase"  $restorepoint = Get-VESQLPluginRestorePoint -Database $database  $files = Get-VESQLPluginDatabaseFile -RestorePoint $restorepoint  $path = @("C:\SQLDBfile1\new\_file.mdf","C:\SQLDBfile2\new\_file.ldf")  $sqlcreds = Get-Credential  $oscreds = Get-Credential  $restore = Start-VESQLPluginDatabaseRestore -Database $database -ServerName "dlsql02" -RestorePoint $restorepoint -File $files -TargetPath $path -UseSqlAuthentication -SqlCredentials $sqlcreds -GuestCredentials $oscreds |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $database variable. 2. Run the [Get-VESQLPluginDatabaseFile](get-vesqlplugindatabasefile.md) cmdlet. Set the $database variable as the Database parameter value. 3. Declare the $path variable. Assign to this variable an array of paths for every database file that you want to restore. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to Microsoft SQL Server. Save the result to the $sqlcreds variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter guest credentials that will be used for authenticating to the guest OS. Save the result to the $oscreds variable. 6. Run the Start-VESQLPluginDatabaseRestore cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the ServerName parameter value. * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $files variable as the File parameter value. * Set the $path variable as the TargetPath parameter value. * Provide the UseSqlAuthentication parameter. * Set the $sqlcreds variable as the SqlCredentials parameter value. * Set the $oscreds variable as the GuestCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Microsoft SQL Server Database to Point-in-Time State

|  |  |
| --- | --- |
| This example shows how to restore a database backed up with Veeam Plug-in for Microsoft SQL Server as of a specific point-in-time state. The restore job will run with the following options:   * The cmdlet will restore the database as of a specific point-in-time state. * The cmdlet will restore the database to the dlsql02 server. * The cmdlet will use the NoRecovery restore option. * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server and the guest OS.   |  | | --- | | $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "db1"  $restorepoint = Get-VESQLPluginRestorePoint -Database $database  $loginterval = Get-VESQLPluginLogInterval -RestorePoint $restorepoint[2]  $creds = Get-Credential  $pit = Get-Date -Date "2025-10-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  $restore = Start-VESQLPluginDatabaseRestore -Database $database -ServerName "dlsql02" -RecoveryState NoRecovery -SqlCredentials $creds -ToPointInTimeUtc $pitutc |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable.   The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the third restore point in the array.   1. Run the [Get-VESQLPluginLogInterval](get-vesqlpluginloginterval.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $loginterval variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to guest OS and the Microsoft SQL Server on the target server. Save the result to the $creds variable. 3. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state. Save the result to the $pit variable. 4. Convert the $pit variable to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable.   Note that you can use the $loginterval variable to check the available restore period within the selected restore point.   1. Run the Start-VESQLPluginDatabaseRestore cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the ServerName parameter value. * Set the NoRecovery property as the RecoveryState parameter value. * Set the $creds variable as the SqlCredentials parameter value. * Set the $pitutc variable as the ToPointInTimeUtc parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Restoring Microsoft SQL Server Database to Specific Restore Point with Quick Recovery

|  |  |
| --- | --- |
| This example shows how to restore a database backed up with Veeam Plug-in for Microsoft SQL Server as of a specific restore point, using quick recovery. The restore job will run with the following options:   * The cmdlet will restore the database as of the latest state of the selected restore point. * The cmdlet will restore the database to the original server. * The cmdlet will use the StandBy restore option. * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server. * The cmdlet will use the guest credentials for authenticating to the guest OS.   |  | | --- | | $session = Get-VESQLPluginRestoreSession  $database = Get-VESQLPluginDatabase -Session $session[0] -Name "db2"  $restorepoint = Get-VESQLPluginRestorePoint -Database $database  $creds = Get-Credential  $oscreds = Get-Credential  $restore = Start-VESQLPluginDatabaseRestore -Database $database -RestorePoint $restorepoint -RecoveryState StandBy -StandbyFilePath "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\Standby\SecondaryDatabase.trn" -QuickRecovery -UseSQLAuthentication -SqlCredentials $creds -GuestCredentials $oscreds |  Perform the following steps:   1. Run the [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $restorepoint variable.   The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the third restore point in the array.   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to guest OS and the Microsoft SQL Server on the target server. Save the result to the $creds variable. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state. Save the result to the $pit variable.  1. Run the Start-VESQLPluginDatabaseRestore cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Set the $restorepoint variable as the RestorePoint parameter value. * Set the StandBy property as the RecoveryState parameter value. * Specify the StandbyFilePath parameter value. * Provide the QuickRecovery parameter. * Provide the UseSQLAuthentication parameter. * Set the $creds variable as the SqlCredentials parameter value. * Set the $oscreds variable as the GuestCredentials parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VESQLPluginRestoreSession](get-vesqlpluginrestoresession.md)
* [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md)
* [Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

* [Get-VESQLPluginDatabaseFile](get-vesqlplugindatabasefile.md)
* [Get-VESQLPluginLogInterval](get-vesqlpluginloginterval.md)

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
