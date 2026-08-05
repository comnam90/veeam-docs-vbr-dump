---
title: "Start-VEPSQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqldatabaseexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VEPSQLDatabaseExport


Short Description

Starts an export process for a backed-up or a published PostgreSQL database.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export a PostgreSQL database from a backed-up Windows machine to the Linux machine where the PowerShell session is running.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-WindowsStagingCredentials] <PSCredential> [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [-Force] [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Windows machine to the Windows machine where the PowerShell session is running.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-WindowsStagingCredentials] <PSCredential> [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-Force] [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Windows machine to another Linux machine.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-WindowsStagingCredentials] <PSCredential> [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [-LinuxTargetHost] <String> [-LinuxTargetSshPort <Int32>] [-Force]  [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Windows machine to another Windows machine.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-WindowsStagingCredentials] <PSCredential> [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-WindowsTargetHost] <String> [-Force]  [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Linux machine to the Linux machine where the PowerShell session is running.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-LinuxStagingCredentials] <VEPSQLLinuxCredential> [-StagingSshPort <Int32>] [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [-Force] [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Linux machine to the Windows machine where the PowerShell session is running.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-LinuxStagingCredentials] <VEPSQLLinuxCredential> [-StagingSshPort <Int32>] [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-Force] [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Linux machine to another Linux machine.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-LinuxStagingCredentials] <VEPSQLLinuxCredential> [-StagingSshPort <Int32>] [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [-LinuxTargetHost] <String> [-LinuxTargetSshPort <Int32>] [-Force] [<CommonParameters>] |

* Export a PostgreSQL database from a backed-up Linux machine to another Windows machine.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-Database] <VEPSQLDatabase> [-StagingServerName] <String> [-LinuxStagingCredentials] <VEPSQLLinuxCredential> [-StagingSshPort <Int32>] [-ToPointInTimeUTC <DateTime>] -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-WindowsTargetHost] <String> [-Force]  [<CommonParameters>] |

* Export a published PostgreSQL database to the Linux machine where the PowerShell session is running.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-PublishedDatabase] <VEPSQLPublishedDatabase> -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [-Force]  [<CommonParameters>] |

* Export a published PostgreSQL database to the Windows machine where the PowerShell session is running.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-PublishedDatabase] <VEPSQLPublishedDatabase> -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-Force] [<CommonParameters>] |

* Export a published PostgreSQL database to another Linux machine.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-PublishedDatabase] <VEPSQLPublishedDatabase> -Path <String> [-DisableCompression] [-LinuxTargetCredentials] <VEPSQLLinuxCredential> [-LinuxTargetHost] <String> [-LinuxTargetSshPort <Int32>] [-Force] [<CommonParameters>] |

* Export a published PostgreSQL database to another Windows machine.

|  |
| --- |
| Start-VEPSQLDatabaseExport [-PublishedDatabase] <VEPSQLPublishedDatabase> -Path <String> [-DisableCompression] [-WindowsTargetCredentials] <PSCredential> [-WindowsTargetHost] <String> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet starts an export process for a backed-up or a published PostgreSQL database. You can export the necessary PostgreSQL database to the local host where the PowerShell session is running or any Windows or Linux server.

After you run the Start-VEPSQLDatabaseExport cmdlet, you can use the following cmdlets:

