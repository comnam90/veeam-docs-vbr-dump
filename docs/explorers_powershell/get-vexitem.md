---
title: "Get-VEXItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexitem.html"
last_updated: "5/6/2025"
product_version: "13.0.1.1071"
---

# Get-VEXItem


Short Description

Returns items added to Microsoft Exchange mailboxes.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get mailbox items from a folder.

|  |
| --- |
| Get-VEXItem -Folder <VEXFolder> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get mailbox items from a mailbox database.

|  |
| --- |
| Get-VEXItem -Database <VEXDatabase[]> [-Query <String>] [<CommonParameters>] |

* Get mailbox items from a mailbox.

|  |
| --- |
| Get-VEXItem -Mailbox <VEXMailbox> [-Query <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns items added to Microsoft Exchange mailboxes. You can search the folder, mailbox or the entire mailbox database to get the necessary item.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Folder | Specifies a mailbox folder. The cmdlet will return items from this folder. | Accepts the [VEXFolder](vexfolder.md) object. To get this object, run the [Get-VEXFolder](get-vexfolder.md) cmdlet. | True | Named | True (ByValue) |
| Query | Specifies a query string for mailbox item search. The cmdlet will return items that match the search query from the specified folder, database or mailbox.  For more information, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. | String | False | Named | False |
| Recurse | Defines that the cmdlet will return items from all subfolders of the specified parent folder.  Default: False | SwitchParameter | False | Named | False |
| Database | Specifies an array of mailbox databases. The cmdlet will return items from these databases. | Accepts the [VEXDatabase](vexdatabase.md)[] object. To get this object, run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. | True | Named | True (ByValue) |
| Mailbox | Specifies a mailbox. The cmdlet will return items from this mailbox. | Accepts the [VEXMailbox](vexmailbox.md) object. To get this object, run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXItem](vexitem.md)[] array that contains Microsoft Exchange mailbox items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Mailbox Items from Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get mailbox items with the support keyword from the DB\_0754907780.edb mailbox database.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  Get-VEXItem -Database $database -Query "support" |  Perform the following steps:   1. Get a mailbox database:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.  1. Run the Get-VEXitem cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Mailbox Items from Mailbox [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get mailbox items from the Sales mailbox.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  Get-VEXItem -Mailbox $salesmailbox |  Perform the following steps:   1. Get the Sales mailbox:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Get-VEXitem cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Mailbox Items from Mailbox Folder [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get items from the Contacts mailbox folder.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  $contacts = Get-VEXFolder -Mailbox $mailbox -Name "Contacts"  Get-VEXItem -Folder $contacts -Recurse |  Perform the following steps:   1. Get the Contacts folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $mailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable.  1. Run the Get-VEXitem cmdlet. Set the $contacts variable as the Folder parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Mailbox Items from Database [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get mailbox items with the support keyword from a mailbox database.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  Get-VEXItem -Database $database -Query "support" |  Perform the following steps:   1. Get the mailbox database:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable.  1. Run the Get-VEXitem cmdlet. Set the $database variable as the Database parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Mailbox Items from Mailbox [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get mailbox items from the Sales mailbox.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "Sales"  Get-VEXItem -Mailbox $salesmailbox |  Perform the following steps:   1. Get the Sales mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Get-VEXitem cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting Mailbox Items from Folder [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get items from the Contacts mailbox folder.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  $contacts = Get-VEXFolder -Mailbox $mailbox -Name "Contacts"  Get-VEXItem -Folder $contacts -Recurse |   1. Get the Contacts folder:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $mailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable.  1. Run the Get-VEXitem cmdlet. Set the $contacts variable as the Folder parameter value. Provide the Recurse parameter. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Get-VEXFolder](get-vexfolder.md)


