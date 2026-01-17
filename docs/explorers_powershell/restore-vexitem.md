---
title: "Restore-VEXItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-vexitem.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restores backups of Exchange mailboxes.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore Exchange mailbox items.

|  |
| --- |
| Restore-VEXItem -Item <VEXItem[]> [-ApplicationId <Guid>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-ImpersonationAccountName <String>] [-OrganizationName <String>] [-Region <VBOOffice365Region>] [-Server <String>] [-TargetMailbox <String>] [-Credential <PSCredential>] [-ToFolder <String>] [-RestoreChangedItem] [-RestoreDeletedItem] [-MarkAsUnread] [-Force] [<CommonParameters>] |

* Restore Exchange mailboxes.

|  |
| --- |
| Restore-VEXItem -Mailbox <VEXMailbox> [-ApplicationId <Guid>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-ImpersonationAccountName <String>] [-OrganizationName <String>] [-Region <VBOOffice365Region>] [-Server <String>] [-TargetMailbox <String>] [-Credential <PSCredential>] [-ToFolder <String>] [-RestoreChangedItem] [-RestoreDeletedItem] [-MarkAsUnread] [-Force] [-ExcludeDrafts] [-ExcludeDeletedItems] [-ExcludeInPlaceHoldItems] [-ExcludeLitigationHoldItems] [<CommonParameters>] |

* Restore Exchange mailbox folders.

|  |
| --- |
| Restore-VEXItem -Folder <VEXFolder> [-ApplicationId <Guid>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-ImpersonationAccountName <String>] [-OrganizationName <String>] [-Region <VBOOffice365Region>] [-Server <String>] [-TargetMailbox <String>] [-Credential <PSCredential>] [-ToFolder <String>] [-RestoreChangedItem] [-RestoreDeletedItem] [-MarkAsUnread] [-Force] [<CommonParameters>] |

* Restore multiple Exchange organization mailboxes.

|  |
| --- |
| Restore-VEXItem -MultipleMailboxes <VEXMailbox[]> [-SkipUnresolvedMailboxes] [-RestoreItemsForLastDays <Int32>] [-Office365Credential <PSCredential>] [-ApplicationId <Guid>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-ImpersonationAccountName <String>] [-Region <VBOOffice365Region>] [-Domain <String>] [-Server <String>] [-Credential <PSCredential>] [-RestoreChangedItem] [-RestoreDeletedItem] [-MarkAsUnread] [-Force] [-ExcludeDrafts] [-ExcludeDeletedItems] [-ExcludeInPlaceHoldItems] [-ExcludeLitigationHoldItems] [<CommonParameters>] |

Detailed Description

This cmdlet restores backups of Exchange organization mailboxes. You can restore Exchange organization mailboxes with one of the following authentication methods:

* Authentication methods that utilize legacy protocols.
* Multi-factor authentication. To restore data the cmdlet utilizes a Microsoft Entra application.

