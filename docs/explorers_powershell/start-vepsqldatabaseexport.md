---
title: "start-vepsqldatabaseexport"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqldatabaseexport.html"
last_updated: "7/9/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Starts an export process for a backed-up or a published PostgreSQL database.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export a backed-up PostgreSQL database to a target server with Linux.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-LinuxStagingCredentials] <VEPSQLLinuxCredential> [-StagingServerName] <String> [-StagingSshPort <Int32>] [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [[-LinuxTargetHost] <String>] [-LinuxTargetSshPort <Int32>] [-Force] [<CommonParameters>] |

* [For Windows-based backup servers] Export a backed-up PostgreSQL database to the local host on which the Veeam Backup & Replication console is installed.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-LinuxStagingCredentials] <VEPSQLLinuxCredential> [-StagingServerName] <String> [-StagingSshPort <Int32>] [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-Force] [<CommonParameters>] |

* Export a published PostgreSQL database to a target server with Linux.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-PublishedDatabase] <VEPSQLPublishedDatabase> -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [[-LinuxTargetHost] <String>] [-LinuxTargetSshPort <Int32>] [-Force] [<CommonParameters>] |

* [For Windows-based backup servers] Export a published PostgreSQL database to to the local host on which the Veeam Backup & Replication console is installed.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-PublishedDatabase] <VEPSQLPublishedDatabase> -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet starts an export process for a backed-up or a published PostgreSQL database. You can export the necessary PostgreSQL database to the local host on which the Veeam Backup & Replication console is installed (available for Windows-based backup servers only) or any Linux server.

After you run the Start-VEPSQLDatabaseExport cmdlet, you can use the following cmdlets:

* [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md)
* [Restart-VEPSQLDatabaseExport](restart-vepsqldatabaseexport.md)
* [Stop-VEPSQLDatabaseExport](stop-vepsqldatabaseexport.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a backed-up PostgreSQL database. The cmdlet will export this database. | Accepts the [VEPSQLDatabase](vepsqldatabase.md) type. To get this object, run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| PublishedDatabase | Specifies a published PostgreSQL database. The cmdlet will export this database. | Accepts the [VEPSQLPublishedDatabase](vepsqlpublisheddatabase.md) type. To get this object, run the [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md) cmdlet. | True | 0 | True (ByValue) |
| LinuxStagingCredentials | Specifies the credentials for the staging server. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) type. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | True | 1 | True (ByValue) |
| StagingServerName | Specifies DNS name or IP address of the staging server. | String | True | 2 | True (ByValue) |
| LinuxTargetCredentials | Specifies the credentials for the target Linux machine. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) type. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | True | 3 | True (ByValue) |
| WindowsTargetCredentials | For Windows-based backup servers.  Specifies the credentials for the local host on which the Veeam Backup & Replication console is installed. | Accepts the PSCredential type. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | 3 | True (ByValue) |
| LinuxTargetHost | Specifies the name of the target Linux server. | String | True | 4 | True (ByValue) |
| DisableCompression | Defines that the cmdlet will not compress the output file. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing PostgreSQL database files with the database files from the backup.  If you provide this parameter, the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| LinuxTargetSshPort | Specifies an SSH port number that the cmdlet will use to access the target Linux machine. | Int32 | False | Named | False |
| Path | Specifies the target path. The cmdlet will export a database to the location specified in this path.  Note: This parameter works for both Windows and Linux target machines. | String | True | Named | False |
| StagingSshPort | Specifies an SSH port number that the cmdlet will use to connect to the staging server | Int32 | False | Named | False |
| ToPointInTimeUTC | Specifies the point in time in the UTC format within a restore interval of the PostgreSQL database.  The cmdlet will export the specified database to the state of the specified point in time. If you do not use this parameter, the cmdlet will restore the instance to the point in time when the restore point for which you started the restore session was created. | DateTime | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabaseExport](vepsqldatabaseexport.md) object that contains information about the specified export session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Latest State of Published Database to Local Host [For Window-Based Backup Servers Only]

|  |  |
| --- | --- |
| This example shows how to export a backed-up database to the local host on which the Veeam Backup & Replication console is installed, using its latest state on the backup file. Note that this operation is only available if you use a Windows-based backup server.  |  | | --- | | $publisheddatabase = Get-VEPSQLPublishedDatabase -Name "database\_1"  $wincreds = Get-Credential  $export = Start-VEPSQLDatabaseExport -PublishedDatabase $publisheddatabase -WindowsTargetCredentials $wincreds -Path "C:\Users\Administrator\Desktop\rhel01\_5433\_postgres.dump" -DisableCompression |  Perform the following steps:   1. Run the [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md) cmdlet. Specify the Name parameter value. Save the result to the $publisheddatabase variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the local host on which the Veeam Backup & Replication console is installed. Save the result to the $wincreds variable. 3. Run the Start-VEPSQLDatabaseExport cmdlet. Specify the following settings:  * Set the $publisheddatabase variable as the Database parameter value and select the necessary database. * Set the $wincreds variable as the WindowsTargetCredentials parameter value. * Specify the Path parameter value.  * Provide the DisableCompression parameter so that the cmdlet does not reduce size of the output.   Save the result to the $export variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Point-in-Time State of Backed-Up Database to Linux Server

|  |  |
| --- | --- |
| This example shows how to export a backed-up PostgreSQL database to a Linux server, using a point-in-time state on the backup file.  |  | | --- | | $session = Get-VEPSQLRestoreSession  $databases = Get-VEPSQLDatabase -Session $session[0]  $time = Get-Date -Date "2023-11-24 13:00:00"  $timeutc = $time.ToUniversalTime()  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEPSQLLinuxCredential -Account "root" -Password $securepassword  $targetsecurepassword = Read-Host -Prompt "Enter password" -AsSecureString  $targetlinuxcreds = New-VEPSQLLinuxCredential -Account "root" -Password $targetsecurepassword  $export = Start-VEPSQLDatabaseExport -Database $databases[0] -LinuxStagingCredentials $linuxcreds -StagingServerName "rhel01" -LinuxTargetCredentials $targetlinuxcreds -LinuxTargetHost "rhel02" -LinuxTargetSshPort 22 -ToPointInTimeUTC $timeutc -Path "/var/lib/postgresql/rhel01\_5433\_postgres.dump" |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $databases variable. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when switchover must be performed. Save the result to the $time variable. 3. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $TimeUtc variable. 4. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the staging server. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 5. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $linuxcreds variable. 6. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux server. Provide the AsSecureString parameter. Save the result to the $targetsecurepassword variable. 7. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $targetsecurepassword variable as the Password parameter value. Save the result to the $targetlinuxcreds variable. 8. Run the Start-VEPSQLDatabaseExport cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value and select the necessary database. * Set the $linuxcreds variable as the LinuxStagingCredentials parameter value. * Specify the StagingServerName parameter value. * Set the $targetlinuxcreds variable as the LinuxTargetCredentials parameter value. * Specify the LinuxTargetHost parameter value. * Specify the LinuxTargetSshPort parameter value. * Set the $timeutc variable as the ToPointInTimeUTC parameter value. * Specify the Path parameter value.   Save the result to the $export variable to use it with other cmdlets. |

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Get-VEPSQLDatabase](get-vepsqldatabase.md)
* [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md)

Page updated 7/9/2025

Page content applies to build 13.0.1.1071
