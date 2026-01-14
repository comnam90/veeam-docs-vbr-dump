---
title: "send-vespitem"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/send-vespitem.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Sends SharePoint items as attachments to emails.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Send a SharePoint document library.

|  |
| --- |
| Send-VESPItem [-DocumentLibrary] <VESPDocumentLibrary> [-From <String>] -To <String> [-Subject <String>] [-Body <String>] [-Force] [<CommonParameters>] |

* Send a SharePoint document.

|  |
| --- |
| Send-VESPItem [-Document] <VESPDocument[]> [-From <String>] -To <String> [-Subject <String>] [-Body <String>] [-Force] [<CommonParameters>] |

* Send a SharePoint attachment file.

|  |
| --- |
| Send-VESPItem [-Attachment] <VESPItemAttachment[]> [-From <String>] -To <String> [-Subject <String>] [-Body <String>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet sends the following backed-up SharePoint items as email message attachments:

* SharePoint document libraries.
* SharePoint documents.
* Microsoft organization attachments.

|  |
| --- |
| Note |
| Before sending restored SharePoint organization attachments, check the following prerequisites:   * You must specify Veeam Explorer for Microsoft SharePoint email settings. For more information, see [Set-VESPMailSettings](set-vespmailsettings.md). * You must start a restore session. For more information, see [Start-VBOSharePointItemRestoreSession](start-vbosharepointitemrestoresession.md) or [Start-VBRSharePointItemRestoreSession](start-vbrsharepointitemrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DocumentLibrary | Specifies a SharePoint document library. The cmdlet will send send this document library as an attachment in the email message. | Accepts the [VESPDocumentLibrary](vespdocumentlibrary.md) object. To get this object, run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. | True | 0 | True (ByValue) |
| From | Specifies an email address from which the cmdlet will send backed-up SharePoint data.  If this parameter is omitted, the cmdlet will use the email address, specified in email settings. | String | False | Named | False |
| To | Specifies an email address to which the cmdlet will send restored data. | String | True | Named | False |
| Subject | Specifies a subject of an email message. | String | False | Named | False |
| Body | Specifies a body of an email message. | String | False | Named | False |
| Force | Defines that the cmdlet will skip the certificate check of the recipient.  If you provide this parameter, the cmdlet will send SharePoint attachments without checking whether the recipient certificate is valid. Otherwise, the cmdlet will not send SharePoint attachments if the recipient certificate validation fails.  Default: False | SwitchParameter | False | Named | False |
| Document | Specifies an array of SharePoint documents that you want to send in the email message. | Accepts the [VESPDocument](vespdocument.md)[] object. To get this object, run the [Get-VESPDocument](get-vespdocument.md) cmdlet. | True | 0 | True (ByValue) |
| Attachment | Specifies an array of SharePoint attachments that you want to send in the email message. | Accepts the [VESPItemAttachment](vespitemattachment.md)[] object. To get this object, run the [Get-VESPItemAttachment](get-vespitemattachment.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Sending SharePoint Document Library [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to send the Regulations document library to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $documentLibrary = Get-VESPDocumentLibrary -Database $database -Name "Regulations"  Send-VESPItem -DocumentLibrary $documentLibrary -To administrator@test.local |  Perform the following steps:   1. Get the SharePoint document library:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable.  1. Run the Send-VESPItem cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Sending SharePoint Document [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to send the reports.txt document to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $document = Get-VESPDocument -Database $database -Query "reports.txt"  Send-VESPItem -Document $document -To administrator@test.local |  Perform the following steps:   1. Get the SharePoint document:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. Save the result to the $document variable.  1. Run the Send-VESPItem cmdlet. Set the $document variable as the Document parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Sending SharePoint Attachment [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to send the attachments of the Reports SharePoint item to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBRSharePointItemRestoreSession  $database = Get-VESPDatabase -Session $session -Name "WSS\_Content.mdf"  $item = Get-VESPItem -Database $database -Query "Reports"  $attachment = Get-VESPItemAttachment -Item $item  Send-VESPItem -Attachment $attachment -To administrator@test.local |  Perform the following steps:   1. Get the SharePoint item:  1. Run the [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPDatabase](get-vespdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. Save the result to the $item variable.  1. Run the [Get-VESPItemAttachment](get-vespitemattachment.md) cmdlet. Set the $item variable as the Item parameter value. Save the result to the $attachment variable. 2. Run the Send-VESPItem cmdlet. Set the $attachment variable as the Attachment parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Sending SharePoint Document Library [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to send the Regulations document library to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $documentLibrary = Get-VESPDocumentLibrary -Organization $organization -Name "Regulations"  Send-VESPItem -DocumentLibrary $documentLibrary -To administrator@test.local |  Perform the following steps:   1. Get the SharePoint document library:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $documentLibrary variable.  1. Run the Send-VESPItem cmdlet. Set the $documentLibrary variable as the DocumentLibrary parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Sending SharePoint Document [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to send the reports.txt document to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $document = Get-VESPDocument -Organization $organization -Query "reports.txt"  Send-VESPItem -Document $document -To administrator@test.local |  Perform the following steps:   1. Get the SharePoint document:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPDocument](get-vespdocument.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $document variable.  1. Run the Send-VESPItem cmdlet. Set the $document variable as the Document parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Sending SharePoint Attachment [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to send the attachments to the Reports SharePoint item to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBOSharePointItemRestoreSession  $organization = Get-VESPOrganization -Session $session -Name "ABC\*"  $item = Get-VESPItem -Organization $organization -Query "Reports"  $attachment = Get-VESPItemAttachment -Item $item  Send-VESPItem -Attachment $attachment -To administrator@test.local |  Perform the following steps:   1. Get the SharePoint item:  1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VESPOrganization](get-vesporganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $organization variable. 3. Run the [Get-VESPItem](get-vespitem.md) cmdlet. Set the $organization variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $item variable.  1. Run the [Get-VESPItemAttachment](get-vespitemattachment.md) cmdlet. Set the $item variable as the Item parameter value. Save the result to the $attachment variable. 2. Run the Send-VESPItem cmdlet. Set the $attachment variable as the Attachment parameter value. Specify the To parameter value. |

Related Commands

* [Get-VBRSharePointItemRestoreSession](get-vbrsharepointitemrestoresession.md)
* [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)
* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md)
* [Get-VESPDocument](get-vespdocument.md)
* [Get-VESPItem](get-vespitem.md)
* [Get-VESPItemAttachment](get-vespitemattachment.md)
* [Get-VESPDatabase](get-vespdatabase.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
