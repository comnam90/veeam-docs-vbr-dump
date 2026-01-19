---
title: "New-VEORLinuxCredential"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new-veorlinuxcredential.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# New-VEORLinuxCredential


Short Description

Creates Linux credential record to connect to a Linux machine.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VEORLinuxCredential [-Account] <String> [-Password <SecureString>] [-PrivateKeyFilePath <String>] [-Passphrase <SecureString>] [-ElevateAccountToRoot] [-AddToSudoers] [-UseSuIfSudoUnavailable] [-RootPassword <SecureString>] [<CommonParameters>] |

Detailed Description

This cmdlet creates a Linux credential record. You can use this credential record to connect to the Oracle database and restore this database to a Linux machine.

Run the [Restore-VEORDatabase](restore-veordatabase.md) cmdlet to restore an Oracle database.

Run the [Restore-VEORRMANDatabase](restore-veorrmandatabase.md) cmdlet to restore Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the user name of the account that will be used to connect to the target Linux server.  Note: The account must be a member of the dba group. | String | True | 0 | False |
| Password | Specifies a password that will be used to connect to the target Linux server. | SecureString | False | Named | False |
| PrivateKeyFilePath | Specifies the path for the private key that the cmdlet will use to connect to the target Linux server. | String | False | Named | False |
| Passphrase | Specifies a passphrase that the cmdlet will use to connect to the target Linux server. | SecureString | False | Named | False |
| ElevateAccountToRoot | Defines that the account must be elevated to root. | SwitchParameter | False | Named | False |
| AddToSudoers | Defines that the cmdlet will add the account to sudoers. | SwitchParameter | False | Named | False |
| UseSuIfSudoUnavailable | Defines that the Su command is used instead of the Sudo command. | SwitchParameter | False | Named | False |
| RootPassword | Specifies the root password. | SecureString | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORLinuxCredential](veorlinuxcredential.md) object that contains a Linux credential record.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Linux Credential Record with Password

|  |  |
| --- | --- |
| This example shows how to create a Linux credential record with the password authentication method. Veeam Explorer for Oracle will use these credentials to connect to the target Linux machine.  |  | | --- | | $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $credentials = New-VEORLinuxCredential -Account "root" -Password $securepassword |  Perform the following steps:   1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux server. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the New-VEORLinuxCredential cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $credentials variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Linux Credential Record with Private Key

|  |  |
| --- | --- |
| This example shows how to create a Linux credential record with the private key authentication method. Veeam Explorer for Oracle will use these credentials to connect to the target Linux machine.  |  | | --- | | $securepassword = Read-Host -Prompt "Enter secure string" -AsSecureString  $credentials = New-VEORLinuxCredential -Account "root" -PrivateKeyFilePath "/home/.ecryptfs/<user>/.Private/" -Passphrase $securepassword |  Perform the following steps:   1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to create a secure password. Enter credentials that will be used to connect to the target Linux server. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the New-VEORLinuxCredential cmdlet. Specify the following settings:  * Specify the Account parameter value. * Specify the PrivateKeyFilePath parameter value. * Set $securepassword variable as the Passphrase parameter value.   Save the result to the $credentials variable to use it with other cmdlets. |

Related Commands

[Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)


