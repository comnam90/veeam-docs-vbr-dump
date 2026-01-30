---
title: "Add-VBRCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcredentials.html"
last_updated: "4/3/2024"
product_version: "13.0.1.1071"
---

# Add-VBRCredentials


Short Description

Creates credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add credentials records by a user name and a password.

|  |
| --- |
| Add-VBRCredentials -User <string> [-Password <string>] [-Description <string>] [-Type {Linux | Windows | LinuxPubKey | ManagedSvcAccount}] [-SshPort <int>] [-Passphrase <string>] [-ElevateToRoot] [-AddToSudoers] [-FailoverToSu] [-RootPassword <string>] [-PrivateKeyPath <string>] [-PrivateKey <string>]  [<CommonParameters>] |

* Add credentials records by specifying the user credentials.

|  |
| --- |
| Add-VBRCredentials -Credential <pscredential> [-Description <string>] [-Type {Linux | Windows | LinuxPubKey | ManagedSvcAccount}][-SshPort <int>] [-Passphrase <string>] [-ElevateToRoot] [-AddToSudoers] [-FailoverToSu] [-RootPassword <string>] [-PrivateKeyPath <string>] [-PrivateKey <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new credentials record that you can use to:

* Authenticate with the instances of your virtual infrastructure.
* Add Windows or Linux credentials records including authentication using the Identity/Pubkey method.
* Add Group Managed Service Accounts (gMSAs). For more information, see the [Using Group Managed Service Accounts](https://helpcenter.veeam.com/docs/backup/vsphere/using_gmsa.html?ver=120) section in the User Guide for VMware vSphere.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| User | Specifies a user name you want to use for authenticating with instances of your virtual infrastructure.  Note: You should use DOMAIN\username format for all hosts except ESX/ESXi hosts. | String | True | Named | False |
| Password | Specifies a password you want to use for authenticating with instances of your virtual infrastructure.  Note: This parameter is not required if the Type parameter is set to ManagedSvcAccount. In other cases, this parameter is required. | String | False | Named | False |
| Credential | Specifies credentials you want to add. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. | True | Named | False |
| Description | Specifies a description for a credentials record. It is recommended to input this value to make credential records easily identified. | String | False | Named | False |
| Type | Specifies the credentials type: Linux, Windows, LinuxPubKey, ManagedSvcAccount.  Default: Windows. | VBRCredentialsType | False | Named | False |
| SshPort | For the Identity/Pubkey authentication method.  Specifies a number of an SSH port that you want to use to connect to a Linux server.  Permitted values: 1 to 65535.  Default: 22. | Int32 | False | Named | False |
| Passphrase | Specifies a passphrase for a Linux private key on the backup server. | String | False | Named | False |
| ElevateToRoot | For the Identity/Pubkey authentication method.  Defines that non-root users are provided with root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| AddToSudoers | For the Identity/Pubkey authentication method.  Defines that a user account is added to sudoers file.  Default: (if the ElevateToRoot parameter is set to False) False. | SwitchParameter | False | Named | False |
| FailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  If you provide this parameter, Veeam Backup & Replication will failover to the su command if sudo command fails. Otherwise, if sudo fails Veeam Backup & Replication will not be able to add Linux credentials records.  Default: False. | SwitchParameter | False | Named | False |
| RootPassword | For the Identity/Pubkey authentication method.  Specifies a root password for authentication. | String | False | Named | False |
| PrivateKeyPath | For the Identity/Pubkey authentication method.  The private key is located at the c:\temp\deneb.ppk path. Use this parameter to specify a private key for the Linux public key option of the Type parameter. | String | False | Named | False |
| PrivateKey | For the Identity/Pubkey authentication method.  Specifies a private key. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CCredentials object that contains user credentials records.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating New Windows Credentials Record Using User Name and Password

|  |  |
| --- | --- |
| This command creates a new Windows credentials record with the Administrator user name and the qwerty password of the account. The description is Administrator Credentials.  |  | | --- | | Add-VBRCredentials -Type "Windows" -User "Administrator" -Password "qwerty" -Description "Administrator Credentials" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating New Credentials Record for Administrator

|  |  |
| --- | --- |
| This example shows how to add a credential record for administrator.  |  | | --- | | Get-Credential | Add-VBRCredentials -Description "Administrator Credentials" |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. 2. Pipe the cmdlet output to the Add-VBRCredentials cmdlet. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating New Linux Credentials Record for Administrator

|  |  |
| --- | --- |
| This command adds a Linux credentials record with the Administrator user name and the qwerty password of the account. The credentials record will use the 23 SSH port. The root password privileges are given to the user.  |  | | --- | | Add-VBRCredentials -Type "Linux" -User "Administrator" -Password "qwerty" -SshPort "23" -ElevateToRoot -AddToSudoers -RootPassword "rootpwd" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Adding Linux Pubkey Credentials Record

|  |  |
| --- | --- |
| This command adds a Linux Pubkey credentials record with the user1 user name and the qwerty password of the account. The path to the private key is c:\temp\deneb.ppk. The passphrase to the private key is Pass.  |  | | --- | | Add-VBRCredentials -Type "LinuxPubKey" -User "user1" –Password "qwerty" -PrivateKeyPath "c:\temp\deneb.ppk" -Passphrase "Pass" | |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


