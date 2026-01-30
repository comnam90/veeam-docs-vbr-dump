---
title: "Export-VEXItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-vexitem.html"
last_updated: "2/27/2025"
product_version: "13.0.1.1071"
---

# Export-VEXItem


Short Description

Exports Exchange organization backups.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export Exchange organization mailbox items.

|  |
| --- |
| Export-VEXItem -Item <VEXItem[]> -To <String> [-PstSizeLimit <UInt64>] [-Force] [<CommonParameters>] |

* Export an Exchange organization mailbox folder.

|  |
| --- |
| Export-VEXItem -Folder <VEXFolder> -To <String> [-PstSizeLimit <UInt64>] [-Force] [-ContentKeyword <String[]>] [<CommonParameters>] |

* Export an Exchange organization mailbox.

|  |
| --- |
| Export-VEXItem -Mailbox <VEXMailbox> -To <String> [-PstSizeLimit <UInt64>] [-Force] [-ContentKeyword <String[]>] [<CommonParameters>] |

* Export databases of Exchange organization mailboxes.

|  |
| --- |
| Export-VEXItem -Database <VEXDatabase[]> -To <String> [-PstSizeLimit <UInt64>] [-Force] [-ContentKeyword <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet exports Exchange organization mailbox databases, mailboxes, folders and mailbox items into Personal Folder Files (PST files). Additionally, the cmdlet exports mailbox items to Outlook Message Files (MSG files).

|  |
| --- |
| Note |
| * Before running this cmdlet, you must first start a restore session. For more information on how to start a restore session, see [Start-VBOExchangeItemRestoreSession](start-vboexchangeitemrestoresession.md) or [Start-VBRExchangeItemRestoreSession](start-vbrexchangeitemrestoresession.md). * If you start a restore session for Veeam Backup for Microsoft 365, the report about export operations will only be sent to the user account provided in Veeam Explorer for Microsoft Exchange email settings. For more information, see [Set-VEXMailSettings](set-vexmailsettings.md). * The machine on which you are going to run restore sessions must have a 64-bit version of Microsoft Outlook 2016, Microsoft Outlook 2013 or Microsoft Outlook 2010 installed. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies items of an Exchange organization mailbox. The cmdlet will export these items. | Accepts the [VEXItem](vexitem.md)[] object. To get this object, run the [Get-VEXItem](get-vexitem.md) cmdlet. | True | Named | True (ByValue) |
| To | Specifies a path and a name for the PST file or a path for MSG files.  To export databases, mailboxes and folders to a PST file, specify the path and the name for the PST file. The cmdlet will create the PST file with the specified name if it does not exist.  To export items to MSG files, specify the path and the folder. The cmdlet will create the MSG file for each item in the folder that you specified. | String | True | Named | False |
| PstSizeLimit | Specifies the size limit of the exported PST file in GB. The value must be between 1 GB and 49 GB.  If the data you want to export exceeds the specified size limit, Veeam Explorer for Microsoft Exchange will create multiple PST files. | Uint64 | False | Named | False |
| Force | Defines that the cmdlet will perform export operations without notifying the user.  Default: False | SwitchParameter | False | Named | False |
| Folder | Specifies a folder of an Exchange organization mailbox. The cmdlet will export this folder with all its subfolders. | Accepts the [VEXFolder](vexfolder.md) object. To get this object, run the [Get-VEXFolder](get-vexfolder.md) cmdlet. | True | Named | True (ByValue) |
| ContentKeyWord | Specifies a keyword to query data for Exchange organization mailbox. The cmdlet will look for the specified keywords in all message fields (From, To, Subject, Body). After that, the cmdlet will export data that contains the specified keywords. | String[] | False | Named | False |
| Mailbox | Specifies an Exchange organization mailbox that you want to export. | Accepts the [VEXMailbox](vexmailbox.md) object. To get this object, run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. | True | Named | True (ByValue) |
| Database | Specifies an array of Exchange organization mailbox databases. The cmdlet will export these databases. | Accepts the [VEXDatabase](vexdatabase.md)[] object. To get this object, run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Mailbox Items [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to export mailbox items. The cmdlet will export items with the following settings:   * The cmdlet will export items that contain the smith keyword. * The cmdlet will export items from the Contacts folder to the Smith Contacts.pst file.   |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox -Name "Contacts"  $smith = Get-VEXItem -Folder $contacts -Query "smith"  Export-VEXItem -Item $smith -To "C:\North Backup\Sales\Contacts\Smith\Smith Contacts.pst" |  Perform the following steps:   1. Get items with names containing the smith keyword om the Contacts folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable. 5. Run the [Get-VEXItem](get-vexitem.md) cmdlet. Set the $contacts variable as the Folder parameter value. Specify the Query parameter value. Save the result to the $smith variable.  1. Run the Export-VEXitem cmdlet. Set the $smith variable as the Item parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Mailbox Folder [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to export the Contacts folder to the Contacts.pst file.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox -Name "Contacts"  Export-VEXItem -Folder $contacts -To "C:\North Backup\Sales\Contacts\Contacts.pst" |  Perform the following steps:   1. Get the mailbox folder:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable.  1. Run the Export-VEXitem cmdlet. Set the $contacts variable as the Folder parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Exporting Mailbox [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to export the sales mailbox to the Sales.pst file.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  Export-VEXItem -Mailbox $salesmailbox -To "C:\North Backup\Sales\Sales.pst" |  Perform the following steps:   1. Get the sales mailbox:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Export-VEXitem cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Exporting Database [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to export the DB\_0754907780.edb mailbox database to the DB\_0754907780.pst file.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  Export-VEXItem -Database $database -To "C:\Backup\DB\_0754907780.pst" |  Perform the following steps:   1. Get the mailbox database:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.  1. Run the Export-VEXitem cmdlet. Set the $database variable as the Database parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Exporting Mailbox Items [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to export mailbox items. The cmdlet will export items with the following settings:   * The cmdlet will export items that contain the smith keyword. * The cmdlet will export items from the Contacts folder to the Smith Contacts.pst.   |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $mailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $mailbox -Name "Contacts"  $smith = Get-VEXItem -Folder $contacts -Query "smith"  Export-VEXItem -Item $smith -To "C:\North Backup\Sales\Contacts\Smith" |  Perform the following steps:   1. Get items with names containing smith from the Contacts folder:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $mailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable. 5. Run the [Get-VEXItem](get-vexitem.md) cmdlet. Set the $contacts variable as the Folder parameter value. Specify the Query parameter value. Save the result to the $smith variable.  1. Run the Export-VEXitem cmdlet. Set the $smith variable as the Item parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Exporting Mailbox Folder [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to export the Contacts folder to the Contacts.pst file.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  $contacts = Get-VEXFolder -Mailbox $salesmailbox -Name "Contacts"  Export-VEXItem -Folder $contacts -To "C:\North Backup\Sales\Contacts\Contacts.pst" |  Perform the following steps:   1. Get the Contacts mailbox folder:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable. 4. Run the [Get-VEXFolder](get-vexfolder.md) cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $contacts variable.  1. Run the Export-VEXitem cmdlet. Set the $contacts variable as the Folder parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Exporting Mailbox [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to export the sales mailbox to the Sales.pst file.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $salesmailbox = Get-VEXMailbox -Database $database -Name "sales"  Export-VEXItem -Mailbox $salesmailbox -To "C:\North Backup\Sales\Sales.pst" |  Perform the following steps:   1. Get the sales mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $salesmailbox variable.  1. Run the Export-VEXitem cmdlet. Set the $salesmailbox variable as the Mailbox parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 8. Exporting Mailbox Database [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to export a mailbox database to the North.pst file on the machine where the PowerShell session is running.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  Export-VEXItem -Database $database -To "C:\North Backup\North.pst" |  Perform the following steps:   1. Get the mailbox database:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable.  1. Run the Export-VEXitem cmdlet. Set the $database variable as the Database parameter value. Specify the To parameter value. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Get-VEXFolder](get-vexfolder.md)
* [Get-VEXItem](get-vexitem.md)


