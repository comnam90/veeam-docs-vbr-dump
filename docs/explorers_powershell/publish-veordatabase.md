---
title: "Publish-VEORDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/publish-veordatabase.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---

# Publish-VEORDatabase


Short Description

Publishes a backed-up Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Publish-VEORDatabase [-Database] <VEORDatabase> [-Server <String>] [-OracleHome <String>] [-GlobalDatabaseName <String>] [-OracleSid <String>] [-WindowsCredentials <PSCredential>] [-OracleHomePassword <SecureString>] [-LinuxCredentials <VEORLinuxCredential>] [-SshPort <Int32>] [-ToDateTime <DateTime>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet publishes a backed-up Oracle database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database that the cmdlet will publish. | Accepts the [VEORDatabase](veordatabase.md) object. To get this object, run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Server | For publishing to another server.  Specifies DNS name or IP address of the target Oracle server to which the database will be published.  Note: Do not provide this parameter if you want to publish to the original server. | String | False | Named | False |
| LinuxCredentials | For publishing to a Linux machine.  Specifies Linux credentials that the cmdlet will use to connect to a Linux machine. | Accepts the [VEORLinuxCredential](veorlinuxcredential.md) object. To get this object, run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. | False | Named | False |
| OracleHome | For publishing to another location.  Specifies the target Oracle home path. The cmdlet will publish an Oracle database to the location specified in the Oracle home path.  Note: Do not provide this parameter if you want to publish to the original location. | String | False | Named | False |
| GlobalDatabaseName | For publishing to another location.  Specifies a target global database name. The cmdlet will publish an Oracle database with the specified name.  Note: Do not provide this parameter if you want to publish to the original location. | String | False | Named | False |
| OracleSid | For publishing to another location.  Specifies target SID for an Oracle database. The cmdlet will publish the database with the specified SID.  Note: Do not provide this parameter if you want to publish to the original location. | String | False | Named | False |
| WindowsCredentials | For publishing to a Windows machine.  Specifies Windows credentials that the cmdlet will use to connect to a Windows machine. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| OracleHomePassword | For publishing Oracle Database 12c or later to a Windows machine.  Specifies Oracle home credentials that the cmdlet will use for starting Oracle Services on the guest OS.  Note: This parameter is required in case you use the following types of Oracle home User:   * Existing Windows user * New Windows user | SecureString | False | Named | False |
| ToDateTime | Specifies a point in time within the restore interval of an Oracle database.  The cmdlet will publish the database to the state of the specified point in time.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | Named | False |
| SshPort | For publishing to a Linux machine.  Specifies the SSH port number that the cmdlet will use to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |
| Force | Defines that the cmdlet will replace the target Oracle database with the database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORPublishedDatabase](veorpublisheddatabase.md) object that contains settings of the published Oracle database.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Publishing Oracle Database to Windows Machine

|  |  |
| --- | --- |
| This example shows how to publish a backed-up Oracle database to a Windows machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  $creds = Get-Credential  Publish-VEORDatabase -Database $database -Server "OracleSrv2049" -WindowsCredentials $creds |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable. 3. Run the Publish-VEORDatabase cmdlet. Set the $database variable as the Database parameter value. Specify the Server parameter value. Set the $creds variable as the WindowsCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Publishing Oracle Database to Linux Machine

|  |  |
| --- | --- |
| This example shows how to publish backed-up Oracle databases to the original Linux machine with Oracle.  |  | | --- | | $session = Get-VEORRestoreSession  $database = Get-VEORDatabase -Session $session[0] -Name "orcl"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEORLinuxCredential -Account "root" -Password $securepassword  Publish-VEORDatabase -Database $database -LinuxCredentials $linuxcreds |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEORDatabase](get-veordatabase.md) cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.  1. Get Linux credentials:  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the [New-VEORLinuxCredential](new-veorlinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value.  1. Run the Publish-VEORDatabase cmdlet. Specify the following settings:  * Set the $database variable as the Database parameter value. * Set the $linuxcreds variable as the LinuxCredentials parameter value. |

Related Commands

* [Get-VEORRestoreSession](get-veorrestoresession.md)
* [Get-VEORDatabase](get-veordatabase.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [New-VEORLinuxCredential](new-veorlinuxcredential.md)