|  |
| --- |
| Note |
| * Before running this cmdlet, you must first start a restore session. For more information on how to start a restore session, see [Start-VBOExchangeItemRestoreSession](start-vboexchangeitemrestoresession.md) or [Start-VBRExchangeItemRestoreSession](start-vbrexchangeitemrestoresession.md). * When restoring from Veeam Backup & Replication backups, consider the following:  * The machine running Veeam Explorer for Microsoft Exchange must be within the same domain as the target Microsoft Exchange server. * The account used to run Veeam Explorer for Microsoft Exchange must exist within the same domain as the target Microsoft Exchange server. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of items for an Exchange organization mailbox. The cmdlet will restore these items. | Accepts the [VEXItem](vexitem.md)[] object. To get this object, run the [Get-VEXItem](get-vexitem.md) cmdlet. | True | Named | True (ByValue) |
| ApplicationId | To restore data using multi-factor authentication.  Specifies a Microsoft Entra application ID. The cmdlet will use this application ID to set up a secure connection to a Microsoft organization. | Guid | False | Named | False |
| ApplicationCertificatePath | To restore data using multi-factor authentication.  Specifies a path to the certificate. The cmdlet will import this certificate that is located in this path to set up an encrypted connection to a Microsoft organization. | String | False | Named | False |
| ApplicationCertificatePassword | To restore data using multi-factor authentication.  Specifies the certificate password. The cmdlet will use this password to confirm the certificate that you want to import to a Microsoft Entra application. This parameter is obligatory. | SecureString | False | Named | False |
| ImpersonationAccountName | To restore data using multi-factor authentication.  Specifies a user name of a Microsoft Exchange user. The cmdlet will use this user name for authenticating to the Microsoft Exchange server. Use this parameter together with the ApplicationCertificatePassword parameter. | String | False | Named | False |
| OrganizationName | To restore data to another organization.  Specifies an organization name. The cmdlet will restore an Exchange items to this organization.  Note: This parameter is available for restore from backups created by Veeam Backup for Microsoft 365 only. | String | False | Named | False |
| Region | To restore data to another organization.  Specifies a Microsoft Entra region. The cmdlet will restore Exchange items to a Microsoft organization that belongs to one of the following regions:   * Worldwide * Germany * China * USDefence * USGovernment   Note: This parameter is available for restore from backups created by Veeam Backup for Microsoft 365 only. | VBOOffice365Region | False | Named | False |
| Server | Specifies DNS name or IP address of the Microsoft Exchange server with the Client Access Server (CAS) role. The cmdlet will perform a restore to this mailbox server. | String | False | Named | False |
| TargetMailbox | Specifies an Exchange organization mailbox. The cmdlet will perform a restore to this mailbox.  Note: The mailbox must be in the username@domain format.  If this parameter is omitted, the cmdlet will perform a restore to the same mailbox on the production Exchange server. | String | False | Named | False |
| Credential | Specifies account credentials that you want to use for connecting to the Microsoft Exchange server.  If omitted, the cmdlet will use a currently logged in user Windows account credentials to connect to the Microsoft Exchange server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ToFolder | Specifies a mailbox folder. The cmdlet will restore backups to this folder. | String | False | Named | False |
| RestoreChangedItem | Defines that the cmdlet will restore all versions of mailbox items that were modified by the user.  Default: False | SwitchParameter | False | Named | False |
| RestoreDeletedItem | Defines that the cmdlet will restore mailbox items that were deleted by the user.  Default: False | SwitchParameter | False | Named | False |
| MarkAsUnread | Defines that the cmdlet will mark the restored mailbox items as unread.  Default: False | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform a restore without notifying a user.  Default: False | SwitchParameter | False | Named | False |
| Mailbox | Specifies an Exchange organization mailbox that you want to restore. | Accepts the [VEXMailbox](vexmailbox.md) object. To get this object, run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. | True | Named | True (ByValue) |
| ExcludeDrafts | Defines that the cmdlet will not restore the Drafts folder.  Default: False | SwitchParameter | False | Named | False |
| ExcludeDeletedItems | Defines that the cmdlet will not restore the Deleted Items folder.  Default: False | SwitchParameter | False | Named | False |
| ExcludeInPlaceHoldItems | Defines that the cmdlet will not restore mailbox items that have been placed on hold.  Default: False | SwitchParameter | False | Named | False |
| ExcludeLitigationHoldItems | Defines that the cmdlet will not restore the mailbox items that have been placed on Litigation Hold.  Default: False | SwitchParameter | False | Named | False |
| Folder | Specifies a folder of an Exchange organization mailbox. The cmdlet will restore this folder with all its subfolders. | Accepts the [VEXFolder](vexfolder.md) object. To get this object, run the [Get-VEXFolder](get-vexfolder.md) cmdlet. | True | Named | True (ByValue) |
| MultipleMailboxes | Specifies an array of Exchange organization mailboxes that you want to restore. | Accepts the [VEXMailbox](vexmailbox.md)[] object. To get this object, run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. | True | Named | True (ByValue) |
| SkipUnresolvedMailboxes | Defines that the cmdlet will not restore mailboxes that do not resolve.  Default: False | SwitchParameter | False | Named | False |
| RestoreItemsForLastDays | Specifies the number of subsequent past days from which this cmdlet will restore the items from the selected users in the first place. | Int32 | False | Named | False |
| Office365Credential | Specifies an account credentials that you want to use for connecting to the Microsoft Office365 server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| Domain | Specifies the Exchange organization domain. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXRestoreResult](vexrestoreresult.md)[] array that contains information about the restore process.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Exchange Mailbox [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to restore the Sales mailbox with the following settings:   * The cmdlet will restore mailbox to the ExchangeCAS.Domain.local production server. * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  $creds = Get-Credential  Restore-VEXItem -Mailbox $salesmailbox -Server ExchangeCAS.Domain.local -Credential $creds -RestoreChangedItem |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Provide the RestoreChangedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Mailbox Folder [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to restore the Contacts folder with the following settings:   * The cmdlet will restore the Contacts folder to the sales@Domain.local mailbox on the ExchangeCAS.Domain.local production server.  * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox -Name "Contacts"  $creds = Get-Credential  Restore-VEXItem -Folder $contacts -Server ExchangeCAS.Domain.local -Credential $creds -TargetMailbox "sales@Domain.local" -RestoreChangedItem |  Perform the following steps:   1. Get the mailbox folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create the PSCredential object. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $contacts variable as the Folder parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Specify the TargetMailbox parameter value. * Provide the RestoreChangedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring All Mailbox Items [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to restore all mailbox items with the following settings:   * The cmdlet will restore items from the Contacts folder and its subfolders to the ExchangeCAS.Domain.local production server.  * The cmdlet will restore all versions of mailbox items that were modified by the user. * The cmdlet will restore mailbox items that were deleted by the user.   |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox -Name "Contacts"  $contactitems = Get-VEXItem -Folder $contacts -Recurse  $creds = Get-Credential  Restore-VEXItem -Item $contactitems -Server ExchangeCAS.Domain.local -Credential $creds -RestoreChangedItem -RestoreDeletedItem |  Perform the following steps:   1. Get all items from the folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable. 5. Run the [Get-VEXItem](get-vexitem.md) cmdlet. Set the $contacts variable as the Folder parameter value. Provide the Recurse parameter. Save the result to the $contactitems variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $contactitems variable as the Item parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Specify the TargetMailbox parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreDeletedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Multiple Mailboxes [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to restore multiple Exchange mailboxes with the following settings:   * The cmdlet will restore mailboxes to the ExchangeCAS.Domain.local production server.  * The cmdlet will restore all versions of mailbox items that were modified by the user. * The cmdlet will restore mailbox items that were deleted by the user.   |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $mailbox = Get-VEXMailbox -Database $database  $creds = Get-Credential  Restore-VEXItem -MultipleMailboxes $mailbox -Server ExchangeCAS.Domain.local -Credential $creds -RestoreChangedItem -RestoreDeletedItem |  Perform the following steps:   1. Get all items from the folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Save the result to the $mailbox variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $mailbox variable as the MultipleMailboxes parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreDeletedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Restoring Exchange Mailbox [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore the Sales mailbox with the following settings:   * The cmdlet will restore the mailbox to the outlook.office365.com production server. * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $creds = Get-Credential  Restore-VEXItem -Mailbox $salesmailbox -Server outlook.office365.com -Credential $creds -RestoreChangedItem |  Perform the following steps:   1. Get the sales mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Provide the RestoreChangedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Restoring Exchange Mailbox Using Multi-Factor Authentication with Microsoft Entra Application ID [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore the Sales mailbox with the following settings:   * The cmdlet will use the c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 Microsoft Entra application ID. * The cmdlet will restore the mailbox to the @tech-365.tech Microsoft organization. * The cmdlet will restore the mailbox to the Worldwide Microsoft Entra region. * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  Restore-VEXItem -Mailbox $salesmailbox -ApplicationId c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 -OrganizationName @tech-365.tech -Region Worldwide -RestoreChangedItem |  Perform the following steps:   1. Get the Sales mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value. * Specify the ApplicationId parameter value. * Specify the OrganizationName parameter value. * Specify the Region parameter value. * Provide the RestoreChangedItem parameter.  1. To set up a secure connection to a Microsoft organization, open the <https://microsoft.com/devicelogin> link in a browser and enter the code that you get in the PowerShell Console for authenticating to the Microsoft 365 server. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Restoring Exchange Mailbox Using Multi-Factor Authentication with Microsoft Entra Application Certificate [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore the Sales mailbox with the following settings:   * The cmdlet will use the c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 Microsoft Entra application ID. * The cmdlet will use the certificate located at the C:\Certificate path. * The cmdlet will restore the mailbox to the @tech-365.tech Microsoft organization. * The cmdlet will restore the mailbox to the Worldwide Microsoft Entra region. * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  Enter password: \*\*\*\*\*\*\*\*  Restore-VEXItem -Mailbox $salesmailbox -ApplicationId c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 -ApplicationCertificatePath "C:\Certificate\Cert.pfx" -ApplicationCertificatePassword $securepassword -ImpersonationAccountName "global2@tech-365.tech" -OrganizationName @tech-365.tech -Region Worldwide -RestoreChangedItem |  Perform the following steps:   1. Get the Sales mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to specify the password. Specify the text that will show up in the password prompt window in the Prompt parameter. Specify the AsSecureString parameter to convert the password to the secure string. 2. Enter the password.  1. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value. * Specify the ApplicationId parameter value. * Specify the ApplicationCertificatePath parameter value. * Set the $securepassword variable as the ApplicationCertificatePassword parameter value. * Specify the ImpersonationAccountName parameter value. * Specify the OrganizationName parameter value. * Specify the Region parameter value. * Provide the RestoreChangedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 8. Restoring Folder [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore the Contacts folder with the following settings:   * The cmdlet will restore the Contacts folder to the sales@abc.onmicrosoft.com mailbox on the outlook.office365.com production server. * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "north.sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox -Name "Contacts"  $creds = Get-Credential  Restore-VEXItem -Folder $contacts -Server outlook.office365.com -Credential $creds -TargetMailbox "sales@abc.onmicrosoft.com" -RestoreChangedItem |  Perform the following steps:   1. Get the mailbox folder:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md). Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create the PSCredential object. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $contacts variable as the Folder parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Specify the TargetMailbox parameter value. * Provide the RestoreChangedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 9. Restoring All Mailbox Items [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore all mailbox items with the following settings:   * The cmdlet will restore items from the Contacts folder and its subfolders to the outlook.office365.com production server. * The cmdlet will restore all versions of mailbox items that were modified by the user. * The cmdlet will restore mailbox items that were deleted by the user.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox  $contactitems = Get-VEXItem -Folder $contacts -Recurse  $creds = Get-Credential  Restore-VEXItem -Item $contactitems -Server outlook.office365.com -Credential $creds -RestoreChangedItem -RestoreDeletedItem |  Perform the following steps:   1. Get all items from the Contacts folder:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet to get an active restore session. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable. 5. Run the [Get-VEXItem](get-vexitem.md) cmdlet. Set the $contacts variable as the Folder parameter value. Provide the Recurse parameter. Save the result to the $contactitems variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable. 2. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $contactitems variable as the Item parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreDeletedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 10. Restoring Exchange Mailbox Using Multi-Factor Authentication [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore mailbox items to the same organization with the following settings:   * The cmdlet will use the 7ddefae2-c812-4fe8-bd8b-6222efc8b434 Microsoft Entra application ID to restore mailbox. * The cmdlet will restore all versions of mailbox items that were modified by the user.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  Restore-VEXItem -Mailbox $salesmailbox -ApplicationId 7ddefae2-c812-4fe8-bd8b-6222efc8b434 -RestoreChangedItem |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value. * Specify the ApplicationId parameter value. * Provide the RestoreChangedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 11. Restoring Exchange Mailbox to Different Organization [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore mailbox items to a different organization with the following settings:   * The cmdlet will restore the mailbox items to the UserA@tech.com mailbox.  * The cmdlet will restore mailbox items that are missing in the target location.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  $creds = Get-Credential  Restore-VEXItem -Mailbox $salesmailbox -Credential $creds -TargetMailbox UserA@tech.com -RestoreDeletedItem |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $creds variable.  1. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value. * Set the $creds variable as the Credential parameter value. * Specify the TargetMailbox parameter value. * Provide the RestoreDeletedItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 12. Restoring Exchange Mailbox to Different Organization Using Multi-Factor Authentication with Microsoft Entra Application ID [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to restore mailbox items to the tech.onmicrosoft.com organization with the following settings:   * The tech.onmicrosoft.com organization belongs to the Worldwide Microsoft Entra region. * The cmdlet will apply the 7ddefae2-c812-4fe8-bd8b-6222efc8b434 Microsoft Entra application ID to restore data. * The cmdlet restore the mailbox items to the UserA@tech.com mailbox.  * The cmdlet will restore mailbox items that are missing in the target location.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "ABC\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  Restore-VEXItem -Mailbox $salesmailbox -OrganizationName tech.onmicrosoft.com -Region Worldwide -ApplicationId 7ddefae2-c812-4fe8-bd8b-6222efc8b434 -TargetMailbox UserA@tech.com -RestoreDeletedItem |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Restore-VEXItem cmdlet. Specify the following settings:  * Set the $salesmailbox variable as the Mailbox parameter value.  * Specify the OrganizationName parameter value. * Specify the Region parameter value. * Specify the ApplicationID parameter value.  * Specify the TargetMailbox parameter value. * Provide the RestoreDeletedItem parameter.  1. To set up a secure connection to a Microsoft organization, open the <https://microsoft.com/devicelogin> link in a browser and enter the code that you get in the PowerShell Console for authenticating to the Microsoft 365 server. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Get-VEXFolder](get-vexfolder.md)
* [Get-VEXItem](get-vexitem.md)

Page updated 7/11/2025

Page content applies to build 13.0.1.1071