* [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md)
* [Restart-VEPSQLDatabaseExport](restart-vepsqldatabaseexport.md)
* [Stop-VEPSQLDatabaseExport](stop-vepsqldatabaseexport.md)

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Database | Specifies a backed-up PostgreSQL database. The cmdlet will export this database. | Accepts the [VEPSQLDatabase](vepsqldatabase.md) object. To get this object, run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. | True | 0 | True (ByValue) |
| PublishedDatabase | Specifies a published PostgreSQL database. The cmdlet will export this database. | Accepts the [VEPSQLPublishedDatabase](vepsqlpublisheddatabase.md) object. To get this object, run the [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md) cmdlet. | True | 0 | True (ByValue) |
| LinuxStagingCredentials | Specifies the credentials for the Linux-based staging server. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) object. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | True | 1 | True (ByValue) |
| WindowsStagingCredentials | Specifies the credentials for the Windows-based staging server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | 1 | True (ByValue) |
| StagingServerName | Specifies DNS name or IP address of the staging server. | String | True | 2 | True (ByValue) |
| LinuxTargetCredentials | Specifies the credentials for the target Linux machine. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) object. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | True | 3 | True (ByValue) |
| WindowsTargetCredentials | Specifies the credentials for the target Windows machine. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | 3 | True (ByValue) |
| LinuxTargetHost | Specifies the name of the target Linux server. | String | True | 4 | True (ByValue) |
| WindowsTargetHost | Specifies the name of the target Windows server. | String | True | 4 | True (ByValue) |
| DisableCompression | Defines that the cmdlet will not compress the output file. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing PostgreSQL database files with the database files from the backup.  If you provide this parameter, the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| LinuxTargetSshPort | Specifies the SSH port number. The cmdlet will use this port to connect to the target Linux machine. | Int32 | False | Named | False |
| Path | Specifies the target path. The cmdlet will export a database to the location specified in this path.  Note: This parameter works for both Windows and Linux target machines. | String | True | Named | False |
| StagingSshPort | Specifies the SSH port number. The cmdlet will use this port to connect to the staging Linux machine. | Int32 | False | Named | False |
| ToPointInTimeUTC | Specifies the point in time in the UTC format within a restore interval of the PostgreSQL database.  The cmdlet will export the specified database to the state of the specified point in time. If you do not use this parameter, the cmdlet will export the database to the point in time when the restore point for which you started the restore session was created. | DateTime | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabaseExport](vepsqldatabaseexport.md) object that contains information about the specified export session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Latest State of Published Database to Windows Host

|  |  |
| --- | --- |
| This example shows how to export a published database to a Windows server, using its latest state on the backup file.  |  | | --- | | $publisheddatabase = Get-VEPSQLPublishedDatabase -Name "database\_1"  $wincreds = Get-Credential  $export = Start-VEPSQLDatabaseExport -PublishedDatabase $publisheddatabase -WindowsTargetCredentials $wincreds -Path "C:\Users\Administrator\Desktop\rhel01\_5433\_postgres.dump" -DisableCompression |  Perform the following steps:   1. Run the [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md) cmdlet. Specify the Name parameter value. Save the result to the $publisheddatabase variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the local host on which the PowerShell session is running. Save the result to the $wincreds variable. 3. Run the Start-VEPSQLDatabaseExport cmdlet. Specify the following settings:  * Set the $publisheddatabase variable as the PublishedDatabase parameter value. * Set the $wincreds variable as the WindowsTargetCredentials parameter value. * Specify the Path parameter value.  * Provide the DisableCompression parameter so that the cmdlet does not reduce size of the output.   Save the result to the $export variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Point-in-Time State of Backed-Up Database to Another Linux Server

