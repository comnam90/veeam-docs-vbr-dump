---
title: "restore-vesqlirdatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-vesqlirdatabase.html"
last_updated: "4/8/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Performs instant recovery of a backed-up Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VESQLIRDatabase [-Database] <VESQLDatabase> [-DatabaseName <String>] [-ServerName <String>] [-InstanceName <String>] [-Port <Int32>] [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-ToPointInTimeUtc <DateTime>] [-TargetFolder <String>] [-File <VESQLDatabaseFile[]>] [-TargetPath <String[]>] [-Force] -SwitchOverOptions <VESQLIRSwitchOverOptions> [<CommonParameters>] |

Detailed Description

This cmdlet performs instant restore of a backed-up Microsoft SQL Server database. You can restore a database to the original location or to another location. For details, see the [Instant Recovery](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_instant_recovery.html?ver=13) section of the Veeam Explorers User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database. The cmdlet will restore this database. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| SwitchOverOptions | Specifies a switchover option: automatic, manual or scheduled. | Accepts the [VESQLIRSwitchOverOptions](vesqlirswitchoveroptions.md) object. To get this object, run the [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md) cmdlet. | True | Named | True (ByValue) |
| DatabaseName | For restore to another location.  Specifies a name for the restored Microsoft SQL Server database on the target location. The database will be restored with the specified name. | String | False | Named | False |
| ServerName | For restore to another location.  Specifies DNS name or IP address of the target SQL Server server. The cmdlet will restore the database to the specified Microsoft SQL Server machine. | String | False | Named | False |
| InstanceName | For restore to another location.  Specifies the name of the target Microsoft SQL Server instance. The cmdlet will restore the Microsoft SQL Server database to the specified target instance. | String | False | Named | False |
| Port | Specifies a port number that will be used to connect to the target Microsoft SQL Server. | Int32 | False | Named | False |
| SqlCredentials | Specifies Microsoft SQL Server credentials for authenticating to Microsoft SQL Server on the target machine.  Note: If you do not specify Microsoft SQL Server credentials, the cmdlet will use the current account credentials. If these credentials do not work, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the target machine.  Note: If you omit this parameter the cmdlet will use credentials specified in the SQLCredentials parameter to connect to both Microsoft SQL Server and to the guest OS. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the target machine. If these credentials do not work, the cmdlet will use the credentials specified in the backup job.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS on the target server. * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ToPointInTimeUtc | Specifies a point in time in the UTC format within the restore interval of a Microsoft SQL Server database.  The cmdlet will restore the database to the state of the specified point in time. | DateTime | False | Named | False |
| TargetFolder | For restoring Microsoft SQL database files to specific location.  Specifies the destination folder. The cmdlet will restore all database files to that folder.  Note: This parameter is not available if you use the TargetPath parameter. | String | False | Named | False |
| File | Specifies an array of file names for Microsoft SQL Server databases. | Accepts the [VESQLDatabaseFile](vesqldatabasefile.md)[] object. To get this object, run the [Get-VESQLDatabaseFile](get-vesqldatabasefile.md) cmdlet. | False | Named | False |
| TargetPath | Specifies a target path array. The cmdlet will restore Microsoft SQL Server database files to the locations specified in the array.  Consider the following:   * For every Microsoft SQL Server database file you must assign a specific file path. * This parameter is not available if you use the TargetFolder parameter. | String[] | False | Named | False |
| Force | Defines that the cmdlet will overwrite an existing Microsoft SQL database with a Microsoft SQL database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLIRDatabase](vesqlirdatabase.md) object that contains information about the Microsoft SQL Server database published within the instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Instant Restore of Microsoft SQL Server Databases to Original Location with Scheduled Switchover

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of the SQLDatabase database to the original location using the scheduled switchover option. The cmdlet will perform the switchover at 13:00:00 on 2023-11-24.  |  | | --- | | $time = Get-Date -Date "2023-11-24 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VESQLIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc  $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  Restore-VESQLIRDatabase -Database $database -SwitchOverOptions $ScheduledSwitch |  Perform the following steps:   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the time when the switchover must be performed. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $TimeUtc variable. 3. Run the [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md) cmdlet. Provide the Scheduled parameter. Set the $TimeUTC variable as the SwitchingTimeUtc parameter value. Save the result to the $ScheduledSwitch variable. 4. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the Restore-VESQLIRDatabase cmdlet. Set the $database variable as the Database parameter value. Set the $ScheduledSwitch variable as the SwitchOverOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Instant Recovery of Microsoft SQL Server Databases to Specific Folder and Switching Over Manually

|  |  |
| --- | --- |
| This example shows how to restore the SQLDatabase01 database files to the latest state with the following settings:   * The cmdlet will restore the database to the localhost target server. * The cmdlet will restore the database to the SQLExpress instance. * The cmdlet will restore the database with the TableDatabase2023 name. * The cmdlet will restore the database to the C:\ folder. * To perform the switchover operation manually, you must run the [Switch-VESQLIRDatabase](switch-vesqlirdatabase.md) cmdlet.   |  | | --- | | $restore = Get-VBRApplicationRestorePoint -Id E4786E49-D943-4E27-80C2-C99A059CBB27  $session = Start-VESQLRestoreSession -RestorePoint $restore  $database = Get-VESQLDatabase -Session $session -Name "SQLDatabase01"  $ManualSwitch = New-VESQLIRSwitchOverOptions -Manual  $IRDatabase = Restore-VESQLIRDatabase -Database $database -SwitchOverOptions $ManualSwitch -ServerName "localhost" -InstanceName "SQLExpress" -DatabaseName "TableDatabase2023" -TargetFolder "C:\"  Switch-VESQLIRDatabase -Database $IRDatabase |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Specify the ID parameter value. Save the restore point to the $restore variable. 2. Run the [Start-VESQLRestoreSession](start-vesqlrestoresession.md) cmdlet. Specify the RestorePoint parameter value. Save the restore point to the $session variable. 3. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 4. Run the [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md) cmdlet. Provide the Manual parameter. Save the result in the $ManualSwitch variable. 5. Run the Restore-VESQLIRDatabase cmdlet with the $database variable. Specify the following options:  * Set the $database variable as the Database parameter value. * Set the $ManualSwitch variable as the SwitchOverOptions parameter value. * Specify the ServerName parameter value. * Specify the InstanceName parameter value. * Specify the DatabaseName parameter value. * Specify the TargetFolder parameter value.   Save the result to the $IRDatabase variable.   1. Run the [Switch-VESQLIRDatabase](switch-vesqlirdatabase.md) cmdlet. Set the $IRDatabase variable as the Database parameter value. |

Related Commands

* [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

* [Get-VESQLDatabaseFile](get-vesqldatabasefile.md)
* [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md)
* [Switch-VESQLIRDatabase](switch-vesqlirdatabase.md)

Page updated 4/8/2025

Page content applies to build 13.0.1.1071
