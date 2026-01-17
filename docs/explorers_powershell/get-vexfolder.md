---
title: "Get-VEXFolder"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexfolder.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns folders added to Microsoft Exchange mailboxes.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all root folders of the mailbox without their subfolders..

|  |
| --- |
| Get-VEXFolder [-Mailbox] <VEXMailbox> [[-Name] <String>] [-Recurse] [<CommonParameters>] |

* Get subfolders for the specified mailbox folder.

|  |
| --- |
| Get-VEXFolder [-Parent] <VEXFolder> [[-Name] <String>] [-Recurse] [<CommonParameters>] |

Detailed Description

This cmdlet returns folders added to Microsoft Exchange mailboxes. The cmdlet will return mailbox folders on which the user has owner permissions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Mailbox | Specifies a mailbox database. The cmdlet will return all mailboxes from this database. | Accepts the [VEXMailbox](vexmailbox.md) object. To get this object, run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies a name of the mailbox. The cmdlet will return the mailbox with this name. | String | False | 1 | False |
| Recurse | Defines that the cmdlet will return the specified parent folder and all of its subfolders.  Default: False | SwitchParameter | False | Named | False |
| Parent | Specifies a parent folder in the mailbox. The cmdlet will return subfolders of this parent folder. | Accepts the VEXFolder object. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXFolder](vexfolder.md)[] array that contains folders added to Microsoft Exchange mailboxes.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Folders with Subfolders from Mailbox [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get all folders and subfolders from the Sales mailbox.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  Get-VEXFolder -Mailbox $mailbox -Recurse |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable.  1. Run the Get-VEXFolder cmdlet with the $mailbox variable. Provide the Recurse parameter to get parent folders with subfolders. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Subfolders of Specific Folder [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get subfolders under the Contacts parent folder.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  $parent = Get-VEXFolder -Mailbox $mailbox -Name "Contacts"  Get-VEXFolder -Parent $parent |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable.  1. Run the Get-VEXFolder cmdlet. Set the $mailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $parent variable. 2. Run the Get-VEXFolder cmdlet. Set the $parent variable as the Parent parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Folders with Subfolders from Mailbox [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get all folders with subfolders from the Sales mailbox.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session[0]  $mailbox = Get-VEXMailbox -Database $database[0] -Name "Sales"  Get-VEXFolder -Mailbox $mailbox -Recurse |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as Session parameter value and select the necessary restore session. In this example, it is the first restore session in the array. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value and select the necessary database. In this example, it is the first database in the array. Specify the Name parameter value. Save the result to the $mailbox variable.  1. Run the Get-VEXFolder cmdlet. Set the $mailbox variable as the Mailbox parameter value. Provide the Recurse parameter to get parent folders with subfolders. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Subfolders of Specific Folder [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get subfolders under the Contacts parent folder.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  $mailbox = Get-VEXMailbox -Database $database -Name "Sales"  $parent = Get-VEXFolder -Mailbox $mailbox -Name "Contacts"  Get-VEXFolder -Parent $parent |  Perform the following steps:   1. Get the mailbox:  1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. Save the result to the $mailbox variable.  1. Run the Get-VEXFolder cmdlet. Set the $mailbox variable as the Mailbox parameter value. Specify the Name parameter value. Save the result to the $parent variable. 2. Run the Get-VEXFolder cmdlet. Set the $parent variable as the Parent parameter value. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
