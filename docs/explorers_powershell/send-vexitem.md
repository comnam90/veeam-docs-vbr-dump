---
title: "Send-VEXItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/send-vexitem.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Sends Exchange mailbox items as attachments to emails.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Send-VEXItem [-Item] <VEXItem[]> [-From <String>] -To <String> [-Subject <String>] [-Body <String>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet sends Exchange mailbox items as attachments to emails.

|  |
| --- |
| Note |
| Before sending Exchange mailbox items, you must perform the following actions:   * Specify email settings for Veeam Explorer for Microsoft Exchange. For more information on how to specify email settings, see [Set-VEXMailSettings](set-vexmailsettings.md). * Start a restore session. For more information on how to start a restore session, see [Start-VBOExchangeItemRestoreSession](start-vboexchangeitemrestoresession.md) or [Start-VBRExchangeItemRestoreSession](start-vbrexchangeitemrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies items of the Exchange organization mailbox. The cmdlet will send these items as attachments to email. | Accepts the [VEXItem](vexitem.md)[] object. To get this object, run the [Get-VEXItem](get-vexitem.md) cmdlet. | True | 0 | True (ByValue) |
| From | Specifies the email address from which Veeam Explorer for Microsoft Exchange will send restored mailbox data.  If this parameter is omitted, Veeam Explorer for Microsoft Exchange will use the email address specified in the email settings. | String | False | Named | False |
| To | Specifies an email address to which Veeam Explorer for Microsoft Exchange will send restored mailbox data. | String | True | Named | False |
| Subject | Specifies a subject of an email message. | String | False | Named | False |
| Body | Specifies a body of an email message. | String | False | Named | False |
| Force | Defines that the cmdlet will skip the certificate check of the recipient.  If you provide this parameter, the cmdlet will send Exchange items without checking whether the recipient certificate is valid.  Otherwise, the cmdlet will not send Exchange items if the recipient certificate validation fails.  Default: False | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Sending Exchange Mailbox Items [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to send items that were restored from the Contacts folder with the following settings:   * The cmdlet will send restored items from the admin.north@support.com to the sales.north@support.com email address. * The subject of the email message is Sales Contacts. * The body of the email message is Please find attached "North Sales" Contacts.   |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  $contacts = Get-VEXFolder -Mailbox $mailbox  $items = Get-VEXItem -Folder $contacts -Recurse  Send-VEXItem -Item $items -From admin.north@support.com -To sales.north@support.com -Subject "Sales Contacts" -Body "Please find attached "North Sales" Contacts" |  Perform the following steps:   1. Get items from the Contacts folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $mailbox variable as the Mailbox parameter value. Save the result to the $contacts variable. 5. Run the [Get-VEXitem](get-vexitem.md) cmdlet. Set the $contacts variable as the Folder parameter value. Provide the Recurse parameter. Save the result to the $items variable.  1. Run the Send-VEXItem cmdlet. Specify the following settings:  * Set the $items variable as the Item parameter value.  * Specify the From parameter value. * Specify the To parameter value. * Specify the Subject parameter value. * Specify the Body parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Sending Exchange Mailbox Items [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to send items that were restored from the Contacts folder with the following settings:   * The cmdlet will send restored items from the admin.north@support.com to the sales.north@support.com email address. * The subject of the email message is Sales Contacts. * The body of the email message is Please find attached "North Sales" Contacts.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session[0]  $mailbox = Get-VEXMailbox -Database $database[0] -Name "sales"  $contacts = Get-VEXFolder -Mailbox $mailbox  $items = Get-VEXItem -Folder $contacts -Recurse  Send-VEXItem -Item $items -From admin.north@support.com -To sales.north@support.com -Subject "Sales Contacts" -Body "Please find attached "North Sales" Contacts" |  Perform the following steps:   1. Get items from the Contacts folder:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. In this example, it is the first restore session in the array. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value and select the necessary database. In this example, it is the first database in the array. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $mailbox variable as the Mailbox parameter value. Save the result to the $contacts variable. 5. Run the [Get-VEXitem](get-vexitem.md) cmdlet. Set the $contacts variable as the Folder parameter value. Provide the Recurse parameter. Save the result to the $items variable.  1. Run the Send-VEXItem cmdlet. Specify the following settings:  * Set the $items variable as the Item parameter value. * Specify the From parameter value. * Specify the To parameter value. * Specify the Subject parameter value. * Specify the Body parameter value. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Get-VEXFolder](get-vexfolder.md)
* [Get-VEXitem](get-vexitem.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
