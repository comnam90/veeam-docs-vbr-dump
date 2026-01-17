---
title: "New-VEMDBLinuxCredentials"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new-vemdblinuxcredentials.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# New-VEMDBLinuxCredentials


Short Description

Creates Linux credential record to connect to a target MongoDB server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VEMDBLinuxCredentials [-Account] <String> [-Password <SecureString>] [-PrivateKeyFilePath <String>] [-Passphrase <SecureString>] [-ElevateAccountToRoot] [-AddToSudoers] [-UseSuIfSudoUnavailable] [-RootPassword <SecureString>] [<CommonParameters>] |

Detailed Description

This cmdlet creates a Linux credential record. You can use this credential record to connect to the target Linux machine with MongoDB. Note that the user must have root privileges on the target server.

Run the [Start-VEMDBDataRestore](start-vemdbdatarestore.md) cmdlet to restore MongoDB collections to the primary node of a MongoDB replica set or restore the entire instance to a target Linux machine with MongoDB.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the user name of the account that will be used to connect to the target Linux server. | String | True | 0 | False |
| AddToSudoers | Defines that the cmdlet will add the account to the sudoers file. | SwitchParameter | False | Named | False |
| ElevateAccountToRoot | Defines that the account must be elevated to root. | SwitchParameter | False | Named | False |
| Passphrase | Specifies a passphrase. The cmdlet will use that passphrase to connect to the target Linux server. | SecureString | False | Named | False |
| Password | Specifies a password that will be used to connect to the target Linux server. | SecureString | False | Named | False |
| PrivateKeyFilePath | Specifies the path for the private key. The cmdlet will use that key to connect to the target Linux server. | String | False | Named | False |
| RootPassword | Specifies the root password. | SecureString | False | Named | False |
| UseSuIfSudoUnavailable | Defines that the su command is used instead of the sudo command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBLinuxCredentials](vemdblinuxcredentials.md) object that contains a Linux credential record.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Linux Credential Record with Password

|  |  |
| --- | --- |
| This example shows how to create a Linux credential record with the password authentication method. Veeam Explorer for MongoDB will use these credentials to connect to the target Linux machine.  |  | | --- | | $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $credentials = New-VEMDBLinuxCredentials -Account "root" -Password $securepassword |  Perform the following steps:   1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux machine. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the New-VEMDBLinuxCredentials cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $credentials variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Linux Credential Record with Private Key

|  |  |
| --- | --- |
| This example shows how to create a Linux credential record with the private key authentication method. Veeam Explorer for MongoDB will use these credentials to connect to the target Linux machine.  |  | | --- | | $securepassword = Read-Host -Prompt "Enter secure string" -AsSecureString  $credentials = New-VEMDBLinuxCredentials -Account "root" -PrivateKeyFilePath "/home/.ecryptfs/<user>/.Private/" -Passphrase $securepassword |  Perform the following steps:   1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux machine. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the New-VEMDBLinuxCredentials cmdlet. Specify the following settings:  * Specify the Account parameter value. * Specify the PrivateKeyFilePath parameter value. * Set the $securepassword variable as the Passphrase parameter value.   Save the result to the $credentials variable to use it with other cmdlets. |

Related Commands

[Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)


