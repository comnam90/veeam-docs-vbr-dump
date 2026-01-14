---
title: "New-VBRLinuxFileRestoreHelperHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrlinuxfilerestorehelperhost.html"
last_updated: "11/29/2024"
product_version: "13.0.1.1071"
---

# New-VBRLinuxFileRestoreHelperHost

In this article

Short Description

Creates temporary Linux helper host used to launch the Guest OS File Restore.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a Linux helper host with credentials that already exist in Veeam Backup & Replication.

|  |
| --- |
| New-VBRLinuxFileRestoreHelperHost [-Credentials <CCredentials>] [-Force] [-Name <string>] [-SSHFingerprint <string>]  [<CommonParameters>] |

* Create a Linux helper host with a new set of credentials.

|  |
| --- |
| New-VBRLinuxFileRestoreHelperHost [-Force] [-Name <string>] [-SSHAddToSudoers] [-SSHElevateToRoot] [-SSHFailoverToSu] [-SSHFingerPrint <string>] [-SSHPassword <String>] [-SSHPort <int>] [-SSHRootPassword <string>] [-SSHUser <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRLinuxFileRestoreHelperHost object. This object contains connectivity parameters and a fingerprint.

|  |
| --- |
| Note |
| If you create a Linux helper host with the second parameter set, a new set of credentials will be created each time you run the New-VBRLinuxFileRestoreHelperHost cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies the credentials you want to use for authenticating with the Linux server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Force | Defines that the cmdlet will add temporary Linux helper host specification without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| Name | Specifies the DNS name or IP address of the Linux server. | String | True | Named | False |
| SSHAddToSudoers | Defines that the user account is added to sudoers file.  Default: False. | SwitchParameter | False | Named | False |
| SSHElevateToRoot | Defines that non-root users are provided with the root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  Default: False. | SwitchParameter | False | Named | False |
| SSHFingerPrint | Specifies the SSH host fingerprint. | String | False | Named | False |
| SSHPassword | Specifies the password you want to use for authenticating with the Linux server. | String | True | Named | False |
| SSHPort | Specifies the SSH port for connection to the Linux server.  Default: 22. | Int32 | False | Named | False |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | False |
| SSHUser | Specifies the user name you want to use for authenticating with the Linux server. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLinuxFileRestoreHelperHost object that contains settings for a temporary Linux helper host.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Temporary Linux Helper Host with Existing Credentials

|  |  |
| --- | --- |
| This example shows how to create a Linux helper host using credentials that already exist in Veeam Backup & Replication.  |  | | --- | | $backup = Get-VBRBackup -Name "Backup Job 1"  $point = Get-VBRRestorePoint -Backup $backup  $cred = Get-VBRCredentials -Name "root"  $hh = New-VBRLinuxFileRestoreHelperHost -Force -Name "154.19.90.152" -Credentials $cred  $session = Start-VBRLinuxFileRestore -RestorePoint $point -HelperHost $hh |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $point variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $cred variable. 4. Run the New-VBRLinuxFileRestoreHelperHost cmdlet. Provide the Force parameter. Specify the Name parameter value. Set the $cred variable as the Credentials parameter value. Save the result to the $hh variable. 5. Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $point variable as the RestorePoint parameter value. Set the $hh variable as the HelperHost parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Temporary Linux Helper Host with New Credentials

|  |  |
| --- | --- |
| This example shows how to create a Linux helper host using a new set of credentials.  |  | | --- | | $name = "154.19.90.152"  $hh = New-VBRLinuxFileRestoreHelperHost -Name $name -SSHUser LinuxUser -SSHPassword P@ssw0rd -SSHElevateToRoot -SSHAddToSudoers -SSHRootPassword P@ssw0rd |  Perform the following steps:   1. Specify the DNS name or IP address. Save the result to the $name variable. 2. Run the New-VBRLinuxFileRestoreHelperHost cmdlet. Specify the following settings:  * Set the $name variable as the Name parameter value. * Specify the SSHUser parameter value. * Specify the SSHPassword parameter value. * Provide SSHElevateToRoot and SSHAddToSudoers parameters. * Specify the SSHRootPassword parameter value.   Save the result to the $hh variable. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md)

Page updated 11/29/2024

Page content applies to build 13.0.1.1071
