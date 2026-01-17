---
title: "Restore-VEORIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-veorirdatabase.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Performs instant recovery of a backed-up Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VEORIRDatabase [-Database] <VEORDatabase> [-Server <String>] [-OracleHome <String>] [-GlobalDatabaseName <String>] [-OracleSid <String>] [-WindowsCredentials <PSCredential>] [-OracleHomePassword <SecureString>] [-LinuxCredentials <VEORLinuxCredential>] [-SshPort <Int32>] [-ToPointInTimeUTC <DateTime>] [-File <VEORDatabaseFile[]>] [-TargetPath <String[]>] -SwitchOverOptions <VEORIRSchedule> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet performs instant recovery of a backed-up Oracle database. You can recover the database to the original location or to another location. For details, see the [Instant Recovery](https://helpcenter.veeam.com/docs/vbr/userguide/veor_ir.html?ver=13) section of the Veeam Explorers User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database that the cmdlet will restore. | Accepts the [VEORDatabase](veordatabase.md) object. To get this object, run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. | True | 0 | True (ByValue) |
| SwitchOverOptions | Specifies a switchover option: Auto, Manual or Scheduled. | Accepts the [VEORIRSchedule](veorirschedule.md) object. To get this object, run the [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md) cmdlet. | True | Named | True (ByValue) |
| Server | For restore to another server.  Specifies DNS name or IP address of the target server to which the database will be restored.  Note: Do not provide this parameter if you want to restore to the original server. | String | False | Named | False |
| OracleHome | For restore to another location.  Specifies the target Oracle home path. The cmdlet will restore an Oracle database to the location specified in the Oracle home path.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| GlobalDatabaseName | For restore to another location.  Specifies the global database name. The cmdlet will restore an Oracle database with the specified name.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| OracleSid | For restore to another location.  Specifies a new SID for an Oracle database. The cmdlet will restore the database with the specified SID.  Note: Do not provide this parameter if you want to restore to the original location. | String | False | Named | False |
| WindowsCredentials | For restore to a Windows machine.  Specifies Windows credentials that the cmdlet will use to connect to a Windows machine. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| OracleHomePassword | For restoring Oracle Database 12c or later on Windows server.  Specifies Oracle home credentials that the cmdlet will use for starting Oracle Services on the guest OS.  Note: This parameter is required in case you use the following types of Oracle home User:   * Existing Windows user * New Windows user | SecureString | False | Named | False |
| LinuxCredentials | For restore to a Linux machine.  Specifies Linux credentials that the cmdlet will use to connect to a Linux machine. | Accepts the [VEORLinuxCredential](veorlinuxcredential.md) object. To get this object, run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. | False | Named | False |
| ToPointInTimeUtc | Specifies a point in time in the UTC format within the restore interval of an Oracle database.  The cmdlet will restore the database to the state of the specified point in time. | DateTime | False | Named | False |
| File | Specifies an array of Oracle database files. | Accepts the [VEORDatabaseFile](veordatabasefile.md)[] object. To get this object, run the [Get-VEORDatabaseFile](get-veordatabasefile.md) cmdlet. | False | Named | False |
| TargetPath | Specifies the target path array. The cmdlet will restore the Oracle database files to the locations specified in the array.  Note: You must assign a specific file path for each Oracle database file. | String[] | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing Oracle database with the database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| SshPort | For restore to a Linux machine.  Specifies the SSH port number that the cmdlet will use to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORIRDatabase](veorirdatabase.md) object that contains the Oracle database published within the instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Instant Recovery of Oracle Database to Original Location with Scheduled Switchover

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of the orcl database to the original location using the scheduled switchover option. The cmdlet will perform the switchover at 13:00:00 on 2023-11-24.  |  | | --- | | $time = Get-Date -Date "2023-11-24 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VEORIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc  $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  Restore-VEORIRDatabase -Database $database -SwitchOverOptions $ScheduledSwitch |  Perform the following steps:   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $TimeUtc variable. 3. Run the [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md) cmdlet. Provide the Scheduled parameter and specify the SwitchingTimeUtc parameter value. Save the result to the $ScheduledSwitch variable. 4. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the Restore-VEORIRDatabase cmdlet. Set the $database variable as the Database parameter value. Set the $ScheduledSwitch variable as the SwitchOverOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Instant Recovery of Oracle Database to Specific Server with Manual Switchover

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of the orcl database to its latest state with the following settings:   * The cmdlet will restore the database to the linorcl01 target server. * The cmdlet will restore an Oracle database with the orcl\_published.tech.local global database name. * The cmdlet will restore the database with the orclpub SID. * The cmdlet will restore an Oracle database to the /home/oracle/app/oracle/product/19.3.0/db\_home\_2 Oracle home path. * To perform the switchover operation manually, you must run the [Switch-VEORIRDatabase](switch-veorirdatabase.md) cmdlet.   |  | | --- | | $restore = Get-VBRApplicationRestorePoint -Id fa4de91d-a493-41a8-88f7-1e29b0ab838d  $session = Start-VEORRestoreSession -RestorePoint $restore  $db = Get-VEORDatabase -Session $session -Name "orcl"  $ManualSwitch = New-VEORIRSwitchOverOptions -Manual  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxCredentials = New-VEORLinuxCredential -Account "oracle" -Password $securepassword -ElevateAccountToRoot  $IRDatabase = Restore-VEORIRDatabase -Database $db -SwitchOverOptions $ManualSwitch -Server "linorcl01" -OracleSid "orclpub" -GlobalDatabaseName "orcl\_published.tech.local" -LinuxCredentials $linuxCredentials -OracleHome "/home/oracle/app/oracle/product/19.3.0/db\_home\_2" -Force  Switch-VEORIRDatabase -Database $IRDatabase |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Specify the Id parameter value. Save the result to the $restore variable. 2. Run the [Start-VEORRestoreSession](start-veorrestoresession.md) cmdlet. Set the $restore variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter. Save the result to the $db variable. 4. Run the [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md) cmdlet. Provide the Manual parameter. Save the result in the $ManualSwitch variable. 5. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 6. Run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Provide the ElevateAccountToRoot parameter. Save the result to the $linuxCredentials variable. 7. Run the Restore-VEORIRDatabase cmdlet. Specify the following settings:  * Set the $db variable as the Database parameter value. * Set the $ManualSwitch variable as the SwitchOverOptions parameter value. * Specify the Server parameter value. * Specify the OracleSid parameter value. * Specify the GlobalDatabaseName parameter value. * Set the $linuxCredentials variable as the LinuxCredentials parameter value. * Specify the OracleHome parameter value. * Provide the Force parameter.   Save the result to the $IRDatabase variable.   1. Run the Switch-VEORIRDatabase cmdlet. Set the $IRDatabase variable as the Database parameter value. |

Related Commands

* [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md)
* [Get-VEORDatabase](get-veordatabase.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [New-VEORLinuxCredential](new-veorlinuxcredential.md)
* [ConvertTo-SecureString](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.5)

* [Switch-VEORIRDatabase](switch-veorirdatabase.md)

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
