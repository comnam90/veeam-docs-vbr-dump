---
title: "Start-VESQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqldatabaseexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VESQLDatabaseExport


Short Description

Exports a backed-up Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export a database using explicitly provided credentials.

|  |
| --- |
| Start-VESQLDatabaseExport [-Database] <VESQLDatabase> [-Path] <String> [-TargetHost <String>] -TargetGuestCredentials <PSCredential> [-ToPointInTimeUtc <DateTime>] [-ServerName <String>] [-InstanceName <String>] [-Port <Int32>] [-SqlCredentials <PSCredential>] [-UseSQLAuthentication] [-GuestCredentials <PSCredential>] [-ToBackupFile] [-EnableCompression] [-Force] [<CommonParameters>] |

* Export a database using a Group Managed Service Account (gMSA) for authentication.

|  |
| --- |
| Start-VESQLDatabaseExport [-Database] <VESQLDatabase> [-Path] <String> [-TargetHost <String>] [-TargetGuestCredentials <PSCredential>] [-ToPointInTimeUtc <DateTime>] [-ServerName <String>] [-InstanceName <String>] [-Port <Int32>] -GMSAAccount <String> [-ToBackupFile] [-EnableCompression] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet exports a Microsoft SQL Server database to a target Windows server. To specify the target Windows server, use the TargetHost parameter. You can use the following export options:

* Export a Microsoft SQL Server database in the .mdf format. If transaction log backups are available for the selected restore point, they will be exported as well, in the .ldf format.
* Export a Microsoft SQL Server database as a backup (.bak) file. To enable this option, use the ToBackupFile parameter.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Database | Specifies a Microsoft SQL Server database that you want to export. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies the export path on the target Windows server.  To export your database as a backup (.bak) file, specify the ToBackupFile parameter.  Note: To overwrite an existing file in the export destination, use the Force parameter. | String | True | 1 | False |
| ToPointInTimeUtc | Specifies a point in time within the restore interval of a Microsoft SQL Server database.  The cmdlet will export the database to the state of the specified point in time.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | Named | False |
| ServerName | Specifies DNS name or IP address of the staging server. | String | False | Named | False |
| InstanceName | Specifies the Microsoft SQL Server instance on the staging server to which the cmdlet will connect. | String | False | Named | False |
| Port | Specifies a port number that will be used to connect to the staging server. | Int32 | False | Named | False |
| SqlCredentials | Specifies SQL credentials for authenticating to Microsoft SQL Server on the staging server.  Note: If you do not specify SQL credentials, the cmdlet will use the current account credentials. If these credentials do not work, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the staging server.  Note: If you omit this parameter, the cmdlet will use the credentials specified in the SQLCredentials parameter to connect to both Microsoft SQL Server and to the guest OS on the staging server. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the staging server.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS on the staging server. * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ToBackupFile | Defines that the cmdlet will export the specified Microsoft SQL Server database as a backup (.bak) file. | SwitchParameter | False | Named | False |
| EnableCompression | For the ToBackupFile parameter.  Defines that the cmdlet will compress the new backup (.bak) file.  Note: This option is available only if your version of Microsoft SQL Server supports the compression option. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will overwrite the following files:   * The .bak file that you specify in the Path parameter. * Microsoft SQL Server database .mdf and .ldf files in case they are located in the target folder.   Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| GMSAAccount | Specifies the name of the Group Managed Service Account (gMSA). The cmdlet will use this account to authenticate to Microsoft SQL Server on the target machine. | String | True | Named | False |
| TargetHost | Specifies the DNS name or IP address of the target Windows server to which the cmdlet will export the database. | String | False | Named | False |
| TargetGuestCredentials | Specifies credentials to authenticate to the target Windows server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Microsoft SQL Server Database Files to Latest State

|  |  |
| --- | --- |
| This example shows how to export Microsoft SQL Server database files to the latest state on the backup file. This example uses the backup server as a staging server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  $targetcreds = Get-Credential  Start-VESQLDatabaseExport -Database $database -Path "C:\SQLExport" -TargetGuestCredentials $targetcreds |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $targetcreds variable. 3. Run the Start-VESQLDatabaseExport cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. * Set the $targetcreds variable as the TargetGuestCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Microsoft SQL Server Database to Latest State as .bak File

|  |  |
| --- | --- |
| This example shows how to export a Microsoft SQL Server database to the latest state on the backup file. The database is exported as a .bak file. This example uses SQL credentials to authenticate to Microsoft SQL Server on the staging server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  $sqlcreds = Get-Credential  $targetcreds = Get-Credential  Start-VESQLDatabaseExport -Database $database -Path "C:\export\Export.bak" -ServerName "StagingServer" -SqlCredentials $sqlcreds -TargetGuestCredentials $targetcreds -ToBackupFile |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the SQL credentials that will be used for authenticating to Microsoft SQL Server on the staging server. Save the result to the $sqlcreds variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $targetcreds variable. 4. Run the Start-VESQLDatabaseExport cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. * Specify the ServerName parameter value to select the staging server. * Set the $sqlcreds variable as the SqlCredentials parameter value. * Set the $targetcreds variable as the TargetGuestCredentials parameter value. * Provide the ToBackupFile parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Exporting Microsoft SQL Server Database Files to Specific Point in Time

|  |  |
| --- | --- |
| This example shows how to export Microsoft SQL Server database files to a specific point-in-time state.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQL database"  $pit = Get-Date -Date "2026-05-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  $windowscreds = Get-Credential  $sqlcreds = Get-Credential  $targetcreds = Get-Credential  Start-VESQLDatabaseExport -Database $database -Path "C:\Export" -ServerName "StagingServer" -UseSQLAuthentication -GuestCredentials $windowscreds -SqlCredentials $sqlcreds -TargetGuestCredentials $targetcreds -ToPointInTimeUtc $pitutc |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state. Save the result to the $pit variable. 3. Convert the $pit variable to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable.   Note that you can use the [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md) cmdlet to get the restore interval of the necessary database in UTC.   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter guest credentials that will be used for authenticating to the guest OS on the staging server. Save the result to the $windowscreds variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to Microsoft SQL Server on the staging server. Save the result to the $sqlcreds variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $targetcreds variable. 4. Run the Start-VESQLDatabaseExport cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. * Specify the ServerName parameter value to select the staging server. * Provide the UseSQLAuthentication parameter. * Set the $windowscreds variable as the GuestCredentials parameter value. * Set the $sqlcreds variable as the SqlCredentials parameter value. * Set the $targetcreds variable as the TargetGuestCredentials parameter value. * Set the $pitutc variable as the ToPointInTimeUtc parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Exporting Microsoft SQL Server Database to Another Windows Server

|  |  |
| --- | --- |
| This example shows how to export Microsoft SQL Server database files to another Windows server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  $targetcreds = Get-Credential  Start-VESQLDatabaseExport -Database $database -Path "C:\SQLExport" -TargetHost "TargetServer" -TargetGuestCredentials $targetcreds |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $targetcreds variable. 3. Run the Start-VESQLDatabaseExport cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. * Specify the TargetHost parameter value to select the target Windows server. * Set the $targetcreds variable as the TargetGuestCredentials parameter value. |

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md)

Page updated 2026-06-10

