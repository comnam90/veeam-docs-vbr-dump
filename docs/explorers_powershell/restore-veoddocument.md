---
title: "Restore-VEODDocument"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-veoddocument.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restores OneDrive documents.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore a specific OneDrive document.

|  |
| --- |
| Restore-VEODDocument [-Document] <VBOOneDriveDocument[]> [-RestoreChangedItems] [-RestoreDeletedItems] [-RestoreSharedAccess] [-SkipSharedAccessNotificationSending] [-Credential <PSCredential>] [-ApplicationId <Guid>] [-TargetUser <String>] [-TargetFolder <String>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-Overwrite] [<CommonParameters>] |

* Restore all documents of a specific OneDrive user.

|  |
| --- |
| Restore-VEODDocument [-User] <VBOOneDriveUser> [-RestoreChangedItems] [-RestoreDeletedItems] [-RestoreSharedAccess] [-SkipSharedAccessNotificationSending] [-Credential <PSCredential>] [-ApplicationId <Guid>] [-TargetUser <String>] [-TargetFolder <String>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-Overwrite] [<CommonParameters>] |

* Restore documents of multiple OneDrive users.

|  |
| --- |
| Restore-VEODDocument [-MultipleUsers] <VBOOneDriveUser[]> [-SkipUnresolvedUsers] [-Credential <PSCredential>] [-Office365Credential <PSCredential>] [-OnPremisesCredential <PSCredential>] [-ApplicationId <Guid>] [-ApplicationCertificatePath <String>] [-ApplicationCertificatePassword <SecureString>] [-Overwrite] [<CommonParameters>] |

Detailed Description

This cmdlet allows you to restore OneDrive documents.

