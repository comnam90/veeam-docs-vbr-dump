---
title: "Set-VBRLinux"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrlinux.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Set-VBRLinux


Short Description

Modifies settings of a Linux server added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify settings of a Linux server added to the backup infrastructure.

|  |
| --- |
| Set-VBRLinux -Server <CHost> [-Description <string>] [-SSHPort <int>] [-Credentials <CCredentials>] [-Package <VBRLinuxPackage[]>] [-Force]  [<CommonParameters>] |

* Modify credentials of a Linux server added to the backup infrastructure.

|  |
| --- |
| Set-VBRLinux -Server <CHost> -SSHUser <string> -SSHPassword <string> [-Description <string>] [-SSHPort <int>] [-SSHElevateToRoot] [-SSHAddToSudoers] [-SSHFailoverToSu] [-SSHRootPassword <string>] [-SSHTempCredentials] [-SSHFingerprint <string>] [-Package <VBRLinuxPackage[]>] [-Force] [<CommonParameters>] |

* Modify settings of a Linux server added to the backup infrastructure with a certificate.

|  |
| --- |
| Set-VBRLinux -Server <CHost> [-Description <String>] [-SSHPort <Int32>] [-UseCertificate] [-HandshakeCode <String>] [-Package <VBRLinuxPackage[]>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a Linux server added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Linux server which settings that you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| SSHUser | Specifies the user name you want to use for authenticating with the Linux server. | String | True | Named | False |
| SSHPassword | Specifies the password you want to use for authenticating with the Linux server. | String | True | Named | False |
| Description | Specifies the description of the Linux server. | String | False | Named | False |
| SSHPort | Specifies the SSH port for connection to the Linux server.  Default: 22 | Int | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Linux server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| SSHElevateToRoot | Defines that non-root users are provided with the root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| SSHAddToSudoers | Defines that the user account is added to sudoers file.  Default: (if the ElevateToRoot parameter is set to False) False. | SwitchParameter | False | Named | False |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  If you provide this parameter, Veeam Backup & Replication will failover to the su command if sudo command fails. Otherwise, if sudo fails Veeam Backup & Replication will not be able to add Linux credentials records.  Default: False. | SwitchParameter | False | Named | False |
| SSHRootPassword | Specifies the root password to be used for authentication. | String | False | Named | False |
| SSHTempCredentials | Defines that the cmdlet will use the temporary credentials to connect to Linux server.  Default: False. | SwitchParameter | False | Named | False |
| UseCertificate | Defines if certificate-based authentication is used. | SwitchParameter | True | Named | False |
| SSHFingerprint | Specifies SSH host fingerprint. | String | False | Named | False |
| Force | Defines that the cmdlet will modify settings of Linux server without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| Package | Specifies the Linux package. | Accepts the VBRLinuxPackage object. To get this object, run the [Get-VBRLinuxPackage](get-vbrlinuxpackage.md) cmdlet. | False | Named | False |
| HandshakeCode | Specifies the handshake code used to pair with the server. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of a Linux server added to the backup infrastructure.

Examples

Modifying Linux Server Settings

This example shows how to set the SSH port to 2222.

|  |
| --- |
| $server = Get-VBRServer  Set-VBRLinux -Server $server -SSHPort 2222 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable.
2. Run the Set-VBRLinux cmdlet. Set the $server variable as the Server parameter value. Specify the SSHPort parameter value.

Related Commands

[Get-VBRServer](get-vbrserver.md)


