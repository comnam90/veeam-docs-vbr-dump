---
title: "Restore-VESQLDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-vesqldatabase.html"
last_updated: "9/19/2025"
product_version: "13.0.1.1071"
---

# Restore-VESQLDatabase


Short Description

Restores a backed-up Microsoft SQL database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VESQLDatabase [-Database] <VESQLDatabase> [-DatabaseName <String>] [-ServerName <String>] [-InstanceName <String>] [-Port <Int32>] [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-ToPointInTimeUtc <DateTime>] [-AvailabilityGroupName <String>] [-TargetFolder <String>] [-File <VESQLDatabaseFile[]>] [-TargetPath <String[]>] [-Force] [-RecoveryState <RestoreMode>] [-StandbyFilePath <String>] [<CommonParameters>] |

Detailed Description

This cmdlet restores a backed-up Microsoft SQL database. You can restore a Microsoft SQL database to the original location or to another location.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database that you want to restore. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| DatabaseName | For restore to another location.  Specifies a name for the restored Microsoft SQL Server database on the target location. The database will be restored with the specified name. | String | False | Named | False |
| ServerName | For restore to another location.  Specifies DNS name or IP address of a Microsoft SQL target server. The cmdlet will restore a Microsoft SQL database to the specified target server. | String | False | Named | False |
| InstanceName | For restore to another location.  Specifies the name of the target instance. The cmdlet will restore the Microsoft SQL Server database to the specified target instance. | String | False | Named | False |
| Port | Specifies a port number that will be used to connect to the target Microsoft SQL Server machine. | Int32 | False | Named | False |
| SqlCredentials | Specifies SQL credentials for authenticating to Microsoft SQL Server on the target machine.  Note: If you do not specify SQL credentials, the cmdlet will use the current account credentials. If these credentials do not work, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the target machine.  Note: If you omit this parameter, the cmdlet will use credentials specified in the SQLCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the target machine. If these credentials do not work, the cmdlet will use the credentials specified in the backup job.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ToPointInTimeUtc | Specifies a point in time in UTC within the restore interval of a Microsoft SQL database.  The cmdlet will restore the database to the state of the specified point in time. | DateTime | False | Named | False |
| AvailabilityGroupName | Specifies the name of the AlwaysOn availability group. The cmdlet will add a Microsoft SQL database to the specified group. | String | False | Named | False |
| TargetFolder | For restoring Microsoft SQL database files to one location.  Specifies the destination folder. The cmdlet will restore all database files to that folder.  Note: This parameter is not available if you use the TargetPath parameter. | String | False | Named | False |
| File | Specifies an array of file names for Microsoft SQL databases. | Accepts the [VESQLDatabaseFile](vesqldatabasefile.md)[] object. To get this object, run the [Get-VESQLDatabaseFile](get-vesqldatabasefile.md) cmdlet. | False | Named | False |
| TargetPath | Specifies a target path array. The cmdlet will restore Microsoft SQL database files to the locations specified in the target path array.  Consider the following:   * For every Microsoft SQL database file, you must assign a specific file path. * This parameter is not available if you use the TargetFolder parameter. | String[] | False | Named | False |
| Force | Defines that the cmdlet will overwrite an existing Microsoft SQL database with a Microsoft SQL database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| RecoveryState | Specifies the restore scenario.   * Recovery — use this option to leave a Microsoft SQL database in the ready to use state. With this option, you will not be able to restore additional transaction logs. * NoRecovery — use this option to leave a Microsoft SQL database in the non-operational state and to avoid rolling back uncommitted transactions. Use this option to restore transaction logs that are backed up with a third-party tool. * StandBy — use this option to leave the Microsoft SQL database in the read-only mode. It allows you to undo uncommitted transactions. The undo actions are saved in a standby file so that the recovery effects can be reversed.   Default: Recovery | RestoreMode | False | Named | False |
| StandbyFilePath | For the StandBy parameter.  Specifies a location for the standby file with the uncommitted transactions. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Microsoft SQL Server Database to Original Location

