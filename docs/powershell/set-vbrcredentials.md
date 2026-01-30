---
title: "Set-VBRCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcredentials.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRCredentials


Short Description

Modifies credentials records properties.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify credentials records.

|  |
| --- |
| Set-VBRCredentials -Credential <CCredentials> [-User <string>] [-Password <string>] [-Description <string>] [-SshPort <int>] [-Passphrase <string>] [-ElevateToRoot] [-AddToSudoers] [-FailoverToSu] [-RootPassword <string>]  [<CommonParameters>] |

* Modify credentials records by specifying the file path to the Linux private key.

|  |
| --- |
| Set-VBRCredentials -Credential <CCredentials> [-User <string>] [-Password <string>] [-Description <string>] [-SshPort <int>] [-Passphrase <string>] [-ElevateToRoot] [-AddToSudoers] [-FailoverToSu] [-RootPassword <string>] [-PrivateKeyPath <string>]  [<CommonParameters>] |

* Modify credentials records by specifying the Linux private key.

|  |
| --- |
| Set-VBRCredentials -Credential <CCredentials> [-User <string>] [-Password <string>] [-Description <string>] [-SshPort <int>] [-Passphrase <string>] [-ElevateToRoot] [-AddToSudoers] [-FailoverToSu] [-RootPassword <string>] [-PrivateKey <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to modify password or description of a selected credentials record.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credential | Specifies credentials you want to modify. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | True (ByValue, |
| User | Specifies a user name you want to use to authenticate against instances of your virtual infrastructure.  Note: You should use DOMAIN\username format for all hosts except ESX/ESXi hosts. | String | False | Named | False |
| Password | Specifies a password you want to use to authenticate with instances of your virtual infrastructure. | String | False | Named | False |
| Description | Specifies a description for a credentials record. It is recommended to input this value to make credential records easily identified. | String | False | Named | False |
| SshPort | Used for Identity/Pubkey authentication method.  Specifies a number of an SSH port that you want to use to connect to a Linux server.  Permitted values: 1 to 65535.  Default: 22. | Int32 | False | Named | False |
| Passphrase | Specifies a passphrase for a Linux private key on a backup server. | String | False | Named | False |
| ElevateToRoot | Used for Identity/Pubkey authentication method.  Defines that non-root users are provided with root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| AddToSudoers | Used for Identity/Pubkey authentication method.  Defines that a user account is added to the sudoers file.  Default: (if the ElevateToRoot parameter is set to False) False. | SwitchParameter | False | Named | False |
| FailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  If you provide this parameter, Veeam Backup & Replication will failover to the su command if the sudo command fails. Otherwise, if the sudo fails Veeam Backup & Replication will not be able to add Linux credentials records.  Default: False. | SwitchParameter | False | Named | False |
| RootPassword | Used for Identity/Pubkey authentication method.  Specifies a root password for authentication. | String | False | Named | False |
| PrivateKeyPath | Used for Identity/Pubkey authentication method.  Specifies a path to a private key. Use this parameter to specify a private key for the LinuxPubKey option of the Type parameter. | String | False | Named | False |
| PrivateKey | Used for Identity/Pubkey authentication method.  Specifies a private key. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CCredentials object that contains user credentials.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting New Password for Credentials Record Using User Name

|  |  |
| --- | --- |
| This example shows how to set a new password for the credentials record with the Administrator user name. The new password is qwerty.  |  | | --- | | $credentials = Get-VBRCredentials -Name "Administrator"  Set-VBRCredentials -Credential $credentials -Password "qwerty" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Set-VBRCredentials cmdlet. Set the $credentials variable as the Credential parameter value. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting New Password for Credentials Record Using User Name [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set a new password for the credentials record with the Administrator user name. The new password is qwerty.  |  | | --- | | Get-VBRCredentials -Name "Administrator" | Set-VBRCredentials -Password "qwerty" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRCredentials cmdlet. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Setting New Description for Specific Credentials Record

|  |  |
| --- | --- |
| This example shows how to set a new description for the credentials record. The new description is ESXi Host Credentials.  |  | | --- | | $credentials = Get-VBRCredentials  Set-VBRCredentials -Credential $credentials[1] -Description "ESXi Host Credentials" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $credentials variable.   The Get-VBRCredentials cmdlet will return an array of credential records. Mind the ordinal number of the necessary credential record (in our example, it is the second restore session in the array).   1. Run the Set-VBRCredentials cmdlet. Set the $credentials variable as the Credentials parameter value. Specify the Description parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


