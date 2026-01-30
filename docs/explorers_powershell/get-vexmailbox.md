---
title: "Get-VEXMailbox"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexmailbox.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VEXMailbox


Short Description

Returns Microsoft Exchange mailboxes.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEXMailbox [-Database] <VEXDatabase> [[-Name] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Microsoft Exchange mailboxes from the specified mailbox database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft Exchange mailbox database. The cmdlet will return an array of mailboxes from this mailbox database. | Accepts the [VEXDatabase](vexdatabase.md) object. To get this object, run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of Microsoft Exchange mailbox names. The cmdlet will return an array of mailboxes with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXMailbox](vexmailbox.md)[] array that contains Microsoft Exchange mailboxes.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Specific Mailbox [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get the Sales mailbox backed up on the Veeam Backup & Replication server.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "DB\_0754907780.edb"  Get-VEXMailbox -Database $database -Name "Sales" |  Perform the following steps:   1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md). Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable. 3. Run the Get-VEXMailbox cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Mailbox [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get the Sales mailbox backed up on the Veeam Backup for Microsoft 365 server.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  $database = Get-VEXDatabase -Session $session -Name "support3backup\*"  Get-VEXMailbox -Database $database -Name "Sales" |  Perform the following steps:   1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $database variable. 3. Run the Get-VEXMailbox cmdlet. Set the $database variable as the Database parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)