|  |
| --- |
| Note |
| To perform restore operations, you must first start a restore session. For more information on how to start a restore session, see [Start-VEODRestoreSession](start-veodrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Document | Specifies OneDrive documents. This cmdlet will restore the specified OneDrive documents. | Accepts the [VBOOneDriveDocument](vboonedrivedocument.md)[] object. To get this object, run the [Get-VEODDocument](get-veoddocument.md) cmdlet. | True | 0 | True (ByValue) |
| RestoreChangedItems | Defines that the cmdlet will restore all versions of OneDrive documents that were modified by the user.  Default: False | SwitchParameter | False | Named | False |
| RestoreDeletedItems | Defines that the cmdlet will restore all document items that were deleted by the user.  Default: False | SwitchParameter | False | Named | False |
| RestoreSharedAccess | Defines that the cmdlet will restore shared access permissions with the restored document.  Default: False | SwitchParameter | False | Named | False |
| SkipSharedAccessNotificationSending | Defines that the cmdlet will not send shared access notifications.  Default: False | SwitchParameter | False | Named | False |
| Credential | Specifies the account credentials that you want to use for connecting to the OneDrive server.  If omitted, the cmdlet will use the current user Windows account credentials to connect to the OneDrive server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ApplicationId | To restore data using multi-factor authentication.  Specifies a Microsoft Entra application ID. The cmdlet will use this application ID to set up a secure connection to a Microsoft organization. | Guid | False | Named | False |
| TargetUser | Specifies the restore target OneDrive user. This cmdlet will restore OneDrive document to the specified user. | String | False | Named | False |
| TargetFolder | Specifies the restore target OneDrive folder. This cmdlet will restore OneDrive document to the specified folder. | String | False | Named | False |
| ApplicationCertificatePath | To restore data using multi-factor authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will import the certificate that is located in this path to set up an encrypted connection to a Microsoft organization. | String | False | Named | False |
| ApplicationCertificatePassword | To restore data using multi-factor authentication.  Specifies the certificate password. The cmdlet will use this password to confirm the certificate that you want to import to a Microsoft Entra application. This parameter is obligatory. | SecureString | False | Named | False |
| Overwrite | Defines that the cmdlet will overwrite items in the target directory with the restored items if these items have the same name.  Default: False | SwitchParameter | False | Named | False |
| User | Specifies OneDrive user. The cmdlet will restore documents of this user. | Accepts the [VBOOneDriveUser](vboonedriveuser.md) object. To get this object, run the [Get-VEODUser](get-veoduser.md) cmdlet. | True | 0 | True (ByValue) |
| MultipleUsers | Specifies an array of OneDrive users. The cmdlet will restore documents of these users.  Note: This cmdlet will restore documents to the production versions of the same OneDrive users. | Accepts the [VBOOneDriveUser](vboonedriveuser.md)[] object. To get this object, run the [Get-VEODUser](get-veoduser.md) cmdlet. | True | 0 | True (ByValue) |
| SkipUnresolvedUsers | Defines that the cmdlet will not restore items of the users that are not resolved.  Default: False | SwitchParameter | False | Named | False |
| Office365Credential | Specifies the credentials that the cmdlet will use for authenticating to Microsoft 365 organization.  Note: Specify the organization user name in the domain\account format. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| OnPremisesCredential | Specifies the credentials that the cmdlet will use for authenticating to On-Premises SharePoint organization.  Note: Specify the organization user name in the domain\account format. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Specific OneDrive Document

|  |  |
| --- | --- |
| This example shows how to restore the document.txt OneDrive document of the userAlpha user with the following settings:   * The cmdlet will restore the document to the userBeta user. * The cmdlet will restore the document to the UserBetaFolder folder. * The cmdlet will restore all versions of OneDrive documents that were modified by the user. * The cmdlet will restore all document items that were deleted by the user. * The cmdlet will restore all child items. * The cmdlet will overwrite the items in the target directory with the restored items if these items have the same name.   |  | | --- | | $credentials = Get-Credential  $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "document.txt" -Recurse  Restore-VEODDocument -Document $document -RestoreChangedItems -RestoreDeletedItems -Credential $credentials -TargetUser "userBeta" -TargetFolder "UserBetaFolder" -Overwrite |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type Windows credentials to connect to the OneDrive organization. Save the result to the $credentials variable. 2. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 3. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameters value. Save the result to the $user variable. 4. Run the [Get-VEODDocument](get-veoddocument.md) cmdlet. Set the $user variable as the User parameter value. Specify the Name and Recurse parameters. Save the result to the $document variable. 5. Run the Restore-VEODDocument cmdlet. Specify the following settings:  * Set the $document variable as the Document parameter value. * Provide the RestoreChangedItems parameter. * Provide the RestoreDeletedItems parameter. * Set the $credentials variable as the Credential parameter value. * Specify the TargetUser parameter value. * Specify the TargetFolder parameter value. * Provide the Overwrite parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring OneDrive Documents of Specific User

|  |  |
| --- | --- |
| This example shows how to restore all OneDrive documents of the userAlpha user with the following settings:   * The cmdlet will restore the document to the userBeta user. * The cmdlet will restore the document to the UserBetaFolder folder. * The cmdlet will restore all versions of OneDrive documents that were modified by the user. * The cmdlet will restore all document items that were deleted by the user. * The cmdlet will restore all child items.  * The cmdlet will overwrite the items in the target directory with the restored items if these items have the same name.   |  | | --- | | $credentials = Get-Credential  $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  Restore-VEODDocument -User $user -RestoreChangedItems -RestoreDeletedItems -Credential $credentials -TargetUser "userBeta" -TargetFolder "UserBetaFolder" -Overwrite |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type Windows credentials to connect to the OneDrive organization. Save the result to the $credentials variable. 2. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 3. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameters value. Save the result to the $user variable. 4. Run the Restore-VEODDocument cmdlet. Specify the following settings:  * Set the $user variable as the User parameter value. * Provide the RestoreChangedItems parameter. * Provide the RestoreDeletedItems parameter. * Set the $credentials variable as the Credential parameter value. * Specify the TargetUser parameter value. * Specify the TargetFolder parameter value. * Provide the Overwrite parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring OneDrive Documents of Multiple Users

|  |  |
| --- | --- |
| This example shows how to restore OneDrive documents of multiple users with the following settings:   * The cmdlet will not restore documents for users that are not resolved.  * The cmdlet will overwrite the items in the target directory with the restored items if these items have the same name.   |  | | --- | | $o365credentials = Get-Credential  $onPremisesCredentials = Get-Credential  $session = Get-VEODRestoreSession  $users = Get-VEODUser -Session $session  Restore-VEODDocument -MultipleUsers $users -Office365Credential $o365credentials -OnPremisesCredential $onPremisesCredentials -Overwrite -SkipUnresolvedUsers |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type Windows credentials to connect to the OneDrive organization. Save the result to the $o365credentials variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type Windows credentials to connect to On-Premises SharePoint organization. Save the result to the $onPremisesCredentials variable. 2. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 3. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $users variable. 4. Run the Restore-VEODDocument cmdlet. Specify the following settings:  * Set the $users variable as the MultipleUsers parameter value. * Set the $o365credentials variable as the Office365Credential parameter value. * Set the $onPremisesCredentials variable as the OnPremisesCredential parameter value. * Provide the SkipUnresolvedUsers parameter. * Provide the Overwrite parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Specific OneDrive Document Using Multi-Factor Authentication with Microsoft Entra Application ID

|  |  |
| --- | --- |
| This example shows how to restore the document.txt OneDrive document of the userAlpha user with the following settings:   * The cmdlet will apply the 6049d4a6-b814-4b67-aa4c-14580af94dce Microsoft Entra application ID to connect to a Microsoft organization. * The cmdlet will restore the document to the userBeta user. * The cmdlet will restore the document to the UserBetaFolder folder. * The cmdlet will restore all versions of OneDrive documents that were modified by the user. * The cmdlet will restore all document items that were deleted by the user. * The cmdlet will restore all child items. * The cmdlet will overwrite the items in the target directory with the restored items if these items have the same name.   |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "document.txt" -Recurse  Restore-VEODDocument -Document $document -RestoreChangedItems -RestoreDeletedItems -ApplicationId 6049d4a6-b814-4b67-aa4c-14580af94dce -TargetUser "userBeta" -TargetFolder "UserBetaFolder" -Overwrite |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameters value. Save the result to the $user variable. 3. Run the [Get-VEODDocument](get-veoddocument.md) cmdlet. Set the $user variable as the User parameter value. Specify the Name and Recurse parameters. Save the result to the $document variable. 4. Run the Restore-VEODDocument cmdlet. Specify the following settings:  * Set the $document variable as the Document parameter value. * Provide the RestoreChangedItems parameter. * Provide the RestoreDeletedItems parameter. * Specify the ApplicationId parameter value. * Specify the TargetUser parameter value. * Specify the TargetFolder parameter value. * Provide the Overwrite parameter.  1. To set up a secure connection to a Microsoft organization, open the <https://microsoft.com/devicelogin> link in your browser and enter the code that you get in the PowerShell Console for authenticating to the Microsoft 365 server. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Restoring Specific OneDrive Document Using Multi-Factor Authentication with Microsoft Entra Application Certificate

|  |  |
| --- | --- |
| This example shows how to restore the document.txt OneDrive document of the userAlpha user with the following settings:   * The cmdlet will apply the 6049d4a6-b814-4b67-aa4c-14580af94dce Microsoft Entra application ID to connect to a Microsoft organization.  * The cmdlet will use the certificate located at the C:\Certificate path.  * The cmdlet will restore the document to the userBeta user. * The cmdlet will restore the document to the UserBetaFolder folder. * The cmdlet will restore all versions of OneDrive documents that were modified by the user. * The cmdlet will restore all document items that were deleted by the user. * The cmdlet will restore all child items. * The cmdlet will overwrite the items in the target directory with the restored items if these items have the same name.   |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "document.txt" -Recurse  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  Restore-VEODDocument -Document $document -RestoreChangedItems -RestoreDeletedItems -ApplicationId 6049d4a6-b814-4b67-aa4c-14580af94dce -ApplicationCertificatePath "C:\Certificate\Cert.pfx" -ApplicationCertificatePassword $securepassword -TargetUser "userBeta" -TargetFolder "UserBetaFolder" -Overwrite |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameters value. Save the result to the $user variable. 3. Run the [Get-VEODDocument](get-veoddocument.md) cmdlet. Set the $user variable as the User parameter value. Specify the Name and Recurse parameters. Save the result to the $document variable. 4. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to specify the password. Specify the text that will show up in the password prompt window in the Prompt parameter. Specify the AsSecureString parameter to convert the password to the secure string. 5. Enter the password. 6. Run the Restore-VEODDocument cmdlet. Specify the following settings:  * Set the $document variable as the Document parameter value. * Provide the RestoreChangedItems parameter. * Provide the RestoreDeletedItems parameter. * Specify the ApplicationId parameter value.  * Specify the ApplicationCertificatePath parameter value. * Specify the ApplicationCertificatePassword parameter value.  * Specify the TargetUser parameter value. * Specify the TargetFolder parameter value. * Provide the Overwrite parameter. |

Related Commands

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [Get-VEODRestoreSession](get-veodrestoresession.md)
* [Get-VEODUser](get-veoduser.md)
* [Get-VEODDocument](get-veoddocument.md)

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