|  |  |
| --- | --- |
| This example shows how to restore a Microsoft SQL database to the original location. The restore operation will run with the following settings:   * The cmdlet will use the credentials of the user that is running the PowerShell session. * If these credentials do not work, the cmdlet will use the backup job credentials to connect to the guest OS and to Microsoft SQL Server.     |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "New SQL Database"  Restore-VESQLDatabase -Database $database |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the Restore-VESQLDatabase cmdlet. Set the $database variable as the Database parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Microsoft SQL Server Database to Specific Folder

|  |  |
| --- | --- |
| This example shows how to restore a Microsoft SQL database to a specific folder. SQL credentials are used for authenticating to the guest OS and Microsoft SQL Server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQL Database"  $creds = Get-Credential  Restore-VESQLDatabase -Database $database -ServerName "SQLServer" -TargetFolder "C:\SQL\Restore" -SQLCredentials $creds |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to the guest OS and Microsoft SQL Server. Save the result to the $creds variable. 3. Run the Restore-VESQLDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database value. * Specify the ServerName parameter value. * Specify the TargetFolder parameter value. * Set the $creds variable as the SQLCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Microsoft SQL Server Database Files to Specific Path Array

|  |  |
| --- | --- |
| This example shows how to restore Microsoft SQL Server database files to the specified array of paths. The restore session will run with the following options:   * The cmdlet will restore the File1.mdf file to the C:\SQLDBfile1\new\_file.mdf location. * The cmdlet will restore the File2.ldf file to the C:\SQLDBfile2\new\_file.ldf location. * The cmdlet will use SQL credentials for authenticating to Microsoft SQL Server. * The cmdlet will use the guest credentials for authenticating to the guest OS.   |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  $files = Get-VESQLDatabaseFile -Database $database  $files  Path                                               Type  ----                                               ----  C:\Program Files\File1.mdf                         Primary  C:\Program Files\File2.ldf                         Secondary  $path = @("C:\SQLDBfile1\new\_file.mdf","C:\SQLDBfile2\new\_file.ldf")  $sqlcreds = Get-Credential  $oscreds = Get-Credential  Restore-VESQLDatabase -Database $database -ServerName "SQLServer" -File $files -TargetPath $path -UseSqlAuthentication -SqlCredentials $sqlcreds -GuestCredentials $oscreds |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $database variable. 2. Run the [Get-VESQLDatabaseFile](get-vesqldatabasefile.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $files variable. 3. Use the $files variable to get details about the Microsoft SQL database files. 4. Declare the $path variable. Assign to this variable an array of paths for every database file that you want to restore. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to Microsoft SQL Server. Save the result to the $sqlcreds variable. 6. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter guest credentials that will be used for authenticating to the guest OS. Save the result to the $oscreds variable. 7. Run the Restore-VESQLDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the ServerName parameter value. * Set the $files variable as the File parameter value. * Set the $path variable as the TargetPath parameter value. * Provide the UseSqlAuthentication parameter. * Set the $sqlcreds variable as the SqlCredentials parameter value. * Set the $oscreds variable as the GuestCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Microsoft SQL Server Database to Point-in-Time State

|  |  |
| --- | --- |
| This example shows how to restore Microsoft SQL database files to a point-in-time state. The database files are restored to a specific folder on the target server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  $creds = Get-Credential  $pit = Get-Date -Date "2023-05-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  Restore-VESQLDatabase -Database $database -ServerName "SQLServer" -TargetFolder "C:\SQL\Restore" -SQLCredentials $creds -ToPointInTimeUtc $pitutc |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to guest OS and the Microsoft SQL Server on the target server. Save the result to the $creds variable. 3. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state. Save the result to the $pit variable. 4. Convert the $pit variable to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable.   Note that you can use the [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md) cmdlet to get the restore interval of the necessary database in UTC.   1. Run the Restore-VESQLDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the ServerName parameter value. * Specify the TargetFolder parameter value. * Set the $creds variable as the SQLCredentials parameter value. * Set the $pitutc variable as the ToPointInTimeUtc parameter value. |

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

* [Get-VESQLDatabaseFile](get-vesqldatabasefile.md)
* [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md)


