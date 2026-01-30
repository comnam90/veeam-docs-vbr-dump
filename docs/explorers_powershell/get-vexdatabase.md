---
title: "Get-VEXDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexdatabase.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VEXDatabase


Short Description

Returns Microsoft Exchange mailbox databases.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEXDatabase [-Session] <IExchangeRestoreSession> [[-Name] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft Exchange mailbox databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return an array of Microsoft Exchange mailbox databases within the specified restore session. | Accepts the IExchangeRestoreSession object. To get this object, run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) or [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | [For Veeam Backup & Replication backups] Specifies an array of Microsoft Exchange mailbox database names. The cmdlet will return an array of Microsoft Exchange mailbox databases with these names.  [For Veeam Backup for Microsoft 365 backups] Specifies an array of Microsoft Exchange organization names. The cmdlet will return an array of Microsoft Exchange organizations with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXDatabase](vexdatabase.md)[] array that contains Microsoft Exchange mailbox databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Microsoft Exchange Databases within Specified Restore Session [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a list of Microsoft Exchange databases within the specified restore session.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  Get-VEXDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the second restore session in the array.   1. Run the Get-VEXDatabase cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft Exchange Database with Specified Name [For Veeam Backup & Replication]

|  |  |
| --- | --- |
| This example shows how to get a specific mailbox database for exploring and restoring mailbox items.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  Get-VEXDatabase -Session $session[1] -Name "DB\_0754907780.edb" |  Perform the following steps:   1. Run the [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md) cmdlet to get an active restore session. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the second restore session in the array.   1. Run the Get-VEXDatabase cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Microsoft Exchange Databases within Specified Restore Session [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get mailbox databases for exploring and restoring mailbox items.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  Get-VEXDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the second restore session in the array.   1. Run the Get-VEXDatabase cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Microsoft Exchange Database with Specified Name [For Veeam Backup for Microsoft 365]

|  |  |
| --- | --- |
| This example shows how to get how to get the ABC Microsoft Exchange organization.  |  | | --- | | $session = Get-VBOExchangeItemRestoreSession  Get-VEXDatabase -Session $session[1] -Name "ABC\*" |  Perform the following steps:   1. Run the [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the second restore session in the array.   1. Run the Get-VEXDatabase cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. |

Related Commands

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)

* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)