|  |  |
| --- | --- |
| This example shows how to export a backed-up PostgreSQL database to a Linux server, using a point-in-time state on the backup file.  |  | | --- | | $session = Get-VEPSQLRestoreSession  $databases = Get-VEPSQLDatabase -Session $session[0]  $time = Get-Date -Date "2026-11-24 13:00:00"  $timeutc = $time.ToUniversalTime()  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEPSQLLinuxCredential -Account "root" -Password $securepassword  $targetsecurepassword = Read-Host -Prompt "Enter password" -AsSecureString  $targetlinuxcreds = New-VEPSQLLinuxCredential -Account "root" -Password $targetsecurepassword  $export = Start-VEPSQLDatabaseExport -Database $databases[0] -LinuxStagingCredentials $linuxcreds -StagingServerName "rhel01" -LinuxTargetCredentials $targetlinuxcreds -LinuxTargetHost "rhel02" -LinuxTargetSshPort 22 -ToPointInTimeUTC $timeutc -Path "/var/lib/postgresql/rhel01\_5433\_postgres.dump" |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $databases variable. 2. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the point in time to which the database must be exported. Save the result to the $time variable. 3. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $timeutc variable. 4. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the staging server. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 5. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $linuxcreds variable. 6. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux server. Provide the AsSecureString parameter. Save the result to the $targetsecurepassword variable. 7. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $targetsecurepassword variable as the Password parameter value. Save the result to the $targetlinuxcreds variable. 8. Run the Start-VEPSQLDatabaseExport cmdlet. Specify the following settings:  * Set the $databases variable as the Database parameter value and select the necessary database. * Set the $linuxcreds variable as the LinuxStagingCredentials parameter value. * Specify the StagingServerName parameter value. * Set the $targetlinuxcreds variable as the LinuxTargetCredentials parameter value. * Specify the LinuxTargetHost parameter value. * Specify the LinuxTargetSshPort parameter value. * Set the $timeutc variable as the ToPointInTimeUTC parameter value. * Specify the Path parameter value.   Save the result to the $export variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Exporting Latest State of Backed-Up Database from Windows Machine to Another Windows Server

|  |  |
| --- | --- |
| This example shows how to export a backed-up PostgreSQL database from a Windows machine to another Windows server, using its latest state on the backup file.  |  | | --- | | $session = Get-VEPSQLRestoreSession  $databases = Get-VEPSQLDatabase -Session $session[0]  $stagingcreds = Get-Credential  $targetcreds = Get-Credential  $export = Start-VEPSQLDatabaseExport -Database $databases[0] -StagingServerName "winserver01" -WindowsStagingCredentials $stagingcreds -WindowsTargetCredentials $targetcreds -WindowsTargetHost "winserver02" -Path "C:\PostgreSQL\Exports\database\_1.dump" |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In this example, it is the first restore session in the array.   1. Run the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $databases variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials for the Windows-based staging server. Save the result to the $stagingcreds variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials for the target Windows server. Save the result to the $targetcreds variable. 4. Run the Start-VEPSQLDatabaseExport cmdlet. Specify the following settings:  * Set the $databases variable as the Database parameter value and select the necessary database. * Specify the StagingServerName parameter value. * Set the $stagingcreds variable as the WindowsStagingCredentials parameter value. * Set the $targetcreds variable as the WindowsTargetCredentials parameter value. * Specify the WindowsTargetHost parameter value. * Specify the Path parameter value.   Save the result to the $export variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Exporting Published Database to Another Linux Server

|  |  |
| --- | --- |
| This example shows how to export a published PostgreSQL database to another Linux server.  |  | | --- | | $publisheddatabase = Get-VEPSQLPublishedDatabase -Name "database\_1"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEPSQLLinuxCredential -Account "postgres" -Password $securepassword  $export = Start-VEPSQLDatabaseExport -PublishedDatabase $publisheddatabase -LinuxTargetCredentials $linuxcreds -LinuxTargetHost "rhel03" -LinuxTargetSshPort 22 -Path "/var/lib/postgresql/database\_1.dump" |  Perform the following steps:   1. Run the [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md) cmdlet. Specify the Name parameter value. Save the result to the $publisheddatabase variable. 2. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux server. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 3. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $linuxcreds variable. 4. Run the Start-VEPSQLDatabaseExport cmdlet. Specify the following settings:  * Set the $publisheddatabase variable as the PublishedDatabase parameter value. * Set the $linuxcreds variable as the LinuxTargetCredentials parameter value. * Specify the LinuxTargetHost parameter value. * Specify the LinuxTargetSshPort parameter value. * Specify the Path parameter value.   Save the result to the $export variable to use it with other cmdlets. |

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Get-VEPSQLDatabase](get-vepsqldatabase.md)
* [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 2026-04-10

