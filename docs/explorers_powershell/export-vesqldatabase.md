---
title: "Export-VESQLDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-vesqldatabase.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Export-VESQLDatabase


Short Description

Exports a backed-up Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VESQLDatabase [-Database] <VESQLDatabase> -Path <String> [-ToPointInTime <DateTime>] [-ServerName <String>] [-InstanceName <String>] [-Port <Int32>] [-UseSQLAuthentication] [-SqlCredentials <PSCredential>] [-GuestCredentials <PSCredential>] [-ToBackupFile] [-EnableCompression] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet allows you to export a Microsoft SQL Server database to the machine where the PowerShell session is running. You can use the following export options:

* Export a Microsoft SQL Server database in the .mdf format. If transaction log backups are available for the selected restore point, they will be exported as well, in the .ldf format.
* Export a Microsoft SQL Server database as a backup (.bak) file. To enable this option, use the ToBackupFile parameter.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database that you want to export. | Accepts the [VESQLDatabase](vesqldatabase.md) object. To get this object, run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies the export path on the machine where the PowerShell session is running.  To export your database as a backup (.bak) file, specify the ToBackupFile parameter.  Note: To overwrite an existing file in the export destination, use the Force parameter. | String | True | Named | False |
| ToPointInTime | Specifies a point in time within the restore interval of a Microsoft SQL Server database.  The cmdlet will export the database to the state of the specified point in time.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | Named | False |
| ServerName | Specifies DNS name or IP address of the staging server. | String | False | Named | False |
| InstanceName | Specifies the Microsoft SQL Server instance on the staging server to which the cmdlet will connect. | String | False | Named | False |
| Port | Specifies a port number that will be used to connect to the staging server. | Int32 | False | Named | False |
| SqlCredentials | Specifies SQL credentials for authenticating to Microsoft SQL Server on the staging server.  Note: If you do not specify SQL credentials, the cmdlet will use the current account credentials. If these credentials do not work, the cmdlet will use the credentials specified in the backup job. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSQLAuthentication | Defines that the cmdlet will use SQL authentication to connect to Microsoft SQL Server on the staging server.  Note: If you omit this parameter, the cmdlet will use the credentials specified in the SQLCredentials parameter to connect to both Microsoft SQL Server and to the guest OS on the staging server. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies credentials for authenticating to the staging server.  Consider the following:   * If you omit this parameter, the cmdlet will use the credentials specified in the SqlCredentials parameter to connect to both Microsoft SQL Server and to the guest OS on the staging server. * If you do not specify SQL credentials, the cmdlet will use the current account credentials. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ToBackupFile | Defines that the cmdlet will export the specified Microsoft SQL Server database as a backup (.bak) file. | SwitchParameter | False | Named | False |
| EnableCompression | For the ToBackupFile parameter.  Defines that the cmdlet will compress the new backup (.bak) file.  Note: This option is available only if your version of Microsoft SQL Server supports the compression option. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will overwrite the following files:   * The .bak file that you specify in the Path parameter. * Microsoft SQL Server database .mdf and .ldf files in case they are located in the target folder.   Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Microsoft SQL Server Database Files to Latest State

|  |  |
| --- | --- |
| This example shows how to export Microsoft SQL Server database files to the latest state on the backup file. This example uses the backup server as a staging server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  Export-VESQLDatabase -Database $database -Path "C:\SQLExport" |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the Export-VESQLDatabase cmdlet. Set the $database variable as the Database parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Microsoft SQL Server Database to Latest State as .bak File

|  |  |
| --- | --- |
| This example shows how to export a Microsoft SQL Server database to the latest state on the backup file. The database is exported as a .bak file. This example uses SQL credentials to authenticate to the guest OS and Microsoft SQL Server on the staging server.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQLDatabase"  $sqlcreds = Get-Credential  Export-VESQLDatabase -Database $database -Path "C:\export\Export.bak" -ServerName "StagingServer" -SQLCredentials $sqlcreds -ToBackupFile |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the SQL credentials that will be used for authenticating to the guest OS and Microsoft SQL Server on the staging server. Save the result to the $sqlcreds variable. 3. Run the Export-VESQLDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value.  * Specify the ServerName parameter value to select the staging server. * Set the $sqlcreds variable as the SQLCredentials parameter value. * Provide the ToBackupFile parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Exporting Microsoft SQL Server Database Files to Specific Point in Time

|  |  |
| --- | --- |
| This example shows how to export Microsoft SQL Server database files to a specific point-in-time state.  |  | | --- | | $session = Get-VESQLRestoreSession  $database = Get-VESQLDatabase -Session $session[0] -Name "SQL database"  $pit = Get-Date -Date "2023-05-25 15:00:00"  $pitutc = $pit.ToUniversalTime()  $windowscreds = Get-Credential  $sqlcreds = Get-Credential  Export-VESQLDatabase -Database $database -Path "C:\Export" -ServerName "StagingServer" -UseSQLAuthentication -GuestCredentials $windowscreds -SQLCredentials $sqlcreds -ToPointInTime $pitutc |  Perform the following steps:   1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VESQLDatabase](get-vesqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the point-in-time state. Save the result to the $pit variable. 3. Convert the $pit variable to the UTC format using the ToUniversalTime() method. Save the result to the $pitutc variable.   Note that you can use the [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md) cmdlet to get the restore interval of the necessary database in UTC.   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter guest credentials that will be used for authenticating to the guest OS on the staging server. Save the result to the $windowscreds variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter SQL credentials that will be used for authenticating to Microsoft SQL Server on the staging server. Save the result to the $sqlcreds variable. 3. Run the Export-VESQLDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value.  * Specify the ServerName parameter value to select the staging server. * Provide the UseSQLAuthentication parameter. * Set the $windowscreds variable as the GuestCredentials. * Set the $sqlcreds variable as the SQLCredentials parameter value. * Set the $pitutc variable as the ToPointInTime parameter value. |

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLDatabase](get-vesqldatabase.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-VESQLDatabaseRestoreInterval](get-vesqldatabaserestoreinterval.md)


