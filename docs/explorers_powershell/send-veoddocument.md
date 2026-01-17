---
title: "Send-VEODDocument"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/send-veoddocument.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Sends OneDrive documents as attachments to emails.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Send specific OneDrive documents.

|  |
| --- |
| Send-VEODDocument [-Document] <VBOOneDriveDocument[]> [-From <String>] -To <String> [-Subject <String>] [-Text <String>] [-Force] [<CommonParameters>] |

* Send documents of a specific OneDrive user.

|  |
| --- |
| Send-VEODDocument [-User] <VBOOneDriveUser> [-From <String>] -To <String> [-Subject <String>] [-Text <String>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet sends OneDrive documents as attachments of mail messages.

|  |
| --- |
| Note |
| Before sending restored OneDrive documents, you must verify that you meet the following prerequisites:   * You must specify Veeam Explorer for Microsoft OneDrive for Business email settings. For more information, see [Set-VEODMailSettings](set-veodmailsettings.md). * You must start a restore session. For more information, see [Start-VEODRestoreSession](start-veodrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Document | Specifies an array of OneDrive documents. The cmdlet will send these documents as an attachment in the email message. | Accepts the [VBOOneDriveDocument](vboonedrivedocument.md)[] object. To get this object, run the [Get-VEODDocument](get-veoddocument.md) cmdlet. | True | 0 | True (ByValue) |
| From | Specifies an email address. The cmdlet will send OneDrive document from this email address.  Note: If you omit this parameter, the cmdlet will use the email address specified in email settings. | String | False | Named | False |
| To | Specifies an email address. The cmdlet will send OneDrive document to this email address. | String | True | Named | False |
| Subject | Specifies a subject of an email message. | String | False | Named | False |
| Text | Specifies a body of an email message. | String | False | Named | False |
| Force | Defines that the cmdlet will skip the certificate check of the recipient.  If you provide this parameter, the cmdlet will send OneDrive documents without checking whether the recipient certificate is valid. Otherwise, the cmdlet will not send OneDrive documents if the recipient certificate validation fails.  Default: False | SwitchParameter | False | Named | False |
| User | Specifies a name of the OneDrive user. This cmdlet will send OneDrive document of this user. | Accepts the [VBOOneDriveUser](vboonedriveuser.md) object. To get this object, run the [Get-VEODUser](get-veoduser.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Sending Specific OneDrive Document

|  |  |
| --- | --- |
| This example shows how to send the Review009.txt OneDrive document of the userAlpha user with the following settings:   * The cmdlet will send the document to the user.Alpha@mail.com email address. * The subject of the message is OneDriveDoc. * The body of the message is Mail text.   |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "Review009.txt" -Recurse  Send-VEODDocument -Document $document -To user.Alpha@mail.com -Subject "OneDriveDoc" -Text "Mail text" |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable. 3. Run the [Get-VEODDocument](get-veoddocument.md) cmdlet. Set the $user variable as the User parameter value. Specify the Name and Recurse parameters Save the result to the $document variable. 4. Run the Send-VEODDocument cmdlet. Specify the following settings:  * Set the $document variable as the Document parameter value. * Specify the To parameter value. * Specify the Subject parameter value. * Specify the Text parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Sending OneDrive Documents of Specific User

|  |  |
| --- | --- |
| This example shows how to send OneDrive documents of the userAlpha user with the following settings:   * The cmdlet will send documents to the user.Alpha@mail.com email address. * The subject of the message is OneDriveDoc. * The body of the message is Mail text.   |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  Send-VEODDocument -User $user -To user.Alpha@mail.com -Subject "OneDriveDoc" -Text "Mail text" |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable. 3. Run the Send-VEODDocument cmdlet. Specify the following settings:  * Set the $user variable as the User parameter value. * Specify the To parameter value. * Specify the Subject parameter value. * Specify the Text parameter value. |

Related Commands

* [Get-VEODRestoreSession](get-veodrestoresession.md)
* [Get-VEODUser](get-veoduser.md)

* [Get-VEODDocument](get-veoddocument.md)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
