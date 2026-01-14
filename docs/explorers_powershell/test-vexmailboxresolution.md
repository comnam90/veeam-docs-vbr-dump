---
title: "test-vexmailboxresolution"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/test-vexmailboxresolution.html"
last_updated: "3/25/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Tests the availability of Microsoft Exchange mailboxes before a bulk mailbox restore.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides cmdlet sets that allow you to:

* Test mailbox resolution.

|  |
| --- |
| Test-VEXMailboxResolution [-Credential <PSCredential>] -Mailbox <VEXMailbox[]> [-Office365Credential <PSCredential>] [-Domain <String>] [-Force] [<CommonParameters>] |

* [For Veeam Backup for Microsoft 365 only] Test resolution of mailboxes using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Test-VEXMailboxResolution [-Credential <PSCredential>] -Mailbox <VEXMailbox[]> -ApplicationId <Guid> [-Domain <String>] [-Force] [<CommonParameters>] |

* [For Veeam Backup for Microsoft 365 only] Multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Test-VEXMailboxResolution [-Credential <PSCredential>] -Mailbox <VEXMailbox[]> -ApplicationId <Guid> -ApplicationCertificatePath <String> [-ApplicationCertificatePassword <SecureString>] [-Domain <String>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet tests the availability of mailboxes. You may want to run this cmdlet before you start a bulk mailbox restore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credential | Specifies Windows user credentials to connect to the Active Directory domain and the Exchange server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| Mailbox | Specifies a mailbox. The cmdlet will check whether this mailbox is available. | Accepts the [VEXMailbox](vexmailbox.md)[] object. To get this object, run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. | True | Named | False |
| Office365Credential | Specifies a Microsoft 365 user account credentials to connect to the backup proxy server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| Domain | Specifies a mailbox domain. | String | False | Named | False |
| Force | Defines that the cmdlet will ignore the certificate upon the connection.  Default: False | SwitchParameter | False | Named | False |
| ApplicationId | Specifies a Microsoft Entra application ID. The cmdlet will use this application ID to set up a secure connection to a Microsoft organization.  Note: This parameter works for mailboxes that are backed-up with Veeam Backup for Microsoft 365 only. | Guid | True | Named | False |
| ApplicationCertificatePath | To test mailbox resolution using multi-factor authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will import the certificate that is located in this path to set up an encrypted connection to a Microsoft organization and to test the mailbox resolution. | String | True | Named | False |
| ApplicationCertificatePassword | To test mailbox resolution using multi-factor authentication.  Specifies the certificate password. The cmdlet will use this password to confirm the certificate that you want to import to a Microsoft Entra application. After that the cmdlet will set up an encrypted connection to a Microsoft organization and will test the mailbox resolution. This parameter is obligatory. | SecureString | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Testing Mailbox Resolution [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to test the availability of Exchange mailboxes.  |  | | --- | | $credentials = Get-Credential  $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $mailbox = Get-VEXMailbox -Database $database  Test-VEXMailboxResolution -Mailbox $mailboxes -Domain test.local -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Type Windows credentials to connect to the Active Directory domain and the Exchange server. Save the result to the $credentials variable. 2. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 3. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 4. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $mailbox variable. 5. Run the Test-VEXMailboxResolution cmdlet. Specify the following settings:  * Set the $mailbox variable as the Mailbox parameter value. * Specify the Domain parameter value. * Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Testing Mailboxes Resolution [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to test the availability of Exchange mailboxes from the support3backup.onmicrosoft.com backed-up Exchange organization.  |  | | --- | | $credentials = Get-Credential  $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $mailboxes = Get-VEXMailbox -Database $database  Test-VEXMailboxResolution -Mailbox $mailboxes -Domain test.local -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type Windows credentials to connect to the Active Directory domain and the Exchange server. Save the result to the $credentials variable. 2. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 3. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 4. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $mailboxes variable. 5. Run the Test-VEXMailboxResolution cmdlet. Specify the following settings:  * Set the $mailboxes variable as the Mailbox parameter value. * Specify the Domain parameter value. * Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Testing Mailbox Resolution Using Multi-Factor Authentication with Microsoft Entra Application ID [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to test the availability of the Sales Exchange mailbox. Veeam Backup for Microsoft 365 will use the 76397916-8dcb-4348-96ac-6e2e881f9292 Microsoft Entra application ID to set up a secure connection to a Microsoft organization.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  Test-VEXMailboxResolution -Mailbox $mailbox -Domain test.local -ApplicationId 76397916-8dcb-4348-96ac-6e2e881f9292 |  Perform the following steps:   1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the Test-VEXMailboxResolution cmdlet. Specify the following settings:  * Set the $mailbox variable as the Mailbox parameter value. * Specify the Domain parameter value. * Specify the ApplicationId parameter value.  1. To set up a secure connection to a Microsoft organization, open the <https://microsoft.com/devicelogin> link in your browser and enter the code that you get in the PowerShell Console for authenticating to the Microsoft 365 server. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Testing Mailbox Resolution Using Multi-Factor Authentication with Microsoft Entra Application Certificate [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to test the availability of the Sales Exchange mailbox with the Microsoft Entra application certificate.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  $securepassword = Read-Host "Enter your password" -AsSecureString  Enter your password: \*\*\*\*\*\*\*\*\*\*  Test-VEXMailboxResolution -Mailbox $mailbox -Domain test.local -ApplicationCertificatePath "C:\certificate\cert.pfx" -ApplicationCertificatePassword $securepassword |  Perform the following steps:   1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the message that the console will display as a prompt. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 5. Enter the password. 6. Run the Test-VEXMailboxResolution cmdlet. Specify the following settings:  * Set the $mailbox variable as the Mailbox parameter value. * Specify the Domain parameter value. * Specify the ApplicationCertificatePath parameter value. * Set the $securepassword variable as the ApplicationCertificatePassword parameter value.  1. To set up a secure connection to a Microsoft organization, open the <https://microsoft.com/devicelogin> link in your browser and enter the code that you get in the PowerShell Console for authenticating to the Microsoft 365 server. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)

Page updated 3/25/2025

Page content applies to build 13.0.1.1071
