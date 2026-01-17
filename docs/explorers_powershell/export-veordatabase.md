---
title: "Export-VEORDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-veordatabase.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Export-VEORDatabase


Short Description

Exports a backed-up Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VEORDatabase [-Database] <VEORDatabase> [-Path] <String> [-ToDateTime <DateTime>] [-Server <String>] [-WindowsCredentials <PSCredential>] [-LinuxCredentials <VEORLinuxCredential>] [-SshPort <Int32>] [-Force] [-EnableRmanBackup] [-OracleHome <String>] [-RmanBackupFormat <String>] [-RmanBackupTagName <String>] [-RmanBackupEnableCompression] [-ChannelsNumber <Int32>] [-OracleHomePassword <SecureString>] [<CommonParameters>] |

Detailed Description

This cmdlet exports a backed-up Oracle database to the machine where the PowerShell session is running. You can use the following export options:

* Export the raw database files of the Oracle database. If archived redo logs are available for the selected restore point, they will be exported in the .arc format.
* Export an Oracle database as an RMAN backup. To enable this option, use the EnableRmanBackup parameter.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database. The cmdlet will export this database. | Accepts the [VEORDatabase](veordatabase.md) object. To get this object, run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies the target path. The cmdlet will export a database to the location specified in this path. | String | True | 1 | False |
| LinuxCredentials | Specifies Linux credentials that the cmdlet will use to connect to the Linux staging server. | Accepts the [VEORLinuxCredential](veorlinuxcredential.md) object. To get this object, run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. | False | Named | False |
| ToDateTime | Specifies a point in time within the restore interval of an Oracle database.  The cmdlet will export the database to the state of the specified point in time.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | Named | False |
| Server | Specifies DNS name or IP address of the staging Oracle server.  Note: A staging server is necessary when exporting an Oracle database as an RMAN backup and when exporting database files from a backup of a Linux machine with Oracle. | String | False | Named | False |
| SshPort | Specifies the SSH port number. The cmdlet will use that port to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |
| WindowsCredentials | Specifies Windows credentials that the cmdlet will use to connect to the Windows staging server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing Oracle database files with the database files from the backup.  If you provide this parameter, the cmdlet will show no prompt before executing the command. Otherwise, the cmdlet will keep the existing version of Oracle database files. | SwitchParameter | False | Named | False |
| OracleHome | For export as RMAN backup and export of database files from backups of Linux machines.  Specifies the Oracle home path on the staging server that the cmdlet will use. | String | False | Named | False |
| OracleHomePassword | For export as RMAN backup for Windows machines with Oracle. For Oracle Database 12c or later.  Specifies Oracle home credentials that the cmdlet will use to start Oracle Services on the staging server.  Note that this parameter is required for the following types of Oracle Home user:   * Existing Windows user * New Windows user | SecureString | False | Named | False |
| EnableRmanBackup | Defines that the cmdlet will export Oracle databases using Oracle RMAN.  If you do not specify this parameter, the cmdlet will not apply Oracle RMAN to export Oracle databases. | SwitchParameter | False | Named | False |
| RmanBackupFormat | Specifies the FORMAT parameter of backed-up database files. The cmdlet will export Oracle databases using the specified FORMAT parameter. | String | False | Named | False |
| RmanBackupTagName | Specifies tags of backed-up database files. The cmdlet will export Oracle databases using the specified tags. | String | False | Named | False |
| RmanBackupEnableCompression | Defines that the cmdlet will back up Oracle databases with compression.  If you do not specify this parameter, the cmdlet will export Oracle databases without compression. | SwitchParameter | False | Named | False |
| ChannelsNumber | Specifies a number of channels that will be used to export Oracle databases.  Default: 4  Permitted value: 1-255. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. [For Windows Machines] Exporting Oracle Database as RMAN Backup

|  |  |
| --- | --- |
| This example shows how to export an Oracle database as an RMAN backup, from a backup of a Windows machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  $windowscreds = Get-Credential  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  Export-VEORDatabase -Database $database -Path "C:\Users\Administrator\Desktop\orcl" -EnableRmanBackup -Server "Staging\_Server" -OracleHome "C:\oracle" -OracleHomePassword $securepassword -WindowsCredentials $windowscreds |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to specify the Windows credentials for the staging server. Save the result to the $windowscreds variable. 3. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to specify the Oracle Home password for the staging server. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 4. Run the Export-VEORDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. * Provide the EnableRmanBackup parameter. * Specify the Server parameter to select a Windows machine that will serve as a staging server. * Specify the OracleHome parameter value. * Set the $securepassword variable as the OracleHomePassword parameter value. * Set the $windowscreds variable as the WindowsCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. [For Windows Machines] Exporting Oracle Database Files from Backup

|  |  |
| --- | --- |
| This example shows how to export database files from a backup of a Windows machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  Export-VEORDatabase -Database $database -Path "C:\Users\Administrator\Desktop\orcl" |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the Export-VEORDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. [For Linux Machines] Exporting Oracle Database Files from Backup

|  |  |
| --- | --- |
| This example shows how to export database files from a backup of a Linux machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEORLinuxCredential -Account "root" -Password $securepassword  Export-VEORDatabase -Database $database -Path "C:\Users\Administrator\Desktop\orcl" -Server "Staging\_Server" -LinuxCredentials $linuxcreds |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.  1. Get Linux credentials:  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value.  1. Run the Export-VEORDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Specify the Path parameter value. * Specify the Server parameter to select a Linux machine that will serve as a staging server. * Set the $linuxcreds variable as the LinuxCredentials parameter value. |

Related Commands

* [Get-VEORRestoreSession](get-veorrestoresession.md)
* [Get-VEORDatabase](get-veordatabase.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [New-VEORLinuxCredential](new-veorlinuxcredential.md)


